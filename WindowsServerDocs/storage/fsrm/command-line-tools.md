---
layout: Conceptual
title: File Server Resource Manager Command-Line Tools | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/fsrm/command-line-tools
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: This article describes Windows Server 2016 command-line tools
ms.date: 2017-07-07T00:00:00.0000000Z
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
locale: en-us
document_id: 89bc243c-323a-0eae-16dc-16b9d540a386
document_version_independent_id: 0e0f8382-9571-d6fa-78b5-63680eaab92f
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/fsrm/command-line-tools.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/fsrm/command-line-tools
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/fsrm/command-line-tools.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/4e834929-0ce1-4c1d-9c81-fcb14721edfb
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/75670257-a3f0-4627-9981-8046f99219e6
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: a8a6bb18-734c-7936-4ef4-cd700eded146
---

# File Server Resource Manager Command-Line Tools | Microsoft Learn

File Server Resource Manager installs the [FileServerResourceManager](/en-us/powershell/module/fileserverresourcemanager/) PowerShell cmdlets as well as the following command-line tools:

- **Dirquota.exe**. Use to create and manage quotas, auto apply quotas, and quota templates.
- **Filescrn.exe**. Use to create and manage file screens, file screen templates, file screen exceptions, and file groups.
- **Storrept.exe**. Use to configure report parameters and generate storage reports on demand. Also use to create report tasks, which you can schedule by using **schtasks.exe**.

You can use these tools to manage storage resources on a local computer or a remote computer. For more information about these command-line tools, see the following references:

- **Dirquota**: https://go.microsoft.com/fwlink/?LinkId=92741
- **Filescrn**: https://go.microsoft.com/fwlink/?LinkId=92742
- **Storrept**: https://go.microsoft.com/fwlink/?LinkId=92743

Note

To see command syntax and the available parameters for a command, run the command with the **/?** parameter.

## Remote management using the command-line tools

Each tool has several options for performing actions similar to those that are available in the File Server Resource Manager MMC snap-in. To have a command perform an action on a remote computer instead of the local computer, use the **/remote**:*ComputerName* parameter.

For example,**Dirquota.exe** includes a **template export** parameter to write quota template settings to an XML file, and a **template import** parameter to import template settings from the XML file. Adding the **/remote**:*ComputerName* parameter to the **Dirquota.exe template import** command will import the templates from the XML file on the local computer to the remote computer.

Note

When you run the command-line tools with the **/remote**:*ComputerName* parameter to perform a template export (or import) on a remote computer, the templates are written to (or copied from) an XML file on the local computer.

## Additional considerations

To manage remote resources with the command-line tools:

- You must be logged on with a domain account that is a member of the **Administrators** group on the local computer and on the remote computer.
- You must run the command-line tools from an elevated Command Prompt window. To open an elevated Command Prompt window, click **Start**, point to **All Programs**, click **Accessories**, right-click **Command Prompt**, and then click **Run as administrator**.
- The remote computer must be running Windows Server, and File Server Resource Manager must be installed.
- The **Remote File Server Resource Manager Management** exception on the remote computer must be enabled. Enable this exception by using Windows Firewall in Control Panel.

## Additional References

- [Managing Remote Storage Resources](managing-remote-storage-resources)