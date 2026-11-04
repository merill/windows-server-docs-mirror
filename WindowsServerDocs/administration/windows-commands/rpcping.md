---
layout: Conceptual
title: rpcping | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/rpcping
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the rpcping command, which confirms the RPC connectivity between the computer running Microsoft Exchange Server and any of the supported Microsoft Exchange Client workstations on the network.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 8f3b5d48-6ea4-85f0-e493-96d7c16a9fac
document_version_independent_id: 927a2aa4-600d-4274-a808-8fc27b2220f0
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/rpcping.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/rpcping
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/rpcping.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/0b654e73-5728-4af3-8c2e-17bfbf4c9f23
- https://authoring-docs-microsoft.poolparty.biz/devrel/390894b2-8646-4f7e-b8cd-2209156272a9
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/11529658-843a-40bd-b2f8-5eed118be619
- https://authoring-docs-microsoft.poolparty.biz/devrel/12b23b77-ab37-4318-a036-4f6690586386
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: b20b3fb1-818a-621f-8767-07966b3ba6bf
---

# rpcping | Microsoft Learn

Confirms the RPC connectivity between the computer running Microsoft Exchange Server and any of the supported Microsoft Exchange Client workstations on the network. This utility can be used to check if the Microsoft Exchange Server services are responding to RPC requests from the client workstations via the network.

## Syntax

