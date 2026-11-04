---
layout: Conceptual
title: wdsutil get-multicasttransmission | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wdsutil-get-multicasttransmission
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for wdsutil get-multicasttransmission, which displays information about the multicast transmission for a specified image.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 65b8fd40-49d7-fca7-ae19-4fbd11b00449
document_version_independent_id: 7e82a585-4900-05fd-55d0-ae1f729b3d7b
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wdsutil-get-multicasttransmission.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wdsutil-get-multicasttransmission
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wdsutil-get-multicasttransmission.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: c9649ea1-b3ba-01ca-83c9-54f67f7a96fe
---

# wdsutil get-multicasttransmission | Microsoft Learn

Displays information about the multicast transmission for a specified image.

## Syntax

**Windows Server 2008**

```
wdsutil [Options] /Get-MulticastTransmissiomedia:<Image name> [/Server:<Server name>mediatype:InstallmediaGroup:<Image group name>]
[/Filename:<File name>] [/Show:Clients]
```

**Windows Server 2008 R2**

for boot image transmissions:

```
wdsutil [Options] /Get-MulticastTransmissiomedia:<Image name>
    [/Server:<Server name>]
    [/details:Clients]
  mediatype:Boot
    /Architecture:{x86 | ia64 | x64}
        [/Filename:<File name>]
```

for install image transmissions:

```
wdsutil [Options] /Get-MulticastTransmissiomedia:<Image name>
         [/Server:<Server name>]
         [/details:Clients]
       mediatype:Install
    mediaGroup:<Image Group>]
     [/Filename:<File name>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| media:&lt;Image name&gt; | Displays the multicast transmission that is associated with this image. |
| [/Server:&lt;Server name&gt;] | Specifies the name of the server. This can be the NetBIOS name or the fully qualified domain name (FQDN). If no server name is specified, the local server is used. |
| /imagetype:Install | Specifies the image type. Note that this option must be set to **Install**. |
| /imagegroup:&lt;Image group name&gt;] | Specifies the image group that contains the image. If no image group name is specified and only one image group exists on the server, that image group is used. If more than one image group exists on the server, you must use this option to specify an image group. |
| /Architecture:{x86 | ia64 | x64} | Specifies the architecture of the boot image that is associated with the transmission. Because it is possible to have the same image name for boot images in different architectures, you should specify the architecture to ensure that the correct image is used. |
| [/Filename:&lt;File name&gt;] | Specifies the file that contains the image. If the image cannot be uniquely identified by name, you must use this option to specify the file name. |
| [/Show:Clients]<br>or<br><br>[/details:Clients] | Displays information about client computers that are connected to the multicast transmission. |

## Examples

**Windows Server 2008**

To view information about the transmission for an image named Vista with Office, type one of the following:

```
wdsutil /Get-MulticastTransmission:Vista with Office imagetype:Install
wdsutil /Get-MulticastTransmission /Server:MyWDSServer image:Vista with Office imagetype:Install imageGroup:ImageGroup1 /Filename:install.wim /Show:Clients
```

**Windows Server 2008 R2**

To view information about the transmission for an image named Vista with Office, type one of the following:

```
wdsutil /Get-MulticastTransmission:Vista with Office
 /Imagetype:Install
```

```
wdsutil /Get-MulticastTransmission /Server:MyWDSServer image:Vista with Office imagetype:Install ImageGroup:ImageGroup1 /Filename:install.wim /details:Clients
```

```
wdsutil /Get-MulticastTransmission /Server:MyWDSServer:X64 Boot Imagetype:Boot /Architecture:x64 /Filename:boot.wim /details:Clients
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [wdsutil get-allmulticasttransmissions command](wdsutil-get-allmulticasttransmissions)
- [wdsutil new-multicasttransmission command](wdsutil-new-multicasttransmission)
- [wdsutil remove-multicasttransmission command](wdsutil-remove-multicasttransmission)
- [wdsutil start-multicasttransmission command](wdsutil-start-multicasttransmission)