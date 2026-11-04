---
layout: Conceptual
title: ksetup | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/ksetup
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the ksetup command, which performs tasks related to setting up and maintaining Kerberos protocol and the Key Distribution Center (KDC) to support Kerberos realms.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 410b80f2-815c-22f3-5e93-5ed7671cf2d8
document_version_independent_id: b7b6210d-51c1-8b91-fafc-93ca8c0d7d3d
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/ksetup.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/ksetup
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/ksetup.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: fe6f356c-565e-4ad5-c5ea-c998f0e41cb6
---

# ksetup | Microsoft Learn

Performs tasks related to setting up and maintaining Kerberos protocol and the Key Distribution Center (KDC) to support Kerberos realms. Specifically, this command is used to:

- Change the computer settings for locating Kerberos realms. In non-Microsoft, Kerberos-based implementations, this information is usually kept in the Krb5.conf file. In Windows Server operating systems, it's kept in the registry. You can use this tool to modify these settings. These settings are used by workstations to locate Kerberos realms and by domain controllers to locate Kerberos realms for cross-realm trust relationships.
- Initialize registry keys that the Kerberos Security Support Provider (SSP) uses to locate a KDC for the Kerberos realm, if the computer is isn't a member of a Windows domain. After configuration, the user of a client computer running the Windows operating system can log on to accounts in the Kerberos realm.
- Search the registry for the domain name of the user's realm and then resolves the name to an IP address by querying a DNS server. The Kerberos protocol can use DNS to locate KDCs by using only the realm name, but it must be specially configured to do so.

## Syntax

```
ksetup
[/setrealm <DNSdomainname>]
[/mapuser <principal> <account>]
[/addkdc <realmname> <KDCname>]
[/delkdc <realmname> <KDCname>]
[/addkpasswd <realmname> <KDCPasswordName>]
[/delkpasswd <realmname> <KDCPasswordName>]
[/server <servername>]
[/setcomputerpassword <password>]
[/removerealm <realmname>]
[/domain <domainname>]
[/changepassword <oldpassword> <newpassword>]
[/listrealmflags]
[/setrealmflags <realmname> [sendaddress] [tcpsupported] [delegate] [ncsupported] [rc4]]
[/addrealmflags <realmname> [sendaddress] [tcpsupported] [delegate] [ncsupported] [rc4]]
[/delrealmflags [sendaddress] [tcpsupported] [delegate] [ncsupported] [rc4]]
[/dumpstate]
[/addhosttorealmmap] <hostname> <realmname>]
[/delhosttorealmmap] <hostname> <realmname>]
[/setenctypeattr] <domainname> {DES-CBC-CRC | DES-CBC-MD5 | RC4-HMAC-MD5 | AES128-CTS-HMAC-SHA1-96 | AES256-CTS-HMAC-SHA1-96}
[/getenctypeattr] <domainname>
[/addenctypeattr] <domainname> {DES-CBC-CRC | DES-CBC-MD5 | RC4-HMAC-MD5 | AES128-CTS-HMAC-SHA1-96 | AES256-CTS-HMAC-SHA1-96}
[/delenctypeattr] <domainname>
```

### Parameters

| Parameter | Description |
| --- | --- |
| [ksetup setrealm](ksetup-setrealm) | Makes this computer a member of a Kerberos realm. |
| [ksetup addkdc](ksetup-addkdc) | Defines a KDC entry for the given realm. |
| [ksetup delkdc](ksetup-delkdc) | Deletes a KDC entry for the realm. |
| [ksetup addkpasswd](ksetup-addkpasswd) | Adds a kpasswd server address for a realm. |
| [ksetup delkpasswd](ksetup-delkpasswd) | Deletes a kpasswd server address for a realm. |
| [ksetup server](ksetup-server) | Allows you to specify the name of a Windows computer on which to apply the changes. |
| [ksetup setcomputerpassword](ksetup-setcomputerpassword) | Sets the password for the computer's domain account (or host principal). |
| [ksetup removerealm](ksetup-removerealm) | Deletes all information for the specified realm from the registry. |
| [ksetup domain](ksetup-domain) | Allows you to specify a domain (if the `<domainname>` hasn't already been set by the **/domain** parameter). |
| [ksetup changepassword](ksetup-changepassword) | Allows you to use the kpasswd to change the logged on user's password. |
| [ksetup listrealmflags](ksetup-listrealmflags) | Lists the available realm flags that **ksetup** can detect. |
| [ksetup setrealmflags](ksetup-setrealmflags) | Sets realm flags for a specific realm. |
| [ksetup addrealmflags](ksetup-addrealmflags) | Adds additional realm flags to a realm. |
| [ksetup delrealmflags](ksetup-delrealmflags) | Deletes realm flags from a realm. |
| [ksetup dumpstate](ksetup-dumpstate) | Analyzes the Kerberos configuration on the given computer. Adds a host to realm mapping to the registry. |
| [ksetup addhosttorealmmap](ksetup-addhosttorealmmap) | Adds a registry value to map the host to the Kerberos realm. |
| [ksetup delhosttorealmmap](ksetup-delhosttorealmmap) | Deletes the registry value that mapped the host computer to the Kerberos realm. |
| [ksetup setenctypeattr](ksetup-setenctypeattr) | Sets one or more encryption types trust attributes for the domain. |
| [ksetup getenctypeattr](ksetup-getenctypeattr) | Gets the encryption types trust attribute for the domain. |
| [ksetup addenctypeattr](ksetup-addenctypeattr) | Adds encryption types to the encryption types trust attribute for the domain. |
| [ksetup delenctypeattr](ksetup-delenctypeattr) | Deletes the encryption types trust attribute for the domain. |
| /? | Displays Help at the command prompt. |

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)