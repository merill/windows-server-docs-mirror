---
layout: Conceptual
title: prndrvr | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/prndrvr
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the prndrvr command, which adds, deletes, and lists printer drivers.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 3521ea5e-05f4-4415-4946-7776916f0060
document_version_independent_id: db5d5ea1-17c7-1e41-527d-30cd131dae3b
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/prndrvr.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/prndrvr
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/prndrvr.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: f6390b9b-0bb2-bc63-0003-5305009d2bb6
---

# prndrvr | Microsoft Learn

Adds, deletes, and lists printer drivers. This command is a Visual Basic script located in the `%WINdir%\System32\printing_Admin_Scripts\<language>` directory. To use this command at a command prompt, type **cscript** followed by the full path to the prndrvr file, or change directories to the appropriate folder. For example: `cscript %WINdir%\System32\printing_Admin_Scripts\en-US\prndrvr`.

Used without parameters, **prndrvr** displays command-line help.

## Syntax

```
cscript prndrvr {-a | -d | -l | -x | -?} [-m <model>] [-v {0|1|2|3}] [-e <environment>] [-s <Servername>] [-u <Username>] [-w <password>] [-h <path>] [-i <inf file>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| -a | Installs a driver. |
| -d | Deletes a driver. |
| -l | Lists all printer drivers installed on the server specified by the **-s** parameter. If you don't specify a server, Windows lists the printer drivers installed on the local computer. |
| -x | Deletes all printer drivers and additional printer drivers not in use by a logical printer on the server specified by the **-s** parameter. If you don't specify a server to remove from the list, Windows deletes all unused printer drivers on the local computer. |
| -m `<model_name>` | Specifies (by name) the driver you want to install. Drivers are often named for the model of printer they support. See the printer documentation for more information. |
| `-v {0|1|2|3}` | Specifies the version of the driver you want to install. See the description of the **-e**parameter for information on which versions are available for which environment. If you don't specify a version, the version of the driver appropriate for the version of Windows running on the computer where you are installing the driver is installed. |
| -e `<environment>` | Specifies the environment for the driver you want to install. If you don't specify an environment, the environment of the computer where you are installing the driver is used. The supported environment parameters are: **Windows NT x86**, **Windows x64** or **Windows IA64**. |
| -s `<Servername>` | Specifies the name of the remote computer that hosts the printer that you want to manage. If you don't specify a computer, the local computer is used. |
| -u `<Username>` -w `<password>` | Specifies an account with permissions to connect to the computer that hosts the printer that you want to manage. All members of the target computer's local Administrators group have these permissions, but the permissions can also be granted to other users. If you don't specify an account, you must be logged on under an account with these permissions for the command to work. |
| -h `<path>` | Specifies the path to the driver file. If you don't specify a path, the path to the location where Windows was installed is used. |
| -i `<filename.inf>` | Specifies the complete path and file name for the driver you want to install. If you don't specify a file name, the script uses one of the inbox printer .inf files in the inf subdirectory of the Windows directory.<br>if the driver path is not specified, the script searches for driver files in the driver.cab file. |
| /? | Displays help at the command prompt. |

#### Remarks

- If the information that you supply contains spaces, use quotation marks around the text (for example, "Computer Name").
- The **-x** parameter deletes all additional printer drivers (drivers installed for use on clients running alternate versions of Windows), even if the primary driver is in use. If the fax component is installed, this option also deletes fax drivers. The primary fax driver is deleted if it is not in use (that is, if there is no queue using it). If the primary fax driver is deleted, the only way to re-enable fax is to reinstall the fax component.

### Examples

To list all drivers on the local \printServer1 server, type:

```
cscript prndrvr -l -s
```

To add a version 3 Windows x64 printer driver for the Laser printer model 1 model of printer using the c:\temp\Laserprinter1.inf driver information file for a driver stored in the c:\temp folder, type:

```
cscript prndrvr -a -m Laser printer model 1 -v 3 -e Windows x64 -i c:\temp\Laserprinter1.inf -h c:\temp
```

To delete a version 3 Windows x64 printer driver for Laser printer model 1, type:

```
cscript prndrvr -a -m Laser printer model 1 -v 3 -e Windows x64
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [Print Command Reference](print-command-reference)