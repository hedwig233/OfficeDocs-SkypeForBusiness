---
title: Diagnostic event namespaces for Microsoft Teams
description: "Learn about event namespaces and review a list of event namespaces for Microsoft Teams, including a description of each event namespace." 
ms.author: danbrown
author: DHB-MSFT
manager: dansimp
ms.topic: reference
ms.service: msteams
audience: ITPro
ms.collection: 
- privacy-teams
- must-keep
hideEdit: true
ms.localizationpriority: medium
ms.date: 06/25/2025
appliesto: Microsoft Teams
---

# Diagnostic event namespaces for Microsoft Teams

Microsoft collects diagnostic events from your use of Microsoft 365 products, including Microsoft Teams. Diagnostic events can be collected through client-related diagnostic data (from [required diagnostic data](/microsoft-365-apps/privacy/required-diagnostic-data) and [optional diagnostic data](/microsoft-365-apps/privacy/optional-diagnostic-data)) and service-related diagnostic data (from [required service data](/microsoft-365-apps/privacy/required-service-data#service-calls-content-and-service-related-diagnostic-data)). We collect these events to make sure our apps and services are secure and up to date, to detect, diagnose and remediate problems, and to make product improvements. Events can be viewed in the Diagnostic Data Viewer, network protocol analyzers, and data subject rights (DSR) exports.

For more information about client-related and service-related diagnostic data for Microsoft 365 apps and services (such as Word, PowerPoint, Excel, Teams, and Microsoft 365 Copilot), see [Understanding Microsoft 365 diagnostic events in exported data](/microsoft-365-apps/privacy/diagnostic-events-exported-data).

> [!NOTE]
> Diagnostic events that are processed might have associated pseudonymous identifiers. A pseudonymous identifier can't be directly attributed to an individual without using additional information and is often used to protect personal privacy or improve data security by replacing personal identifiers with placeholder values. However, because a pseudonymous identifier can ultimately be linked to an individual, it's considered personal data.

All diagnostic events are grouped into event namespaces. Event namespaces indicate the feature, app, or service that the generated events are associated with. The following sections describe the event namespaces used to group events collected from your use of Microsoft Teams.

As an example, the following event represents the user action of clicking Meeting Recap (EventName: clickAINotesTab_click_meetingRecap) in Teams (AppName: Teams). More details about this event are available through the event namespaces [TeamsPremium](#teamspremium), [Copilot](#copilot), and [IntelligentRecap](#intelligentrecap) (EventCategory: TeamsPremium, Copilot, IntelligentRecap).

```json
{
  "time": "2025-03-13T13:47:24.438000+00:00",
  "correlationId": null,
  "properties": {
    "ActionTime": "2025-03-13T13:47:24.438Z",
    "AppName": "Teams",
    "Action": "meetingRecap",
    "Target": "",
    "IP": "",
    "InputMethod": "",
    "DevicePlatform": "Windows",
    "SearchTerm": "",
    "SearchResult": "",
    "BrowserType": "edge",
    "Location": "",
    "EventCategory": "TeamsPremium,Copilot,IntelligentRecap",
    "EventName": "clickAINotesTab_click_meetingRecap"
  }
}
```

## Avatar

Includes diagnostic events that represent user interactions related to the creation, customization, and management of avatars within meetings and application settings. This includes things like when users engage with avatars before joining a meeting, switch between different avatar views, or enable and disable avatars during meetings, and use immersive features such as launching and interacting with avatars in dedicated panels and customizing them in the side panel. Actions included can also be when users install or remove the avatar application, manage settings, and interact with coachmarks (temporary popups to guide users about functionality) for onboarding experiences. Avatar functionality is used with meeting controls, allowing users to enhance virtual presence through customizable digital representations.

## Channel

Includes diagnostic events related to all user actions related to channels, including managing messages, interactions, and organization of conversations within a team, creating, editing, and deleting channel posts, pinning/unpinning messages, translating content, and saving messages for later reference. This namespace also covers actions like immersive reading of messages, copying links to channel posts, and reacting to messages with emojis, managing tabs within a channel, navigating through files, and using various applications or custom features within channel threads. This namespace supports seamless communication and collaboration within Teams' structured group discussions.

## Chat

Includes diagnostic events focused on interactions within one-on-one and group chats, supporting actions such as sending and editing messages, reacting with emojis, and managing chat participants, opening and managing chat tabs, bookmarking messages, deleting or undoing sent messages and navigating through chat history, managing chat notifications, accessing people cards for direct messaging, and leveraging smart replies. This provides a cohesive experience for instant messaging in Teams, enabling efficient communication with individuals or groups while maintaining a streamlined interface for content organization.

## CMD (calls and meetings)

Includes diagnostic events that help understand interactions related to calling and meetings, including joining, scheduling, and managing meeting experiences,  initiating meetings from a calendar, joining calls via pre-join screens, and enabling various collaboration tools during a session. Functionalities such as screen sharing, enabling video, raising hands, and reacting with emojis are also included, as well as adding participants to meetings, starting recordings, enabling transcriptions, and changing meeting views. This provides insights into user engagement with Teams’ conferencing capabilities.

## CollabAction

Includes diagnostic events related to user activities in collaboration across various Teams functionalities, engaging in actions that involve meeting, calling, channel, chat, or file functionality, as well as activities like replying to messages, sending reactions, sharing files, creating new teams or channels, managing team members, engaging with meeting notes, sending invitations, initiating recordings, and editing shared documents.

## Copilot

Includes diagnostic events related to the success or failure of user interactions involving Microsoft’s AI assistant. These interactions can be things like a user engaging with Teams Copilot for chat and meeting assistance, using suggested prompts, interacting with generated insights, and rewriting text. These events don’t include prompts or responses, only diagnostics about the user’s interactions. Teams Copilot aids in summarizing meeting discussions, extracting action items, and providing intelligent recommendations in chats. This includes functionalities such as managing Teams Copilot settings and is aimed at understanding the overall usage patterns of the novel space of generative AI within Microsoft’s ecosystem.

## ESP (engagement surface platform)

Includes diagnostic events related to surfaces in Teams that highlight new features or updates to Teams, based on user context. For example, if a user logs into Teams after not using Teams for a long time, they may see a “What’s new” card that indicates new features or changes that happened since their last login. This event namespace focuses on instances where users see engagement surfaces like the above example, interact with those surfaces, and respond to platform-driven prompts, supporting relevant messages reaching users, and helping organizations deliver contextual information through the Teams interface.

## Files

Includes diagnostic events related to the success or failure of interactions with documents and file-sharing activities within Teams, including things like users opening files in native applications or within Teams, downloading files, renaming, moving, and copying documents, pinning important files as tabs, uploading new documents, creating new documents directly from Teams, and using cloud storage for seamless collaboration. This also helps understand file sharing within chat, channel, and meeting contexts, enabling efficient file management across Teams' collaborative ecosystem.

## IntelligentRecap

Includes diagnostic events focused on summarizing and extracting insights from meetings via Teams Copilot, including user interactions with AI-generated meeting notes, task assignments, transcript analysis, and participant feedback mechanisms. This enhances productivity by providing structured insights from meetings, allowing users to quickly review discussions and follow up on key points.

## LifeCycleActions

Includes diagnostic events related to synchronous and asynchronous user actions across meetings and chats. Synchronous interactions include things like starting a recording, sharing a whiteboard or a PowerPoint file, enabling live captions, and managing breakout rooms. Asynchronous interactions include things like reacting to messages in meeting chats, opening shared files, navigating to meeting recaps, and editing meeting options. This supports Teams understanding meaningful user interactions throughout the lifecycle of meetings and chats and isolating whether the action was considered synchronous or asynchronous.

## PlatformActive

Includes diagnostic events related to user engagement across various third-party applications and services within Teams, including interactions with bots, messaging extensions, and personal apps. Users open files, navigate through tabs, interact with adaptive cards, and invoke bots through commands or actions. This helps us understand application usage through notifications, pop-ups, and deep links, and gives us insights into how users engage with the platform's extensibility features, helping to improve app discoverability, efficiency, and user experience.

## PlatformEngaged

Includes diagnostic events focused on deeper third-party interactions within the Teams platform, including engagement with bot cards, messaging extensions, adaptive cards, and sending links. It also includes interactions like engaging with pop out tabs, opening personal apps, interacting with content bubbles, applying custom scenes in meetings, and engaging with external applications. This supports Teams understanding meaningful engagement of third-party hosted apps and optimizing interactions to enhance productivity across different collaboration experiences.

## SearchAction

Includes diagnostic events focused on user behavior related to search functions in Teams. It includes search initiation (typing in the search bar or executing a slash command), search execution (pressing enter or selecting a search query), and search engagement (clicking on results such as messages, people, files, or teams). This supports Teams improving the search experience, and improving relevance, speed, and accessibility of content for users.

## SimpleCollab

Includes diagnostic events related to actions within Teams that are attributed to features launched as a result of the SimpleCollab experience. These include creating custom sections, reordering items, and renaming sections. Users can filter and navigate conversations, toggle between different chat and channel views, and tailor their workspace based on their preferences and needs. This supports users streamlining their workflows by structuring their Teams environment via SimpleCollab to suit their needs.

## TeamsPhone

Includes diagnostic events related to all functionalities related to the cloud-based PBX phone service hosted via Teams. It includes call settings such as forwarding options, delegate management, and ringtone adjustments, and when users configure emergency call settings, toggle browser pop-outs, and join calls via various entry points. This provides insights into Teams Phone engagement, supporting enhancements to call quality, configuration flexibility, and accessibility.

## TeamsPremium

Includes diagnostic events related to advanced features available in Microsoft Teams' paid offerings. It includes diagnostics about protected meetings with watermarking, end-to-end encryption, and sensitivity labels, when users tailor their meetings with custom branding, utilize together mode scenes, or use premium meeting templates. It also gives diagnostics about additional intelligence features, including live captions translation, intelligent recap, and enhanced meeting recordings. This helps to enhance the security, customization, and intelligence of high-value meetings within Teams.

## TFLCollabAction

Includes diagnostic events related to collaborative actions within the Teams for Life (TFL) ecosystem. It includes diagnostics about scheduling meetings, sharing media during calls, managing communities, and interacting with chat messages. It also includes interactions around creating and editing posts, forwarding messages, reacting to content, and engaging in polls. This supports a seamless experience across various collaborative scenarios.

## UserStream

Includes diagnostic events related to telemetry from curated user data, providing a holistic view of user activity across Teams. It includes diagnostics about engagement with meetings, chats, channels, files, and Teams Copilot interactions. This supports analytics on user behaviors, helping organizations optimize feature usage, enhance adoption, and improve overall platform experience.

## Yammer

Includes diagnostic events focused on question and answer (Q&A) interactions within the Teams-Yammer interface. Yammer is now called Viva Engage and encompasses other community focused features. It includes diagnostics about displaying, dismissing, and engaging with Q&A coachmarks (temporary popups to guide users about functionality) to help users navigate and utilize the Q&A features efficiently. This helps improve the discoverability and usability of Yammer’s engagement features within Teams, fostering knowledge-sharing and community engagement.