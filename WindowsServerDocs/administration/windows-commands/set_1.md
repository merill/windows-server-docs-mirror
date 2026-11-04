---
layout: Conceptual
title: set | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/set_1
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for set, which displays, sets, or removes cmd.exe environment variables.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2023-09-06T00:00:00.0000000Z
locale: en-us
document_id: beaee6aa-060a-58d2-a474-b47b3ac89f9e
document_version_independent_id: bae22319-b13a-63f8-6da4-6411fece9f91
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/set_1.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/set_1
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/set_1.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/8b896464-3b7d-4e1f-84b0-9bb45aeb5f64
- https://authoring-docs-microsoft.poolparty.biz/devrel/86a4b315-a9f1-4577-b985-6fb0e0e67420
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1d2d671-9549-46e8-918c-24349120dbf5
- https://authoring-docs-microsoft.poolparty.biz/devrel/96ac410d-d052-4707-8007-df31dd0fe041
platformId: fff5f1bb-6723-44c0-669a-7ae9bec90369
---

# set | Microsoft Learn

Displays, sets, or removes cmd.exe environment variables. If used without parameters, **set** displays the current environment variable settings.

Note

This command requires command extensions, which are enabled by default.

The **set** command can also run from the Windows Recovery Console, using different parameters. For more information, see [Windows Recovery Environment (WinRE)](/en-us/windows-hardware/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference).

## Syntax

```
set [<variable>=[<string>]]
set [/p] <variable>=[<promptString>]
set /a <variable>=<expression>
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<variable>` | Specifies the environment variable to set or modify. |
| `<string>` | Specifies the string to associate with the specified environment variable. |
| /p | Sets the value of `<variable>` to a line of input entered by the user. |
| `<promptstring>` | Specifies a message to prompt the user for input. This parameter must be used with the **/p** parameter. |
| /a | Sets `<string>` to a numerical expression that is evaluated. |
| `<expression>` | Specifies a numerical expression. |
| /? | Displays help at the command prompt. |

#### Remarks

- If command extensions are enabled (the default) and you run **set** with a value, it displays all of the variables that begin with that value.
- The characters `<`, `>`, `|`, `&`, and `^` are special command shell characters, and they must be preceded by the escape character (`^`) or enclosed in quotation marks when used in `<string>` (for example, "StringContaining&Symbol"). If you use quotation marks to enclose a string that contains one of the special characters, the quotation marks are set as part of the environment variable value.
- Use environment variables to control the behavior of some batch files and programs and to control the way Windows and the MS-DOS subsystem appears and works. The **set** command is often used in the **Autoexec.nt** file to set environment variables.
- If you use the **set** command without any parameters, the current environment settings are displayed. These settings usually include the **COMSPEC** and **PATH** environment variables, which are used to help find programs on disk. Two other environment variables used by Windows are **PROMPT** and **DIRCMD**.
- If you specify values for `<variable>` and `<string>`, the specified `<variable>` value is added to the environment and `<string>` is associated with that variable. If the variable already exists in the environment, the new string value replaces the old string value.
- If you specify only a variable and an equal sign (without `<string>`) for the **set** command, the `<string>` value associated with the variable is cleared (as if the variable isn't there).
- If you use the **/a** parameter, the following operators are supported, in descending order of precedence:

    | Operator | Operation performed |
    | --- | --- |
    | `( )` | Grouping |
    | `! ~ -` | Unary |
    | `* / %` | Arithmetic |
    | `+ -` | Arithmetic |
    | `<< >>` | Logical shift |
    | `&` | Bitwise AND |
    | `^` | Bitwise exclusive OR |
    | `= *= /= %= += -= &= ^=` | `= <<= >>=` |
    | `,` | Expression separator |
- If you use logical (`&&` or `||`) or modulus (**%**) operators, enclose the expression string in quotation marks. Any non-numeric strings in the expression are considered environment variable names, and their values are converted to numbers before they're processed. If you specify an environment variable name that isn't defined in the current environment, a value of zero is allotted, which allows you to perform arithmetic with environment variable values without using the % to retrieve a value.
- If you run **set /a** from the command line outside of a command script, it displays the final value of the expression.
- Numeric values are decimal numbers unless prefixed by 0x for hexadecimal numbers or 0 for octal numbers. Therefore, 0x12 is the same as 18, which is the same as 022.
- Delayed environment variable expansion support is disabled by default, but you can enable or disable it by using **cmd /v**.
- When creating batch files, you can use **set** to create variables, and then use them in the same way that you would use the numbered variables **%0** through **%9**. You can also use the variables **%0** through **%9** as input for **set**.
- If you call a variable value from a batch file, enclose the value with percent signs (**%**). For example, if your batch program creates an environment variable named *BAUD*, you can use the string associated with *BAUD* as a replaceable parameter by typing **%baud%** at the command prompt.

## Examples

To set the value *TEST^1* for the environment variable named `testVar`, type:

```
set testVar=TEST^^1
```

The **set** command assigns everything that follows the equal sign (=) to the value of the variable. Therefore, if you type `set testVar=TEST^1`, you'll get the following result, `testVar=TEST1`.

To set the value *TEST&1* for the environment variable `testVar`, type:

```
set testVar=TEST^&1
```

To set an environment variable named *include* so the string *c:\directory* is associated with it, type:

```
set include=c:\directory
```

You can then use the string *c:\directory* in batch files by enclosing the name *include* with percent signs (**%**). For example, you can use `dir %include%` in a batch file to display the contents of the directory associated with the *include* environment variable. After this command is processed, the string c:\directory replaces **%include%**.

To use the **set** command in a batch program to add a new directory to the *path* environment variable, type:

```
@echo off
rem ADDPATH.BAT adds a new directory
rem to the path environment variable.
set path=%1;%path%
set
```

To display a list of all of the environment variables that begin with the letter *p*, type:

```
set p
```

To display a list of all of the environment variables on the current device, type:

```
set
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)