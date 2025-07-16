---
title: Enroll a Teams Rooms device into the Pro Management Portal
author: mstonysmith
ms.author: tonysmit
manager: pamgreen
ms.reviewer: altsou
ms.date: 5/08/2025
ms.topic: how-to
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
description: Onboarding Teams Rooms devices to the Pro Management Portal
f1keywords: 
---

# Enrolling a device into the Pro Management Portal

This article explains how to enroll Teams Rooms devices to the Pro Management Portal. The Pro Management Portal supports Teams Rooms on Windows, Teams Rooms on Android, and Teams panel devices.

For Teams Rooms on Windows devices, the Teams Rooms Pro Management agent is automatically downloaded and installed at device setup. For Teams Rooms on Android devices or Teams panels, the admin agent included on the device automatically connects to the Pro Management Portal. Devices once signed into Teams automatically enrolls and appears in the Teams Rooms Pro Management Portal. 

## Prerequisites

Follow these procedures to set up your environment or device prior to attempting to connect a device to the Pro Management Portal.

### Network security

Ensure the required URLs listed in [Teams Rooms - Network Security](security.md?tabs=Windows#network-security) are allowed on your network. For GCC-High customers, also add these two URLs:
- mmrgcchiot.azure-devices.us
- mmrgcchstor.blob.core.usgovcloudapi.net

 > [!NOTE]
 > All network traffic between the monitoring agent and the Pro Management Portal is SSL over port 443. See [Teams Rooms - Network Security](security.md?tabs=Windows#network-security) for the full list of required connectivity endpoints for functionality for other device services.

### If necessary, configure proxy settings on the device

Review proxy requirements and configuration steps for your Teams Rooms devices in [Prepare your environment for Teams devices](rooms-prep.md#pro-management-agent-proxy).

>[!IMPORTANT]
>Teams Rooms devices automatically include the Pro Management Portal agent and don't require manual installation. These steps are here for troubleshooting purposes only.

## Manual Teams Rooms on Windows enrollment process

The enrollment process involves these steps:

1. On the left navigation bar of the Microsoft Teams Rooms Pro Management portal [Commercial & GCC: http://portal.rooms.microsoft.com](https://portal.rooms.microsoft.com/) or [GCC-High: http://devices.gov.teams.microsoft.us](http://devices.gov.teams.microsoft.us), expand **Settings** and select **General**.
1. Under *Enroll a room*, select **Download installer** to download the monitoring agent software.
1. Install the agent using the installer downloaded in step 2. This can be done either by running the MSI locally or via Intune. 
1. The room appears in the portal within 5-10 minutes.

   ![Screenshot of settings and self-enrollment keys.](../media/software-installation-005new.png)

### Agent Installation

After downloading the installer, unzip its contents to access the file **ManagedRoomsInstaller.msi**.

There are two modes of installation: 1) individual local machine install and 2) mass deploy mode (usually via Intune). We recommend individual install for nondomain joined machines or for machines that you have no way of running MSI installers remotely.

#### Individual device installation

1. Log in to the device as administrator. Ensure the *Performing operations as the Admin user of the device* steps are followed.

1. Copy the file **ManagedRoomsInstaller.msi** to the MTR device.

   On running the ***ManagedRoomsInstaller.msi*** is a License Agreement screen.

1. After reading the agreement, check ***I accept the terms in the License Agreement*** and press **Install**.

    This begins the Microsoft Teams Rooms Pro monitoring software install. A prompt for elevation (run as administrator) is displayed.

1. Select **Yes**.

    The installation continues. During the installation procedure, a console window opens and begins the final stage of the Microsoft Teams Rooms Pro monitoring software installation.

    > [!NOTE]
    > Don't close the window. Once the installation is complete, the wizard displays a "Finish" button.

#### Intune-enrolled device bulk deployment

The following components are prerequisites for successful installation: 

- **Intune enrollment**: Teams Rooms on Windows devices must be already enrolled in Intune.
  For more information about how to enroll Teams Rooms on Windows devices in Intune, see [Enrolling Microsoft Teams Rooms on Windows devices with Microsoft Endpoint Manager - Microsoft Tech Community](https://techcommunity.microsoft.com/t5/intune-customer-success/enrolling-microsoft-teams-rooms-on-windows-devices-with/ba-p/3246986)
- **Microsoft Entra group with all Teams Rooms on Windows devices as members** – a group created in Microsoft Entra ID that includes all Teams Rooms on Windows devices that should be part of the Microsoft Teams Rooms Premium service. This group is used for targeting the deployment of the MTR Pro agent.
  
> [!NOTE]
> You may consider using Dynamic groups in Microsoft Entra ID for this purpose, more information at [Enrolling Microsoft Teams Rooms on Windows devices with Microsoft Endpoint Manager - Microsoft Tech Community](https://techcommunity.microsoft.com/t5/intune-customer-success/enrolling-microsoft-teams-rooms-on-windows-devices-with/ba-p/3246986)

**To install using Intune**

1. Sign in to the [Microsoft Endpoint Manager admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
1. Select **Apps** > **All apps** > **Add**.
1. In the **Select app type** pane, under **Other** app types, select **Line-of-business app**.
1. Click **Select**. The **Add app** steps are displayed. 
1. In the **Add app** pane, click **Select app package file**.
   1. In the **App package file** pane, select  **Browse**. Then, select the **ManagedRoomsInstaller.msi** file downloaded previously (refer to the prerequisites section).
   1. When you're finished, select **OK** on the **App package file** pane to add the app.
1. In the **App information** page, perform the following changes:
   1. Publisher: enter **Microsoft Corporation**.
   1. Ignore app version: select **Yes**.

      > [!NOTE]
      > The MTR Pro agent is self updating; hence, you should explicitly ignore the app version (any baseline version can update automatically).

   1. (Optional) Category: Select **Computer Management**.
   
1. Click **Next** to display the **Assignments** page.
   1. Under the **Required** section, click **+ add group** to target a group of devices for installation of the agent.
   1. In the **Select group** pane, type the group name in the Search box (refer to prerequisites above) and click on the desired **group** and click **Select**.
      For more information, see [Add groups to organize users and devices](https://go.microsoft.com/fwlink/?linkid=2202166) and [Assign apps to groups with Microsoft Intune](https://go.microsoft.com/fwlink/?linkid=2202270).
1. Click **Next** to display the **Review + create** page.
1. Review the values and settings you entered for the app. When you're done, click **Create** to add the app to Intune.

Once the process is completed, your devices will start installing the MTR Pro agent after a few minutes.

> [!NOTE]
> Following installation, the Teams Rooms Pro management agent may take up to eight hours to execute a self-update to the latest version and become listed in the Teams Rooms Pro management portal. To expedite the automatic enrollment in the Teams Rooms Pro management portal, consider restarting the Teams Rooms device following the agent deployment.

## Unenrolling and uninstalling monitoring software

To unenroll the device, remove the monitoring agent from the Teams Rooms device as follows:

1. On the device being monitored, log in the device as administrator. Be sure to follow the steps in *Performing operations as the Admin user of the device*.
1. Download reset script from [aka.ms/MTRPDeviceOffBoarding](https://aka.ms/MTRPDeviceOffBoarding).
1. Extract the script somewhere on the device and copy the path.
1. Open PowerShell as administrator: In the Windows ***Search*** field (bottom-left section of the screen), enter 'PowerShell' and right-click ***Windows PowerShell***.
1. Select *"Run as Administrator"* and accept UAC prompt.
1. Enter *Set-ExecutionPolicy –ExecutionPolicy RemoteSigned* , then press **Y** on next prompt.
1. Paste or type the full path to the unzipped offboarding script into the PowerShell window and press **Enter**.
   Example:

   ```powershell
   C:\Users\admin\Downloads\MTRP\_Device\_Offboarding\MTRP\_Device\_Offboarding.ps1
   ```

1. This command resets the device to user standard MTR updates and removes the Teams Rooms Pro management monitoring agent and files.

1. From the left-hand menu in the Microsoft Teams Rooms Pro Management portal, select **Rooms**.
1. In the list of rooms provided, choose the room you want to unenroll and select **Remove** to stop getting incident alerts or investigation tickets, or to report an incident for the room.

## Troubleshooting table

> [!NOTE]
> All Microsoft Teams Rooms Pro monitoring errors are logged on a specific Event Log file named **Microsoft Managed Rooms**.

***Application runtime log file location*** =

C:\Windows\ServiceProfiles\LocalService\AppData\Local\ServicePortalAgent\ app-x.x.x\ServicePortalAgent\ServicePortal\_Verbose\_LogFile.log, where **x.x.x** is the app version number.

|Symptom|Recommended Procedure|
|---|---|
|You receive an error message stating: </p><p> ***ERROR: Please run this application with*** <br> ***elevated privileges***|Run the application with escalated privileges and try again.|
|||
|You receive an error message stating: </p><p> ***TPM data cannot be found***|Ensure that your device has TPM (Trusted Platform Module) turned on in its BIOS. This is found in the security settings of the device BIOS.|
|||
|You receive an error message: </p><p> ***ERROR: Local user account named 'Admin' or 'Skype' not found***|Ensure that the user accounts exist on the certified Microsoft Teams Rooms systems device.|
|||
|You receive any error state messages that aren't covered here.|Provide a copy of your installation log to your Microsoft Teams System support agent.|
