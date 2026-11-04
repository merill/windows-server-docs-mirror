---
layout: Conceptual
title: Create and configure a virtual switch with Hyper-V | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/virtualization/hyper-v/get-started/create-a-virtual-switch-for-hyper-v-virtual-machines
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: hyper-v
ms.update-cycle: 1095-days
description: Learn how to create and configure a virtual switch for use by the Hyper-V host and guest virtual machines.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2025-01-29T00:00:00.0000000Z
zone_pivot_groups: windows
locale: en-us
document_id: 61dec703-ec84-c4fc-ab45-83decde810f2
document_version_independent_id: 2b0ebf31-825f-39cd-d7c8-8e207344252e
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/virtualization/hyper-v/get-started/Create-a-virtual-switch-for-Hyper-V-virtual-machines.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: virtualization/hyper-v/get-started/create-a-virtual-switch-for-hyper-v-virtual-machines
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/virtualization/hyper-v/get-started/Create-a-virtual-switch-for-Hyper-V-virtual-machines.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 74f40c34-8979-05ad-5a1b-2e61edc8fbaf
---

# Create and configure a virtual switch with Hyper-V | Microsoft Learn

This article shows you how to create and configure your virtual switch using Hyper-V Manager or PowerShell. A virtual switch allows virtual machines created on Hyper-V hosts to communicate with other computers.

::: zone pivot="windows-server"

When you first install the Hyper-V role on Windows Server, you can optionally create a virtual switch at the same time. To learn more about virtual switches, see [Hyper-V Virtual Switch](../virtual-switch).

For more information about how you can set up your networking infrastructure with Windows Server, review the [Networking](../../../networking/) documentation.

::: zone-end

## Prerequisites

Before you can create and configure your virtual switch, your computer must meet the following prerequisites:

::: zone pivot="windows-server"

- The Hyper-V server role must be installed.

::: zone-end

::: zone pivot="windows"

- Hyper-V must be enabled

::: zone-end

