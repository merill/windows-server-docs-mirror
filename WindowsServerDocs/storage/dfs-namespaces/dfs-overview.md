---
layout: Conceptual
title: DFS Namespaces overview in Windows Server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/dfs-namespaces/dfs-overview
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
ms.author: roharwoo
ms.topic: overview
author: robinharwood
ms.date: 2025-05-21T00:00:00.0000000Z
description: This article describes DFS Namespaces, which is a role service in Windows Server enabling you to group shared folders located on different servers into one or more logically structured namespaces.
locale: en-us
document_id: ea517059-9b5a-bc03-b1f6-f4b8f8871090
document_version_independent_id: d6c91daf-152c-ab4e-c446-ec2fee710184
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/dfs-namespaces/dfs-overview.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/dfs-namespaces/dfs-overview
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/dfs-namespaces/dfs-overview.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 7c7a0386-3763-940a-06cc-b0baeda0e2b8
---

# DFS Namespaces overview in Windows Server | Microsoft Learn

DFS (Distributed File System) Namespaces is a role service in Windows Server that enables you to group shared folders located on different servers into one or more logically structured namespaces. This makes it possible to give users a virtual view of shared folders, where a single path leads to files located on multiple servers, as shown in the following figure:

![DFS Namespaces technology elements](media/dfs-overview.png)

Here's a description of the elements that make up a DFS namespace:

- **Namespace server** - A namespace server hosts a namespace. The namespace server can be a member server or a domain controller.
- **Namespace root** - The namespace root is the starting point of the namespace. In the previous figure, the name of the root is Public, and the namespace path is \\Contoso\Public. This type of namespace is a domain-based namespace because it begins with a domain name, and its metadata is stored in Active Directory Domain Services (AD DS). Although a single namespace server is shown in the previous figure, a domain-based namespace can be hosted on multiple namespace servers to increase the availability of the namespace.
- **Folder** - Folders without folder targets add structure and hierarchy to the namespace, and folders with folder targets provide users with actual content. When users browse a folder that has folder targets in the namespace, the client computer receives a referral that transparently redirects the client computer to one of the folder targets.
- **Folder targets** - A folder target is the UNC path of a shared folder or another namespace that is associated with a folder in a namespace. The folder target is where data and content is stored. In the previous figure, the folder named Tools has two folder targets, one in London and one in New York, and the folder named Training Guides has a single folder target in New York. A user who browses to \\Contoso\Public\Software\Tools is transparently redirected to the shared folder \\LDN-SVR-01\Tools or \\NYC-SVR-01\Tools, depending on which site the user is currently located in.

This article discusses how to install DFS, what's new, and where to find evaluation and deployment information.

You can administer namespaces by using DFS Management, the [DFS Namespace (DFSN) Cmdlets in Windows PowerShell](/en-us/powershell/module/dfsn/), the **DfsUtil** command, or scripts that call Windows Management Instrumentation (WMI).

## Server requirements and limits

There are no hardware or software requirements for running DFS Management or using DFS Namespaces.

A namespace server is a domain controller or member server that hosts a namespace. The number of namespaces you can host on a server is determined by the operating system running on the namespace server.

Servers that are running at least Windows Server 2012 can host multiple domain-based namespaces in addition to a single stand-alone namespace.

The following table describes other factors to consider when choosing servers to host a namespace.

| Server Hosting Stand-Alone Namespaces | Server Hosting Domain-Based Namespaces |
| --- | --- |
| Must contain an NTFS volume to host the namespace. | Must contain an NTFS volume to host the namespace. |
| Can be a member server or domain controller. | Must be a member server or domain controller in the domain in which the namespace is configured. (This requirement applies to every namespace server that hosts a given domain-based namespace.) |
| Can be hosted by a failover cluster to increase the availability of the namespace. | The namespace can't be a clustered resource in a failover cluster. However, you can locate the namespace on a server that also functions as a node in a failover cluster if you configure the namespace to use only local resources on that server. |

## Install DFS Namespaces

DFS Namespaces and DFS Replication are a part of the File and Storage Services role. The management tools for DFS (DFS Management, the DFS Namespaces module for Windows PowerShell, and command-line tools) are installed separately as part of the Remote Server Administration Tools.

Install DFS Namespaces by using [Windows Admin Center](../../manage/windows-admin-center/overview), Server Manager, or PowerShell, as described in the next sections.

# [Server Manager](#tab/server-manager)
1. Open Server Manager, click **Manage**, and then click **Add Roles and Features**. The Add Roles and Features Wizard appears.
2. On the **Server Selection** page, select the server or virtual hard disk (VHD) of an offline virtual machine on which you want to install DFS.
3. Select the role services and features that you want to install.

    - To install the DFS Namespaces service, on the **Server Roles** page, select **DFS Namespaces**.
    - To install only the DFS Management Tools, on the **Features** page, expand **Remote Server Administration Tools**, **Role Administration Tools**, expand **File Services Tools**, and then select **DFS Management Tools**.

        **DFS Management Tools** installs the DFS Management snap-in, the DFS Namespaces module for Windows PowerShell, and command-line tools, but it doesn't install any DFS services on the server.

# [PowerShell](#tab/powershell)
Open a Windows PowerShell session with elevated user rights, and then type the following command, where &lt;name&gt; is the role service or feature that you want to install. See the following table for a list of relevant role service or feature names:

```PowerShell
Install-WindowsFeature <name>
```

| Role service or feature | Name |
| --- | --- |
| DFS Namespaces | `FS-DFS-Namespace` |
| DFS Management Tools | `RSAT-DFS-Mgmt-Con` |

For example, to install the Distributed File System Tools portion of the Remote Server Administration Tools feature, type:

```PowerShell
Install-WindowsFeature "RSAT-DFS-Mgmt-Con"
```

To install the Distributed File System Tools portion for a client device, type:

```PowerShell
Add-WindowsCapability -Name Rsat.FileServices.Tools~~~~0.0.1.0 -Online
```

To install the DFS Namespaces, and the Distributed File System Tools portions of the Remote Server Administration Tools feature, type:

```PowerShell
Install-WindowsFeature "FS-DFS-Namespace", "RSAT-DFS-Mgmt-Con"
```

---

## Interoperability with Azure virtual machines

Using DFS Namespaces on a virtual machine in Microsoft Azure has been tested.

- You can host domain-based namespaces in Azure virtual machines, including environments with Microsoft Entra ID.
- You can cluster stand-alone namespaces in Azure virtual machines using failover clusters that use [Shared Disk](/en-us/azure/virtual-machines/disks-shared) or [Ultra Disks](/en-us/azure/virtual-machines/disks-enable-ultra-ssd).

To learn about how to get started with Azure virtual machines, see [Azure virtual machines documentation](/en-us/azure/virtual-machines/).