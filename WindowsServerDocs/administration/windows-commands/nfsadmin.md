---
layout: Conceptual
title: nfsadmin | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/nfsadmin
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the nfsadmin command, which manages both Server for NFS and Client for NFS.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 9a2472b3-77f4-89e9-1002-6f715098dd99
document_version_independent_id: 800c79c6-c172-a9c6-cebc-ec1260984d9b
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/nfsadmin.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/nfsadmin
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/nfsadmin.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/97159432-14a9-4307-a469-d2f2c75f0e33
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/50565c62-5f6b-4687-be38-323113c72c2e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 56fb422c-64a7-4060-3c37-f9b5bc92d610
---

# nfsadmin | Microsoft Learn

A command-line utility that administers Server for NFS or Client for NFS on the local or remote computer running Microsoft Services for Network File System (NFS). Used without parameters, nfsadmin server displays the current Server for NFS configuration settings and nfsadmin client displays the current Client for NFS configuration settings.

## Syntax

```
nfsadmin server [computername] [-u Username [-p Password]] -l
nfsadmin server [computername] [-u Username [-p Password]] -r {client | all}
nfsadmin server [computername] [-u Username [-p Password]] {start | stop}
nfsadmin server [computername] [-u Username [-p Password]] config option[...]
nfsadmin server [computername] [-u Username [-p Password]] creategroup <name>
nfsadmin server [computername] [-u Username [-p Password]] listgroups
nfsadmin server [computername] [-u Username [-p Password]] deletegroup <name>
nfsadmin server [computername] [-u Username [-p Password]] renamegroup <oldname> <newname>
nfsadmin server [computername] [-u Username [-p Password]] addmembers <hostname>[...]
nfsadmin server [computername] [-u Username [-p Password]] listmembers
nfsadmin server [computername] [-u Username [-p Password]] deletemembers <hostname><groupname>[...]
nfsadmin client [computername] [-u Username [-p Password]] {start | stop}
nfsadmin client [computername] [-u Username [-p Password]] config option[...]
```

### General Parameters

| Parameter | Description |
| --- | --- |
| computername | Specifies the remote computer you want to administer. You can specify the computer using a Windows Internet Name Service (WINS) name or a Domain Name System (DNS) name, or by Internet Protocol (IP) address. |
| -u Username | Specifies the user name of the user whose credentials are to be used. It might be necessary to add the domain name to the user name in the form *domain\username*. |
| -p Password | Specifies the password of the user specified using the **-u** option. If you specify the **-u** option but omit the **-p** option, you are prompted for the user's password. |

### Server for NFS-related parameters

| Parameter | Description |
| --- | --- |
| -l | Lists all locks held by clients. |
| -r `{client|all}` | Releases the locks held by a client or, if all is specified, by all clients. |
| start | Starts the Server for NFS service. |
| stop | Stops the Server for NFS service. |
| config | Specifies general settings for Server for NFS. You must supply at least one of the following options with the **config** command argument:<br>- **mapsvr=`<server>`** - Sets server as the User Name Mapping server for Server for NFS. Although this option continues to be supported for compatibility with previous versions, you should use the sfuadmin utility instead.<br>- **auditlocation=`{eventlog|file|both|none}`**- Specifies whether events will be audited and where the events will be recorded. One of the following arguments is required:<br>    - **eventlog** - Specifies that audited events will be recorded only in the Event Viewer application log.<br>    - **file** - Specifies that audited events will be recorded only in the file specified by `config fname`.<br>    - **both** - Specifies that audited events will be recorded in the Event Viewer application log as well as the file specified by `config fname`.<br>    - **none** - Specifies that events aren't audited.<br>- **fname=`<file>`** - Sets the file specified by file as the audit file. The default is **%sfudir%\log\nfssvr.log**.<br>- **fsize=`<size>`** - Sets size as the maximum size in megabytes of the audit file. The default maximum size is **7 MB**.<br>- **`audit=[+|-]mount [+|-]read [+|-]write [+|-]create [+|-]delete [+|-]locking [+|-]all`** - Specifies the events to be logged. To start logging an event, type a plus sign (**+**) before the event name; to stop logging an event, type a minus sign (**-**) before the event name. If the sign is omitted, the **+** sign is assumed. Don't use **all** with any other event name.<br>- **lockperiod=`<seconds>`** - Specifies the number of seconds that Server for NFS will wait to reclaim locks after a connection to Server for NFS has been lost and then reestablished or after the Server for NFS service has been restarted.<br>- **portmapprotocol=`{TCP|UDP|TCP+UDP}`** - Specifies which transport protocols Portmap supports. The default setting is **TCP+UDP**.<br>- **mountprotocol=`{TCP|UDP|TCP+UDP}`** - Specifies which transport protocols mount supports. The default setting is **TCP+UDP**.<br>- **nfsprotocol=`{TCP|UDP|TCP+UDP}`** - Specifies which transport protocols Network File System (NFS) supports. The default setting is **TCP+UDP**<br>- **nlmprotocol=`{TCP|UDP|TCP+UDP}`** - Specifies which transport protocols Network Lock Manager (NLM) supports. The default setting is **TCP+UDP**.<br>- **nsmprotocol=`{TCP|UDP|TCP+UDP}`** - Specifies which transport protocols Network Status Manager (NSM) supports. The default setting is **TCP+UDP**.<br>- **enableV3=`{yes|no}`** - Specifies whether NFS version 3 protocols will be supported. The default setting is **yes**.<br>- **renewauth=`{yes|no}`** - Specifies whether client connections will be required to be reauthenticated after the period specified by config renewauthinterval. The default setting is **no**.<br>- **renewauthinterval=`<seconds>`** - Specifies the number of seconds that elapse before a client is forced to be reauthenticated if `config renewauth` is set to **yes**. The default value is **600 seconds**.<br>- **dircache=`<size>`** - Specifies the size in kilobytes of the directory cache. The number specified as size must be a multiple of 4 between 4 and 128. The default directory cache size is **128 KB**.<br>- **translationfile=`<file>`** - Specifies a file containing mapping information for replacing characters in the names of files when moving them from Windows-based to UNIX-based file systems. If file is not specified, then file name character translation is disabled. If the value of **translationfile** is changed, you must restart the server for the change to take effect.<br>- **dotfileshidden=`{yes|no}`** - Specifies whether files with names beginning with a period (.) are marked as hidden in the Windows file system, and consequently hidden from NFS clients. The default setting is **no**.<br>- **casesensitivelookups=`{yes|no}`** - Specifies whether directory lookups are case sensitive (require exact matching of character case).<br>    You must also disable Windows kernel case-insensitivity to support case-sensitive file names. To support case-sensitivity, change the **DWord** value of the registry key, `HKLM\SYSTEM\CurrentControlSet\Control\Session Manager\kernel`, to **0**.<br>- **ntfscase=`{lower|upper|preserve}`** - Specifies whether the case of characters in the names of files in the NTFS file system will be returned in lowercase, uppercase, or in the form stored in the directory. The default setting is **preserve**. This setting can't be changed if **casesensitivelookups** is set to **yes**. |
| creategroup `<name>` | Creates a new client group, giving it the specified name. |
| listgroups | Displays the names of all client groups. |
| deletegroup `<name>` | Removes the client group specified by name. |
| renamegroup `<oldname>``<newname>` | Changes the name of the client group specified by *oldname* to *newname*. |
| addmembers `<hostname>[...]` | Adds a *host* to the client group specified by *name*. |
| listmembers `<name>` | Lists the host computers in the client group specified by *name*. |
| deletemembers `<hostname><groupname>[...]` | Removes the client specified by *host* from the client group specified by *group*. |

