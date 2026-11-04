---
layout: Conceptual
title: reg compare | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/reg-compare
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the reg compare command, which compares specified registry subkeys or entries.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 9d7a42cc-ec9a-e4d0-45c4-8ecfe8f891a0
document_version_independent_id: 6ec79b5d-c609-260b-ba04-f60140652940
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/reg-compare.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/reg-compare
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/reg-compare.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: b96e8cb0-548a-3d4a-0e86-ed76e0f06fe5
---

# reg compare | Microsoft Learn

Compares specified registry subkeys or entries.

## Syntax

```
reg compare <keyname1> <keyname2> [{/v Valuename | /ve}] [{/oa | /od | /os | on}] [/s]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<keyname1>` | Specifies the full path of the subkey or entry to be added. To specify a remote computer, include the computer name (in the format `\\<computername>\`) as part of the *keyname*. Omitting `\\<computername>\` causes the operation to default to the local computer. The *keyname* must include a valid root key. Valid root keys for the local computer are: **HKLM**, **HKCU**, **HKCR**, **HKU**, and **HKCC**. If a remote computer is specified, valid root keys are: **HKLM** and **HKU**. If the registry key name contains a space, enclose the key name in quotes. |
| `<keyname2>` | Specifies the full path of the second subkey to be compared. To specify a remote computer, include the computer name (in the format `\\<computername>\`) as part of the *keyname*. Omitting `\\<computername>\` causes the operation to default to the local computer. Specifying only the computer name in *keyname2* causes the operation to use the path to the subkey specified in *keyname1*. The *keyname* must include a valid root key. Valid root keys for the local computer are: **HKLM**, **HKCU**, **HKCR**, **HKU**, and **HKCC**. If a remote computer is specified, valid root keys are: **HKLM** and **HKU**. If the registry key name contains a space, enclose the key name in quotes. |
| /v `<Valuename>` | Specifies the value name to compare under the subkey. |
| /ve | Specifies that only entries that have a value name of null should be compared. |
| /oa | Specifies that all differences and matches are displayed. By default, only the differences are listed. |
| /od | Specifies that only differences are displayed. This is the default behavior. |
| /os | Specifies that only matches are displayed. By default, only the differences are listed. |
| /on | Specifies that nothing is displayed. By default, only the differences are listed. |
| /s | Compares all subkeys and entries recursively. |
| /? | Displays help at the command prompt. |

#### Remarks

- The return values for the **reg compare** operation are:

    | Value | Description |
    | --- | --- |
    | 0 | The comparison is successful and the result is identical. |
    | 1 | The comparison failed. |
    | 2 | The comparison was successful and differences were found. |
- The symbols displayed in the results, include:

    | Symbol | Description |
    | --- | --- |
    | = | *KeyName1* data is equal to *KeyName2* data. |
    | &lt; | *KeyName1* data is less than *KeyName2* data. |
    | &gt; | *KeyName1* data is greater than *KeyName2* data. |

### Examples

To compare all values under the key **MyApp** with all values under the key **SaveMyApp**, type:

```
reg compare HKLM\Software\MyCo\MyApp HKLM\Software\MyCo\SaveMyApp
```

To compare the value for the Version under the key **MyCo** and the value for the Version under the key **MyCo1**, type:

```
reg compare HKLM\Software\MyCo HKLM\Software\MyCo1 /v Version
```

To compare all subkeys and values under HKLM\Software\MyCo on the computer named ZODIAC, with all subkeys and values under HKLM\Software\MyCo on the local computer, type:

```
reg compare \\ZODIAC\HKLM\Software\MyCo \\. /s
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)