```
rpcping [/t <protseq>] [/s <server_addr>] [/e <endpoint>
        |/f <interface UUID>[,majorver]] [/O <interface object UUID]
        [/i <#_iterations>] [/u <security_package_id>] [/a <authn_level>]
        [/N <server_princ_name>] [/I <auth_identity>] [/C <capabilities>]
        [/T <identity_tracking>] [/M <impersonation_type>]
        [/S <server_sid>] [/P <proxy_auth_identity>] [/F <RPCHTTP_flags>]
        [/H <RPC/HTTP_authn_schemes>] [/o <binding_options>]
        [/B <server_certificate_subject>] [/b] [/E] [/q] [/c]
        [/A <http_proxy_auth_identity>] [/U <HTTP_proxy_authn_schemes>]
        [/r <report_results_interval>] [/v <verbose_level>] [/d]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /t `<protseq>` | Specifies the protocol sequence to use. Can be one of the standard RPC protocol sequences: ncacn\_ip\_tcp, ncacn\_np, or ncacn\_http.<br>If not specified, default is ncacn\_ip\_tcp. |
| /s `<server_addr>` | Specifies the server address. If not specified, the local machine will be pinged. |
| /e `<endpoint>` | Specifies the endpoint to ping. If none is specified, the endpoint mapper on the target machine will be pinged.<br>This option is mutually exclusive with the interface (**/f**) option. |
| /o `<binding_options>` | Specifies the binding options for the RPC ping. |
| /f `<interface UUID>[,Majorver]` | Specifies the interface to ping. This option is mutually exclusive with the endpoint option. The interface is specified as a UUID.<br>if the *majorver* is not specified, version 1 of the interface will be sought.<br><br>When interface is specified, **rpcping** will query the endpoint mapper on the target machine to retrieve the endpoint for the specified interface. The endpoint mapper will be queried using the options specified in the command line. |
| /O `<object UUID>` | Specifies the object UUID if the interface registered one. |
| /i `<#_iterations>` | Specifies the number of calls to make. The default is 1. This option is useful for measuring connection latency if multiple iterations are specified. |
| /u `<security_package_id>` | Specifies the security package (security provider) RPC will use to make the call. The security package is identified as a number or a name. If a number is used it is the same number as in the RpcBindingSetAuthInfoEx API. If you specify this option, you must specify an authentication level other than *none*. There's no default for this option. If it isn't specified, RPC won't use security for the ping. The list below shows the names and numbers. Names are not case sensitive:<br>- Negotiate / 9 or one of nego, snego or negotiate<br>- NTLM / 10 or NTLM<br>- SChannel / 14 or SChannel<br>- Kerberos / 16 or Kerberos<br>- Kernel / 20 or Kernel |
| /a `<authn_level>` | Specifies the authentication level to use. If this option is specified, the security package ID (**/u**) must also be specified. If this option isn't specified, RPC won't use security for the ping. There's no default for this option. Possible values are:<br>- connect<br>- call<br>- pkt<br>- integrity<br>- privacy |
| /N `<server_princ_name>` | Specifies a server principal name.<br>This field can be used only when authentication level and security package are selected. |
| /I `<auth_identity>` | Allows you to specify alternative identity to connect to the server. The identity is in the form user,domain,password. If the user name, domain, or password have special characters that can be interpreted by the shell, enclose the identity in double quotes. You can specify `\*` instead of the password and RPC will prompt you to enter the password without echoing it on the screen. If this field is not specified, the identity of the logged on user will be used.<br>This field can be used only when authentication level and security package are selected. |
| /C `<capabilities>` | Specifies a hexadecimal bitmask of flags. This field can be used only when authentication level and security package are selected. |
| /T `<identity_tracking>` | Specifies static or dynamic. If not specified, dynamic is the default.<br>This field can be used only when authentication level and security package are selected. |
| /M `<impersonation_type>` | Specifies anonymous, identify, impersonate or delegate. Default is impersonate.<br>This field can be used only when authentication level and security package are selected. |
| /S `<server_sid>` | Specifies the expected SID of the server.<br>This field can be used only when authentication level and security package are selected. |
| /P `<proxy_auth_identity>` | Specifies the identity to authenticate with to the RPC/HTTP proxy. Has the same format as for the **/I** option. You must specify security package (**/u**), authentication level (**/a**), and authentication schemes (**/H**) in order to use this option. |
| /F `<RPCHTTP_flags>` | Specifies the flags to pass for RPC/HTTP front end authentication. The flags may be specified as numbers or names The currently recognized flags are:<br>- Use SSL / 1 or ssl or use\_ssl<br>- Use first auth scheme / 2 or first or use\_first<br><br>You must specify security package (**/u**) and authentication level (**/a**) to use this option. |
| /H `<RPC/HTTP_authn_schemes>` | Specifies the authentication schemes to use for RPC/HTTP front end authentication. This option is a list of numerical values or names separated by comma. Example: Basic,NTLM. Recognized values are (names are not case sensitive):<br>- Basic / 1 or Basic<br>- NTLM / 2 or NTLM<br>- Certificate / 65536 or Cert<br><br><br>You must specify security package (**/u**) and authentication level (**/a**) in order to use this option. |
| /B `<server_certificate_subject>` | Specifies the server certificate subject. You must use SSL for this option to work.<br>You must specify security package (**/u**) and authentication level (**/a**) in order to use this option. |
| /b | Retrieves the server certificate subject from the certificate sent by the server and prints it to a screen or a log file. Valid only when the Proxy echo only option (/E) and the use SSL options are specified.<br>You must specify security package (**/u**) and authentication level (**/a**) in order to use this option. |
| /R | Specifies the HTTP proxy. If *none*, the RPC proxy is used. The value *default* means to use the IE settings in your client machine. Any other value will be treated as the explicit HTTP proxy. If you do not specify this flag, the default value is assumed, that is, the IE settings are checked. This flag is valid only when the **/E** (echo Only) flag is enabled. |
| /E | Restricts the ping to the RPC/HTTP proxy only. The ping does not reach the server. Useful when trying to establish whether the RPC/HTTP proxy is reachable. To specify an HTTP proxy, use the /R flag. If an HTTP proxy is specified in the /o flag, this option will be ignored.<br>You must specify security package (**/u**) and authentication level (**/a**) in order to use this option. |
| /q | Specifies quiet mode. Does not issue any prompts except for passwords. Assumes *Y* response to all queries. Use this option with care. |
| /c | Use smart card certificate. rpcping will prompt user to choose smart card. |
| /A | Specifies the identity with which to authenticate to the HTTP proxy. Has the same format as for the /I option.<br>You must specify authentication schemes (/U), security package (**/u**) and authentication level (**/a**) in order to use this option. |
| /U | Specifies the authentication schemes to use for HTTP proxy authentication. This option is a list of numerical values or names separated by comma. Example: Basic,NTLM. Recognized values are (names are not case sensitive):<br>- Basic / 1 or Basic<br>- NTLM / 2 or NTLM<br><br>You must specify security package (**/u**) and authentication level (**/a**) in order to use this option. |
| /r | If multiple iterations are specified, this option will make **rpcping** display current execution statistics periodically instead after the last call. The report interval is given in seconds. Default is 15. |
| /v | Tells **rpcping** how verbose to make the output. Default value is 1. 2 and 3 provide more output from **rpcping**. |
| /d | Launches RPC network diagnostic UI. |
| /p | Specifies to prompt for credentials if authentication fails. |
| /? | Displays help at the command prompt. |

## Examples

To find out if the Exchange server you connect through RPC/HTTP is accessible, type:

```
rpcping /t ncacn_http /s exchange_server /o RpcProxy=front_end_proxy /P username,domain,* /H Basic /u NTLM /a connect /F 3
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)