---
title:  Teams client diagnostic logging in the Teams admin center
ms.author: heidip
author: MicrosoftHeidi
manager: jtremper
ms.topic: article
ms.date: 06/16/2025
ms.service: msteams
audience: admin
ms.collection: 
- M365-collaboration
- m365initiative-deployteams
ms.reviewer: shals
search.appverid: MET150
f1.keywords:
- NOCSH
description: Diagnostic logging for Teams client updates in the Teams admin center to manage client updates and prevent sedimentation.
appliesto: 
- Microsoft Teams
ms.localizationpriority: medium
---

# Diagnostic logs for Teams Client

> [!IMPORTANT]
> This article describes a Microsoft Teams feature that isn't released. It's announced, and it's coming soon. If you're an admin, you can find out when this feature is released in the Message Center (in the [Microsoft 365 admin center](https://portal.office.com/adminportal/home)). For more information, see: [Remote log collection](https://www.microsoft.com/microsoft-365/roadmap?msockid=37b3f69009a468232e49e575081e694c&searchterms=Remote+log+collection). This article provides an overview of the new tool for Teams admins to collect diagnostic logs for Teams clients from the Microsoft Teams admin center.
> 
> This feature is currently supported for Windows (non-VDI) and Mac Applications only.

Diagnostic data from clients is essential for triaging and mitigating problems. To streamline problem resolution, reduce overhead, and avoid end user interruptions, we're giving admins the ability to remotely gather diagnostic logs from Teams clients without end-user interruptions. Admins can now remotely collect diagnostic logs from users’ machines from the users page in the Microsoft Teams admin center.

## Steps to gather diagnostic logs

1. Go to the **Users** tab on the left-hand navigation menu, and then select **Manage users**. Once there, navigate to the specific user page of the user you need diagnostic logs collected from.
1. On the user page, the **Client health** health tab provides more information about client health for all client versions that user is running.
1. This page also allows you to gather diagnostic logs from a specific device or multiple devices.
1. Choose the client and version you want to collect diagnostic logs from and select the **Request client logs** option.
1. Once log collection is started, the **Client log status** column on this page with be set to **Pending**.
1. Once log collection is complete, you can download and share the logs with your team or Microsoft, and you can also view the collected logs. You can also view the status for all logs collected within your tenant.
1. You can also view the status for all logs collected within your tenant.

:::image type="content" source="media/diagnostic-log-walkthrough-screenshot.png" alt-text="A screenshot of the log collection page showing the steps to gather diagnostic logs outlined in this section of the article.":::

### Devices that use a government cloud account

Client log collection isn't supported on devices that have both commercial and government cloud accounts added simultaneously to the Teams client.

:::image type="content" source="media/diagnostic-log-ineligible.png" alt-text="A screenshot of the log collection page showing Ineligible under the Client log status column.":::

## Manage Logs

1. Selecting **View client logs** from the Teams client health page lets you view the status for all logs collected in your tenant.
1. This page shows tabs for in-progress and ready to download log requests.
  - You can also delete one or all logs collected using the **Delete** option.

## Further information

- These logs are stored for 30 days.
- Logs are stored in a Microsoft secure and compliant storage location.
- User consent isn't required and no prompt or message is shown to users when logs are collected.
- The types of logs collected are client logs and shell logs (media logs). There are no screenshots or heaps collected.
