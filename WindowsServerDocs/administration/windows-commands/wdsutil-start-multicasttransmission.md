---
layout: Conceptual
title: wdsutil start-multicasttransmission | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wdsutil-start-multicasttransmission
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for Subcommand start-MulticastTransmission, which starts a Scheduled-Cast transmission of an image.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 667a6e69-f942-c8b1-ee9c-dc1216bab4f4
document_version_independent_id: 0210104e-6237-aca4-c383-5fc9a32cfa8a
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wdsutil-start-multicasttransmission.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wdsutil-start-multicasttransmission
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wdsutil-start-multicasttransmission.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c783a8fb-cf36-41ad-90c6-0692a0540484
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: cea0094f-83ec-8ac9-9073-01fa1197bb5b
---

# wdsutil start-multicasttransmission | Microsoft Learn

Starts a Scheduled-Cast transmission of an image.

## Syntax

**Windows Server 2008**

```
wdsutil /start-MulticastTransmissiomedia:<Image name> [/Server:<Server namemediatype:InstallmediaGroup:<Image group name>] [/Filename:<File name>]
```

**Windows Server 2008 R2** for boot images:

```
wdsutil [Options] /start-MulticastTransmissiomedia:<Image name>
        [/Server:<Server name>]
      mediatype:Boot
        /Architecture:{x86 | ia64 | x64}
        [/Filename:<File name>]
```

for install images:

```
wdsutil [Options] /start-MulticastTransmissiomedia:<Image name>
        [/Server:<Server name>]
      mediatype:Install
       mediaGroup:<Image Group>]
        [/Filename:<File name>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| media:&lt;Image name&gt; | Specifies the name of the image. |
| [/Server:&lt;Server name&gt;] | Specifies the name of the server. This can be either the NetBIOS name or the fully qualified domain name (FQDN). If no server name is specified, the local server will be used. |
| mediatype:{Install|Boot} | Specifies the image type. Note that this option must be set to **Install** for Windows Server 2008. |
| /Architecture:{x86 | ia64 | x64} | The architecture of the boot image that is associated with the transmission to start. Since it is possible to have the same image name for boot images in different architectures, you should specify the architecture to ensure that the correct transmission is used. |
| \mediaGroup:&lt;Image group name&gt;] | Specifies the image group of the image. If no image group name is specified and only one image group exists on the server, that image group will be used. If more than one image group exists on the server, you must use this option to specify the image group name. |
| [/Filename:&lt;File name&gt;] | Specifies the name of the file that contains the image. If the image cannot be uniquely identified by name, you must use this option to specify the file name. |

## Examples

To start a multicast transmission, type one of the following:

```
wdsutil /start-MulticastTransmissiomedia:Vista with Office
/Imagetype:Install
wdsutil /start-MulticastTransmission /Server:MyWDSServemedia:Vista with Officemediatype:InstalmediaGroup:ImageGroup1 /Filename:install.wim
```

To start a boot image multicast transmission for Windows Server 2008 R2, type:

```
wdsutil /start-MulticastTransmission /Server:MyWDSServemedia:X64 Boot Imagemediatype:Boot /Architecture:x64
/Filename:boot.wim\n\
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [wdsutil get-allmulticasttransmissions command](wdsutil-get-allmulticasttransmissions)
- [wdsutil get-multicasttransmission command](wdsutil-get-multicasttransmission)
- [wdsutil new-multicasttransmission command](wdsutil-new-multicasttransmission)
- [wdsutil remove-multicasttransmission command](wdsutil-remove-multicasttransmission)