---
layout: Conceptual
title: auditpol resourceSACL | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/auditpol-resourcesacl
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the auditpol resourceSACL command, which configures global resource system access control lists (SAcls).
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: b38bc2ad-874b-53f6-68d3-3bc3b9920f0b
document_version_independent_id: de8d20cc-4265-3740-fefd-8501474edb4c
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/auditpol-resourcesacl.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/auditpol-resourcesacl
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/auditpol-resourcesacl.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/97159432-14a9-4307-a469-d2f2c75f0e33
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/50565c62-5f6b-4687-be38-323113c72c2e
platformId: 1c02e245-17fd-ac8e-0ecd-d2b6986d346a
---

# auditpol resourceSACL | Microsoft Learn

Configures global resource system access control lists (SACLs).

To perform *resourceSACL* operations, you must have **Write** or **Full Control** permissions for that object set in the security descriptor. You can also perform *resourceSACL* operations if you have the **Manage auditing and security log** (SeSecurityPrivilege) user right.

## Syntax

```
auditpol /resourceSACL
[/set /type:<resource> [/success] [/failure] /user:<user> [/access:<access flags>]]
[/remove /type:<resource> /user:<user> [/type:<resource>]]
[/clear [/type:<resource>]]
[/view [/user:<user>] [/type:<resource>]]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /set | Adds a new entry to or updates an existing entry in the resource SACL for the resource type specified. |
| /remove | Removes all entries for the given user in the global object access auditing list. |
| /clear | Removes all entries from the global object access auditing list. |
| /view | Lists the global object access auditing entries in a resource SACL. The user and resource types are optional. |
| /? | Displays help at the command prompt. |

### Arguments

| Argument | Description |
| --- | --- |
| /type | The resource for which object access auditing is being configured. The supported, case-sensitive, argument values are *File* (for directories and files) and *Key* (for registry keys). |
| /success | Specifies success auditing. |
| /failure | Specifies failure auditing. |
| /user | Specifies a user in one of the following forms:<br>- DomainName\Account (such as DOM\Administrators)<br>- StandaloneServer\Group Account (see [LookupAccountName function](/en-us/windows/win32/api/winbase/nf-winbase-lookupaccountnamea))<br>- {S-1-x-x-x-x} (x is expressed in decimal, and the entire SID must be enclosed in curly braces). For example: {S-1-5-21-5624481-130208933-164394174-1001}<br>    **Note:** If the SID form is used, no check is done to verify the existence of this account. |
| /access | Specifies a permission mask that can be specified through:<br>Generic access rights, including:<br><br>- GA - GENERIC ALL<br>- GR - GENERIC READ<br>- GW - GENERIC WRITE<br>- GX - GENERIC EXECUTE<br><br><br>Access rights for files, including:<br><br>- FA - FILE ALL ACCESS<br>- FR - FILE GENERIC READ<br>- FW - FILE GENERIC WRITE<br>- FX - FILE GENERIC EXECUTE<br><br><br>Access rights for registry keys, including:<br><br>- KA - KEY ALL ACCESS<br>- KR - KEY READ<br>- KW - KEY WRITE<br>- KX - KEY EXECUTE<br><br><br>For example: `/access:FRFW` enables audit events for read and write operations.<br><br>A hexadecimal value representing the access mask (such as 0x1200a9)<br><br>This is useful when using resource-specific bit masks that are not part of the security descriptor definition language (SDDL) standard. If omitted, Full access is used. |

## Examples

To set a global resource SACL to audit successful access attempts by a user on a registry key:

```
auditpol /resourceSACL /set /type:Key /user:MYDOMAIN\myuser /success
```

To set a global resource SACL to audit successful and failed attempts by a user to perform generic read and write functions on files or folders:

```
auditpol /resourceSACL /set /type:File /user:MYDOMAIN\myuser /success /failure /access:FRFW
```

To remove all global resource SACL entries for files or folders:

```
auditpol /resourceSACL /type:File /clear
```

To remove all global resource SACL entries for a particular user from files or folders:

```
auditpol /resourceSACL /remove /type:File /user:{S-1-5-21-56248481-1302087933-1644394174-1001}
```

To list the global object access auditing entries set on files or folders:

```
auditpol /resourceSACL /type:File /view
```

To list the global object access auditing entries for a particular user that are set on files or folders:

```
auditpol /resourceSACL /type:File /view /user:MYDOMAIN\myuser
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [auditpol commands](auditpol)