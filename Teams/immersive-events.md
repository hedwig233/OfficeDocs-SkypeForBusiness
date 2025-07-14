---
# Required metadata
# For more information, see https://learn.microsoft.com/en-us/help/platform/learn-editor-add-metadata
# For valid values of ms.service, ms.prod, and ms.topic, see https://learn.microsoft.com/en-us/help/platform/metadata-taxonomies

title: Plan for immersive events
description: Immersive events in Teams
author:      Sean-Kerawala # GitHub alias
ms.author:   sekerawa # Microsoft alias
manager: tyadams
ms.service: msteams
ms.topic: concept-article
ms.date:     07/07/2025
ms.subservice: meetings
---
# Plan for Teams immersive events

> [!NOTE]
> This feature is currently in Public Preview.

Teams Immersive lets your users create, customize, and host immersive 3D events in Microsoft Teams. With Teams Immersive, users can:

- Schedule Teams Immersive events from Teams calendar

- Join an immersive event directly through Teams or Outlook Calendar

- Design 3D spaces and schedule immersive events for PC or Mac – no code or technical expertise required.

## Turn on Teams Public Preview to use Immersive events

To use Immersive Events in Microsoft Teams, both organizers and attendees must be on the Public Preview build. Without Public Preview, users can only access Generally Available features and can't receive early access to new features.

### Steps for your users to join Public Preview

