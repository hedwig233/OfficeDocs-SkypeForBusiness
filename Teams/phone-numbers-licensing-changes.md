---
title: "Phone numbers and licensing changes"
author: sfrancis206
ms.author: scottfrancis
manager: pamgreen
ms.reviewer: julienp
ms.date: 05/09/2025
ms.topic: how-to
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
  - Skype for Business
  - Microsoft Teams
ms.localizationpriority: Medium
f1.keywords:
- CSH
ms.custom:
  - has-azure-ad-ps-ref
  - azure-ad-ref-level-one-done

description: Learn how licensing changes can affect phone number management.
---

# How licensing affects phone number management

How you remove and assign licenses to users can impact a user's ability to make and receive Public Switched Telephone Network (PSTN) calls in Microsoft Teams. This article describes how you can manage licensing changes to ensure your users' ability to make and receive PSTN calls isn't impacted.

For general information on managing phone numbers, see [Manage phone numbers for your organization](manage-phone-numbers-landing-page.md). For general information on Teams add-on licensing, see [Microsoft Teams add-on licenses](./teams-add-on-licensing/microsoft-teams-add-on-licensing.md).

## Remove a license

If you have a user with an assigned phone number and you remove one or more of the prerequisites licenses, it unassigns the phone number from the user. Without an assigned phone number, the user's ability to make and receive PSTN calls in Microsoft Teams is impacted.

Depending on the user's [PSTN connectivity option](pstn-connectivity.md), removing a license has the following impact on telephony parameters:

- **Removing a Microsoft 365 Calling Plan license from a user with a Calling Plan phone number** will:
  - Copy any value in OnPremLineUri to LineUri
  - Set EnterpriseVoiceEnabled to False
  - Set phone number assignment status to Unassigned in the phone number database

- **Removing a Microsoft 365 Phone System license from a user with an Operator Connect phone number** will:
  - Clear LineUri
  - Set EnterpriseVoiceEnabled to False
  - Set the phone number’s assignment status to Unassigned in the phone number database

- **Removing a Microsoft 365 Phone System license from a user with a Direct Routing phone number** will:
  - Clear LineUri
  - Set EnterpriseVoiceEnabled to False
  - Remove the phone number from the phone number database

## Change a license

You may need to change a license for a user that involves one of the prerequisite licenses. When you make a prerequisite license change, ensure that the changes are made in one operation and saved at the same time. This method ensures that the user keeps their assigned phone number and can continue making and receiving PSTN calls in Microsoft Teams.

For example, assume you want to assign a Microsoft 365 E5 license to a user who currently has a Microsoft 365 E3 license. 

- If you're using Teams admin center, in the **Licenses and apps** tab on the user details, ensure that the old license is removed and the new license is added before you click **Save changes**. 

- If you're using the PowerShell cmdlet [Set-MgUserLicense](/powershell/module/microsoft.graph.users.actions/set-mguserlicense), execute the cmdlet once and use both the -AddLicenses and the -RemoveLicenses parameters.

(If you remove the old license and save the change, and then add the new license and save the change, the phone number is unassigned and the user might lose the ability to make and receive PSTN calls in Microsoft Teams. After assigning the new license, you’ll need to re-assign the phone number to the user.)

For information about how to change the license simultaneously with group-based licensing, see [Change license assignments for a user or group in Microsoft Entra ID](/azure/active-directory/enterprise-users/licensing-groups-change-licenses).
