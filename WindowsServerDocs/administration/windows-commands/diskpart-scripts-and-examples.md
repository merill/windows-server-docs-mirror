---
layout: Conceptual
title: diskpart scripts and examples | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/diskpart-scripts-and-examples
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for diskpart scripts and examples about how to automate disk-related tasks, such as creating volumes or converting disks to dynamic disks.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 0c50c55c-6062-bb83-5f41-73377349c9ca
document_version_independent_id: 68b62cde-c85f-9240-362a-c5702ba10ae7
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/diskpart-scripts-and-examples.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/diskpart-scripts-and-examples
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/diskpart-scripts-and-examples.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/68cb9039-df60-49b0-8ef8-89ad96497f63
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/725b6df3-93e8-472d-834e-e7e0d2953d35
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: d8d8a2b0-b6eb-3f17-57fb-0b6be947dc9f
---

# diskpart scripts and examples | Microsoft Learn

Use `diskpart /s` to run scripts that automate disk-related tasks, such as creating volumes or converting disks to dynamic disks. Scripting these tasks is useful if you deploy Windows by using unattended Setup or the Sysprep tool, which do not support creating volumes other than the boot volume.

To create a diskpart script, create a text file that contains the Diskpart commands that you want to run, with one command per line, and no empty lines. You can start a line with `rem` to make the line a comment. For example, here's a script that wipes a disk and then creates a 300 MB partition for the Windows Recovery Environment:

```
select disk 0
clean
convert gpt
create partition primary size=300
format quick fs=ntfs label=Windows RE tools
assign letter=T
```

## Examples

- To run a diskpart script, at the command prompt, type the following command, where *scriptname* is the name of the text file that contains your script:

```
diskpart /s scriptname.txt
```

- To redirect diskpart's scripting output to a file, type the following command, where *logfile* is the name of the text file where diskpart writes its output:

```
diskpart /s scriptname.txt > logfile.txt
```

### Remarks

- When using the **diskpart** command as a part of a script, we recommend that you complete all of the diskpart operations together as part of a single diskpart script. You can run consecutive diskpart scripts, but you must allow at least 15 seconds between each script for a complete shutdown of the previous execution before running the **diskpart** command again in successive scripts. Otherwise, the successive scripts might fail. You can add a pause between consecutive diskpart scripts by adding the `timeout /t 15` command to your batch file along with your diskpart scripts.
- When diskpart starts, the diskpart version and computer name display at the command prompt. By default, if diskpart encounters an error while attempting to perform a scripted task, diskpart stops processing the script and displays an error code (unless you specified the **noerr** parameter). However, diskpart always returns errors when it encounters syntax errors, regardless of whether you used the **noerr** parameter. The **noerr** parameter enables you to perform useful tasks such as using a single script to delete all partitions on all disks regardless of the total number of disks.

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [Sample: Configure UEFI/GPT-Based Hard Drive Partitions by Using Windows PE and DiskPart](/en-us/previous-versions/windows/it-pro/windows-8.1-and-8/hh825686%28v=win.10%29)
- [Sample: Configure BIOS/MBR-Based Hard Disk Partitions by Using Windows PE and DiskPart](/en-us/previous-versions/windows/it-pro/windows-8.1-and-8/hh825677%28v=win.10%29)
- [Storage Cmdlets in Windows PowerShell](/en-us/powershell/module/storage/)