---
title: "Integration between Microsoft Teams services and Exchange Server"
ms.reviewer: cbland
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 06/26/2025
audience: ITPro
ms.topic: quickstart
ms.service: skype-for-business-server
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.custom:
  - has-azure-ad-ps-ref, azure-ad-ref-level-one-done
ms.collection: IT_Skype16
ms.assetid: ffe4c3ba-7bab-49f1-b229-5142a87f94e6
description: "Integrating Microsoft Teams services with on-premises Exchange Server enables Teams calendar feature and Cloud Voicemail integration for mailboxes hosted on Exchange Server."
---

# Configure Integration and OAuth between Microsoft Teams services and Exchange Server 

[!INCLUDE[appliesto-2015-2019-sub.md](../../../SfBServer2019/includes/appliesto-2015-2019-sub.md)]

Integrating Microsoft Teams services with on-premises Exchange Server enables Teams calendar feature and [Cloud Voicemail](/microsoftteams/set-up-phone-system-voicemail) integration for mailboxes hosted on Exchange Server (on-premises). More information can be found in the [How Exchange and Microsoft Teams interact](/MicrosoftTeams/exchange-teams-interact#requirements-to-create-and-view-meetings-for-mailboxes-hosted-on-premises) documentation.

This topic applies to integration with any supported version of Exchange Server. Check the [Exchange Server Supportability Matrix](/exchange/plan-and-deploy/supportability-matrix#supported-versions-and-builds) to find out which versions of Exchange Server are in a supported state.

## What do you need to know before you begin?

- Estimated time to complete this task: 15 minutes

- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the [Exchange and Shell infrastructure permissions](/exchange/exchange-and-shell-infrastructure-permissions-exchange-2013-help) topic.

- For information about keyboard shortcuts that may apply to the procedures in this topic, see [Keyboard shortcuts in the Exchange admin center]( https://go.microsoft.com/fwlink/p/?LinkId=746512).

- For information about compatibility, see [Skype for Business compatibility with Office apps](../../plan-your-deployment/clients-and-devices/compatibility-with-office.md).

## Configure integration between Exchange Server and O365

### Step 1: Configure OAuth authentication between Exchange Server and Exchange Online

Perform the steps outlined in the [Configure OAuth authentication between Exchange and Exchange Online organizations](/exchange/configure-oauth-authentication-between-exchange-and-exchange-online-organizations-exchange-2013-help) documentation.

### Step 2: Create a new Mail User account used by Microsoft Teams Calendar Scheduler Service

This step must be performed on the Exchange server. It creates a mail user and assigns the necessary management role permissions. This account will be used in the next step to grant the Microsoft Teams scheduling application the required permissions for calendar delegation.

Specify a verified domain for your Exchange organization. This domain should be the same domain used as the primary Simple Mail Transfer Protocol (SMTP) domain used for the on-premises Exchange accounts. This domain is referred as `<your Verified Domain>` in the following procedure. Also, the `<DomainControllerFQDN>` should be the fully qualified domain name (FQDN) of a domain controller.

```powershell
$user = New-MailUser -Name "TeamsScheduler" -ApplicationAccount -ExternalEmailAddress "TeamsScheduler-ApplicationAccount@<your Verified Domain>" -DomainController <DomainControllerFQDN>
```

This command hides the new mail user from address lists:

```powershell
Set-MailUser -Identity $user.Identity -HiddenFromAddressListsEnabled $true -DomainController <DomainControllerFQDN>
```

Create a new role based on the `UserApplication` role:

```powershell
New-ManagementRole -Name "TeamsSchedulerRole" -Parent "UserApplication" -DomainController <DomainControllerFQDN>
```
 
Remove all cmdlets from the new role except [GetDelegate](/exchange/client-developer/web-service-reference/getdelegate), as this is the only command required by the scheduling (delegation) service:

```powershell
Get-ManagementRoleEntry "TeamsSchedulerRole\*" -DomainController <DomainControllerFQDN> | Where-Object { $_.Name -ne "GetDelegate" } | Remove-ManagementRoleEntry -DomainController <DomainControllerFQDN>
```
 
Assign the `TeamsSchedulerRole` role to the new account:

```powershell
New-ManagementRoleAssignment -Role "TeamsSchedulerRole" -User $user.Identity -DomainController <DomainControllerFQDN>
```

### Step 3: Create and enable a Partner Application for Teams Calendar Scheduler Service integration

Create a new partner application using the account you previously created in [Step 2](#step-2-create-a-new-mail-user-account-used-by-microsoft-teams-calendar-scheduler-service). Run the following command in the Exchange Management Shell (EMS) within your on-premises Exchange organization:

```powershell
New-PartnerApplication -Name "TeamsScheduler" -ApplicationIdentifier "7557eb47-c689-4224-abcf-aef9bd7573df" -Enabled $true -LinkedAccount $user.Identity
```

### Step 4: Create and enable a Partner Application for Cloud Voicemail integration

Create a new partner application to enable Cloud Voicemail integration. Run the following command in the Exchange Management Shell (EMS) on your on-premises Exchange server:

```powershell
New-PartnerApplication -Name "CloudVoicemail" -ApplicationIdentifier "db7de2b5-2149-435e-8043-e080dd50afae" -Enabled $true
```

### Step 5: Export the Exchange Server auth certificate

Run a PowerShell script to export the public key of the Exchange Server auth certificate, which you will import to your Microsoft Teams organization in the next step.

Save the following text to a PowerShell script file named, for example, `ExportAuthCert.ps1`.

```powershell
$thumbprint = (Get-AuthConfig).CurrentCertificateThumbprint
if((Test-Path $env:SYSTEMDRIVE\OAuthConfig) -eq $false)
{
   New-Item -Path $env:SYSTEMDRIVE\OAuthConfig -Type Directory
}
Set-Location -Path $env:SYSTEMDRIVE\OAuthConfig
$oAuthCert = Get-ChildItem -Path Cert:\LocalMachine\My | Where-Object {$_.Thumbprint -match $thumbprint}
$certType = [System.Security.Cryptography.X509Certificates.X509ContentType]::Cert
$certBytes = $oAuthCert.Export($certType)
$CertFile = "$env:SYSTEMDRIVE\OAuthConfig\OAuthCert.cer"
[System.IO.File]::WriteAllBytes($CertFile, $certBytes)
```

In Exchange Management Shell in your on-premises Exchange organization, run the PowerShell script that you created. For example: `.\ExportAuthCert.ps1`

### Step 6: Upload the Exchange Server auth certificate to Microsoft Entra ACS

Next, use the Microsoft Graph PowerShell module to upload the on-premises auth certificate that you exported in the previous step to Microsoft Entra Access Control Services (ACS). If you don't have the module installed, open a Windows PowerShell window as an administrator and run the following command:

```powershell
Install-Module -Name Microsoft.Graph.Applications
```

1. Open a Windows PowerShell workspace that has the Microsoft Graph cmdlets installed. All commands in this step must run using the Windows PowerShell connected to Microsoft Graph console.

2. Save the following text to a PowerShell script file named, for example,  `UploadAuthCert.ps1`.

   ```powershell
   Connect-MgGraph -Scopes Application.ReadWrite.All

   $CertFile = "$env:SYSTEMDRIVE\OAuthConfig\OAuthCert.cer"
   $objFSO = New-Object -ComObject Scripting.FileSystemObject
   $CertFile = $objFSO.GetAbsolutePathName($CertFile)
   $cer = [System.Security.Cryptography.X509Certificates.X509Certificate2]::new($CertFile)
   $binCert = $cer.GetRawCertData()
   $credValue = [System.Convert]::ToBase64String($binCert)
   $serviceNames = @("db7de2b5-2149-435e-8043-e080dd50afae", "7557eb47-c689-4224-abcf-aef9bd7573df", "00000004-0000-0ff1-ce00-000000000000")
   foreach ($serviceName in $serviceNames) {
      Write-Host "[+] Trying to query the service principals for service: $serviceName" -ForegroundColor Cyan
      $p = Get-MgServicePrincipal -Filter "AppId eq '$serviceName'"
      Write-Host "[+] Trying to query the keyCredentials for service: $serviceName" -ForegroundColor Cyan
      $servicePrincipalKeyInformation = Get-MgServicePrincipal -Filter "AppId eq '$serviceName'" -Select "keyCredentials"

      $keyCredentialsLength = $servicePrincipalKeyInformation.KeyCredentials.Length
      if ($keyCredentialsLength -gt 0) {
         Write-Host "[+] $keyCredentialsLength existing key(s) found - we keep them if they have not expired" -ForegroundColor Cyan

         $newCertAlreadyExists = $false
         $servicePrincipalObj = New-Object -TypeName Microsoft.Graph.PowerShell.Models.MicrosoftGraphServicePrincipal
         $keyCredentialsArray = @()

         foreach ($cred in $servicePrincipalKeyInformation.KeyCredentials) {
            $thumbprint = [System.Convert]::ToBase64String($cred.CustomKeyIdentifier)

            Write-Host "[+] Processing existing key: $($cred.DisplayName) thumbprint: $thumbprint" -ForegroundColor Cyan

            if ($newCertAlreadyExists -ne $true) {
               $newCertAlreadyExists = ($cer.Thumbprint).Equals($thumbprint, [System.StringComparison]::OrdinalIgnoreCase)
            }

            if ($cred.EndDateTime -lt (Get-Date)) {
               Write-Host "[+] This key has expired on $($cred.EndDateTime) and will not be retained" -ForegroundColor Yellow
               continue
            }

            $keyCredential = New-Object -TypeName Microsoft.Graph.PowerShell.Models.MicrosoftGraphKeyCredential
            $keyCredential.Type = "AsymmetricX509Cert"
            $keyCredential.Usage = "Verify"
            $keyCredential.Key = $cred.Key

            $keyCredentialsArray += $keyCredential
         }

         if ($newCertAlreadyExists -eq $false) {
            Write-Host "[+] New key: $($cer.Subject) thumbprint: $($cer.Thumbprint) will be added" -ForegroundColor Cyan
            $keyCredential = New-Object -TypeName Microsoft.Graph.PowerShell.Models.MicrosoftGraphKeyCredential
            $keyCredential.Type = "AsymmetricX509Cert"
            $keyCredential.Usage = "Verify"
            $keyCredential.Key = [System.Text.Encoding]::ASCII.GetBytes($credValue)

            $keyCredentialsArray += $keyCredential

            $servicePrincipalObj.KeyCredentials = $keyCredentialsArray
            Update-MgServicePrincipal -ServicePrincipalId $p.Id -BodyParameter $servicePrincipalObj
         } else {
            Write-Host "[+] New key: $($cer.Subject) thumbprint: $($cer.Thumbprint) already exists and will not be uploaded again" -ForegroundColor Yellow
         }
      } else {
         $params = @{
            type = "AsymmetricX509Cert"
            usage = "Verify"
            key = [System.Text.Encoding]::ASCII.GetBytes($credValue)
         }

         Write-Host "[+] This is the first key which will be added to this service principal" -ForegroundColor Cyan
         Update-MgServicePrincipal -ServicePrincipalId $p.Id -KeyCredentials $params
      }
   }
   ```

3. Run the PowerShell script that you created in the previous step. For example:  `.\UploadAuthCert.ps1`

4. After you start the script, a credentials dialog box is displayed. Enter the credentials for the tenant administrator account in your Microsoft Online Microsoft Entra organization. After running the script, leave the Windows PowerShell connected to Microsoft Graph session open. You will use the session to run a PowerShell script in the next step.

### Step 7: Verify that the certificate was uploaded to the first-party Service Principals
1. In the PowerShell connected to Microsoft Graph session, run the following

   ```powershell
   (Get-MgServicePrincipal -Filter "AppId eq '7557eb47-c689-4224-abcf-aef9bd7573df'" -Select "keyCredentials").KeyCredentials | Format-List *
   (Get-MgServicePrincipal -Filter "AppId eq 'db7de2b5-2149-435e-8043-e080dd50afae'" -Select "keyCredentials").KeyCredentials | Format-List *
   (Get-MgServicePrincipal -Filter "AppId eq '00000004-0000-0ff1-ce00-000000000000'" -Select "keyCredentials").KeyCredentials | Format-List *
   ```

2. Confirm you see a key listed with start date and end data that matches your Exchange OAuth certificate start and end dates

### Step 8: Delete the legacy Skype for Business Online Partner Application

> [!CAUTION]
> Don't delete the legacy Skype for Business Online Partner Application yet. Removing this first-party application will disrupt the functionality of out-of-office voicemail greetings, which still depend on the legacy system.
> Microsoft will inform you once it's safe to remove this application.

The legacy first-party `Skype for Business Online` application, which has the application ID `00000004-0000-0ff1-ce00-000000000000`, will be deprecated in near future.
As part of this effort, dedicated first-party application for `Teams Calendar Scheduler Service` and `Cloud Voicemail` were introduced.

Follow the steps in this section to delete any partner application that uses legacy first-party `Skype for Business Online` application:

```powershell
Get-PartnerApplication | Where-Object { $_.ApplicationIdentifier -eq "00000004-0000-0ff1-ce00-000000000000" -and $_.Enabled -eq $true } | Remove-PartnerApplication
```

### Verify your success

Verify that the configuration is correct by verifying some of the features are working successfully. 

1. Confirm Cloud Voicemail functionality in an Exchange Hybrid configuration
- Make a Teams call to a user who has an active `Out of Office` voicemail greeting.
- Leave a voicemail message.
- Listen to the greeting during the call:
  - If the [CloudVoicemail Partner Application](#step-4-create-and-enable-a-partner-application-for-cloud-voicemail-integration) is working, you will hear the `Out of Office` greeting.
  - If it is not working, the regular greeting will play instead.
- After the call, check whether your voicemail message was successfully delivered to the user's mailbox.

2. Confirm conversation history for mobile clients is visible in the Outlook `Conversation History` folder.

3. Confirm that archived chat messages are deposited in the user's on-premises mailbox in the `Purges` folder using [EWSEditor](https://github.com/dseph/EwsEditor/releases).

Alternatively, inspect the traffic during the OAuth handshake. OAuth traffic is distinct and does not resemble basic authentication. A key indicator is the presence of issuer identifiers in the token exchange, such as:
- `7557eb47-c689-4224-abcf-aef9bd7573df@<realm>`
- `db7de2b5-2149-435e-8043-e080dd50afae@<realm>`
- `00000004-0000-0ff1-ce00-000000000000@<realm>` (in legacy first-party app usage scenario)

These identifiers may also appear with a leading slash, for example: `/7557eb47-c689-4224-abcf-aef9bd7573df@<realm>`. These tokens do not include a username or password, which highlights a core principle of OAuth: authentication without credential exchange.

If you want to be sure you're successfully using OAuth, make certain you know what to expect and know what the traffic should look like. So [here's what to expect](https://tools.ietf.org/html/draft-ietf-oauth-v2-23#page-34).

Here's an [example of setting one up](/archive/blogs/kaevans/updated-fiddler-oauth-inspector), but you can use any network tracing tool you like to undertake this process.

## Related topics

[Configure OAuth authentication between Exchange and Exchange Online organizations](/exchange/configure-oauth-authentication-between-exchange-and-exchange-online-organizations-exchange-2013-help)