1. Your users can send you a request to join the Public Preview program. To allow them to join, you must first set up a __Teams Update policy__. To learn more about managing the Update policy, see [Public preview in Microsoft Teams](public-preview-doc-updates.md#set-the-update-policy).
2. Once you set the __Teams Update policy__, users can open the Teams app and select __Settings and more (...)__ next to their user profile.
3. Select __Settings__ > __About Teams__.
4. Under __Early access__, select the __Public preview__ checkbox.
5. They should confirm that they have either a Teams Premium or Mesh Trial license.
6. On their PC or Mac, select __Calendar__, toggle __New Calendar__ to __Off__.
7. Now, they can join or customize an event via Teams desktop on PC or Mac.

This page for admins covers the required tasks and suggests functional roles that you might need to know about the rollout. You should follow your organization's standard rollout process, including change and configuration management. The following steps are outlined in this article:

1. [Prepare your organization](#prepare-your-organization)

1. [Review minimum hardware requirements](#hardware-requirements)

1. [Assign licenses to event organizers (only organizers require a license)](#license-requirements)

1. [Configure endpoints and firewalls](#endpoints-and-firewall)

1. [Check your bandwidth requirements](#bandwidth-requirements)

1. [Work with stakeholders to communicate change](#work-with-stakeholders-that-communicate-change)

1. (optional) [Allow guests to join immersive events](#allow-guests-to-join-immersive-events)

1. (optional) [Assign event policies to turn off Immersive events for users and groups](#manage-who-can-schedule-immersive-events-through-powershell)

For details on the Teams Immersive events experience for your users, see [Get started with immersive events in Microsoft Teams](https://support.microsoft.com/topic/a69189df-39c7-478f-a335-0aef7c4e5781).

## Prepare your organization

Executive-level sponsorship is highly advisable to help with any cross-team blocking issues.

You need access to a few administration tools:

- Microsoft Admin Center is needed to manage and assign Teams Premium and/or Mesh Trial Licenses

- Teams Admin Center is needed to configure avatar and immersive spaces administration.

- (optional) Purview Admin Center to create Sensitivity Labels.

In addition, ensure all organizers and attendees of immersive events have access to Sharepoint and OneDrive. Event customizations often reference files such as images, videos, audio, or 3D models that are stored in Microsoft 365. Creating Microsoft 365 Groups can be a helpful way to enable secure content sharing.

## Hardware requirements

PC and Mac minimum hardware requirements are 4-core CPU & 8-GB RAM.

## License requirements

For Teams Immersive, your organization needs:

- __Teams Premium license in a tenant for Commercial use__ (currently only available in Teams Premium Introductory Pricing or Teams Premium for Departments). Learn more about [Microsoft Teams Premium licensing](/microsoftteams/teams-add-on-licensing/licensing-enhance-teams). Optionally, the Microsoft Mesh Trial is available in Microsoft Admin Center, which enables organizing Teams immersive events via Teams and Outlook Calendars. For organizations without Teams Premium, this trial enables rapidly onboarding to using Immersive events. Important! All users with the Teams Premium or Microsoft Mesh Trial license can schedule immersive events. Co-organizers and attendees only require a prerequisite license (Microsoft E3 or E5 license).

- __Pre-requisite license for Teams Premium__. Your users must have a commercial Teams license: Microsoft Teams Enterprise, Teams Essentials, or one of the following Microsoft 365, or Business SKUs with Teams included: Microsoft 365 Business Basic, Microsoft 365 Business Standard, Microsoft 365 Business Premium, Microsoft 365 E3/E5, and Office 365 E1/E3/E5.

This section outlines the specific endpoints and firewall requirements for immersive events in Teams.

In general, the standard set of Microsoft 365 requirements outlined in [Microsoft Microsoft 365 URLs and IP address ranges](/microsoft-365/enterprise/urls-and-ip-address-ranges?view=o365-worldwide&preserve-view=true) applies to all Teams Immersive event features. Configure your enterprise firewall settings to align with the standard set of Microsoft 365 requirements for __Microsoft Teams__, and __Microsoft 365 Common__ outlined in [Microsoft Microsoft 365 URLs and IP address ranges](/microsoft-365/enterprise/urls-and-ip-address-ranges?view=o365-worldwide&preserve-view=true).

## Endpoints and firewall

As part of these requirements, ensure that you configure your firewall to enable traffic to *.cloud.microsoft.com, *.office.com, *.graph.microsoft.com, *.substrate.office.com, and *.microsoft.com over TCP 443, 80.

Teams Immersive also requires the IP addresses and port ranges detailed in [Firewall configuration for Azure Communication Services](/azure/communication-services/concepts/voice-video-calling/network-requirements) for media capabilities such as audio and screen sharing. Without access to these endpoints, Teams Immersive might not work properly for users in your organization.

## Bandwidth requirements

The following network bandwidth requirements are designed to help users in your organization have the best possible experience with Teams immersive events.

While we're constantly working on improving how immersive events work even in poor network conditions, you might want to optimize your network if users in your organization report poor audio quality, audio cutting out, or delayed or jerky avatar movement.

Teams immersive experiences build on top of [Microsoft Teams network bandwidth requirements](/microsoftteams/prepare-network) for capabilities (such as video and screenshare), with extra bandwidth needed for immersive capabilities (such as avatar movement and spatial audio).

### Immersive participants

- Minimum (kbps): 30/370

- Recommended (kbps): 80/700

- Best performance (kbps): 100/850

As an example, an immersive event with a participant sharing their screen requires a minimum of 440-kbps downstream, and 830-kbps upstream, and a maximum of 8,176-kbps downstream and 8,926-kbps upstream.

## Work with stakeholders that communicate change

The stakeholders listed above all have active steps, which affect the setup of your Teams Immersive roll out. However, the deployment might also affect other parts of your organization, or there could be policies and guidelines that should be considered early in the planning process. Here are some areas of your organization you might need to reach out to before you deploy.

- Change Communications: If you have a standard process for contacting users about pending changes, make sure Teams Immersive is part of those communications.

- Help Desk: Have a support plan in place for users who experience issues using Teams Immersive. Make sure your admins have a way to review issues experienced by users so they can be communicated to Microsoft as needed.

- Human Resources: While Teams Immersive doesn't require any specific action from Human Resources for deployment or operations, HR might be interested that immersive events are about creating 3D experiences for users. Check with your HR department for any policies that might affect your Mesh meeting experience.

- Company Branding: If you decide to create custom event experiences for your users, you should check with your company branding experts to make sure any meeting assets meets branding standards.

## Allow guests to join immersive events

Teams Immersive events are joinable by users within your organization and guests.

Some organizations might have trusted individuals they want to invite to their immersive event.

To add a guest, follow the [step-by-step guidance](https://support.microsoft.com/en-us/office/add-guests-to-a-team-in-microsoft-teams-fccb4fa6-f864-4508-bdde-256e7384a14f) for adding trusted guests to your tenant via Microsoft Admin Center.

> [!NOTE]
> Guests can be invited as attendees. Guests can't be organizers or co-organizers of Immersive events. External (cross-tenant) and anonymous users aren't currently supported.

## Manage who can schedule immersive events through PowerShell

You can use PowerShell to manage who can schedule immersive events in your organization.

To manage who can schedule immersive events, use the __`-ImmersiveEvents`__ parameter within the PowerShell [__CsTeamsEventsPolicy__](/powershell/module/teams/set-csteamseventspolicy) cmdlet.

### Turn off immersive events

To prevent organizers with this policy from creating immersive, use the following script:

```powershell
Set-CsTeamsEventsPolicy -Identity <policy name> -ImmersiveEvents Disabled
```

### Turn on immersive events

To allow organizers with this policy to create immersive events, use the following script:

```powershell
Set-CsTeamsEventsPolicy -Identity <policy name> -ImmersiveEvents Enabled
```

Tp learn more about __`-ImmersiveEvents`__  policies in PowerShell, see  [Set-CsTeamsEventsPolicy](/powershell/module/teams/set-csteamseventspolicy).

## Platform support

- Immersive events in Teams is available only on PC and MAC, not on web.
- Users can still schedule on web, but to join the immersive event, they must use a PC/MAC.
- Quest is not yet supported for Immersive events

## Endpoint availability

- Supported: Teams app on PC and Mac (*app on Meta Quest headset coming soon)

- Not supported: Teams on Web, Teams on Mobile, VDI (Virtual Machine) support, Microsoft Teams Rooms, Dial-In

## User type support

- Supported: Users in your organization (same tenant) and guest users

- Not supported: Cross-tenant (external) and anonymous users

## Known limitations

- Immersive events aren't currently available on Meta Quest headset (Quest app coming soon).

- In an immersive customization session, there is no way to play a video or audio for preview. Video and audio objects can only be played during the live event.

- The user doing a screen share doesn't see the screenshare content on the screen share object in the event. However, the content appears for everyone else in the event.

- Screen share doesn't include content audio. As a workaround, to play video during presentations, use a video object.

## Related topics

- [Get started with immersive events in Microsoft Teams](https://support.microsoft.com/topic/a69189df-39c7-478f-a335-0aef7c4e5781)
- [Plan meetings](plan-meetings.md)
- [Plan webinars](plan-webinars.md)
- [Plan town halls](plan-town-halls.md)
