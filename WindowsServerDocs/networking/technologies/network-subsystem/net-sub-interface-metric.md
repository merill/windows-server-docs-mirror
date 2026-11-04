---
layout: Conceptual
title: Configure the Order of Network Interfaces | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/technologies/network-subsystem/net-sub-interface-metric
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Learn how to use the interface metric to configure the order of network interfaces.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2021-10-27T00:00:00.0000000Z
locale: en-us
document_id: 2198b2a6-6d6f-c4ee-4904-f63701b02a58
document_version_independent_id: 740087d9-5ee2-a930-61ef-2510376f5cbb
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/technologies/network-subsystem/net-sub-interface-metric.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/technologies/network-subsystem/net-sub-interface-metric
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/technologies/network-subsystem/net-sub-interface-metric.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/e0ffb20c-01c6-407b-a9bd-29111652a1dc
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/3904bce4-d817-48cf-85fd-b6146fca83b7
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: ee9321bb-def5-9dd1-5fd8-c9f975f8db67
---

# Configure the Order of Network Interfaces | Microsoft Learn

In Windows Server 2016 and Windows 10, you can use the interface metric to configure the order of network interfaces.

This is different than in previous versions of Windows and Windows Server, which allowed you to configure the binding order of network adapters by using either the user interface or the commands **INetCfgComponentBindings::MoveBefore** and **INetCfgComponentBindings::MoveAfter**. These two methods for ordering network interfaces are not available in Windows Server 2016 and Windows 10.

Instead, you can use the new method for setting the enumerated order of network adapters by configuring the interface metric of each adapter. You can configure the interface metric by using the [Set-NetIPInterface](/en-us/powershell/module/nettcpip/set-netipinterface) Windows PowerShell command.

When network traffic routes are chosen and you have configured the **InterfaceMetric** parameter of the **Set-NetIPInterface** command, the overall metric that is used to determine the interface preference is the sum of the route metric and the interface metric. Typically, the interface metric gives preference to a particular interface, such as using wired if both wired and wireless are available.

The following Windows PowerShell command example shows use of this parameter.

```powershell
Set-NetIPInterface -InterfaceIndex 12 -InterfaceMetric 15
```

The order in which adapters appear in a list is determined by the IPv4 or IPv6 interface metric. For more information, see [GetAdaptersAddresses function](/en-us/windows/win32/api/iphlpapi/nf-iphlpapi-getadaptersaddresses?f=255&amp;MSPPError=-2147217396).

For links to all topics in this guide, see [Network Subsystem Performance Tuning](net-sub-performance-top).