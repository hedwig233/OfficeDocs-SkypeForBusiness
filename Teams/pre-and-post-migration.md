---
title: Best migration practices for app centric management
author: surbhigupta12
ms.author: surbhigupta
manager: prkosh
ms.topic: how-to
audience: admin
ms.service: msteams
ms.subservice: teams-apps
ms.collection: 
  - M365-voice
  - m365initiative-voice
  - M365-collaboration
  - Tier1
search.appverid: MET150
ms.date: 04/28/2025
ms.reviewer: nguyenb
description: Learn about the best practices for migrating to app centric migration, which includes pre and post migration best practices.
f1.keywords:
- NOCSH
ms.localizationpriority: high
appliesto: 
  - Microsoft Teams
ms.custom: seo-marvel-apr2020
---

# Best migration practices for app centric management

App centric management simplifies the process of allowing apps for your users and groups. App centric management migration involves preserving the users and apps allowed in your app permission policies. You can also add or exclude users during the migration.

We recommend you follow these steps before and after the manual migration to check app centric management migration health.

## Pre-migration

1. [Export app catalog and note allowed apps](#step-1-export-app-catalog-and-note-allowed-apps)
1. [Review permission policies and note allowed or blocked apps](#step-2-review-permission-policies-and-note-allowed or blocked-apps)
1. [Identify users permitted for each app through permission policies](#step-3-identify-users-permitted-for-each-app)

### Step 1: Export app catalog and note allowed apps

Navigate to **Manage Apps** page and export the full list of apps in the catalog as a CSV file, including each app’s allowed or blocked app status. The allowed or blocked status determines whether the app is available to everyone or no one, respectively. This status is used in the following steps to filter your users. For more details, see [export app catalog as CSV](manage-apps.md#export-app-catalog-as-csv).

    :::image type="content" source="media/step1–export-app-catalog.png" alt-text="Screenshot showing  export App catalog and note your allowed apps.":::

### Step 2: Review permission policies and note allowed or blocked apps

If you have multiple permission policies, follow these steps to get the permission policies list:

1. Go to **Teams admin center** > **Manage apps** > **Permission policies**.
1. Open each permission policy and note which apps are allowed or blocked.

Steps to get the permission policies list using PS cmdlet:

1. Run Get-CsTeamsAppPermissionPolicy(/powershell/module/teams/get-csteamsapppermissionpolicy?view=teams-ps &preserve-view=true).

<expand>Interpreting results:
    :::image type="content" source="media/step2–interpret-results.png" alt-text="Screenshot showing interpreting results.":::

In the preceeding example, there are three policies in the tenant: Global, Test Policy, and Test 2.

For the Global policy, these are the permission policies:
* Microsoft apps (Default Catalog Apps): com.microsoft.teamspace.tab.vsts, cd2d8695-bdc9-4d8e-9620-cc963ed81f41, com.microsoft.teamspace.tab.planner, a6b63365-31a4-4f43-92ec-710b71557af9 and so on are allowed, the rest are blocked (allowed app list)
* Third-party apps (Global Catalog Apps) three apps are allowed, the rest are blocked (allowed App list)
* Custom apps (Private Catalog Apps): All allowed (blocked app list is empty)

Response legend<sentence>:

* Allowed app list with a list of apps: List of apps allowed, all other apps are blocked.
* Allowed app list with an empty list of apps: All apps are blocked.
* Blocked app list with an empty list of apps: All apps are allowed.
* Blocked app list with a list of apps: Apps are blocked and all other apps are allowed.

#### Retrieve allowed apps in each permission policy

PowerShell cmdlet:
In the example above, not all default apps are shown in the response. To see all the default apps, you need to assign a variable to the result.
For example: $msftApps = Get-CsTeamsAppPermissionPolicy -Identity "Global" | Select-Object -ExpandProperty DefaultCatalogApps $msftApps.id

#### Filter out blocked apps

After gathering information on all apps permitted within the tenant, identify the individuals or groups for whom each app is authorized.

Merge it with export from Manage apps page and anything that is blocked in Manage apps are blocked no matter what the policy assignment might return.

### Step 3: Identify users permitted for each app

You can identify users permitted for each app in the following methods:
* [Teams admin center](#get-a-list-of-users-assigned-to-a-policy-in-ui)
* [PowerShell](#identify-users-allowed-for-each-app-in-powershell)

#### Get a list of users assigned to a policy in UI

1. Go to Teams admin center - https://admin.teams.microsoft.com/
1. Go to **Users** > **Manage users**.
    :::image type="content" source="media/step3-manage-users-page.png" alt-text="Screenshot showing manage users page.":::

1. Select the filter located at the top right of the Manage users table.
    :::image type="content" source="media/step3-manage-users-page-filter.png" alt-text="Screenshot showing manage users page filter.":::

1. Select the policy name for which you need the user assignments and click **Apply**.
    :::image type="content" source="media/step3-manage-users-page-filter-applied.png" alt-text="Screenshot showing manage users page applied page.":::

All the users assigned to the policy filtered are displayed.

    :::image type="content" source="media/step3-manage-users-page-filter-result.png" alt-text="Screenshot showing manage users page filter results.":::

1. You can also export the users list to CSV.
    :::image type="content" source="media/step3-manage-users-page-export-csv.png" alt-text="Screenshot showing export manage users page csv.":::

#### Identify users allowed for each app in PowerShell

You can also use the following PowerShell command to export user assignments for each custom policy. This script generates an Excel file if the given policy has user assignments; otherwise, a message is shown indicating that no user assignments exist.

PowerShell command output is as follows:
    :::image type="content" source="media/step3b-pscommand-output.png" alt-text="PowerShell command output.":::

The exported file appears as follows:
    :::image type="content" source="media/step3b-exported-file.png" alt-text="Exported file output.":::

* To define the base path for exports: `$basePath = "C:\Users\patelsagar\Downloads"`
* To ensure the base path exists:
if (-not (Test-Path -Path $basePath)) { 
    New-Item -ItemType Directory -Path $basePath | Out-Null 
}

* To retrieve all Teams app permission policies:
`$policies = Get-CsTeamsAppPermissionPolicy | Select-Object Identity`

* To loop through each policy:
'foreach ($policy in $policies) {
    $policyName = $policy.Identity
    #Ignore 'Global' policy
    if ($policyName -eq 'Global') {
        continue
    }'

* To remove 'TAG:' prefix if it exists:

    `if ($policyName -like 'TAG:*') { 
        $policyName = $policyName -replace '^TAG:', ''
    }`

* To retrieve the users assigned to the current policy:
    `$users = Get-CsOnlineUser -Filter "TeamsAppPermissionPolicy -eq '$policyName' -and SoftDeletionTimestamp -eq `$null" |
             Select-Object Identity, DisplayName, UserPrincipalName, TeamsAppPermissionPolicy, AccountEnabled, AccountType`

* To check if the users count is zero:
  `if ($users.Count -eq 0) {
        Write-Host "`e[31m$policyName does not have any user assignments`e[0m"
        continue
    }`

* To export users to a CSV file:
    `$outputPath = "$basePath\users_$($policyName).csv"
     $users | Export-Csv -Path $outputPath -NoTypeInformation`
    Write-Host "`e[32mExported users for policy: $policyName to $outputPath`e[0m" 
}

## Post migration

After migrating to , customers can validate against the pre-migration posture using the same steps. Follow the instructions defined in this section to gather your previous permission policies and compare them to your app centric management settings. Review your permission policies and note your allowed/blocked apps.

## Bulk app management

1. **Create Distribution Lists and Add Members**: You can use the `New-DistributionGroup` and `Add-DistributionGroupMember` cmdlets to create distribution lists and add members.

For example:
`New-DistributionGroup -Name "DTDEAUG_MSTeamsAppPolicy_M365TeamsAdmins" -PrimarySmtpAddress "DTDEAUG_MSTeamsAppPolicy_M365TeamsAdmins@man-es.com"`
`Add-DistributionGroupMember -Identity "DTDEAUG_MSTeamsAppPolicy_M365TeamsAdmins" -Member "user1@man-es.com"`

1. Assign all apps to a distribution list: To assign all apps to the distribution list DTDEAUG_MSTeamsAppPolicy_M365TeamsAdmins@man-es.com, you can use the `Update-M365TeamsApp` cmdlet. Here is an example to assign all apps together:

`$apps = Get-AllM365TeamsApps
foreach ($app in $apps) {
    Update-M365TeamsApp -Id $app.Id -AppAssignmentType UsersAndGroups -Groups "DTDEAUG_MSTeamsAppPolicy_M365TeamsAdmins@man-es.com"
}`

1. Modify availability of specific apps to everyone: To modify the availability of specific apps to everyone, you can use the `Update-M365TeamsApp` cmdlet with the `AppAssignmentType` parameter set to `Everyone`.

For example:
`$appIds = @("appId1", "appId2", "appId3", ...) # List of 53 app IDs
foreach ($appId in $appIds) {
    Update-M365TeamsApp -Id $appId -AppAssignmentType Everyone
}`

1. Allow Microsoft apps to multiple distribution lists: To allow all Microsoft apps to the distribution lists DTDEAUG_MSTeamsAppPolicy_ITTestMSPVA@man-es.com and DTDEAUG_MSTeamsAppPolicy_M365TeamsAdmins@man-es.com, you can use the `Update-M365TeamsApp` cmdlet.

For example:
$msApps = Get-AllM365TeamsApps | Where-Object { $_.Publisher -eq "Microsoft" }
foreach ($app in $msApps) {
    Update-M365TeamsApp -Id $app.Id -AppAssignmentType UsersAndGroups -Groups "DTDEAUG_MSTeamsAppPolicy_ITTestMSPVA@man-es.com","DTDEAUG_MSTeamsAppPolicy_M365TeamsAdmins@man-es.com"
}

1. Here's an example of the `list.csv` file:
AppId,DistributionList
appId1,DTDEAUG_MSTeamsAppPolicy_Group1@man-es.com
appId2,DTDEAUG_MSTeamsAppPolicy_Group2@man-es.com
appId3,DTDEAUG_MSTeamsAppPolicy_Group3@man-es.com
...

The following PowerShell script can be used to read the CSV file and assign the applications to the specified distribution lists:
`$csv = Import-Csv -Path "C:\path\to\list.csv"
foreach ($row in $csv) {
    Update-M365TeamsApp -Id $row.AppId -AppAssignmentType UsersAndGroups -Groups $row.DistributionList
}`

This PowerShell script loops through each row in the CSV file and assign the applications to the corresponding distribution lists.

Another example:

1. Made required changes to Teams Admin Center Configuration Updates.
1. Applied all available apps to Teams Admin Distribution Group for smooth management.  
PowerShell command used:
`Import-Csv .\AppList1.csv | %{Update-M365TeamsApp -Id $_.AppId  -AppAssignmentType UsersAndGroups -Groups $_.GroupID -OperationType Add}`

1. Assigned all Microsoft apps to a designated custom policy group to keep all Microsoft apps organized and managed under a specific policy for targeted user group.
PowerShell command used:
`Import-Csv .\AppList2.csv | %{Update-M365TeamsApp -Id $_.AppId  -AppAssignmentType UsersAndGroups -Groups $_.GroupID -OperationType Add}`

1. Mapped specific apps to their respective custom policy groups for making access control more effective.
PowerShell command used:
`Import-Csv .\AppList3.csv | %{Update-M365TeamsApp -Id $_.AppId  -AppAssignmentType UsersAndGroups -Groups $_.GroupID -OperationType Add}`

1. Update **Global Policy** to make selected apps accessible to all users across the organization.
PowerShell command used:
`gc '.\GlobalApps.txt' | %{Update-M365TeamsApp -Id $_ -AppAssignmentType Everyone}`

## Related articles

* [Check the availability and state of app](/powershell/module/teams/get-m365teamsapp)
* [View all Teams apps in the app catalog](/powershell/module/teams/get-allm365teamsapps)
* [Updates the state of an app](/powershell/module/teams/update-m365teamsapp)