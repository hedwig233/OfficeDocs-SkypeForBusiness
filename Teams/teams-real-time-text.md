---
title: Manage real-time text (RTT) in Teams for users in your organization
ms.author: wlibebe
author: wlibebe
manager: pamgreen
ms.reviewer: harinlee
ms.date: 4/28/2025
ms.topic: how-to
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.subservice: meetings
audience: Admin
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
search.appverid: MET150
f1.keywords:
- CSH
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
  - m365initiative-voice
  - highpri
  - Tier1
description: Learn how to manage real-time text (rtt) for your users’ meetings and calls.
---

# Manage real-time text (RTT) in Teams for users in your organization

**APPLIES TO:** ![Image of a checkmark for yes](/office/media/icons/success-teams.png) Meetings ![Image of a x for no](/office/media/icons/cancel-teams.png) Webinars ![Image of a x for no](/office/media/icons/cancel-teams.png) Town halls ![Image of a checkmark for yes](/office/media/icons/success-teams.png) 1:1 and group VoIP calls

## Overview

Real-time text (RTT) in Microsoft Teams allows participants to instantly send and see written messages on the screen during calls and meetings. RTT displays each character while participants type, which is beneficial for participants with accessibility needs and in situations where voice communication isn’t practical. Unlike chat, RTT messages are sent and received immediately, without participants taking any extra action to send.

:::image type="content" source="media/rtt-meetings-small.png" alt-text="Screenshot of a Teams meeting where participants are using RTT." lightbox="media/rtt-meetings-expand.png":::

## How it works

RTT messages are transmitted over dedicated data channels, ensuring that each character typed is sent and received immediately. This real-time transmission is crucial for maintaining the fluidity of conversation. RTT utilizes specific data channels (for example, ID 24) that are always active during a call or meeting. These channels are responsible for the continuous flow of text data. The user interface shows the RTT data to the meeting screen, manages the display list, and handles text input interactions based on message finalization. The data channel is paused when calls are on-hold and resume when the call continues. This process ensures that RTT messages are displayed prominently and in real-time to all meeting and call participants.
  
## Manage whether your users can use RTT in Teams meetings and group calls

You can use the Teams admin center or PowerShell to manage whether your users can use RTT in Teams meetings and group calls. **This policy setting is on by default.**

### Teams admin center for meetings and group calls

1. Open the Teams admin center.
2. Expand **Meetings** from the navigation pane.
3. Under **Meetings**, select **Meeting policies**.
4. Either select an existing policy or create a new one.
5. Navigate to the **Recording and transcription** section.
6. Toggle the **Real-time-text (RTT)** setting **On** (default)  or **Off** .
7. Select **Save**

### PowerShell

To manage how users in your org use RTT in Teams meetings and group calls, use the **`- RealTimeText`** parameter within the PowerShell [**CsTeamsMeetingPolicy**](/powershell/module/teams/set-csteamsmeetingpolicy) cmdlet.
To prevent users with this policy from using RTT in Teams meetings and group call, use the following script:

```PowerShell
Set-CsTeamsMeetingPolicy -Identity <policy name> - RealTimeText Disabled
```

## Manage whether your users can use RTT in Teams 1:1 VoIP calls

You can use the Teams admin center or PowerShell to manage whether your users can use RTT in Teams 1:1 VoIP calls. **This policy setting is on by default.**

### Teams admin center for 1:1 VoIP calls

1. Open the Teams admin center.
1. Expand **Voice** from the navigation pane.
1. Under **Voice**, select **Calling policies**.
1. Either select an existing policy or create a new one.
1. Toggle the **Real-time-text (RTT)** setting **On**(default) or **Off** .
1. Select **Save**

### PowerShell

To manage how users in your org use RTT in Teams meetings and group calls, use the **`- RealTimeText`** parameter within the PowerShell [**CsTeamsCallingPolicy**](/powershell/module/teams/set-csteamscallingpolicy) cmdlet.
To prevent users with this policy from using RTT in Teams 1:1 VoIP calls, use the following script:

```PowerShell
Set-CsTeamsCallingPolicy -Identity <policy name> - RealTimeText Disabled
```

## User experience

- To see RTT in recordings, users must turn on captions.  
- Users joining meetings from Microsoft Teams Rooms, can see, but can’t send RTT on the screen.

## Feature support

RTT is supported on the following platforms and types of meetings and calls:

- Meetings
- Group calls
- 1:1 VoIP calls
- Microsoft Teams Rooms meetings (Windows and Android)  
- Mobile devices (iOS and Android)
- Compliance recordings

RTT isn’t supported on the following platforms and types of meetings and calls:

- PSTN calls
- Emergency calling
- Webinars
- Town halls
- Teams Phones
- End to end encrypted meetings

## Data storage

RTT follows the same storage as transcription. To learn more, see [Teams meeting recording and transcript storage and permissions in OneDrive and SharePoint]( tmr-meeting-recording-change.md).

## Related articles

- [Overview- Recording and transcription for Teams meetings, events, and calls](recording-transcription-overview.md)
- [Teams meeting recording and transcript storage and permissions in OneDrive and SharePoint]( tmr-meeting-recording-change.md)
