---
layout: Conceptual
title: refsutil salvage | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/refsutil-salvage
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the refsutil salvage tool, which attempts to diagnose and recover a damaged Resilient File System (ReFS) volume by copying data to another volume in Windows.
author: robinharwood
ms.author: roharwoo
ms.date: 2025-04-02T00:00:00.0000000Z
ms.topic: reference
locale: en-us
document_id: ed7e9ea0-dc27-e126-7b0e-2e631174e27b
document_version_independent_id: ed7e9ea0-dc27-e126-7b0e-2e631174e27b
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/refsutil-salvage.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/refsutil-salvage
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/refsutil-salvage.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: f9c6536b-463f-ac96-827f-3ff76584078e
---

# refsutil salvage | Microsoft Learn

The `refsutil salvage` command attempts to diagnose severely damaged Resilient File System (ReFS) volumes. It works by identifying files that remain intact despite the damage. Once these recoverable files are identified, the tool copies them to a different, specified volume.

The `refsutil salvage` tool operates in two phases, Scan Phase and Copy Phase:

- **Scan Phase**: Involves diagnosing the damaged ReFS volume and identifying recoverable files. In manual mode, you're able to pause and resume this phase. Progress and logs are stored in the working directory, allowing you to continue the scan from where it was left off.
- **Copy Phase**: Involves copying the identified recoverable files to a specified target volume. This phase can be run independently in manual mode. Logs and progress for this phase are also saved in the working directory.

In automatic mode, both the Scan Phase and Copy Phase run sequentially without user intervention. All progress and logs are saved in the working directory, ensuring that the process can be monitored and managed efficiently.

You typically don't need to use the `refsutil salvage` tool unless the volume appears as RAW, indicating corruption. If the volume is in a read-only state, the data is still accessible and can be retrieved without this tool.

Note

The `refsutil salvage` command is only supported in the following operating systems:

- Windows 10 Pro for Workstations or later
- Windows Server 2019 or later

## Syntax

```
refsutil salvage -QA | -FA | -C <source volume> <working directory> <target directory> <options>
refsutil salvage -D | -QS | -FS | -IC <source volume> <working directory> <options>
refsutil salvage -SL <source volume> <working directory> <target directory> <file list> <options>
```

## Parameters

| Parameter | Description |
| --- | --- |
| `<source volume>` | Specifies the ReFS volume to process in the format `E:` or the path to the volume mount point. |
| `<working directory>` | Specifies the location to store temporary information and logs. It must **not** be located on the `<source volume>`. |
| `<target directory>` | Specifies the location where identified files are copied to. It must **not** be located on the `<source volume>`. |
| `<file list>` | Specifies a file containing a list of specific files to be salvaged from the source volume to the target directory. This file must be generated during the Scan Phase using the `foundfiles.<volume signature>.txt` file. |
| `<options>` | - `-m`: Recovers all possible files, including deleted ones.<br>- `-v`: Specifies to use verbose mode for detailed logging.<br>- `-sv`: Skips the ReFS volume version check and assume the highest volume version that this tool can handle.<br>- `-hl`: Assumes that the volume supports [hard links](/en-us/windows/win32/fileio/hard-links-and-junctions).<br>- `-x`: Forces the volume to dismount first, if necessary. All opened handles to the volume are then invalid. |

Warning

The `-m` parameter causes the process to take longer to run and can also lead to unexpected results. Similarly, the `-sv` parameter can also lead to unexpected results.

## Remarks

In repairing ReFS volumes, two modes are featured, Automatic Mode and Manual Mode. Automatic Mode scans and repairs the volume automatically without user intervention, while Manual Mode offers advanced users detailed control over the repair process, allowing them to review and decide on specific actions.

| Automatic mode | Manual mode | Description |
| --- | --- | --- |
| Quick Automatic |  | `refsutil salvage -QA` This mode performs a Quick Scan Phase followed by a Copy Phase. It operates faster by assuming that critical structures of the volume remain intact, eliminating the need for a full-volume scan. As a result, it minimizes the recovery of outdated files, directories, or volumes. |
| Full Automatic |  | `refsutil salvage -FA` This mode performs a Full Scan Phase followed by a Copy Phase. This mode might take a long time as it scans the entire volume for any recoverable files, directories, or volumes. |
|  | Diagnose Phase | `refsutil salvage -D` Attempts to verify if the `<source volume>` is a ReFS volume and assesses its mountability. If the volume isn't mountable, the tool identifies and provides the reasons. This phase operates independently. |
|  | Quick Scan Phase | `refsutil salvage -QS` Quickly scans the `<source volume>` for recoverable files. This mode operates faster by assuming that certain critical structures of the volume remain intact, eliminating the need for a full-volume scan. As a result, it minimizes the recovery of outdated files, directories, or volumes.  Discovered files are logged in the `foundfiles.<volume signature>.txt` file located in the `<working directory>`. If the Scan Phase was interrupted previously, running the command with the `-QS` flag resumes the scan from the last checkpoint. |
|  | Full Scan Phase | `refsutil salvage -FS` Scans the entire `<source volume>` for recoverable files. This mode might take a significant amount of time as it performs a comprehensive scan of the volume. Discovered files are logged in the `foundfiles.<volume signature>.txt` file located in the `<working directory>`.  If the Scan Phase was interrupted previously, running the command with the `-FS` flag resumes the scan from the last checkpoint. |
|  | Copy Phase | `refsutil salvage -C`- Copies all files listed in the `foundfiles.<volume signature>.txt` file to the `<target directory>`. If the Scan Phase was interrupted prematurely, the `foundfiles.<volume signature>.txt` file might not be created, and no files are copied to the `<target directory>`. `refsutil salvage -SL`<br>- Copies all files listed in `<file list>` from the `<source volume>` to the `<target directory>`. The `<file list>` must be generated during the Scan Phase, although the scan doesn't need to be completed. To create a `<file list>`, copy the `foundfiles.<volume signature>.txt` file to a new file, remove entries for files that shouldn't be restored, and retain entries for files that should be restored. The [Select-String](/en-us/powershell/module/microsoft.powershell.utility/select-string) cmdlet can help filter the `foundfiles.<volume signature>.txt` to include only specific paths, extensions, or file names. `refsutil salvage -IC`<br>- Advanced users can recover files using an interactive console. This mode requires files generated during one of the Scan Phases. |

## Examples

To perform an automatic quick analysis scan, which quickly checks the volume for issues and attempts repairs without user input, run this command:

```
refsutil salvage -QA E: C:\Temp
```

To perform a full analysis scan automatically, which thoroughly checks the volume for issues and attempts repairs without user input, run this command:

```
refsutil salvage -FA E: C:\Temp
```

To perform a comprehensive scan with user control, allowing you to review and decide on specific actions during the repair process, run this command:

```
refsutil salvage -C E: C:\Temp D:\Recovered
```

To perform a quick scan that provides a detailed report of the issues found, enabling verbose logging for more information, run this command:

```
refsutil salvage -QS E: C:\Temp -v
```

To skip the version check during a full scan, which assumes the highest volume version that the tool can handle (useful if you know the tool is compatible with your volume), run this command:

```
refsutil salvage -FS E: C:\Temp -sv
```

To salvage specific files listed in a file list, created during the Scan Phase, and to force dismount the volume if necessary, run this command:

```
refsutil salvage -SL E: C:\Temp D:\Recovered FileList.txt -x
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)