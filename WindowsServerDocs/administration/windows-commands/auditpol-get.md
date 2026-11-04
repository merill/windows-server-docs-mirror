---
layout: Conceptual
title: auditpol get | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/auditpol-get
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the auditpol get command, which retrieves the system policy, per-user policy, auditing options, and audit security descriptor object.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 385a01c7-ad82-d85a-80b2-c731175258a8
document_version_independent_id: 192935e7-3e99-30a7-38c8-2ea4d077ee55
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/auditpol-get.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/auditpol-get
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/auditpol-get.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: 23af2cf1-e635-fee7-6e00-206be2df4930
---

# auditpol get | Microsoft Learn

Retrieves the system policy, per-user policy, auditing options, and audit security descriptor object.

To perform *get* operations on the *per-user* and *system* policies, you must have **Read** permission for that object set in the security descriptor. You can also perform *get* operations if you have the **Manage auditing and security log** (SeSecurityPrivilege) user right. However, this right allows additional access that is not necessary to perform the overall *get* operations.

## Syntax

```
auditpol /get
[/user[:<username>|<{sid}>]]
[/category:*|<name>|<{guid}>[,:<name|<{guid}> ]]
[/subcategory:*|<name>|<{guid}>[,:<name|<{guid}> ]]
[/option:<option name>]
[/sd]
[/r]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /user | Displays the security principal for whom the per-user audit policy is queried. Either the /category or /subcategory parameter must be specified. The user may be specified as a security identifier (SID) or name. If no user account is specified, then the system audit policy is queried. |
| /category | One or more audit categories specified by globally unique identifier (GUID) or name. An asterisk (\*) may be used to indicate that all audit categories should be queried. |
| /subcategory | One or more audit subcategories specified by GUID or name. |
| /sd | Retrieves the security descriptor used to delegate access to the audit policy. |
| /option | Retrieves the existing policy for the CrashOnAuditFail, FullprivilegeAuditing, AuditBaseObjects, or AuditBasedirectories options. |
| /r | Displays the output in report format, comma-separated value (CSV). |
| /? | Displays help at the command prompt. |

### Remarks

All categories and subcategories can be specified by the GUID or name enclosed by quotation marks ("). Users can be specified by SID or name.

## Examples

To retrieve the per-user audit policy for the Guest account and display the output for the System, detailed Tracking, and Object Access categories, type:

```
auditpol /get /user:{S-1-5-21-1443922412-3030960370-963420232-51} /category:System,detailed Tracking,Object Access
```

Note

This command is useful in two scenarios. 1) When monitoring a specific user account for suspicious activity, you can use the `/get` command to retrieve the results in specific categories by using an inclusion policy to enable additional auditing. 2) if audit settings on an account are logging numerous but superfluous events, you can use the `/get` command to filter out extraneous events for that account with an exclusion policy. For a list of all categories, use the `auditpol /list /category` command.

To retrieve the per-user audit policy for a category and a particular subcategory, which reports the inclusive and exclusive settings for that subcategory under the System category for the Guest account, type:

```
auditpol /get /user:guest /category:System /subcategory:{0ccee921a-69ae-11d9-bed3-505054503030}
```

To display the output in report format and include the computer name, policy target, subcategory, subcategory GUID, inclusion settings, and exclusion settings, type:

```
auditpol /get /user:guest /category:detailed Tracking /r
```

To retrieve the policy for the System category and subcategories, which reports the category and subcategory policy settings for the system audit policy, type:

```
auditpol /get /category:System /subcategory:{0ccee921a-69ae-11d9-bed3-505054503030}
```

To retrieve the policy for the detailed Tracking category and subcategories in report format and include the computer name, policy target, subcategory, subcategory GUID, inclusion settings, and exclusion settings, type:

```
auditpol /get /category:detailed Tracking /r
```

To retrieve the policy for two categories with the categories specified as GUIDs, which reports all the audit policy settings of all the subcategories under two categories, type:

```
auditpol /get /category:{69979849-797a-11d9-bed3-505054503030},{69997984a-797a-11d9-bed3-505054503030} subcategory:{0ccee921a-69ae-11d9-bed3-505054503030}
```

To retrieve the state, either enabled or disabled, of the AuditBaseObjects option, type:

```
auditpol /get /option:AuditBaseObjects
```

Where the available options are AuditBaseObjects, AuditBaseOperations, and FullprivilegeAuditing. To retrieve the state enabled, disabled, or 2 of the CrashOnAuditFail option, type:

```
auditpol /get /option:CrashOnAuditFail /r
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [auditpol commands](auditpol)