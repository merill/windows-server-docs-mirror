---
layout: Conceptual
title: wdsutil remove-multicasttransmission | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wdsutil-remove-multicasttransmission
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for wdsutil remove-multicasttransmission, which disables multicast transmitting for an image.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 73c372f8-0412-ffe0-874e-106c6aacada5
document_version_independent_id: 3799a7b8-e1c2-526d-885b-f5e527a22ea2
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wdsutil-remove-multicasttransmission.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wdsutil-remove-multicasttransmission
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wdsutil-remove-multicasttransmission.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 67a133cb-0e7f-496a-ea63-33ab3818eae2
---

# wdsutil remove-multicasttransmission | Microsoft Learn

Disables multicast transmitting for an image. Unless you specify **/force**, existing clients will complete the image transfer but new clients will not be allowed to join.

## Syntax

**Windows Server 2008**

```
wdsutil /remove-MulticastTransmission:<Image name> [/Server:<Server name> mediatype:Install Group:<Image Group>] [/Filename:<File name>] [/force]
```

**Windows Server 2008 R2** for boot images:

```
wdsutil [Options] /remove-MulticastTransmissiomedia:<Image name>
\x20    [/Server:<Server name>]
\x20  mediatype:Boot
\x20    /Architecture:{x86 | ia64 | x64}
\x20    [/Filename:<File name>]
```

for install images:

```
wdsutil [Options] /remove-MulticastTransmissiomedia:<Image name>
        [/Server:<Server name>]
      mediatype:Install
       mediaGroup:<Image Group
        [/Filename:<File name>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| media:&lt;Image name&gt; | Specifies the name of the image. |
| [/Server:&lt;Server name&gt;] | Specifies the name of the server. This can be the NetBIOS name or the fully qualified domain name (FQDN). If no server name is specified, the local server is used. |
| mediatype:{Install|Boot} | Specifies the image type. Note that this option must be set to **Install** for Windows Server 2008. |
| /Architecture:{x86 | ia64 | x64} | Specifies the architecture of the boot image that is associated with the transmission to start. Because it is possible to have the same image name for boot images in different architectures, you should specify the architecture to ensure that the correct transmission is used. |
| \mediaGroup:&lt;Image group name&gt;] | Specifies the image group that contains the image. If no image group name is specified and only one image group exists on the server, that image group is used. If more than one image group exists on the server, you must use this option to specify the image group name. |
| [/Filename:&lt;File name&gt;] | Specifies the file name. If the source image cannot be uniquely identified by name, you must use this option to specify the file name. |
| [/force] | removes the transmission and terminates all clients. Unless you specify a value for the **/force** option, existing clients can complete the image transfer but new clients are not able to join. |

## Examples

To stop a namespace (current clients will complete the transmission, but new clients will not be able to join), type:

```
wdsutil /remove-MulticastTransmission:Vista with Office
/Imagetype:Install
```

```
wdsutil /remove-MulticastTransmission:x64 Boot Image
/Imagetype:Boot /Architecture:x64
```

To force termination of all clients, type:

```
wdsutil /remove-MulticastTransmission /Server:MyWDSServer
/Image:Vista with Officemediatype:InstalmediaGroup:ImageGroup1
/Filename:install.wim /force
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [wdsutil get-allmulticasttransmissions command](wdsutil-get-allmulticasttransmissions)
- [wdsutil get-multicasttransmission command](wdsutil-get-multicasttransmission)
- [wdsutil new-multicasttransmission command](wdsutil-new-multicasttransmission)
- [wdsutil start-multicasttransmission command](wdsutil-start-multicasttransmission)