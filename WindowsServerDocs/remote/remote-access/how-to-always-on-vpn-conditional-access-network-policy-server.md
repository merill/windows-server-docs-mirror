---
layout: Conceptual
title: Configure VPN conditional access on the Network Policy Server (NPS) on Windows Server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-access/how-to-always-on-vpn-conditional-access-network-policy-server
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote
ms.update-cycle: 1095-days
description: Learn how to configure VPN conditional access on the Network Policy Server (NPS)
ms.topic: how-to
ms.date: 2023-05-04T00:00:00.0000000Z
ms.author: roharwoo
author: robinharwood
locale: en-us
document_id: 03e58306-6b81-9947-a81d-4d3928bab7dd
document_version_independent_id: 03e58306-6b81-9947-a81d-4d3928bab7dd
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-access/how-to-always-on-vpn-conditional-access-network-policy-server.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-access/how-to-always-on-vpn-conditional-access-network-policy-server
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-access/how-to-always-on-vpn-conditional-access-network-policy-server.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
platformId: f53b2d21-dd4a-cf11-3f6c-cfe10f9ec4b1
---

# Configure VPN conditional access on the Network Policy Server (NPS) on Windows Server | Microsoft Learn

Conditional access and device compliance can require that managed devices meet standards before they can connect to the VPN. VPN conditional access allows you to restrict the VPN connections to devices whose client authentication certificate contains the Microsoft Entra Conditional Access OID of **1.3.6.1.4.1.311.87**. VPN clients that try to connect by using a certificate other than the short-lived **1.3.6.1.4.1.311.87** cloud certificate will fail to connect.

This article shows you how to configure VPN conditional access directly on the NPS server. To learn how to restrict the VPN connections with Microsoft Entra Conditional Access, see [Conditional access for VPN connectivity using Microsoft Entra ID](how-to-aovpn-conditional-access).

## Restrict the VPN connections

To restrict VPN connections:

1. On the NPS server, open the **Network Policy Server** snap-in.
2. Expand **Policies** &gt; **Network Policies**. Right-click the **Virtual Private Network (VPN) Connections** Network Policy and then select **Properties**
3. Select the **Settings** tab.
4. Select **Vendor Specific**, and then select **Add**.
5. Select the **Allowed-Certificate-OID** option, and then select **Add**.
6. Paste the Microsoft Entra Conditional Access OID of **1.3.6.1.4.1.311.87** as the attribute value, and then select **OK**.
7. Select **OK** again.
8. Select **Close**, and then select **Apply**.

VPN clients that try to connect by using certificate other than the short-lived **1.3.6.1.4.1.311.87** cloud certificate will now fail to connect.