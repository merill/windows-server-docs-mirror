---
layout: Conceptual
title: create (diskshadow) | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/create_2
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the create command, which creates a shadow copy (snapshot) of a volume or alias.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2023-10-12T00:00:00.0000000Z
locale: en-us
document_id: 61265e19-b541-57ec-1ca2-8559df96e4e0
document_version_independent_id: 61265e19-b541-57ec-1ca2-8559df96e4e0
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/create_2.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/create_2
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/create_2.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/aebdc4a3-c54b-4eea-94e3-663d5e166f57
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c783a8fb-cf36-41ad-90c6-0692a0540484
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/1baec8e6-ab38-4b56-bb59-f6282d94f311
platformId: e31f56d3-d58d-da9b-3fa4-fc267ace15d7
---

# create (diskshadow) | Microsoft Learn

Starts the shadow copy creation process using the current context and option settings. Requires at least one volume in the Shadow Copy Set.

## Syntax

```
create
```

### Remarks

- You must add at least one volume with the add volume command before you can use the create command.
- You can use the begin backup command to specify a full backup rather than a copy backup.
- After you run the create command, you can use the exec command to run a duplication script for backup from the shadow copy.

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)