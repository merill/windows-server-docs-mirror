---
layout: Conceptual
title: netsh lan | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/netsh-lan
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the netsh lan command that manages and configures LAN settings on your Windows-based computer.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2025-07-25T00:00:00.0000000Z
locale: en-us
document_id: eb9f5691-f87d-9cac-5b04-2df35e55e38a
document_version_independent_id: eb9f5691-f87d-9cac-5b04-2df35e55e38a
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/netsh-lan.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/netsh-lan
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/netsh-lan.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/aebdc4a3-c54b-4eea-94e3-663d5e166f57
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/1baec8e6-ab38-4b56-bb59-f6282d94f311
platformId: b95b9d50-68e0-79a1-6510-1d4d1c866597
---

# netsh lan | Microsoft Learn

The `netsh lan` command allows you to manage and configure local area network (LAN) settings on your computer.

## Syntax

```
netsh lan add | delete | dump | export | help | reconnect | set | show | ?
```

```
netsh lan add profile [filename=]<string> [interface=]<string>
netsh lan delete profile [interface=]<string>
netsh lan export profile [folder=]<string> [interface=]<string>
```

```
netsh lan reconnect [interface=]<string>
```

```
netsh lan set autoconfig [enabled=] <yes|no> [interface=] <string>
netsh lan set blockperiod [value=]<0-60>
netsh lan set eapuserdata [filename=]<string> [allusers]<yes|no> [interface=]<string>
```

```
netsh lan set profileparameter [[interface=]<string>]
                               [authMode=]<machineOrUser|machineOnly|userOnly|guest>
                               [ssoMode=]<preLogon|postLogon|none> [maxDelay=]<1-120>
                               [allowDialog=]<yes|no> [userVLAN=]<yes|no>
                               [oneXEnabled=]<yes|no> [oneXEnforced=]<yes|no>
```

```
netsh lan set trace [mode=]<yes|no|persistent>
```

```
netsh lan show interfaces
netsh lan show profiles [interface=]<string>
netsh lan show [settings | tracing]
```

## Parameters

| Command | Description |
| --- | --- |
| add profile `filename=<string>``interface=<string>` | Adds a new profile configuration entry to a table for LAN settings. **filename** - The name of the profile XML file. **interface** - The name of the network interface the profile is added to. |
| delete profile `interface=<string>` | Removes a profile configuration entry from a table for LAN settings. **interface** - The name of the network interface. |
| dump | Displays a script of the current LAN configuration. Can also be exported to a text file. |
| export profile `folder=<string>``interface=<string>` | Exports the LAN profiles as XML files for backup or restore. **folder** - The name of the folder where the profile XML files is saved to. **interface** - The name of the network interface. |
| reconnect `interface=<string>` | Re-establishes a connection on a network interface. If the string value contains spaces, it must be wrapped in double quotes (**" "**). **interface** - The name of the network interface to reconnect to. |
| set allowexplicitcreds `allow=<yes|no>` | Allows or disallows the use of shared user credentials. The `allow` parameter required. |
| set autoconfig `enabled=<yes|no>``interface=<string>` | **enabled** - specifies whether autoconfiguration is set to on or off. **interface** - The name of the network interface.  Both parameters are required. |
| set blockperiod `value=<0-60>` | **value** - Sets the duration, in minutes, where automatic connection attempts to a network are paused. The blocked state is cleared when you manually attempt to connect to a LAN, when a session changes, or when the network media reconnects. |
| set eapuserdata `filename=<string>``allusers=<yes|no>``interface=<string>` | **filename** - Specifies the name of the user data XML file. **allusers** - Specifies whether userdata should be saved for all users or the current user. **interface** - The name of the network interface.  Both `filename` and `allusers` parameters are required. If the interface name isn't specified, the machine userdata is set. |
| set profileparameter `interface=<string>``authMode=<machineOrUser` | `machineOnly` | `userOnly` | `guest>``ssoMode=<preLogon` | `postLogon` | `none>``maxDelay=<1-120>``allowDialog=<yes|no>``userVLAN=<yes|no>``oneXEnabled=<yes|no>``oneXEnforced=<yes|no>` | Configures or modifies LAN profile settings. **interface** - The name of the network interface. **authMode** - The method type used for authenticating credentials. **ssoMode** - The type of single sign-on (SSO) used (if any). **maxDelay** - The timeout value to establish an SSO connection. **allowDialog** - Enables or disables a dialog for prelogon. Prelogon is relevant in scenarios where network authentication is needed before a user logs into the system, such as with 802.1X authentication. **userVLAN** - Specifies whether the network connection can switch to a different Virtual Local Area Network (VLAN) after a user authenticates. **oneXEnabled** - Specifies whether 802.1X authentication is enabled on the network interface. **oneXEnforced** - Specifies if 802.1X authentication is enforced. When enforced, the network interface requires successful 802.1X authentication before allowing network access. |
| set tracing `mode=<yes|no|persistent>` | Specifies if you want to enable or disable logging trace files for the LAN connection for diagnostic purposes. If set to `persistent`, tracing is enabled even after a network adapter is disabled, re-enabled, or a system is rebooted. |
| show `interfaces` | `profiles` | `settings` | `tracing` | Displays the current LAN settings and information. `interfaces` - Displays the local LAN interfaces.`profiles` - Displays all local configured LAN profiles. `settings` - Displays the local global LAN settings. `tracing` - Displays if LAN tracing is enabled or disabled. |
| help or ? | Displays a list of commands and their descriptions in the current context. |

## Remarks

- **add profile**: The `interface` parameter is optional. The filename parameter is required and specifies the XML file that contains the profile data.
- **delete profile**: The `interface` parameter is optional. If you specify an interface, the profile is deleted only from that interface. If no interface is specified, the profile is deleted from the machine profile.
- **export profile**: The `interface` parameter is optional. If an interface name is specified, the profile for that interface is exported as "InterfaceName.xml". If no interface is specified, all profiles are exported, and the machine profile is saved as "MachineProfile.xml".

    The folder name is required and must point to an existing folder accessible from the local computer. You can use an absolute path or a relative path based on the current working directory. The value "." refers to the current directory, while ".." refers to its parent directory. Universal Naming Convention (UNC) paths aren't supported.
- **reconnect**: The `interface` parameter is optional. If an interface name is specified, only that interface reconnects. If no interface is specified, all interfaces reconnect.
- **set profileparameter**: Modifies the profile on specified interface. If the interface is specified, then only profile on that interface is modified. At least one parameter besides `interface` must be specified.

## Examples

To add a new LAN profile from an XML file to a specific interface, run the following command:

```cmd
netsh lan add profile filename="C:\Profiles\MyLANProfile.xml" interface="Ethernet"
```

To re-establish a connection on a network interface, run the following command:

```cmd
netsh lan reconnect interface="Ethernet"
```

To enable autoconfiguration on a network interface, run the following command:

```cmd
netsh lan set autoconfig enabled=yes interface="Ethernet"
```

To configure a LAN profile to use machine-only authentication mode, run the following command:

```cmd
netsh lan set profileparameter interface="Ethernet" authMode=machineOnly
```

To set the block period for automatic connection attempts to 30 minutes, run the following command:

```cmd
netsh lan set blockperiod value=30
```

To save Extensible Authentication Protocol (EAP) user data to an XML file for all users on a specific interface, run the following command:

```cmd
netsh lan set eapuserdata filename="C:\UserData\EAPConfig.xml" allusers=yes interface="Ethernet"
```

To display all the local configured LAN profiles, run the following command:

```cmd
netsh lan show profiles
```