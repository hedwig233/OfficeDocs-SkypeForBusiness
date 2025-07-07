---
# Required metadata
# For more information, see https://learn.microsoft.com/en-us/help/platform/learn-editor-add-metadata
# For valid values of ms.service, ms.prod, and ms.topic, see https://learn.microsoft.com/en-us/help/platform/metadata-taxonomies

title: Plan for immersive events
description: Immersive events in Teams
author:      Sean-Kerawala # GitHub alias
ms.author:   sekerawa # Microsoft alias
ms.service: msteams
ms.topic: concept-article
ms.date:     07/03/2025
ms.subservice: meetings
---
# Plan for Teams immersive events

Teams Immersive lets you create, customize, and host immersive 3D events in Microsoft Teams.

- Schedule Teams Immersive events from Teams calendar

- Join an immersive event directly through Teams or Outlook Calendar

- Design 3D spaces and schedule immersive events for PC or Mac – no code or technical expertise required.

This page covers the required tasks and suggests functional roles that may need to know about the rollout, but follow your organization's standard rollout process, including change and configuration management.

1. Prepare your organization

1. Review minimum hardware requirements

1. Assign licenses to event organizers (only organizers require license)

1. Configure endpoints and firewalls

1. Check your bandwidth requirements

1. Work with stakeholders to communicate change

1. (optional) Enable guests to join immersive events 

1. (optional) Assign event policies to turn off Immersive events for users and groups

### Prepare your organization

Executive-level sponsorship is highly advisable to help with any cross-team blocking issues.

You need access to a few administration tools:

- Microsoft Admin Center is needed to manage and assign Teams Premium and/or Mesh Trial Licenses

- Teams Admin Center (TAC) is needed to configure avatar and immersive spaces administration.

- (optional) Purview Admin Center to create Sensitivity Labels

In addition, ensure all organizers and attendees of immersive events have access to Sharepoint and OneDrive. Event customizations often reference files such as images, videos, audio, or 3D models that are stored in Microsoft 365. Creating a Microsoft 365 Group can be a helpful way to enable secure content sharing.

### Hardware requirements

PC and Mac minimum hardware requirements are 4-core CPU & 8-GB RAM.

### License requirements

For Teams Immersive, your organization needs:

- __Teams Premium license in a tenant for Commercial use__ (currently only available in Teams Premium Introductory Pricing or Teams Premium for Departments). Learn more about [Microsoft Teams Premium licensing](/microsoftteams/teams-add-on-licensing/licensing-enhance-teams). Optionally, the Microsoft Mesh Trial is available in Microsoft Admin Center, which enables organizing Teams immersive events via Teams and Outlook Calendars. For organizations without Teams Premium, this trial enables rapidly onboarding to using Immersive events. Important! All users with the Teams Premium or Microsoft Mesh Trial license will be able to schedule immersive events. Co-organizers and attendees only require a prerequisite license (Microsoft E3 or E5 license).

- __Pre-requisite license for Teams Premium__. Your users must have a commercial Teams license: Microsoft Teams Enterprise, Teams Essentials, or one of the following M365, O365, or Business SKUs with Teams included: Microsoft 365 Business Basic, Microsoft 365 Business Standard, Microsoft 365 Business Premium, Microsoft 365 E3/E5, and Office 365 E1/E3/E5.

This section outlines the specific endpoints and firewall requirements for immersive events in Teams.

In general, the standard set of Microsoft 365 requirements outlined in [Microsoft M365 URLs and IP address ranges](/microsoft-365/enterprise/urls-and-ip-address-ranges?view=o365-worldwide&preserve-view=true) applies to all Teams Immersive event features. Configure your enterprise firewall settings to align with the standard set of Microsoft 365 requirements for __Microsoft Teams__, and __Microsoft 365 Common__ outlined in [Microsoft M365 URLs and IP address ranges](/microsoft-365/enterprise/urls-and-ip-address-ranges?view=o365-worldwide&preserve-view=true).

As part of these requirements, ensure that you configure your firewall to enable traffic to *.cloud.microsoft.com, *.office.com, *.graph.microsoft.com, *.substrate.office.com, and *.microsoft.com over TCP 443, 80.

Teams Immersive also requires the IP addresses and port ranges detailed in [Firewall configuration for Azure Communication Services](/azure/communication-services/concepts/voice-video-calling/network-requirements) for media capabilities such as audio and screen sharing. Without access to these endpoints, Teams Immersive may not work properly for users in your organization.

### Bandwidth requirements

The following network bandwidth requirements are designed to help users in your organization have the best possible experience with Teams immersive events.

While we're constantly working on improving how immersive events work even in poor network conditions, you may want to optimize your network if users in your organization report poor audio quality, audio cutting out, or delayed or jerky avatar movement.

Teams immersive experiences build on top of [Microsoft Teams network bandwidth requirements](/microsoftteams/prepare-network) for capabilities (such as video and screenshare), with extra bandwidth needed for immersive capabilities (such as avatar movement and spatial audio).

__Immersive participants__

- Minimum (kbps): 30/370

- Recommended (kbps): 80/700

- Best performance (kbps): 100/850

As an example, an immersive event with a participant sharing their screen requires a minimum of 440-kbps downstream, and 830-kbps upstream, and a maximum of 8,176-kbps downstream and 8,926-kbps upstream.

### Work with stakeholders that communicate change

The stakeholders listed above all have active steps which impact the setup of your Teams Immersive roll out, but there may be other parts of your org that will be impacted by the deployment or might have policies or guidelines that need to be considered early in your planning process. Here are some areas of your organization you might need to reach out to before you deploy.

- Change Communications: If you have a standard process for contacting users about pending changes, make sure Teams Immersive is part of those communications.

- Help Desk: Have a support plan in place for users who experience issues using Teams Immersive. Make sure your admins have a way to review issues experienced by users so they can be communicated to Microsoft as needed.

- Human Resources: While Teams Immersive doesn't require any specific action from Human Resources for deployment or operations, HR may be interested that immersive events are about creating 3D experiences for users. Check with your HR department for any policies that may impact your Mesh meeting experience.

- Company Branding: If you decide to create custom event experiences for your users, you should check with your company branding experts to make sure any meeting assets meets branding standards.

### Enable guests to join immersive events

Teams Immersive events are joinable by users within your organization and guests.

Some organizations may have trusted individuals they want to invite to their immersive event.

To add a guest, follow this [step-by-step guidance](https://support.microsoft.com/en-us/office/add-guests-to-a-team-in-microsoft-teams-fccb4fa6-f864-4508-bdde-256e7384a14f) for adding trusted guest users to your tenant via Microsoft Admin Center. 

> [!NOTE]
> Guests can be invited as attendees. Guests can't be organizers or co-organizers of Immersive events. External (cross-tenant) and anonymous users aren't currently supported.

### Turn immersive events on or off

Teams Immersive is on by default, meaning anyone with a Teams Premium or Mesh Trial license can schedule an immersive event. 

For admins seeking to limit specific users or groups from creating immersive events, navigate to Teams Admin Center and set Event Policies to turn off Immersive events policy.

Alternatively, if using PowerShell Module 7.1.0, the event policy "ImmersiveEvents" should be set to "Enabled". Syntax is New-CsTeamsEventsPolicy.

