---
layout: Conceptual
title: wdsutil set-server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wdsutil-set-server
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for Subcommand set-Server, which configured the settings for a Windows Deployment Services server.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 86981375-beca-844b-4ba3-0a23af0bdccc
document_version_independent_id: 7ed6ffdb-e027-ca54-70c1-69f6e08773e9
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wdsutil-set-server.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wdsutil-set-server
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wdsutil-set-server.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
platformId: b92ed30a-61c1-768d-d641-723f8c85dc83
---

# wdsutil set-server | Microsoft Learn

Configures the settings for a Windows Deployment Services server.

## Syntax

```
wdsutil [Options] /Set-Server [/Server:<Server name>]
    [/Authorize:{Yes | No}]
    [/RogueDetection:{Yes | No}]
    [/AnswerClients:{All | Known | None}]
    [/Responsedelay:<time in seconds>]
    [/AllowN12forNewClients:{Yes | No}]
    [/ArchitectureDiscovery:{Yes | No}]
    [/resetBootProgram:{Yes | No}]
    [/DefaultX86X64Imagetype:{x86 | x64 | Both}]
    [/UseDhcpPorts:{Yes | No}]
    [/DhcpOption60:{Yes | No}]
    [/RpcPort:<Port number>]
    [/PxepromptPolicy
        [/Known:{OptIn | Noprompt | OptOut}]
        [/New:{OptIn | Noprompt | OptOut}]
    [/BootProgram:<Relative path>]
         /Architecture:{x86 | ia64 | x64}
    [/N12BootProgram:<Relative path>]
         /Architecture:{x86 | ia64 | x64}
    [/BootImage:<Relative path>]
         /Architecture:{x86 | ia64 | x64}
    [/PreferredDC:<DC Name>]
    [/PreferredGC:<GC Name>]
    [/PrestageUsingMAC:{Yes | No}]
    [/NewMachineNamingPolicy:<Policy>]
    [/NewMachineOU]
         [/type:{Serverdomain | Userdomain | UserOU | Custom}]
         [/OU:<Domain name of OU>]
    [/DomainSearchOrder:{GCOnly | DCFirst}]
    [/NewMachineDomainJoin:{Yes | No}]
    [/OSCMenuName:<Name>]
    [/WdsClientLogging]
         [/Enabled:{Yes | No}]
         [/LoggingLevel:{None | Errors | Warnings | Info}]
    [/WdsUnattend]
         [/Policy:{Enabled | Disabled}]
         [/CommandlinePrecedence:{Yes | No}]
         [/File:<path>]
             /Architecture:{x86 | ia64 | x64}
    [/AutoaddPolicy]
         [/Policy:{AdminApproval | Disabled}]
         [/PollInterval:{time in seconds}]
         [/MaxRetry:{Retries}]
         [/Message:<Message>]
         [/RetentionPeriod]
             [/Approved:<time in days>]
             [/Others:<time in days>]
    [/AutoaddSettings]
         /Architecture:{x86 | ia64 | x64}
         [/BootProgram:<Relative path>]
         [/ReferralServer:<Server name>
         [/WdsClientUnattend:<Relative path>]
         [/BootImage:<Relative path>]
         [/User:<Owner>]
         [/JoinRights:{JoinOnly | Full}]
         [/JoinDomain:{Yes | No}]
    [/BindPolicy]
         [/Policy:{Include | Exclude}]
         [/add]
              /address:<IP or MAC address>
              /addresstype:{IP | MAC}
         [/remove]
              /address:<IP or MAC address>
              /addresstype:{IP | MAC}
    [/RefreshPeriod:<time in seconds>]
    [/BannedGuidPolicy]
         [/add]
              /Guid:<GUID>
         [/remove]
             /Guid:<GUID>
    [/BcdRefreshPolicy]
         [/Enabled:{Yes | No}]
         [/RefreshPeriod:<time in minutes>]
    [/Transport]
         [/ObtainIpv4From:{Dhcp | Range}]
             [/start:<start IP address>]
             [/End:<End IP address>]
         [/ObtainIpv6From:Range]
             [/start:<start IP address>]
             [/End:<End IP address>]
         [/startPort:<start Port>
             [/EndPort:<start Port>
        [/Profile:{10Mbps | 100Mbps | 1Gbps | Custom}]
        [/MulticastSessionPolicy]
             [/Policy:{None | AutoDisconnect | Multistream}]
                 [/Threshold:<Speed in KBps>]
                 [/StreamCount:{2 | 3}]
                 [/Fallback:{Yes | No}]
        [/forceNative]
```

### Parameters

