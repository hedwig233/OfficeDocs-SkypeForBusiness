---
title: "Shared Calling scenario"
ms.reviewer: roykuntz, jastark
ms.date: 04/01/2025
author: mkbond007
ms.author: mabond
manager: pamgreen
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.subservice: teams-calling
search.appverid: MET150
ms.collection: 
  - M365-voice
  - m365initiative-voice
  - highpri
  - Tier1
audience: Admin
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
ms.custom: 
  - Phone System
description: "This article provides an example scenario for configuring Shared Calling."
---

# Shared Calling example scenario

Before reading this article, be sure you've read [Plan for Shared Calling](shared-calling-plan.md) and [Configure Shared Calling](shared-calling-setup.md). These articles describe licensing requirements, prerequisite configuration, and how to configure a Shared Calling policy.

This article provides a sample scenario for setting up Shared Calling by using PowerShell or the Teams admin center for the following steps:

1. Get the Shared Calling user.
1. Enable voice for the user.
1. Get the phone number of the Auto attendant resource account.
1. Create the emergency call routing policy based on the phone number type of the Auto attendant and assign the policy to the user so that they can make emergency calls.
1. Set the static emergency location on the resource account. For the Teams admin center, this step is done when creating the Shared Calling policy.
1. Define the emergency callback numbers that are the same phone number type as the Auto attendant resource account.
1. Create the Shared Calling policy with emergency callback numbers.
1. Grant the Shared Calling policy to the user.

## Shared Calling PowerShell example

```powershell
# Get the Shared Calling user
$user = Get-CsOnlineUser -Identity user@contoso.com

## Enable voice for the user
Set-CsPhoneNumberAssignment -Identity user@contoso.com -EnterpriseVoiceEnabled $true

## Get the phone number of the Auto attendant resource account
$mainaa = 'main-aa@contoso.com'
$PhoneNumber=Get-CsPhoneNumberAssignment -AssignedPstnTargetId $mainaa

if ($PhoneNumber.NumberType -eq 'DirectRouting') {
    # Define the emergency numbers for emergency calling
    $en1=New-CsTeamsEmergencyNumber -EmergencyDialString 933 -OnlinePSTNUsage WW
    $en2=New-CsTeamsEmergencyNumber -EmergencyDialString 911 -OnlinePSTNUsage WW

    New-CsTeamsEmergencyCallRoutingPolicy -Identity TECRP-DR -EmergencyNumbers @{add=$en1,$en2} -AllowEnhancedEmergencyServices $true

    # Grant the policy to the user
    Grant-CsTeamsEmergencyCallRoutingPolicy -Identity $user -PolicyName TECRP-DR
}

else {
    # Define the emergency numbers for emergency calling
    $en1=New-CsTeamsEmergencyNumber -EmergencyDialString 933
    $en2=New-CsTeamsEmergencyNumber -EmergencyDialString 911

    New-CsTeamsEmergencyCallRoutingPolicy -Identity TECRP-CPOC -EmergencyNumbers @{add=$en1,$en2} -AllowEnhancedEmergencyServices $true

    # Grant the policy to the user
    Grant-CsTeamsEmergencyCallRoutingPolicy -Identity $user -PolicyName TECRP-CPOC
}

# Set the static emergency location on the resource account
$CivicAddress = Get-CsOnlineLisCivicAddress -City Seattle
Set-CsPhoneNumberAssignment -LocationId $CivicAddress.DefaultLocationId -PhoneNumber $PhoneNumber.TelephoneNumber

# Define the emergency callback numbers that are the same phone number type as the Auto attendant resource account
$ecbn1 = '+14255556789'
$ecbn2 = '+14255554321'

# Create the Shared Calling policy with emergency callback numbers
$ra = Get-CsOnlineUser -Identity $mainaa
New-CsTeamsSharedCallingRoutingPolicy -Identity Seattle -ResourceAccount $ra.Identity -EmergencyNumbers @{add=$ecbn1,$ecbn2}

# Grant the Shared Calling policy to the user
Grant-CsTeamsSharedCallingRoutingPolicy -Identity $user -PolicyName Seattle
```

## Shared Calling Teams admin center example

You can set up Shared Calling from the Teams admin center, similar to this scenario, by following these steps:

1. To enable Enterprise Voice for a user, go to **Users** > **Manage users** and select the licensed user you want to enable for Shared Calling. This user must have a Phone System license assigned to them. For this example, we use "user@contoso.com."
1. Under the **Account** tab > **Assigned phone number**, turn **Enterprise Voice** to **On** and select **Save**.
1. Go to **Voice** > **Auto attendants** and select the Auto attendant you want to use for Shared Calling. Copy the phone number associated with the Auto attendant's resource account from the **Resource accounts** section of the Auto attendant wizard. To verify the phone number type assigned the resource account, select the resource account and select **Assign/Unassign**. For this example, we use the phone number associated with the resource account "main-aa@contoso.com."
1. To create an emergency call routing policy, go to **Voice** > **Emergency call routing policies** and select **Add**.
    1. Enter a name and description for the emergency call routing policy. For this example, we set the name to "TECRP-DR" and the description as "Emergency call routing policy for Direct Routing."
    1. Toggle **Dynamic emergency calling** to **On**.
    1. Select **Add** and add the emergency numbers by including the Emergency dial string. For example, you can set an **Emergency dial string** to 911 and another to 933. Select **Save**. If your organization uses Direct Routing, you must add Public Switched Telephone Network (PSTN) usages. If not, then no action is needed. For more information, see [Routing of emergency calls for Shared Calling](shared-calling-setup.md#routing-of-emergency-calls).
1. To create a Shared Calling policy, go to **Voice** > **Shared calling policies** and select **Add**.
    1. Enter a unique name and description for the policy. For this example, we set the name to "Seattle" and the description as "Shared Calling policy for Seattle."
    1. For **Resource account**, select the resource account that you want to use for your Shared Calling policy.
    1. To set the static emergency location to the phone number associated with the Auto attendant's resource account, select **Update phone number**. From the **Assign phone number** side panel, select the emergency location and select **Save**. You must set the assigned emergency location to save your Shared Calling policy.
    1. If you want to use emergency callback numbers for the Shared Calling policy, select **Add emergency callback numbers**. From the side panel, select the **Phone number type** and **Assigned phone number**. Once you've added emergency callback numbers, select **Add**. For this example, we use the emergency callback numbers "+14255556789" and "+14255554321." Emergency callback numbers must match the phone number type of the Auto attendant's resource account for this policy.
    1. Select **Save**.
1. To apply this Shared Calling policy to a licensed and voice-enabled user, you can either:
    - Go to **Users** > **Manage users** and check the user you want to enable for Shared Calling and select **Edit settings**. From the side panel, under Shared Calling policy, select the policy you created and select **Apply**.
    - Go to **Voice** > **Shared calling policies** and select the Shared Calling policy you created. Under the **Assigned users** tab, select **Add**. From the side panel, select the user you want to enable for Shared Calling and select **Add**.

## Related topics

- [Plan for Shared Calling](shared-calling-plan.md)
- [Configure Shared Calling policies](shared-calling-setup.md)
- [Set-CsTeamsSharedCallingRoutingPolicy](/powershell/module/teams/set-csteamssharedcallingroutingpolicy)
- [Set-CsPhoneNumberAssignment](/powershell/module/teams/set-csphonenumberassignment)
- [Manage emergency calling](what-are-emergency-locations-addresses-and-call-routing.md)
