---
layout: Conceptual
title: netsh wlan | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/netsh-wlan
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: The netsh wlan command manages, configures, and helps troubleshoot wireless networking settings in Windows.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2025-10-08T00:00:00.0000000Z
locale: en-us
document_id: 0721d238-40fa-485b-b523-f19bc222974a
document_version_independent_id: 0721d238-40fa-485b-b523-f19bc222974a
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/netsh-wlan.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/netsh-wlan
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/netsh-wlan.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 4b9229ec-f0c5-7ea6-9579-4a5e9433a5d6
---

# netsh wlan | Microsoft Learn

The `netsh wlan` command enables administrators to configure, manage, and troubleshoot wireless networking on Windows. It offers subcommands for connecting to Wi-Fi networks, managing wireless profiles, filtering SSIDs, exporting settings, and diagnosing connectivity problems.

## Syntax

```
netsh wlan [add | connect | delete | disconnect | dump | export | help | IHV | refresh | reportissues | set | show | start | stop | ?]
```

```
netsh wlan add filter [permission=]allow|block|denyall [ssid=]<string> [networktype=]infrastructure|adhoc
netsh wlan add profile [filename=]<string> [interface=]<string> [user=]all|current
```

```
netsh wlan connect [name=]<string> [ssid=]<string> [interface=]<string>
```

```
netsh wlan delete filter [permission=]allow|block|denyall [ssid=]<string> [networktype=]infrastructure|adhoc
netsh wlan delete profile [name=]<string> [[interface=]<string>]
```

```
netsh wlan disconnect [interface=]<string>
```

```
netsh wlan dump
```

```
netsh wlan export <hostednetworkprofile>
netsh wlan export profile [name=]<string> [folder=]<string> [[interface=]<string>] [key=<string>]
```

```
netsh wlan IHV <startlogging> <stoplogging>
```

```
netsh wlan refresh hostednetwork [data=]key
```

```
netsh wlan reportissues
```

```
netsh wlan set allowexplicitcreds [allow=]yes|no
netsh wlan set autoconfig [enabled=]yes|no [interface=]<string>
netsh wlan set blockednetworks [display=]show|hide
netsh wlan set blockperiod [value=]0-60
netsh wlan set createalluserprofile [enabled=]yes|no
netsh wlan set hostednetwork [mode=]allow|disallow [ssid=]<ssid> [key=]<passphrase> [keyUsage=]persistent|temporary
netsh wlan set profileorder [name=]<string> [interface=]<string> [priority=]<integer>
netsh wlan set profileparameter [name=]<string> [interface=]<string> [SSIDname=]<string> [ConnectionType=]ESS|IBSS
                                [autoSwitch=yes|no] [ConnectionMode=auto|manual] [nonBroadcast=yes|no]
                                [Randomization=]yes|no|daily [authentication=]open|shared|WPA|WPA2|WPAPSK|WPA2PSK
                                [encryption=]none|WEP|TKIP|AES [keyType=]networkKey|passphrase [keyIndex=]1-4
                                [keyMaterial=<string>] [PMKCacheMode=]yes|no [PMKCacheSize=]1-255 [PMKCacheTTL=300-86400]
                                [preAuthMode=]yes|no [preAuthThrottle=]1-16 [FIPS=]yes|no [useOneX=]yes|no
                                [authMode=]machineOrUser|machineOnly|userOnly|guest [ssoMode=]preLogon|postLogon|none
                                [maxDelay=]1-120 [allowDialog=]yes|no [userVLAN=]yes|no [heldPeriod=]1-3600
                                [AuthPeriod=1-3600] [StartPeriod=]1-3600 [maxStart=]1-100 [maxAuthFailures=]1-100
                                [cacheUserData=]yes|no [cost=]default|unrestricted|fixed|variable
netsh wlan set profiletype [name=]<string> [profiletype=]all|current [interface=]<string>
netsh wlan set randomization [enabled=]yes|no [interface=]<string>
netsh wlan set tracing [mode=]yes|no|persistent
```

```
netsh wlan show all
netsh wlan show allowexplicitcreds
netsh wlan show autoconfig
netsh wlan show blockednetworks
netsh wlan show createalluserprofile
netsh wlan show drivers
netsh wlan show filters
netsh wlan show hostednetwork
netsh wlan show interfaces
netsh wlan show networks
netsh wlan show onlyUseGPProfilesforAllowedNetworks
netsh wlan show profiles
netsh wlan show randomization
netsh wlan show settings
netsh wlan show tracing
netsh wlan show wirelesscapabilities
netsh wlan show wlanreport
```

```
netsh wlan start hostednetwork
```

```
netsh wlan stop hostednetwork
```

## Parameters

