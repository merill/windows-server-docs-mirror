---
layout: Conceptual
title: mount | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/mount
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the mount command, which mounts Network File System (NFS) network shares.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2023-09-27T00:00:00.0000000Z
locale: en-us
document_id: d98186ad-af7e-d25d-2135-f0c65ffd5288
document_version_independent_id: 55c29643-935f-7eab-6a3a-8814f96e8669
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/mount.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/mount
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/mount.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 7f4f3b1d-af54-f2e4-f353-61357df5fa10
---

# mount | Microsoft Learn

A command-line utility that mounts Network File System (NFS) network shares. When used without options or arguments, **mount** displays information about all mounted NFS file systems.

Note

This utility is available only if **Client for NFS** is installed.

## Syntax

```
mount [-o <option>[...]] [-u:<username>] [-p:{<password> | *}] {\\<computername>\<sharename> | <computername>:/<sharename>} {<devicename> | *}
```

### Parameters

| Parameter | Description |
| --- | --- |
| -o rsize=`<buffersize>` | Sets the size in kilobytes of the read buffer. Acceptable values are 1, 2, 4, 8, 16, and 32; the default is 32 KB. |
| -o wsize=`<buffersize>` | Sets the size in kilobytes of the write buffer. Acceptable values are 1, 2, 4, 8, 16, and 32; the default is 32 KB. |
| -o timeout=`<seconds>` | Sets the time-out value in seconds for a remote procedure call (RPC). Acceptable values are 0.8, 0.9, and any integer in the range 1-60; the default is 0.8. |
| -o retry=`<number>` | Sets the number of retries for a soft mount. Acceptable values are integers in the range 1-10; the default is 1. |
| -o mtype=`{soft|hard}` | Sets the mount type for your NFS share. By default, Windows uses a soft mount. Soft mounts time out more easily when there are connection issues; however, to reduce I/O disruption during NFS server reboots, we recommend using a hard mount. |
| -o lang=`{euc-jp|euc-tw|euc-kr|shift-jis|Big5|Ksc5601|Gb2312-80|Ansi}` | Specifies the language encoding to configure on an NFS share. You can use only one language on the share. This value can include any of the following values:<br>- **euc-jp:** Japanese<br>- **euc-tw:** Chinese<br>- **euc-kr:** Korean<br>- **shift-jis:** Japanese<br>- **Big5:** Chinese<br>- **Ksc5601:** Korean<br>- **Gb2312-80:** Simplified Chinese<br>- **Ansi:** ANSI-encoded |
| -o fileaccess=`<mode>` | Specifies the default permission mode of new files created on the NFS share. Specify *mode* as a three-digit number in the form *ogw*, where *o*, *g*, and *w* are each a digit representing the access granted the file's owner, group, and the world, respectively. The digits must be in the range 0-7, including:<br>- **0:** No access<br>- **1:** x (execute access)<br>- **2:** w (write access)<br>- **3:** wx (write and execute access)<br>- **4:** r (read access)<br>- **5:** rx (read and execute access)<br>- **6:** rw (read and write access)<br>- **7:** rwx (read, write, and execute access) |
| -o anon | Mounts as an anonymous user. |
| -o nolock | Disables locking (default is **enabled**). |
| -o casesensitive | Forces file lookups on the server to be case sensitive. |
| -o sec=`{sys|krb5|krb5i|krb5p}` | Specifies the security mechanism for mounting an NFS share. This value can include any of the following:<br>- **sec=sys:** No authentication or security checks are performed. Data transfers aren't encrypted.<br>- **sec=krb5:** Specifies Kerberos authentication for mounting the NFS share.<br>- **sec=krb5i:** Extends Kerberos security by adding data integrity checks between the client and server hasn't been tampered.<br>- **sec=krb5p:** Enhances Kerberos security by enabling data privacy, which encrypts data exchanged between the client and server. |
| -u:`<username>` | Specifies the user name to use for mounting the share. If *username* isn't preceded by a backslash ( **\** ), it's treated as a UNIX user name. |
| -p:`<password>` | The password to use for mounting the share. If you use an asterisk (**\***), you're prompted for the password. |
| `<computername>` | Specifies the name of the NFS server. |
| `<sharename>` | Specifies the name of the file system. |
| `<devicename>` | Specifies the drive letter and name of the device. If you use an asterisk (**\***) this value represents the first available driver letter. |

### Examples

To mount the NFS share anonymously on network drive Z, type:

```cmd
mount -o anon \\ServerIP\ShareName Z:
```

Note

In order for this parameter to function as intended, the NFS server must allow anonymous access.

To mount the NFS share and disable file locking for network drive Z, type:

```cmd
mount -o nolock \\ServerIP\ShareName Z:
```

To mount the NFS share with permissions for the *ogw* set as rwx, rw, r, and to continuously reconnect to the NFS server if the connection is lost for network drive Z, type:

```cmd
mount -o fileaccess=764 mtype=hard \\ServerIP\ShareName Z:
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)