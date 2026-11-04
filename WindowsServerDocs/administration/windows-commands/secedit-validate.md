---
layout: Conceptual
title: secedit validate | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/secedit-validate
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the secedit validate command, which validates the security settings stored in a security template.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: e9f353a9-7085-7e80-19d7-8a5b1e25a481
document_version_independent_id: 2dbf0016-1ccb-d089-32fc-274b676cf45b
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/secedit-validate.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/secedit-validate
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/secedit-validate.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 36dad2ad-03d6-72f6-e7cd-025e267cd085
---

# secedit validate | Microsoft Learn

Validates the security settings stored in a security template (.inf file). Validating security templates can help you determine if one is corrupted or inappropriately set. Corrupted or inappropriately set security templates aren't applied.

## Syntax

```
secedit /validate <configuration file name>
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<configuration file name>` | Required. Specifies the path and file name for the security template that will be validated. Log files aren't updated by this command. |

## Examples

To verify that the rollback .inf file, *secRBKcontoso.inf*, is still valid after rollback, type:

```
secedit /validate secRBKcontoso.inf
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [secedit /analyze](secedit-analyze)
- [secedit /configure](secedit-configure)
- [secedit /export](secedit-export)
- [secedit /generaterollback](secedit-generaterollback)
- [secedit /import](secedit-import)