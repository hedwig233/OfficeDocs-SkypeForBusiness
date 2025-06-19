---
title: "Acquire phone numbers for your organization"
author: sfrancis206
ms.author: scottfrancis
manager: pamgreen
ms.reviewer: julienp
ms.date: 2/27/2025
ms.topic: conceptual
ms.assetid: 6b61cb3c-361c-48a8-a9ef-d81bddde27bb
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: 
  - M365-voice
  - m365initiative-voice
  - highpri
  - Tier1
audience: Admin
appliesto: 
  - Skype for Business
  - Microsoft Teams
ms.localizationpriority: Medium
f1.keywords:
- CSH
ms.custom: 
  - ms.teamsadmincenter.voice.phonenumbers.overview
  - ms.teamsadmincenter.voice.searchandacquire.PSTNpartner
  - ms.lync.lac.NewNumberManualAcquisitionOpenSupportTicket
  - ms.lync.lac.VASAMissingGeoCodes
  - Calling Plans
  - seo-marvel-apr2020
description: Learn how to get telephone numbers for Microsoft Teams for your organization.
---

# Get telephone numbers in Microsoft Teams

**APPLIES TO:** ![Image of a checkmark for yes](/office/media/icons/success-teams.png)Microsoft Calling Plans, Operator Connect, Teams Phone Mobile, and Direct Routing

This article provides an overview and considerations for getting phone numbers in Microsoft Teams.

Telephone numbers aren't included with [Teams Phone licensing](teams-phone-licensing.md). Telephone numbers for your tenant are acquired through the service provider that provides your tenant with connectivity and access to the Public Switched Telephone Network (PSTN).

Once you get a PSTN connection to your tenant, you can then acquire telephone numbers from the service provider and assign the numbers to accounts that are licensed to use Teams Phone.

To learn more about the PSTN integrations available to you, see [PSTN Connectivity options](pstn-connectivity.md).

Once numbers are acquired and available in your tenant, they can be managed in the following administrative tools:

- Teams admin center (TAC)
- Teams PowerShell
- On-premises Active Directory (for Direct Routing on-premises numbers)

To learn more, see [Manage phone numbers for users](assign-change-or-remove-a-phone-number-for-a-user.md).

## Prerequisites

Before you can get telephone numbers in Teams, you must have a phone number services agreement and a tenant integration with one or more PSTN service providers. To learn more, see [PSTN Connectivity options](pstn-connectivity.md).

## Number usage types

Number usages define the services that support a given phone number. The following table lists the number usage types supported with Microsoft Teams Phone.

|Number usage |Usage type and purpose |Number type supported |
|:-----|:-----|:-----|
|**User** |User (subscriber) <br>These numbers are for users or devices in your organization. |Geographic (Toll) |
|**Voice app** |Call queue and Auto attendant <br>Voice app service numbers are for assigning to resource accounts that support voice applications. |Geographic (Toll) <br>Toll-free |
|**Conference** |Dedicated conference bridge <br>Conference service numbers are for assigning to conference bridges so that users can dial-by-phone into a Teams meeting. |Geographic (Toll) <br>Toll-free |

### Acquiring and managing telephone numbers

How you acquire and manage telephone numbers depends on your PSTN connectivity solution. Use the following table to learn more about how to acquire numbers for your tenant:

|PSTN connectivity solution |Guidance for acquiring and managing numbers |
|:-----|:-----|
|Microsoft Calling Plan |[Get phone numbers with Microsoft Calling Plans](getting-phone-numbers-for-your-users.md) |
|Operator Connect |[Get phone numbers with Operator Connect](get-phone-numbers-with-operator-connect.md) |
|Teams Phone Mobile |[Get phone numbers with Teams Phone Mobile](operator-connect-mobile-configure.md#step-2-manage-phone-numbers-and-assign-licenses)|
|Direct Routing |[Get phone numbers with Direct Routing](get-phone-numbers-with-direct-routing.md) |

## Related articles

- [Set up telephone numbers with Calling Plans](manage-phone-numbers-for-your-organization/manage-phone-numbers-for-your-organization.md)

- [Set up telephone numbers with Operator Connect](operator-connect-configure.md#set-up-phone-numbers)

- [Set up telephone numbers with Teams Phone Mobile](operator-connect-mobile-configure.md#step-2-manage-phone-numbers-and-assign-licenses)

- [Set up telephone numbers with Direct Routing](direct-routing-enable-users.md#configure-the-phone-number-and-enable-enterprise-voice)

- [Manage phone numbers for users](assign-change-or-remove-a-phone-number-for-a-user.md)

- [Plan Direct Routing](direct-routing-plan.md)

- [Configure Direct Routing](direct-routing-configure.md)
