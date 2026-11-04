---
layout: Conceptual
title: vssadmin list providers - in Windows and Windows Server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/vssadmin-list-providers
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Use the vssadmin list providers command to show the registered volume shadow copy providers on a computer, including their type and version.
ms.topic: reference
author: robinharwood
ms.author: roharwoo
ms.date: 2026-09-07T00:00:00.0000000Z
ai-usage: ai-assisted
locale: en-us
document_id: f46af995-7046-451c-52be-8ad69c628ee6
document_version_independent_id: f46af995-7046-451c-52be-8ad69c628ee6
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/vssadmin-list-providers.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/vssadmin-list-providers
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/vssadmin-list-providers.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 7e7eac86-3a6e-20a5-974a-9153ba057e1a
---

# vssadmin list providers - in Windows and Windows Server | Microsoft Learn

Lists the volume shadow copy providers registered on the computer. A shadow copy provider is the component that creates and manages shadow copies (point-in-time snapshots) of a volume. A provider can be the built-in system provider that Windows includes, or a software or hardware provider that a storage vendor supplies.

Run this command when you want to confirm which providers are available before you create a shadow copy, or to verify that a vendor-supplied provider is installed and registered correctly.

## Syntax

```
vssadmin list providers
```

## Examples

To list all registered volume shadow copy providers, type:

```
vssadmin list providers
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [vssadmin command](vssadmin)