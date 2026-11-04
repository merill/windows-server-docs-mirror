---
layout: Conceptual
title: reg commands | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/reg
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the reg commands, which perform operations on registry subkey information and values in registry entries.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 6c6e37c1-c801-8d0c-0d69-5c9026b2929e
document_version_independent_id: bbdabe87-e3a2-492b-9e0d-05c0db0cfdc5
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/reg.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/reg
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/reg.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: f5211185-2a43-4278-bc96-729919be20fd
---

# reg commands | Microsoft Learn

Performs operations on registry subkey information and values in registry entries.

Some operations enable you to view or configure registry entries on local or remote computers, while others allow you to configure only local computers. Using **reg** to configure the registry of remote computers limits the parameters that you can use in some operations. Check the syntax and parameters for each operation to verify that they can be used on remote computers.

Caution

Don't edit the registry directly unless you have no alternative. The registry editor bypasses standard safeguards, allowing settings that can degrade performance, damage your system, or even require you to reinstall Windows. You can safely alter most registry settings by using the programs in Control Panel or Microsoft Management Console (MMC). If you must edit the registry directly, back it up first.

## Syntax

```
reg add
reg compare
reg copy
reg delete
reg export
reg import
reg load
reg query
reg restore
reg save
reg unload
```

### Parameters

| Parameter | Description |
| --- | --- |
| [reg add](reg-add) | Adds a new subkey or entry to the registry. |
| [reg compare](reg-compare) | Compares specified registry subkeys or entries. |
| [reg copy](reg-copy) | Copies a registry entry to a specified location on the local or remote computer. |
| [reg delete](reg-delete) | Deletes a subkey or entries from the registry. |
| [reg export](reg-export) | Copies the specified subkeys, entries, and values of the local computer into a file for transfer to other servers. |
| [reg import](reg-import) | Copies the contents of a file that contains exported registry subkeys, entries, and values into the registry of the local computer. |
| [reg load](reg-load) | Writes saved subkeys and entries into a different subkey in the registry. |
| [reg query](reg-query) | Returns a list of the next tier of subkeys and entries that are located under a specified subkey in the registry. |
| [reg restore](reg-restore) | Writes saved subkeys and entries back to the registry. |
| [reg save](reg-save) | Saves a copy of specified subkeys, entries, and values of the registry in a specified file. |
| [reg unload](reg-unload) | Removes a section of the registry that was loaded using the **reg load** operation. |

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)