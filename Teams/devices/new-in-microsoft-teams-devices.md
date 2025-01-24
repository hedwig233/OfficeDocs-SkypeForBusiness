---
title: Release notes for devices in Microsoft Teams
author: mstonysmith
ms.author: tonysmit
manager: pamgreen
ms.reviewer: eviegrimshaw
ms.date: 01/23/2025
ms.topic: article
ms.service: msteams
ms.subservice: itpro-devices
audience: Admin
appliesto:
  - Microsoft Teams
ms.collection:
  - teams-rooms-devices
  - Teams_ITAdmin_Devices
  - Tier1
f1.keywords:
  - CSH
ms.localizationpriority: medium
search.appverid: MET150
description: Learn about what's new in Microsoft Teams devices.
---

# What's new in Microsoft Teams devices

This article contains updates for Microsoft Teams devices. To view feature updates for Microsoft Teams desktop, web, or mobile, go to [What's new in Microsoft Teams](https://support.microsoft.com/office/what-s-new-in-microsoft-teams-d7092a6d-c896-424c-b362-a472d5f105de).

To view feature updates for Microsoft Teams Rooms, go to:

- [Release notes for Microsoft Teams Rooms on Windows](../rooms/rooms-release-note.md)
- [Release notes for Microsoft Teams Rooms on Android](../rooms/rooms-release-note.md)

## [Teams panels](#tab/panels)

Insert information from Support article here.

## [Teams Phones](#tab/phones)

### January 8, 2024

#### Teams app version: 1449/1.0.94.2024122303 (Poly, Yealink, AudioCodes)

##### Queues app

We're excited to announce the Queues app for desk phones, a Teams solution that empowers organizations to efficiently manage customer engagements, starting with calls on certified Teams Phones. The experience is primarily for agents and includes a dedicated Queues app on the home screen. This app allows agents to view and opt in or out of all the call queues an agent is part of. Agents can also view others on the line along with call history of the call queue.

[Screenshot 1?]
[Screenshot 2?]

> [!NOTE]
> - The Queues app is enabled by default for all Teams users in your organization who are assigned both a Teams Premium and Teams Phone license and who are voice enabled. To learn more about managing the Queues app, see [Manage Queues app for Microsoft Teams](../manage-queues-app.md).

##### Circular delegation

Circular delegation now allows users to share lines with each other as a group on Teams Phone devices. This feature is useful for scenarios where multiple users need to manage shared lines. In a typical circular delegation setup, User A delegates to User B, and User B delegates to User A, allowing them all to share the line with each other. This setup can be configured using cmdlets because the Teams client and Teams Admin Center don't currently support this feature. ​​​​​​​

##### Multi-banner updates

The multiple-banners feature improves the user experience by managing notifications more effectively on phone devices. When users receive multiple notifications, the system allows users to collapse all notifications or clear them in bulk, providing a cleaner and more organized interface.

### December 18, 2024

#### Teams app version: 1449/1.0.94.2024121004 (Poly, Yealink, AudioCodes)

- Bug fixes related to transfer flow, among other issues.

### December 18, 2024

#### Teams app version: 1449/1.0.94.2024063004 (Yealink T5x/CP960, AudioCodes C488HD/450HD, Yealink MP52/VP59, Crestron UC-P8/ UC-P8-C/ UC-P10/ UC-P10-C/ UC-2)

- Banner notifications to inform users about their device support coverage status.

### December 10, 2024

#### Teams app version: 1449/1.0.94.2024112802  (Poly, Yealink, AudioCodes)​​​​​​​

- Bug fixes on lock screen, password expiration, LED issues on nontouch devices, among others, are included.

### November 25, 2024

#### Teams app version: 1449/1.0.94.2024062906 (Yealink – T5x, CP960, MP52, VP59; AudioCodes – C488HD/450HD, Crestron –UC-P8x, UC-P10x, UC-2)

- Bug fixes on several minor issues reported by customers.

### November 13, 2024

#### Teams app version: 1449/1.0.94.2024103101 (Touch phones – AudioCodes, Poly, Yealink)

- Bug fixes and improvements to line keys, calls, and Enhanced 911 calls, among others.

### October 29, 2024

#### Teams app version: 1449/1.0.94.2024101709 (Yealink, Poly, AudioCodes)

Today, on Teams Phone devices, you're able to configure custom contacts and speed dial on-the-line key buttons on nontouch phones and sidecars phone devices certified for Microsoft Teams. You can quickly access frequently dialed numbers and contacts, using one-touch dialing, as well as easy management of contact lists on both line keys and sidecars.

[Screenshot #3]

- Bug fixes and improvements on live captions.
- Privacy link updates for recordings and transcription.

### October 1, 2024

#### Teams app version: 1449/1.0.94.2024092304 (Yealink, Poly, AudioCodes)

- Bug fixes and improvements on contacts sync, presence, and transfer flows, among others.

### September 5, 2024

#### Teams app version: 1449/1.0.94.2024082806 (Yealink, Poly, AudioCodes)

- Enhancements in the call parking and retrieval feature to make both faster.
- Lightweight calling experience on nontouch phones.
- Bug fixes and improvements for compliance, recording scenarios, and other issues.

### September 3, 2024

#### Teams app version: 1449/1.0.94.2024062811 (Yealink T5x, CP960 & Poly Trio 8800/8500)

- Bug fixes and improvements for end-of-certification and end-of-best-effort support phones.

### August 27, 2024

### Teams app version: 1449/1.0.94.2024062702 (Yealink T5x, CP960 & Poly Trio 8800/8500)

- To support incoming call notifications and voicemail, migrate end-of-certification and end-of-best-effort support phones from the discontinued call-notification service to the new notification service.

This update also includes these features, which were already available for certified Teams Phones:

- Improvement was made to show caller information on incoming emergency call notification.
- The date-time format specified under Device Settings is the same on the home screen.
- When the Explicit Recording Consent policy is enabled, audio conference phones will support auto consent.
- The Public Switched Telephone Network (PSTN) calling issue on the new shared-line-appearance experience is fixed.
- When there are fewer than four apps on a given account, they'll now show on the home screen instead of being hidden under the More menu.
- Caller ID now shows incoming PSTN calls on call queues.
- You can now continue dialing a number when there's an incoming call.
- When ending a call or turning off your speaker, you won't be navigated to the home screen. Instead, you can continue from the previous screen.
- A new back button was introduced on the calling screen so you can easily navigate away from an ongoing call.
- View and join active calls handled by delegates as a delegator.
- Grant delegates permission to join active calls and resume calls.
- A delegate can view shared call history per a delegator's line, easily switch between different lines, and view other delegates managing a line.
- The presence on the device and sidecar gets updated in near real time.
- Live captions are supported on PSTN calls.
- You'll be able to program Teams Phone devices to autodial a preconfigured PSTN number, or directory contact, when the handset is picked up. You can configure a common-area phone as a hotline phone by navigating to **Settings** > **Device Settings** > **Calling** > **Hotline**, and specifying the autodial contact and display name.
- A redesigned dial pad helps reduce unnecessary mistakes while dialing a phone number. It offers a new dial-pad-only view in large-screen landscape phones.
- Simplified navigation improves the performance and reduces page-navigation time by replacing the bottom navigation bar with a new home screen navigation experience. You can easily go to the home screen from any app and navigate to different apps from the home screen. You can also use **More** to reorder apps.
- The user experience on the calls app and sidecar was made lighter weight to improve performance.
- Date and time are now displayed on the title bar across apps.
- Support added for reverse number lookup of PSTN numbers on call-queue calls.
- The issue of autodialing on a partially entered number is fixed.
- Option to sign out on common area phones. Advanced calling experience requires an Admin PIN.
- Lighter weight meeting reduces the time it takes users to get connected to a meeting on selecting **Join**.
- Support added for reverse number lookup of PSTN contacts added via the Teams desktop.
- Performance of the phones attached to expansion modules is improved.
- The "Resume call" reliability is improved on consult transfer.
- Audio conferencing isn't supported on Teams Phone devices with the Meeting Teams Room Basic license.
- You now have the option to add and edit your emergency location on phones.
- Emergency service disclaimers specified by admins in the Teams Admin Center (TAC) as part of emergency policy will be shown on the desk phones.
- Busy-on-busy when users are in a call setting enabled by admins in TAC will be honored on phone devices (excluding the User-controlled option).
- Admins can configure app restart settings from TAC for optimal phone performance (not currently available for Government cloud accounts).
- Record one-on-one PSTN calls.
- License enforcement.
- Faster call joining.

### August 16, 2024

#### Teams app version: 1449/1.0.94.2024080808

- Bug fixes and improvements on transfer scenarios, contacts, among others, are included.

### July 16, 2024

#### Teams app version -1449/1.0.94.2024071104​​​​​​​

- This app is available for government clouds (GCCH and DoD).
- **Updates on user experiences** We changed the default home-screen experience for the meeting sign-in mode. It's now like the personal sign-in mode experience. Additionally, updates have been made to remove the dial pad on the Calls app for touch phones with physical buttons.
- Explicit Consent for Recording** Users see a notification on Teams Phone devices when a participant starts recording or transcription, asking for participant consent. This feature is turned off by default but can be enabled by admins. Admins will have the option to turn on this policy for users in your tenant by clicking on the highlighted switch on "Require participant agreement for recording, transcription, and Copilot."

[Screenshot #4]

- **Private Line**  The Private Line feature allows bosses to have a second private phone number on their Teams device, ensuring privacy for important calls. These calls are distinct in the call history. To learn more, see Configure private lines in Microsoft Teams.
- **Lightweight People App**  The updated People app provides a faster and simplified experience for managing contacts, allowing users to switch between different contact lists and to create contact groups.​​​​​
- **Rich Call History**  Call-history updates include better logging for ignored, missed, and forwarded calls, with clear labeling for different call types.
- **Call Transfer Improvements**  Improvements to call transfers include viewing a list of speed dials during transfer, and better handling of keyboard overlap on touch phones. Also, for phones that don’t have touch screens, there are improvements to finish transfers using call-transfer hard keys on phones.

### July 5, 2024

#### Teams app version: 1449/1.0.94.2024062301 (AUDC: C448HD, C450HD. Yealink: MP52, VP59. Crestron: UC-2, UC-P8, UC-P10, UC-P8-C and UC-P10-C)

- Intermittent issue on meeting join while using Better Together is fixed for touch phones
- Intermittent issue on a device getting locked out is fixed for nontouch phones.
- Issue of remote user not hearing music while on hold in nontouch phones is fixed.
- Fixes for authentication issues, including a fix for sign-in failures immediately following signing out.
- Issue of pin lock appearing when disabled is fixed.

### July 3, 2024

#### Teams app version - 1449/1.0.94.2024062010 (touch phones: AudioCodes, Poly, Yealink. For non-touch phones: AudioCodes C435, Poly CCX350)

- Bug fixes and improvements on the enforce pin-lock feature.
- This app is also available for customers in government clouds (GCCH and DoD).

### June 18, 2024

#### Teams app version - 1449/1.0.94.2024061301

- Minor updates in the people and calls apps.
- Bug fixes and improvements.

### June 4, 2024

#### Teams App version: 1449/1.0.94.2024051306 (Touch phones – AudioCodes, Poly, Yealink)

- Bug fixes for crash issues.

### May 21, 2024

#### Teams App version: 1449/1.0.94.2024051306 (Non-touch phones – Poly CCX350, AudioCodes C435HD)

- You can park and unpark a call.
- You can turn on the Advanced Calling and Auto Restart settings.
- You can add contacts and contact groups.
- Admin’s can turn on call forwarding on home screens via **Teams admin center** > **Configuration** > **Display call forwarding on home screen**, allowing Teams Phone device users to setup call forwarding directly from their home screens.
- Admin’s have the option to turn off call-quality surveys on Teams Phone devices from **Teams admin center** > **Configuration**, and by turning off **Call quality survey**.

[Screenshot #5]

- Send incoming calls to voicemail from the incoming call screen (configurable by calling a policy through PowerShell). You can control how you want to handle a secondary incoming call through the Busy-on-Busy setting (configurable by calling a policy in the Teams admin center).
- When a contact has multiple numbers, you can choose which one to call.
- People can control how they want to handle second incoming calls through the Busy-on-Busy setting. Admins can allow people to configure the Busy-on-Busy setting by selecting **Let users decide** in **Teams admin center** > **Calling policy**.

[Screenshot #6]

### May 5, 2024

#### Teams app version: 1449/1.0.94.2024042905 (Touch Phones - AudioCodes, Poly, Yealink)

- Send incoming calls to voicemail from the incoming call screen.

[Screenshot #7, maybe not good enough to keep]

> [!NOTE]
> Admins can control roll out of this option on selected accounts by configuring the AllowCallRedirect parameter in the Teams calling policy associated with the account. [Screenshot #8, maybe not good enough to keep]

- People can control how they want to handle a second incoming call through the Busy-on-Busy setting. Admins can allow people to configure the Busy-on-busy setting by selecting **Let users decide** in **Teams admin center** > **Calling policy**.

[Screenshot #9]
[Screenshot #10]

- Admins can allow call the forwarding option on home screens via **Teams admin center** > **Configuration** by turning on **Display call forwarding on home screen.** The same setting can be configured on the phone device. This allows people using a device (including common-area phones) to set up call forwarding directly from their home screen.

> [!NOTE]
> These features will be rolled out gradually.

- Admins can notify people to set or change their phone lock PIN by enabling a configuration profile setting in Teams admin center. They can also lock the phone device via the menu on home screen.

[Screenshot #11]

> [!NOTE]
> These features will be rolled out gradually.

- Survival Branch Office (SBA) will be supported on Voice over Internet Protocol (VoIP) calls.
- Admins have the option of disabling call-quality surveys on Teams Phone devices from **Teams admin center** > **Configuration**.

[Screenshot #12]

> [!NOTE]
> These features will be rolled out gradually.

- The issue of Better together on the new Teams desktop app is fixed.
- After consult transfer, the issue of an ongoing call going to the banner for the remote caller is fixed.  

### March 15, 2024

#### Teams App version: 1449/1.0.94.2024031102 (Yealink, Poly, AudioCodes)

> [!NOTE]
> For AudioCodes phones, this app update applies to firmware version 1.19.705.

- Improvement to show caller information on incoming emergency call notification.
- Issue of not ending hot-desk on timeout is fixed.
- Issue of showing an incorrect call-recording string and a localized calling string is fixed.
- Issue related to the hard-key hold button is fixed.

### March 12, 2024

#### Teams App version: 1449/1.0.94.2024011601, 1449/1.0.94.2024020601 (AudioCodes)

> [!NOTE]
> The update applies to AudioCodes phones on firmware version 1.19.516 or higher.

- Significant reduction in sign-out and authentication errors due to Workplace Join failures, timeout issues, and memory leaks.


## [Teams displays](#tab/displays)

Insert information from Support article here.
