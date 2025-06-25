---
title: Export content with Copilot
author: MicrosoftHeidi
ms.author: heidip
manager: dansimp
ms.topic: article
audience: admin
ms.service: msteams
ms.date: 06/04/2025
description: In this article, you learn about how to export Teams content using Copilot.
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
  - NewAdminCenter_Update
  - seo-marvel-apr2020
ms.collection:
  - M365-collaboration
appliesto:
  - Microsoft Teams
---

# Microsoft 365 Copilot Interactions & Microsoft 365 Chat

The Copilot Activity Export API allows you to export Copilot interactions data, which includes the user prompt to Copilot and the Copilot response back to the user. This API captures the user intent and Copilot accessed resources and the response back to the user across Microsoft 365 Copilot apps such as Teams, Word, and Outlook.

## How to access Copilot Activity Export APIs

- **Example 1** is a simple query to retrieve all the copilot interactions without any filters (beta):

  ```HTTP
  GET https://graph.microsoft.com/beta/copilot/users/{id}/interactionHistory/getAllEnterpriseInteractions 
  ```
- **Example 2** is a simple query to retrieve all the copilot interactions with appclass filters (beta):

  ```HTTP
  GET https://graph.microsoft.com/beta/copilot/users/{id}/interactionHistory/getAllEnterpriseInteractions?$filter=appClass eq 'IPM.SkypeTeams.Message.Copilot.Teams or appClass eq 'IPM.SkypeTeams.Message.Copilot.BizChat' (beta)
  ```
## Prerequisites to access Copilot Activity Export APIs

Application permissions are used by apps that run without a signed-in user present. Only an administrator can approve application permissions. The following permissions are needed:
- *AiEnterpriseInteraction.Read.All*: enables access to all copilot interactions across Microsoft 365 apps and Microsoft 365 Chat
- A **Microsoft 365 Copilot license** is required for accessing the new Copilot Activity Export API.
