---
layout: Conceptual
title: sc.exe create | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/sc-create
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the sc.exe create command, which creates a subkey and entries for a service in the registry and in the Service Control Manager database.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2023-09-29T00:00:00.0000000Z
ms.custom: sfi-ropc-nochange
locale: en-us
document_id: 582a188c-bf96-b9c5-50fc-2dacade5fba0
document_version_independent_id: 2f25595f-9d0e-a533-2dac-7c6495c94511
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/sc-create.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/sc-create
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/sc-create.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: c7ce441d-51d9-7642-29b5-6e83f0c81363
---

# sc.exe create | Microsoft Learn

Creates a subkey and entries for a service in the registry and in the Service Control Manager database.

## Syntax

```
sc.exe [<servername>] create [<servicename>] [type= {own | share | kernel | filesys | rec | interact type= {own | share}}] [start= {boot | system | auto | demand | disabled | delayed-auto}] [error= {normal | severe | critical | ignore}] [binpath= <binarypathname>] [group= <loadordergroup>] [tag= {yes | no}] [depend= <dependencies>] [obj= {<accountname> | <objectname>}] [displayname= <displayname>] [password= <password>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<servername>` | Specifies the name of the remote server on which the service is located. The name must use the Universal Naming Convention (UNC) format (for example, \myserver). To run SC.exe locally, don't use this parameter. |
| `<servicename>` | Specifies the service name returned by the **getkeyname** operation. |
| `type= {own | share | kernel | filesys | rec | interact type= {own | share}}` | Specifies the service type. The options include:<br>- **own** - Specifies a service that runs in its own process. It doesn't share an executable file with other services. This is the default value.<br>- **share** - Specifies a service that runs as a shared process. It shares an executable file with other services.<br>- **kernel** - Specifies a driver.<br>- **filesys** - Specifies a file system driver.<br>- **rec** - Specifies a file system-recognized driver that identifies file systems used on the computer.<br>- **interact** - Specifies a service that can interact with the desktop, receiving input from users. Interactive services must be run under the LocalSystem account. This type must be used in conjunction with **type= own** or **type= share** (for example, **type= interact** **type= own**). Using **type= interact** by itself will generate an error. |
| `start= {boot | system | auto | demand | disabled | delayed-auto}` | Specifies the start type for the service. The options include:<br>- **boot** - Specifies a device driver that is loaded by the boot loader.<br>- **system** - Specifies a device driver that is started during kernel initialization.<br>- **auto** - Specifies a service that automatically starts each time the computer is restarted and runs even if no one logs on to the computer.<br>- **demand** - Specifies a service that must be started manually. This is the default value if **start=** is not specified.<br>- **disabled** - Specifies a service that cannot be started. To start a disabled service, change the start type to some other value.<br>- **delayed-auto** - Specifies a service that starts automatically a short time after other auto services are started. |
| `error= {normal | severe | critical | ignore}` | Specifies the severity of the error if the service fails to start when the computer is started. The options include:<br>- **normal** - Specifies that the error is logged and a message box is displayed, informing the user that a service has failed to start. Startup will continue. This is the default setting.<br>- **severe** - Specifies that the error is logged (if possible). The computer attempts to restart with the last-known good configuration. This could result in the computer being able to restart, but the service may still be unable to run.<br>- **critical** - Specifies that the error is logged (if possible). The computer attempts to restart with the last-known good configuration. If the last-known good configuration fails, startup also fails, and the boot process halts with a Stop error.<br>- **ignore** - Specifies that the error is logged and startup continues. No notification is given to the user beyond recording the error in the Event Log. |
| `binpath= <binarypathname>` | Specifies a path to the service binary file. There is no default for **binpath=**, and this string must be supplied. |
| `group= <loadordergroup>` | Specifies the name of the group of which this service is a member. The list of groups is stored in the registry, in the **HKLM\System\CurrentControlSet\Control\ServiceGroupOrder** subkey. The default value is null. |
| `tag= {yes | no}` | Specifies whether or not to obtain a TagID from the CreateService call. Tags are used only for boot-start and system-start drivers. |
| `depend= <dependencies>` | Specifies the names of services or groups that must start before this service. The names are separated by forward slashes (/). |
| `obj= {<accountname> | <objectname>}` | Specifies a name of an account in which a service will run, or specifies a name of the Windows driver object in which the driver will run. The default setting is **LocalSystem**. |
| `displayname= <displayname>` | Specifies a friendly name for identifying the service in user interface programs. For example, the subkey name of one particular service is **wuauserv**, which has a more friendly display name of Automatic Updates. |
| `password= <password>` | Specifies a password. This is required if an account other than the LocalSystem account is used. |
| /? | Displays help at the command prompt. |

#### Remarks

- Each command-line option (parameter) must include the equal sign as part of the option name.
- A space is required between an option and its value (for example, **type= own**. If the space is omitted, the operation fails.

## Examples

To create and register a new binary path for the *NewService* service, type:

```
sc.exe \\myserver create NewService binpath= c:\windows\system32\NewServ.exe
```

```
sc.exe create NewService binpath= c:\windows\system32\NewServ.exe type= share start= auto depend= +TDI NetBIOS
```

To learn more about the `sc.exe` command, see [SC commands](/en-us/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/cc754599%28v=ws.11%29).

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)