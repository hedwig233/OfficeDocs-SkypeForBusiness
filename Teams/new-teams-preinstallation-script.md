---
title:  Preinstallation script for Teams clients
ms.author: heidip
author: MicrosoftHeidi
manager: jtremper
ms.topic: article
ms.date: 06/30/2025
ms.service: msteams
audience: admin
ms.collection: 
- M365-collaboration
- m365initiative-deployteams
ms.reviewer: daro
search.appverid: MET150
f1.keywords:
- NOCSH
description: This article documents a script that administrators can run before beginning an organization's installation of Teams clients, or after an installation fails for some or all clients. This script should help determine what may be blocking the installation of the Teams client on a device or devices.
appliesto: 
- Microsoft Teams
ms.localizationpriority: high
---

# Teams client preinstallation script

Microsoft has a [preinstallation check script](https://aka.ms/NewTeamsReadinessCheck) designed to identify why devices can't install the Teams client. The script also suggests solutions to any problems it finds. Admins can save time installing Teams by running the script in these two use cases:

- Before you install Teams for the first time.
- After the Teams client installation fails on some devices.

By running this script, admins can proactively identify and resolve issues, making it easier to install the Teams across their organization.

> [!NOTE]
> If you want to get a preinstall check status across all devices, run this script using device management software like Intune. If you want to have the preinstall script check the status for a single device, you can run it directly on the device.

## Using the script

You can run the script locally on a device, in Intune, or using some other device management software.

We have sample instructions to run the script in Intune at this location: [Sample instructions](https://github.com/microsoft/MDE-PowerBI-Templates/blob/master/ASR_scripts/AddShortcuts_with_Intune.md)

After running the script:

- If run locally, the failures and suggested resolutions display in the command line for administrators to see. Administrators can fix the issues and run the Teams client installation again.
- If the script is run in Intune or other device management software:
  - Administrators can see issues and suggested resolutions for each device.
  - Administrators can download these results as a CSV file.
  - Administrators can filter the CSV file for each error to identify all devices requiring a specific fix.
  - Administrators can fix one error at a time across all machines and rerun the Teams installation.

A video demonstration of the script being run [is located here](https://learn.microsoft.com/_themes/docs.theme/master/en-us/_themes/global/video-embed-one-stream.html?id=3fb0b236-236f-4817-8bf0-e93262b859b1).
