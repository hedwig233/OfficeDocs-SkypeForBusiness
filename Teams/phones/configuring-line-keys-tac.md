---
# Required metadata
# For more information, see https://learn.microsoft.com/en-us/help/platform/learn-editor-add-metadata
# For valid values of ms.service, ms.prod, and ms.topic, see https://learn.microsoft.com/en-us/help/platform/metadata-taxonomies

title: 'Configure line keys from Teams Admin center '
description: 'Article describing how to configure line keys from TAC '
author:      pbadkur1 # GitHub alias
ms.author:   pbadkur1 # Microsoft alias
ms.service: msteams
ms.topic: article
ms.date:     07/24/2025
ms.subservice: itpro-devices
---
# Configuring Line Keys from Teams Admin Center (TAC)

This article provides a comprehensive guide for IT administrators to configure line keys on Microsoft Teams-certified phone devices using the Teams Admin Center (TAC). 

Line keys allow users to quickly access contacts or perform call-related actions. Admins can centrally configure these keys via TAC for both Common Area Phones (CAP) and personal Teams phones. The configuration experience is tailored to device types and user roles, ensuring flexibility and control. The configuration is available for both common area phones, those with a Teams Shared Device License and personal phones, those with a Teams Phone License, for more details see [How to Deploy Teams Phone Devices](https://techcommunity.microsoft.com/blog/microsoftteamsblog/how-to-deploy-teams-phone-devices/3994979).

### App Version Requirements

- Teams Phone App: <Insert app version>

- Teams Admin Center (TAC): <Insert>

### Steps to configure  



Step 1: Update the phone device and check for default settings 

- Navigate to **Settings > Calling > Line Keys Settings** on the device.

- For common area phones, ensure **Allow admin override** and **Hide unassigned line keys** are enabled and ON by default.

- For personal phones, enable **Allow admin override** to turn it ON as they are not enabled by default. 

Step 2: On TAC, create a configuration profile

- Sign in to https://admin.teams.microsoft.com/.

- Go to **Teams Devices > Phones > Configuration Profile > Add Profile**.

- Scroll to the **Line Keys** section.

- Toggle **Configure line keys** to ON. 

- You can choose to follow either of the options to configure line keys now:

  - If you enable Device Profile Template, use the **Phones tab** to configure line keys on touch and non-touch devices and **Sidecar tab** for connected sidecar devices. Complete the remaining steps below to configure line keys:
  
    - Using the drop-down choose the device or sidecar model you wish to configure line keys for.
    
    - Assign line keys for each position. If the model chosen is a touch device, speed dials, shared line and call queues are available to be assigned. If the model chosen is a non-touch device, only speed dials are available to be assigned. For sidecars connected to touch devices, speed dials, shared line and call queues are available to be assigned.
    
  - If you do not enable Device Profile Template, simply assign line keys for positions you wish to use.
  
- **Save** the configuration profile. 

- **Apply** the configuration profile to selected devices. 

