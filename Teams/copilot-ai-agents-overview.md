---
title: Overview of AI in Microsoft Teams
author: DaniEASmith
ms.author: danismith
manager: jtremper
ms.reviewer: sophiapeng
ms.date: 04/02/2025
ms.topic: overview
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
ms.collection: 
  - M365-collaboration
  - magic-ai-copilot
ms.custom:
f1.keywords:
- NOCSH
appliesto: 
  - Microsoft Teams
ms.localizationpriority: high
search.appverid: MET150
description: Discover which AI features are available in Microsoft Teams for your organization and how to set them up.
---

# Overview of AI in Microsoft Teams for IT admins

Microsoft has introduced an ever-growing catalog of AI tools and features for Microsoft Teams, starting with features like voice isolation and suggested replies. Today, this catalog includes a powerful, personal AI assistant called Copilot in Teams and task-tailored agents like Facilitator.

This article is for IT admins and discusses the AI tools and features available in Teams along with links to their related documentation.

In this article, learn about:

- [Standard AI features in Microsoft Teams](#standard-ai-features-in-microsoft-teams)
- [Microsoft 365 Copilot features in Teams](#microsoft-365-copilot-features-in-teams)
- [Microsoft 365 Copilot app in Teams](#microsoft-365-copilot-app-in-teams)
- [Microsoft Copilot in Teams](#microsoft-copilot-in-teams)
- [Microsoft 365 agents in Teams](#microsoft-365-agents-in-teams)
- [AI features included with Teams Premium](#ai-features-included-with-teams-premium)

## Standard AI features in Microsoft Teams

*Required licenses:*
> [!div class="checklist"]
> - *Microsoft Business (Basic, Standard, and Premium) or Microsoft 365 (E3/E5/F1/F3/A3/A5/G3/G5)*
> - *Teams Enterprise or Teams Enterprise (EEA)*

Microsoft Teams includes some AI features that don’t require any extra licenses, just a Microsoft 365 subscription and a Teams license. These features enhance your users’     Teams experience in their workflow, chats, and meetings, including:

- **Microsoft Copilot Chat app**: The Copilot Chat app in Teams allows users to ask Copilot open-ended questions, request help creating new content, and use [Copilot Pages](https://support.microsoft.com/topic/introducing-microsoft-365-copilot-pages-6674bd51-9ff5-42c4-9256-44d9428a726f). Without a Microsoft 365 Copilot license, Copilot’s responses are only grounded in public web data.

- **Suggested replies**: Teams can suggest replies to users based on the previous conversation in 1:1 and group chats.

- **Video optimization**: Teams can optimize users’ video feeds through AI-assisted adjustments, like auto-brightness and facial recognition.

- **Voice isolation for calls and meetings**: Teams can use AI to separate a user's voice from other sounds and voices in Teams calls and meetings, displaying the user’s name when they speak and identifying them as the speaker in a transcript. Voice isolation is also used to reduce background noise.

- **Intelligent media quality classifiers in Call Quality Dashboard (CQD)**: Teams can monitor call quality using Machine Learning (ML) algorithms with intelligent media quality classifiers in CQD, which provide advanced analysis into causality, media degradation, and root cause to address and prevent call quality issues.

| Feature | Admin articles | End-user articles |
| ------- | -------------- | ----------------- |
| Microsoft Copilot Chat app | [Overview of Microsoft Copilot Chat](/copilot/overview) | [Microsoft Copilot Chat](https://support.microsoft.com/copilot-microsoft365-chat) |
| Suggested replies | None | [Use suggested replies to respond to messages](https://support.microsoft.com/office/use-suggested-replies-to-respond-to-messages-without-typing-in-microsoft-teams-010c54e1-a613-4771-94ed-76d7fb77cba5) |
| Facial recognition | [Create Recognition profiles for Microsoft IntelliFrame](rooms/voice-recognition.md) | [Create Recognition profiles for Microsoft IntelliFrame](https://support.microsoft.com/office/create-recognition-profiles-for-microsoft-intelliframe-f0084478-52a7-4c52-bcdc-9063ed0e0bc0) |
| Voice isolation for calls and meetings | [Manage voice isolation for your users' Microsoft Teams calls and meetings](voice-isolation.md) | [Voice isolation in Microsoft Teams calls and meetings](https://support.microsoft.com/office/voice-isolation-in-microsoft-teams-calls-and-meetings-a9756ea9-4cec-44c4-aefb-6f5d17c89427) <br> <br> [Reduce background noise in Microsoft Teams meetings](https://support.microsoft.com/office/reduce-background-noise-in-microsoft-teams-meetings-1a9c6819-137d-4b3b-a1c8-4ab20b234c0d)|
| Intelligent media quality classifiers in CQD | [Intelligent media quality classifiers in Call Quality Dashboard (CQD)](cqd-intelligent-media-quality-classifiers.md) | None |

## Microsoft 365 Copilot features in Teams

*Required licenses:*
> [!div class="checklist"]
> - *Microsoft Business (Basic, Standard, and Premium) or Microsoft 365 (E3/E5/F1/F3/A3/A5/G3/G5)*
> - *Teams Enterprise or Teams Enterprise (EEA)*
> - *Microsoft 365 Copilot*

> [!IMPORTANT]
> All prompts, files, and responses using Microsoft Copilot, including the Microsoft Copilot Chat app and the Microsoft 365 Copilot app, never leave your organization’s Microsoft 365 service boundary. This includes prompts and responses that access public web data. Your data is always secured and private within your service boundary.
>
> Microsoft 365 Copilot and Microsoft 365 Copilot Chat are ISO/IEC 42001:2023 certified to further ensure that we develop, deploy, and use AI systems responsibly. For more information, see [Microsoft 365 Copilot Achieves ISO/IEC 42001:2023 Certification](https://techcommunity.microsoft.com/blog/microsoft365copilotblog/microsoft-365-copilot-achieves-isoiec-420012023-certification/4397144).

The Microsoft 365 Copilot license is the foundation for many AI tool sets in Teams, like Copilot in Teams and Facilitator. If you want your users to access a robust set of AI features, purchase and assign Microsoft 365 Copilot licenses to them.  

Review the following resources for more information about Microsoft 365 Copilot:

- [What is Microsoft 365 Copilot?](/copilot/microsoft-365/microsoft-365-copilot-overview)
- [Which Copilot is right for me or my organization?](/copilot/microsoft-365/which-copilot-for-your-organization)
- [Set up Microsoft 365 Copilot](/copilot/microsoft-365/microsoft-365-copilot-setup)
- [Copilot Prompt Gallery](https://copilot.cloud.microsoft/prompts?)

### Microsoft 365 Copilot app in Teams

The Microsoft 365 Copilot license upgrades your users’ Microsoft Copilot Chat app experience. The Microsoft 365 Copilot app is like the Microsoft Copilot Chat app, where users can ask open-ended questions, get help creating new content, and explore ideas. However, The Microsoft 365 Copilot app is also grounded in users’ work data. Users can then toggle between whether they want their prompts grounded in work data or public web data.

### Microsoft Copilot in Teams

Microsoft 365 Copilot in Teams is your users’ personal Copilot, helping them in their workflows with skills like file and chat summarization, open-ended question and answer, task generation, and intelligent feedback and suggestions.

- **Copilot in Teams chats and channels**: Copilot in your users’ chats and channels helps them catch up on conversations quickly and help contribute intelligently.

- **Copilot in Teams meetings and events**: Copilot in meetings and events uses recording, transcription, and meeting chat data to ensure participants get the most out of meetings.

- **Copilot in Teams Phone**: Copilot in Teams Phone empowers your users to have more productive calls or catch up on ones they missed.

- **Copilot in Teams Rooms**: Copilot enhances Teams Rooms experiences with features like responding to open-ended questions, recapping what was discussed in the room, and providing meeting insights.

- **Copilot in Teams for multitenant organizations** - B2B members who are licensed with Microsoft 365 Copilot can access Copilot in Teams across their multitenant organization.

| Feature | Admin articles | End-user articles |
| ------- | -------------- | ----------------- |
| Copilot in Teams chats and channels | None | [Use Copilot in Microsoft Teams chat and channels](https://support.microsoft.com/office/use-copilot-in-microsoft-teams-chat-and-channels-cccccca2-9dc8-49a9-ab76-b1a8ee21486c) |
| Copilot in Teams meetings and events | [Manage Microsoft 365 Copilot in Teams meetings and events](copilot-teams-transcription.md) | [Use Copilot in Microsoft Teams meetings](https://support.microsoft.com/office/use-copilot-in-microsoft-teams-meetings-0bf9dd3c-96f7-44e2-8bb8-790bedf066b1) |
| Copilot in Teams Phone | [Manage Microsoft 365 Copilot in Teams calls](copilot-teams-calling-transcription.md) | [Get started with Copilot in Microsoft Teams Phone](https://support.microsoft.com/office/get-started-with-copilot-in-microsoft-teams-phone-97c55ffb-1499-4b0a-8caa-980ebb4b697b) |
| Copilot in Teams Rooms | [Teams Rooms and Copilot overview](rooms/copilot-admin-mtr.md) | None |
| Copilot in Teams for multitenant organizations | [Manage Copilot access for B2B members within multitenant organizations (MTO) in Teams](copilot-mto.md) | None |

### Microsoft 365 agents in Teams

Microsoft 365 agents are designed to help your users with unique work tasks, grounded in scoped knowledge, like extending a project plan or capturing unanswered questions during a meeting. With a Microsoft 365 Copilot license, users can access the following agents in Teams:

- **Facilitator**: Facilitator is a Teams collaboration agent in group chats and meetings where all users can interact with Facilitator like it’s another member.

- **Facilitator for Teams Rooms**: Facilitator can also aid collaboration during in-person, unscheduled meetings via Teams Rooms.

| Feature | Admin articles | End-user articles |
| ------- | -------------- | ----------------- |
| Facilitator | [Set up Facilitator in Microsoft Teams](facilitator-teams.md) | [Keep track of chats with AI notes in Microsoft Teams](https://support.microsoft.com/office/keep-track-of-chats-with-ai-notes-in-microsoft-teams-0b7efbd0-fd3e-48e7-9a4b-4ea22cdc12c0) <br> <br> [Automate notetaking in Microsoft Teams meetings](https://support.microsoft.com/office/automate-notetaking-in-microsoft-teams-meetings-37657f91-39b5-40eb-9421-45141e3ce9f6)|
| Facilitator for Teams Rooms | [Facilitator in Microsoft Teams Rooms](rooms/facilitator-teams-rooms.md) | None |

## AI features included with Teams Premium

*Required licenses:*
> [!div class="checklist"]
> - *Microsoft Business (Basic, Standard, and Premium) or Microsoft 365 (E3/E5/F1/F3/A3/A5/G3/G5)*
> - *Teams Enterprise or Teams Enterprise (EEA)*
> - *Teams Premium*

Some AI features in Teams can be acquired through the [Teams Premium add-on license](/microsoftteams/teams-add-on-licensing/licensing-enhance-teams). Teams Premium enhances users’ Teams experience through intelligent, customizable, and secured collaboration scenarios.

- **Decorate my background**: Your users can use AI to decorate their backgrounds.

- **Intelligent call and meeting recap**: Provide your users with AI-powered insights and recaps of Public Switched Telephone Network (PSTN) calls (if they're [connected to the PSTN](pstn-connectivity.md)), 1:1 Teams calls, and meetings.

- **Live translated captions**: Allow your users to see captions translated into the language they’re most comfortable with.

- **Live translated transcription**: Your users can understand each other better during a meeting or event by translating the meeting transcript into the language they're most comfortable with.

| Feature | Admin articles | End-user articles |
| ------- | -------------- | ----------------- |
| Decorate my background | None | [Change your background in Microsoft Teams meetings](https://support.microsoft.com/office/change-your-background-in-microsoft-teams-meetings-f77a2381-443a-499d-825e-509a140f4780) |
| Intelligent call and meeting recap | [Intelligent recap for Teams calls and meetings](intelligent-recap-calls-meetings.md) | [Recap in Microsoft Teams](https://support.microsoft.com/office/recap-in-microsoft-teams-c2e3a0fe-504f-4b2c-bf85-504938f110ef#bkmk_intelligent_meeting_recap) |
| Live translated captions | [Manage transcription and captions for Teams meetings](meeting-transcription-captions.md) | [Use live captions in Microsoft Teams meetings](https://support.microsoft.com/office/use-live-captions-in-microsoft-teams-meetings-4be2d304-f675-4b57-8347-cbd000a21260) |
| Live translated transcription | [Manage transcription and captions for Teams meetings](meeting-transcription-captions.md) | [View live transcription in Microsoft Teams meetings](https://support.microsoft.com/office/view-live-transcription-in-microsoft-teams-meetings-dc1a8f23-2e20-4684-885e-2152e06a4a8b) |

## Related articles

- [Copilot in Microsoft Teams help & learning](https://support.microsoft.com/copilot-teams?ocid=PromptGallery_SMC_Teams)
- [Frequently asked questions about Copilot in Microsoft Teams](https://support.microsoft.com/office/frequently-asked-questions-about-copilot-in-microsoft-teams-e8737767-4087-4ae6-b1d8-10264152b05a)
- [Frequently asked questions about Facilitator in Microsoft Teams](https://support.microsoft.com/office/frequently-asked-questions-about-facilitator-in-microsoft-teams-f7317b78-fd53-4cfe-88f0-f0a0751a4150)