| Command | Description |
| --- | --- |
| wlan `add` | `filter` - Adds a wireless network into either the wireless network *allowed* or *disallowed* list. The parameter `ssid` is required if the permission is set to `allow` or `block`. If `denyall` is set, `ssid` isn't required. `permission` - Sets the permission type of the filter.  - `allow` - `block` - `denyall``ssid` - The SSID of the wireless network. `networktype` - The network type of the wireless network.  - `infrastructure` - `adhoc``profile` - Adds a WLAN profile to the specified network interface:  - `filename` (required): Specifies the XML file containing the profile data.  - `interface` (optional): The name of the wireless interface, as listed by the `show interface` command. If provided, the profile is added only to the specified interface; otherwise, it's added to all wireless interfaces.  - `user` (optional): Determines whether the profile applies to all (`all`) users or only the current (`current`) user. By default, the profile is applied to all users. |
| wlan `connect` | Connects to a wireless network using the specified profile. If more than one network interface is available, you must specify which interface to use, otherwise the interface parameter can be omitted.  The profile name is required, while the Service Set Identifier (SSID) is optional. If the profile contains only one SSID, it's used automatically. If multiple SSIDs exist in the profile, you must specify the SSID.  When you specify an interface, wildcard names aren't supported. If the chosen interface is already connected to a wireless network, the command disconnects from the current network before attempting to connect to the new one. If the current and target networks are the same, the command returns success without making changes. `ssid`: Specifies the SSID of the wireless network. `name`: Specifies the profile name to use for the connection attempt. `interface`: Specifies the interface name from which the connection is attempted. |
| wlan `delete` | `filter` - Removes a wireless network from the wireless network *allowed* or *disallowed* list. The parameter `ssid` is required if the permission is set to `allow` or `block`. If `denyall` is set, `ssid` isn't required. `permission` - Sets the permission type of the filter.  - `allow` - `block` - `denyall``ssid` - The SSID of the wireless network. `networktype` - The network type of the wireless network.  - `infrastructure` - `adhoc``profile` - Removes a WLAN profile from the specified network interface:  - `name` (required): Specifies the name of the profile to remove. The profile name can have wildcard characters and multiple profiles with the matching name is removed.  - `interface` (optional): The name of the wireless interface, as listed by the `show interface` command. If provided, the profile is removed only from the specified interface; otherwise, it's removed from all wireless interfaces. |
| wlan `disconnect` | Disconnects the device from the wireless network on the specified interface. The `interface=` parameter is required if there are two or more available interfaces on the device. Wildcard characters can be used to specify multiple interfaces. |
| wlan `dump` | Creates a script containing the current context configuration. The script can be saved to a file and used to restore settings if they're altered or need to be replicated on another system. |
| wlan `export` | Exports selected WLAN profiles to XML files in the specified folder. Each exported profile is saved as "Interface Name-Profile Name.xml". `hostednetworkprofile` - Exports the hosted network profile to an XML file. `profile` - Exports the specified profiles to an XML file. Options are:  - `name`: Specifies the profile name to export.  - `folder`: Specifies the destination folder for the exported profile XML files.  - `interface`: Specifies the network interface associated with the profile.  - `key`: To display the security key in plain text, use `key=clear`.  The `folder`, `name`, and `interface` parameters are optional.  - If `name` is specified, only that profile is exported; otherwise, all profiles are exported.  - If `folder` is provided, it must be an existing, accessible local folder (absolute or relative path). **"."** refers to the current directory, and **".."** to its parent. UNC paths aren't supported. By default, profiles are saved in the current directory.  - If `interface` is specified, only the profile on that interface is exported; otherwise, all profiles with the given name are exported.  - If the `key` parameter is set to plain text and the caller is a local administrator, the XML file includes the key in plain text. Otherwise, the key is encrypted in the output file. |
| wlan `IHV` | `startlogging` - Starts verbose logging for Wi-Fi Independent Hardware Vendor (IHV) events. `stoplogging` - Stops verbose logging for Wi-Fi IHV events. |
| wlan `refresh` | Refreshes the settings of the hosted wireless network. `data` - Instructs the WLAN service to update the hosted network with a new security key. |
| wlan `reportissues` | Generates a WLAN smart trace report to help diagnosing and reporting wireless network issues. |
| wlan `set allowexplicitcreds` | `allow` - Enables (`yes`) or disables (`no`) the use of explicit credentials for WLAN connections. This parameter is required. |
| wlan `set autoconfig` | `enabled` - Turns WLAN auto-configuration to on (`yes`) or off (`no`). `interface` - Specifies the wireless network interface to configure.  If `enabled=no` is set, then Windows doesn't connect to any wireless network automatically from the specified interface. |
| wlan `set blockednetworks` | `display` - Shows (`show`) or hides (`hide`) blocked wireless networks in the network list. If `display=hide` is set, blocked networks aren't displayed in the list of available wireless networks. |
| wlan `set blockperiod` | `value` - Sets the period (in minutes, `0` to `60`) to block a wireless network after a failed connection attempt. The blocked status is cleared when you manually attempt to connect, when the user session changes, or when the network interface reconnects. |
| wlan `set createalluserprofile` | `enabled` - Allows (`yes`) or disallows (`no`) creation of all-user wireless profiles. This parameter is required. |
| wlan `set hostednetwork` | `mode` - Enables (`allow`) or disables (`disallow`) the hosted network feature. `ssid` - Sets the SSID (network name) for the hosted network. `key` - Specifies the passphrase for the hosted network. The user security key should be a string with 8 to 63 ASCII characters. `keyUsage` - Determines if the key is `persistent` or `temporary`. If `keyUsage` is set to `persistent`, the security key is saved and reused whenever the hosted network is started in the future. If set to `temporary`, the key is used only for the current or next hosted network session and is deleted when the hosted network is stopped. If `keyUsage` isn't specified, the key defaults to `persistent`. |
| wlan `set profileorder` | Sets the preference order of a wireless network profile for a specific interface. All three parameters (`name`, `interface`, and `priority`) are required. Only *User* profiles can have their order changed. Group Policy profiles are read-only and always take precedence over *User* profiles. The `priority` parameter determines the new position of the profile in the preferred *User* profile list. For example, setting `priority=1` moves the profile to the top of the *User* profile list. `name` - Specifies the name of the wireless profile. `interface` - Specifies the wireless network interface to apply the profile order. `priority` - Sets the priority (integer value) of the profile. |
| wlan `profileparameter` | Modifies the specified profile. If the interface is specified, then only the profile on that interface is modified. The `name` parameter is required. At least one other parameter besides the profile name and interface must also be specified. `name`: Specifies the name of the wireless profile. `interface`: Specifies the wireless network interface. `SSIDname`: Specifies the SSID for the profile. `ConnectionType` - Specifies whether the network is infrastructure (`ESS`) or ad-hoc (`IBSS`). `ConnectionMode` - Sets the connection mode to automatic (`auto`) or manual (`manual`). Must be set to `manual` for ad-hoc (`IBSS`) networks. `autoSwitch` - Determines if the device automatically switches to a more preferred network when available (`yes` or `no`). `randomization` - Enables (`yes`) or disables (`no`) MAC address randomization for privacy. If `daily` is set, MAC address randomization refreshes every day. `nonBroadcast` - Indicates whether to connect to a hidden (non-broadcast) network (`yes` or `no`). `authentication` - Sets the authentication method used for the connection:  - `open`: No authentication (password) required.  - `shared`: Shared WEP key authentication.  - `WPA` - `WPA2` - `WPAPSK` - `WPA2PSK``encryption` - Specifies the encryption protocol for wireless traffic (`WEP`, `TKIP`, `AES`, or `none`). `keyType` - Defines if the shared key is a `networkkey` or a `passphrase`. `keyIndex` - Selects the key index (`1` to `4`) used for encrypting WEP wireless traffic. The value represents one of four stored WEP keys. `keyMaterial` - Specifies the network key or passphrase. `PMKCacheMode` - Enables (`yes`) or disables (`no`) PMK caching (only for WPA2 networks). `PMKCacheSize` - Sets the number of entries (`1` to `255`) in the PMK cache on the client. `PMKCacheTTL` - Specifies how long in seconds (`300` to `86400`) a PMK cache entry is retained. `preAuthMode` - Enables (`yes`) or disables (`no`) pre-authentication (only for WPA2 networks). `preAuthThrottle` - Sets the number of pre-authentication attempts on neighboring access points from `1` to `16`. `FIPS` - Turns on (`yes`) FIPS mode or off (`no`) for enhanced security compliance. `useOneX` - Enables (`yes`) or disables (`no`) 802.1X authentication. `authMode` - Selects the type of credentials used for authentication (`machineoruser`, `machineonly`, `useronly`, or `guest`). `ssoMode` - Specifies the single sign-on mode to use, if any (`prelogon`, `postlogon`, or `none`). `maxDelay` - Sets the maximum time in seconds allowed to establish a single sign-on connection (`1` to `120`). `allowDialog` - Allows (`allow`) or prevents (`no`) dialog prompts during pre-logon. `userVLAN` - Indicates if the network switches to a different VLAN after user authentication (`yes` or `no`). `heldPeriod` - Sets the interval in seconds (`1` to `3600`) between authentication attempts. `AuthPeriod` - Maximum time in seconds (`1` to `3600`) the client waits for a response from the authenticator. `StartPeriod` - Time in seconds (`1` to `3600`) to wait before sending an EAPOL-Start message. `maxStart` - Maximum number of EAPOL-Start messages sent during authentication from `1` to `100`. `maxAuthFailures` - Maximum number of authentication failures allowed for a set of credentials from `1` to `100`. `cacheUserData` - Enables (`yes`) or disables (`no`) caching of user credentials for future use. `cost` - Sets the cost category for the network profile:  - `default`: Treats Wi-Fi as non-metered unless otherwise specified.  - `unrestricted`: Treats the network as unlimited.  - `fixed`: Marks the network as metered with a fixed data limit.  - `variable`: Marks the network as metered, but assumes the cost or data availability might change (roaming charges or dynamic pricing). |
| wlan `set profiletype` | Changes the profile type for the specified profile. If the interface is specified, then only the profile on that interface is changed. The `name` and `profiletype` parameters are required. `name` - The profile name to be changed. `profiletype` - Specifies the desired profile type using `all` or `current` for a single user. `interface` - Specifies the name of the interface on which the profile is set. |
| wlan `set randomization` | `enabled` - Enables (`yes`) or disables (`no`) MAC address randomization. `interface` - Specifies the wireless network interface.  This command fails if the interface doesn't support randomization or if randomization is blocked by the system admin. Both parameters are required. |
| wlan `set tracing` | `mode` - Enables (`yes`) or disables (`no`) tracing, with the option to make tracing `persistent`. If enabled, trace logs for wireless LAN are collected and saved to the trace files. Under persistent mode, tracing is still in effect after system reboot. If mode is set to disable, then both persistent and non-persistent tracing stops. |
| wlan `show` | Displays the following information: `all` - Provides detailed information about all wireless devices and networks on the system. `allowexplicitcreds` - Displays the current configuration for using explicit user credentials with wireless connections. `autoconfig` - Whether automatic wireless network configuration is enabled or disabled. `blockednetworks` - Displays the current visibility settings for blocked wireless networks. `createalluserprofile` - If users are permitted to create wireless profiles available to all users. `drivers` - Lists properties and details of installed wireless LAN drivers. `filters` - Displays the current lists of allowed and blocked wireless networks. `hostednetwork` - Displays the status and properties of the hosted wireless network. `interfaces` - Lists all wireless LAN interfaces detected on the system. `networks` - Displays all visible wireless networks in range. `onlyUseGPProfilesforAllowedNetworks` - Indicates whether only Group Policy-configured profiles are used for allowed networks. `profiles` - Lists all configured wireless network profiles. `randomization` - Indicates the status of MAC address randomization for wireless connections. `settings` - Displays global configuration settings for wireless LAN. `tracing` - Whether wireless LAN tracing is currently active. `wirelesscapabilities` - Lists the wireless features and capabilities supported by the system. `wlanreport` - Generates a report summarizing recent wireless network sessions and activity. |
| wlan `start hostednetwork` | Starts the WLAN service on the hosted network. |
| wlan `stop hostednetwork` | Stops the WLAN service on the hosted network. |
| `help`*or*`?` | Displays a list of commands and their descriptions in the current context. |

