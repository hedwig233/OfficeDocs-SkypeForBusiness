---
ms.date: 03/17/2018
title: "Plan for Microsoft Edge Server deployments in Skype for Business Server"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
audience: ITPro
ms.topic: install-set-up-deploy
ms.service: skype-for-business-server
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.collection: 
- IT_Skype16
- Strat_SB_Hybrid
ms.custom:
ms.assetid: 9cdc3e23-3f6a-4e4d-9e04-f038596b6700
description: "Summary: Plan for your Skype for Business Server Microsoft Edge environment. This article introduces you to Microsoft Edge concepts and lets you get organized with our more in-depth articles."
---

# Plan for Edge Server deployments in Skype for Business Server
 
[!INCLUDE [appliesto-2015-2019-sub](../../../SfBServer2019/includes/appliesto-2015-2019-sub.md)]

**Summary:** Plan for your Skype for Business Server Microsoft Edge environment. This article introduces you to Microsoft Edge concepts and lets you get organized with our more in-depth articles.
  
When you have a Skype for Business Server environment that's working internally, the next step for you might be to introduce a Microsoft Edge Server or a Microsoft Edge pool to the environment. This role would be vital if you want the services provided by Skype for Business Server to be used by people who are outside your internal network. These can potentially include:
  
- Remote Users: Employees who are offsite, either temporarily or in an ongoing way.
    
- Federated Users: Your partner organizations' employees.
    
- Mobile Users.
    
- Potential customers, partners, and even anonymous users you want to invite to meetings and presentations.
    
External User Access, which is what Microsoft Edge Servers provide, allow all this to happen. Your internal users are able to enjoy the following services that are hosted by your Skype for Business Server deployment:
  
- IM and presence for communication: Authorized external users can join in IM conversations and conferences. They can get presence information for other users (who get their presence info too). You can't do multiparty conferences if you're using a public IM provider, that's strictly peer-to-peer communication. But both SIP and XMPP protocols are supported.
    
- Audio/video (A/V) conferencing: Authorized external users can participate in your Skype for Business Server audio and video conferences.
    
- Web conferencing: Your authorized external users can participate in your Skype for Business conferences. You can also enable participation for remote users, federated users, and anonymous users if you'd like. Public IM users can't participate in conferences. There are also options to let these users participate in application and desktop sharing, and even act as meeting organizers or presenters.
    
Mobile device access is supported, as is Enterprise Voice. You can invite external users to those meetings you wish them to attend, even anonymous users, if you want to give permissions to them.
  
If this sounds like something your organization needs, then planning for a Microsoft Edge environment's going to be a significant help in deploying it. For further reading, we have the articles listed below.

> [!NOTE]
> XMPP Gateways and proxies are available in Skype for Business Server 2015 but are no longer supported in Skype for Business Server 2019. For more information, see [Migrating XMPP federation](../../../SfBServer2019/migration/migrating-xmpp-federation.md). 
  
## Planning topics:

The planning articles are:
  
- [Microsoft Edge Server system requirements in Skype for Business Server 2015](system-requirements.md)
    
- [Microsoft Edge Server environmental requirements in Skype for Business Server 2015](edge-environmental-requirements.md)
    
- [Microsoft Edge Server scenarios in Skype for Business Server 2015](scenarios.md)
    


