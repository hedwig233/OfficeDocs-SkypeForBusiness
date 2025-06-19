---
title: Teams devices management apps
author: mstonysmith
ms.author: tonysmit
manager: pamgreen
ms.reviewer: vapati
ms.date: 03/03/2025
ms.topic: article
audience: Admin
appliesto:
  - Microsoft Teams
ms.service: msteams
ms.subservice: itpro-devices
ms.collection: 
  - teams-rooms-devices
  - Teams_ITAdmin_Devices
  - Tier2
f1.keywords: 
  - NOCSH
search.appverid: MET150
ms.localizationpriority: medium
description: Learn about the versions of Android-based management apps that are supported on Android-based Teams devices including the Teams admin agent app, the Intune app, and the Microsoft Authenticator app.
---
# Teams devices management apps

This article provides the details about the releases of following apps for Android-based Teams devices:

- Teams admin agent app
- Intune app
- Microsoft Authenticator app

For more information on updating your Teams devices remotely, see [Update Microsoft Teams devices remotely](/microsoftteams/devices/remote-update).

For product release information about firmware and Teams app, refer to the following:

- [Release notes for Microsoft Teams Rooms](/microsoftteams/rooms/rooms-release-note?tabs=Android)

- [What's new in Microsoft Teams devices](https://support.microsoft.com/office/what-s-new-in-microsoft-teams-devices-eabf4d81-acdd-4b23-afa1-9ee47bb7c5e2)

- [Devices for Teams](/microsoftteams/devices/teams-ip-phones#product-release-information-for-teams-phones)

> [!NOTE]
> The following releases contains details for apps released after 1st October 2024.
## [Teams admin agent](#tab/Agent)

The following are supported versions of Teams admin agent app:

|**Release date**|**App version**|**Related devices**|
|:-----|:-----|:-----|
|October 1, 2024|[1.0.0.202407050618.product](#100202407050618)|All certified Teams device models |
|February 10, 2025|[1.0.0.202412110504.product](#100202412110504)|All certified Teams device models|
|May 19, 2025|[1.0.0.202505080136.product](#100202505080136) (Hotfix)|All certified Teams device models (except Logitech devices)|

### 1.0.0.202407050618

**This release is currently available for all Teams certified devices and contains following updates:** 

- Improvements to determine device health more appropriately with the help of additional signals.

- Improvements for better management of configurations for devices.

- Bug fixes to improve admin agent overall update reliability.

### 1.0.0.202412110504

**This release is currently available for all Teams certified devices and contains following updates:**

- Improvements to device settings management by supporting partial configuration change and two-way sync of settings between Teams admin center and device.

- Improvements to carry out operations like updates, configuration changes in a non-disruptive manner.

- IP address support for Cisco devices.

- Bug fixes to improve admin agent for better management of android devices.

### 1.0.0.202505080136

**This release (hotfix) is currently available for all Teams certified devices (except Logitech devices) and contains following updates:**

- Bug fixes for critical security issue.

## [Intune](#tab/Intune)

The following are supported versions of the Intune app:

|**Release date**|**App version**|**Related devices**|
|:-----|:-----|:-----|
|January, 2025|[25.02.1](#25021)|All certified Teams device models|

### 25.02.1

**This release is currently available for all Teams certified devices and contains following updates:** 

- Telemetry improvements for more efficient investigations

- Customers using Conditional Access policies should first deploy the updated AOSP Agent to a small group of devices and confirm Conditional Access continues to work as expected, before deploying the updated AOSP Agent to your entire device fleet.

## [Microsoft Authenticator](#tab/Authenticator)

The following are supported versions of the Microsoft Authenticator app:

|**Release date**|**App version**|**Related devices**|
|:-----|:-----|:-----|
|June, 2025|[6.2505.3166](#625053166)|All certified Teams device models|

### 6.2505.3166

**This release is currently available for all Teams certified devices and contains following updates.**

_Note: This version is a hotfix release targeted specifically at resolving ANR (App Not Responding) issues observed in a limited set of environments using the May 2024 GA candidate._ 

- Fixed __App Not Responding (ANR)__ issues during sign-in and device provisioning flows.

- Improved __Multi-Factor Authentication (MFA)__ upgrade prompt experience.

- Built on stable baseline: __GA candidate version 6.2410.__ 

- This version includes a __validated and stable broker version: 13.3.2__ and __common library: 17.3.1__.

## Related articles
- [Microsoft Teams certified Android devices](/microsoftteams/devices/teams-ip-phones)
- [Teams Rooms certified systems and peripherals](/microsoftteams/rooms/certified-hardware?tabs=Windows#teams-rooms-for-android-certification-program)
- [Product release information for Microsoft Teams Rooms on Android](/microsoftteams/rooms/android-app-firmware)

- [Personal peripherals certified for Microsoft Teams](/microsoftteams/devices/usb-devices)
