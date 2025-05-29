---
title: Manage Microsoft 365 Copilot in Teams calls - Overview
author: mkbond007
ms.author: mabond
manager: pamgreen
ms.reviewer: nijait
ms.date: 05/12/2025
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
description: Learn how to manage Microsoft 365 Copilot in Teams calls with admin policies in the Teams admin center. Learn how to manage transcripts and transcription for Copilot Microsoft Teams calls.
---

# Manage Microsoft 365 Copilot in Teams calls

**APPLIES TO:** ![Image of a checkmark for yes](/office/media/icons/success-teams.png) 1:1 Calls ![Image of a checkmark for yes](/office/media/icons/success-teams.png) PSTN Calls ![Image of a x for no](/office/media/icons/cancel-teams.png) Meetings ![Image of a x for no](/office/media/icons/cancel-teams.png) Webinars ![Image of a x for no](/office/media/icons/cancel-teams.png) Town halls

Microsoft 365 Copilot in Teams calls is an artificial intelligence (AI) tool that captures important conversation points. Each call participant with a Microsoft 365 Copilot license can ask prompts that are only visible to them. Microsoft 365 Copilot in Teams can also recommend follow-up tasks, all in real time during a call. As an admin, you can manage how users in your org use Copilot for Teams calls.

This article explains how Microsoft 365 Copilot in Teams calls works and gives an overview of available features.

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

## During and after the call

If you enable transcription and Copilot for Teams calls, once a licensed user starts transcription (or recording) during a call, licensed users can select the Copilot button for use during and after the call.

To learn more about how your users can use Copilot during and after the call, see [Get started with Copilot in Microsoft Teams Phone](https://support.microsoft.com/office/97c55ffb-1499-4b0a-8caa-980ebb4b697b).

## Only during the call

You can allow licensed users to use Copilot only during a call, making AI-generated content not available after the call ends. This option occurs when the **Copilot** setting is set to **On** and transcription isn't enabled, either by the transcription calling policy (if turned off) or if licensed users don't turn on transcription during a call.

Once someone with a Microsoft 365 Copilot license selects the Copilot button during the call, Copilot runs for all licensed users. This option relies on speech-to-text audio processing data that isn't saved after the call ends. Users can't access Copilot in Teams and its history after the call.

With Copilot for Teams calls, you can turn off Copilot for calls for users in your organization. All call artifacts are removed immediately after the call ends. This is useful if you want to limit the use of Copilot in Teams calls for compliance or regulatory reasons. For example, if your organization is in a regulated industry such as finance or healthcare, you may want to turn off Copilot for Teams calls for users in your organization because of transcript retention and eDiscovery implications. You can also turn off the ability for users to record or transcribe calls, but still allow them to use Copilot for other purposes.

For information about using Copilot only during Teams *meetings*, see [Manage Microsoft 365 Copilot in Teams meetings and events](copilot-teams-transcription.md).

## Prerequisites

Copilot only mode is automatically available to users in your organization with the following required licenses and policies:

### Licensing

- You must assign your users a Microsoft 365 subscription that includes Teams or a Microsoft 365 (no Teams) subscription with a separate Teams license.
- You must assign a Microsoft 365 Copilot license to your users.
- For Public Switched Telephone Network (PSTN) calls, you must also assign a Teams Phone license and have a calling plan for your users. For information on Teams Phone licensing, see [Microsoft Teams add-on licenses](/microsoftteams/teams-add-on-licensing/microsoft-teams-add-on-licensing). To learn more about PSTN connectivity options, see [PSTN connectivity options](pstn-connectivity.md).

### Policies

#### Transcription

To allow your users to use Copilot with Teams calls *after* a PSTN or 1:1 peer-to-peer Voice over Internet Protocol (VoIP) call, you must turn on transcription via Teams calling policy. To turn on transcription, see [Configure call recording, transcription, and captions in Teams](call-recording-transcription-captions.md#enable-call-transcription). Otherwise, depending on your Copilot setting, Copilot is only available during the call.

## Configure Copilot for Teams calls

As an admin, you can manage how users in your organization use Copilot for Teams calls. You can set the preferred method for Copilot with or without a saved transcript of the call. You can turn off the ability for users to transcribe Teams calls, but still allow them to use Copilot for other purposes.

To configure Copilot in Teams calls for your users, follow these steps:

1. In the Teams admin center, go to **Voice** > **Calling policies**.
1. For the policy you want to modify, select **Edit**.
1. In the **Copilot** dropdown, select **On**, **On with saved transcript required**, or **Off**.
    - **On**: Call participants can use Copilot with or without transcription during calls.
    - **On with saved transcript required**: Users assigned this policy can only use Copilot when transcription is enabled during calls. If transcription isn't enabled, then users can't see the Copilot option for the call.
    - **Off**: Copilot is off for calls.
1. Select **Save**.

To learn more about managing call transcription, see [Configure call recording, transcription, and captions in Teams](call-recording-transcription-captions.md).

## Related articles

- [Microsoft 365 Copilot documentation](/microsoft-365-copilot)
- [Configure call recording, transcription, and captions in Teams](call-recording-transcription-captions.md)
- [Get started with Copilot in Microsoft Teams Phone](https://support.microsoft.com/office/97c55ffb-1499-4b0a-8caa-980ebb4b697b)
