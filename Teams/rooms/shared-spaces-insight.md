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
description: Providing guidance to IT admins about the Shared Spaces Insights feature.
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

        :::image type="content" source="../media/shared-spaces-insights-page.png" alt-text="Screenshot that shows the Shared Spaces insights page." lightbox="../media/shared-spaces-insights-page.png":::

## Space Utilization Metric Definition

The space utilization metric is a metric derived from two inputs: calendar reservations and device signals as a proxy for room occupancy. A room is considered utilized when it is either:
- Reserved and occupied
- Reserved and not occupied
- Not Reserved and occupied

:::image type="content" source="../media/space-utilization-metric-definition.png" alt-text="Screenshot that shows the space utilization metric definition page." lightbox="../media/space-utilization-metric-definition.png":::

The device signals from Teams Rooms that contribute to the room occupancy include:
- Joining a Teams meeting
- Making a call
- Local HDMI ingest outside of a meeting

## Feature Walkthrough

### Data Visualization Description

You can hover over the “i” to see a brief description of the data visualization.

:::image type="content" source="../media/data-visualization.png" alt-text="Screenshot that shows the page on which you can view the description of Data Visualization." lightbox="../media/data-visualization.png":::

### Global Page Filters

- **Location Discovery**: This filter's pane is located on the top of the page at which it lets you filter the data for your preferred location (country, city, building, floor, and room). The floor and room options are selectable once a building is selected. The location data is pulled from the room account. If the address information in your room account isn't complete, it won't appear in the location filters. For example, if the room account only has the building information filled out and not information about country, state/province, or city, this room appears when the building is selected but not when the country, state/province, or city is selected.

:::image type="content" source="../media/location-discovery.png" alt-text="Screenshot that shows the page on which can apply filters to the location-related attributes." lightbox="../media/location-discovery.png":::

- **Days of the week and business hours filter**: You can customize the business hours and days to make the insights customized to your organization’s schedule. These filters apply to the whole insights page.

After setting the filters based on your preference, you must select **Apply** to generate the data.

- **Date range selector**: Above the filter box, there's a date range selector that allows you to customize the data displayed. The default setting for the date filter is **Last 30 days**, but you can adjust this setting to view data from the past 7 days, 30 days, 90 days, or a custom range up to 6 months. To set a custom date range, you must select **Custom range** and then specify the start and end dates using a calendar interface. After setting the desired dates, selecting **Apply** will update the graph to reflect data from the selected period.

:::image type="content" source="../media/date-range-selector.png" alt-text="Screenshot that shows the page on which can apply filters to the date range to define a preferred date." lightbox="../media/date-range-selector.png":::

- **Group filter**: The data can also be filtered by the group filter at the top of the Pro Management Portal as a page-level filter.

:::image type="content" source="../media/group-level-filtering.png" alt-text="Screenshot that shows the page on which group-level filtering can be applied." lightbox="../media/group-level-filtering.png":::

### Data Tiles

The tiles on the top of the page show the following details:

- **Total number of rooms**: The current number of Teams Rooms available based on the locations selected.
- **Total capacity**: The summed-up value of the capacity from the capacity property in the room resource account of all the latest Teams Rooms based on the locations selected. If the capacity information isn't available, it will be excluded.

After the data tiles, there are different data visualizations of your shared spaces usage and insights.