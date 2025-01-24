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

#### Teams app version: 1449/1.0.94.2024062702 (Yealink T5x, CP960 & Poly Trio 8800/8500)

- To support incoming call notifications and voicemail, migrate end-of-certification and end-of-best-effort support phones from the discontinued call-notification service to the new notification service.

This update also includes these features, which were already available for certified Teams Phones:

- Improvement was made to show caller information on incoming emergency call notification.
- The date-time format specified under Device Settings is the same on the home screen.
- When the **Explicit Recording Consent** policy is enabled, audio conference phones support auto consent.
- The Public Switched Telephone Network (PSTN) calling issue on the new shared-line-appearance experience is fixed.
- When there are fewer than four apps on a given account, they appear on the home screen instead of being hidden under the More menu.
- Caller ID now shows incoming PSTN calls on call queues.
- You can now continue dialing a number when there's an incoming call.
- When ending a call or turning off your speaker, you won't be navigated to the home screen. Instead, you can continue from the previous screen.
- A new back button was introduced on the calling screen so you can easily navigate away from an ongoing call.
- View and join active calls handled by delegates as a delegator.
- Grant delegates permission to join active calls and resume calls.
- A delegate can view shared call history per a delegator's line, easily switch between different lines, and view other delegates managing a line.
- The presence on the device and sidecar gets updated in near real time.
- Live captions are supported on PSTN calls.
- You can program Teams Phone devices to autodial a preconfigured PSTN number, or directory contact, when the handset is picked up. You can configure a common-area phone as a hotline phone by navigating to **Settings** > **Device Settings** > **Calling** > **Hotline**, and specifying the autodial contact and display name.
- A redesigned dial pad helps reduce unnecessary mistakes while dialing a phone number. It offers a new dial-pad-only view in large-screen landscape phones.
- Simplified navigation improves the performance and reduces page-navigation time by replacing the bottom navigation bar with a new home screen navigation experience. You can easily go to the home screen from any app and navigate to different apps from the home screen. You can also use **More** to reorder apps.
- The user experience on the calls app and sidecar was made lighter weight to improve performance.
- Date and time are now displayed on the title bar across apps.
- Support added for reverse number lookup of PSTN numbers on call-queue calls.
- The issue of autodialing on a partially entered number is fixed.
- Option to sign out on common area phones. Advanced calling experience requires an admin PIN.
- Lighter weight meeting reduces the time it takes users to get connected to a meeting on selecting **Join**.
- Support added for reverse number lookup of PSTN contacts added via the Teams desktop.
- Performance of the phones attached to expansion modules is improved.
- The "Resume call" reliability is improved on consult transfer.
- Audio conferencing isn't supported on Teams Phone devices with the Meeting Teams Room Basic license.
- You can add and edit your emergency location on phones.
- Emergency service disclaimers specified by admins in the Teams Admin Center (TAC) as part of emergency policy will be shown on the desk phones.
- Busy-on-Busy when users are in a call setting enabled by admins in TAC will be honored on phone devices (excluding the User-controlled option).
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
- **Updates on user experiences** We changed the default home-screen experience for the meeting sign-in mode. It's now like the personal sign-in mode experience. Additionally, updates to remove the dial pad on the Calls app for touch phones with physical buttons.
- **Explicit Consent for Recording**  Users see a notification on Teams Phone devices when a participant starts recording or transcription, asking for participant consent. This feature is turned off by default but can be enabled by admins. Admins can turn on this policy for users in your tenant by clicking on the highlighted switch on "Require participant agreement for recording, transcription, and Copilot."

