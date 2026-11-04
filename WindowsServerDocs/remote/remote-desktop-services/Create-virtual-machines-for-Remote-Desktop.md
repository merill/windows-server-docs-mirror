---
layout: Conceptual
title: Create virtual machines for Remote Desktop | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-desktop-services/create-virtual-machines-for-remote-desktop
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote-desktop-services
ms.update-cycle: 1095-days
description: Create VMs to host Remote Desktop components in the cloud.
ms.author: roharwoo
ms.date: 2024-07-03T00:00:00.0000000Z
ms.topic: how-to
author: robinharwood
locale: en-us
document_id: 936d7a6f-a9f9-1e6d-2410-6f3acbcaceb7
document_version_independent_id: 3004c4c5-139f-1771-af9d-a8f848598e55
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-desktop-services/Create-virtual-machines-for-Remote-Desktop.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-desktop-services/create-virtual-machines-for-remote-desktop
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-desktop-services/Create-virtual-machines-for-Remote-Desktop.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ddab3cd8-636f-4a91-896e-1c23f399a6bd
- https://authoring-docs-microsoft.poolparty.biz/devrel/68ec7f3a-2bc6-459f-b959-19beb729907d
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f409bb5d-e203-40c5-9d95-0ee717231beb
- https://authoring-docs-microsoft.poolparty.biz/devrel/90370425-aca4-4a39-9533-d52e5e002a5d
platformId: 053af588-64a5-cd20-ad11-08774753db9a
---

# Create virtual machines for Remote Desktop | Microsoft Learn

Use the following steps to create the virtual machines in the tenant's environment that will be used to run the Windows Server 2016 roles, services, and features required for a desktop hosting deployment.

For this example of a basic deployment, the minimum of 3 virtual machines will be created. One virtual machine will host the Remote Desktop (RD) Connection Broker and License Server role services and a file share for the deployment. A second virtual machine will host the RD Gateway and Web Access role services. A third virtual machine host the RD Session Host role service. For very small deployments, you can reduce VM costs by using Microsoft Entra App Proxy to eliminate all public endpoints from the deployment and combining all the role services onto a single VM. For larger deployments, you can install the various role services on individual virtual machines to allow better scaling.

This section outlines the steps necessary to deploy virtual machines for each role based on Windows Server images in the [Microsoft Azure Marketplace](https://azure.microsoft.com/marketplace/). If you need to create virtual machines from a custom image, which requires PowerShell, check out [Create a Windows VM with Resource Manager and PowerShell](/en-us/azure/virtual-machines/windows/quick-create-powershell). Then return here to attach Azure data disks for the file share and enter an external URL for your deployment.

1. [Create Windows virtual machines](/en-us/azure/virtual-machines/windows/quick-create-portal) to host the RD Connection Broker, RD License Server, and File server.

    For our purpose, we used the following naming conventions:

    - RD Connection Broker, License Server, and File Server:

        - VM: Contoso-Cb1
        - Availability set: CbAvSet
    - RD Web Access and RD Gateway Server:

        - VM: Contoso-WebGw1
        - Availability set: WebGwAvSet
    - RD Session Host:

        - VM: Contoso-Sh1
        - Availability set: ShAvSet

    Each VM uses the same resource group.
2. Create and attach an Azure data disk for the user profile disk (UPD) share:

    1. In the Azure portal click **Browse &gt; Resource groups**, click the resource group for the deployment, and then click the VM created for the RD Connection Broker (for example, Contoso-Cb1).
    2. Click **Settings &gt; Disks &gt; Attach new**.
    3. Accept the defaults for name and type.
    4. Enter a size (in GB) that is large enough to hold network shares for the tenant's environment, including user profile disks and certificates. You can approximate 5 GB per user you plan to have
    5. Accept the defaults for location and host caching, and then click **OK**.
3. Create an external load balancer to access the deployment externally:

    1. In the Azure portal click **Browse &gt; Load balancers**, and then click **Add**.
    2. Enter a **Name**, select **Public** as the **Type** of load balancer, and select the appropriate **Subscription**, **Resource Group**, and **Location**.
    3. Select **Choose a public IP address**, **Create new**, enter a name, and select **Ok**.
    4. Select **Create** to create the load balancer.
4. Configure the external load balancer for your deployment

    1. In the Azure portal click **Browse &gt; Resource groups**, click the resource group for the deployment, and then click the load balancer you created for the deployment.
    2. Add a backend pool for the load balancer to send traffic to:
        1. Select **Backend pool** and **Add**.
        2. Enter a **Name** and select **+ Add a virtual machine**.
        3. Select **Availability set** and **WebGwAvSet**.
        4. Select **Virtual machines**, **Contoso-WebGw1**, **Select**, **OK**, and **OK**.
    3. Add a probe so the load balancer knows what machines are active:
        1. Select **Probes** and **Add**.
        2. Enter a **Name** (like HTTPS), select **TCP**, enter **Port** 443, and select **OK**.
    4. Enter load balancing rules to balance the incoming traffic:
        1. Select **Load balancing rules** and **Add**
        2. Enter a **Name** (like HTTPS), select **TCP**, and 443 for both the **Port** and the **Backend port**.
            - For a Windows 10 and Windows Server 2016 Deployment, leave **Session persistence** as **None**, otherwise select **Client IP**.
        3. Select **OK** to accept the HTTPS rule.
        4. Create a new rule by selecting **Add**.
        5. Enter a **Name** (like UDP), select **UDP**, and 3391 for both the **port and the \*\*Backend port**.
            - For a Windows 10 and Windows Server 2016 deployment, leave **Session persistence** as **None**, otherwise select **Client IP**.
        6. Select **OK** to accept the UDP rule.
    5. Enter an inbound NAT rule to directly connect to Contoso-WebGw1
        1. Select **Inbound NAT rules** and **Add**.
        2. Enter a **Name** (like RDP-Contoso-WebGw1), select **Customm** for the service, **TCP** for the protocol, and enter 14000 for the **Port**.
        3. Select **Choose a virtual machine** and Contoso-WebGw1.
        4. Select **Custom** for the port mapping, enter 3389 for the **Target port**, and select **OK**.
5. Enter an external URL/DNS name for your deployment to access it externally:

    1. In the Azure portal, click **Browse &gt; Resource groups**, click the resource group for the deployment, and then click the public IP address you created for RD Web Access and RD Gateway.
    2. Click **Configuration**, enter a DNS name label (like contoso), and then click **Save**. This DNS name label (contoso.westus.cloudapp.azure.com) is the DNS name that you'll use to connect to your RD Web Access and RD Gateway server.