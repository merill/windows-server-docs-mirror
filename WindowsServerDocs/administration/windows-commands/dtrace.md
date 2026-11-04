---
layout: Conceptual
title: DTrace | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/dtrace
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: DTrace is a dynamic tracing framework that allows users to monitor and debug system performance for Windows and other operating systems.
ms.topic: reference
author: robinharwood
ms.author: roharwoo
ms.date: 2024-04-18T00:00:00.0000000Z
locale: en-us
document_id: 5fd04cdd-b811-d1d0-7623-a84e704a7634
document_version_independent_id: 5fd04cdd-b811-d1d0-7623-a84e704a7634
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/dtrace.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/dtrace
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/dtrace.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
- https://authoring-docs-microsoft.poolparty.biz/devrel/540ac133-a371-4dbb-8f94-28d6cc77a70b
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
- https://authoring-docs-microsoft.poolparty.biz/devrel/60bfc045-f127-4841-9d00-ea35495a5800
platformId: 2ef897f1-16bb-cc2b-2dc2-0c2bce8d464e
---

# DTrace | Microsoft Learn

Beginning with Windows Server 2025, `dtrace` is included as a built-in tool. DTrace is a command-line utility that allows users to monitor and debug their system performance in real-time. With `dtrace`, users can dynamically instrument the kernel and user-space code without modifying the code itself.

This powerful tool supports various data collection and analysis techniques, including aggregations, histograms, and tracing of user-level events. Probes can be specified in `dtrace` scripts where the script defines the probes to be monitored and the actions to be taken when the probes fire. A probe is a specific point in the code where data can be collected to perform these actions.

Note

This built-in port of `dtrace` differs from the MSI installer of DTrace for Windows surrounding parameters and other capabilities. To learn more about DTrace for Windows, see [DTrace on Windows](/en-us/windows-hardware/drivers/devtest/dtrace).

