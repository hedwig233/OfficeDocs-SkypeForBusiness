---
title: "Manage the usage of a phone number"
author: sfrancis206
ms.author: scottfrancis
manager: pamgreen
ms.reviewer: julienp
ms.date: 04/04/2025
ms.topic: how-to
ms.assetid: 
ms.tgt.pltfrm: cloud
audience: admin
ms.service: msteams
ms.subservice: teams-calling
search.appverid: 
ms.collection: 
- M365-voice
- m365initiative-voice
- Tier1
appliesto:
  - Microsoft Teams
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
  - Calling Plans
description: "Learn how to change the usage of a phone number to be used as either a service number or a user number."
---

# Manage the usage of a phone number

 Microsoft Teams supports using telephone numbers for different purposes. A telephone number's purpose in Teams can be to support a single end user or shared device, or to support services that support your organization.

 The purpose of the telephone number is indicated as it's *usage*.

There are three types of number usages in Teams:

- **User** for phone numbers assigned directly to a user or a person.

- **Voice app** for phone numbers assigned to an Auto attendant or Call queue.

- **Conference** for phone numbers assigned to an Audio conferencing bridge.

For more information about types of phone numbers, see [Manage phone numbers for your organization](manage-phone-numbers-landing-page.md).

You might want to change the usage of a phone number, when you want to assign it to a different purpose.

Before changing the usage of a number:

- Be sure you have the right licenses for the target type of number usage.

- You can only assign toll-free numbers to voice apps (Auto attendants and Call queues) and Audio conferencing bridges.

## How to manage the usage of a phone number

You can change the usage of your organization phone numbers by using the Teams admin center.

To change the usage of a phone number by using the Teams admin center:

1. Open the Microsoft Teams admin center and log in with a Teams Telephony Administrator or higher account. 

1. In the left navigation, select **Voice** > **Phone numbers**.

1. On the **Phone numbers** page, choose an unassigned number in the list, and then select **Change usage**.

   If you don't see a **Change usage** option, check the following:
   
   - Make sure you're selecting an unassigned number before trying to change its usage. The value of the **Assignment status** column should be **Unassigned.** Otherwise, the option isn't available. 
      
   - If the number is currently assigned, you need to [remove the phone number from a user](/MicrosoftTeams/assign-change-or-remove-a-phone-number-for-a-user#remove-a-phone-number-from-a-user) or resource account first. To unassign a number from a conference bridge, see [Change numbers on your Audio Conferencing bridge](change-the-phone-numbers-on-your-audio-conferencing-bridge.md#steps-when-you-unassign-a-service-phone-number-for-a-conferencing-bridge).
   - Make sure you have more types of usage in the **Available usages** column than in the **Licensed usages** column. Otherwise, number usage change option isn't applicable.
      
1. In the **Change usage** pane, open the list of available usages for the phone number, and then select the intended option. 
1. Select **Apply** to set the Licensed usage.

> [!NOTE]
> The list of available usages for the telephone number might vary depending on its type (geographic, or toll-free), country or region, and provider. You can quickly review the available usages for each phone number by setting the **Available usages** column in the Phone numbers table to visible.

> [!IMPORTANT]
> Microsoft recommends that you use roles with the fewest permissions. Least privileged access practices help improve security for your organization. Global Administrator is a highly privileged role that should be limited to emergency scenarios when you can't use an existing role. To learn more, see [About administrator roles in the Microsoft 365 admin center](/microsoft-365/admin/add-users/about-admin-roles) and [Teams administrator roles](using-admin-roles.md).

## Still need assistance?

If you still need assistance, contact the [Telephone Number Services - Service Desk](/MicrosoftTeams/manage-phone-numbers-for-your-organization/contact-tns-service-desk).

## Related articles

[Manage phone numbers for your organization](manage-phone-numbers-landing-page.md)

[Manage phone numbers for users](assign-change-or-remove-a-phone-number-for-a-user.md)


