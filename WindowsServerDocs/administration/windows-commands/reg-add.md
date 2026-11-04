---
layout: Conceptual
title: reg add | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/reg-add
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the reg add command, which adds a new subkey or entry to the registry.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2024-01-04T00:00:00.0000000Z
locale: en-us
document_id: bd817f1d-e494-af38-4a10-86360d63c195
document_version_independent_id: 11fcbf91-6c28-9ae8-045a-35ea97444dfe
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/reg-add.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/reg-add
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/reg-add.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 3ee63eb9-a0d4-d414-2854-3e0d0742c0c5
---

# reg add | Microsoft Learn

Adds a new subkey or entry to the registry.

## Syntax

```
reg add <keyname> [/v valuename | /ve] [/t datatype] [/s separator] [/d data] [/f] [/reg:32 | /reg:64]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<keyname>` | Specifies the full path of the subkey or entry to be added. To specify a remote computer, include the computer name (in the format `\\<computername>\`) as part of the *keyname*. Omitting `\\<computername>\` causes the operation to default to the local computer. The *keyname* must include a valid root key. Valid root keys for the local computer are: <br>- **HKCR** (HKEY\_CLASSES\_ROOT)<br>- **HKCU** (HKEY\_CURRENT\_USER)<br>- **HKLM** (HKEY\_LOCAL\_MACHINE)<br>- **HKU** (HKEY\_USERS)<br>- **HKCC** (HKEY\_CURRENT\_CONFIG)<br><br>If a remote computer is specified, valid root keys are: **HKLM** and **HKU**. If the registry key name contains a space, enclose the key name in quotes. |
| /v `<Valuename>` | Specifies the name of the add registry entry. |
| /ve | Specifies that the added registry entry has a null value. |
| /t `<Type>` | Specifies the type for the registry entry. *Type* must be one of the following:<br>- REG\_SZ<br>- REG\_MULTI\_SZ<br>- REG\_DWORD\_BIG\_ENDIAN<br>- REG\_DWORD<br>- REG\_BINARY<br>- REG\_DWORD\_LITTLE\_ENDIAN<br>- REG\_LINK<br>- REG\_FULL\_RESOURCE\_DESCRIPTOR<br>- REG\_EXPAND\_SZ |
| /s `<Separator>` | Specifies the character to be used to separate multiple instances of data when the **REG\_MULTI\_SZ** data type is specified and more than one entry is listed. If not specified, the default separator is **\0**. |
| /d `<Data>` | Specifies the data for the new registry entry. |
| /f | Adds the registry entry without prompting for confirmation. |
| /reg:32 | Specifies the key should be accessed using the 32-bit registry view. |
| /reg:64 | Specifies the key should be accessed using the 64-bit registry view. |
| /? | Displays help at the command prompt. |

#### Remarks

- Subtrees can't be added with this operation. This version of **reg** doesn't ask for confirmation when adding a subkey.
- The return values for the **reg add** operation are:

| Value | Description |
| --- | --- |
| 0 | Success |
| 1 | Failure |

- For the **REG\_EXPAND\_SZ** key type, use the caret symbol ( **^** ) with **%** inside the /d parameter.

### Examples

To add the key *HKLM\Software\MyCo* on remote computer *ABC*, type:

```
reg add \\ABC\HKLM\Software\MyCo
```

To add a registry entry to *HKLM\Software\MyCo* with a value named *Data*, the type *REG\_BINARY*, and data of *fe340ead*, type:

```
reg add HKLM\Software\MyCo /v Data /t REG_BINARY /d fe340ead
```

To add a multi-valued registry entry to *HKLM\Software\MyCo* with a value named *MRU*, the type *REG\_MULTI\_SZ*, and data of *fax\0mail\0*, type:

```
reg add HKLM\Software\MyCo /v MRU /t REG_MULTI_SZ /d fax\0mail\0
```

To add an expanded registry entry to *HKLM\Software\MyCo* with a value named *Path*, the type *REG\_EXPAND\_SZ*, and data of *%systemroot%*, type:

```
reg add HKLM\Software\MyCo /v Path /t REG_EXPAND_SZ /d ^%systemroot^%
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)