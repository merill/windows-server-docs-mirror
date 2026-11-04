---
layout: Conceptual
title: wdsutil new-multicasttransmission | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wdsutil-new-multicasttransmission
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for wdsutil new-multicasttransmission, which creates a new multicast transmission for an image.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 6d0c4673-403d-22bf-920b-edbe56cc06bc
document_version_independent_id: a9fed557-d44b-4d2f-209c-d6fe39a26c1c
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wdsutil-new-multicasttransmission.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wdsutil-new-multicasttransmission
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wdsutil-new-multicasttransmission.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 36f13c35-12df-3e80-689e-d69ec101addf
---

# wdsutil new-multicasttransmission | Microsoft Learn

Creates a new multicast transmission for an image. This command is equivalent to creating a transmission by using the Windows Deployment Services mmc snap-in (right-click the **Multicast Transmissions** node, and then click **create Multicast Transmission**). You should use this command when you have both the Deployment Server role service and the Transport Server role service installed (which is the default installation). If you have only the Transport Server role service installed, use [wdsutilnew-Namespace command](wdsutil-new-namespace).

## Syntax

For install images transmissions:

```
wdsutil [Options] /New-MulticastTransmissiomedia:<Image name>
        [/Server:<Server name>]
        /FriendlyName:<Friendly name>
        [/Description:<Description>]
        /Transmissiontype: {AutoCast | ScheduledCast}
            [/time:<YYYY/MM/DD:hh:mm>]
            [/Clients:<Num of Clients>]
      imagetype:Install
       ImageGroup:<Image Group>]
        [/Filename:<File name>]
```

For boot image transmissions (only supported for Windows Server 2008 R2):

```
wdsutil [Options] /New-MulticastTransmissiomedia:<Image name>
        [/Server:<Server name>]
        /FriendlyName:<Friendly name>
        [/Description:<Description>]
        /Transmissiontype: {AutoCast | ScheduledCast}
            [/time:<YYYY/MM/DD:hh:mm>]
            [/Clients:<Num of Clients>]
      imagetype:Boot
        /Architecture:{x86 | ia64 | x64}
        [/Filename:<File name>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /image:&lt;Image name&gt; | Specifies the name of the image to be transmitted using multicasting. |
| [/Server:&lt;Server name&gt;] | Specifies the name of the server. This can be the NetBIOS name or the fully qualified domain name (FQDN). If no server name is specified, the local server will be used. |
| /FriendlyName:&lt;Friendly name&gt; | Specifies the friendly name of the transmission. |
| [/Description:&lt;Description&gt;] | Specifies the description of the transmission. |
| /imagetype:{Boot|Install} | Specifies the type of image to be transmitted using multicasting. Note **Boot** is only supported for Windows Server 2008 R2. |
| /ImageGroup:&lt;Image group name&gt;] | Specifies the image group that contains the image. If no image group name is specified and only one image group exists on the server, that image group is used. If more than one image group exists on the server, you must use this option to specify the image group name. |
| [/Filename:&lt;File name&gt;] | Specifies the file name. If the source image cannot be uniquely identified by name, you must use this option to specify the file name. |
| /Transmissiontype:{AutoCast | ScheduledCast} | Specifies whether to start the transmission automatically (AutoCast) or based on the specified start criteria (ScheduledCast).<br>- **Auto-Cast**. This transmission type indicates that as soon as an applicable client requests an install image, a multicast transmission of the selected image begins. As other clients request the same image, they are joined to the transmission that is already started.<br>- **Scheduled-Cast**. This transmission type sets the start criteria for the transmission based on the number of clients that are requesting an image and/or a specific day and time. You can specify the following options:<br>    - [/time: &lt;time&gt;] - Sets the time that the transmission should start by using the following format: YYYY/MM/DD:hh:mm.<br>    - [/Clients: &lt;Number of clients&gt;] - Sets the minimum number of clients to wait for before the transmission starts. |
| /Architecture:{x86 | ia64 | x64} | Specifies the architecture of the boot image to transmit using multicasting. Because it is possible to have the same name for boot images of different architectures, you should specify the architecture to ensure the correct image is used. |
| [/Filename:&lt;File name&gt;] | Specifies the file name. If the source image cannot be uniquely identified by name, you must specify the file name. |

## Examples

To create an Auto-Cast transmission of a boot image in Windows Server 2008 R2, type:

```
wdsutil /New-MulticastTransmission /FriendlyName:WDS Boot Transmission
/Image:X64 Boot imagetype:Boot /Architecture:x64 /Transmissiontype:AutoCast
```

To create an Auto-Cast transmission of an install image, type:

```
wdsutil /New-MulticastTransmission /FriendlyName:WDS AutoCast Transmission
/Image:Vista with Officeimage imagetype:Install /Transmissiontype:AutoCast
```

To create a Scheduled-Cast transmission of an install image, type:

```
wdsutil /New-MulticastTransmission /FriendlyName:WDS SchedCast Transmission /Server:MyWDSServer Image:Vista with Office imagetype:Install
/Transmissiontype:ScheduledCast /time:2006/11/20:17:00 /Clients:100
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [wdsutil get-allmulticasttransmissions command](wdsutil-get-allmulticasttransmissions)
- [wdsutil get-multicasttransmission command](wdsutil-get-multicasttransmission)
- [wdsutil remove-multicasttransmission command](wdsutil-remove-multicasttransmission)
- [wdsutil start-multicasttransmission command](wdsutil-start-multicasttransmission)