---
title: Overview of security and compliance
author: MSFTTracyP
ms.author: tracyp
manager: laurawi
ms.date: 04/04/2025
ms.topic: concept-article
ms.service: msteams
ms.reviewer:
audience: admin
description: An overview of Microsoft Teams security and compliance features including privacy and encryption, auditing and reporting, and more.
ms.localizationpriority: medium
search.appverid: MET150
ms.collection:
  - M365-collaboration
  - remotework
  - purview-compliance
  - essentials-security
  - essentials-compliance
f1.keywords:
  - CSH
ms.custom:
  - ms.teamsadmincenter.dashboard.helparticle.securityandcompliance
  - seo-marvel-apr2020
  - seo-marvel-jun2020
appliesto:
  - Microsoft Teams
---

# Security and compliance in Microsoft Teams

Microsoft Teams is built on the Microsoft 365 and Office 365 hyper-scale, enterprise-grade cloud, delivering the advanced security and compliance capabilities our customers expect. This article contains Teams-specific security and compliance information. Don't miss these Microsoft Mechanics videos about security and compliance:

- [Microsoft Teams Essentials for IT: Security and Compliance](https://youtu.be/91lHNKVVvQ4) (12:42 min)
- [Microsoft Teams Controls for Security and Compliance](https://www.youtube.com/watch?v=Km4T4hMM__k) (10:54 min)

> [!IMPORTANT]
> As a customer of Microsoft 365 or Office 365, you own and control your data. Microsoft doesn't use your data for anything other than providing you with the service you subscribed to. As a service provider, we don't scan your email, documents, or teams for advertising or for purposes that aren't service-related. Microsoft doesn't have access to uploaded content. Like OneDrive and SharePoint in Microsoft 365, customer data stays within the tenant. You can check out more about our trust and security related information at the [Microsoft Trust Center](https://microsoft.com/trustcenter). Teams follows the same guidance and principles as the Microsoft Trust Center.

## Security

Teams enforces the following security measures:

- Team-wide and organization-wide two-factor authentication.
- Single sign-on through Microsoft Entra ID.
- Encryption of data in transit and at rest.

SharePoint encryption handles files stored in SharePoint. OneNote encryption handles notes stored in OneNote. OneNote data is stored in the team SharePoint site. You can also use the Wiki tab for note taking, and that content is also stored within the team SharePoint site.

For more information about authentication, see [Identity models and authentication](identify-models-authentication.md). For more information about modern authentication, see [How modern authentication works](sign-in-teams.md).

Because Teams works in partnership with SharePoint, OneNote, Exchange, and more, you should be comfortable managing security in Microsoft 365 or Office 365 all-up. To learn more, read about [how to configure your Microsoft 365 or Office 365 organization for increased security](/office365/securitycompliance/tenant-wide-setup-for-increased-security).

> [!NOTE]
> Currently, [private channels](private-channels.md) supports limited security and compliance features. Support for the full set of security and compliance features in private channels is coming soon.

### Microsoft Defender for Office 365

Defender for Office 365 has extended protection features for Microsoft Teams. For more information, see [Microsoft Defender for Office 365 support for Microsoft Teams](/defender-office-365/mdo-support-teams-about).

### Secure Score

Microsoft Secure Score is a measurement of an organization's security posture, with a higher number indicating more improvement actions taken. It can be found in the [Microsoft 365 security center](https://security.microsoft.com/securescore). Following the Secure Score recommendations can protect your organization from threats. From a centralized dashboard in the Microsoft 365 security center, organizations can monitor and work on the security of their Microsoft 365 identities, apps, and devices. Microsoft Teams now has recommendations on Secure Score and administrators are encouraged to monitor their security stance on the platform.

Secure Score helps organizations:

- Report on the current state of the organization's security posture.
- Improve their security posture by providing discoverability, visibility, guidance, and control.
- Compare with benchmarks and establish key performance indicators (KPIs).

### How Conditional Access policies work for Teams

Microsoft Teams relies heavily on Exchange Online and SharePoint for core productivity scenarios. For example:

- Meetings
- Calendars
- Interop chats
- File sharing

Conditional Access policies for these cloud apps apply to Microsoft Teams when a user directly signs in to Microsoft Teams on any client.

Microsoft Teams is supported separately as a cloud app in Microsoft Entra Conditional Access policies. Conditional Access policies that are set for the Microsoft Teams cloud app apply to Microsoft Teams when a user signs in. However, without the correct policies on other apps like Exchange Online and SharePoint, users might still be able to access those resources directly. For more information about setting up a Conditional Access policy in the Azure portal, see [Microsoft Entra Quickstart](/azure/active-directory/active-directory-conditional-access-azure-portal-get-started).

Microsoft Teams desktop clients for Windows and Mac support modern authentication. Modern authentication brings sign-in based on the Microsoft Authentication Library (MSAL) to Microsoft Office client applications across platforms.

Microsoft Teams desktop application supports AppLocker. For more information about AppLocker prerequisites, see requirements to use [AppLocker](/windows/security/threat-protection/windows-defender-application-control/applocker/requirements-to-use-applocker).

## Compliance

Teams has support for a wide range of information in Microsoft Purview solutions to help you with compliance areas, including:

- Communication compliance for channels, chats, and attachments.
- Retention policies.
- Data loss prevention (DLP).
- eDiscovery and legal hold for channels, chats, and files.
- Audit log search.
- Mobile application management with Microsoft Intune.

This article provides information on these areas, and you can use [Microsoft Purview](https://purview.microsoft.com/) to manage these solutions.

### Auditing

Microsoft Purview Audit (Standard), Microsoft Purview Audit (Premium), and audit log search plug right into Microsoft Purview. These features enable you to set alerts and report on audit events. You can export specific or generic event sets for investigation. You can set up alerts for all audit log data within the Microsoft Purview portal, and filter and export this data for further analysis. For more information, see [Search the audit log for events in Microsoft Teams](/purview/audit-teams-audit-log-events).

### Communication compliance

Microsoft Purview Communication Compliance allows you to add users to policies that examine Microsoft Teams communications for the following types of content:

- Offensive language.
- Sensitive information.
- Information related to internal and regulatory standards.

You can scan the following types of communication to minimize the communication risks in your organization:

- Chat in public and private Teams channels.
- Individual chats.
- Attachments.

For more information, see [Learn about communication compliance](/purview/communication-compliance).

### Content search

You can use content search to search for all Teams data through rich filtering capabilities. You can export the results to a specific container for compliance and litigation support. You can take this action with or without an eDiscovery case. This feature enables compliance admins to gather Teams data from all users, review it, and then export it for further processing. For more information, see [Content Search](/purview/ediscovery-teams-content-search).

> [!TIP]
> You can filter content searches by Microsoft Teams specific content, such as Chat and Channel Messages, Meetings, and Calls. For more information, see [Content search in Microsoft Teams](/purview/ediscovery-teams-content-search).

### Customer Key

Microsoft 365 offers an extra layer of encryption on top of service encryption for your content. Customer Key uses encryption keys you provide to encrypt different types of data in Microsoft Teams. Customer Key at the application level encrypts Teams files stored in SharePoint. For more information, see [Service encryption with Microsoft Purview Customer Key](/purview/customer-key-overview).

Customer Key at the tenant level encrypts the following data:

- Teams chat messages (1:1 chats, group chats, meeting chats, and channel conversations).
- Teams media messages (images, code snippets, videos, and wiki images).
- Teams calls and meeting recordings stored in Teams storage.
- Teams chat notifications.
- Teams chat suggestions.
- Teams status messages.

For more information, see the following articles:

- [Overview of Customer Key at the tenant level](/purview/customer-key-overview)
- [New Microsoft Purview Information Protection capabilities to know and protect your sensitive data](https://techcommunity.microsoft.com/t5/microsoft-security-and/announcing-new-microsoft-information-protection-capabilities-to/ba-p/1999692)
- [Customer Key support for Microsoft Teams now in Public Preview](https://techcommunity.microsoft.com/t5/microsoft-teams-blog/customer-key-support-for-microsoft-teams-now-in-public-preview/ba-p/1999893)

### Data Loss Prevention (DLP)

Microsoft Purview Data Loss Prevention (DLP) in Microsoft Teams, and the larger DLP story for Microsoft Purview, revolves around business readiness when it comes to protecting sensitive documents and data. Whether you have concerns around sensitive information in messages or documents, DLP policies help ensure your users don't share this sensitive data with the wrong people.

For information on Data Loss Prevention in Teams, see [DLP for Microsoft Teams](/purview/dlp-microsoft-teams). A good article for DLP concerns is [Learn about data loss prevention](/purview/dlp-learn-about-dlp).

### eDiscovery

Microsoft Purview eDiscovery (Premium) supports the electronic aspect of identifying, collecting, and producing electronically stored information (ESI) in response to a request for production in a law suit or investigation. Capabilities include:

- Case management.
- Preservation.
- Search.
- Analysis.
- Export of Teams data:
  - Chats.
  - Messaging and files.
  - Meeting and call summaries. A summary of events is created and made available in eDiscovery.

For more information, see the following articles:

- [Conduct an eDiscovery investigation of content in Microsoft Teams](/purview/ediscovery-teams-investigation).
- [eDiscovery](/purview/ediscovery-manage-legal-investigations)
- [Content search](/purview/ediscovery-content-search-overview)

### Information barriers

Microsoft Purview Information Barriers enable you to create policies to keep people or groups from communicating with one another. For example:

- No business need for the parties to communicate.
- Regulations prevent the parties from communicating.

Microsoft Purview Information Barriers also allows you to set policies relating to things like lookups and eDiscovery. These policies can affect users in 1:1 chats, group chats, or at a team-level.

For more information, see [Information barriers in Microsoft Teams](/purview/information-barriers-teams).

### Legal hold

During litigation, you might need to preserve all data associated with a user (custodian) or a Team to use as evidence for the case. You can do this by placing either a user (user mailbox) or a Team on legal hold. For a team legal hold, the team's mailbox can be put on the following holds:

- In-Place Hold (a subset of the mailbox or site collection through targeted queries or filtered content is put on hold), or
- Litigation Hold (the entire mailbox or site collection is placed on hold).

In either case, once the hold is set it ensures that, even if end users delete or edit channel messages that are in the group mailbox, immutable copies of that content are maintained and available through eDiscovery search. Legal holds are typically applied within the context of an eDiscovery case.

See [Overview of retention policies](/purview/retention) to understand more about preservation and holds in Microsoft Purview. For more Teams-specific information on legal hold, we also have [Place a Microsoft Teams user or team on legal hold](/purview/ediscovery-teams-legal-hold) for you to learn more.

### Retention policies

Retention policies in Microsoft Teams allow you to meet the following scenarios:

- Retain data for regulatory, legal, business, or other reasons.
- Remove irrelevant content and communications.
- Retain data for a prescribed period of time and then remove it.

For more information, see [Retention policies in Microsoft Teams](retention-policies.md).

### Sensitivity labels

Apply [sensitivity labels](/purview/sensitivity-labels) to protect and regulate access to sensitive organizational content created during collaboration within teams. For example:

- Apply labels that configure the privacy of teams (public or private).
- Control guest access and external sharing.
- Manage access from unmanaged devices.

For more information, see [Sensitivity labels in Microsoft Teams](sensitivity-labels.md).

## Privacy

At Microsoft, protecting your data is our highest priority. To learn about our privacy practices, see the following articles:

- [Privacy at Microsoft](https://www.microsoft.com/trust-center/privacy)
- [Our commitment to privacy and security in Microsoft Teams](https://www.microsoft.com/microsoft-365/blog/2020/04/06/microsofts-commitment-privacy-security-microsoft-teams/)
- [For IT professionals: Privacy and security in Microsoft Teams](https://www.microsoft.com/microsoft-365/blog/2020/04/06/it-professionals-privacy-security-microsoft-teams/#:~:text=We%20safeguard%20your%20privacy%20by,and%20distribution%20of%20your%20data.)

## Information Protection Architecture

The following figure indicates the ingestion flow of Teams data to both Exchange and SharePoint for Teams Files and Messages.

:::image type="content" alt-text="Diagram of the workflow of Teams data to Exchange and SharePoint." source="media/Overview_of_security_and_compliance_in_Microsoft_Teams_image1.png" lightbox="media/Overview_of_security_and_compliance_in_Microsoft_Teams_image1.png":::

The following figure indicates the ingestion flow of Teams Meetings and calling data to Exchange.

:::image type="content" alt-text="Diagram of the workflow of Teams Meetings and calling data to Exchange." source="media/Overview_of_security_and_compliance_in_Microsoft_Teams_image1a.png" lightbox="media/Overview_of_security_and_compliance_in_Microsoft_Teams_image1a.png":::

> [!IMPORTANT]
> There can be up to a 24-hour delay to discover Teams content.

## Licensing

When it comes to information protection capabilities, Microsoft 365 subscriptions, Office 365 subscriptions, and the associated standalone licenses determine the available features.

For information on determining the licensing needs to implement features for security and compliance, see the [licensing requirements](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance) for security and compliance features.

> [!NOTE]
> Content search, eDiscovery (Standard), and eDiscovery (Premium) don't need to be enabled in Microsoft Purview to work. For more information, see [Microsoft 365 eDiscovery solutions](/purview/ediscovery).

## Location of data in Teams

Data in Teams resides in the geographic region associated with your Microsoft 365 or Office 365 organization. To see what regions are currently supported, see [Location of data in Microsoft Teams](privacy/location-of-data-in-teams.md).

If you need to see which region houses data for your tenant, go to the [Microsoft 365 admin center](https://portal.office.com/adminportal/home) > **Settings** \> **Organization profile**. Scroll down to **Data location**.

:::image type="content" alt-text="Screenshot of Data location table including Teams in the admin center." source="media/Overview_of_security_and_compliance_in_Microsoft_Teams_image5.png":::

## Compliance standards

Teams uses the following standards:

- [ISO 27001](/microsoft-365/compliance/offering-iso-27001)
- [ISO 27018](/microsoft-365/compliance/offering-iso-27018)
- [SSAE18 SOC 1 and SOC 2](/microsoft-365/compliance/offering-soc)
- [HIPAA](/microsoft-365/compliance/offering-hipaa-hitech)
- [EU Model Clauses (EUMC)](/microsoft-365/compliance/offering-eu-model-clauses).

Within the Microsoft compliance framework, Microsoft classifies Microsoft 365 and Office 365 applications and services into four categories. Each category is defined by specific compliance commitments that must be met for a Microsoft 365 or Office 365 service, or a related Microsoft service, to be listed in that category.

For more information, see [Data Protection Resources](https://servicetrust.microsoft.com/ViewPage/TrustDocumentsV3?command=Download&downloadType=Document&downloadId=b7d05b86-c69b-41ba-8245-21161b9febf9&tab=7f51cb60-3d6c-11e9-b2af-7bb9f5d2d913&docTab=7f51cb60-3d6c-11e9-b2af-7bb9f5d2d913_Compliance_Guides). Teams also supports Cloud Security Alliance compliance.

## Related articles

- [Microsoft 365 Security](/microsoft-365/security/)
- [Microsoft Purview](/purview/)
- [Microsoft compliance offerings](/microsoft-365/compliance/offering-home)
