---
layout: Conceptual
title: if | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/if
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the if command, which performs conditional processing in batch programs.
ms.topic: reference
author: robinharwood
ms.author: roharwoo
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: c179cec0-fc0c-2f8e-8b15-cd23b46e58dd
document_version_independent_id: 7d9137c1-5db0-c8ec-419c-ac4540433438
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/if.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/if
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/if.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/86a4b315-a9f1-4577-b985-6fb0e0e67420
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/96ac410d-d052-4707-8007-df31dd0fe041
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: be6c8c98-937d-27c0-7d50-3d6a0d28c7ac
---

# if | Microsoft Learn

Performs conditional processing in batch programs.

## Syntax

```
if [not] ERRORLEVEL <number> <command> [else <expression>]
if [not] <string1>==<string2> <command> [else <expression>]
if [not] exist <filename> <command> [else <expression>]
```

If command extensions are enabled, use the following syntax:

```
if [/i] <string1> <compareop> <string2> <command> [else <expression>]
if cmdextversion <number> <command> [else <expression>]
if defined <variable> <command> [else <expression>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| not | Specifies that the command should be carried out only if the condition is false. |
| errorlevel `<number>` | Specifies a true condition only if the previous program run by Cmd.exe returned an exit code equal to or greater than *number*. |
| `<command>` | Specifies the command that should be carried out if the preceding condition is met. |
| `<string1>==<string2>` | Specifies a true condition only if *string1* and *string2* are the same. These values can be literal strings or batch variables (for example, `%1`). You do not need to enclose literal strings in quotation marks. |
| exist `<filename>` | Specifies a true condition if the specified file name exists. |
| `<compareop>` | Specifies a three-letter comparison operator, including:<br>- **EQU** - Equal to<br>- **NEQ** - Not equal to<br>- **LSS** - Less than<br>- **LEQ** - Less than or equal to<br>- **GTR** - Greater than<br>- **GEQ** - Greater than or equal to |
| /i | Forces string comparisons to ignore case. You can use **/i** on the `string1==string2` form of **if**. These comparisons are generic, in that if both *string1* and *string2* are comprised of numeric digits only, the strings are converted to numbers and a numeric comparison is performed. |
| cmdextversion `<number>` | Specifies a true condition only if the internal version number associated with the command extensions feature of Cmd.exe is equal to or greater than the number specified. The first version is 1. It increases by increments of one when significant enhancements are added to the command extensions. The **cmdextversion** conditional is never true when command extensions are disabled (by default, command extensions are enabled). |
| defined `<variable>` | Specifies a true condition if *variable* is defined. |
| `<expression>` | Specifies a command-line command and any parameters to be passed to the command in an **else** clause. |
| /? | Displays help at the command prompt. |

#### Remarks

- If the condition specified in an **if** clause is true, the command that follows the condition is carried out. If the condition is false, the command in the **if** clause is ignored and the command executes any command that is specified in the **else** clause.
- When a program stops, it returns an exit code. To use exit codes as conditions, use the **errorlevel** parameter.
- If you use **defined**, the following three variables are added to the environment: **%errorlevel%**, **%cmdcmdline%**, and **%cmdextversion%**.

    - **%errorlevel%**: Expands into a string representation of the current value of the ERRORLEVEL environment variable. This variable assumes that there isn't already an existing environment variable with the name ERRORLEVEL. If there is, you'll get that ERRORLEVEL value instead.
    - **%cmdcmdline%**: Expands into the original command line that was passed to Cmd.exe prior to any processing by Cmd.exe. This assumes that there isn't already an existing environment variable with the name CMDCMDLINE. If there is, you'll get that CMDCMDLINE value instead.
    - **%cmdextversion%**: Expands into the string representation of the current value of **cmdextversion**. This assumes that there isn't already an existing environment variable with the name CMDEXTVERSION. If there is, you'll get that CMDEXTVERSION value instead.
- You must use the **else** clause on the same line as the command after the **if**.

### Examples

To display the message **Cannot find data file if the file Product.dat cannot be found**, type:

```
if not exist product.dat echo Cannot find data file
```

To format a disk in drive A and display an error message if an error occurs during the formatting process, type the following lines in a batch file:

```
:begin
@echo off
format a: /s
if not errorlevel 1 goto end
echo An error occurred during formatting.
:end
echo End of batch program.
```

To delete the file Product.dat from the current directory or display a message if Product.dat is not found, type the following lines in a batch file:

```
IF EXIST Product.dat (
del Product.dat
) ELSE (
echo The Product.dat file is missing.
)
```

Note

These lines can be combined into a single line as follows:

```
IF EXIST Product.dat (del Product.dat) ELSE (echo The Product.dat file is missing.)
```

To echo the value of the ERRORLEVEL environment variable after running a batch file, type the following lines in the batch file:

```
goto answer%errorlevel%
:answer1
echo The program returned error level 1
goto end
:answer0
echo The program returned error level 0
goto end
:end
echo Done!
```

To go to the okay label if the value of the ERRORLEVEL environment variable is less than or equal to 1, type:

```
if %errorlevel% LEQ 1 goto okay
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [goto command](goto)