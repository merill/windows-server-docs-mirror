---
layout: Conceptual
title: auditpol set | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/auditpol-set
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the auditpol set command, which sets the per-user audit policy, system audit policy, or auditing options.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 4db7a055-a5ca-e6f9-5786-99d0f325e708
document_version_independent_id: eb61d370-6e32-6776-d0bc-17197bacf84f
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/auditpol-set.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/auditpol-set
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/auditpol-set.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 7e0e8623-5dab-a295-cf5c-f256c98271d3
---

# auditpol set | Microsoft Learn

Sets the per-user audit policy, system audit policy, or auditing options.

To perform *set* operations on the *per-user* and *system* policies, you must have **Write** or **Full Control** permission for that object set in the security descriptor. You can also perform *set* operations if you have the **Manage auditing and security log** (SeSecurityPrivilege) user right. However, this right allows additional access that is not necessary to perform the overall *set* operations.

## Syntax

```
auditpol /set
[/user[:<username>|<{sid}>][/include][/exclude]]
[/category:<name>|<{guid}>[,:<name|<{guid}> ]]
[/success:<enable>|<disable>][/failure:<enable>|<disable>]
[/subcategory:<name>|<{guid}>[,:<name|<{guid}> ]]
[/success:<enable>|<disable>][/failure:<enable>|<disable>]
[/option:<option name> /value: <enable>|<disable>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /user | The security principal for whom the per-user audit policy specified by the category or subcategory is set. Either the category or subcategory option must be specified, as a security identifier (SID) or name. |
| /include | Specified with /user; indicates that the user's per-user policy will cause an audit to be generated even if it is not specified by the system audit policy. This setting is the default and is automatically applied if neither the /include nor /exclude parameters are explicitly specified. |
| /exclude | Specified with /user; indicates that the user's per-user policy will cause an audit to be suppressed regardless of the system audit policy. This setting is ignored for users who are members of the local Administrators group. |
| /category | One or more audit categories specified by globally unique identifier (GUID) or name. If no user is specified, the system policy is set. |
| /subcategory | One or more audit subcategories specified by GUID or name. If no user is specified, the system policy is set. |
| /success | Specifies success auditing. This setting is the default and is automatically applied if neither the /success nor /failure parameters are explicitly specified. This setting must be used with a parameter indicating whether to enable or disable the setting. |
| /failure | Specifies failure auditing. This setting must be used with a parameter indicating whether to enable or disable the setting. |
| /option | Sets the audit policy for the CrashOnAuditFail, FullprivilegeAuditing, AuditBaseObjects, or AuditBasedirectories options. |
| /sd | Sets the security descriptor used to delegate access to the audit policy. The security descriptor must be specified by using the Security Descriptor Definition Language (SDDL). The security descriptor must have a discretionary access control list (DACL). |
| /? | Displays help at the command prompt. |

## Examples

To set the per-user audit policy for all subcategories under the detailed Tracking category for the user mikedan so that all the user's successful attempts will be audited, type:

```
auditpol /set /user:mikedan /category:detailed Tracking /include /success:enable
```

To set the per-user audit policy for categories specified by name and GUID, and subcategories specified by GUID to suppress auditing for any successful or failed attempts, type:

```
auditpol /set /user:mikedan /exclude /category:Object Access,System,{6997984b-797a-11d9-bed3-505054503030}
/subcategory:{0ccee9210-69ae-11d9-bed3-505054503030},:{0ccee9211-69ae-11d9-bed3-505054503030}, /success:enable /failure:enable
```

To set the per-user audit policy for the specified user for all the categories for the suppression of auditing of all but successful attempts, type:

```
auditpol /set /user:mikedan /exclude /category:* /success:enable
```

To set the system audit policy for all subcategories under the detailed Tracking category to include auditing for only successful attempts, type:

```
auditpol /set /category:detailed Tracking /success:enable
```

Note

The failure setting is not altered.

To set the system audit policy for the Object Access and System categories (which is implied because subcategories are listed) and subcategories specified by GUIDs for the suppression of failed attempts and the auditing of successful attempts, type:

```
auditpol /set /subcategory:{0ccee9210-69ae-11d9-bed3-505054503030},{0ccee9211-69ae-11d9-bed3-505054503030}, /failure:disable /success:enable
```

To set the auditing options to the enabled state for the CrashOnAuditFail option, type:

```
auditpol /set /option:CrashOnAuditFail /value:enable
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [auditpol commands](auditpol)