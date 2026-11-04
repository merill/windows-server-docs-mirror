---
layout: Conceptual
title: scwcmd configure | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/scwcmd-configure
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the scwcmd configure command, which applies a Security Configuration Wizard (SCW)-generated security policy to a computer.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: aeaceb6b-b829-802d-a268-f0c24aaa1e68
document_version_independent_id: 6f1e4a82-566b-7dfd-897f-e76209bf02ab
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/scwcmd-configure.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/scwcmd-configure
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/scwcmd-configure.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
platformId: 6717a0dc-98d3-59eb-14f8-d4d6ccd3ba63
---

# scwcmd configure | Microsoft Learn

Applies a Security Configuration Wizard (SCW)-generated security policy to a computer. This command-line tool also accepts a list of computer names as input.

## Syntax

```
scwcmd configure [[[/m:<computername> | /ou:<OuName>] /p:<policy>] | /i:<computerlist>] [/u:<username>] [/pw:<password>] [/t:<threads>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /m:`<computername>` | Specifies the NetBIOS name, DNS name, or IP address of the computer to configure. If the **/m** parameter is specified, then the **/p** parameter must also be specified. |
| /ou:`<OuName>` | Specifies the fully qualified domain name (FQDN) of an organizational unit (OU) in Active Directory Domain Services. If the **/ou** parameter is specified, then the **/p** parameter must also be specified. All computers in the OU will be configured against the given policy. |
| /p:`<policy>` | Specifies the path and file name of the .xml policy file to be used to perform the configuration. |
| /i:`<computerlist>` | Specifies the path and file name of an .xml file that contains a list of computers along with their expected policy files. All computers in the .xml file will be analyzed against their corresponding policy files. A sample .xml file is `%windir%\security\SampleMachineList.xml`. |
| /u:`<username>` | Specifies an alternate user credential to use when performing the configuration on a remote computer. The default is the logged on user. |
| /pw:`<password>` | Specifies an alternate user credential to use when performing the configuration on a remote computer. The default is the password of the logged on user. |
| /t:`<threads>` | Specifies the number of simultaneous outstanding configuration operations that should be maintained during the analysis. The value range is 1-1000, with a default value of 40. |
| /l | Causes the analysis process to be logged. One log file will be generated for each computer being analyzed. The log files will be stored in the same directory as the result files. Use the **/o** option to specify the directory for the result files. |
| /e | Log an event to the Application Event log if a mismatch is found. |
| /? | Displays help at the command prompt. |

## Examples

To configure a security policy against the file *webpolicy.xml*, type:

```
scwcmd configure /p:webpolicy.xml
```

To configure a security policy for the computer at *172.16.0.0* against the file *webpolicy.xml* by using the credentials of the *webadmin* account, type:

```
scwcmd configure /m:172.16.0.0 /p:webpolicy.xml /u:webadmin
```

To configure a security policy on all computers on the list *campusmachines.xml* with a *maximum of 100 threads*, type:

```
scwcmd configure /i:campusmachines.xml /t:100
```

To configure a security policy for the *WebServers OU* against the file *webpolicy.xml* by using the *DomainAdmin* credentials, type:

```
scwcmd configure /ou:OU=WebServers,DC=Marketing,DC=ABCCompany,DC=com /p:webpolicy.xml /u:DomainAdmin
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [scwcmd analyze command](scwcmd-analyze)
- [scwcmd register command](scwcmd-register)
- [scwcmd rollback command](scwcmd-rollback)
- [scwcmd transform command](scwcmd-transform)
- [scwcmd view command](scwcmd-view)