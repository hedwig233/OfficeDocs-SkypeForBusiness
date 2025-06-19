---
ms.date: 03/17/2018
title: "Configure archiving disclaimers for external users in Skype for Business Server"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
audience: ITPro
ms.topic: quickstart
ms.service: skype-for-business-server
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.assetid: 394ac291-05cd-4fa1-acb3-714af538b47f
description: "Summary: Read this article to learn how to configure an archiving disclaimer for Skype for Business Server."
---

# Configure archiving disclaimers for external users in Skype for Business Server
 
[!INCLUDE [appliesto-2015-2019-sub](../../../SfBServer2019/includes/appliesto-2015-2019-sub.md)]

**Summary:** Read this article to learn how to configure an archiving disclaimer for Skype for Business Server.
  
If your organization communicates with external partners, you need to let them know that you're archiving communications with them. When you deploy an Microsoft Edge Server and enable federation for your organization, you're asked whether you want to automatically send an archiving disclaimer to external partners. 
  
If you need to change this configuration, you can use the Skype for Business Server Control Panel or the Windows PowerShell **Set-CsAccessEdgeConfiguration** cmdlet. Cmdlets can be run either from the Skype for Business Server management shell or from a remote session of Windows PowerShell.
  
To enable external users to collaborate with users in your Skype for Business Server deployment, you must also configure at least one external access policy to support external user access. For details, see Manage XMPP Federated Partners for Your Organization. For details about controlling access for specific federated domains, see Control Access by Individual Federated Domains.
  
## Enable or disable archiving disclaimer using the Control Panel

1. From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, sign in any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel. 
    
3. In the left navigation bar, select **Federation and External Access**, and then select **Access Edge Configuration**.
    
4. On the **Access Edge Configuration** tab, select **Global**, select **Edit**, and then select **Show details**.
    
5. In **Edit Access Edge Configuration**, under **Enable federation and public IM connectivity**, select or clear the **Send archiving disclaimer to federated partners** check box to enable or disable automatically sending the archiving disclaimer.
    
6. Select **Commit**.
    
## Enable or disable archiving disclaimer using Windows PowerShell

To enable the archiving disclaimer, set the value of the **EnableArchivingDisclaimer** property to True ($True):
  
```powershell
Set-CsAccessEdgeConfiguration -EnableArchivingDisclaimer $True
```

To disable the archiving disclaimer, set the value of the **EnableArchivingDisclaimer** property to False ($False):
  
```powershell
Set-CsAccessEdgeConfiguration -EnableArchivingDisclaimer $False
```



