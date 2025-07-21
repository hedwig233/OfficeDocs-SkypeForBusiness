---
# Required metadata
# For more information, see https://learn.microsoft.com/en-us/help/platform/learn-editor-add-metadata
# For valid values of ms.service, ms.prod, and ms.topic, see https://learn.microsoft.com/en-us/help/platform/metadata-taxonomies

title: Remote management of contacts for Teams Phones
description: IT Admins can remotely add or delete contacts from their Teams Phones using Teams admin center
author:      ArchanaYerragangu # GitHub alias
ms.author:   ayerragangu # Microsoft alias
ms.service: microsoft-365-admin
ms.topic: article
ms.date:     07/21/2025
---

# Remote management of contacts for Teams Phones

This article provides guidance on the remote management of contacts on Microsoft Teams certified Phones using the Teams admin center. This feature allows users to easily access emergency or frequently used contacts, which will be available in the Company contacts folder on Teams Phones.

> [!NOTE]
> This feature is currently available only for common area phones

#### Steps for managing contacts in Teams admin center

To manage contacts on Teams phones through the Teams admin center, follow these steps:

- __Update the Teams phone to version 1449/1.0.94.2025062601 or later:__ After updating the phone, you will notice changes. To update your Teams phones, refer to [Update your phones remotely](/microsoftteams/phones/remote-update-teams-phones). Ensure that you are running Android version __1449/1.0.94.2025062601__ or later.

- Sign in to the Teams admin center.

- Navigate to Teams devices > Phones > click on the Common area phones tab.

- To add contacts to the __Company contacts__ folder:

  - Select the devices for which you want to add contacts, then click __Manage Contacts__.
  
  - A right pane will open. In the __Add contact__ search box, search and select the desired contacts.
  
  - If you cannot find contacts in the search box, use the __Import contacts__ option. A sample CSV file will be available for download.
  
  - Click __Save__.
  
  - The contacts will sync to the __Company contacts__ folder within approximately 24 hours.
  
- To delete contacts from the __Company contacts__ folder:

  - Select the device from which you need to delete contacts, then click __Manage Contacts__.
  
  - In the right pane, remove the applicable contacts and click __Save__.
  
  - Confirm the deletion in the pop-up that appears.
  
> [!NOTE]
> Manage contacts is currently applicable only for common area phones.
> All Manage Contacts operations, such as adding or deleting a contact, may take up to 24 hours to reflect on the device.
> Contact deletion can be performed for one device at a time.
> The activity log is currently available only for Phones and can be used to track just the Manage Contacts operations.

