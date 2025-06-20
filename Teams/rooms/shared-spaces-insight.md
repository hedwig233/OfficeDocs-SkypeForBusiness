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

The new Shared Spaces insights page in the Pro Management portal provides IT administrators with customized utilization insights, including time-series data visualizations, for shared spaces beginning with Teams Rooms. This feature uses calendar data and occupancy signals from Teams Rooms to track usage with filters for location, business hours, days of the week, and date ranges. Future updates include desk and Bring Your Own Device (BYOD) room spaces.

## Prerequisites for IT admins

- **Licensing**: To have access to the portal and see the insights of your shared spaces in your organization, you'll need at least one Pro license, Rooms Premium, or Teams Shared Device (TSD) license.
- **Latest MTR on Android Admin Agent**: Update MTR on Android devices to the latest [Admin Agent version 1.0.0.202412110504.product](../devices/certified-device-apps.md) (AA 753) or newer versions. MTR on Android devices on older Admin Agent versions won't report room occupancy in the device local time zones.

## Space Utilization Metric Definition

The space utilization metric is a metric derived from the following two inputs: 

- [Calendar reservations](#calendar-reservations)
- [Device signals as a proxy for room occupancy](#device-signals-as-a-proxy-for-room-occupancy)

The following screenshot depicts the causes of a space utilization metric:

:::image type="content" source="../media/space-utilization-metric-definition.png" alt-text="Screenshot that shows the space utilization metric definition page." lightbox="../media/space-utilization-metric-definition.png":::

### Calendar reservations

The "calendar reservations" input indicates which room, how many, and when were they occupied.

A room is considered utilized when either of the following scenarios are fulfilled:

- Reserved and occupied
- Reserved and not occupied
- Not Reserved and occupied

### Device signals as a proxy for room occupancy

The device signals from Teams Rooms that contribute to the room occupancy include:

- Joining a Teams meeting
- Making a call
- Local HDMI ingest outside of a meeting

## Where is this in Pro Portal?

This section provides the steps for the user to navigate to the **Shared Spaces Insights (Preview)** page, at which you can find insights into the utilization data of the shared spaces.

1. Launch the Pro Management Portal using the URL https://portal.rooms.microsoft.com/.
1. Navigate to the new **Analytics & Reports** tab.
1. From the left navigation menu, select **Shared Spaces Insights (Preview)**. The **Shared Spaces Insights (Preview)** page appears, as shown in the following screenshot:
  
   :::image type="content" source="../media/shared-spaces-insights-page.png" alt-text="Screenshot that shows the Shared Spaces insights page." lightbox="../media/shared-spaces-insights-page.png":::

### Page components

The **Shared Spaces Insights (Preview)** page contains components that provide insights into the utilization trends for the shared spaces. The components are:

  - [Global page filters](#global-page-filters)
  - [Shared spaces utilization percentage](#shared-spaces-utilization-percentage)
  - [Peak utilization chart](#peak-utilization-chart)
  - [Overall shared spaces utilization](#overall-shared-spaces-utilization)
  - [Most and least utilized rooms](#most-and-least-utilized-rooms)

For information on what each of these components denote, you can hover over the “i”, as shown in the following example:

:::image type="content" source="../media/data-visualization.png" alt-text="Screenshot that shows the page on which you can view the description of Data Visualization." lightbox="../media/data-visualization.png":::

> [!NOTE]
> The preceding screenshot shows the example of hovering around the "i" icon of only  the **Peak utilization chart** component. Similarly, other components—except **Global page filters**—will have the "i" icon on the top-right of their respective panes.

#### Global page filters

- **Location Discovery**: This filter's pane is located on the top of the page at which it lets you filter the data for your preferred location. To determine a location for which you want to filter the data, you must choose a value from the following dropdown lists:
- Country/Region
- State/Province
- City
- Building name

  > [!NOTE]
  > Only after youy choose a value for the **Building name** attribute, the **Floor** and **Room** dropdown lists become selectable.

- Floor
- Room

The following screenshot depicts the location discovery-related attributes with a value to be chosen for each attribute to determine the location:

:::image type="content" source="../media/location-discovery.png" alt-text="Screenshot that shows the page on which can apply filters to the location-related attributes." lightbox="../media/location-discovery.png":::

The location data is pulled from the room account. If the address information in your room account isn't complete, it won't appear in the location filters. For example, if the room account only has the building information filled out and not information about country, state/province, or city, this room appears when the building is selected but not when the country, state/province, or city is selected.

- **Days of the week and business hours filter**: "Days" and "business hours" are the other attributes for which you must choose values to customize the insights/data pertaining to the usage of the page's components. You must choose values for from the following dropdown lists:

    - Days of week
    - Business hours

After setting the filters based on your preference for **Location Discovery** and **Days of the week and business hours filter**, you must select **Apply** to generate the data.

- **Date range selector**: Above the filter box, there's a date range selector that allows you to customize the data displayed. The default setting for the date filter is **Last 30 days**, but you can adjust this setting to view data from the past 7 days, 30 days, 90 days, or a custom range up to 6 months. To set a custom date range, you must select **Custom range** and then specify the start and end dates using a calendar interface. 

  After setting the desired dates, you must select **Apply** for the graph to get updated and to reflect data from the selected period.

:::image type="content" source="../media/date-range-selector.png" alt-text="Screenshot that shows the page on which can apply filters to the date range to define a preferred date." lightbox="../media/date-range-selector.png":::

- **Group filter**: The data can also be filtered by the group filter at the top of the Pro Management Portal as a page-level filter.

:::image type="content" source="../media/group-level-filtering.png" alt-text="Screenshot that shows the page on which group-level filtering can be applied." lightbox="../media/group-level-filtering.png":::

##### Data Tiles

Data tiles refer to the two tiles below the dropdown lists that display the utilization data for the groups you choose from the dropdown list on the top–left side of the **Shared Spaces Insights (Preview)** page (adjacent to the portal's name).

The two data tiles displaythe following categories of information:

- **Total number of rooms**: The current number of Teams Rooms available based on the locations selected.
- **Total capacity**: The summed-up value of the capacity from the capacity property in the room resource account of all the latest Teams Rooms based on the locations selected. If the capacity information isn't available, it's excluded.

#### Shared spaces utilization percentage

:::image type="content" source="../media/shared-spaces-utilization-percentage.png" alt-text="Screenshot that shows the utilization percentage of shared spaces in a tile format." lightbox="../media/shared-spaces-utilization-percentage.png":::

This stacked column chart in the preceding screenshot shows the utilization percentage of your shared spaces during the selected time period and provides insights on how your shared spaces are used. It's derived from the following two primary sources:

- Reservations data sourced from exchange
- Occupancy captured from device signals spaces insight

The categories for which the tiles (in the preceding diagram) provide data are:

- **Reserved and Occupied**: Percentage of time the space was both booked and occupied
- **Reserved and not Occupied**: Percentage of time the space was booked but not occupied
- **Not Reserved and Occupied**: Percentage of time the space was occupied but not booked
- **Not Reserved and Not Occupied**: Percentage of time the space was neither booked nor occupied

#### Peak utilization chart

:::image type="content" source="../media/peak-utilization-chart.png" alt-text="Screenshot that shows the data of the time period during which the shared spaces' utilization was at its peak." lightbox="../media/peak-utilization-chart.png":::

This chart shows the peak utilization of your spaces throughout the week, with color gradients indicating the percentage of room utilization ranges of 0-10% up to 90-100% during different time slots. The blue rectangle below the heat map highlights the top 5 busiest timeslots.

You can use this chart to identify the peak space usage timeslot on a given day, when the rooms or desks are most and least used.

#### Overall Shared Spaces Utilization

This column chart illustrates the overall utilization of the spaces in the chosen timeframe. The x-axis represents the selected period while the y-axis shows the percentage of shared spaces' utilization.

:::image type="content" source="../media/overall-shared-spaces-utilization.png" alt-text="Screenshot that shows the chart depicting the overall utilization percentage of the shared spaces." lightbox="../media/overall-shared-spaces-utilization.png":::

#### Most and Least Utilized Rooms

:::image type="content" source="../media/most-least-utilized-rooms.png" alt-text="Screenshot that shows the chart depicting the rooms that most utilized and least utilized." lightbox="../media/most-least-utilized-rooms.png":::

The most and least utilized rooms' tables provide insights into the utilization of your shared spaces based on the selected period and location. The first table in the preceding screenshot lists the most-used rooms and second the least-used rooms sorted by the utilization rate. The utilization rate, average reservation rate, and average occupancy rate columns are defined in the metrics definitions above.
