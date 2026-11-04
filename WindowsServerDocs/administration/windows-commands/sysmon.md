---
layout: Conceptual
title: Sysmon in Windows | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/sysmon
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Learn how to use Sysmon, a Windows system service and device driver, to monitor and log system activity to the Windows event log. Explore syntax and examples.
author: robinharwood
ms.author: roharwoo
ms.date: 2026-02-23T00:00:00.0000000Z
ms.topic: reference
locale: en-us
document_id: ac8a97a2-7055-f2c0-72fe-c137282f0266
document_version_independent_id: ac8a97a2-7055-f2c0-72fe-c137282f0266
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/sysmon.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/sysmon
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/sysmon.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: 81ac5fc3-3874-fd5e-04c6-bef079e58b37
---

# Sysmon in Windows | Microsoft Learn

System Monitor (Sysmon) is a Windows system service and device driver that you install on a system. It stays resident across system reboots to monitor and log system activity to the Windows event log. It provides detailed information about process creations, network connections, and changes to file creation time.

Tip

Starting February 2026, Sysmon is available as a built-in optional feature for Windows 11. To learn more, see [Sysmon overview](/en-us/windows/security/operating-system-security/sysmon/overview).

Looking for the Sysinternals standalone documentation? See [Sysinternals Sysmon](/en-us/sysinternals/downloads/sysmon).

## Syntax

```cmd
sysmon [-i [<configfile>]] [-c [<configfile>]] [-m] [-s] [-u [force]] [-accepteula]
```

## Parameters

| Parameter | Description |
| --- | --- |
| `-i [<configfile>]` | Installs the service and driver. Optionally includes a configuration file. |
| `-c [<configfile>]` | Updates the configuration of an installed Sysmon driver, or dumps the current configuration if no other argument is provided. Optionally includes a configuration file. |
| `-m` | Installs the event manifest. The service install implicitly does this action. |
| `-s [<schemaversion>]` | Prints the configuration schema definition of the specified version. Specify `all` to dump all schema versions. The default is latest. |
| `-u [force]` | Uninstalls the service and driver. Using `-u force` causes uninstall to proceed even when some components aren't installed. |
| `-accepteula` | Automatically accepts the End User License Agreement (EULA) on installation. |
| `-? config` | Displays more information on configuration files. |

## Remarks

- Event logs are stored in `Applications and Services Logs/Microsoft/Windows/Sysmon/Operational` log.
- The install or uninstall options don't require a reboot.
- To reset the configuration to default settings, use `sysmon -c --`.

## Examples

To install Sysmon with default settings, run the following command:

```cmd
sysmon -accepteula -i
```

To install Sysmon with a configuration file, run the following command:

```cmd
sysmon -accepteula -i c:\windows\config.xml
```

To dump the current configuration, run the following command:

```cmd
sysmon -c
```

To reset the configuration to default settings, run the following command:

```cmd
sysmon -c --
```

To reconfigure Sysmon with a configuration file, run the following command:

```cmd
sysmon -c c:\windows\config.xml
```

To display the configuration schema, run the following command:

```cmd
sysmon -s
```

To display the configuration schema for a specific version, run the following command:

```cmd
sysmon -s 4.50
```

To display all configuration schema versions, run the following command:

```cmd
sysmon -s all
```

To uninstall Sysmon, run the following command:

```cmd
sysmon -u
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)