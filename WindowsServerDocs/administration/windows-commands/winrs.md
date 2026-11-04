---
layout: Conceptual
title: winrs | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/winrs
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the winrs command that allows you to manage and execute programs remotely.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2023-04-01T00:00:00.0000000Z
locale: en-us
document_id: 0a5939d3-d2d3-680f-5365-97d2ed3d6c58
document_version_independent_id: 3ae77896-fb5d-bfc6-6ec5-542344c3273b
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/winrs.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/winrs
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/winrs.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: fd7de9eb-1d98-3db3-f00a-7b917e6c408b
---

# winrs | Microsoft Learn

Windows remote Management using the winrs command enables you to manage and execute programs remotely.

## Syntax

```
winrs [/<parameter>[:<value>]] <command>
```

## Parameters

| Parameter | Description |
| --- | --- |
| /remote:&lt;endpoint&gt; | Specifies the target endpoint using a NetBIOS name or the standard connection:<br>- &lt;url&gt;: [&lt;transport&gt;://]&lt;target&gt;[:&lt;port&gt;]<br><br>if not specified, **/r:localhost** is used. |
| /unencrypted | Specifies that the messages to the remote shell aren't encrypted. This parameter is useful for troubleshooting or when the network traffic is already encrypted using **ipsec**, or when physical security is enforced.<br>By default, the messages are encrypted using Kerberos or NTLM keys.<br><br>This command-line option is ignored when HTTPS transport is selected. |
| /username:&lt;username&gt; | Specifies username on command line.<br>If not specified, the tool uses Negotiate authentication or prompt for the name.<br><br>If **/username** is specified, **/password** must also be specified. |
| /password:&lt;password&gt; | Specifies password on command line.<br>If **/password** isn't specified but **/username** is, the tool prompts for the password.<br><br>If **/password** is specified, **/username** must also be specified. |
| /timeout:&lt;seconds&gt; | This option is deprecated. |
| /directory:&lt;path&gt; | Specifies starting directory for remote shell.<br>If not specified, the remote shell starts in the user's home directory defined by the environment variable **%USERPROFILE%**. |
| /environment:&lt;string&gt;=&lt;value&gt; | Specifies a single environment variable to be set when shell starts, which allows changing default environment for shell.<br>Multiple occurrences of this switch must be used to specify multiple environment variables. |
| /noecho | Specifies that echo should be disabled. noecho may be necessary to ensure that user's answers to remote prompts aren't displayed locally.<br>By default echo is on. |
| /noprofile | Specifies that the user's profile shouldn't be loaded.<br>By default, the server attempts to load the user profile.<br><br>If the remote user isn't a local administrator on the target system, then this option is required (the default results in error.) |
| /allowdelegate | Specifies that the user's credentials can be used to access a remote share, for example, a different machine than the target endpoint. |
| /compression | Turn on compression. Older installations on remote machines might not support compression. <br>Default setting is off because older installations on remote machines might not support compression. |
| /usessl | Use an SSL connection when using a remote endpoint. Specifying SSL instead of the transport **https:** uses the default **WinRM** default port. |
| /? | Displays help at the command prompt. |

## Remarks

- All command-line options accept either short form or long form. For example, both **/r** and **/remote** are valid.
- To terminate the **/remote** command, the user can type **Ctrl-C** or **Ctrl-break**, which is sent to the remote shell. The second **Ctrl-C** forces termination of **winrs.exe**.
- To manage active remote shells or winrs configuration, use the WinRM tool. The URI alias to manage active shells is **shell/cmd**. The URI alias for winrs configuration is **winrm/config/winrs**.

## Examples

```
winrs /r:https://contoso.com command
```

```
winrs /r:contoso.com /usessl command
```

```
winrs /r:myserver command
```

```
winrs /r:http://127.0.0.1 command
```

```
winrs /r:http://169.51.2.101:80 /unencrypted command
```

```
winrs /r:https://[::FFFF:129.144.52.38] command
```

```
winrs /r:http://[1080:0:0:0:8:800:200C:417A]:80 command
```

```
winrs /r:https://contoso.com /t:600 /u:administrator /p:$%fgh7 ipconfig
```

```
winrs /r:myserver /env:path=^%path^%;c:\tools /env:TEMP=d:\temp config.cmd
```

```
winrs /r:myserver netdom join myserver /domain:testdomain /userd:johns /passwordd:$%fgh789
```

```
winrs /r:myserver /ad /u:administrator /p:$%fgh7 dir \\anotherserver\share
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)