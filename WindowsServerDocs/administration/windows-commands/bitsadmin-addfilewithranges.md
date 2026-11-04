---
layout: Conceptual
title: bitsadmin addfilewithranges | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/bitsadmin-addfilewithranges
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the bitsadmin addfilewithranges command, which adds a file to the specified job. BITS downloads the specified ranges from the remote file.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: f4da742d-2141-ca97-d979-c1674ae58d8d
document_version_independent_id: e43f70f1-f78d-6963-88ef-bfe2063e2dd9
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/bitsadmin-addfilewithranges.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/bitsadmin-addfilewithranges
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/bitsadmin-addfilewithranges.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 06ed54cd-ab13-9c28-6798-a54c32bc68ad
---

# bitsadmin addfilewithranges | Microsoft Learn

Adds a file to the specified job. BITS downloads the specified ranges from the remote file. This switch is valid only for download jobs.

## Syntax

```
bitsadmin /addfilewithranges <job> <remoteURL> <localname> <rangelist>
```

### Parameters

| Parameter | Description |
| --- | --- |
| job | The job's display name or GUID. |
| remoteURL | URL of the file on the server. |
| localname | Name of the file on the local computer. Must contain an absolute path to the file. |
| rangelist | Comma-delimited list of offset:length pairs. Use a colon to separate the offset value from the length value. For example, a value of `0:100,2000:100,5000:eof` tells BITS to transfer 100 bytes from offset 0, 100 bytes from offset 2000, and the remaining bytes from offset 5000 to the end of the file. |

## Remarks

- The token **eof** is a valid length value within the offset and length pairs in the `<rangelist>`. It instructs the service to read to the end of the specified file.
- The `addfilewithranges` command will fail with error code 0x8020002c, if a zero-length range is specified along with another range using same offset, such as:

    `c:\bits>bitsadmin /addfilewithranges j2 http://bitsdc/dload/1k.zip c:\1k.zip 100:0,100:5`

    **Error message:** Unable to add file to job - 0x8020002c. The list of byte ranges contains some overlapping ranges, which are not supported.

    **Workaround:** Don't specify the zero-length range first. For example, use `bitsadmin /addfilewithranges j2 http://bitsdc/dload/1k.zip c:\1k.zip 100:5,100:0`

## Examples

To transfer 100 bytes from offset 0, 100 bytes from offset 2000, and the remaining bytes from offset 5000 to the end of the file:

```
bitsadmin /addfilewithranges http://downloadsrv/10mb.zip c:\10mb.zip 0:100,2000:100,5000:eof
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [bitsadmin command](bitsadmin)