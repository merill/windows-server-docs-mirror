---
layout: Conceptual
title: Manage Hyper-V Integration Services | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/virtualization/hyper-v/manage/manage-hyper-v-integration-services
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: hyper-v
ms.update-cycle: 1095-days
description: This article describes how to turn Hyper-V integration services on and off, and install them if needed.
ms.author: roharwoo
author: robinharwood
ms.date: 2025-02-18T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: cf5eedca-3535-d00e-98ab-9e25496a30a7
document_version_independent_id: 797c37a7-ccd5-ed59-2dc3-5cf3892bbf3b
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/virtualization/hyper-v/manage/Manage-Hyper-V-integration-services.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: virtualization/hyper-v/manage/manage-hyper-v-integration-services
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/virtualization/hyper-v/manage/Manage-Hyper-V-integration-services.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 5d9a04ca-b2d2-97ab-5128-d5b8b9a7bf24
---

# Manage Hyper-V Integration Services | Microsoft Learn

Hyper-V Integration Services enhance virtual machine performance and provide convenience features by leveraging two-way communication with the Hyper-V host. Many of these services are conveniences, such as guest file copy, while others are important to the virtual machine's functionality, such as synthetic device drivers. This set of services and drivers are sometimes referred to as *integration components*. You can control whether or not individual convenience services operate for any given virtual machine. The driver components aren't intended to be serviced manually.

For details about each integration service, see [Hyper-V Integration Services](/en-us/virtualization/hyper-v-on-windows/reference/integration-services).

Important

Each service you want to use must be enabled in both the host and guest in order to function. When you enable a service in the host, it automatically starts running in the guest. All integration services except *Hyper-V Guest Service Interface* are on by default on Windows guest operating systems. The services can be turned on and off individually. The next sections show you how.

## Turn an integration service on or off using Hyper-V Manager

1. From the center pane, right-click the virtual machine and select **Settings**.
2. From the left pane of the **Settings** window, under **Management**, select **Integration Services**.

The Integration Services pane lists all integration services available on the Hyper-V host, and whether the host has enabled the virtual machine to use them.

### Turn an integration service on or off using PowerShell

To do this in PowerShell, use [Enable-VMIntegrationService](/en-us/powershell/module/hyper-v/enable-vmintegrationservice) and [Disable-VMIntegrationService](/en-us/powershell/module/hyper-v/disable-vmintegrationservice).

The following examples demonstrate turning the guest file copy integration service on and off for a virtual machine named *DemoVM*.

1. Get a list of running integration services:

    ```powershell
    Get-VMIntegrationService -VMName "DemoVM"
    ```
2. The output should look like this:

    ```powershell
    VMName      Name                    Enabled PrimaryStatusDescription SecondaryStatusDescription
    ------      ----                    ------- ------------------------ --------------------------
    DemoVM      Guest Service Interface False   OK
    DemoVM      Heartbeat               True    OK                       OK
    DemoVM      Key-Value Pair Exchange True    OK
    DemoVM      Shutdown                True    OK
    DemoVM      Time Synchronization    True    OK
    DemoVM      VSS                     True    OK
    ```
3. Turn on Guest Service Interface:

    ```powershell
    Enable-VMIntegrationService -VMName "DemoVM" -Name "Guest Service Interface"
    ```
4. Verify that Guest Service Interface is enabled:

    ```powershell
    Get-VMIntegrationService -VMName "DemoVM"
    ```
5. Turn off Guest Service Interface:

    ```powershell
    Disable-VMIntegrationService -VMName "DemoVM" -Name "Guest Service Interface"
    ```

## Checking the guest's integration services version

Some features may not work correctly or at all if the guest's integration services aren't current. To get the version information for Windows, sign in to the guest operating system, open a command prompt, and run this command:

```powershell
REG QUERY "HKLM\Software\Microsoft\Virtual Machine\Auto" /v IntegrationServicesVersion
```

## Start and stop an integration service from a Windows guest

In order for an integration service to be fully functional, its corresponding service must be running within the guest in addition to being enabled on the host. In Windows guests, each integration service is listed as a standard Windows service. You can use the Services applet in Control Panel or PowerShell to stop and start these services.

Important

Stopping an integration service may severely affect the host's ability to manage your virtual machine. To work correctly, each integration service you want to use must be enabled on both the host and guest. As a best practice, you should only control integration services from Hyper-V using the instructions in this article. The matching service in the guest operating system stops or starts automatically when you change its status in Hyper-V. If you start a service in the guest operating system but it's disabled in Hyper-V, the service stops. If you stop a service in the guest operating system that is enabled in Hyper-V, Hyper-V starts it again. If you disable the service in the guest, Hyper-V is unable to start it.

### Use Windows Services to start or stop an integration service within a Windows guest

1. Open Services manager by running `services.msc` as an Administrator or by double-clicking the Services icon in Control Panel.

    ![Screen shot that shows the Windows Services pane](media/hvservices.png)
2. Find the services that start with **Hyper-V**.
3. Right-click the service you want start or stop. Select the desired action.

### Use PowerShell to start or stop an integration service within a Windows guest

1. To get a list of integration services, run:

    ```powershell
    Get-Service -Name vmic* | FT -AutoSize
    ```
