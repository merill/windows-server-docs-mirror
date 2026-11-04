---
layout: Conceptual
title: whoami | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/whoami
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for whoami, which displays user, group and privileges information for the user who is currently logged on to the local system.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2025-05-23T00:00:00.0000000Z
locale: en-us
document_id: 15c3e19b-dd81-20a2-f797-9590d37cb84e
document_version_independent_id: f3d14a6d-f4fb-971f-c648-d69439e1b81e
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/whoami.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/whoami
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/whoami.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 478d882a-03b1-04fa-3ddd-4821bb5f4afe
---

# whoami | Microsoft Learn

The `whoami` command shows information about the user, groups, and privileges for the account currently logged on to the local system. When run without any parameters, `whoami` returns the current domain and user name.

## Syntax

```
whoami [/upn | /fqdn | /logonid]
whoami {[/user] [/groups] [/claims] [/priv]} [/fo <format>] [/nh]
whoami /all [/fo <format>] [/nh]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /upn | Displays the user name in user principal name (UPN) format. |
| /fqdn | Displays the user name in fully qualified domain name (FQDN) format. |
| /logonid | Displays the logon ID of the current user. |
| /user | Displays the current domain and user name and the security identifier (SID). |
| /groups | Displays the user groups to which the current user belongs. |
| /claims | Displays the claims for current user, such as claim name, flags, type and values. |
| /priv | Displays the security privileges of the current user. |
| /fo &lt;format&gt; | Specifies the output format. Valid values include:- **table** - Displays output in a table. This is the default value.<br>- **list** - Displays output in a list.<br>- **csv** - Displays output in comma-separated value (CSV) format. |
| /all | Displays all information in the current access token, including the current user name, security identifiers (SID), privileges, and groups that the current user belongs to. |
| /nh | Specifies that the column header shouldn't be displayed in the output. This is valid only for table and CSV formats. |
| /? | Displays help at the command prompt. |

## Examples

To display the domain and user name of the person who is currently logged on to this computer, type:

```
whoami
```

Output similar to the following appears:

```
DOMAIN1\administrator
```

To display all of the information in the current access token, type:

```
whoami /all
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)