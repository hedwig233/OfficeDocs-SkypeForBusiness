---
title: Using Network Planner - example scenario
author: MicrosoftHeidi
ms.author: heidip
manager: jtremper
ms.reviewer: rowille
ms.topic: article
ms.date: 06/18/2025
ms.service: msteams
audience: admin
ms.collection: 
- M365-collaboration
search.appverid: MET150
f1.keywords:
- NOCSH
description: This example scenario shows you how to use the Network Planner tool to create sites and personas and run reports. The example includes local and remote sites with Public Switched Telephone Network (PSTN).
ms.localizationpriority: medium
---

# Introduction

The Network Planner tool is available in the Teams admin center. It helps you determine network requirements for your organization. This example scenario shows how you can use the tool to create sites, personas, and running reports for a company called Contoso.

## Before you begin

We assume you already know your way around the Teams admin center, and you're familiar with what you need to do to prepare your network for Teams. If this article is where you're starting with Network Planner, we recommend you read the following articles first:

- [Prepare your organization's network for Teams](prepare-network.md)
- [Use the Network Planner for Microsoft Teams](network-planner.md)

## Overview of Contoso network

Contoso has three locations:

- **Seattle Headquarters:** The main location for Contoso. It has 1,000 employees and 25 of them are calling only. The site is connected to the internet, and there's a local telephone connection (PSTN). Contoso has Direct Routing set up to be able to use the local telephone connection with Teams.
- **Kirkland Office:** This branch office has 400 employees and 10 are calling only. The site uses its connection to the headquarters for both internet and phone (PSTN) traffic. This office is connected to the Seattle headquarters using a WAN connection.
- **Denver Office:** This office has 250 employees and 50 are calling only. The site has its own local internet connection, but has no direct telephone connection (PSTN).

Let's get started!

## Add a network plan

In the Teams admin center, expand **Org-wide settings** and then select **Network planner**. The first thing you need to do is create a network plan.

1. Select **Add a network plan**.
2. In the **New network plan** pane, add a name and description for your network plan. For this example, we use *Contoso1* as the plan name, and *Contoso network plan* as the description.
3. Select **Save**.

![Add a new network plan.](media/network-planner-new-network-plan.png)

After you save your network plan, it displays in your network plans list.

![List of network plans.](media/network-planner-network-plans.png)

## Create custom personas

Next you need to create the necessary personas to represent your users. Since each location has specialized users who only make phone calls, you need to create that persona.

1. On the Network planner page, select the **Personas** tab, and then select **+ Custom persona**.
2. Add a name and description for this persona. For this example, we name it *Calling only*.
3. Turn on **Audio** and turn off everything else so that calling is the only permission turned on.
4. Select **Save** to add the persona to the list.

![Adding a persona in network planner.](media/network-planner-add-persona.png)

## Add sites to your network plan

Now, you need to add the three sites to your network plan. The following table summarizes the characteristics of Contoso's network locations.

|Location |Total number of employees |Calling only employees |Internet connection |PSTN connection |WAN link capacity | Internet link capacity |
|----------------|-----|---|---------------------------|--------------------------------|----------|----------|
|Seattle HQ      |1000 |25 |Local Internet             |Local PSTN using Direct Routing |200 Mbps  | 500 Mbps |
|Kirkland Office |400  |10 |Remote Internet through HQ |Remote PSTN through HQ          | 200 Mbps | N/A      |
|Denver Office   |250  |50 |Local Internet             |No PSTN connection              | N/A      | 150 Mbps |

1. Select your network plan in Network Planner.
2. Select the **Network sites** tab and select **Add a network site**.

![Adding a network site.](media/network-planner-add-network-site.png)

3. Using the table in this section, fill in the details for the Seattle HQ site. Turn on both the **ExpressRoute** and **Connected to WAN** toggles.

![New site details.](media/network-planner-add-network-site-2.png)

4. Since the Seattle HQ site has local internet and local PSTN connections, you need to correctly specify these characteristics.

![New site egress settings.](media/network-planner-add-network-site-link-capacity.png)

5. Select **Save** to complete adding the Seattle HQ site.
6. Create the Denver site using the same process. WAN shouldn't be enabled.
7. Since the Kirkland site uses the connection to Seattle HQ for both internet and PSTN connectivity, we considered it to be a remote site. When creating the Kirkland site, specify that it's connected to the WAN and select *Remote* for both **Internet egress** and **PSTN egress**.

![Remote site egress settings](media/network-planner-add-remote-site-egress-kirkland.png)

## Create a report

Now that you have your sites added, you can create a report. You define your user distribution while creating the report.

1. Select the **Report** tab, and then select **Start a report** to open the user distribution page. Add a name and a description for your report to begin.

![Creating a network planner report](media/network-planner-add-report.png)

2. When you first start a report, the user counts for each site are distributed automatically, for example 80% to office workers, 20% to remote workers. You can adjust the number of users for each persona to match your user population at this point. Let's assume that Contoso has the same 80/20 split between office workers and remote workers for each site. Be sure to take the calling only personas out of the number of users in the office. The resulting distribution should look like this image:

![User distribution among different personas for each site](media/network-planner-persona-distribution-2.png)

## Analyze report output

Once you generate the report, you see a screen displaying your bandwidth requirements both as overall and modality specific values. By default, the allowed bandwidth is set to 30%. By changing this value and selecting **Run report**, you can see the different impact on the bandwidth for your network. Any areas that need more bandwidth are highlighted in red.

![Report analysis](media/network-planner-contoso-report-output.png)

Network planner also gives you recommendations based on the projected impact of Teams on your network. Select the recommendation view icon to see recommendations for each site, if there are any. The following image shows a sample recommendation view.

![Recommendation view](media/network-planner-recommendation-view.png)

Here, you can see that currently the Kirkland site's bandwidth needs to be increased to get the best performance from Teams.

## Learn more

The example scenario for Network Planner is complete. You can [go back to the Network Planner article](network-planner.md), or check out the following resources for more information on getting your organization ready for Teams:

- [Prepare your organization's network for Microsoft Teams](prepare-network.md)
- [Improve and monitor call quality for Teams](monitor-call-quality-qos.md)
- [Office 365 URLs and IP address ranges](/office365/enterprise/urls-and-ip-address-ranges)
