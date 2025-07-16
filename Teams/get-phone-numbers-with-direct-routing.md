---
title: "Get Direct Routing phone numbers in your Teams tenant"
author: sfrancis206
ms.author: scottfrancis
manager: pamgreen
ms.reviewer: pavellatif
ms.date: 05/05/2025
ms.topic: how-to
ms.assetid: aa2ec464-3481-4bbb-8c14-e13e18093df5
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
f1.keywords:
- CSH
ms.custom: 
  - Calling Plans
description: "Learn how to upload Direct Routing telephone numbers to your Teams admin center."
---

# Get phone numbers with Direct Routing uploaded to your tenant

**APPLIES TO:** ![Image of a checkmark for yes](/office/media/icons/success-teams.png) Direct Routing

This article provides considerations and guidance for IT pros and admins who are acquiring new telephone numbers from a Direct Routing partner.

Direct Routing is one of several methods available to integrate your tenant with the Public Switched Telephone Network (PSTN).

To learn more about Direct Routing as a PSTN solution, see [Plan for Direct Routing](direct-routing-plan.md).

In a Direct Routing solution, the phone number services agreement is between your organization and your PSTN operator. You may fulfill other requirements with your Direct Routing PSTN operator, like assigning number usage types, Emergency Calling services, and more.

To reserve and acquire new Direct telephone numbers or to port existing numbers to your Direct Routing partner, work with your Direct Routing PSTN partner directly.

Once you acquire numbers from your partner, use the following guidance to upload those numbers so that you can manage your Direct Routing numbers in Teams.

One your numbers are uploaded to Teams, you can use Teams to assign Direct Routing numbers to users. To learn more, see [Manage phone numbers for users](assign-change-or-remove-a-phone-number-for-a-user.md).

## Considerations for getting Direct Routing numbers in your tenant

Direct Routing phone numbers can be managed in on-premises Active Directory or in Microsoft 365. Managing numbers in Microsoft 365 is recommended.

### Direct Routing numbers managed in an on-premises Active Directory

If you have or had a Skype for Business Server hybrid deployment,
your on-premises Active Directory is most likely synchronizing with Microsoft 365. This means that directory attributes on user and resource accounts are managed in the on-premises Active Directory and synchronized into Microsoft 365.

If the Direct Routing phone number is managed on the user or resource account in the on-premises Active Directory, the msRTCSIP-Line parameter on the account contains a value. You can use a tool such as ADSI Edit to view the msRTCSIP-Line parameter for a user or resource account that has a Direct Routing phone number assigned in on-premises Active Directory.

Through the directory synchronization process (Microsoft Entra Connect), this parameter is automatically synchronized to the user or resource account in Microsoft 365. After the synchronization is complete, view the phone number by looking at the OnPremLineURi parameter in the output from the [Get-CsOnlineUser](/powershell/module/teams/get-csonlineuser) cmdlet.

| Where | Parameter | Value |
| :------------| :-------| :---------|
| On-premises AD | msRTCSIP-Line | tel:+14255551234 |
| Microsoft 365 | OnPremLineURi | tel:+14255551234 |

### Direct Routing numbers managed in Microsoft 365

If you're not managing Direct Routing phone numbers in the on-premises Active Directory, then they're only managed in Microsoft 365. When numbers are managed in Microsoft 365 and you run the Get-CsOnlineUser cmdlet for a user or resource account, there's no visible value in the OnPremLineUri parameter.

You can manage Direct Routing numbers in Microsoft 365 with Teams PowerShell, using the [Set-CsPhoneNumberAssignment](/powershell/module/teams/set-csphonenumberassignment) and [Get-CsPhoneNumberAssignment](/powershell/module/teams/get-csphonenumberassignment) cmdlets.

### Direct Routing numbers managed in both an on-premises Active Directory and Microsoft 365

It's possible to manage Direct Routing phone numbers of some user and resource accounts in on-premises Active Directory while managing others in Microsoft 365. This capability depends on whether the attribute msRTCSIP-Line is set on the user or resource account in the on-premises Active Directory.

### Change where Direct Routing phone numbers are managed

To move management of Direct Routing phone numbers from on-premises Active Directory to Microsoft 365, in the on-premises Active Directory user or resource account, remove the phone number from the msRTCSIP-Line attribute.

