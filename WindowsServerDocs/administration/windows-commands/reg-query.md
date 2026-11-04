---
layout: Conceptual
title: reg query | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/reg-query
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the reg query command, which returns a list of the next tier of subkeys and entries that are located under a specified subkey in the registry.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2022-11-02T00:00:00.0000000Z
locale: en-us
document_id: b712cc31-d8c9-7694-01b8-a85cda240f7f
document_version_independent_id: 9c95c177-9bef-03ec-5774-f92b7ea42c9e
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/reg-query.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/reg-query
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/reg-query.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/12ed19f9-ebdf-4c8a-8bcd-7a681836774d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3a764584-4f97-452b-8f1d-36f19b12f6ae
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: e17ea3f5-8dff-b8eb-3640-8ae27129928e
---

# reg query | Microsoft Learn

Returns a list of the next tier of subkeys and entries that are located under a specified subkey in the registry.

## Syntax

```
reg query <keyname> [{/v <valuename> | /ve}] [/s] [/se <separator>] [/f <data>] [{/k | /d}] [/c] [/e] [/t <Type>] [/z] [/reg:32] [/reg:64]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<keyname>` | Specifies the full path of the subkey. To specify a remote computer, include the computer name (in the format `\\<computername>\`) as part of the *keyname*. Omitting `\\<computername>\` causes the operation to default to the local computer. The *keyname* must include a valid root key. Valid root keys for the local computer are: **HKLM**, **HKCU**, **HKCR**, **HKU**, and **HKCC**. If a remote computer is specified, valid root keys are: **HKLM** and **HKU**. If the registry key name contains a space, enclose the key name in quotes. |
| /v `<valuename>` | Specifies the registry value name that is to be queried. If omitted, all value names for *keyname* are returned. *Valuename* for this parameter is optional if the **/f** option is also used. |
| /ve | Runs a query for value names that are empty. |
| /s | Specifies to query all subkeys and value names recursively. |
| /se `<separator>` | Specifies the single value separator to search for in the value name type **REG\_MULTI\_SZ**. If *separator* isn't specified, **\0** is used. |
| /f `<data>` | Specifies the data or pattern to search for. Use double quotes if a string contains spaces. If not specified, a wildcard (**\***) is used as the search pattern. |
| /k | Specifies to search in key names only. Must be used with /f. |
| /d | Specifies to search in data only. |
| /c | Specifies that the query is case sensitive. By default, queries are not case sensitive. |
| /e | Specifies to return only exact matches. By default, all the matches are returned. |
| /t `<Type>` | Specifies registry types to search. Valid types are: **REG\_SZ**, **REG\_MULTI\_SZ**, **REG\_EXPAND\_SZ**, **REG\_DWORD**, **REG\_BINARY**, **REG\_NONE**. If not specified, all types are searched. |
| /z | Specifies to include the numeric equivalent for the registry type in search results. |
| /reg:32 | Specifies the key should be accessed using the 32-bit registry view. |
| /reg:64 | Specifies the key should be accessed using the 64-bit registry view. |
| /? | Displays help at the command prompt. |

#### Remarks

- The return values for the **reg query** operation are:

    | Value | Description |
    | --- | --- |
    | 0 | Success |
    | 1 | Failure |

### Examples

To display the value of the name value Version in the HKLM\Software\Microsoft\ResKit key, type:

```
reg query HKLM\Software\Microsoft\ResKit /v Version
```

To display all subkeys and values under the key HKLM\Software\Microsoft\ResKit\Nt\Setup on a remote computer named ABC, type:

```
reg query \\ABC\HKLM\Software\Microsoft\ResKit\Nt\Setup /s
```

To display all the subkeys and values of the type REG\_MULTI\_SZ using **#** as the separator, type:

```
reg query HKLM\Software\Microsoft\ResKit\Nt\Setup /se #
```

To display the key, value, and data for exact and case sensitive matches of SYSTEM under the HKLM root of data type REG\_SZ, type:

```
reg query HKLM /f SYSTEM /t REG_SZ /c /e
```

To display the key, value, and data that match **0F** in the data under the HKCU root key of data type REG\_BINARY, type:

```
reg query HKCU /f 0F /d /t REG_BINARY
```

To display the keys, values, and data that match **asp.net** under the key HKLM\SOFTWARE\Microsoft and all subkeys, type:

```
reg query HKLM\SOFTWARE\Microsoft /s /f asp.net
```

To display only the keys that match **asp.net** under the key HKLM\SOFTWARE\Microsoft and all subkeys, type:

```
reg query HKLM\SOFTWARE\Microsoft /s /f asp.net /k
```

To display the value and data for value names of null (default) under HKLM\SOFTWARE, type:

```
reg query HKLM\SOFTWARE /ve
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)