For a comprehensive guide on using DTrace, see the [Dynamic Tracing Guide](https://illumos.org/books/dtrace/bookinfo.html).

## Enable DTrace

Before `dtrace` can be used, it must first be enabled. To enable `dtrace`, open an elevated command prompt or PowerShell as admin and run:

```
bcdedit /set dtrace on
```

A reboot is required for this change to take effect.

## Syntax

```
dtrace [-BCeFhlqSvVwYZ] [-b bufsz] [-c cmd] [-D name[=def]] [-I path]
[-L path] [-o output] [-p pid] [-s script] [-U name] [-x opt[=val]] [-X a|c|s|t]
[-y symbol path]

[-P provider [[ predicate ] action ]] [-m [ provider: ]
module [[ predicate ] action ]] [-f [[ provider: ] module: ]
func [[ predicate ] action ]] [-n [[[ provider: ] module: ] func: ]
name [[ predicate ] action ]] [-i probe-id [[ predicate ] action ]] [ args ... ]
```

Note

The parameters for dtrace.exe are *case-sensitive*. Make sure to use the correct casing when specifying parameters to avoid any unexpected behavior.

| Parameter | Description |
| --- | --- |
| -b `<bufsz>` | Sets the size of the buffer used to store trace data, where *bufsz* is the desired size of the buffer in bytes, kilobytes (**k**), megabytes (**m**), or gigabytes (**g**). |
| -c `<cmd>` | Runs the specified command and exits once it completes, where *cmd* is the command that you want to run before starting the trace. If more than one instance of **-c** is used, dtrace exits when all commands finish running and reports the exit status for each child process. |
| -C | Runs the ucpp preprocessor on script files before running the trace. |
| -D `<name>`=`<def>` | Defines a symbol when invoking the preprocessor, where *name* is the name of the symbol to define, and *def* is an optional value to assign to the symbol. |
| -e | Exits after compiling a request but before enabling probes. |
| -f | Enables or lists probes that match the specified function name. |
| -F | Combines the trace output by function, making it easier to analyze. |
| -h | Generates a header file with definitions for static probes. |
| -i `<probe-id>` | Enables or lists probes that match the specified probe ID, where *probe-id* is the identifier for the probe to be traced. |
| -I `<path>` | Adds the specified directory to the preprocessor search path, where *path* is the directory that you want to add that contain the *#include* files. |
| -l | Lists probes that match specified criteria based on the **-P**, **-m**, **-f**, **-n**, **-i**, and **-s** parameters. If these parameters aren't specified, all probes are listed. |
| -L `<path>` | Adds the specified directory to the library search path, where *path* is the library directory that you want to add that contain common definitions. |
| -m | Enables or lists probes that match the specified module name in an argument using the format *provider:module* or *module*. If qualifiers aren't specified besides the module name, all probes with that module name are matched. |
| -n | Enables or lists probes that match the specified probe name in an argument using the format *provider:module:function:name*, *module:function:name*, *function:name*, or *name*. If qualifiers aren't specified besides the probe name, all probes with that name are matched. |
| -o `<output>` | Sets the output file for the trace data, where *output* is the name of the file that you want to use for the trace data. |
| -p `<pid>` | Grabs the specified process-ID (PID) and caches its symbol tables, which can be used to analyze the program's behavior. |
| -P `<provider>` | Enables or lists probes that match the specified provider name, where *provider* is the name of the provider. More than one instance of the **-P** parameter can be used at the same time. |
| -q | Sets quiet mode, which only outputs explicitly traced data. |
| -s `<script>` | Enables or lists probes according to the specified D script, where *script* is the name of the script that you want to run. If **-e** is specified, the program is compiled but no data collection is performed. If **-l** is specified, the program is compiled and the list of probes matched are displayed, but no data collection is performed. If **-e** or **-l** aren't specified, the program is compiled, data collection is performed according to the probes specified and tracing begins. |
| -S | Prints the D-language compiler intermediate code for debugging to *stderr*. |
| -U `<name>` | Undefines a symbol when invoking the preprocessor, where *name* is the name of the symbol that you want to undefine. |
| -v | Sets verbose mode, which reports stability attributes and arguments. |
| -V | Displays the version of the dtrace API. |
| -w | Permits destructive actions when specified with the **-s**, **-P**, **-m**, **-f**, **-n**, or **-i** parameters. Destructive actions can include actions such as modifying kernel variables, changing the behavior of system calls, or crashing the system. |
| -x `<opt>`=`<val>` | Enables or modifies the compiler and tracing options, where *opt* is the name of the option that you want to enable or modify, and *val* is an optional value. |
| -X `<a|c|s|t>` | Controls how strict the C code being compiled adheres to the ISO C standard when invoking the cpp. The available arguments are: <br>- `-Xa` (default): provides ISO C plus K&R compatibility extensions with semantic changes required by ISO C. The predefined macro \_\_STDC\_\_ has a value of **0** when cpp is invoked.<br>- `-Xc` (conformance): Provides a strict conformant of ISO C without K&R C compatibility extensions. The predefined macro \_\_STDC\_\_ has a value of **1** when cpp is invoked.<br>- `-Xs` (K&R C): Provides K&R C only, and the \_\_STDC\_\_ macro isn't defined when cpp is invoked.<br>- `-Xt` (transition): Provides ISO C plus K&R C compatibility extensions without semantic changes required by ISO C. The predefined macro \_\_STDC\_\_ has a value of **0** when cpp is invoked. |
| -y `<symbol path>` | Sets the symbol search path for the dtrace script to resolve, where *symbol path* is the path to the shared library or directory that contains the symbols. To learn more, see [Symbol Paths](/en-us/windows/win32/debug/symbol-paths). |
| -Y | Uses the **default** symbol search path for the dtrace script. |
| -Z | Permits probe descriptions that match zero probes for debugging. |

The following list describes the remaining descriptions:

- **Predicate**: The predicate is enclosed in forward slashes (`/ /`) and is a D-expression, which is a boolean expression that can reference variables, constants, and functions. Predicates can be used to filter the output of `dtrace` based on these events. This expression is evaluated each time a probe fires. If the predicate evaluates to true, the associated action is executed.
- **Action**: The action is enclosed in curly braces (`{ }`) and is a set of D-language statements that are executed when a probe fires and its associated predicate, if any, evaluates to true. Actions can be used to print output statements, record data, or perform other operations, such as sending a signal or modifying a variable.
- **Module**: A component of a provider that contains a set of related probes. Modules can be specified in `dtrace` scripts to limit the scope of the script to a specific module or set of modules.
- **Func**: A function name that is associated with a probe. For example, the `syscall::NtReadFile` probe is associated with the `read` function. Functions can be specified in `dtrace` scripts to limit the scope of the script to a specific function or set of functions.
- **Args**: The arguments that are passed to the action expression when a probe fires and its associated predicate, if any, evaluates to true. Args can be used to capture data from the probe context, such as the values of function arguments or system call return values. Args can also be used to pass data between probes or to modify the behavior of the script.

## Examples

To trace all system calls, print the name of the executable and the name of the system call being made, run:

```cmd
dtrace -n 'syscall:::entry { printf("%s called syscall %s", execname, probefunc); }'
```

This command traces the "function\_name" function in the process with the specified PID and prints the name of the function, the PID of the process calling it, and the name of the executable.

```cmd
dtrace -n 'pid$target::function_name:entry { printf("Function %s called by process %d (%s)", probefunc, pid, execname); }' -p <PID>
```

For further examples on using `dtrace`, see [Getting started with DTrace - One line commands](/en-us/windows-hardware/drivers/devtest/dtrace#getting-started-with-dtrace---one-line-commands).