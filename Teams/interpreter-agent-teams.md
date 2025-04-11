---
title: Manage Interpreter agent for your organization 
author: wlibebe
ms.author: wlibebe
manager: pamgreen
ms.reviewer: harinlee
ms.date: 4/4/2025
ms.topic: how-to
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.subservice: meetings
audience: Admin
ms.collection: 
  - m365initiative-meetings
  - magic-ai-copilot
ms.custom:
  - admindeeplinkTEAMS
f1.keywords:
- NOCSH
appliesto: 
  - Microsoft Teams
ms.localizationpriority: high
search.appverid: MET150
description: Learn how to manage Interpreter agent in Microsoft Teams to provide translation during meetings.
---

# Manage Interpreter agent for your organization

**APPLIES TO:** ![Image of a checkmark for yes](/office/media/icons/success-teams.png) Meetings ![Image of a x for no](/office/media/icons/cancel-teams.png) Webinars ![Image of a x for no](/office/media/icons/cancel-teams.png) Town halls

> [!IMPORTANT]
> This feature is currently in Teams Public preview.
>
> Features in preview might not be complete and could undergo changes before becoming available in the public release. They're provided for evaluation and exploration purposes only.

Interpreter agent acts as a translator in Microsoft Teams meetings, allowing participants with a Microsoft 365 Copilot license to listen to the meeting in their chosen language. Interpreter listens to the spoken language in the meeting and translates it into another language in real-time, allowing participants who speak different languages to understand each other and collaborate effectively. To represent their voices, participants can choose to have Interpreter simulate their own voice when translating to others or select one of the following preset automated voices:  Voice 1 (female), Voice 2 (male), Voice 3 (neutral).

As an admin, you can control whether your organization can use Interpreter and select the default setting for voice representation.

