---
title: "AppliedBandwidthSource table"
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
ms.assetid: 24fb3caf-19b3-4c0a-90d7-ca5d53de32ad
description: "The AppliedBandwidthSource table is a supporting table. Each record represents one source."
---

# AppliedBandwidthSource table

[!INCLUDE[appliesto-2015-xxx-xxx.md](../../../SfBServer2019/includes/appliesto-2015-xxx-xxx.md)]

The AppliedBandwidthSource table is a supporting table. Each record represents one source.
  
|**Column**|**Data Type**|**Key/Index**|**Details**|
|:-----|:-----|:-----|:-----|
|**AppliedBandwidthSourceKey** <br/> |int  <br/> |Primary  <br/> |Unique number identifying the source.  <br/> |
|**AppliedBandwidthSource** <br/> |varchar(256)  <br/> |Unique  <br/> |This is the source of the bandwidth cap being imposed. It describes where the bandwidth limit is coming from (for example, "Policy Server," "TURN Server," or "Modality").  <br/> |
   

