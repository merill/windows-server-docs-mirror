---
layout: Conceptual
title: wdsutil set-image | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wdsutil-set-image
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for wdsutil set-image, which changes the attributes of an image.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 27039b6f-52b5-b738-11ef-f6d5b6380182
document_version_independent_id: 2440a739-38ac-d6a3-30e9-91696664808c
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wdsutil-set-image.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wdsutil-set-image
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wdsutil-set-image.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
platformId: b61542ae-a400-7680-d102-952937391d76
---

# wdsutil set-image | Microsoft Learn

Changes the attributes of an image.

## Syntax

for boot images:

```
wdsutil /Set-Imagmedia:<Image name> [/Server:<Server name>mediatype:Boot /Architecture:{x86 | ia64 | x64} [/Filename:<File name>] [/Name:<Name>]
[/Description:<Description>] [/Enabled:{Yes | No}]
```

for install images:

```
wdsutil /Set-Imagmedia:<Image name> [/Server:<Server name>]
   mediatype:InstallmediaGroup:<Image group name>]
     [/Filename:<File name>]
     [/Name:<Name>]
     [/Description:<Description>]
     [/UserFilter:<SDDL>]
     [/Enabled:{Yes | No}]
     [/UnattendFile:<Unattend file path>]
         [/OverwriteUnattend:{Yes | No}]
```

### Parameters

| Parameter | Description |
| --- | --- |
| media:&lt;Image name&gt; | Specifies the name of the image. |
| [/Server:&lt;Server name&gt;] | Specifies the name of the server. This can be either the NetBIOS name or the fully qualified domain name (FQDN). If no server name is specified, the local server will be used. |
| mediatype:{Boot | Install} | Specifies the type of image. |
| /Architecture:{x86 | ia64 | x64} | Specifies the architecture of the image. Because you can have the same image name for different boot images in different architectures, specifying the architecture ensures that the correct image is modified. |
| [/Filename:&lt;File name&gt;] | if the image cannot be uniquely identified by name, you must use this option to specify the file name. |
| [/Name] | Specifies the name of the image. |
| [/Description:&lt;Description&gt;] | Sets the description of the image. |
| [/Enabled:{Yes | No}] | Enables or disables the image. |
| \mediaGroup:&lt;Image group name&gt;] | Specifies the image group that contains the image. If no image group name is specified and only one image group exists on the server, that image group will be used. If more than one image group exists on the server, you must use this option to specify the image group. |
| [/UserFilter:&lt;SDDL&gt;] | Sets the user filter on the image. The filter string must be in Security Descriptor Definition Language (SDDL) format. Note that, unlike the **/Security** option for image groups, this option only restricts who can see the image definition, and not the actual image file resources. To restrict access to the file resources, and therefore access to all images within an image group, you will need to set security for the image group itself. |
| [/UnattendFile:&lt;Unattend file path&gt;] | Sets the full path to the unattend file to be associated with the image. For example: **D:\Files\Unattend\Img1Unattend.xml** |
| [/OverwriteUnattend:{Yes | No}] | You can specify **/Overwrite** to overwrite the unattend file if there is already an unattend file associated with the image. Note that the default setting is **No**. |

## Examples

To set values for a boot image, type one of the following:

```
wdsutil /Set-Imagmedia:WinPE boot imagemediatype:Boot /Architecture:x86 /Description:New description
wdsutil /verbose /Set-Imagmedia:WinPE boot image /Server:MyWDSServemediatype:Boot /Architecture:x86 /Filename:boot.wim
/Name:New Name /Description:New Description /Enabled:Yes
```

To set values for an install image, type one of the following:

```
wdsutil /Set-Imagmedia:Windows Vista with Officemediatype:Install /Description:New description
wdsutil /verbose /Set-Imagmedia:Windows Vista with Office /Server:MyWDSServemediatype:InstalmediaGroup:ImageGroup1
/Filename:install.wim /Name:New name /Description:New description /UserFilter:O:BAG:DUD:AI(A;ID;FA;;;SY)(A;ID;FA;;;BA)(A;ID;0x1200a9;;;AU) /Enabled:Yes /UnattendFile:\\server\share\unattend.xml /OverwriteUnattend:Yes
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [wdsutil add-image command](wdsutil-add-image)
- [wdsutil copy-image command](wdsutil-copy-image)
- [wdsutil Export-image command](wdsutil-export-image)
- [wdsutil get-image command](wdsutil-get-image)
- [wdsutil remove-image command](wdsutil-remove-image)
- [wdsutil replace-image command](wdsutil-replace-image)