2. The output should look similar to this:

    ```powershell
    Status  Name               DisplayName
    ------  ----               -----------
    Running vmicguestinterface Hyper-V Guest Service Interface
    Running vmicheartbeat      Hyper-V Heartbeat Service
    Running vmickvpexchange    Hyper-V Data Exchange Service
    Running vmicrdv            Hyper-V Remote Desktop Virtualization Service
    Running vmicshutdown       Hyper-V Guest Shutdown Service
    Running vmictimesync       Hyper-V Time Synchronization Service
    Stopped vmicvmsession      Hyper-V PowerShell Direct Service
    Running vmicvss            Hyper-V Volume Shadow Copy Requestor
    ```
3. Run either [Start-Service](/en-us/powershell/module/microsoft.powershell.management/start-service) or [Stop-Service](/en-us/powershell/module/microsoft.powershell.management/stop-service). For example, to turn off Windows PowerShell Direct, run:

    ```powershell
    Stop-Service -Name vmicvmsession
    ```

## Start and stop an integration service from a Linux guest

Linux integration services are generally provided through the Linux kernel. The Linux integration services driver is named **hv\_utils**.

1. To find out if **hv\_utils** is loaded, use this command:

    ```bash
    lsmod | grep hv_utils
    ```
2. The output should look similar to this:

    ```bash
    Module                  Size   Used by
    hv_utils               20480   0
    hv_vmbus               61440   8 hv_balloon,hyperv_keyboard,hv_netvsc,hid_hyperv,hv_utils,hyperv_fb,hv_storvsc
    ```
3. To find out if the required daemons are running, use this command.

    ```bash
    ps -ef | grep hv
    ```
4. The output should look similar to this:

    ```bash
    root       236     2  0 Jul11 ?        00:00:00 [hv_vmbus_con]
    root       237     2  0 Jul11 ?        00:00:00 [hv_vmbus_ctl]
    ...
    root       252     2  0 Jul11 ?        00:00:00 [hv_vmbus_ctl]
    root      1286     1  0 Jul11 ?        00:01:11 /usr/lib/linux-tools/3.13.0-32-generic/hv_kvp_daemon
    root      9333     1  0 Oct12 ?        00:00:00 /usr/lib/linux-tools/3.13.0-32-generic/hv_kvp_daemon
    root      9365     1  0 Oct12 ?        00:00:00 /usr/lib/linux-tools/3.13.0-32-generic/hv_vss_daemon
    user     43774 43755  0 21:20 pts/0    00:00:00 grep --color=auto hv
    ```
5. To see what daemons are available, run:

    ```bash
    compgen -c hv_
    ```
6. The output should look similar to this:

    ```bash
    hv_vss_daemon
    hv_get_dhcp_info
    hv_get_dns_info
    hv_set_ifconfig
    hv_kvp_daemon
    hv_fcopy_daemon
    ```

    Integration service daemons that might be listed include the following. If any are missing, they might not be supported on your system or they might not be installed. Find details, see [Supported Linux and FreeBSD virtual machines for Hyper-V on Windows](../supported-linux-and-freebsd-virtual-machines-for-hyper-v-on-windows).

    - **hv\_vss\_daemon**: This daemon is required to create live Linux virtual machine backups.
    - **hv\_kvp\_daemon**: This daemon allows setting and querying intrinsic and extrinsic key value pairs.
    - **hv\_fcopy\_daemon**: This daemon implements a file copying service between the host and guest.

### Examples

These examples demonstrate stopping and starting the KVP daemon, named `hv_kvp_daemon`.

1. Use the process ID (PID) to stop the daemon's process. To find the PID, look at the second column of the output, or use `pidof`. Hyper-V daemons run as root, so you'll need root permissions.

    ```bash
    sudo kill -15 `pidof hv_kvp_daemon`
    ```
2. To verify that all `hv_kvp_daemon` processes are gone, run:

    ```bash
    ps -ef | hv
    ```
3. To start the daemon again, run the daemon as root:

    ```bash
    sudo hv_kvp_daemon
    ```
4. To verify that the `hv_kvp_daemon` process is listed with a new process ID, run:

    ```bash
    ps -ef | hv
    ```

## Keep integration services up to date

We recommend that you keep integration services up to date to get the best performance and most recent features for your virtual machines. This happens for Windows guests by default if they are set up to get important updates from Windows Update. Linux guests using current kernels contain integration services built in, but there may be optional updates available. You will receive the latest integration components when you update the kernel. For more information about Linux guests, see [Supported Linux and FreeBSD virtual machines for Hyper-V on Windows](../supported-linux-and-freebsd-virtual-machines-for-hyper-v-on-windows).

## Install or update integration services for Hyper-V hosts earlier than Windows Server 2016 and Windows 10

For Hyper-V hosts earlier than Windows Server 2016 and Windows 10, you'll need to **manually install or update** the integration services in the guest operating systems.

To manually install or update the integration services:

1. Open Hyper-V Manager.
2. Connect to the virtual machine. Right-click the virtual machine and select **Connect**.
3. From the Action menu of Virtual Machine Connection, select **Insert Integration Services Setup Disk**. This action loads the setup disk in the virtual DVD drive. Depending on the guest operating system, you might need to start the installation manually from File Explorer.
4. After the installation finishes, integration services are available for use.