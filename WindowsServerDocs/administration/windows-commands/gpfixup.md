---
layout: Conceptual
title: gpfixup | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/gpfixup
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the gpfixup command, which fixes domain name dependencies in Group Policy Objects and Group Policy links after a domain rename operation.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 5544a918-6b74-b6ed-f8f7-471ed5c36e05
document_version_independent_id: b75fee58-04c7-6f6c-4c05-a0858ed41956
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/gpfixup.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/gpfixup
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/gpfixup.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: fdbcec3f-072b-74c7-a3bb-828015f57148
---

# gpfixup | Microsoft Learn

Fixes domain name dependencies in Group Policy Objects and Group Policy links after a domain rename operation. To use this command, you must install Group Policy Management as a feature through Server Manager.

## Syntax

```
gpfixup [/v]
[/olddns:<olddnsname> /newdns:<newdnsname>]
[/oldnb:<oldflatname> /newnb:<newflatname>]
[/dc:<dcname>] [/sionly]
[/user:<username> [/pwd:{<password>|*}]] [/?]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /v | Displays detailed status messages. If this parameter isn't used, only error messages or a summary status message stating, **SUCCESS** or **FAILURE** appears. |
| /olddns:`<olddnsname>` | Specifies the old DNS name of the renamed domain as `<olddnsname>` when the domain rename operation changes the DNS name of a domain. You can use this parameter only if you also use the **/newdns** parameter to specify a new domain DNS name. |
| /newdns:`<newdnsname>` | Specifies the new DNS name of the renamed domain as `<newdnsname>` when the domain rename operation changes the DNS name of a domain. You can use this parameter only if you also use the **/olddns** parameter to specify the old domain DNS name. |
| /oldnb:`<oldflatname>` | Specifies the old NetBIOS name of the renamed domain as `<oldflatname>` when the domain rename operation changes the NetBIOS name of a domain. You can use this parameter only if you use the **/newnb** parameter to specify a new domain NetBIOS name. |
| /newnb:`<newflatname>` | Specifies the new NetBIOS name of the renamed domain as `<newflatname>` when the domain rename operation changes the NetBIOS name of a domain. You can use this parameter only if you use the **/oldnb** parameter to specify the old domain NetBIOS name. |
| /dc:`<dcname>` | Connect to the domain controller named `<dcname>` (a DNS name or a NetBIOS name). `<dcname>` must host a writable replica of the domain directory partition as indicated by one of the following:<br>- The DNS name `<newdnsname>` by using **/newdns**<br>- The NetBIOS name `<newflatname>` by using **/newnb**If this parameter isn't used, you can connect to any domain controller in the renamed domain indicated by `<newdnsname>` or `<newflatname>`. |
| /sionly | Performs only the Group Policy fix that relates to managed software installation (the Software Installation extension for Group Policy). Skip the actions that fix Group Policy links and the SYSVOL paths in GPOs. |
| /user:`<username>` | Runs this command in the security context of the user `<username>`, where `<username>` is in the format domain\user. If this parameter isn't used, this command runs as the logged in user. |
| /pwd:`{<password> | *}` | Specifies the password for the user. |
| /? | Displays Help at the command prompt. |

### Examples

This example assumes that you have already performed a domain rename operation in which you changed the DNS name from **MyOldDnsName** to **MyNewDnsName**, and the NetBIOS name from **MyOldNetBIOSName** to **MyNewNetBIOSName**.

In this example, you use the **gpfixup** command to connect to the domain controller named **MyDcDnsName** and repair GPOs and Group Policy links by updating the old domain name embedded in the GPOs and links. Status and error output is saved to a file that is named **gpfixup.log**.

```
gpfixup /olddns: MyOldDnsName /newdns:MyNewDnsName /oldnb:MyOldNetBIOSName /newnb:MyNewNetBIOSName /dc:MyDcDnsName 2>&1 >gpfixup.log
```

This example is the same as the previous one, except that it assumes the NetBIOS name of the domain was not changed during the domain rename operation.

```
gpfixup /olddns: MyOldDnsName /newdns:MyNewDnsName /dc:MyDcDnsName 2>&1 >gpfixup.log
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [Administering Active Directory Domain Rename](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc794869%28v=ws.10%29)