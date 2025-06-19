---
title: "EndpointSubnet table"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 2/1/2018
audience: ITPro
ms.topic: article
ms.service: skype-for-business-server
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.assetid: d62e51d6-2117-4c41-adce-08f8d9d75ce0
description: "The EndpointSubnet table is a supporting table. Each record represents one subnet captured from endpoints."
---

# EndpointSubnet table

[!INCLUDE[appliesto-2015-xxx-xxx.md](../../../SfBServer2019/includes/appliesto-2015-xxx-xxx.md)]
 
The EndpointSubnet table is a supporting table. Each record represents one subnet captured from endpoints. 
  
|**Column**|**Data Type**|**Key/Index**|**Details**|
|:-----|:-----|:-----|:-----|
|**SubnetIP** <br/> |int  <br/> |Primary, Foreign  <br/> |Integer representation for the subnet.  <br/> |
|**NextUpdateTS** <br/> |datetime  <br/> ||For internal use only.  <br/> |
   

