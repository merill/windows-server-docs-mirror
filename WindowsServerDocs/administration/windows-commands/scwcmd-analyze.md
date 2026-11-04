---
layout: Conceptual
title: scwcmd analyze | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/scwcmd-analyze
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the scwcmd analyze command, which determines whether a computer is in compliance with a policy.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 8150ad57-4231-50ea-73a5-fb388a623c1f
document_version_independent_id: 70530d42-9b6c-ccbf-13aa-d12063f7ac1c
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/scwcmd-analyze.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/scwcmd-analyze
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/scwcmd-analyze.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: 15ca79ef-bd88-f258-5ae5-53d1aa823eeb
---

# scwcmd analyze | Microsoft Learn

Determines whether a computer is in compliance with a policy. Results are returned in an .xml file.

This command also accepts a list of computer names as input. To view the results in your browser, use **scwcmd view** and specify `%windir%\security\msscw\TransformFiles\scwanalysis.xsl` as the .xsl transform.

## Syntax

```
scwcmd analyze [[[/m:<computername> | /ou:<OuName>] /p:<policy>] | /i:<computerlist>] [/o:<resultdir>] [/u:<username>] [/pw:<password>] [/t:<threads>] [/l] [/e]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /m:`<computername>` | Specifies the NetBIOS name, DNS name, or IP address of the computer to analyze. If the **/m** parameter is specified, then the **/p** parameter must also be specified. |
| /ou:`<OuName>` | Specifies the fully qualified domain name (FQDN) of an organizational unit (OU) in Active Directory Domain Services. If the **/ou** parameter is specified, then the **/p** parameter must also be specified. All computers in the OU will be analyzed against the given policy. |
| /p:`<policy>` | Specifies the path and file name of the .xml policy file to be used to perform the analysis. |
| /i:`<computerlist>` | Specifies the path and file name of an .xml file that contains a list of computers along with their expected policy files. All computers in the .xml file will be analyzed against their corresponding policy files. A sample .xml file is `%windir%\security\SampleMachineList.xml`. |
| /o:`<resultdir>` | Specifies the path and directory where the analysis result files should be saved. The default is the current directory. |
| /u:`<username>` | Specifies an alternate user credential to use when performing the analysis on a remote computer. The default is the logged on user. |
| /pw:`<password>` | Specifies an alternate user credential to use when performing the analysis on a remote computer. The default is the password of the logged on user. |
| /t:`<threads>` | Specifies the number of simultaneous outstanding analysis operations that should be maintained during the analysis. The value range is 1-1000, with a default value of 40. |
| /l | Causes the analysis process to be logged. One log file will be generated for each computer being analyzed. The log files will be stored in the same directory as the result files. Use the **/o** option to specify the directory for the result files. |
| /e | Log an event to the Application Event log if a mismatch is found. |
| /? | Displays help at the command prompt. |

## Examples

To analyze a security policy against the file *webpolicy.xml*, type:

```
scwcmd analyze /p:webpolicy.xml
```

To analyze a security policy on the computer named *webserver* against the file *webpolicy.xml* by using the credentials of the *webadmin* account, type:

```
scwcmd analyze /m:webserver /p:webpolicy.xml /u:webadmin
```

To analyze a security policy against the file *webpolicy.xml*, with a *maximum of 100 threads*, and output the results to a file named results in the *resultserver* share, type:

```
scwcmd analyze /i:webpolicy.xml /t:100 /o:\\resultserver\results
```

To analyze a security policy for the *WebServers OU* against the file *webpolicy.xml* by using the *DomainAdmin* credentials, type:

```
scwcmd analyze /ou:OU=WebServers,DC=Marketing,DC=ABCCompany,DC=com /p:webpolicy.xml /u:DomainAdmin
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [scwcmd configure command](scwcmd-configure)
- [scwcmd register command](scwcmd-register)
- [scwcmd rollback command](scwcmd-rollback)
- [scwcmd transform command](scwcmd-transform)
- [scwcmd view command](scwcmd-view)