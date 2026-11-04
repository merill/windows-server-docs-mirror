---
layout: Conceptual
title: import diskshadow | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/import
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the import command, which imports a transportable shadow copy from a loaded metadata file into the system.
ms.topic: reference
author: robinharwood
ms.author: roharwoo
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 714d5946-951e-8655-fb80-3f6efb38d502
document_version_independent_id: 6b6a2646-3be5-cc98-50b2-49d9e89d7d2e
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/import.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/import
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/import.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/aebdc4a3-c54b-4eea-94e3-663d5e166f57
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/1baec8e6-ab38-4b56-bb59-f6282d94f311
platformId: 900428e5-d05b-db2a-fd90-1a8aadafe442
---

# import diskshadow | Microsoft Learn

Imports a transportable shadow copy from a loaded metadata file into the system.

> 
> [IMPORTANT] Before you can use this command, you must use the [load metadata command](load-metadata) to load a DiskShadow metadata file.

## Syntax

```
import
```

#### Remarks

- Transportable shadow copies aren't stored on the system immediately. Their details are stored in a Backup Components Document XML file, which DiskShadow automatically requests and saves in a .cab metadata file in the working directory. Use the [set metadata command](set-metadata) to change the path and name of this XML file.

## Examples

The following is a sample DiskShadow script that demonstrates the use of the **import** command:

```
#Sample DiskShadow script demonstrating IMPORT
SET CONTEXT PERSISTENT
SET CONTEXT TRANSPORTABLE
SET METADATA transHWshadow_p.cab
#P: is the volume supported by the Hardware Shadow Copy provider
ADD VOLUME P:
CREATE
END BACKUP
#The (transportable) shadow copy is not in the system yet.
#You can reset or exit now if you wish.

LOAD METADATA transHWshadow_p.cab
IMPORT
#The shadow copy will now be loaded into the system.
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [diskshadow command](diskshadow)