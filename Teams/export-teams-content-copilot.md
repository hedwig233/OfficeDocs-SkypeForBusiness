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

- **Example 1** is a simple query to retrieve all the copilot interactions without any filters:

  ```HTTP
  GET https://graph.microsoft.com/v1.0/copilot/users/{id}/interactionHistory/getAllEnterpriseInteractions 
  ```
- **Example 2** is a simple query to retrieve all the copilot interactions with appclass filters:

  ```HTTP
  GET https://graph.microsoft.com/v1.0/copilot/users/{id}/interactionHistory/getAllEnterpriseInteractions?$filter=appClass eq 'IPM.SkypeTeams.Message.Copilot.Teams or appClass eq 'IPM.SkypeTeams.Message.Copilot.BizChat'
  ```
## Prerequisites to access Copilot Activity Export APIs

Application permissions are used by apps that run without a signed-in user present. Only an administrator can approve application permissions. The following permissions are needed:
- *AiEnterpriseInteraction.Read.All*: enables access to all copilot interactions across Microsoft 365 apps and Microsoft 365 Chat
- A **Microsoft 365 Copilot license** is required for accessing the new Copilot Activity Export API.
## Supported appClass Filters:

The following appClass filters are supported:

- `IPM.SkypeTeams.Message.Copilot.Word`

- `IPM.SkypeTeams.Message.Copilot.Excel`

- `IPM.SkypeTeams.Message.Copilot.Teams`

- `IPM.SkypeTeams.Message.Copilot.BizChat`

- `IPM.SkypeTeams.Message.Copilot.WebChat`

These filters allow you to specify the type of Copilot interactions you want to retrieve based on the app class. Rest of the interactions are not supported.

#### Known issue:

It has been observed that for some interactions in Teams Meeting Copilot, the `contexts[]` may be missing in the `aiResponse` interactions. The corresponding user prompt, however, always includes the `contexts[]` to ensure accurate context retrieval. The development team is aware of this problem and is working on a resolution.  Below example shows a userprompt, aiResponse pair that has valid contexts[] in the userprompt and missing contexts[] in the corresponding aiResponse. 

```json
[
    {
        "id": "1746757256660",
        "sessionId": "19:-SMwOyVjy2H3_BnsIO6WGUTXwuN1_BIw4U2TP4UcCwo1@thread.v2",
        "requestId": "db42bee0-7cfb-451f-8eb6-f929762ee970",
        "appClass": "IPM.SkypeTeams.Message.Copilot.Teams",
        "interactionType": "userPrompt",
        "conversationType": "appchat",
        "etag": "1746757256660",
        "createdDateTime": "2025-05-09T02:20:56.66Z",
        "locale": "en-us",
        "contexts": [
            {
                "contextReference": "https://microsoft.teams.com/threads/19:meeting_MTQ4ZDdkMzktYjhkZC00ODdlLTkwN2UtYzcwYjVmOWIxYTNm@thread.v2",
                "displayName": "Teams Meeting Copilot",
                "contextType": "TeamsMeeting"
            }
        ],
        "from": {
            "@odata.type": "#microsoft.graph.chatMessageFromIdentitySet",
            "application": null,
            "device": null,
            "user": {
                "@odata.type": "#microsoft.graph.teamworkUserIdentity",
                "id": "886cb6c8-eb73-4f72-ad99-69ebf43f70ad",
                "displayName": "8:orgid:886cb6c8-eb73-4f72-ad99-69ebf43f70ad",
                "userIdentityType": "aadUser",
                "tenantId": "bcefad10-7e12-4123-8457-f3ac71b098db"
            }
        },
        "body": {
            "contentType": "text",
            "content": "what was this meeting about?&lt;attachment id=\"19:meeting_MTQ4ZDdkMzktYjhkZC00ODdlLTkwN2UtYzcwYjVmOWIxYTNm@thread.v2\"&gt;&lt;/attachment&gt;"
        },
        "attachments": [
            {
                "attachmentId": "19:meeting_MTQ4ZDdkMzktYjhkZC00ODdlLTkwN2UtYzcwYjVmOWIxYTNm@thread.v2",
                "contentType": "reference",
                "contentUrl": "https://microsoft.teams.com/threads/19:meeting_MTQ4ZDdkMzktYjhkZC00ODdlLTkwN2UtYzcwYjVmOWIxYTNm@thread.v2",
                "content": null,
                "name": "Teams Meeting Copilot"
            }
        ],
        "links": [],
        "mentions": []
    },
    {
        "id": "1746757257162",
        "sessionId": "19:-SMwOyVjy2H3_BnsIO6WGUTXwuN1_BIw4U2TP4UcCwo1@thread.v2",
        "requestId": "db42bee0-7cfb-451f-8eb6-f929762ee970",
        "appClass": "IPM.SkypeTeams.Message.Copilot.Teams",
        "interactionType": "aiResponse",
        "conversationType": "appchat",
        "etag": "1746757257162",
        "createdDateTime": "2025-05-09T02:20:57.162Z",
        "locale": "en-us",
        "contexts": [],
        "from": {
            "@odata.type": "#microsoft.graph.chatMessageFromIdentitySet",
            "device": null,
            "user": null,
            "application": {
                "@odata.type": "#microsoft.graph.teamworkApplicationIdentity",
                "id": "fb8d773d-7ef8-4ec0-a117-179f88add510",
                "displayName": "Copilot in Teams",
                "applicationIdentityType": "bot"
            }
        },
        "body": {
            "contentType": "text",
            "content": "I need to hear more discussion before I can get to work. Please try again in a few minutes."
        },
        "attachments": [],
        "links": [],
        "mentions": []
    }
]

```

> [!NOTE]
> - Refer to [Teams Export APIs throttling limits](/graph/throttling-limits) to understand Throttling limits for the Copilot Interactions Export API.
> - Delta function call isn't supported. 
> - For optimal performance, the recommended $top value is 100. 
> - This API can be used to retrieve the supported Copilot Interactions for deleted users. 
> - Deleted copilot interactions for the supported app classes can be retrieved using this API. 
> - If a user prompt is edited, it is considered as new interaction and can be retrieved using this API. 
> 
