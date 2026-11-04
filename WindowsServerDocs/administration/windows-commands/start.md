---
layout: Conceptual
title: start | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/start
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the start command, which starts a separate Command Prompt window to run a specified program or command.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2026-04-16T00:00:00.0000000Z
locale: en-us
document_id: a52b78b6-e846-0b32-25c0-f9aab145b112
document_version_independent_id: 0c56bb98-4f1f-dd55-63ae-8bb18535cee1
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/start.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/start
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/start.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/19ec6774-09b8-473e-a17e-b17b518bbad7
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ade36b61-c646-4bd8-87ee-f3a843461962
platformId: 0bd3e6fc-cc51-e22a-41ef-49c66bd67a30
---

# start | Microsoft Learn

Starts a separate Command Prompt window to run a specified program or command.

## Syntax

```
start <"title"> [/d <path>] [/i] [{/min | /max}] [{/separate | /shared}] [{/low | /normal | /high | /realtime | /abovenormal | /belownormal}] [/node <NUMA node>] [/affinity <hexaffinity>] [/wait] [/b] [/machine <x86|amd64|arm|arm64>] [<command> [<parameter>... ] | <program> [<parameter>... ]]
```

Note

The **machine** parameter is currently in PREVIEW for Windows 11 only. The parameter is available beginning with the [Windows 11 Insider Preview Build 22557](https://blogs.windows.com/windows-insider/2022/02/16/announcing-windows-11-insider-preview-build-22557/). This information relates to a prerelease product that may be substantially modified before it's released. Microsoft makes no warranties, expressed or implied, with respect to the information provided here.

### Parameters

| Parameter | Description |
| --- | --- |
| `"title"` | Specifies the title to display in the **Command Prompt** window title bar. |
| /d `<path>` | Specifies the startup directory. |
| /i | Passes the Cmd.exe startup environment to the new **Command Prompt** window. If `/i` isn't specified, the current environment is used. |
| `{/min | /max}` | Specifies to minimize (`/min`) or maximize (`/max`) the new **Command Prompt** window. |
| `{/separate | /shared}` | Starts 16-bit programs in a separate memory space (`/separate`) or shared memory space (**/shared**). These options aren't supported on 64-bit platforms. |
| `{/low | /normal | /high | /realtime | /abovenormal | /belownormal}` | Starts an application in the specified priority class. |
| /node `<NUMA node>` | Leverages memory locality on NUMA (Non-Uniform Memory Architecture) nodes as a decimal integer. Two processes that communicate with each other through shared memory on the preferred NUMA node can minimize memory latencies while allocating memory from the same NUMA node when possible. They're free to run on processors outside the specified node. |
| /affinity `<hexaffinity>` | Applies the specified processor affinity mask (expressed as a hexadecimal number) to the new application. Two programs are able to run on specific processor cores within the same NUMA node. This number can be changed to the processor-specific supported amount without having to change the affinity mask. |
| /wait | Starts an application and waits for it to end. |
| /b | Starts an application without opening a new **Command Prompt** window. CTRL+C handling is ignored unless the application enables CTRL+C processing. Use CTRL+BREAK to interrupt the application. |
| /machine `<x86 | amd64 | arm | arm64>` | Specifies the machine architecture of the application process. |
| `[<command> [<parameter>... ] | <program> [<parameter>... ]]` | Specifies the command or program to start. |
| `<parameter>` | Specifies parameters to pass to either the command or the program. |
| /? | Displays help at the command prompt. |

#### Remarks

- You can run non-executable files through their file association by typing the name of the file as a command. This applies to any file type that has a registered association, including URLs, which are automatically detected and opened in the default browser, and documents such as `.txt` or `.pdf` files, which are opened in their associated application.
- If you run a command that contains the string CMD as the first token without an extension or path qualifier, CMD is replaced with the value of the COMSPEC variable. This prevents users from picking up `cmd` from the current directory.
- If you run a 32-bit graphical user interface (GUI) application, `cmd` doesn't wait for the application to quit before returning to the command prompt. This behavior doesn't occur if you run the application from a command script.
- If you're running on a 64-bit platform, the `/separate` and `/shared` parameters aren't supported.
- If you run a command that uses a first token that isn't a command or the file path to an existing file with an extension, `Cmd.exe` uses the value of the PATHEXT environment variable to determine which extensions to look for and in what order. The default value for the PATHEXT variable is `.COM;.EXE;.BAT;.CMD;.VBS;.VBE;.JS;.JSE;.WSF;.WSH;.MSC`

    Note the syntax is the same as the PATH variable, with semicolons (;) separating each extension.
- **start** searches for a specified executable file, and if found, the executable launches regardless of the current working directory. When searching for an executable file, if there's no match on any extension, **start** checks to see if the name matches a directory name. If it does, **start** opens `Explorer.exe` on that path.

## Examples

To start the *Myapp* program at the command prompt and retain use of the current **Command Prompt** window, type:

```cmd
start Myapp
```

To view the **start** command-line help information in a separate maximized **Command Prompt** window, type:

```cmd
start /max start /?
```

To open a URL in the default browser, type:

```cmd
start "Bing" "https://www.bing.com"
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)