To learn more about the Interpreter experience in meetings, see [Interpreter in Microsoft Teams meetings](https://support.microsoft.com/office/interpreter-in-microsoft-teams-meetings-c7efe2bb-535d-42ab-a5c4-d2d91619b46d).

## Supported languages

Interpreter supports the following languages for speaking and listening: Chinese (Mandarin), English, French, German, Italian, Japanese, Korean, Portuguese (Brazil), Spanish.

## Prerequisites and licensing for Public preview

The following list contains the prerequisites for users to access Interpreter in Teams meetings. Users must meet all the following requirements:

> [!NOTE]
> We'll update the licensing requirements for General availability. Check back soon for updates.

- An eligible *Microsoft 365* base license.
  - For the list of eligible base licenses, see [Understand licensing requirements for Microsoft 365 Copilot](/copilot/microsoft-365/microsoft-365-copilot-licensing).
- An eligible *Microsoft Teams* license.
  - Teams licenses might be included in your *Microsoft 365* subscription, or you might need to purchase a separate Teams license if you have *Microsoft 365 (no Teams)* licenses.
- A *Microsoft 365 Copilot* license.
  - For information on how to acquire *Microsoft 365 Copilot* licenses, see [Where can I get Microsoft Copilot?](https://support.microsoft.com/topic/where-can-i-get-microsoft-copilot-40a622db-6d25-4266-b008-4bbcb55cf52f)
- Be a Microsoft Teams Public preview participant.
  - For information on how to access Teams Public preview features, see [Microsoft Teams Public preview](/microsoftteams/public-preview-doc-updates).
  
## Data, security, and privacy

When your users allow Interpreter to simulate their voice, their voice sample isn’t stored.

### How Interpreter works

Interpreter performs real-time speech-to-speech (STS) translation using Azure Cognitive Services, supporting multi-speaker, mixed-language conversations in Teams meetings.
Here's how it works:

1. Speech Recognition (ST)- Converts spoken language into English text.
2. Machine translation (MT)- Translates English text into the selected languages.
3. Text-to-speech (TTS)- Produces translated speech in the chosen language. TTS can simulate the speaker’s voice or use a predefined voice based on user preference and the admin policy.
4. A bot transmits meeting audio for cloud-based processing and returns translations instantly.

### How Interpreter uses your users' voices

When a user turns on voice simulation in the Interpreter, other participants hear the translated speech in the speaker’s own voice.

Here's how it works:

1. **Admin policy**- To set the default value for **Your voice representation** to **Simulate my voice** for all users in your organization, you use the **`-VoiceSimulationInInterpreter`** parameter.
2. **User Interpreter settings**- Users can choose whether to use voice simulation during meetings.
3. **Privacy-first design**- The system samples brief segments of the speaker’s voice to simulate their tone, style, and voice characteristics in real-time, without storing biometric data. It preserves the speaker's natural tone, pitch, and style, without exaggerating emotions.
4. **Voice simulation**- AI generates a simulated voice in the selected language for seamless end-to-end translation.

:::image type="content" source="media/interpreter-agent-diagram-small.png" alt-text="Architecture diagram of language media processing to ACS speech." lightbox="media/interpreter-agent-diagram-expand.png":::

## Manage Interpreter using PowerShell

You must use PowerShell to manage Interpreter for your entire organization.

To manage Interpreter for your entire organization, you can use the **`-AIInterpreter`** and **`-VoiceSimulationInInterpreter`** parameters in the PowerShell [CsTeamsMeetingPolicy](/powershell/module/teams/set-csteamsmeetingpolicy) cmdlet.

### Turn Interpreter on or off

The org-wide **`-AIInterpreter`** parameter controls whether your users with a Microsoft 365 Copilot license can use Interpreter during meetings in your organization. **This parameter is enabled by default.**

To turn off Interpreter for your entire organization, use the following script:

```PowerShell
Set-CsTeamsMeetingPolicy -Identity <policy name> -AIInterpreter Disabled
```

To turn on Interpreter for your entire organization, use the following script:

```PowerShell
Set-CsTeamsMeetingPolicy -Identity <policy name> -AIInterpreter Enabled
```

### Set the default value for voice representation

The org-wide **`-VoiceSimulationInInterpreter`** parameter controls your users' default value for **Your voice representation** in **Interpreter settings**. The **Your voice representation** setting controls how a user's voice is represented to other participants. **By default, this parameter is set to disabled.**

Here's the user experience for Interpreter depending on the value you choose:

- **Enabled**: Sets the default value for **Your voice representation** to **Simulate my voice**. When users turn on Interpreter, it automatically simulates their voices when translating to others in meetings. Users can also select an automated voice.

- **Disabled**: Sets the default value for **Your voice representation** to **Automated voice**. When users turn on Interpreter, they select one of the automated voices for translation. Users can also choose to allow Interpreter to simulate their voice. **This is the default value.**

To set the org-wide default value for the **Your voice representation** setting to **Simulate my voice**, use the following script:  

```PowerShell
Set-CsTeamsMeetingPolicy -Identity <policy name> -VoiceSimulationInInterpreter Enabled
```

To set the org-wide default value for the **Your voice representation** setting to **Automated voice**, use the following script:

```PowerShell
Set-CsTeamsMeetingPolicy -Identity <policy name> -VoiceSimulationInInterpreter Disabled
```

## Supported platforms and clients

### Supported

Interpreter is supported on the following platforms and clients:

- Teams desktop (Windows and Mac)
- Teams mobile (iOS and Android)
- Teams web (Chrome, Microsoft Edge, and Firefox)
- Scheduled meetings
- Channel meetings
- Virtual Desktop Infrastructure (VDI)

### Not supported

Interpreter isn't supported on the following platforms and clients:

- Unscheduled 1:1 calls (VoIP or Public Switched Telephone Network (PSTN))
- Meetings scheduled using Microsoft Teams Rooms or personal devices
- Town halls
- Webinars
- Microsoft Teams free

## Related articles

- [Manage Microsoft 365 Copilot in Teams meetings and events](copilot-teams-transcription.md)
- [Set up Facilitator in Microsoft Teams for collaborative AI-generated notes](facilitator-teams.md)
- [What is responsible AI?](https://support.microsoft.com/topic/what-is-responsible-ai-33fc14be-15ea-4c2c-903b-aa493f5b8d92)
- [Frequently asked questions: AI, Microsoft Copilot, and Microsoft Designer](https://support.microsoft.com/topic/frequently-asked-questions-ai-microsoft-copilot-and-microsoft-designer-987b275d-f6f2-4d5d-94c5-e927cffae705)
- [Providing feedback about Microsoft Copilot with Microsoft 365 apps](https://support.microsoft.com/topic/providing-feedback-about-microsoft-copilot-with-microsoft-365-apps-c481c26a-e01a-4be3-bdd0-aee0b0b2a423?ocid=CopilotLab_SMC_Privacy_Feedback)
