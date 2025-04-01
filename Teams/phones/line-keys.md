---
title: Manage line keys for speed dial on Teams phones
author: mstonysmith
ms.author: tonysmit
manager: pamgreen
ms.reviewer: prashibadkur
ms.date: 11/04/2024
ms.topic: how-to
audience: Admin
appliesto:
- Microsoft Teams
ms.service: msteams
ms.subservice: itpro-devices
ms.collection:
  - teams-rooms-devices
  - Teams_ITAdmin_Devices
  - Tier1
f1.keywords:
  - NOCSH
search.appverid: MET150
ms.localizationpriority: medium
description: Learn how to set up and manage line or speed dial keys on Microsoft Teams certified phones for quick access to custom contacts and speed dial.
---

# Line or speed dial keys on Microsoft Teams certified phones

This article provides you with guidance on setting up and managing line keys (or speed dial keys) on Microsoft Teams certified phones. This feature allows your users to use a phone line key to set up speed dial for their contacts and phone numbers for quick access using buttons on touch and nontouch devices. A phone line key is one of the keys used to designate individual lines on a phone. Depending on the model and manufacturer, phones typically have between 2 and 12 phone line keys. 

## Steps to use line keys to set up speed dial for nontouch devices 

To set up a line key for speed dial, follow these steps:

1. **Update the Teams phone to version 1449/1.0.94.2024101709 or later**. After updating the phone, you notice a new home screen experience on your device with a dedicated place for your line keys. To update your Teams phones, see [Update your phones remotely](remote-update-teams-phones.md).  Verify that you're running Android version 1449/1.0.94.2024101709 or later.

    You can see the versioning information in the Teams admin center or on the Teams phone.
   
    To see it in the Teams admin center:
   
   1. Sign in to the Teams admin center.
   1. Go to **Teams devices** > **Phones** > then select the phone you want to look at.
   1. Then in the table under **Software type** look for **Teams** and in the **Current version** column you can see the version.
   
      To see the versioning information on the Teams phone itself: Go to the **Profile** icon > **Settings** > **About**.
      
      > [!IMPORTANT]
      > With this update, you can use line keys to set up speed dial for contacts and phone numbers only.
      
      > [!NOTE]
      > With this update, line keys are available for nontouch Teams phone and Teams phones with sidecars.
      
1. **To assign a contact for speed dial:** Select on **Assign line key** and search for an existing contact including with an external phone number, or add a new one.

   - When you first start to assign line keys, you see:
   
     :::image type="content" source="./media/nontouch-line-keys-empty.jpg" alt-text="Screenshot of a non touch phone with line keys."
     
   - Find an available line key for you to use, and select **Assign line key**.
   
     :::image type="content" source="./media/nontouch-line-keys-assign.jpg" alt-text="Screenshot of an available line key on a Teams phone."
     
   - Press and hold on a line key to assign a contact or phone number:
   
     :::image type="content" source="./media/nontouch-line-keys-help.jpg" alt-text="Screenshot of how to long press a line key to set it up."
     
   - After you assign a contact or phone number to the line key, you'll see:
   
     :::image type="content" source="./media/nontouch-line-keys-assigned.jpg" alt-text="Screenshot of how to long press a line key that is assigned."
     
1. **To modify or manage an assigned line key:** Long press an existing line key to see a detailed menu with the following options:

     :::image type="content" source="./media/nontouch-line-keys-manage.jpg" alt-text="Screenshot of line key management options."
   
   - **Unassign line key** - Use this setting to remove an assigned line key.
   - **Reassign line key** - Use this setting to modify the contact assigned to this line key.
   - **Manage line key** - Use this setting to access more management options.
      
1. **To place a call:** Press or select on the key to place a call to the user or number assigned to that line key.

1. To hide unassigned line keys, navigate to settings to view Calling settings. Enable toggle on Hide unassigned line key. Go back to home screen, unassigned line keys will now be hidden.  

## Steps to use line keys to set up speed dial for touch devices

Update your Teams phones to **1449/1.0.94.2025084203** or later. After updating the phone, you notice a new home screen experience on your device with a dedicated app for line keys on your home screen.

**To assign a contact for speed dial** From the Home Screen, select on **Assign line key** and search for an existing contact with an external phone number or add a new one.

![Screenshot of the home screen.](media/line-key-updates-1.png)

When you first start to assign line keys, you see:

![Screenshot of assinging a line key.](media/line-key-updates-2.png)

Press and hold on a line key to assign a contact or phone number.

![Screenshot of pressing an holding for quick actions.](media/line-key-updates-3.png)

**To modify or manage an assigned line key** Long press an existing line key to see a detailed menu:

- **Reassign line key** - Use this setting to remove an assigned line key.
- **Unassign line key** -  Use this setting to modify the contact assigned to this line key.
- **Manage line key** - Use this setting to access more management options.

**To place a call** Press or select on the key to place a call to the user or number assigned to that line key.

![Screenshot of settings and options.](media/line-key-updates-4.png)

**To pin line key app to your home screen** Navigate to settings to view Home screen options and choose Line keys.

**To hide unassigned line keys** Navigate to settings to view **Calling settings**. Turn on **Hide unassigned line key**. Go back to line key app, unassigned line keys will now be hidden.  

## Frequently Asked Question

**Question:**  Can line keys be configured on the Teams Admin Center with this update?  

**Answer:**  No, currently configuration support is only on the Teams phone.

**Question:**  What other functions can I perform using line keys?  

**Answer:**  With this update, you can use line keys for quick access to speed dial only. In the future, we support line keys for call controls and offer enhancements for shared line configuration.

**Question:**  Does this change the existing functionality of sidecars?  

**Answer:**  No, the current functionality of the pinning of speed dial, shared lines, and group contacts doesn't change. However, in future updates, we'll also support ability to configure them as line keys on the sidecar.

### Related articles

- [Microsoft Certified Teams phones](../devices/teams-phones-certified-hardware.md)
- [Phones for Microsoft Teams](phones-for-teams.md)