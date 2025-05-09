---
title: Manage Microsoft 365 Copilot in Teams calls
author: mkbond007
ms.author: mabond
manager: pamgreen
ms.reviewer: nijait
ms.date: 05/01/2025
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

Microsoft 365 Copilot in Teams calls is an artificial intelligence (AI) tool that captures important conversation points. Each call participant with a Microsoft 365 Copilot license can ask prompts that are only visible to them. Call participants can learn things like who said what and where people agree or disagree. Microsoft 365 Copilot in Teams can also recommend follow-up tasks, all in real time during a call. As an admin, you can manage how users in your org use Copilot for Teams calls.

This policy is only available for Teams *calls*. It’s not available for Teams meetings or events. For more information about Copilot in Teams meetings and events, see [Manage Microsoft 365 Copilot in Teams meetings and events](copilot-teams-transcription.md).

Once someone with a Microsoft 365 Copilot license selects the Copilot button during a call, Copilot runs for all licensed users. This option relies on speech-to-text audio processing data that isn't saved after the call ends. Users can't access Copilot in Teams and its history after the call.

To learn more about how call participants can use Copilot during **and after** a call, see [Get started with Copilot in Microsoft Teams Phone](https://support.microsoft.com/office/97c55ffb-1499-4b0a-8caa-980ebb4b697b).

As an IT admin, you can also set Copilot's value to **Off** for calling to prevent anyone in a call from using Copilot.

> [!IMPORTANT]
> Microsoft 365 Copilot in Teams calls isn’t available in end-to-end encrypted calls. For more information on end-to-end encryption, see [Use end-to-end encryption for one-to-one Microsoft Teams calls](teams-end-to-end-encryption.md).

## Prerequisites

For 1:1 Teams calls, you must assign an add-on Microsoft 365 Copilot license for your intended users. To learn more about the Microsoft 365 Copilot license, see [Microsoft 365 Copilot documentation](/microsoft-365-copilot).

For Teams calls using the Public Switched Telephone Network (PSTN), you must also assign a Teams Phone license to your users. For more information about Teams Phone with PSTN connectivity licenses, see [Microsoft Teams add-on licenses](/teams-add-on-licensing/microsoft-teams-add-on-licensing.md).

## Transcription

You can use the **Calling policies** section in the Teams admin center or the **`-AllowTranscriptionForCalling`** parameter in the [**CsTeamsCallingPolicy**](/powershell/module/teams/set-csteamscallingpolicy) PowerShell cmdlet to manage your calling transcription policy. This setting's value impacts how or if Copilot works for your users.

To learn more about managing transcription, see [Configure call recording, transcription, and captions in Teams calls](call-recording-transcription-captions.md).

## Manage Copilot for Teams calls

You can use the Teams admin center or PowerShell to manage how users in your organization use Copilot in Teams calls. You can apply your Copilot calling policies to groups or individual users.

The following table shows the behaviors of the settings for the **`-Copilot`** parameter used with [**Set-CsTeamsCallingPolicy**](/powershell/module/teams/set-csteamscallingpolicy) PowerShell cmdlet:

|Teams admins center policy value |PowerShell setting value |Behavior|
|---------|---------|---------------|
|On|Enabled|Call participants can use Copilot with or without transcription during calls. If a user enables transcription during the call, users can't access a transcript after the call ends and a transcription isn't saved.|
|On with saved transcript required|EnabledWithTranscript| **This is the default value**. Users assigned this policy can only use Copilot when transcription is enabled during calls. If transcription isn't enabled, then users can't see the Copilot option for the call. |
|Off|Disabled|Copilot is off for calls.|

### Manage Copilot for Teams calls in the Teams admin center

1. Open the Teams admin center.
2. Expand **Voice** from the navigation pane.
3. Under **Voice**, select **Calling policies**.
4. Either select an existing policy or create a new one.
5. From the dropdown for the **Copilot** setting, select **On**, **On with saved transcript required**, or **Off**.
6. Select **Save**

### Manage Copilot for Teams calls using PowerShell

To manage how users in your org use Copilot in Teams calls, use the **`-Copilot`** parameter within the  [**CsTeamsCallingPolicy**](/powershell/module/teams/set-csteamscallingpolicy) PowerShell cmdlet.

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
