---
title: Shared Spaces Insight
author: mstonysmith
ms.author: tonysmit
manager: pamgreen
ms.reviewer: srpall
ms.date: 06/12/2025
ms.topic: article
audience: Admin
ms.service: msteams
ms.subservice: itpro-rooms
appliesto: 
  - Microsoft Teams
ms.collection: 
  - M365-collaboration
  - teams-rooms-devices
  - Tier1
ms.localizationpriority: medium
search.appverid: MET150
description: Provide a view of the health of your meeting rooms.
f1keywords: 
---

# Shared Spaces Insight

## Overview

The new Shared Spaces insights page in the Pro Management portal provides IT administrators with customized utilization insights, including time-series data visualizations, for shared spaces beginning with Teams Rooms. This feature uses calendar data and occupancy signals from Teams Rooms to track usage with filters for location, business hours, days of the week, and date ranges. Future updates will include desk and Bring Your Own Device (BYOD) room spaces.

## Prerequisites for IT admins

- **Licensing**: To have access to the portal and see the insights of your shared spaces in your organization, you'll need at least one Pro license, Rooms Premium, or Teams Shared Device (TSD) license.
- **Latest MTR on Android Admin Agent**: Update MTR on Android devices to the latest [Admin Agent version 1.0.0.202412110504.product](../devices/certified-device-apps.md) (AA 753) or newer versions. MTR on Android devices on older Admin Agent versions won't report room occupancy in the device local time zones.

## How to view Shared Spaces insights

To view the Shared Spaces insights in the Teams Pro Management portal, perform the following steps:

1. Launch the Pro Management Portal using the URL https://portal.rooms.microsoft.com/.
1. Navigate to the new **Analytics & Reports** tab.
1. From the left navigation menu, select **Shared Spaces Insights (Preview)**.
1. Select the desired location, business hours and days.
    1. To select the desired location, choose a value from the following dropdown lists:
        1. Country/Region
        1. State/Province
        1. City
        1. Building name
        1. Floor
        1. Room
    1. To select business hours and days, choose a value from the dropdown lists:
        1. Days of week
        1. Business hours

        :::image type="content" source="media/shared-spaces-insights-page.png" alt-text="Screenshot that shows the Shared Spaces insights page." lightbox="media/shared-spaces-insights-page.png":::

## Space Utilization Metric Definition

The space utilization metric is a metric derived from two inputs: calendar reservations and device signals as a proxy for room occupancy. A room is considered utilized when it is either:
- Reserved and occupied
- Reserved and not occupied
- Not Reserved and occupied

:::image type="content" source="media/space-utilization-metric-definition.png" alt-text="Screenshot that shows the space utilization metric definition page." lightbox="media/space-utilization-metric-definition.png":::

The device signals from Teams Rooms that contribute to the room occupancy include:
- Joining a Teams meeting
- Making a call
- Local HDMI ingest outside of a meeting
