---
layout: Conceptual
title: wdsutil get-allmulticasttransmissions | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wdsutil-get-allmulticasttransmissions
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for wdsutil get-allmulticasttransmissions, which displays information about all multicast transmissions on a server.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 9f4140b5-401c-8e2c-0b21-012d808b6a65
document_version_independent_id: fb17b335-ce95-711a-74a4-7d8557f026e3
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wdsutil-get-allmulticasttransmissions.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wdsutil-get-allmulticasttransmissions
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wdsutil-get-allmulticasttransmissions.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 552d9041-588f-66fb-d971-c975e1189ba4
---

# wdsutil get-allmulticasttransmissions | Microsoft Learn

Displays information about all multicast transmissions on a server.

## Syntax

For Windows Server 2008:

```
wdsutil /Get-AllMulticastTransmissions [/Server:<Server name>] [/Show:Clients] [/ExcludedeletePending]
```

For Windows Server 2008 R2:

```
wdsutil /Get-AllMulticastTransmissions [/Server:<Server name>] [/Show:{Boot | Install | All}] [/details:Clients]  [/ExcludedeletePending]
```

### Parameters

| Parameter | Explanation |
| --- | --- |
| [/Server:&lt;Server name&gt;] | Specifies the name of the server. This can be either the NetBIOS name or the fully qualified domain name (FQDN). If no server name is specified, the local server will be used. |
| [/Show] | **Windows Server 2008**<br>/Show:Clients - Displays information about client computers that are connected to the multicast transmissions.<br><br>**Windows Server 2008 R2**<br><br>Show: {Boot | Install | All} - The type of image to return. **Boot** returns only boot image transmissions. **Install** returns only install image transmissions. **All** returns both image types. |
|  |  |
| /details:clients | Only supported for Windows Server 2008 R2. If present, clients that are connected to the transmission will be displayed. |
| [/ExcludedeletePending] | Excludes any deactivated transmissions from the list. |

## Examples

To view information about all transmissions, type:

- Windows Server 2008: `wdsutil /Get-AllMulticastTransmissions`
- Windows Server 2008 R2: `wdsutil /Get-AllMulticastTransmissions /Show:All` To view information about all transmissions except deactivated transmissions, type:
- Windows Server 2008: `wdsutil /Get-AllMulticastTransmissions /Server:MyWDSServer /Show:Clients /ExcludedeletePending`
- Windows Server 2008 R2: `wdsutil /Get-AllMulticastTransmissions /Server:MyWDSServer /Show:All /details:Clients /ExcludedeletePending`

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [wdsutil get-multicasttransmission command](wdsutil-get-multicasttransmission)
- [wdsutil new-multicasttransmission command](wdsutil-new-multicasttransmission)
- [wdsutil remove-multicasttransmission command](wdsutil-remove-multicasttransmission)
- [wdsutil start-multicasttransmission command](wdsutil-start-multicasttransmission)