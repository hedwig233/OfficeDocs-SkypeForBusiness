---
title: "Setting up Bookable Desks in Microsoft Teams "  
author: mstonysmith
ms.author: tonysmit
manager: pamgreen
ms.reviewer: eviegrimshaw
ms.date: 07/01/2024  
ms.topic: article
audience: Admin
appliesto: 
  - Microsoft Teams
ms.service: msteams  
ms.subservice: itpro-rooms
ms.localizationpriority: medium
ms.collection: 
  - teams-rooms-devices
  - Teams_ITAdmin_Rooms
  - Tier1
ms.custom: QuickDraft 
search.appverid: MET150  
f1.keywords:
  - NOCSH  
description: Helps admins set up Bookable Desks for their Microsoft Teams organization.
---

# Setting up Bookable Desks in Microsoft Teams

Unlock the full potential of your desks with Microsoft Teams. Bookable desks in Microsoft Teams are designed to enhance the efficiency of your organization by enabling users to seamlessly reserve desks upon plug-in to peripherals while providing you with the tools to understand and manage those spaces.

## Overview of steps  

To set up and use Bookable Desks in your organization, you must perform these tasks:

- Step 1: Review the prerequisites.

- Step 2: Create resource accounts.

- Step 3: Collect information on peripheral devices on each desk such as a monitor.

- Step 4: Enable additional features for users. 

- Step 5: Verify the user experience. 

## Step 1 - Review the prerequisites 

- Confirm that you have access to the Microsoft Teams Pro Management portal.

- Ensure that your users have access to the new version of Microsoft Teams desktop app on Windows or Mac.

## Step 2 - Create Desk Pool Accounts

Desk pool accounts, known as **'workspaces'** in Exchange, are slightly different from room accounts. The capacity of a desk pool represents the number of seats in that pool and is set by the admin. The pool can be reserved by multiple users at the same time until all seats (the capacity) are taken. For example, the capacity on a desk pool is set to 2. User A and User B are both able to reserve it from 8am to 5pm, and the remaining capacity will be 0. This means that a third user won't be able to reserve it between 8am and 5pm.

To create a desk pool account, you'll need to set up the workspace resource account in Exchange. We recommend following the steps outlined in [Configure desk booking](/microsoft-365/places/configure-desk-booking?branch=main#configure-desk-pools).

After you create the account, allow 24 to 48 hours for the account to appear in Outlook, Teams, and Teams Rooms Pro Management Portal.

## Step 3 - Collect information on peripheral devices

Next, to ensure a seamless user experience, peripherals such as the monitors on the physical desks need to be associated or linked to the desk pool account you created earlier. To do this, you need to identify the peripherals based on their unique information such as product ID, vendor ID, and serial number.

You can use a free PowerShell script to fetch the details of a peripheral and ensure they're mapped to the corresponding desk pool accounts in the Teams Rooms Pro Management portal. The PowerShell script is located [here ](https://www.microsoft.com/en-us/download/details.aspx?id=106063)to download, and for detailed step-by-step instructions, see [Add peripherals to inventory](/microsoftteams/rooms/get-peripheral-information).

## Step 4 - Enable additional features for users

You have the option to [enable the automatic work location update policy](/powershell/module/teams/new-csteamsworklocationdetectionpolicy) for your organization or for a group of users. Automatic work location updates are designed to enhance the end user experience by making it easier to keep their work location up-to-date and connect with others when they are in the office. With the policy enabled, users have the option to enable automatic work location updates. They can do so in Teams desktop client under **Settings** > **Privacy** > **Sharing your work location**. After users have opted-in, their work location will automatically update to **In the office** when they connect to a bookable desk, provided their work location was previously set to unknown or remote. The detected location lasts until the end of their working hours. If they plug in after work hours, the location will be set until 11:59pm that day. This feature allows for a seamless transition between remote and in-office work, which enhances collaboration and communication within your team and other users. 

## Step 5 - Test the end user experience

Wait 24 hours after associating to test this experience. After that point, ensure that you're signed into Teams on a Windows or Mac laptop. Upon plugging the laptop into a peripheral you associated to a desk pool account and assuming there are seats available to book, you should receive an activity feed notification that 'The space is reserved and ready for you' along with a booking in your calendar. You can also reserve the desk for a future time slot. To learn more on the end user experience, see [First things to know about bookable desks in Microsoft Teams](https://support.microsoft.com/en-us/office/first-things-to-know-about-bookable-desks-in-microsoft-teams-5d10c217-1205-48a1-a883-ff4533f4ae71?preview=true).

## Frequently asked questions

**Question: What are Desk Pools?**  

**Answer:** Desk pools are a group of seats in the office that are close to one other and in the same area. When an employee books a desk in the desk pool, they're reserving a seat in the desk pool.

**Question: What is the difference between individual desks** **and desk pools?**

**Answer**: Individual desks are a new type of resource account in Exchange which will allow a user to book a specific seat instead of booking one of the seats in a desk pool. Support for individual desks for the Bookable desks solution is coming soon.

**Question:** **Is the bookable desks feature available on Classic (old Teams) and new Teams?**

**Answer**: No, the bookable desk experience is only available on the new Teams client. To download and switch to the latest Teams client see, [New Microsoft Teams](https://adoption.microsoft.com/en-us/new-microsoft-teams/).

**Question: Does Bookable** **desks work with Microsoft Places?**

**Answer**: Yes, it does! If a user is automatically reserved in a desk pool, the booking will also appear as the user's desk booking for the day in Places. If a user books a seat in a desk pool in advance through Places, upon plug-in to a bookable desk, the user sees a confirmation message that they're all set for their reservation.

**Question: How can I be sure that it will work with my devices? Do I need** **to buy new hardware?**

**Answer**: That is one of the beauties of Bookable desks! No new hardware is required. We have designed our solution with the goal of working with all models and manufacturers, which is dependent on the device having unique properties. We currently support monitor and devices with both audio and video capabilities. Support for docking stations and webcams are coming soon. 

**Question: Is there another way I can associate my devices other than the PowerShell script?**

**Answer**: Yes, there is! You can also associate the device manually through Pro Management portal. Navigate to **Planning > Inventory > Devices >** select on an unassociated device (one with a 'Needs action' tag) > select on 'Add device to a room or desk' > search for the desired desk pool you'd like to assign the device to. To make it easier to discover devices, they'll be automatically discovered using your users' Teams app. Once five unique users have plugged into a device on a desk, it will automatically surface in the **Devices** tab for association.

## Related links

- [First things to know about bookable desks for end users](https://support.microsoft.com/office/first-things-to-know-about-bookable-desks-5d10c217-1205-48a1-a883-ff4533f4ae71)

