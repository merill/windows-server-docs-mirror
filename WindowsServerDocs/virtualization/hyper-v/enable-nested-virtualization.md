---
layout: Conceptual
title: Run Hyper-V in a Virtual Machine with Nested Virtualization | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/virtualization/hyper-v/enable-nested-virtualization
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: hyper-v
ms.update-cycle: 1095-days
description: Learn how to use nested virtualization to run Hyper-V in a virtual machine and emulate configurations that normally require multiple hosts.
keywords: windows 10, windows 11, hyper-v
author: robinharwood
ms.author: roharwoo
ms.date: 2025-06-10T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 9026b0ef-6af6-972e-34c9-09d770a38464
document_version_independent_id: 9026b0ef-6af6-972e-34c9-09d770a38464
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/virtualization/hyper-v/enable-nested-virtualization.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: virtualization/hyper-v/enable-nested-virtualization
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/virtualization/hyper-v/enable-nested-virtualization.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 7e136990-c4c0-654f-38d9-ee4e89cffcfb
---

# Run Hyper-V in a Virtual Machine with Nested Virtualization | Microsoft Learn

Nested virtualization enables you to run Hyper-V inside a virtual machine, allowing you to emulate complex environments without needing multiple physical hosts. This article explains how to configure and use nested virtualization on supported Windows platforms, including prerequisites, setup steps, and networking options. Use this article to test scenarios, run emulators, or develop solutions that require multiple layers of virtualization.

To learn more about Nested Virtualization and supported scenarios, see [What is Nested Virtualization for Hyper-V?](nested-virtualization).

## Prerequisites

### Intel processor with VT-x and EPT technology

- The Hyper-V host must be either Windows Server 2016 or later, or Windows 10 or later.
- VM configuration version 8.0 or higher.

### AMD EPYC / Ryzen processor or later

- The Hyper-V host must be either Windows Server 2022 or later, or Windows 11 or later.
- VM configuration version 9.3 or higher.

Note

The guest can be any Windows supported guest operating system. Some newer versions of Windows can use extra CPU features that improve performance. To enable Nested Virtualization in an Azure VM, make sure to set Security Type as **"Standard"**.

## Enable Nested Virtualization

To enable nested virtualization, follow these steps:

1. Create a virtual machine. See the prerequisites for the required OS and VM versions.
2. While the virtual machine is in the OFF state, run the following command on the physical Hyper-V host to enable nested virtualization for the virtual machine.

    ```powershell
    Set-VMProcessor -VMName <VMName> -ExposeVirtualizationExtensions $true
    ```
3. Start the virtual machine.
4. Install Hyper-V within the virtual machine, just like you would for a physical server. For more information on installing Hyper-V, see, [Install Hyper-V](/en-us/windows-server/virtualization/hyper-v/get-started/install-hyper-v).

Note

With Windows Server 2019 and earlier as the first level VM, the number of vCPUs should be 225 or less. To learn more about virtual machine limits, see [Maximums for virtual machines](/en-us/windows-server/virtualization/hyper-v/plan/plan-hyper-v-scalability-in-windows-server#maximums-for-virtual-machines).

## Disable Nested Virtualization

You can disable nested virtualization for a stopped virtual machine using the following PowerShell command:

```powershell
Set-VMProcessor -VMName <VMName> -ExposeVirtualizationExtensions $false
```

## Networking options

There are two options for networking with nested virtual machines:

1. MAC address spoofing
2. NAT networking

### MAC address spoofing

In order for network packets to be routed through two virtual switches, MAC address spoofing must be enabled on the first (L1) level of virtual switch. To enable MAC address spoofing, run the following PowerShell command.

```powershell
Get-VMNetworkAdapter -VMName <VMName> | Set-VMNetworkAdapter -MacAddressSpoofing On
```

### Network Address Translation (NAT)

The second option relies on network address translation (NAT). This approach is best suited for cases where MAC address spoofing isn't possible, like in a public cloud environment.

First, a virtual NAT switch must be created in the host virtual machine (the "middle" VM). The following example creates a new internal switch named `VmNAT` and creates a NAT object for all IP addresses in the `192.168.100.0/24` subnet.

```powershell
New-VMSwitch -Name VmNAT -SwitchType Internal
New-NetNat –Name LocalNAT –InternalIPInterfaceAddressPrefix “192.168.100.0/24”
```

Next, assign an IP address to the net adapter:

```powershell
Get-NetAdapter "vEthernet (VmNat)" | New-NetIPAddress -IPAddress 192.168.100.1 -AddressFamily IPv4 -PrefixLength 24
```

Each nested virtual machine must have an IP address and gateway assigned to it. The gateway IP must point to the NAT adapter from the previous step. You might also want to assign a DNS server:

```powershell
Get-NetAdapter "vEthernet (VmNat)" | New-NetIPAddress -IPAddress 192.168.100.2 -DefaultGateway 192.168.100.1 -AddressFamily IPv4 -PrefixLength 24
Netsh interface ip add dnsserver “vEthernet (VmNat)” address=<my DNS server>
```