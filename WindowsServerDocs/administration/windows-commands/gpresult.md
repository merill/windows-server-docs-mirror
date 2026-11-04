---
layout: Conceptual
title: gpresult | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/gpresult
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the gpresult command, which displays the Resultant Set of Policy (RSoP) information for a remote user and computer.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2023-09-28T00:00:00.0000000Z
locale: en-us
document_id: b095f55a-3e89-09f4-7735-ecb4be8ba6ff
document_version_independent_id: 1fbbe8ab-ca51-8535-d8f6-db058ae79248
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/gpresult.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/gpresult
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/gpresult.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 79afdf07-fa17-fd76-e035-377d332f2fb3
---

# gpresult | Microsoft Learn

Displays the Resultant Set of Policy (RSoP) information for a remote user and computer. To use RSoP reporting for remotely targeted computers through the firewall, you must have firewall rules that enable inbound network traffic on the ports.

## Syntax

```
gpresult [/s <system> [/u <username> [/p [<password>]]]] [/user [<targetdomain>\]<targetuser>] [/scope {user | computer}] {/r | /v | /z | [/x | /h] <filename> [/f] | /?}
```

Note

Except when using **/?**, you must include an output option, **/r**, **/v**, **/z**, **/x**, or **/h**.

### Parameters

| Parameter | Description |
| --- | --- |
| /s `<system>` | Specifies the name or IP address of a remote computer. Don't use backslashes. The default is the local computer. |
| /u `<username>` | Uses the credentials of the specified user to run the command. The default user is the user who is signed in to the computer that issues the command. |
| /p `[<password>]` | Specifies the password of the user account that is provided in the **/u** parameter. If **/p** is omitted, **gpresult** prompts for the password. The **/p** parameter can't be used with **/x** or **/h**. |
| /user `[<targetdomain>\]<targetuser>]` | Specifies the remote user whose RSoP data is to be displayed. |
| /scope `{user | computer}` | Displays RSoP data for either the user or the computer. If **/scope** is omitted, **gpresult** displays RSoP data for both the user and the computer. |
| `[/x | /h] <filename>` | Saves the report in either XML (**/x**) or HTML (**/h**) format at the location and with the file name that is specified by the *filename* parameter. Can't be used with **/u**, **/p**, **/r**, **/v**, or **/z**. |
| /f | Forces **gpresult** to overwrite the file name that is specified in the **/x** or **/h** option. |
| /r | Displays RSoP summary data. |
| /v | Displays verbose policy information. This includes detailed settings that were applied with a precedence of 1. |
| /z | Displays all available information about Group Policy. This includes detailed settings that were applied with a precedence of 1 and higher. |
| /? | Displays help at the command prompt. |

#### Remarks

- Group Policy is the primary administrative tool for defining and controlling how programs, network resources, and the operating system operate for users and computers in an organization. In an active directory environment, Group Policy is applied to users or computers based on their membership in sites, domains, or organizational units.
- Because you can apply overlapping policy settings to any computer or user, the Group Policy feature generates a resulting set of policy settings when the user signs in. The **gpresult** command displays the resulting set of policy settings that were enforced on the computer for the specified user when the user signed in.
- Because **/v** and **/z** produce much information, it's useful to redirect output to a text file (for example, `gpresult/z >policy.txt`).
- On ARM64 versions of Windows, only the `gpresult` in SysWow64 works with the `/h` parameter.

### Examples

To retrieve RSoP data for only the remote user *maindom\targetuser*, on the computer *srvmain*, enter:

```
gpresult /s srvmain /user maindom\targetuser /scope user /r
```

To save all available information about Group Policy to a file named *policy.txt* for only the remote user *maindom\targetuser*, on the computer *srvmain*, enter:

```
gpresult /s srvmain /user maindom\targetuser /z > policy.txt
```

To display RSoP data for the signed-in user, *maindom\hiropln* with the password *p@ssW23*, for the computer *srvmain*, enter:

```
gpresult /s srvmain /u maindom\hiropln /p p@ssW23 /r
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)