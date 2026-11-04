---
layout: Conceptual
title: ftp ascii | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/ftp-ascii
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the ftp ascii command, which sets the file transfer type to ASCII.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 60721cd1-add3-38db-4f7e-fc08993b30b9
document_version_independent_id: c6ef5862-e0ad-9001-7036-1292b38a1915
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/ftp-ascii.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/ftp-ascii
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/ftp-ascii.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 046517b2-6d4d-4e1e-49d4-5a14f6e6d869
---

# ftp ascii | Microsoft Learn

Sets the file transfer type to ASCII. The **ftp** command supports both ASCII (default) and binary image file transfer types, but we recommend using ASCII when transferring text files. In ASCII mode, character conversions to and from the network standard character set are performed. For example, end-of-line characters are converted as necessary, based on the target operating system.

## Syntax

```
ascii
```

### Examples

To set the file transfer type to ASCII, type:

```
ascii
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [ftp binary command](ftp-binary)
- [Additional FTP guidance](/en-us/previous-versions/orphan-topics/ws.10/cc756013%28v=ws.10%29)