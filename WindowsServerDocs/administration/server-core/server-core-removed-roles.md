---
layout: Conceptual
title: Roles, Role Services, and Features not in Windows Server - Server Core | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/server-core/server-core-removed-roles
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: administration
ms.update-cycle: 1095-days
description: Learn about the roles and features not included in the Server Core installation option for Windows Server.
ms.mktglfcycl: manage
ms.sitesec: library
author: robinharwood
ms.author: roharwoo
ms.date: 2018-02-23T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: c3f61d1a-2618-d087-7506-96b7e4ef9fa5
document_version_independent_id: 2bfb97f6-7f20-f483-4e6f-c7ebac64d0fd
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/server-core/server-core-removed-roles.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/server-core/server-core-removed-roles
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/server-core/server-core-removed-roles.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ddab3cd8-636f-4a91-896e-1c23f399a6bd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f409bb5d-e203-40c5-9d95-0ee717231beb
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 65278aa1-c273-cb5f-3eb4-118bf58e68bc
---

# Roles, Role Services, and Features not in Windows Server - Server Core | Microsoft Learn

The following roles, role services, and features have been removed from the Server Core installation option of Windows Server. Use this information to help figure out if the Server Core option works for your environment.

Note

You can also see a list of the roles, role services, and features that [ARE included in Server Core](server-core-roles-and-services). It's a very large list, so for best results, search that list for the specific role or feature you're interested in.

## Roles not in Server Core

- Fax Server (**Fax**)
- MultiPoint Services (**MultiPointServerRole**)
- Network Policy and Access Services (**NPAS**)
- Windows Deployment Services (**WDS**) *(before Windows Server version 1803)*

## Role Services not in Server Core

Note that some Remote Desktop role services are included in Server Core (Connection Broker, Licensing, Virtualization Host), but others are NOT (Gateway, RD Session Host, Web Access).

- Print and Document Services \ Distributed Scan Server (**Print-Scan-Server**)
- Print and Document Services \ Internet Printing (**Print-Internet**)
- Remote Desktop Services \ Remote Desktop Gateway (**RDS-Gateway**)
- Remote Desktop Services \ Remote Desktop Session Host (**RDS-RD-Server**)
- Remote Desktop Services \ Remote Desktop Web Access (**RDS-Web-Access**)
- Role Service Web Server (IIS) \ Management Tools \ IIS Management Console (**Web-Mgmt-Console**)
- Role Service Web Server (IIS) \ Management Tools \ IIS 6 Management Compatibility \ IIS 6 Management Console (**Web-Lgcy-Mgmt-Console**)
- Windows Deployment Services \ Deployment Server (**WDS-Deployment**)
- Windows Deployment Services \ Transport Server (**WDS-Transport**) *(before Windows Server version 1803)*

## Features not in Server Core

