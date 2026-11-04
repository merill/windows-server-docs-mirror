---
layout: Conceptual
title: Prepare your virtual machines for Remote Desktop | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-desktop-services/rds-prepare-vms
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote-desktop-services
ms.update-cycle: 1095-days
description: Get your VMs ready for Remote Desktop components
ms.author: roharwoo
ms.date: 2024-07-03T00:00:00.0000000Z
ms.topic: how-to
author: robinharwood
locale: en-us
document_id: 3a666d34-ab94-d1cf-1f1b-66b838b97537
document_version_independent_id: a00d3b55-bb1d-f997-4ec2-27a0fd96278b
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-desktop-services/rds-prepare-vms.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-desktop-services/rds-prepare-vms
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-desktop-services/rds-prepare-vms.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ddab3cd8-636f-4a91-896e-1c23f399a6bd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f409bb5d-e203-40c5-9d95-0ee717231beb
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 336ba029-e688-7835-532c-d8531cefd2a9
---

# Prepare your virtual machines for Remote Desktop | Microsoft Learn

You can install Remote Desktop Services components on physical servers or on virtual machines.

The first step is to [create Windows Server virtual machines in Azure](/en-us/azure/virtual-machines/windows/quick-create-portal). You'll want to create three VMs: one for the RD Session Host, one for the Connection Broker, and one for the RD Web and RD Gateway. To ensure the availability of your RDS deployment, create an availability set (under **High availablility** in the VM creation process) and group multiple VMs in that availability set.

After you create your VMs, use the following steps to prepare them for RDS.

1. Connect to the virtual machine using the Remote Desktop Connection (RDC) client:
    1. In the Azure portal open the Resource groups view, and then click the resource group to use for the deployment.
    2. Select the new RDSH virtual machine (for example, Contoso-Sh1).
    3. Click **Connect &gt; Open** to open the Remote Desktop client.
    4. In the client, click **Connect**, and then click **Use another user account**. Enter the user name and password for the local administrator account.
    5. Click **Yes** when warned about the certificate.
2. Enable remote management:
    1. In Server Manager, click **Local Server &gt; Remote management current setting (disabled)**.
    2. Select **Enable remote management for this server**.
    3. Click **OK**.
3. Optional: You can temporarily set Windows Update to not automatically download and install updates. This helps prevent changes and system restarts while you deploy the RDSH server.
    1. In Server Manager, click **Local Server &gt; Windows Update current setting**.
    2. Select **Advanced options &gt; Defer upgrades**.
4. Add the server to the domain:
    1. In Server Manager, click **Local Server &gt; Workgroup current setting**.
    2. Click **Change &gt; Domain**, and then enter the domain name (for example, Contoso.com).
    3. Enter the domain administrator credentials.
    4. Restart the virtual machine.
5. Repeat steps 1 through 4 for the RD Web and GW virtual machine.
6. Repeat steps 1 through 4 for the RD Connection Broker virtual machine.
7. Initialize and format the attached disk on the RD Connection Broker virtual machine:
    1. Connect to the RD Connection Broker virtual machine (step 1 above).
    2. In Server Manager, click **Tools &gt; Computer Management**.
    3. Click **Disk Management**.
    4. Select the attached disk, then **MBR (Master Boot Record)**, and then click **OK**.
    5. Right-click the new disk (marked as **Unallocated**) and click **New Simple Volume**.
    6. In the **New Simple Volume** wizard, accept the default values but provide a applicable name for the **Volume label** (like Shares).
8. On the RD Connection Broker virtual machine create file shares for the user profile disks and certificates:
    1. Open File Explorer, click **This PC**, and open the disk that you added for file shares.
    2. Click **Home** and **New Folder**.
    3. Enter a name for the user disks folder, for example, **UserDisks**.
    4. Right-click the new folder and click **Properties &gt; Sharing &gt; Advanced Sharing**.
    5. Select **Share this folder** and click **Permissions**.
    6. Select **Everyone**, and then click **Remove**. Now click **Add**, enter **Domain Admins**, and click **OK**.
    7. Select **Allow Full Control**, and then click **OK &gt; OK &gt; Close**.
    8. Repeat steps c. to g. to create a shared folder for certificates.