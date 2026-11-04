---
layout: Conceptual
title: logman update api | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/logman-update-api
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the logman update api command, which updates the properties of an existing API tracking data collector.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 1fb8b2b2-6f6f-a278-a713-38d0aba579ce
document_version_independent_id: 46a1da61-d0d6-16d2-bff0-7cbee5d1730c
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/logman-update-api.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/logman-update-api
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/logman-update-api.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/6ab7faaf-d791-4a26-96a2-3b11738538e7
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/302e28b0-1f09-4811-9a9b-2a72e0770581
platformId: 4410f921-18bb-eade-0b92-9f5f2fa16b45
---

# logman update api | Microsoft Learn

Updates the properties of an existing API tracing data collector.

## Syntax

```
logman update api <[-n] <name>> [options]
```

### Parameters

| Parameter | Description |
| --- | --- |
| -s `<computer name>` | Performs the command on the specified remote computer. |
| -config `<value>` | Specifies the settings file containing command options. |
| [-n] `<name>` | Name of the target object. |
| -f `<bin|bincirc>` | Specifies the log format for the data collector. |
| -[-]u `<user [password]>` | Specifies the user to Run As. Entering a `*` for the password produces a prompt for the password. The password is not displayed when you type it at the password prompt. |
| -m `<[start] [stop] [[start] [stop] [...]]>` | Changed to manual start or stop instead of a scheduled begin or end time. |
| -rf `<[[hh:]mm:]ss>` | Run the data collector for the specified period of time. |
| -b `<M/d/yyyy h:mm:ss[AM|PM]>` | Begin collecting data at the specified time. |
| -e `<M/d/yyyy h:mm:ss[AM|PM]>` | End data collection at the specified time. |
| -si `<[[hh:]mm:]ss>` | Specifies the sample interval for performance counter data collectors. |
| -o `<path|dsn!log>` | Specifies the output log file or the DSN and log set name in a SQL database. |
| -[-]r | Repeat the data collector daily at the specified begin and end times. |
| -[-]a | Append an existing log file. |
| -[-]ow | Overwrite an existing log file. |
| -[-]v `<nnnnnn|mmddhhmm>` | Attaches file versioning information to the end of the log file name. |
| -[-]rc `<task>` | Run the command specified each time the log is closed. |
| -[-]max `<value>` | Maximum log file size in MB or maximum number of records for SQL logs. |
| -[-]cnf `<[[hh:]mm:]ss>` | When time is specified, creates a new file when the specified time has elapsed. When time is not specified, creates a new file when the maximum size is exceeded. |
| -y | Answer yes to all questions without prompting. |
| -mods `<path [path [...]]>` | Specifies the list of modules to log API calls from. |
| -inapis` <module!api [module!api [...]]>` | Specifies the list of API calls to include in logging. |
| -exapis `<module!api [module!api [...]]>` | Specifies the list of API calls to exclude from logging. |
| -[-]ano | Log (-ano) API names only, or do not log only (-ano) API names. |
| -[-]recursive | Log (-recursive) or do not log (-recursive) APIs recursively beyond the first layer. |
| -exe `<value>` | Specifies the full path to an executable for API Tracing. |
| /? | Displays context-sensitive help. |

#### Remarks

- Where [-] is listed, adding an extra hyphen (-) negates the option.

### Examples

To update an existing API trace counter called *trace\_notepad*, for the executable file c:\windows\notepad.exe, by excluding the API call TlsGetValue produced by the module kernel32.dll, type:

```
logman update api trace_notepad -exe c:\windows\notepad.exe -exapis kernel32.dll!TlsGetValue
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [logman create api command](logman-create-api)
- [logman command](logman)