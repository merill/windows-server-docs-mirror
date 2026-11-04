---
layout: Conceptual
title: typeperf | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/typeperf
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the typeperf command, which writes performance data to the command window or to a log file.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2023-06-15T00:00:00.0000000Z
locale: en-us
document_id: 5d619802-a7e3-a887-3926-9861829fe157
document_version_independent_id: 67497d14-e7cd-e02e-2c18-6bf76af18e82
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/typeperf.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/typeperf
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/typeperf.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 4cd584e0-69ee-efcc-7a01-80ddf0689392
---

# typeperf | Microsoft Learn

The **typeperf** command writes performance data to the command window or to a log file. To stop **typeperf**, press CTRL+C.

## Syntax

```
typeperf <counter [counter ...]> [options]
typeperf -cf <filename> [options]
typeperf -q [object] [options]
typeperf -qx [object] [options]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<counter [counter [...]]>` | Specifies performance counters to monitor. The `<counter>` parameter is the full name of a performance counter in \Computer\Object(Instance)\Counter format, such as `\\Server1\Processor(0)\% User Time`. |

#### Options

| Option | Description |
| --- | --- |
| -f `<CSV | TSV | BIN | SQL>` | Specifies the output file format. The default is CSV. |
| -cf `<filename>` | Specifies a file containing a list of performance counters to monitor, with one counter per line. |
| -si `<[[hh:]mm:]ss>` | Specifies the sample interval. The default is one second. |
| -o `<filename>` | Specifies the path for the output file, or the SQL database. The default is STDOUT (written to the command window). |
| -q `[object]` | Display a list of installed counters (no instances). To list counters for one object, include the object name. |
| -qx `[object]` | Display a list of installed counters with instances. To list counters for one object, include the object name. |
| -sc `<samples>` | Specifies the number of samples to collect. The default is to collect data until CTRL+C is pressed. |
| -config `<filename>` | Specifies a settings file containing command options. |
| -s `<computer_name>` | Specifies a remote computer to monitor if no computer is specified in the counter path. |
| -y | Answer *yes* to all questions without prompting. |
| /? | Displays help at the command prompt. |

## Examples

To write the values for the local computer's performance counter `\Processor(_Total)\% Processor Time` to the command window at a default sample interval of 1 second until CTRL+C is pressed, type:

```
typeperf \Processor(_Total)\% Processor Time
```

To write the values for the list of counters in the file *counters.txt* to the tab-delimited file *domain2.tsv* at a sample interval of 5 seconds until 50 samples have been collected, type:

```
typeperf -cf counters.txt -si 5 -sc 50 -f TSV -o domain2.tsv
```

To query installed counters with instances for the counter object *PhysicalDisk* and writes the resulting list to the file *counters.txt*, type:

```
typeperf -qx PhysicalDisk -o counters.txt
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)