The phone number needs to be reassigned to the user or resource account in Microsoft 365.

After the removal is synchronized to Microsoft 365, the OnPremLineUri attribute in the output from Get-CsOnlineUser on the user or resource account will be empty.

For more information, see [Clear Skype for Business attributes for all on-premises users in Active Directory](/skypeforbusiness/hybrid/cloud-consolidation-managing-attributes#method-2---clear-skype-for-business-attributes-for-all-on-premises-users-in-active-directory.md).

## Upload Direct Routing numbers to your tenant

Uploading your Direct Routing phone numbers to Microsoft's telephone number management inventory supports future number management enhancements.

For example, if you upload your numbers, you can view them in the Teams admin center under **Phone Numbers** or by using the PowerShell cmdlets [Get-CsPhoneNumberAssignment](/powershell/module/teams/get-csphonenumberassignment) and [Export-CsAcquiredPhoneNumber](/powershell/module/teams/export-csacquiredphonenumber).

Uploading your Direct Routing phone numbers to Microsoft's telephone number management inventory is optional. If you don't upload the phone numbers, you can still assign numbers to users. Assigning a number to a user automatically uploads the number to Microsoft's telephone number management inventory if it's not already there.

### Use Teams admin center

1. Go to **Voice** > **Phone numbers**.

2. Under the **Numbers** tab, select **Add**.

   Adding phone numbers to your tenant and to Microsoft's telephone number management inventory is accomplished by creating an order request. By selecting **Add**, you're originating an order request that creates an order ID and launch the process of uploading your Direct Routing numbers. To complete your order, follow the remaining steps.

3. Give your order a **Name** and **Description**.

4. From the options, choose **From Direct Routing**.

5. Select your preferred method of uploading the numbers by selecting from the drop-down, one of the following options:

#### Add one to many phone numbers

If you select **Add one to many phone numbers**, type or paste the phone numbers you wish to upload in the text field.

If you're adding more than one phone number to this list, separate each number with a comma or a new line.

#### Add phone number range

If you select **Add phone number range**, type or paste the starting and ending numbers of your range in the respective text fields.

#### Upload CSV

If you select **Upload CSV**, select the **Upload CSV** icon and select your CSV file.

The CSV file format requirements are to have a single column, with the first row populated as **TelephoneNumber** and each subsequent row including one phone number.

Download a template by selecting **Download a sample CSV file with Direct Routing Numbers**.

6. Select **Next** and proceed to review the validated numbers to be reserved by Microsoft's telephone number management inventory.

7. Select **Confirm**, then select **Finish**

### Use PowerShell

To upload Direct Routing telephone numbers to Microsoft's telephone number management inventory, use the [New-CsOnlineDirectRoutingTelephoneNumberUploadOrder](/powershell/module/teams/new-csonlinedirectroutingtelephonenumberuploadorder) cmdlet.

Uploading the numbers is an asynchronous operation.

### Order history

View the status of the numbers you uploaded in Teams admin center by navigating to **Voice** > **Phone numbers** and selecting the **Order history** tab.

View the order status of numbers you uploaded with PowerShell by using the [Get-CsOnlineTelephoneNumberOrder](/powershell/module/teams/get-csonlinetelephonenumberorder) PowerShell cmdlet with **OrderType** set to `DirectRoutingNumberCreation`, as shown in the following example:

```PowerShell
 Get-CsOnlineTelephoneNumberOrder -OrderType DirectRoutingNumberCreation -OrderId <orderId>
```

> [!NOTE]
> Whenever porting Direct Routing numbers to Teams using another PSTN connectivity option, the numbers must be released from Microsoft's telephone number management inventory. After unassigning the numbers from the users and before your number port event, use the PowerShell cmdlet [New-CsOnlineTelephoneNumberReleaseOrder](/powershell/module/teams/new-csonlinetelephonenumberreleaseorder) to make the Direct Routing numbers available for porting. A release order can also be used if you don't want to keep your acquired Direct Routing numbers in Microsoft's inventory.

## Related topics

[Manage telephone numbers for your organization](manage-phone-numbers-landing-page.md)

[Plan for Direct Routing](direct-routing-plan.md)

[Manage phone numbers for your users](assign-change-or-remove-a-phone-number-for-a-user.md)
