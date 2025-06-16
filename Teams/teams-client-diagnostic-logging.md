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

Diagnostic data from clients is essential for triaging and mitigating problems. To streamline problem resolution, reduce overhead, and avoid end user interruptions, we're giving admins the ability to remotely gather diagnostic logs from users without end-user involvement. Admins can now remotely collect diagnostic logs from users’ machines, and client health can be monitored per-user from the users page within the Microsoft Teams admin center.

## Steps to gather diagnostic logs

1. Go to the **Users** tab on the left-hand navigation menu, and then select **Manage users**. Once there, navigate to the specific user page of the user you need diagnostic logs collected from.
1. On the user page, the **Client health** health tab provides more information about client health for all client versions that user is running.
1. Tihs page also allows you to gather diagnostic logs from a specific device or multiple devices.
1. Choose the client and version you want to collect diagnostic logs from and select the **Request client logs** option.
1. Once log collection is started, the **Client log status** column on this page with be set to **Pending**.
1. Once log collection is complete, you can download and share the logs with your team or Microsoft, and you can also view the collected logs. You can also view the status for all logs collected within your tenant.

## Manage Logs

You can delete one or all logs collected using the **Delete** option.

## Further information

- These logs will be stored for 30 days (in line with the standard EU guidelines).
- User consent is not required, as this is support data. Admins should have permissions to gather diagnostic logs, and this new functionality empowers admins to be able to collect these diagnostics remotely from users' devices without requiring any end-user interruptions.
- The types of logs collected are client logs and shell logs (media logs). There are no screenshots or heaps collected.
- The collection process will take 0-4 hrs if the device is online. The collection request expires after 3 days.
- Logs are stored in a Microsoft secure and compliant storage called the Outlook Diagnostics System. This is the same storage where M365 diagnostics and other diagnostics are currently being stored. This follows standard compliance practices.
