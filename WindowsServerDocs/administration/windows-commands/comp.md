---
layout: Conceptual
title: comp | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/comp
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the comp command, which compares the contents of two files or sets of files byte-by-byte.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 0800f9f8-1e4a-cb06-54c2-5de3e3b4cf95
document_version_independent_id: 56f10e64-90e1-be29-b104-af97e56ff9eb
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/comp.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/comp
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/comp.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 700b1513-02eb-5c55-1379-b917fbc05c00
---

# comp | Microsoft Learn

Compares the contents of two files or sets of files byte-by-byte. These files can be stored on the same drive or on different drives, and in the same directory or in different directories. When this command compares files, it displays their location and file names. If used without parameters, **comp** prompts you to enter the files to compare.

## Syntax

```
comp [<data1>] [<data2>] [/d] [/a] [/l] [/n=<number>] [/c]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<data1>` | Specifies the location and name of the first file or set of files that you want to compare. You can use wildcard characters (**\*** and **?**) to specify multiple files. |
| `<data2>` | Specifies the location and name of the second file or set of files that you want to compare. You can use wildcard characters (**\*** and **?**) to specify multiple files. |
| /d | Displays differences in decimal format. (The default format is hexadecimal.) |
| /a | Displays differences as characters. |
| /l | Displays the number of the line where a difference occurs, instead of displaying the byte offset. |
| /n=`<number>` | Compares only the number of lines that are specified for each file, even if the files are different sizes. |
| /c | Performs a comparison that is not case-sensitive. |
| /off[line] | Processes files with the offline attribute set. |
| /? | Displays Help at the command prompt. |

## Remarks

- During the comparison, **comp** displays messages that identify the locations of unequal information between the files. Each message indicates the offset memory address of the unequal bytes and the contents of the bytes (in hexadecimal notation unless the **/a** or **/d** command-line parameter is specified). Messages appear in the following format:

    ```
    Compare error at OFFSET xxxxxxxx
    file1 = xx
    file2 = xx
    ```

    After ten unequal comparisons, **comp** stops comparing the files and displays the following message:

    `10 Mismatches - ending compare`
- If you omit necessary components of either *data1* or *data2*, or if you omit *data2* entirely, this command prompts you for the missing information.
- If *data1* contains only a drive letter or a directory name with no file name, this command compares all of the files in the specified directory to the file specified in *data1*.
- If *data2* contains only a drive letter or a directory name, the default file name for *data2* becomes the same name as for *data1*.
- If the **comp** command can't find the specified files, it will prompt you with a message about whether you want to compare additional files.
- The files that you compare can have the same file name, provided they're in different directories or on different drives. You can use wildcard characters (**\*** and **?**) to specify file names.
- You must specify **/n** to compare files of different sizes. If the file sizes are different and **/n** isn't specified, the following message is displayed:

    ```
    Files are different sizes
    Compare more files (Y/N)?
    ```

    To compare these files anyway, press **N** to stop the command. Then, run the **comp** command again, using the **/n** option to compare only the first portion of each file.
- If you use wildcard characters (**\*** and **?**) to specify multiple files, **comp** finds the first file that matches *data1* and compares it with the corresponding file in *data2*, if it exists. The **comp** command reports the results of the comparison for each file matching *data1*. When finished, **comp** displays the following message:

    `Compare more files (Y/N)?`

    To compare more files, press **Y**. The **comp** command prompts you for the locations and names of the new files. To stop the comparisons, press **N**. When you press **Y**, you're prompted for which command-line options to use. If you don't specify any command-line options, **comp** uses the ones you specified before.

## Examples

To compare the contents of the directory *c:\reports* with the backup directory `\\sales\backup\april`, type:

```
comp c:\reports \\sales\backup\april
```

To compare the first ten lines of the text files in the *\invoice* directory and display the result in decimal format, type:

```
comp \invoice\*.txt \invoice\backup\*.txt /n=10 /d
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)