| Parameter | Description |
| --- | --- |
| [/Server:&lt;Server name&gt;] | Specifies the name of the server. This can be either the NetBIOS name or the fully qualified domain name (FQDN). If no server name is specified, the local server will be used. |
| [/Authorize:{Yes | No}] | Specifies whether to authorize this server in Dynamic Host Control Protocol (DHCP). |
| [/RogueDetection:{Yes | No}] | Enables or disables DHCP rogue detection. |
| [/AnswerClients:{All | Known | None}] | Specifies which clients this server will answer. If you set this value to **Known**, a computer must be prestaged in active directory Domain Services (AD DS) before it will be answered by the Windows Deployment Services server. |
| [/Responsedelay:&lt;time in seconds&gt;] | The amount of time that the server will wait before answering a booting client. This setting does not apply to prestaged computers. |
| [/AllowN12forNewClients:{Yes | No}] | for Windows Server 2008, specifies that unknown clients will not have to press the F12 key to initiate a network boot. Known clients will receive the boot program specified for the computer or, if not specified, the boot program specified for the architecture.<br>for Windows Server 2008 R2, this option has been replaced with the following command: wdsutil /Set-Server /PxepromptPolicy /New:Noprompt |
| [/ArchitectureDiscovery:{Yes | No}] | Enables or disables architecture discovery. This facilitates the discovery of x64-based clients that do not broadcast their architecture correctly. |
| [/resetBootProgram:{Yes | No}] | Determines whether the boot path will be erased for a client that has just booted without requiring an F12 key press. |
| [/DefaultX86X64Imagetype: {x86 | x64 | Both}] | Controls which boot images will be shown to x64-based clients. |
| [/UseDhcpPorts:{Yes | No}] | Specifies whether or not the PXE server should attempt to bind to the DHCP port, TCP port 67. If DHCP and Windows Deployment Services are running on the same computer, you should set this option to **No** to enable the DHCP server to utilize the port, and set the **/DhcpOption60** parameter to **Yes**. The default setting for this value is **Yes**. |
| [/DhcpOption60:{Yes | No}] | Specifies whether DHCP option 60 should be configured for PXE support. If DHCP and Windows Deployment Services are running on the same server, set this option to **Yes** and set the **/UseDhcpPorts** option to **No**. The default setting for this value is **No**. |
| [/RpcPort:&lt;Port number&gt;] | Specifies the TCP port number to be used to service client requests. |
| [/PxepromptPolicy] | Configures how known (prestaged) and new clients initiate a PXE boot. This option only applies to Windows Server 2008 R2. You set the settings using the following options:<br>- [/Known:{OptIn|OptOut|Noprompt}] - Sets the policy for prestaged clients.- [/New:{OptIn|OptOut|Noprompt}] - Sets the policy for new clients.<br><br>**OptIn** means the client needs to press a key in order to PXE boot, otherwise it will fall back to the next boot device.<br><br>**Noprompt** means the client will always PXE Boot.<br><br>**OptOut** means the client will PXE boot unless the Esc key is pressed. |
| [/BootProgram:&lt;Relative path&gt;] /Architecture:{x86 | ia64 | x64} | Specifies the relative path to the boot program in the remoteInstall folder (for example, **boot\x86\pxeboot.n12**), and specifies the architecture of the boot program. |
| [/N12BootProgram:&lt;Relative path&gt;] /Architecture:{x86 | ia64 | x64} | Specifies the relative path to the boot program that does not require pressing the F12 key (for example, **boot\x86\pxeboot.n12**), and specifies the architecture of the boot program. |
| [/BootImage:&lt;Relative path&gt;] /Architecture:{x86 | ia64 | x64} | Specifies the relative path to the boot image that booting clients should receive, and specifies the architecture of the boot image. You can specify this for each architecture. |
| [/PreferredDC:&lt;DC Name&gt;] | Specifies the name of the domain controller that Windows Deployment Services should use. This can be either the NetBIOS name or the FQDN. |
| [/PreferredGC:&lt;GC Name&gt;] | Specifies the name of the global catalog server that Windows Deployment Services should use. This can be either the NetBIOS name or the FQDN. |
| [/PrestageUsingMAC:{Yes | No}] | Specifies whether Windows Deployment Services, when creating computer accounts in AD DS, should use the MAC address rather than the GUID/UUID to identify the computer. |
| [/NewMachineNamingPolicy:&lt;Policy&gt;] | Specifies the format to use when generating computer names for clients. For information about the format to use for &lt;policy&gt;, right-click the server in the mmc snap-in, click **Properties**, and view the **directory Services** tab. For example, **/NewMachineNamingPolicy: %61Username%#**. |
| [/NewMachineOU] | Used to specify the location in AD DS where client computer accounts will be created. You specify the location using the following options.<br>- [/type: Serverdomain | Userdomain | UserOU | Custom ] Specifies the type of location. **Serverdomain** creates accounts in the same domain as the Windows Deployment Services server. **Userdomain** creates accounts in the same domain as the user performing the installation. **UserOU** creates accounts in the organizational unit of the user performing the installation. **Custom** allows you to specify a custom location (you must also specify a value for **/OU** with this option).- [/OU:&lt;Domain name of OU&gt;] - if you specify **Custom** for the **/type** option, this option specifies the organizational unit where computer accounts should be created. |
| [/DomainSearchOrder:{GCOnly | DCFirst}] | Specifies the policy for searching computer accounts in AD DS (global catalog or domain controller). |
| [/NewMachineDomainJoin:{Yes | No}] | Specifies whether or not a computer that is not already prestaged in AD DS should be joined to the domain during installation. The default setting is **Yes**. |
| [/WdsClientLogging] | Specifies the logging level for the server.<br>- [/Enabled:{Yes | No}] - Enables or disables logging of Windows Deployment Services client actions.- [/LoggingLevel: {None | Errors | Warnings | Info} - Sets the logging level. **None** is equivalent to disabling logging. **Errors** is the lowest level of logging and indicates that only errors will be logged. **Warnings** includes both warnings and errors. **Info** is the highest level of logging and includes errors, warnings, and informational events. |
| [/WdsUnattend] | These settings control the unattended installation behavior of Windows Deployment Services client. You set the settings using the following options:<br>- [/Policy:{Enabled | Disabled}] - Specifies whether or not unattended installation is used.- [/CommandlinePrecedence: {Yes | No}] - Specifies whether an Autounattend.xml file (if present on the client) or an unattended setup file that was passed directly to the Windows Deployment Services client with the /Unattend option will be used instead of an image unattend file during a client installation. The default setting is **No**.- [/File:&lt;Relative path&gt; /Architecture:{x86 | ia64 | x64}] - Specifies the file name, path, and architecture of the unattend file. |
| [/AutoaddPolicy] | These settings control the Auto-add policy. You define the settings using the following options:<br>- [/Policy: {AdminApproval | Disabled}] - **AdminApprove** causes all unknown computers to be added to a pending queue, where the administrator can then review the list of computers and approve or reject each request, as appropriate. **Disabled** indicates that no additional action is taken when an unknown computer attempts to boots to the server.- [/PollInterval:{time in seconds}] - Specifies the interval (in seconds) at which the network boot program should poll the Windows Deployment Services server.- [/MaxRetry: &lt;Number&gt;] - Specifies the number of times the network boot program should poll the Windows Deployment Services server. This value, along with **/PollInterval**, dictates how long the network boot program will wait for an administrator to approve or reject the computer before timing out. For example, a **MaxRetry** value of 10 and a **PollInterval** vlue of 60 would indicate that the client should poll the server 10 times, waiting 60 seconds between tries. Therefore, the client would time out after 10 minutes (10 x 60 seconds = 10 minutes).- [/Message: &lt;Message&gt;] - Specifies the message that is displayed to the client on the network boot program dialog page.- [/RetentionPeriod] - Specifies the number of days a computer can be in a pending state before being automatically purged.- [/Approved: &lt;time in days&gt;] - Specifies the retention period for approved computers. You must use this parameter with the **/RetentionPeriod** option.- [/Others: &lt;time in days&gt;] - Specifies the retention period for unapproved computers (rejected or pending). You must use this parameter with the **/RetentionPeriod** option. |
| [/AutoaddSettings] | Specifies the default settings to be applied to each computer. You define the settings using the following options:<br>- /Architecture: {x86 | ia64 | x64} - Specifies the architecture.- [/BootProgram: &lt;Relative path&gt;] - Specifies the boot program sent to the approved computer. If no boot program is specified, the default for the architecture of the computer (as specified on the server) will be used.- [/WdsClientUnattend: &lt;Relative path&gt;] - Sets the relative path to the unattend file that the approved client should receive.- [/ReferralServer: &lt;Server name&gt;] - Specifies the Windows Deployment Services server that the client will use to download images.- [/BootImage: &lt;Relative path&gt;] - Specifies the boot image that the approved client will receive.- [/User: &lt;Domain\User | User@Domain&gt;] - Sets permissions on the computer account object to give the specified user the necessary rights to join the computer to the domain.- [JoinRights: {JoinOnly | Full}] - Specifies the type of rights to be assigned to the user. **JoinOnly** requires the administrator to reset the computer account before the user can join the computer to the domain. **Full** gives full access to the user, including the right to join the computer to the domain.- [/JoinDomain: {Yes | No}] - Specifies whether or not the computer should be joined to the domain as this computer account during a Windows Deployment Services installation. The default setting is **Yes**. |
| [/BindPolicy] | Configures the network interfaces for the PXE provider to listen on. You define the policy using the following options:<br>- [/Policy: {Include | Exclude}] - Sets the interface bind policy to include or exclude the addresses on the interface list.- [/add] - adds an interface to the list. You must also specify /addresstype and /address.- [/remove] - removes an interface from the list. You must also specify /addresstype and /address.- /address:&lt;IP or MAC address&gt; - Specifies the IP or MAC address of the interface to add or remove.- /addresstype: {IP | MAC} - Indicates the type of address specified in the **/address** option. |
| [/RefreshPeriod: &lt;seconds&gt;] | Specifies how often (in seconds) the server will refreshes its settings. |
| [/BannedGuidPolicy] | Manages the list of banned GUIDs using the following options:<br>- [/add] /Guid:&lt;GUID&gt; - adds the specified GUID to the list of banned GUIDs. Any client with this GUID will be identified by its MAC address instead.- [/remove] /Guid:&lt;GUID&gt; - removes the specified GUID from the list of banned GUIDs. |
| [/BcdRefreshPolicy] | Configures the settings for refreshing Bcd files using the following options:<br>- [/Enabled:{Yes | No}] - Specifies the Bcd refreshing policy. When **/Enabled** is set to **Yes**, Bcd files are refreshed at the specified time interval.- [/RefreshPeriod:&lt;time in minutes&gt;] - Specifies the time interval at which Bcd files are refreshed. |
| [/Transport] | Configures the following options:<br>- [/ObtainIpv4From: {Dhcp | Range}] - Specifies the source of IPv4 addresses.<br>    - [/start: &lt;starting Ipv4 address&gt;] - Specifies the start of the IP address range. This option is required and valid only if **/ObtainIpv4From** is set to **Range**<br>    - [/End: &lt;Ending Ipv4 address&gt;] - Specifies the end of the IP address range. This option is required and valid only if **/ObtainIpv4From** is set to **Range**.<br>- [/ObtainIpv6From:Range] [/start:&lt;start IP address&gt;] [/End:&lt;End IP address&gt;] Specifies the source of IPv6 addresses. This option only applies to Windows Server 2008 R2 and the only supported value is Range.<br>- [/startPort: &lt;starting port&gt;] - Specifies the start of the port range.<br>- [/EndPort: &lt;Ending port&gt;] - Specifies the end of the port range.<br>- [/Profile: {10Mbps | 100Mbps | 1Gbps | Custom}] - Specifies the network profile to be used. This option is only supported forservers running Windows Server 2008.<br>- [/MulticastSessionPolicy] Configures the transfer settings for multicast transmissions. This command is only available for Windows Server 2008 R2.<br>    - [/Policy:{None | AutoDisconnect | Multistream}] - Determines how to handle slow clients. None means to keep all clients in one session at the same speed. AutoDisconnect means that any clients that drop below the specified /Threshold will be disconnected. Multistream means clients will be separated into multiple sessions as specified by /StreamCount.<br>    - [/Threshold:&lt;Speed in KBps&gt;] - for /Policy:AutoDisconnect, this option sets the minimum transfer rate in KBps. Clients that drop below this rate will be disconnected from multicast transmissions.<br>    - [/StreamCount:{2 | 3}] [/Fallback:{Yes | No}] - for /Policy:Multistream, this option determines the number of sessions. 2 means two sessions (fast and slow) 3 means three sessions (slow, medium, fast).<br>    - [/Fallback:{Yes | No}] - Determines whether clients that are disconnected will continue the transfer using another method (if supported by the client). If you are using the WDS client, the computer will fallback to unicasting. Wdsmcast.exe does not support a fallback mechanism. This option also applies to clients that do not support Multistream. In that case, the computer will fall back to another method instead of moving to a slower transfer session. |

## Examples

To set the server to answer only known clients, with a response delay of 4 minutes, type:

```
wdsutil /Set-Server /AnswerClients:Known /Responsedelay:4
```

To set the boot program and architecture for the server, type:

```
wdsutil /Set-Server /BootProgram:boot\x86\pxeboot.n12 /Architecture:x86
```

To enable logging on the server, type:

```
wdsutil /Set-Server /WdsClientLogging /Enabled:Yes /LoggingLevel:Warnings
```

To enable unattend on the server, as well as the architecture and the client unattend file, type:

```
wdsutil /Set-Server /WdsUnattend /Policy:Enabled /File:WDSClientUnattend \unattend.xml /Architecture:x86
```

To set the Pre-Boot execution Environment (PXE) server to attempt to bind to TCP ports 67 and 60, type:

```
wdsutil /Set-server /UseDhcpPorts:No /DhcpOption60:Yes
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [wdsutil disable-server command](wdsutil-disable-server)
- [wdsutil enable-server command](wdsutil-enable-server)
- [wdsutil get-server command](wdsutil-get-server)
- [wdsutil initialize-server command](wdsutil-initialize-server)
- [wdsutil start-server command](wdsutil-start-server)
- [wdsutil stop-server command](wdsutil-stop-server)
- [wdsutil uninitialize-server command](wdsutil-uninitialize-server)