- Background Intelligent Transfer Service (BITS) \ IIS Server Extension (**BITS-IIS-Ext**)
- BitLocker Network Unlock (**BitLocker-NetworkUnlock**)
- Direct Play (**Direct-Play**)
- Internet Printing Client (**Internet-Print-Client**)
- LPR Port Monitor (**LPR-Port-Monitor**)
- Message Queuing \ Message Queuing Services \ Multicasting Support (**MSMQ-Multicasting**)
- RAS Connection Manager Administration Kit (**CMAK**)
- Remote Assistance (**Remote-Assistance**)
- Remote Server Administration Tools \ Feature Administration Tools \ SMTP Server Tools (**RSAT-SMTP**)
- Remote Server Administration Tools \ Feature Administration Tools \ BitLocker Drive Encryption Administration Utilities \ BitLocker Drive Encryption Tools (**RSAT-Feature-Tools-BitLocker-RemoteAdminTool**)
- Remote Server Administration Tools \ Feature Administration Tools \ BITS Server Extensions Tools (**RSAT-Bits-Server**)
- Remote Server Administration Tools \ Feature Administration Tools \ Network Load Balancing Tools (**RSAT-NLB**)
- Remote Server Administration Tools \ Feature Administration Tools \ SNMP Tools (**RSAT-SNMP**)
- Remote Server Administration Tools \ Feature Administration Tools \ WINS Server Tools (**RSAT-WINS**)
- Remote Server Administration Tools \ Role Administration Tools \ Hyper-V Management Tools \ Hyper-V GUI Management Tools (**Hyper-V-Tools**)
- Remote Server Administration Tools \ Role Administration Tools \ Remote Desktop Services Tools \ Remote Desktop Gateway Tools (**RSAT-RDS-Tools**)
- Remote Server Administration Tools \ Role Administration Tools \ Remote Desktop Services Tools \ Remote Desktop Gateway Tools (**RSAT-RDS-Gateway**)
- Remote Server Administration Tools \ Role Administration Tools \ Remote Desktop Services Tools \ Remote Desktop Licensing Diagnoser Tools (**RSAT-RDS-Licensing-Diagnosis-UI**)
- Remote Server Administration Tools \ Role Administration Tools \ Remote Desktop Services Tools \ Remote Desktop Licensing Tools (**RDS-Licensing-UI**)
- Remote Server Administration Tools \ Role Administration Tools \ Windows Server Update Services Tools \ User Interface Management Console (**UpdateServices-UI**)
- Remote Server Administration Tools \ Role Administration Tools \ Active Directory Certificate Services Tools (**RSAT-ADCS**)
- Remote Server Administration Tools \ Role Administration Tools \ Active Directory Certificate Services Tools \ Certification Authority Management Tools (**RSAT-ADCS-Mgmt**)
- Remote Server Administration Tools \ Role Administration Tools \ Active Directory Certificate Services Tools \ Online Responder Tools (**RSAT-Online-Responder**)
- Remote Server Administration Tools \ Role Administration Tools \ Active Directory Rights Management Services Tools (**RSAT-ADRMS**)
- Remote Server Administration Tools \ Role Administration Tools \ Fax Server Tools (**RSAT-Fax**)
- Remote Server Administration Tools \ Role Administration Tools \ File Services Tools (**RSAT-File-Services**)
- Remote Server Administration Tools \ Role Administration Tools \ File Services Tools \ DFS Management Tools (**RSAT-DFS-Mgmt-Con**)
- Remote Server Administration Tools \ Role Administration Tools \ File Services Tools \ File Server Resource Manager Tools (**RSAT-FSRM-Mgmt**)
- Remote Server Administration Tools \ Role Administration Tools \ File Services Tools \ Services for Network File System Management Tools (**RSAT-NFS-Admin**)
- Remote Server Administration Tools \ Role Administration Tools \ Network Policy and Access Services Tools (**RSAT-NPAS**)
- Remote Server Administration Tools \ Role Administration Tools \ Print and Document Services Tools (**RSAT-Print-Services**)
- Remote Server Administration Tools \ Role Administration Tools \ Volume Activation Tools (**RSAT-VA-Tools**)
- Remote Server Administration Tools \ Role Administration Tools \ Windows Deployment Services Tools (**WDS-AdminPack**)
- Simple TCP/IP Services (**Simple-TCPIP**)
- SMTP Server (**SMTP-Server**)
- TFTP Client (**TFTP-Client**)
- WebDAV Redirector (**WebDAV-Redirector**)
- Windows Biometric Framework (**Biometric-Framework**)
- Windows Defender Features \ GUI for Windows Defender (**Windows-Defender-Gui**)
- Windows Identity Foundation 3.5 (**Windows-Identity-Foundation**)
- Windows PowerShell \ Windows PowerShell ISE (**PowerShell-ISE**)
- Windows Search Service (**Search-Service**)
- Windows TIFF IFilter (**Windows-TIFF-IFilter**)
- Wireless LAN Service (**Wireless-Networking**)
- XPS Viewer (**XPS-Viewer**)