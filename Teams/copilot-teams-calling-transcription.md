---
title: Manage Microsoft 365 Copilot in Teams calls
author: mkbond007
ms.author: mabond
manager: pamgreen
ms.reviewer: nijait
ms.date: 05/29/2025
ms.topic: how-to
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.subservice: teams-calling
audience: Admin
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
search.appverid: MET150
f1.keywords:
- CSH
ms.custom: 
ms.collection: 
  - M365-collaboration
  - m365initiative-voice
  - highpri
  - Tier1
  - teams-copilot
  - magic-ai-copilot
description: Learn how to manage Microsoft 365 Copilot in Teams calling admin policies in the Teams admin center. Learn how to manage transcripts and transcription for Copilot Microsoft Teams calls.
---

# Manage Microsoft 365 Copilot in Teams calls

**APPLIES TO:** ![Image of a checkmark for yes](/office/media/icons/success-teams.png) 1:1 Teams calls ![Image of a checkmark for yes](/office/media/icons/success-teams.png) PSTN calls

> [!NOTE]
> Microsoft 365 Copilot in Teams is available for public and GCC. It isn’t currently available for GCC High and DoD.

## Overview

Microsoft 365 Copilot in Teams calls is an artificial intelligence (AI) tool that captures important conversation points. Each call participant with a Microsoft 365 Copilot license can ask prompts that are only visible to them. Call participants can learn things like who said what and where people agree or disagree. Microsoft 365 Copilot in Teams can also recommend follow-up tasks, all in real time during a call. As an admin, you can manage how users in your org use Copilot for Teams calls.

There are two ways for users in your organization to use Copilot in calls:

