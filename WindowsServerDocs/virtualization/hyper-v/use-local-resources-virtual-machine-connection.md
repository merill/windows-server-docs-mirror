---
layout: Conceptual
title: Use local resources on Hyper-V with VMConnect | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/virtualization/hyper-v/use-local-resources-virtual-machine-connection
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: hyper-v
ms.update-cycle: 1095-days
description: Describes the requirements for using local resources with Virtual Machine Connection (VMConnect) on Hyper-V.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2025-02-18T00:00:00.0000000Z
locale: en-us
document_id: 66ef6164-c7ec-343b-c438-20bee4147c37
document_version_independent_id: 66ef6164-c7ec-343b-c438-20bee4147c37
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/virtualization/hyper-v/use-local-resources-virtual-machine-connection.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: virtualization/hyper-v/use-local-resources-virtual-machine-connection
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/virtualization/hyper-v/use-local-resources-virtual-machine-connection.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
platformId: 1271a525-3d8a-7eb2-0fe2-87e51bfc9fa5
---

# Use local resources on Hyper-V with VMConnect | Microsoft Learn

Virtual Machine Connection (VMConnect) lets you use a computer's local resources in a virtual machine, like a removable USB flash drive or a printer. Enhanced session mode also lets you resize the VMConnect window. This article shows you how to configure the host and then give the virtual machine access to a local resource.

Enhanced session mode and Type clipboard text are available only for virtual machines that run recent Windows operating systems. See Requirements for using local resources.

For virtual machines that run Ubuntu, see [Changing Ubuntu Screen Resolution in a Hyper-V VM](/en-us/archive/blogs/virtual_pc_guy/changing-ubuntu-screen-resolution-in-a-hyper-v-vm).

## Choose a local resource

Local resources include printers, the clipboard, and local drive(s) on the computer where you're running VMConnect. For more information, see Requirements for using local resources.

To choose a local resource:

1. Open VMConnect.
2. Select the virtual machine that you want to connect to.
3. Select **Show options**.

    ![Screenshot that calls out Show options on the bottom left of the dialog box.](media/hyperv-vmconnect-displayconfig.png)
4. Select **Local resources**.

    ![Screenshot that calls out the Local resources tab.](media/hyperv-vmconnect-displayconfig-localresources.png)
5. Select **More**.

    ![Screenshot that calls out the More button.](media/hyperv-vmconnect-displayconfig-localresourcesmore.png)
6. Select the drive that you want to use on the virtual machine and click **Ok**.

    ![Screenshot that shows the local resources and drives that you can select.](media/hyperv-vmconnect-settings-localresourcesdrives.png)
7. Select **Save my settings for future connections to this virtual machine**.

    ![Screenshot that calls out the checkbox to select for this option.](media/hyperv-vmconnect-savesettings.png)
8. Select **Connect**.

The path to the local drive shared to the virtual machine, in a Windows-based guest VM, is located at **This PC** under **Redirected drives and folders**. The path for a Linux-based guest VM is located at **/home/shared-drives**.

## Edit VMConnect settings

You can easily edit your connection settings for VMConnect by running the following command in Windows PowerShell or the command prompt:

`VMConnect.exe <ServerName> <VMName> /edit`

Note

An elevated command prompt may be required.

## Requirements for using local resources

To be able to use a computer's local resources on a virtual machine:

- The Hyper-V host must have **Enhanced session mode policy** and **Enhanced session mode** settings turned on.
- The computer on which you use VMConnect must run at least Windows 10, or Windows Server 2016.
- The virtual machine must have Remote Desktop Services enabled, and run at least Windows 10, or Windows Server 2016.

If the computer running VMConnect and the virtual machine both meet the requirements, you can use any of the following local resources if they're available:

- Display configuration
- Audio
- Printers
- Clipboards for copy and paste
- Smart cards
- USB devices
- Drives
- Supported plug and play devices

## Why use a computer's local resources?

You may want to use the computer's local resources to:

- Troubleshoot a virtual machine without a network connection to the virtual machine.
- Copy and paste files to and from the virtual machine in the same way you copy and paste using a Remote Desktop Connection (RDP).
- Sign in to the virtual machine by using a smart card.
- Print from a virtual machine to a local printer.
- Test and troubleshoot developer applications that require USB and sound redirection without using RDP.