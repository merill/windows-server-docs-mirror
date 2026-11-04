---
layout: Conceptual
title: fsutil 8dot3name | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/fsutil-8dot3name
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the fsutil 8dot3name command, which queries or changes the settings for short name (8dot3 name) behavior.
ms.author: roharwoo
author: robinharwood
ms.topic: reference
ms.date: 2022-11-22T00:00:00.0000000Z
locale: en-us
document_id: f366fe77-febb-cb4b-54f4-8ee1610e1293
document_version_independent_id: 23861f16-2542-95b7-e5d6-9f0afaaa3de8
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/fsutil-8dot3name.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/fsutil-8dot3name
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/fsutil-8dot3name.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 08bdc65b-7079-d874-067b-087602194478
---

# fsutil 8dot3name | Microsoft Learn

Queries or changes the settings for short name (8dot3 name) behavior, which includes:

- Querying the current setting for the short name behavior.
- Scanning the specified directory path for registry keys that might be impacted if short names were stripped from the specified directory path.
- Changing the setting that controls the short name behavior. This setting can be applied to a specified volume or to the default volume setting.
- Removing the short names for all files within a directory.

Important

Permanently removing 8dot3 file names and not modifying registry keys that point to the 8dot3 file names may lead to unexpected application failures, including the inability to uninstall an application. It is recommended you first back up your directory or volume before you attempt to remove 8dot3 file names.

## Syntax

```
fsutil 8dot3name [query] [<volumepath>]
fsutil 8dot3name [scan] [/s] [/l [<log file>] ] [/v] <directorypath>
fsutil 8dot3name [set] { <defaultvalue> | <volumepath> {1|0}}
fsutil 8dot3name [strip] [/t] [/s] [/f] [/l [<log file.] ] [/v] <directorypath>
```

### Parameters

| Parameter | Description |
| --- | --- |
| query `[<volumepath>]` | Queries the file system for the state of the 8dot3 short name creation behavior.<br>If a *volumepath* isn't specified as a parameter, the default 8dot3name creation behavior setting for all volumes is displayed. |
| scan `<directorypath>` | Scans the files that are located in the specified *directorypath* for registry keys that might be impacted if 8dot3 short names were stripped from the file names. |
| set `{<defaultvalue> \| <volumepath>}` | Changes the file system behavior for 8dot3 name creation in the following instances:<br>- When *defaultvalue* is specified, the registry key, **HKLM\System\CurrentControlSet\Control\FileSystem\NtfsDisable8dot3NameCreation**, is set to the *defaultvalue*.<br>    The *DefaultValue* can have the following values:<br><br>    - **0**: Enables 8dot3 name creation for all volumes on the system.<br>    - **1**: Disables 8dot3 name creation for all volumes on the system.<br>    - **2**: Sets 8dot3 name creation on a per volume basis.<br>    - **3**: Disables 8dot3 name creation for all volumes except the system volume.<br>- When a *volumepath* is specified, the specified volumes on disk flag 8dot3name properties are set to enable 8dot3 name creation for a specified volume (**0**) or set to disable 8dot3 name creation on the specified volume (**1**).<br>    You must set the default file system behavior for 8dot3 name creation to the value **2** before you can enable or disable 8dot3 name creation for a specified volume. |
| strip `<directorypath>` | Removes the 8dot3 file names for all files that are located in the specified *directorypath*. The 8dot3 file name is not removed for any files where the *directorypath* combined with the file name contains more than 260 characters.<br>This command lists, but does not modify the registry keys that point to the files that had 8dot3 file names permanently removed. |
| `<volumepath>` | Specifies the drive name followed by a colon or the GUID in the format `volume{GUID}`. |
| /f | Specifies that all files that are located in the specified *directorypath* have the 8dot3 file names removed even if there are registry keys that point to files using the 8dot3 file name. In this case, the operation removes the 8dot3 file names, but does not modify any registry keys that point to the files that are using the 8dot3 file names. **Warning:** It's recommended that you back up your directory or volume prior to using the **/f** parameter because it may lead to unexpected application failures, including the inability to uninstall programs. |
| /l `[<log file>]` | Specifies a log file where information is written.<br>If the **/l** parameter isn't specified, all information is written to the default log file: `%temp%\8dot3_removal_log@(GMT YYYY-MM-DD HH-MM-SS)`.log\*\* |
| /s | Specifies that the operation should be applied to the subdirectories of the specified *directorypath*. |
| /t | Specifies that the removal of 8dot3 file names should be run in test mode. All operations except the actual removal of the 8dot3 file names are performed. You can use test mode to discover which registry keys point to files that use the 8dot3 file names. |
| /v | Specifies that all information that is written to the log file is also displayed on the command-line. |

### Examples

To query for the disable 8dot3 name behavior for a disk volume that is specified with the GUID, {928842df-5a01-11de-a85c-806e6f6e6963}, type:

```
fsutil 8dot3name query volume{928842df-5a01-11de-a85c-806e6f6e6963}
```

You can also query the 8dot3 name behavior by using the **behavior** subcommand.

To remove 8dot3 file names in the *D:\MyData* directory and all subdirectories, while writing the information to the log file that is specified as *mylogfile.log*, type:

```
fsutil 8dot3name strip /l mylogfile.log /s d:\MyData
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [fsutil](fsutil)
- [fsutil behavior](fsutil-behavior)