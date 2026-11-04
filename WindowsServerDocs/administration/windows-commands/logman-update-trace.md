---
layout: Conceptual
title: logman update trace | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/logman-update-trace
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the logman update trace command, which updates the properties of an existing event trace data collector.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 74b24bcf-7ccc-a6b4-5a77-98d12fc8981c
document_version_independent_id: 85abeb31-5387-d459-ab52-00d7c956d90b
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/logman-update-trace.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/logman-update-trace
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/logman-update-trace.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/6ab7faaf-d791-4a26-96a2-3b11738538e7
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/302e28b0-1f09-4811-9a9b-2a72e0770581
platformId: 6456d7ed-e1a0-ac4b-36e4-17e8cd5499e1
---

# logman update trace | Microsoft Learn

Updates the properties of an existing event trace data collector.

## Syntax

```
logman update trace <[-n] <name>> [options]
```

### Parameters

| Parameter | Description |
| --- | --- |
| -s `<computer name>` | Performs the command on the specified remote computer. |
| -config `<value>` | Specifies the settings file containing command options. |
| -ets | Sends commands to Event Trace Sessions directly without saving or scheduling. |
| [-n] `<name>` | Name of the target object. |
| -f `<bin|bincirc>` | Specifies the log format for the data collector. |
| -[-]u `<user [password]>` | Specifies the user to Run As. Entering an `*` for the password produces a prompt for the password. The password is not displayed when you type it at the password prompt. |
| -m `<[start] [stop] [[start] [stop] [...]]>` | Changes to manual start or stop instead of a scheduled begin or end time. |
| -rf `<[[hh:]mm:]ss>` | Runs the data collector for the specified period of time. |
| -b `<M/d/yyyy h:mm:ss[AM|PM]>` | Begins collecting data at the specified time. |
| -e `<M/d/yyyy h:mm:ss[AM|PM]>` | Ends data collection at the specified time. |
| -o `<path|dsn!log>` | Specifies the output log file or the DSN and log set name in a SQL database. |
| -[-]r | Repeats the data collector daily at the specified begin and end times. |
| -[-]a | Appends an existing log file. |
| -[-]ow | Overwrites an existing log file. |
| -[-]v `<nnnnnn|mmddhhmm>` | Attaches file versioning information to the end of the log file name. |
| -[-]rc `<task>` | Runs the command specified each time the log is closed. |
| -[-]max `<value>` | Maximum log file size in MB or maximum number of records for SQL logs. |
| -[-]cnf `<[[hh:]mm:]ss>` | When time is specified, creates a new file when the specified time has elapsed. When time is not specified, creates a new file when the maximum size is exceeded. |
| -y | Answers yes to all questions without prompting. |
| -ct `<perf|system|cycle>` | Specifies the Event Trace Session clock type. |
| -ln `<logger_name>` | Specifies the logger name for Event Trace Sessions. |
| -ft `<[[hh:]mm:]ss>` | Specifies the Event Trace Session flush timer. |
| -[-]p `<provider [flags [level]]>` | Specifies a single Event Trace provider to enable. |
| -pf `<filename>` | Specifies a file listing multiple Event Trace providers to enable. The file should be a text file containing one provider per line. |
| -[-]rt | Runs the Event Trace Session in real-time mode. |
| -[-]ul | Runs the Event Trace Session in user. |
| -bs `<value>` | Specifies the Event Trace Session buffer size in kb. |
| -nb `<min max>` | Specifies the number of Event Trace Session buffers. |
| -mode `<globalsequence|localsequence|pagedmemory>` | Specifies the event trace session logger mode, including:<br>- **Globalsequence** - Specifies that the event tracer add a sequence number to every event it receives irrespective of which trace session received the event.<br>- **Localsequence** - Specifies that the event tracer add sequence numbers for events received at a specific trace session. When this option is used, duplicate sequence numbers can exist across all sessions but will be unique within each trace session.<br>- **Pagedmemory** - Specifies that the event tracer use paged memory rather than the default non-paged memory pool for its internal buffer allocations. |
| /? | Displays context-sensitive help. |

#### Remarks

- Where [-] is listed, adding an extra hyphen (-) negates the option.

### Examples

To update an existing event trace data collector called *trace\_log*, changing the maximum log size to 10 MB, updating the log file format to CSV, and appending file versioning in the format mmddhhmm, type:

```
logman update trace trace_log -max 10 -f csv -v mmddhhmm
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [logman create trace command](logman-create-trace)
- [logman command](logman)