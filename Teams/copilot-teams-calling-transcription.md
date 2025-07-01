---
title: Manage Microsoft 365 Copilot in Teams calls
author: mkbond007
ms.author: mabond
manager: dansimp
ms.reviewer: nijait
ms.date: 07/01/2025
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
description: Learn how to manage Microsoft 365 Copilot in Teams for calls with calling policies in the Teams admin center. Learn how to manage transcripts and transcription for Copilot in Microsoft Teams for calls.
---

# Manage Microsoft 365 Copilot in Teams calls

**APPLIES TO:** ![Image of a checkmark for yes](/office/media/icons/success-teams.png) 1:1 Teams calls ![Image of a checkmark for yes](/office/media/icons/success-teams.png) Public Switched Telephone Network (PSTN) calls

## Overview

Microsoft 365 Copilot is a secure, AI-powered assistant that can help users stay productive by providing real-time insights and summaries for Teams calls. Each call participant with a Microsoft 365 Copilot license can privately engage with Copilot using natural language prompts. Copilot identifies who said what, highlights shared perspectives with differing viewpoints, and suggests follow-up tasks&mdash;all during the call. As an admin, you can configure how users in your organization access and use Copilot in Teams calls.

> [!NOTE]
> Microsoft 365 Copilot in Teams is available for public and GCC. It isn’t currently available for GCC High and DoD.

There are two modes for users in your organization to use Copilot in calls:

- [During and after the call](#during-and-after-the-call)
- [Only during the call](#only-during-the-call)

The following table describes the differences between these two modes and how they work with call recording and transcription:

| Copilot setting in Calling Policy | Transcription started during call  | Copilot available during call | Transcription available after call|
| --- | --- | --- | --- |
| Enabled | Yes | Yes | Yes |
| Enabled | No | Yes | No |
| EnabledWithTranscript | Yes | Yes | Yes|
| EnabledWithTranscript | No | No | No |
| Disabled | Yes | No | Yes |
| Disabled | No | No | No |

### During and after the call

As an admin, if you enable both transcription and Copilot for Teams for your users via calling policy, once a licensed user starts transcription (or recording) during a call, licensed users can select the Copilot button for use during and after the call.

After the calls ends, licensed users can access the Copilot insights, summaries, and recap that were generated during the call. Depending on your organization's retention settings, users can return to access the transcript or recording. After the call, users can view the information exchanged with Microsoft 365 during the call and can ask Microsoft 365 Copilot to generate new insights or summaries.

To learn more about how your users can use Copilot during and after the call, see [Get started with Copilot in Microsoft Teams Phone](https://support.microsoft.com/office/97c55ffb-1499-4b0a-8caa-980ebb4b697b).

### Only during the call

You can limit licensed users to use Copilot only during a call. In this mode, after a call ends, transcription or Copilot content generated during a call isn't retained. To enable this mode, you must use the Teams calling policy to turn on Copilot and turn off transcription for calls. Some organizations may prefer to only have Microsoft 365 Copilot available during the call due to compliance and eDiscovery considerations.

By turning Copilot on and calling transcription off, once a user with a Microsoft 365 Copilot license selects the Copilot button during a call, Copilot runs for all licensed users. This option relies on speech-to-text audio processing data that isn’t saved after the call ends. The information exchanged between the user and Microsoft 365 Copilot during the call isn't saved after the call ends, either. As shown later in this article, you can [configure Copilot for Teams calls](#configure-copilot-for-teams-calls) in the Teams admin center and via PowerShell.

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
|On|Enabled| **This is the default value**. Call participants can use Copilot with or without transcription during calls. If a licensed user doesn't start transcription during the call, users can't access a transcript after the call ends and a transcription isn't saved.|
|On with saved transcript required|EnabledWithTranscript| Users assigned this policy can only use Copilot when a licensed user starts transcription during a call. If transcription isn't enabled, then users can't see the Copilot option for the call and there is no transcript available after the call ends.|
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
6. Select **Save**.

### Using PowerShell

To manage how users in your org use Copilot in Teams calls with PowerShell, use the `-Copilot` parameter within the  [**SetCsTeamsCallingPolicy**](/powershell/module/teams/set-csteamscallingpolicy) PowerShell cmdlet.

To allow licensed users to use Copilot during calls without requiring transcription, use the following command:

```PowerShell
Set-CsTeamsCallingPolicy -Identity <policy name> -Copilot Enabled
```

To turn off Copilot for calls, use the following command:

```PowerShell
Set-CsTeamsCallingPolicy -Identity <policy name> -Copilot Disabled
```

To require transcription for Copilot in calls and turn on calling transcription, use the following command:

```PowerShell
Set-CsTeamsCallingPolicy -Identity <policy name> -Copilot EnabledWithTranscript -AllowTranscriptionForCalling $true
```

## Related articles

[Microsoft 365 Copilot documentation](/microsoft-365-copilot)

[Configure call recording, transcription, and captions in Teams calls](call-recording-transcription-captions.md)

[Use end-to-end encryption for one-to-one Microsoft Teams calls](teams-end-to-end-encryption.md)

[Overview - Recording and transcription for Teams meetings, events, and calls](recording-transcription-overview.md)

[Get started with Copilot in Microsoft Teams Phone](https://support.microsoft.com/office/97c55ffb-1499-4b0a-8caa-980ebb4b697b)
