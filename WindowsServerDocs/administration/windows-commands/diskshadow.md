---
layout: Conceptual
title: Diskshadow | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/diskshadow
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the Diskshadow command, which is a tool that exposes the functionality offered by the volume shadow copy service (VSS).
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 56cd1813-d054-6841-410b-0c75fdae1e86
document_version_independent_id: 8552e280-a677-0671-50df-d64b1cb6cd93
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/diskshadow.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/diskshadow
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/diskshadow.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/aebdc4a3-c54b-4eea-94e3-663d5e166f57
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/1baec8e6-ab38-4b56-bb59-f6282d94f311
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: cadd5171-8167-243d-8ecc-918d95d93f91
---

# Diskshadow | Microsoft Learn

Diskshadow.exe is a tool that exposes the functionality offered by the volume shadow copy Service (VSS). By default, Diskshadow uses an interactive command interpreter similar to that of Diskraid or Diskpart. Diskshadow also includes a scriptable mode.

Note

Membership in the local Administrators group, or equivalent, is the minimum required to run Diskshadow.

## Syntax

For interactive mode, type the following at the command prompt to start the Diskshadow command interpreter:

```
diskshadow
```

For script mode, type the following, where *script.txt* is a script file containing Diskshadow commands:

```
diskshadow -s script.txt
```

### Parameters

You can run the following commands in the Diskshadow command interpreter or through a script file. At a minimum, only **add** and **create** are necessary to create a shadow copy. However, this forfeits the context and option settings, will be a copy backup, and creates a shadow copy with no backup execution script.

| Command | Description |
| --- | --- |
| [set command](set) | Sets the context, options, verbose mode, and metadata file for creating shadow copies. |
| [load metadata command](load-metadata) | Loads a metadata .cab file prior to importing a transportable shadow copy or loads the writer metadata in the case of a restore. |
| [writer command](writer) | verifies that a writer or component is included or excludes a writer or component from the backup or restore procedure. |
| [add command](add) | Adds volumes to the set of volumes that are to be shadow copied, or adds aliases to the alias environment. |
| [create command](create) | Starts the shadow copy creation process, using the current context and option settings. |
| [exec command](exec) | Executes a file on the local computer. |
| [begin backup command](begin-backup) | Starts a full backup session. |
| [end backup command](end-backup) | Ends a full backup session and issues a **backupcomplete** event with the appropriate writer state, if needed. |
| [begin restore command](begin-restore) | Starts a restore session and issues a **prerestore** event to involved writers. |
| [end restore command](end-restore) | Ends a restore session and issues a **postrestore** event to involved writers. |
| [reset command](reset) | Resets Diskshadow to the default state. |
| [list command](list) | Lists writers, shadow copies, or currently registered shadow copy providers that are on the system. |
| [delete shadows command](delete-shadows) | Deletes shadow copies. |
| [import command](import) | Imports a transportable shadow copy from a loaded metadata file into the system. |
| [mask command](mask) | Removes hardware shadow copies that were imported by using the **import** command. |
| [expose command](expose) | Exposes a persistent shadow copy as a drive letter, share, or mount point. |
| [unexpose command](unexpose) | Unexposes a shadow copy that was exposed by using the **expose** command. |
| [break command](break_2) | Disassociates a shadow copy volume from VSS. |
| [revert command](revert) | Reverts a volume back to a specified shadow copy. |
| [exit command](exit) | Exits the command interpreter or script. |

## Examples

This is a sample sequence of commands that will create a shadow copy for backup. It can be saved to file as script.dsh, and executed using `diskshadow /s script.dsh`.

Assume the following:

- You have an existing directory called c:\diskshadowdata.
- Your system volume is C: and your data volume is D:.
- You have a backupscript.cmd file in c:\diskshadowdata.
- Your backupscript.cmd file will perform the copy of shadow data p: and q: to your backup drive.

You can enter these commands manually or script them:

```
#Diskshadow script file
set context persistent nowriters
set metadata c:\diskshadowdata\example.cab
set verbose on
begin backup
add volume c: alias systemvolumeshadow
add volume d: alias datavolumeshadow

create

expose %systemvolumeshadow% p:
expose %datavolumeshadow% q:
exec c:\diskshadowdata\backupscript.cmd
end backup
#End of script
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)