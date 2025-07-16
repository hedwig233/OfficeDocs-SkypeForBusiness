---
title: Accessing the Pro Management portal
author: mstonysmith
ms.author: tonysmit
manager: pamgreen
ms.reviewer: ayerragangu
ms.date: 7/15/2025
ms.topic: article
audience: Admin
ms.service: msteams
ms.subservice: itpro-rooms
appliesto: 
  - Microsoft Teams
ms.collection: 
  - M365-collaboration
  - teams-rooms-devices
  - Tier1
ms.localizationpriority: medium
search.appverid: MET150
description: Learn about how to access the Microsoft Teams Rooms Pro Management portal.
f1keywords: 
---

# Accessing the Pro Management portal

To access the Teams Rooms Pro Management portal, you need to assign one or more users to the below roles:

> [!IMPORTANT]
> Microsoft recommends that you use roles with the fewest permissions. Using lower permissioned accounts helps improve security for your organization. Global Administrator is a highly privileged role that should be limited to emergency scenarios when you can't use an existing role.

1. **Microsoft Entra built-in roles:** Global Administrator, Teams Administrator, Teams Devices Administrator, Global Reader. [Assign Microsoft Entra built-in roles](/entra/identity/role-based-access-control/permissions-reference) to the users using the [Microsoft Entra Admin center](https://entra.microsoft.com/#home).
2. Direct roles assignment within the Teams Rooms Pro Management Portal.

> [!NOTE]
> A Teams Administrator or a Teams Devices Administrator assigned to an Administrative Unit (AU), won't able to access Teams Rooms Pro Management portal, as AUs aren't yet supported. In such cases, consider assigning the users to the Teams Rooms Pro Management built-in roles (**Teams Rooms Pro Manager**, **Site Lead**, and **Site Technician**) or create a custom role. Check [Role Based Access Control](/microsoftteams/rooms/rooms-pro-rbac) for more information.

## How to assign users to the Teams Rooms Pro Manager role

Complete the following steps to assign users to the Teams Rooms Pro Manager role:

1. Log in to the [Teams Rooms Pro Management portal](https://portal.rooms.microsoft.com/) (GCC-High customers use [this link](http://devices.gov.teams.microsoft.us/)) using the administrator privileges outlined in this document.
1. Navigate to **Settings** > **Settings** > **Roles** and then select **Teams Rooms Pro Manager**.
1. Under **Teams Rooms Pro Manager** select the **Assignments** tab and then select **Add**.
1. Follow the wizard to name the assignment and select the users who should be added to it. The assignment will apply to all rooms and room groups.
5. At the end of the assignment wizard, select **Add assignment**.

Users who are assigned to the above-mentioned Microsoft Entra built-in roles or to the Teams Rooms Pro Manager role are responsible for the day-to-day management and monitoring of Teams Rooms and will have access to all rooms and features within the Teams Rooms Pro management portal. To assign additional roles to restrict access to specific rooms and users, see more under [Role Based Access Control](/microsoftteams/rooms/rooms-pro-rbac).

After you've assigned users to the Teams Rooms Pro Manager role, continue to the [Enroll a Teams Rooms device](enroll-a-device.md) to add a Teams Rooms device to the Teams Rooms Pro management portal.