### Client for NFS-related parameters

| Parameter | Description |
| --- | --- |
| start | Starts the Client for NFS service. |
| stop | Stops the Client for NFS service. |
| config | Specifies general settings for Client for NFS. You must supply at least one of the following options with the **config** command argument:<br>- **fileaccess=`<mode>`** - Specifies the default permission mode for files created on Network File System (NFS) servers. The **mode** argument consists of a three digit number, from 0 to 7 (inclusive), which represent the default permissions granted the user, group, and others. The digits translate to UNIX-style permissions as follows: *0=none*, *1=x (execute)*, *2=w (write only)*, *3=wx (write and execute)*, *4=r (read only)*, *5=rx (read and execute)*, *6=rw (read and write)*, and *7=rwx (read, write, and execute)*. For example, `fileaccess=750` gives read, write, and execute permissions to the owner, read and execute permissions to the group, and no access permission to others.<br>- **mapsvr=`<server>`** - Sets server as the User Name Mapping server for Client for NFS. Although this option continues to be supported for compatibility with previous versions, you should use the sfuadmin utility instead.<br>- **mtype=`{hard|soft}`** - Specifies the default mount type. For a hard mount, Client for NFS continues to retry a failed RPC until it succeeds. For a soft mount, Client for NFS returns failure to the calling application after retrying the call the number of times specified by the retry option.<br>- **retry=`<number>`** - Specifies the number of times to try to make a connection for a soft mount. This value must be from 1 to 10, inclusive. The default is **1**.<br>- **timeout=`<seconds>`** - Specifies the number of seconds to wait for a connection (remote procedure call). This value must be *0.8*, *0.9*, or an integer from *1 to 60*, inclusive. The default is **0.8**.<br>- **protocol=`{TCP|UDP|TCP+UDP}`** - Specifies which transport protocols the client supports. The default setting is **TCP+UDP**.<br>- **rsize=`<size>`** -Specifies the size, in kilobytes, of the read buffer. This value can be *0.5, 1, 2, 4, 8, 16,* or *32*. The default is **32**.<br>- **wsize=`<size>`** - Specifies the size, in kilobytes, of the write buffer. This value can be *0.5, 1, 2, 4, 8, 16,* or *32*. The default is **32**.<br>- **perf=default** - Restores the following performance settings to default values, *mtype*, *retry*, *timeout*, *rsize*, or *wsize*. |

### Examples

To stop Server for NFS or Client for NFS, type:

```
nfsadmin server stop
nfsadmin client stop
```

To start Server for NFS or Client for NFS, type:

```
nfsadmin server start
nfsadmin client start
```

To set Server for NFS to not be case-sensitive, type:

```
nfsadmin server config casesensitive=no
```

To set Client for NFS to be case-sensitive, type:

```
nfsadmin client config casesensitive=yes
```

To display all the current Server for NFS or Client for NFS options, type:

```
nfsadmin server config
nfsadmin client config
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [NFS cmdlets reference](/en-us/powershell/module/nfs)