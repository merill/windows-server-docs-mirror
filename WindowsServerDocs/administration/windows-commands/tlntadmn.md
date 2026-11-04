---
layout: Conceptual
title: tlntadmn | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/tlntadmn
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the tlntadmn command, which administers a local or remote computer, running the telnet Server Service.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 33e3e5f8-5ac6-a38e-b305-731c485446da
document_version_independent_id: 0dd6d076-6a2b-520b-abc9-fea848188cc4
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/tlntadmn.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/tlntadmn
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/tlntadmn.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: d04c988b-1f3f-f9d1-b882-c9d753e61c4b
---

# tlntadmn | Microsoft Learn

Administers a local or remote computer that is running the telnet Server Service. If used without parameters, **tlntadmn** displays the current server settings.

This command requires you to log on to the local computer with administrative credentials. To administer a remote computer, you must also provide administrative credentials for the remote computer. You can do so by logging on to the local computer with an account that has administrative credentials for both the local computer and the remote computer. If you can't use this method, you can use the **-u** and **-p** parameters to provide administrative credentials for the remote computer.

## Syntax

```
tlntadmn [<computername>] [-u <username>] [-p <password>] [{start | stop | pause | continue}] [-s {<sessionID> | all}] [-k {<sessionID> | all}] [-m {<sessionID> | all}  <message>] [config [dom = <domain>] [ctrlakeymap = {yes | no}] [timeout = <hh>:<mm>:<ss>] [timeoutactive = {yes | no}] [maxfail = <attempts>] [maxconn = <connections>] [port = <number>] [sec {+ | -}NTLM {+ | -}passwd] [mode = {console | stream}]] [-?]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<computername>` | Specifies the name of the server to connect to. The default is the local computer. |
| -u `<username> -p <password>` | Specifies administrative credentials for a remote server that you want to administer. This parameter is required if you want to administer a remote server to which you are not logged on with administrative credentials. |
| start | starts the telnet Server Service. |
| stop | Stops the telnet Server Service |
| pause | Pauses the telnet Server Service. No new connections will be accepted. |
| continue | Resumes the telnet Server Service. |
| -s `{<sessionID> | all}` | Displays active telnet sessions. |
| -k `{<sessionID> | all}` | Ends telnet sessions. Type the Session ID to end a specific session, or type all to end all the sessions. |
| -m `{<sessionID> | all}  <message>` | Sends a message to one or more sessions. Type the session ID to send a message to a specific session, or type all to send a message to all sessions. type the message that you want to send between quotation marks. |
| config dom = `<domain>` | Configures the default domain for the server. |
| config ctrlakeymap = `{yes | no}` | Specifies if you want the telnet server to interpret CTRL+A as ALT. Type **yes** to map the shortcut key, or type **no** to prevent the mapping. |
| config timeout = `<hh>:<mm>:<ss>` | Sets the time-out period in hours, minutes, and seconds. |
| config timeoutactive = `{yes | no}` | Enables the idle session timeout. |
| config maxfail = `<attempts>` | Sets the maximum number of failed logon attempts before disconnecting. |
| config maxconn = `<connections>` | Sets the maximum number of connections. |
| config port = `<number>` | Sets the telnet port. You must specify the port with an integer smaller than 1024. |
| config sec `{+ | -}NTLM {+ | -}passwd` | Specifies whether you want to use NTLM, a password, or both to authenticate logon attempts. To use a particular type of authentication, type a plus sign (**+**) before that type of authentication. To prevent using a particular type of authentication, type a minus sign (**-**) before that type of authentication. |
| config mode = `{console | stream}` | Specifies the mode of operation. |
| -? | Displays help at the command prompt. |

## Examples

To configure the idle session timeout to 30 minutes, type:

```
tlntadmn config timeout=0:30:0
```

To display active telnet sessions, type:

```
tlntadmn -s
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [telnet Operations Guide](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc753164%28v=ws.10%29)