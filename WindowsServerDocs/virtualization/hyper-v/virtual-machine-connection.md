---
layout: Conceptual
title: Hyper-V Virtual Machine Connection | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/virtualization/hyper-v/virtual-machine-connection
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: hyper-v
ms.update-cycle: 1095-days
description: Describes Virtual Machine Connection, and includes details on how to do common tasks, such as send Ctrl-Alt-Delete to the virtual machine.
ms.topic: concept-article
ms.author: roharwoo
author: robinharwood
ms.date: 2025-06-26T00:00:00.0000000Z
locale: en-us
document_id: 44b9e641-6609-4902-9081-75d6d0ca5d96
document_version_independent_id: 44b9e641-6609-4902-9081-75d6d0ca5d96
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/virtualization/hyper-v/virtual-machine-connection.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: virtualization/hyper-v/virtual-machine-connection
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/virtualization/hyper-v/virtual-machine-connection.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
platformId: c1721b17-d553-ae10-91f9-4a387b92a0ba
---

# Hyper-V Virtual Machine Connection | Microsoft Learn

Virtual Machine Connection (VMConnect) is a tool you can use to connect to a virtual machine to install or interact with the guest operating system in a virtual machine. Some of the tasks you can perform by using VMConnect include the following:

- Start and shut down a virtual machine
- Connect to a DVD image (.iso file) or a USB flash drive
- Create a checkpoint
- Modify the settings of a virtual machine

## Tips for using VMConnect

You might find the following information helpful for using VMConnect:

| To do this… | Do this… |
| --- | --- |
| Send mouse clicks or keyboard input to the virtual machine | Click anywhere in the virtual machine window. The mouse pointer might appear as a small dot when you connect to a running virtual machine. |
| Return mouse clicks or keyboard input to the physical computer | Press CTRL+ALT+LEFT ARROW and then move the mouse pointer outside of the virtual machine window. This mouse release key combination can be changed in the Hyper-V settings in Hyper-V Manager. |
| Send the CTRL+ALT+DELETE key combination to a virtual machine | Select **Action** &gt; **Ctrl+Alt+Delete** or use the key combination CTRL+ALT+END. |
| Switch from window mode to full-screen mode | Select **View** &gt; **Full Screen Mode**. To switch back to window mode, press CTRL+ALT+BREAK. |
| Create a checkpoint to capture the current state of the machine for troubleshooting | Select **Action** &gt; **Checkpoint** or use the key combination CTRL+N. |
| Change the settings of the virtual machine | Select **File** &gt; **Settings**. |
| Connect to a DVD image (.iso file) or a virtual floppy disk (.vfd file) | Select **Media**.<br>Virtual floppy disks aren't supported for generation 2 virtual machines. For more information, see [Should I create a generation 1 or 2 virtual machine in Hyper-V?](plan/should-i-create-a-generation-1-or-2-virtual-machine-in-hyper-v). |
| Use a host's local resources on Hyper-V virtual machine like a USB flash drive | Turn on enhanced session mode on the Hyper-V host, use VMConnect to connect to the virtual machine, and before you connect, choose the local resource that you want to use. For the specific steps, see [Use local resources on Hyper-V virtual machine with VMConnect](use-local-resources-virtual-machine-connection). |
| Change saved VMConnect settings for a virtual machine | Run the following command in Windows PowerShell or the command prompt:<br>`VMConnect.exe <ServerName> <VMName> /edit` |
| Prevent a VMConnect user from taking over another user's VMConnect session | Not having enhanced session mode turned on might pose a security and privacy risk. If a user is connected and logged on to a virtual machine through VMConnect and another authorized user connects to the same virtual machine, the session is taken over by the second user and the first user loses the session. The second user will be able to view the first user's desktop, documents, and applications. |
| Manage integration services or components that allow the VM to communicate with the Hyper-V host | On Hyper-V hosts that run Windows 10 or Windows Server 2016, you can't manage integration services with VMConnect. See these articles: - [Turn on/turn off integration services from the Hyper-V host](manage/manage-hyper-v-integration-services#turn-an-integration-service-on-or-off-using-hyper-v-manager)- [Turn on/turn off integration services from a Windows virtual machine](manage/manage-hyper-v-integration-services#start-and-stop-an-integration-service-from-a-windows-guest)- [Turn on/turn off integration services from a Linux virtual machine](manage/manage-hyper-v-integration-services#start-and-stop-an-integration-service-from-a-linux-guest)- [Keep integration services updated for the virtual machine](manage/manage-hyper-v-integration-services#keep-integration-services-up-to-date). |
| Resize the VMConnect window | You can change the size of the VMConnect window for generation 2 virtual machines that run a Windows operating system. To do this, you might need to turn on enhanced session mode on the Hyper-V host. For virtual machines that run Ubuntu, see [Changing Ubuntu Screen Resolution in a Hyper-V VM](/en-us/archive/blogs/virtual_pc_guy/changing-ubuntu-screen-resolution-in-a-hyper-v-vm). |

## Keyboard shortcuts

By default, keyboard input and mouse clicks are sent to the virtual machine. So you might need to press CTRL + ALT + LEFT ARROW before you use the following shortcut keys.

| Key combination | Description |
| --- | --- |
| CTRL+ALT+LEFT ARROW | Mouse release |
| CTRL+ALT+END | Equivalent of CTRL+ALT+DELETE in the virtual machine |
| CTRL+ALT+BREAK | Switch from full-screen mode back to windowed mode |
| CTRL+O | Opens the settings for the virtual machine |
| CTRL+S | Starts the virtual machine |
| CTRL+N | Creates a checkpoint |
| CTRL+E | Reverts to a checkpoint |
| CTRL+C | Does a screen capture |