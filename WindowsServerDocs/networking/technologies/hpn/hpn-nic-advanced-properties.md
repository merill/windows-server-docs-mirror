---
layout: Conceptual
title: NIC advanced properties | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/technologies/hpn/hpn-nic-advanced-properties
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: You can manage NICs and all the features via Windows PowerShell or the Network Control Panel.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2021-10-26T00:00:00.0000000Z
locale: en-us
document_id: 1c413342-d217-523a-e425-9c7e6e5da850
document_version_independent_id: 46894097-547f-35c2-f693-3363fa3d1474
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/technologies/hpn/hpn-nic-advanced-properties.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/technologies/hpn/hpn-nic-advanced-properties
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/technologies/hpn/hpn-nic-advanced-properties.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 07f78374-ca6e-65e3-6214-f1de290a48c7
---

# NIC advanced properties | Microsoft Learn

You can manage NICs and all the features via Windows PowerShell using the [NetAdapter](/en-us/powershell/module/netadapter/) cmdlet. You can also manage NICs and all the features using Network Control Panel (ncpa.cpl). To learn more, see [Host network requirements for Azure Local](/en-us/azure/azure-local/concepts/host-network-requirements?context=/windows-server/context/windows-server-edge-networking).

1. In **Windows PowerShell**, run the `Get‑NetAdapterAdvancedProperty` cmdlet against two different make/model of NICs.

    ![Get-NetAdapterAdvancedProperty m1](../../media/network-offload-and-optimization/get-netadapteradvancedproperty-m1.png)

    ![Get-NetAdapterAdvancedProperty c1](../../media/network-offload-and-optimization/get-netadapteradvancedproperty-c1.png)

    There are similarities and differences in these two NIC Advanced Properties Lists.
2. In the **Network Control Panel** (ncpa.cpl), do the following:

    a. Right-click the NIC.

    ![Network connections dialog](../../media/network-offload-and-optimization/network-connections-dialog.png)

    b. In the properties dialog, click **Configure**.

    ![C1 Properties](../../media/network-offload-and-optimization/c1-properties.png)

    c. Click the **Advanced** tab to view the advanced properties.

    The items in this list correlates to the items in the `Get-NetAdapterAdvancedProperties` output.

    ![Chelsio Network Adapter Properties](../../media/network-offload-and-optimization/chelsio-network-adapter-properties.png)