- Virtual switch types are: external, internal. and private. Determine [what type of virtual switch you need to create](../plan/plan-hyper-v-networking-in-windows-server).
- Identify which network you connect your computer to. Review the [Core network planning](../../../networking/core-network-guide/core-network-guide#BKMK_planning) article for more information.
- Have administrative rights.

## Create a virtual switch

Once you complete the prerequisites, you're ready to create your virtual switch. In this section, we create a basic virtual switch by following these steps.

# [Hyper-V Manager](#tab/hyper-v-manager)
Here's how to create a virtual switch using Hyper-V Manager.

1. Open Hyper-V Manager.
2. From the **Actions** pane, select **Virtual Switch Manager**.
3. Choose the type of virtual switch, then select **Create Virtual Switch**.
4. Enter a name for the virtual switch, then perform one of the following steps.

    1. If you selected *external*, choose the network adapter (NIC) that you want to use, then select **OK**.

        You're prompted with a warning that the change may disrupt your network connectivity; select **Yes** if you're happy to continue.
    2. If you selected *internal* or *private*, select **OK**.

# [PowerShell](#tab/powershell)
Here's how to create a virtual switch using the [New-VMSwitch](/en-us/powershell/module/hyper-v/new-vmswitch) command.

1. Run PowerShell on your computer in an elevated session.
2. Find existing network adapters by running the [Get-NetAdapter](/en-us/powershell/module/netadapter/get-netadapter) cmdlet. Identify the network adapter name that you want to use for the virtual switch.

    ```powershell
    Get-NetAdapter
    ```
3. To create an *external* virtual switch, run the following command, replacing the placeholders `<switch-name>` and `<netadapter-name>` with your own values.

    ```powershell
    New-VMSwitch -Name <switch-name>  -NetAdapterName <netadapter-name>
    ```

    Use either the parameter **NetAdapterName**, or **NetAdapterInterfaceDescription** to implicitly set the type of the virtual switch to *external*.
4. To create an *internal* or *private* switch, run the following command. Replace `<switch-name>` with the name of your switch and `<switch-type>` with either `Internal` or `Private`.

    ```powershell
    New-VMSwitch -Name <switch-name> -SwitchType <switch-type>
    ```

For more advanced PowerShell scripts that cover improved or new virtual switch features in Windows Server, see [Remote Direct Memory Access and Switch Embedded Teaming](/en-us/azure/azure-local/concepts/host-network-requirements?context=/windows-server/context/windows-server-virtualization).

---

## Management Operating System sharing

An external virtual switch allows your virtual machines to connect to an external network. You can also allow the management operating system to share the same selected network adapter. To begin, follow these steps.

# [Hyper-V Manager](#tab/hyper-v-manager)
Here's how to allow the management operating system to share the selected network adapter switch using Hyper-V Manager.

1. Open Hyper-V Manager.
2. From the **Actions** pane, select **Virtual Switch Manager**.
3. Select the virtual switch you wish to configure, check the **Allow management operating system to share this network adapter** and select **OK**.

    You'll be prompted with a warning that the change may disrupt your network connectivity; select **Yes** if you're happy to continue.

# [PowerShell](#tab/powershell)
Here's how to allow a virtual switch to be shared with the management OS using the [Set-VMSwitch](/en-us/powershell/module/hyper-v/set-vmswitch) command.

1. Run PowerShell on your computer in an elevated session.
2. To allow a virtual switch to be shared with the management OS, run the following commands. Replace the placeholder `<vmswitch name>` the name of your virtual switch.

    ```powershell
    Set-VMSwitch -Name <vmswitch name> -AllowManagementOS $true
    ```

---

## Virtual LAN (VLAN) identification

You can specify the VLAN identification (ID) used by virtual machines network adapters and virtual switches. For virtual switches connected to either an external or internal network, you can specify the (VLAN) ID. The VLAN ID number is used by the management operating system and virtual machines communicating through this virtual switch.

You can also configure your virtual switch with other VLAN options, such port mode and the native VLAN ID. For these options, you need to use PowerShell and ensure the configuration is compatible with your networks configuration.

To configure the VLAN identification for the switch, follow these steps.

# [Hyper-V Manager](#tab/hyper-v-manager)
Here's how to specify the VLAN ID using the Hyper-V Manager.

1. Open Hyper-V Manager.
2. From the **Actions** pane, select **Virtual Switch Manager**.
3. Select the virtual switch you wish to configure, check the **Enable virtual LAN identification for management operating system**.

    1. You can enter any VLAN ID number or leave the default, then select **OK**.

        You're prompted to warn you that the change may disrupt your network connectivity, select **Yes** if you're happy to continue.

VLAN identifiers should be consistent with your network to ensure compatibility between your computer, virtual machines, and other network devices.

# [PowerShell](#tab/powershell)
Here's how to set a VLAN identification using the [Set-VMNetworkAdapterVlan](/en-us/powershell/module/hyper-v/set-vmnetworkadaptervlan) command.

1. Run PowerShell on your computer in an elevated session.
2. To set the VLAN ID to tag traffic and set the port mode to access, run the following commands. Replace the placeholder `<vmswitch name>` the name of your virtual switch and `<id>` with your VLAN ID.

    ```powershell
    Set-VMNetworkAdapterVlan -ManagementOS -VMNetworkAdapterName <vmswitch name> -Access -VlanId <id>
    ```

    Or

    To set port mode to trunk, the native VLAN ID, and allowed VLAN ID list, run the following commands. Replace the placeholder `<vmswitch name>` the name of your virtual switch and `<id>` with your VLAN ID. Replace `<allowed ids>` with a list of allowed VLAN IDs, for example, `200-210`.

    ```powershell
    $parameters = @{
         ManagementOS = $true
         VMNetworkAdapterName = <vmswitch name>
         Trunk = $true
         NativeVlanId = <id>
         AllowedVlanIdList = <allowed ids>
    }
    Set-VMNetworkAdapterVlan @parameters
    ```

This example uses splatting to pass parameter values from the `$parameters` variable to the command. Learn more about [Splatting](/en-us/powershell/module/microsoft.powershell.core/about/about_splatting).

---

::: zone pivot="windows"

## NAT networking

Network Address Translation (NAT) gives a virtual machine access to your computer's network by combining the host computer's IP address with a port through an internal Hyper-V Virtual Switch.

This has a few useful properties:

1. NAT Conserves IP addresses by mapping an external IP address and port to a much larger set of internal IP addresses.
2. NAT allows multiple virtual machines to host applications that require identical (internal) communication ports by mapping these to unique external ports.
3. NAT uses an internal switch -- creating an internal switch doesn't cause you to use network connection and tends to interfere less with a computer's networking.

To set up a NAT network and connect it to a virtual machine, follow the [NAT networking user guide](/en-us/virtualization/hyper-v-on-windows/user-guide/setup-nat-network).

::: zone-end