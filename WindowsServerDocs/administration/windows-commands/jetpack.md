---
layout: Conceptual
title: jetpack | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/jetpack
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the jetpack command, which compacts a Windows Internet Name Service (WINS) or Dynamic Host Configuration Protocol (DHCP) database.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 8222fc32-b66e-e5bf-6749-b89feab31968
document_version_independent_id: 64207e69-2b33-e034-df98-fd4b4821250f
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/jetpack.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/jetpack
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/jetpack.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/68cb9039-df60-49b0-8ef8-89ad96497f63
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/725b6df3-93e8-472d-834e-e7e0d2953d35
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: ebc25c43-9bf9-e0fa-0810-ca98c4c91bf0
---

# jetpack | Microsoft Learn

Compacts a Windows Internet Name Service (WINS) or Dynamic Host Configuration Protocol (DHCP) database. We recommend you compact the WINS database whenever it approaches 30 MB.

Jetpack.exe compacts the database by:

1. Copying the database information to a temporary database file.
2. Deleting the original database file, either WINS or DHCP.
3. Renames the temporary database files to the original filename.

## Syntax

```
jetpack.exe <database_name> <temp_database_name>
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<database_name>` | Specifies the name of the original database file. |
| `<temp_database_name>` | Specifies the name of the temporary database file to be created by jetpack.exe.<br>Note: This temporary file is removed when the compact process is complete. For this command to work properly, you must make sure your temp file name is unique and that a file with that name doesn't already exist. |
| /? | Displays help at the command prompt. |

### Examples

To compact the WINS database, where **Tmp.mdb** is a temporary database and **Wins.mdb** is the WINS database, type:

```
cd %SYSTEMROOT%\SYSTEM32\WINS
NET STOP WINS
jetpack Wins.mdb Tmp.mdb
NET start WINS
```

To compact the DHCP database, where **Tmp.mdb** is a temporary database and **Dhcp.mdb** is the DHCP database, type:

```
cd %SYSTEMROOT%\SYSTEM32\DHCP
NET STOP DHCPSERVER
jetpack Dhcp.mdb Tmp.mdb
NET start DHCPSERVER
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)