- [During and after the call](#during-and-after-the-call)
- [Only during the call](#only-during-the-call)

The following table describes the differences between these two settings and how they work with call recording and transcription:

| Copilot setting in Calling Policy | Transcription enabled during call  | Copilot available during call | Transcription available after call| Copilot available after call |
| --- | --- | --- | --- |
| Enabled | Yes | Yes | Yes | Yes |
| Enabled | No | Yes | No | No |
| EnabledWithTranscript | Yes | Yes | Yes| Yes|
| EnabledWithTranscript | No | No | No | No |
| Disabled | Yes | No | Yes | No |
| Disabled | No | No | No | No |

### During and after the call

If you enable transcription and Copilot for Teams calls, once a licensed user starts transcription (or recording) during a call, licensed users can select the Copilot button for use during and after the call.

To learn more about how your users can use Copilot during and after the call, see [Get started with Copilot in Microsoft Teams Phone](https://support.microsoft.com/office/97c55ffb-1499-4b0a-8caa-980ebb4b697b).

### Only during the call

You can allow licensed users to use Copilot only during a call, so that AI-generated content isn't available after the call ends. This option occurs when the **Copilot** setting is set to **On** and transcription isn't enabled by the transcription calling policy.

By turning Copilot on and transcription off, once someone with a Microsoft 365 Copilot license selects the Copilot button during the call, Copilot runs for all licensed users. This option relies on speech-to-text audio processing data that isn't saved after the call ends. Users can't access Copilot in Teams and its history after the call.

With Copilot for Teams calls, you can turn off Copilot for calls for users in your organization. All call artifacts are removed immediately after the call ends. This is useful if you want to limit the use of Copilot in Teams calls for compliance or regulatory reasons. For example, if your organization is in a regulated industry such as finance or healthcare, you may want to turn off Copilot for Teams calls for users in your organization because of transcript retention and eDiscovery implications. You can also turn off the ability for users to record or transcribe calls, but still allow them to use Copilot for other purposes.

This policy is only available for Teams *calls*. It’s not available for Teams meetings or events. For more information about Copilot in Teams meetings and events, see [Manage Microsoft 365 Copilot in Teams meetings and events](copilot-teams-transcription.md).

To learn more about how call participants can use Copilot during and after a call, see [Get started with Copilot in Microsoft Teams Phone](https://support.microsoft.com/office/97c55ffb-1499-4b0a-8caa-980ebb4b697b).

As an IT admin, you can also set Copilot's value to **Off** for calling to prevent anyone in a call from using Copilot.

> [!IMPORTANT]
> Microsoft 365 Copilot in Teams calls isn’t available in end-to-end encrypted calls. For more information on end-to-end encryption, see [Use end-to-end encryption for one-to-one Microsoft Teams calls](teams-end-to-end-encryption.md).

## Prerequisites

### Licensing

- You must assign your users a Microsoft 365 subscription that includes Teams or a Microsoft 365 (no Teams) subscription with a separate Teams license.
- For 1:1 Teams calls, you must assign an add-on Microsoft 365 Copilot license for your intended users. To learn more about the Microsoft 365 Copilot license, see [Microsoft 365 Copilot documentation](/microsoft-365-copilot).
- For Public Switched Telephone Network (PSTN) calls, you must also assign a Teams Phone license and have a calling plan for your users. For information on Teams Phone licensing, see [Microsoft Teams add-on licenses](/microsoftteams/teams-add-on-licensing/microsoft-teams-add-on-licensing). To learn more about PSTN connectivity options, see [PSTN connectivity options](pstn-connectivity.md).

### Policies

#### Transcription

To allow your users to use Copilot with Teams calls *after* a PSTN or 1:1 peer-to-peer Voice over Internet Protocol (VoIP) call, you must turn on transcription via Teams calling policy. To turn on transcription, see [Configure call recording, transcription, and captions in Teams](call-recording-transcription-captions.md#enable-call-transcription). Otherwise, depending on your Copilot setting, Copilot is only available during the call.

To learn more about managing transcription, see [Configure call recording, transcription, and captions in Teams calls](call-recording-transcription-captions.md).

## Configure Copilot for Teams calls

As an admin, you can manage how users in your organization use Copilot for Teams calls. You can set the preferred method for Copilot with or without a saved transcript of the call. You can turn off the ability for users to transcribe Teams calls, but still allow them to use Copilot for other purposes.

You can use the Teams admin center or PowerShell to manage how users in your organization use Copilot in Teams calls. You can apply your Copilot calling policies to groups or individual users.

The following table shows the behaviors of the settings for the `-Copilot` parameter used with [**Set-CsTeamsCallingPolicy**](/powershell/module/teams/set-csteamscallingpolicy) PowerShell cmdlet:

|Teams admins center policy value |PowerShell setting value |Behavior|
|---------|---------|---------------|
|On|Enabled|Call participants can use Copilot with or without transcription during calls. If a user enables transcription during the call, users can't access a transcript after the call ends and a transcription isn't saved.|
|On with saved transcript required|EnabledWithTranscript| **This is the default value**. Users assigned this policy can only use Copilot when transcription is enabled during calls. If transcription isn't enabled, then users can't see the Copilot option for the call. |
|Off|Disabled|Copilot is off for calls.|

### Using the Teams admin center

To configure Copilot in Teams calls for your users from the Teams admin center, follow these steps:

1. Open the Teams admin center.
2. Expand **Voice** from the navigation pane.
3. Under **Voice**, select **Calling policies**.
4. Either select an existing policy or create a new one.
5. From the dropdown for the **Copilot** setting, select **On**, **On with saved transcript required**, or **Off**.
    - **On**: Call participants can use Copilot with or without transcription during calls.
    - **On with saved transcript required**: Users assigned this policy can only use Copilot when transcription is enabled during calls. If transcription isn't enabled, then users can't see the Copilot option for the call.
    - **Off**: Copilot is off for calls.
6. Select **Save**

### Using PowerShell

To manage how users in your org use Copilot in Teams calls with PowerShell, use the `-Copilot` parameter within the  [**SetCsTeamsCallingPolicy**](/powershell/module/teams/set-csteamscallingpolicy) PowerShell cmdlet.

To allow users to use Copilot during calls without requiring transcription, use the following command:

```PowerShell
Set-CsTeamsCallingPolicy -Identity <policy name> -Copilot Enabled
```

To turn off Copilot for calls, use the following command:

```PowerShell
Set-CsTeamsCallingPolicy -Identity <policy name> -Copilot Disabled
```

To require transcription for Copilot in calls, use the following command:

```PowerShell
Set-CsTeamsCallingPolicy -Identity <policy name> -Copilot EnabledWithTranscript
```

## Related articles

- [Microsoft 365 Copilot documentation](/microsoft-365-copilot)
- [Configure call recording, transcription, and captions in Teams calls](call-recording-transcription-captions.md)
- [Use end-to-end encryption for one-to-one Microsoft Teams calls](teams-end-to-end-encryption.md)
- [Overview - Recording and transcription for Teams meetings, events, and calls](recording-transcription-overview.md)
