---
layout: Conceptual
title: Scale out your RDS deployment by adding an RD Session Host farm | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-desktop-services/rds-scale-rdsh-farm
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote-desktop-services
ms.update-cycle: 1095-days
description: Add a second RD Session Host to your RDS environment.
ms.author: roharwoo
ms.date: 2024-07-03T00:00:00.0000000Z
ms.topic: how-to
author: robinharwood
locale: en-us
document_id: 967d766e-6d2e-7f4d-dc25-3b77ebc5073f
document_version_independent_id: 967d766e-6d2e-7f4d-dc25-3b77ebc5073f
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-desktop-services/rds-scale-rdsh-farm.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-desktop-services/rds-scale-rdsh-farm
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-desktop-services/rds-scale-rdsh-farm.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ddab3cd8-636f-4a91-896e-1c23f399a6bd
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f409bb5d-e203-40c5-9d95-0ee717231beb
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: cf3e64c2-aadd-42a9-52b6-789f4a96c967
---

# Scale out your RDS deployment by adding an RD Session Host farm | Microsoft Learn

You can improve the availability and scale of your RDS deployment by adding a Remote Desktop Session Host (RDSH) farm.

Use the following steps to add another RD Session Host to your deployment:

1. Create a server to host the second RD Session Host. If you are using Azure virtual machines, make sure to include the new VM in the same availability set that holds your first RD Session Host.
2. Enable remote management on the new server or virtual machine:

    1. In Server Manager, click **Local Server &gt; Remote management current setting (disabled)**.
    2. Select **Enable remote management for this server**, and then click **OK**.
    3. Optional: You can temporarily set Windows Update to not automatically download and install updates. This helps prevent changes and system restarts while you deploy the RDSH server. In Server Manager, click **Local Server &gt; Windows Update current setting**. Click **Advanced options &gt; Defer upgrades**.
3. Add the server or VM to the domain:

    1. In Server Manager, click **Local Server &gt; Workgroup current setting**.
    2. Click **Change &gt; Domain**, and then enter the domain name (for example, Contoso.com).
    3. Enter the domain administrator credentials.
    4. Restart the server or VM.
4. Add the new RD Session Host to the farm:

    Note

    Step 1, creating a public IP address for the RDMS virtual machine, is only necessary if you are using a VM for the RDMS and if it does not already have an IP address assigned.

    1. Create a public IP address for the virtual machine running Remote Desktop Management Services (RDMS). The RDMS virtual machine will typically be the virtual machine running the first instance of the RD Connection Broker role.
        1. In the Azure portal, click **Browse &gt; Resource groups**, click the resource group for the deployment and then click the RDMS virtual machine (for example, Contoso-Cb1).
        2. Click **Settings &gt; Network interfaces**, and then click the corresponding network interface.
        3. Click **Settings &gt; IP address**.
        4. For **Public IP address**, select **Enabled**, and then click **IP address**.
        5. If you have an existing public IP address you want to use, select it from the list. Otherwise, click **Create new**, enter a name, and then click **OK** and then **Save**.
    2. Sign into the RDMS.
    3. Add the new RDSH server to Server Manager:
        1. Launch Server Manager, click **Manage &gt; Add Servers**.
        2. In the Add Servers dialog, click **Find Now**.
        3. Select the server you want to use for the RD Session Host or the newly created virtual machine (for example, Contoso-Sh2) and click **OK**.
    4. Add the RDSH server to the deployment
        1. Launch Server Manager.
        2. Click **Remote Desktop Services &gt; Overview &gt; Deployment Servers &gt; Tasks &gt; Add RD Session Host Servers**.
        3. Select the new server (for example, Contoso-Sh2), and then click **Next**.
        4. On the Confirmation page, select **Restart remote computers as needed**, and then click **Add**.
    5. Add RDSH server to the collection farm:
        1. Launch Server Manager.
        2. Click **Remote Desktop Services** and then click the collection to which you want to add the newly created RDSH server (for example, ContosoDesktop).
        3. Under **Host Servers**, click **Tasks &gt; Add RD Session Host Servers**.
        4. Select the newly created server (for example, Contoso-Sh2), and then click **Next**.
        5. On the Confirmation page, click **Add**.