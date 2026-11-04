---
layout: Conceptual
title: wdsutil get-device | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wdsutil-get-device
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for wdsutil get-device, which retrieves Windows Deployment Services information about a prestaged computer (that is, a physical computer that has been lined to a computer account in active directory Domain Services.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 65eeff41-a122-065d-9dfa-b4da8a66cc56
document_version_independent_id: e1aefdc6-1174-65c9-308f-3694027c3a9d
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wdsutil-get-device.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wdsutil-get-device
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wdsutil-get-device.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: 64c5e833-662d-c1bd-8faf-941b42fb09b7
---

# wdsutil get-device | Microsoft Learn

Retrieves Windows Deployment Services information about a prestaged computer (that is, a physical computer that has been lined to a computer account in active directory Domain Services.

## Syntax

```
wdsutil /Get-Device {/Device:<Device name> | /ID:<MAC or UUID>} [/Domain:<Domain>] [/forest:{Yes | No}]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /Device:&lt;Device name&gt; | Specifies the name of the computer (SAMAccountName). |
| /ID:&lt;MAC or UUID&gt; | Specifies either the MAC address or the UUID (GUID) of the computer, as shown in the following examples. Note that a valid GUID must be in one of two formats binary string or GUID string<br>- **Binary string**: /ID:ACEFA3E81F20694E953EB2DAA1E8B1B6- **MAC address**: 00B056882FDC (no dashes) or 00-B0-56-88-2F-DC (with dashes)- **GUID string**: /ID:E8A3EFAC-201F-4E69-953-B2DAA1E8B1B6 |
| [/Domain:&lt;Domain&gt;] | Specifies the domain to be searched for the prestaged computer. The default value for this parameter is the local domain. |
| [/forest:{Yes | No}] | Specifies whether Windows Deployment Services should search the entire forest or the local domain. The default value is **No**, meaning that only the local domain will be searched. |

## Examples

To get information by using the computer name, type:

```
wdsutil /Get-Device /Device:computer1
```

To get information by using the MAC address, type:

```
wdsutil /verbose /Get-Device /ID:00-B0-56-88-2F-DC /Domain:MyDomain
```

To get information by using the GUID string, type:

```
wdsutil /verbose /Get-Device /ID:E8A3EFAC-201F-4E69-953-B2DAA1E8B1B6 /forest:Yes
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [wdsutil set-device command](wdsutil-set-device)
- [wdsutil add-device command](wdsutil-add-device)
- [wdsutil get-alldevices command](wdsutil-get-alldevices)