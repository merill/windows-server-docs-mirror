---
layout: Conceptual
title: chcp | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/chcp
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the chcp command, which changes the active console code page.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 6c4b8705-8d38-cad1-a9aa-42e98003624d
document_version_independent_id: ef824a08-3cbb-b96b-b45f-f54cd0994521
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/chcp.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/chcp
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/chcp.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 2632d71c-bb57-e27f-a5ed-212f13ab1e0f
---

# chcp | Microsoft Learn

Changes the active console code page. If used without parameters, **chcp** displays the number of the active console code page.

## Syntax

```
chcp [<nnn>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<nnn>` | Specifies the code page. |
| /? | Displays help at the command prompt. |

The following table lists each supported code page and its country/region or language:

| Code page | Country/region or language |
| --- | --- |
| 437 | United States |
| 850 | Multilingual (Latin I) |
| 852 | Slavic (Latin II) |
| 855 | Cyrillic (Russian) |
| 857 | Turkish |
| 860 | Portuguese |
| 861 | Icelandic |
| 863 | Canadian-French |
| 865 | Nordic |
| 866 | Russian |
| 869 | Modern Greek |
| 936 | Chinese |

#### Remarks

- Only the original equipment manufacturer (OEM) code page that is installed with Windows appears correctly in a Command Prompt window that uses Raster fonts. Other code pages appear correctly in full-screen mode or in Command Prompt windows that use TrueType fonts.
- You don't need to prepare code pages (as in MS-DOS).
- Programs that you start after you assign a new code page use the new code page. However, programs (except Cmd.exe) that you started before assigning the new code page will continue to use the original code page.

## Examples

To view the active code page setting, type:

```
chcp
```

A message similar to the following appears: `Active code page: 437`

To change the active code page to 850 (Multilingual), type:

```
chcp 850
```

If the specified code page is invalid, the following error message appears: `Invalid code page`

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [Code Page BitFields](/en-us/windows/win32/intl/code-page-bitfields)
- [Code Page Identifiers](/en-us/windows/win32/intl/code-page-identifiers)