## Examples

To add a Wi-Fi profile filter that only allows connection to a specific network SSID, run the following command:

```cmd
netsh wlan add filter permission=allow ssid="MyNetwork" networktype=infrastructure
```

To connect to a Wi-Fi network named "CorpWiFi" using the interface "Wi-Fi", run the following command:

```cmd
netsh wlan connect name=CorpWiFi interface="Wi-Fi"
```

To disconnect from a Wi-Fi network on the interface "Wi-Fi", run the following command:

```cmd
netsh wlan disconnect interface="Wi-Fi"
```

To export the Wi-Fi profile named "CorpWiFi" to the folder "C:\WiFiProfiles" including the security key, run the following command:

```cmd
netsh wlan export profile name="CorpWiFi" folder="C:\WiFiProfiles" key=clear
```

To start logging IHV events related to WLAN, run the following command:

```cmd
netsh wlan IHV startlogging
```

To refresh the hosted network and update its key or password, run the following command:

```cmd
netsh wlan refresh hostednetwork data=MyKey
```

To set the SSID name to "CorpWiFi\_5G" and the connection mode to auto for the Wi-Fi profile "CorpWiFi" on the interface "Wi-Fi", run the following command:

```cmd
netsh wlan set profileparameter name="CorpWiFi" interface="Wi-Fi" SSIDname="CorpWiFi_5G" ConnectionMode=auto
```

To set the profile type for all profiles on the Wi-Fi profile "CorpWiFi" on the interface "Wi-Fi", run the following command:

```cmd
netsh wlan set profiletype name="CorpWiFi" profiletype=all interface="Wi-Fi"
```

To enable WLAN tracing in persistent mode, run the following command:

```cmd
netsh wlan set tracing mode=persistent
```