---
layout: Conceptual
title: netsh branchcache | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/netsh-branchcache
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the netsh branchcache command in Windows, which manages data access speeds in branch offices locally.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2025-07-24T00:00:00.0000000Z
locale: en-us
document_id: 1975c121-07f8-eddb-84b1-6ed6a5897d2b
document_version_independent_id: 1975c121-07f8-eddb-84b1-6ed6a5897d2b
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/netsh-branchcache.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/netsh-branchcache
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/netsh-branchcache.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 1c9e7cee-62f8-f891-1b9c-bc5ee0aa7eb9
---

# netsh branchcache | Microsoft Learn

The `netsh branchcache` command is used in Windows to manage BranchCache, a feature that speeds up access to data in branch offices.

## Syntax

```
netsh branchcache dump | exportkey | flush | help | importkey | reset | set | show | smb | ?
```

```
netsh branchcache exportkey [outputfile=]<File Path> [passphrase]=<Pass Phrase>
netsh branchcache importkey [inputfile=]<File Path> [passphrase]=<Pass Phrase>
```

```
netsh branchcache set [cachesize | key | localcache | publicationcache | publicationcachesize | service]
netsh branchcache set [cachesize | publicationcachesize] [size=]{DEFAULT|<number>} [[percent=]{TRUE|FALSE}]
netsh branchcache set key [[passphrase=]<Pass Phrase>]
netsh branchcache set [localcache | publicationcache] [directory=]{DEFAULT|<File Path>}
netsh branchcache set service [mode=]{DISABLED|LOCAL|DISTRIBUTED|HOSTEDSERVER|HOSTEDCLIENT}
                              [[location]=<Host Name>]
                              [[clientauthentication]={DOMAIN|NONE}]
                              [[serveonbattery]={TRUE|FALSE}]
```

```
netsh branchcache show [hostedcache | localcache | publicationcache | status]
netsh branchcache show status [[detail=]{BASIC|ALL}]
```

```
netsh branchcache smb [dump | help | set | show]
netsh branchcache smb set [latency=]<number>
```

## Parameters

