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

# Shared Spaces Insights

> [!IMPORTANT]
> Currently, the Shared Spaces Insights feature is in Public Preview in the "Public" and "GCC" environments. This feature is currently not yet enabled in the "GCC-H" and "Sovereign cloud" environments.

## Overview

The new **Shared Spaces Insights** page in the Pro Management portal provides IT administrators with customized utilization insights, including time-series data visualizations, for shared spaces beginning with Teams Rooms. This feature uses calendar data and occupancy signals from Teams Rooms to track usage with filters for location, business hours, days of the week, and date ranges.

## Prerequisites for IT admins

To use the Shared Spaces Insights feature, ensure that you meet the following prerequisites:

- **Licensing**: To access the Shared Spaces Insights feature, you need at least one Teams Rooms Pro license, Teams Rooms Premium license, or Teams Shared Device license.
- **Teams Rooms on Android Admin Agent**: Update Teams Rooms on Android devices to [Admin Agent version 1.0.0.202412110504](../devices/certified-device-apps.md#100202412110504) or newer versions to ensure that these devices are visible in the **Shared Spaces Insights** page.
    - Devices updated to the required Admin Agent version on or before May 6, 2025, will begin reporting utilization metrics starting May 6, 2025.
    - Devices updated after May 6, 2025 will begin reporting utilization metrics only going forward after the Admin Agent version is upgraded to 1.0.0.202412110504 or a newer version.
      > [!IMPORTANT]
      > Allow 24 to 48 hours for the utilization metrics to populate.
    - Devices running older versions of the Admin Agent won't appear in the **Shared Spaces Insights** dashboard until they're updated.

## Space Utilization Metric Definition

The space utilization metric is a metric derived from the following inputs: 

- [Calendar reservations](#calendar-reservations)
- [Device signals as a proxy for room occupancy](#device-signals-as-a-proxy-for-room-occupancy)

The following screenshot depicts space utilization metric:

:::image type="content" source="../media/space-utilization-metric-definition.png" alt-text="Screenshot that shows the space utilization metric definition page." lightbox="../media/space-utilization-metric-definition.png":::

A room is considered utilized when either of the following scenarios are fulfilled:

- Reserved and occupied
- Reserved and not occupied
- Not Reserved and occupied

### Calendar reservations

The "calendar reservations" input reflects how frequently the room has been reserved or booked on the room's account calendar in Exchange.

### Device signals as a proxy for room occupancy

The details of the device signals from Teams Rooms that contribute to the room occupancy are provided in the following table:

|Occupancy signal includes  |Teams Rooms on Windows  |Teams Rooms on Android  |
|---------|---------|---------|
|Joining a Teams meeting      |Yes          |Yes          |
|Making a VOIP call      |Yes         |Yes         |
|Making a PSTN call      |Yes         |No         |
|Local HDMI ingest outside of a meeting      |Yes         |No         |
|[Direct Guest Join (DGJ)](third-party-join.md)      |Yes         |No         |

## Where is this in Pro Portal?

To navigate to the **Shared Spaces Insights** page in the Pro Management Portal, perform the following steps:

1. Launch the Pro Management Portal using the URL https://portal.rooms.microsoft.com/.
1. Navigate to the new **Analytics & Reports** tab.
1. From the left navigation menu, select **Shared Spaces Insights**. The **Shared Spaces Insights** page appears, as shown in the following screenshot:
  
   :::image type="content" source="../media/shared-spaces-insights-page.png" alt-text="Screenshot that shows the Shared Spaces insights page." lightbox="../media/shared-spaces-insights-page.png":::

1. Select the desired location, business hours and days, and date filters by choosing values from the following dropdown lists:
  
   |Dropdown filter name  | Filter category  |
   |---------|---------|
   |Country/Region    |Location         |
   |State/Province     |Location         |
   |City     |Location         |
   |Building name     |Location         |
   |Floor     |Location         |
   |Room     |Location         |
   |Days of week     |Business days         |
   |Business hours     |Business hours         |
   |Last 30 days (default value)     |Date (on which rooms were chosen)         |

   :::image type="content" source="../media/attributes-insights.png" alt-text="Screenshot that shows the dropdown lists on the Shared Spaces Insights page." lightbox="../media/attributes-insights.png":::

   > [!NOTE]
   > The **Floor** and **Room** dropdown lists become available only after you choose a value for the **Building name** attribute.

1. Select **Apply**.
   The Shared space utilization insights are shown for each component on the **Shared Spaces Insights** page.

   > [!NOTE]
   > The IT admin can view the utilization metrics of only those shared spaces that they're authorized to view, based on the roles assigned to you. For more information about the roles assigned to you and the shared spaces for which you're authorized to view the utilization metrics, see [Role-Based Access Control (RBAC)](#role-based-access-control-rbac). 

## Global page filters

The global page filters refer to the dropdown lists on the **Shared Spaces Insights** page. These filters are categorized into:

- [Location discovery](#location-discovery)
- [Days of the week and business hours filters](#days-of-the-week-and-business-hours-filters)
- [Date range selector](#date-range-selector)
- [Group filter](#group-filter)

### Location discovery

This filter's pane is located on the top of the page from which it lets you filter the data for your preferred location.

The following screenshot depicts the location discovery-related attributes with a value to be chosen for each attribute to determine the location:

:::image type="content" source="../media/location-discovery.png" alt-text="Screenshot that shows the page on which can apply filters to the location-related attributes." lightbox="../media/location-discovery.png":::

The location data is pulled from the Places API for the room accounts. If the address information in your room account isn't complete, it won't appear in the location filters. For example, if the room account only has the building information filled out and not information about country, state/province, or city, then this room appears when the building is selected but not when the country, state/province, or city is selected.

### Days of the week and business hours filters

"Days" and "business hours" are the other attributes for which you can choose values to customize the insights to your organization's schedule.

Ensure that the filters for **Location Discovery** and **Days of the week and business hours filter** have been set (based on your preference) because only then you can select **Apply** to generate the data.

### Date range selector

Above the filter box, there's a date range selector that allows you to customize the data displayed. The default setting for the date filter is **Last 30 days**, but you can adjust this setting to view data from the past 7 days, 30 days, 90 days, or a custom range up to 6 months. To set a custom date range, you must select **Custom range** and then specify the start and end dates using a calendar interface.

:::image type="content" source="../media/date-range-selector.png" alt-text="Screenshot that shows the page on which can apply filters to the date range to define a preferred date." lightbox="../media/date-range-selector.png":::

After setting the desired dates, you must select **Apply** for the graph to get updated and to reflect data from the selected period.

### Group filter

The data can also be filtered by the group filter at the top of the Pro Management Portal as a page-level filter.

:::image type="content" source="../media/group-level-filtering.png" alt-text="Screenshot that shows the page on which group-level filtering can be applied." lightbox="../media/group-level-filtering.png":::

## Data visualizations

The **Shared Spaces Insights** page contains the following data visualizations:

- [Data tiles](#data-tiles)
- [Shared spaces utilization percentage](#shared-spaces-utilization-percentage)
- [Peak utilization chart](#peak-utilization-chart)
- [Utilization by Days of Week](#utilization-by-days-of-week)
- [Overall Shared Spaces Utilization](#overall-shared-spaces-utilization)
- [Most and Least Utilized Rooms](#most-and-least-utilized-rooms)

For information on each data visualization, you can hover over the "i" as shown in the following example:

:::image type="content" source="../media/data-visualization.png" alt-text="Screenshot that shows the page on which you can view the description of Data Visualization." lightbox="../media/data-visualization.png":::

> [!NOTE]
> All components—except **Global page filters**—will have the "i" icon on the top-right of their respective panes.

### Data tiles

Data tiles are the tiles below the dropdown lists. These tiles display the utilization data for the groups you choose from the dropdown list on the top–left side of the **Shared Spaces Insights** page (next to the portal's name).

The following screenshot depicts the example of a data tile:

:::image type="content" source="../media/data-tiles.png" alt-text="Screenshot that shows a data tile and the information it displays on the Shared Spaces Insights page." lightbox="../media/data-tiles.png":::

The data tiles (in the preceding screenshot) display the following categories of information:

- **Total number of rooms**: This tile displays the latest number of Teams Rooms booked/utilized based on the locations selected.
- **Total capacity**: This tile displays the summed-up capacity (from the [capacity property in the room resource account](/graph/api/resources/room?view=graph-rest-1.0&preserve-view=true)) of all the latest Teams Rooms based on the locations selected. If the capacity information isn't available, it's excluded from the data tiles.
- **Busiest day**: This tile identifies the specific day of the week that witnessed the highest utilization based on the selected period of time and location filters.
- **Peak utilization time slot**: This tile highlights the peak utilization time slot based on the selected period of time.

The data tiles are followed by the other components/data visualizations of your share spaces usage and insights, which are described in the following sections:

### Shared spaces utilization percentage

:::image type="content" source="../media/shared-spaces-utilization-percentage.png" alt-text="Screenshot that shows the utilization percentage of shared spaces in a tile format." lightbox="../media/shared-spaces-utilization-percentage.png":::

The "shared spaces utilization percentage" component refers to a stacked column chart that shows the utilization percentage of your shared spaces during the selected time period. This chart also provides insights on how your shared spaces are used. The data provided in this chart is derived from the following two primary sources:

- Reservations data sourced from exchange
- Occupancy captured from device signals spaces insight

The classifications of data provided by the pie chart (in the preceding screenshot) are:

- **Reserved and Occupied**: Percentage of time the space was both booked and occupied
- **Reserved and not Occupied**: Percentage of time the space was booked but not occupied
- **Not Reserved and Occupied**: Percentage of time the space was occupied but not booked
- **Not Reserved and Not Occupied**: Percentage of time the space was neither booked nor occupied

### Peak utilization chart

:::image type="content" source="../media/peak-utilization-chart.png" alt-text="Screenshot that shows the data of the time period during which the shared spaces' utilization was at its peak." lightbox="../media/peak-utilization-chart.png":::

The "peak utilization chart" shows the peak utilization of your spaces throughout the week, with color gradients indicating the percentage of room utilization ranges starting with 0-10% and going up to 90-100% during different time slots. The blue rectangle below the heat map highlights the top 5 busiest timeslots.

You can use this chart to identify the peak space usage timeslot on a given day, when the spaces are most and least used.

### Utilization by days of week

This column chart provides a breakdown of space utilization across different days of the week, helping you identify trends and patterns in usage. This column chart is depicted in the following screenshot:

:::image type="content" source="../media/utilization-by-days-of-week.png" alt-text="Screenshot that shows the shared spaces' utilization data for different days of the week.' utilization was at its peak." lightbox="../media/utilization-by-days-of-week.png":::

### Overall shared spaces utilization

This column chart illustrates the overall utilization of the spaces in the chosen timeframe. The x-axis represents the selected period while the y-axis shows the percentage of shared spaces' utilization.

:::image type="content" source="../media/overall-shared-spaces-utilization.png" alt-text="Screenshot that shows the chart depicting the overall utilization percentage of the shared spaces." lightbox="../media/overall-shared-spaces-utilization.png":::

### Most and least utilized rooms

:::image type="content" source="../media/most-least-utilized-rooms.png" alt-text="Screenshot that shows the chart depicting the rooms that most utilized and least utilized." lightbox="../media/most-least-utilized-rooms.png":::

The most and least utilized rooms' tables provide insights into the utilization of your shared spaces based on the selected period and location. The first table lists the most-used rooms, and the second table lists the least-used rooms sorted by the utilization rate for the top 200 rooms. The utilization rate, average reservation rate, and average occupancy rate columns are defined in the [Space Utilization Metric Definition](#space-utilization-metric-definition) section.

### Role-Based Access Control (RBAC)

Shared Spaces Insights adheres to [role-based access controls](rooms-pro-rbac.md) in the Pro Management portal, displaying utilization metrics only for spaces the user is authorized to view.