[Screenshot #4]

- **Private Line**  The Private Line feature allows bosses to have a second private phone number on their Teams device, ensuring privacy for important calls. These calls are distinct in the call history. To learn more, see Configure private lines in Microsoft Teams.
- **Lightweight People App**  The updated People app provides a faster and simplified experience for managing contacts, allowing users to switch between different contact lists and to create contact groups.​​​​​
- **Rich Call History**  Call-history updates include better logging for ignored, missed, and forwarded calls, with clear labeling for different call types.
- **Call Transfer Improvements**  Improvements to call transfers include viewing a list of speed dials during transfer, and better handling of keyboard overlap on touch phones. Also, for phones that don’t have touch screens, there are improvements to finish transfers using call-transfer hard keys on phones.

### July 5, 2024

#### Teams app version: 1449/1.0.94.2024062301 (AUDC: C448HD, C450HD. Yealink: MP52, VP59. Crestron: UC-2, UC-P8, UC-P10, UC-P8-C, and UC-P10-C)

- Intermittent issue on meeting join while using Better Together is fixed for touch phones
- Intermittent issue on a device getting locked out is fixed for nontouch phones.
- Issue of remote user not hearing music while on hold in nontouch phones is fixed.
- Fixes for authentication issues, including a fix for sign-in failures immediately following signing out.
- Issue of pin lock appearing when disabled is fixed.

### July 3, 2024

#### Teams app version - 1449/1.0.94.2024062010 (touch phones: AudioCodes, Poly, Yealink. For nontouch phones: AudioCodes C435, Poly CCX350)

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

#### Teams App version: 1449/1.0.94.2024051306 (Nontouch phones – Poly CCX350, AudioCodes C435HD)

- You can park and unpark a call.
- You can turn on the Advanced Calling and Auto Restart settings.
- You can add contacts and contact groups.
- Admin’s can turn on call forwarding on home screens via **Teams Admin Center** > **Configuration** > **Display call forwarding on home screen**, allowing Teams Phone device users to setup call forwarding directly from their home screens.
- Admin’s can turn off call-quality surveys on Teams Phone devices from **Teams Admin Center** > **Configuration**, and by turning off **Call quality survey**.

[Screenshot #5]

- Send incoming calls to voicemail from the incoming call screen (configurable by calling a policy through PowerShell). You can control how you want to handle a secondary incoming call through the Busy-on-Busy setting (configurable by calling a policy in the Teams Admin Center).
- When a contact has multiple numbers, you can choose which one to call.
- People can control how they want to handle second incoming calls through the Busy-on-Busy setting. Admins can allow people to configure the Busy-on-Busy setting by selecting **Let users decide** in **Teams Admin Center** > **Calling policy**.

[Screenshot #6]

### May 5, 2024

#### Teams app version: 1449/1.0.94.2024042905 (Touch Phones - AudioCodes, Poly, Yealink)

- Send incoming calls to voicemail from the incoming call screen.

[Screenshot #7, maybe not good enough to keep]

> [!NOTE]
> Admins can control rollout of this option on selected accounts by configuring the AllowCallRedirect parameter in the Teams calling policy associated with the account. [Screenshot #8, maybe not good enough to keep]

- People can control how they want to handle a second incoming call through the Busy-on-Busy setting. Admins can allow people to configure the Busy-on-Busy setting by selecting **Let users decide** in **Teams Admin Center** > **Calling policy**.

[Screenshot #9]
[Screenshot #10]

- Admins can allow call the forwarding option on home screens via **Teams Admin Center** > **Configuration** by turning on **Display call forwarding on home screen.** The same setting can be configured on the phone device. This allows people using a device (including common-area phones) to set up call forwarding directly from their home screen.

> [!NOTE]
> These features will be rolled out gradually.

- Admins can notify people to set or change their phone lock PIN by enabling a configuration profile setting in Teams Admin Center. They can also lock the phone device via the menu on home screen.

[Screenshot #11]

> [!NOTE]
> These features will be rolled out gradually.

- Survival Branch Office (SBA) will be supported on Voice over Internet Protocol (VoIP) calls.
- Admins have the option of disabling call-quality surveys on Teams Phone devices from **Teams Admin Center** > **Configuration**.

[Screenshot #12]

> [!NOTE]
> These features will be rolled out gradually.

- The issue of Better Together on the new Teams desktop app is fixed.
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

### January 24, 2024

#### Teams App version: 1449/1.0.94.2024011003 (Poly, Yealink, Crestron, AudioCodes)

- The issue of active call moving to banner on merging a call is fixed.
- The issue of consult transfer icon not being clickable sometimes is fixed.

> [!NOTE]
> This update applies to AudioCodes phones on firmware versions 1.19.456 and earlier.

### December 5, 2023

#### Teams App version: 1449/1.0.94.2023112704 (Crestron, Poly, Yealink)

- The date and time format specified under **Device Settings** is the same on the home screen.
- When the **Explicit Recording Consent** policy is enabled, audio conference phones support auto consent.
- The PSTN calling issue on the new shared line appearance experience is fixed.
- When there are less than four apps on a given account, they appear on the home screen instead of being hidden under the **More** menu.

### November 28, 2023

#### Teams app version: 1449/1.0.94.2023111407 (AudioCodes)

> [!NOTE]
> This update applies to AudioCodes phones on firmware version 1.19.584.

- Improvements to reduce issues with workplace join authentication.

### November 6, 2023

#### Teams app version: 1449/1.0.94.2023100602 (AudioCodes)

> [!NOTE]
> This update applies to AudioCodes firmware version 1.19.584 and is available for phones previously on firmware version 1.19.516. A Teams app release for AudioCodes phones currently on other firmware versions will be released soon.

- Enhanced call-delegation experience, faster presence update in the app, and live captions on PSTN calls. For a list of call-delegation updates, see the August 29, 2023, update.

### October 9, 2023

#### Teams App version: 1449/1.0.94.2023091801 (Yealink)

- Caller ID shows for incoming PSTN calls on call queues.
- You can continue dialing a number when there's an incoming call.
- When ending a call or turning off your speaker, you won't be navigated to the home screen. Instead, you can continue from previous screen.
- A new back button on the calling screen which allows you to easily navigate away from an ongoing call.

### August 29, 2023

#### Teams app version: 1449/1.0.94.2023082303 (Crestron, Poly, and Yealink Audio Touch Phones)

Today, on Teams Phone devices, delegators can share their phone line with their assistants and delegates to make and receive calls on their behalf. Call delegates can also:

- View and join active calls handled by delegates, as a delegator.
- Grant delegates permission to join active calls, and resume calls.
- View shared call history, per the delegator's line.
- Easily switch between different lines.
- View other delegates managing a line.
- The presence on the device and sidecar is updated in near real time.
- Live captions are supported on PSTN calls.
- The issue of resolving caller ID on call-queue calls is fixed.
- The issue of showing the "Add location" banner when the emergency policy "External location lookup mode" is turned off is fixed.

### July 31, 2023

#### Teams app version: 1449/1.0.94.2023072509 (AudioCodes, Crestron, and Poly audio phones)

- You can program Teams Phone devices to autodial a preconfigured PSTN number or directory contact when the handset is picked up. You can configure a common area phone as a hotline phone by navigating to **Settings** > **Device Settings** > **Calling** > **Hotline** and specifying the auto-dial contact and display name.

> [!NOTE]
> To configure a phone as hotline phone, the logged in account on the phone device must have **Teams Shared Device License** assigned. **Sign In Mode** must be set to **CommonAreaPhoneSignIn**. The option to configure a hotline phone through the Teams Admin Center will be supported soon.

- Redesigned dial pad helps reduce unnecessary mistakes while dialing a phone number and offers a new dial-pad-only view in large-screen landscape phones.
- Simplified navigation improves performance and reduces page-navigation time by replacing the bottom navigation bar with a new home-screen navigation experience. You can easily go to the home screen from any app and navigate to different apps from the home screen. You can also use **More** to reorder apps.
- The user experience on the calls app and sidecar was made lightweight to improve performance.
- Date and time are now displayed on the title bar across apps.
- Support added for reverse number lookup of PSTN numbers on call-queue calls.
- The issue of autodialing on partially entered number is fixed.
- Option to sign-out on common area phones. The advanced calling experience requires an admin PIN.
- Lightweight meeting reduces the time it takes users to get connected to a meeting by selecting **Join**.

### July 12, 2023

#### Teams app version: 1449/1.0.94.2023063003

- Support added for reverse-number lookup of PSTN contacts added via Teams desktop.
- Performance of the phones attached to expansion modules is improved.

### June 15, 2023

#### Teams app version: 1449/1.0.94.2023060906

- Audio Conferencing is supported on the Microsoft Teams Room Pro License.

> [!NOTE]
> When multiple licenses are assigned to a Teams Phone device account, configure IPPhonePolicy and SignInMode for the desired experience.

- Issue of displaying wrong caller information for incoming Auto Attendant Call Queue calls is fixed on nontouch screen phones.

### May 9, 2023

#### Teams app version: 1449/1.0.94.2023050205 (doesn't include TrioC60 on GCC-H cloud)

- "Resume call" reliability is improved on consult transfer.
- Issue of persisting "Advanced calling" setting in common area phones when signing back in is fixed.
- The intermittent issue of an emergency location banner showing on the phone when "External location lookup mode" is disabled in the Teams Admin Center is fixed.
- Intermittent issue of badge notifications not clearing on the home screen is fixed.

### April 14, 2023

#### Teams app version: 1449/1.0.94.2023041203

- Intermittent issue of the app restarting on F SKUs (frontline worker) and Business SKUs (SMB) is fixed.

### April 4, 2023

#### Teams app version: 1449/1.0.94.2023032903 (AudioCodes, Crestron, Poly)

- Audio conferencing isn't supported on Teams Phone devices with the Meeting Teams Room Basic License.
- You can add and edit your emergency location on phones.
- Emergency service disclaimers specified by admins in the Teams Admin Center (TAC) as part of the emergency policy shown on desk phones.
- Busy-on-Busy when in a call setting enabled by admins in the Teams Admin Center is honored on phone devices (excluding the User controlled option).
- Admins can configure app-restart settings from the Teams Admin Center for optimal phone performance (not currently available for Government cloud accounts).
Record one-on-one PSTN calls
- Faster call joining.
- Issue of defaulting to alphanumeric characters on the Dialpad while dialing a number on Poly CCX 350 is fixed.
- Intermittent issue of boss not getting notification when delegates put a call on hold is fixed.
- Intermittent issue of screen freezing while in a call is fixed.

### February 21, 2023

#### Teams app version: 1449/1.0.94.2023020602

- Dial tone and mute LED sync issue is fixed on audio-conferencing phones.
- Calling resiliency is improved.
- Intermittent issue around greying out of call controls is fixed.
- Intermittent issue around not being able to end calls is fixed.

### January 25, 2023

#### Teams app version: 1449/1.0.94.2023010607

> [!NOTE]
> This update is for public cloud deployments and non-audio-conferencing phones.

- Reliability improvements around authentication.
- Showing detailed error messages around authentication.
- Call button display issue is fixed.
- Emergency notification issue is fixed.

### November 30, 2022

#### Teams app version: 1449/1.0.94.2022110803

- Fixes sign-in issues on nontouch devices.
- Fixes caller ID and caller display name issues.
- Fixes calling related issues on GCCH deployments.

### September 21, 2022

#### Teams app version: 1449/1.0.94.2022090705 (for nonvideo touch phones only)

- Simplified look for incoming and outgoing calls with improved performance.

### July 14, 2022

#### Teams app version: 1449/1.0.94.2022062103

- Several intermittent app-crash issues have been resolved.

### July 6, 2022

#### Teams app version: 1449/1.0.94.2022061702 (Crestron, Poly, Yealink)

- We're enhancing the existing Common Area Phone offering to include all advanced calling features at no extra cost or changes to the original purchased license. Common Area Phone supports calling features including call park, call queues, auto attendants, Intune enrollment into Endpoint Manager, and more, when the device is updated to the minimum app version: 1449/1.0.94.2022061702.
- Emergency calling on GCC-H deployments is supported.

### April 13, 2022

#### Teams app version: 1449/1.0.94.2022041102

- Fixes missing names on phone sidecars.
- Fixes common-area phone dial pad and audio routing issues between the handset and speaker.
- Fixed issues occurring in the Teams Admin Center.

### March 24, 2022

#### Teams app version: 1449/1.0.94.2022030501

- Support end-to-end encryption in one-on-one calls.
- Contact name along with phone number for saved contacts show on calls made via PSTN (Public Switched Telephone Network).
- Hold music during blind-call transfers and consultative-call transfers made via VoIP (Voice over Internet Protocol).
- Customize app restart time from **Settings**.

### March 3, 2022

#### Teams app version: 1449/1.0.94.2022022305

- Resiliency added for location fetch mechanism on devices.

### February 7, 2022

#### Teams app version: 1449/1.0.94.2022020202

- Teams Phones with touch screen have instant push-to-talk communication via the new Walkie-Talkie feature.
- Teams Phones with touch screen improvements for multiple incoming, held, and parked calls.
- Teams conference phones in portrait mode updates for better meeting experience.
- Performance enhancements for screen navigation and sidecar issues.
- Bug fixes for Teams Android devices showing as offline in Teams Admin Center.
- Bug fix to held calls when placing the handset back in the cradle.
- Known issues with ongoing calls when Walkie-Talkie calls interrupt.

### December 16, 2021

#### Teams app version: 1449/1.0.94.2021121302

- More improvements in dial-pad experience for touch-screen phones.
- Improvements in dial-tone management.
- Improvements to audio routing when switching between handset and speaker.

### December 6, 2021

#### Teams app version: 1449/1.0.94.2021112302

- More improvements in dial-pad experience for touch-screen phones.
- Improvements in dial-tone management.
- Improvements to audio routing when switching between handset and speaker.

### November 22, 2021

#### Teams app version: 1449/1.0.94.2021110101

- Improvements in dial-pad and dial-tone experiences for touch-screen phones.

### November 3, 2021

#### Teams app version: 1449/1.0.94.2021101205

- Admins can provision devices from the Teams Admin Center to remotely sign in and sign out from devices.
- Branch office survivability for Teams Phones to make PSTN calls even when the internet connection is down.
- Admins can download all (company portal, device management, and media) logs from the Teams Admin Center.
- Bug fixes related to authentication.
- Bug fixes preventing devices from going offline in the Teams Admin Center.

### June 10, 2021

#### Teams app version: 1449/1.0.94.2021052803

- Performance updates for meeting experiences on low-end hardware.

### June 8, 2021

#### Teams app version: 1449/1.0.94.2021051303

- Transfer a Teams call to another device without hanging up.
- Change your background during a video call or meeting from a set of pictures available in phones with video capability.
- Contacts whose numbers are saved in Outlook are available in the People section of Teams Phones with read-only access. You need to manually dial the number.
- Enforcement of authentication policies and tenant-based policies set by your admin. Login is blocked if the device doesn't meet the necessary policy requirements.
- During a call, select the active-call icon to show more options. Additionally, when a contact has multiple numbers saved, you can choose the number you want to dial from the dropdown list.
- To facilitate quick responses for autoattendant scenarios, dial pad is available for early media scenarios.
- Extending the live captions feature to calls, Teams detects what's said in a call and presents real-time captions in one-on-one calls.
- Ongoing enhancements to improve user experience when using a delegate on touch screens.
- Bug fixes for Link Layer Discovery Protocol (LLDP) for Enhanced 911 (E911) and authentication.

### March 30, 2021

#### Teams app version: 1449/1.0.94.2021033002

- Fixed authentication library crash.

### March 26, 2021

#### Teams app version: 1449/1.0.94.2021022403

- New and improved sign-in experience. Sign in from any browser or smartphone with a prominent device code. Or you can sign in from the device with your username and password.
- Sign-in support and authentication into specialized clouds is available. Choose the **Settings** gear on the sign-in page to see the options for your account.
- IT admins can remotely provision and sign in to a Teams device that's previously not been provisioned.
- Call controls now visible during meetings. You can also switch between Gallery and Together mode and send reactions during meetings.
- Teams devices connected to the network via ethernet will dynamically update location information for emergency calling services based on changes to network attributes, including chassis ID and port ID.
- On video phones, you can change your background during meetings and calls from a select set of images.
- Calling enhancements that improve the usability of touch screens.
- All phone numbers that are part of meeting invites, or from a person’s contact card, can be dialed by selecting them on screen.
- Directly transfer a call to someone’s work voicemail without ringing them.

### December 8, 2020

#### Teams app version: 1449/1.0.94.2020111101

- Video features including 3x3 layout support, gallery view and together mode, background blur, and spotlight.
- Meeting features including request-to-speak and the ability to view screen sharing on select models of audio phones.
- Proximity joining on conference phones.
- Beta release for Sidecars on AudioCodes and Yealink phones.
- Meet-now button on phones.
- Policy support for enabling and disabling home screen and syncing a phone to a computer.
- Support for M365 Government (GCC deployments).

### October 12, 2020

#### Teams app version: 1449/1.0.94.2020091801

- Better-together feature with meeting support.
- Bug fix related to authentication after signing in.
- Bug fix related to device automatically signing out after 90 days.

### August 31, 2020

#### Teams app version: 1449/1.0.94.2020071702

- Home screen shows meeting reminders.
- Ability to customize default apps in the phone and the default view in Calls.
- Support for a Teams button on specific phone models.
- Enable auto accept with video for prescheduled meeting requests.
- Sign-in enhancements with the Company Portal application.
- Bug fixes to the Teams application and the Device management admin-agent application.

> [!NOTE]
> If the phone is stuck on the "Verifying a few things" screen, try turning the phone off and on again.

### June 27, 2020

#### Teams app version: 1449/1.0.94.2020051601

- Contacts and contact groups management in People.
- Live captions for meetings.
- Raise virtual hand in meetings.
- Transfer directly to speed dial.
- Connect to computer for simultaneous lock and unlock.
- Auto dismiss for a call ended and rate-my-call screens.
- Network banner at the top of screen to show network loss.
- Bug fixes to the Teams application and the Device management admin-agent application.

### April 23, 2020

#### Teams app version: 1449/1.0.94.2020031901

- Favorites (speed dial) added to Calls.
- New settings support on Teams Phones for: Custom ringtone, Manage Delegates, and auto dial for extension dialing.
- Device-management updates to support device categorization in Teams Admin Center.
- Bug fixes to the Teams application and the Company Portal application.

### February 18, 2020

#### Teams app version: 1449/1.0.94.2020020601

- Support for dynamic emergency calling on the phone lock screen.
- Hot-desk feature bug fixes to address network-outage scenarios.
- Sign-in improvements.
- Device-management bug fixes to address firmware version reporting.
- Bug fixes to the Teams application.


## [Teams displays](#tab/displays)

> [!IMPORTANT]
> End of certification for Teams display devices is September 3, 2025. Microsoft will make commercially reasonable best efforts to maintain compatibility with the most recent version of the Teams apps provided to manufacturers for a period of two (2) years from this date. For details, see the [Microsoft Product and Services Lifecycle](/lifecycle/products/).

### September 2024

#### Teams app version: 1449/1.0.95.2024062804

- Bug fixes.

### November 2023

#### Teams app version: 1449/1.0.95.2023101102

- Support for QR code sign in for scenarios without reserving the hot desk.
- Improvements to support meeting continuity through hot-desk reservation end times.
- UI and layout enhancements to the hot-desk ambient and display screen.
- Bug fixes and other enhancements.

### June 2023

#### Teams app version: 1449/1.0.95.2023061601

- Streamlined experiences on Teams-certified displays based on assigned licenses.
- Bug fixes and improvements on meeting and calling experiences.

### May 2023

#### Teams displays app version: 1449/1.0.95.2023042701

> [!NOTE]
> This release is an app-only update. Please work with device manufacturers to confirm timelines on full feature functionality on your devices.

- QR code sign in on Teams-certified displays for hot-desking. All Teams Displays with hot-desking capability allow people to sign in using a QR code for a reserved time slot. This feature is enabled by default and can be disabled under **Device settings** > **Admin settings** > **Meetings**. While hot-desking, you can seamlessly sign in to the Teams display for the duration of your session by scanning a QR code using the Teams app on your mobile phone.

The recommended version of Teams on your Android phone is 1416/1.0.0.2023092901 and above. On iOS, the recommended version is 5.9.1, it's (100772023093201), and above.

> [!NOTE]
> The following instructions are for those who use an Android mobile phone with an Android work profile (AWP).

- You can scan a QR code using the camera app on your Android mobile phone. However, the sign-in might not work if you have both work and personal profiles on their Android phones. If this is the case, you need to add a mobile system OS scanner in your work profile.

To add a mobile system OS scanner:

1. In the Intune Admin Center go to **Apps** > **Android**, and add.

2. Select **Android enterprise system app**.

3. Enter the type of Android phone, Google, and paste OS camera package name.

4. Assign it to an individual or group.

5. Download and install the camera app from the app store in your work profile.

- **Virtual front-desk experience on Teams-certified displays**  The Virtual front desk enables staff to greet and serve visitors or employees via video call on a Teams display.  It can be used for virtual reception, helpdesk, and a variety of use cases across industries. IT admins can easily configure the Virtual front desk with contact and routing information. This feature is available on Teams certified displays on the Teams Shared Devices License. It's recommended for accounts without CA policies.
- Admins can now customize the message on display screens and the call button, in addition to configuring a PSTN or VoIP contact on the device itself via **Settings**. They can also use Teams advanced calling capabilities such as call transfer, call forwarding, call queues, etc., if enabled for the configured contact account.
- Improvements to handle multi-call banner scenarios and to ambient UI.
- Bug fixes and improvements.

### January 2023

#### Teams app version: 1449/1.0.95.2023011001 (Crestron)

- Fix for intermittent app crashes occurring in the previous app update (1449/1.0.95.2022102603) for Crestron devices.

### December 2022

#### Teams app version: 1449/1.0.95.2022120505 (Neat Frame)

- Hot desking in portrait mode is  supported. Hotdesking on a Teams display makes finding a space to work easier by allowing you to locate and reserve flexible workspaces.
- Teams Shared Devices License on Teams displays offers hot desking experience. The Teams IP Phone policy setting for hot desking is disabled for displays. You can invoke hot desking using Teams accounts with the Teams Shared Device Licenses.
- Bug fixes and improvements for app crashes.

### November 2022

#### Teams app version: 1449/1.0.95.2022102603 (Crestron)

- Teams Shared Devices License on Teams displays offers a hot-desking experience. The Teams IP Phone policy setting for hot desking is disabled for displays. You can invoke hot desking using Teams accounts with the Teams Shared Device Licenses.
- Bug fixes and improvements for app crashes, reliability of muting and unmuting your microphone during a call, and more.

### December 2021

#### Teams app version: 1449/1.0.95.2021111203

- Teams displays support portrait mode for all calling and meeting screens. Meeting layouts are optimized for portrait videos of individual people. All incoming videos always fit-to-frame when the device is used in portrait orientation.
- Teams displays enabled live event attendee view to allow producer and presenter to join with a quick join link. They have the same capability in displays as in the Teams mobile app. The attendee can access the live event with the event link provided in the calendar details.
- Organizers, presenters, and attendees have the webinar invite on calendar, and can join directly from the calendar event through the **Join** button, which appears on the event when it's about to start.
- The following Teams display settings moved under **Teams Admin Settings** while using a shared account: calling, sign out, and wallpaper.
- Teams displays have the ability to use end-to-end encryption for calls (must be enabled by IT admin).
- IT admins can remotely provision, sign in, and sign out of a Teams device that has previously not been provisioned.