| Parameter | Description |
| --- | --- |
| dump | Dumps the configuration details and settings related to BranchCache on your device. |
| exportykey `<FilePath>\<FileName>``<Passphrase>` | Exports the key which the BranchCache service uses to protect content information. The key can later be imported on another device by using the `importkey` command.  The output file is a directory path and name of the file where the key should be exported. The passphrase is required to import the key. |
| flush | Clears or deletes the local cache of content that BranchCache stores on your device. |
| help *or* ? | Displays help information for the given command. |
| importkey `<FilePath>\<FileName>``<Passphrase>` | Imports a key for the BranchCache service to use to protect content information. The key must be previously exported using the `exportkey` command. If the service is currently running, this command restarts it in order to begin using the new key. |
| reset | Restarts the BranchCache service and clears both the content cache on the client side and any locally stored publication data. This command resets configuration settings to their default settings. |
| set [cachesize | publicationcachesize] [size=]{DEFAULT|`<number>`} [[percent=]{`TRUE`|`FALSE`}] | cachesize - Sets the size of the local cache.  publicationcachesize - Sets the size of the local publication cache.  size - Indicates the cache size as a percentage or an exact `<number>` of bytes. If set to `default`, the default configuration is restored.  percent - Specifies whether the size value is interpreted as a percentage of the hard disk size or in the exact `<number>` of bytes. This parameter is ignored if the size value is set to `default`. `True` - Indicates the size is a percentage of the size of the hard disk. `False` - Indicates the size is an exact number of bytes (default option). |
| set key [[passphrase=]&lt;Passphrase&gt;] | key - Generates a new content information key.  A passphrase is used to generate the key. If a passphrase isn't provided, a random key is generated. If two keys generated using the same passphrase, they're identical. A passphrase can be used to duplicate the same key on another device. |
| set [localcache | publicationcache] [directory=]{DEFAULT|&lt;File Path&gt;} | localcache - Sets the location of the local cache.  publicationcache - Sets the location of the local publication cache.  directory - Is the path to the directory in which the local cache or publication cache should be stored. When set to `default`, it restores the default cache location. This service is restarted, if necessary, in order to complete the change. Any existing cache files are moved to the new location. |
| set service [mode=]{DISABLED | LOCAL | DISTRIBUTED | HOSTEDSERVER | HOSTEDCLIENT} [[location]=&lt;Host Name&gt;] [[clientauthentication]={DOMAIN|NONE}] [[serveonbattery]={TRUE|FALSE}] | mode - Configures the BranchCache service mode. - `disabled` - Disables the BranchCache service.<br>- `local` - Enables caching of data on the local device only.<br>- `distributed` - Activates distributed caching, allowing data to be cached across multiple computers in a peer-to-peer configuration.<br>- `hostedserver` - Sets the device as a Hosted Cache Server to serve cached data to clients.<br>- `hostedclient` - Sets the device as a client of a Hosted Cache Server to receive and store cached data.<br> location - Sets the location of the Hosted Cache Server, which is only necessary if the mode is set to `hostedclient` and is ignored in other modes.  clientauthentication - Sets the method used by a Hosted Cache Server to authenticate connected clients. This parameter is only relevant when the mode is set to `hostedserver` and is ignored otherwise. - `domain` - Requires clients to be members of the same domain as the Hosted Cache Server for authentication.<br>- `none` - No authentication method is implemented for clients.<br> serveonbattery - Allows the local client to respond to peer requests for cached data while operating on battery power. This parameter is applicable only when the mode is set to `distributed` and is ignored otherwise. - `true` - Enables the servicer to provide cached data while on battery.<br>- `false` - Disables the servicing of cached data requests when on battery power. |
| show [hostedcache | localcache | publicationcache | status] | `hostedcache` - Displays the configuration information status of the Hosted Cache server if the device is set up to function as one. `localcache` - Provides details about the local cache on the device, such as the size of the cache on the hard disk and cache location. `publicationcache` - Shows information about the publication cache settings and contents. `status` - Provides a summary of the current BranchCache configuration and operational status, including the mode BranchCache is set to. |
| show status [[detail=]{`BASIC`|`ALL`}] | detail - Specifies the level of detail for the displayed information. `basic` - Shows only essential information (default option). `all` - Displays comprehensive information available. |
| smb [dump]  smb [set | show] latency [latency=]\`<number>` | Manages the BranchCache settings related to the Server Message Block (SMB) protocol. `dump` - Outputs a script that represents the current configuration settings. `set` - Modifies or assigns values to specific configuration parameters. `show` - Displays the current configuration parameters and their values. `latency` - Specifies the minimum link latency, in milliseconds, to the branch office before SMB utilizes BranchCache for caching. |

## Examples

**dump**

To dump the BranchCache configuration to a file, type the following command:

```cmd
netsh branchcache dump > C:\BranchCacheConfig.txt
```

**exportkey**

To export the client key to a file, type the following command:

```cmd
netsh branchcache exportkey C:\Keys\BranchCacheKey.bckey
```

To export a specific key with a password, type the following command:

```cmd
netsh branchcache exportkey C:\Keys\BranchCacheKey.bckey mypassword
```

**flush**

To clear all cached content, type the following command:

```cmd
netsh branchcache flush
```

**help**

To display help for a specific BranchCache command, such as exportkey, type the following command:

```cmd
netsh branchcache exportkey help
```

Note

Both the `help` and `?` commands are used interchangeably.

**importkey**

To import a BranchCache key from a file, type the following command:

```cmd
netsh branchcache importkey C:\Keys\BranchCacheKey.bckey
```

To import a key from a file with a password, type the following command:

```cmd
netsh branchcache importkey C:\Keys\BranchCacheKey.bckey mypassword
```

**reset**

To reset BranchCache to its default state, type the following command:

```cmd
netsh branchcache reset
```

**set**

To set the BranchCache mode to `distributed`, type the following command:

```cmd
netsh branchcache set mode=distributed
```

To set the cache size to a specific percentage, such as `10%`, type the following command:

```cmd
netsh branchcache set cachesize=10%
```

To configure a client to use a hosted cache server, type the following command:

```cmd
netsh branchcache set service mode=HOSTEDCLIENT location=HOSTEDSERVERNAME
```

**show**

To show the current BranchCache status, type the following command:

```cmd
netsh branchcache show status
```

To show the current BranchCache configuration, type the following command:

```cmd
netsh branchcache show configuration
```

**smb**

To set the latency threshold to `80` milliseconds, type the following command:

```cmd
netsh branchcache smb set latency=80
```