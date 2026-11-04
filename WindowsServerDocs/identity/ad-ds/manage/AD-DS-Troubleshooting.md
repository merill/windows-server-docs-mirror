---
layout: Conceptual
title: AD DS Troubleshooting | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/ad-ds-troubleshooting
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: Overview of the troubleshooting section for AD DS
ms.author: roharwoo
author: robinharwood
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: troubleshooting-general
locale: en-us
document_id: 1634a9a7-326e-e566-8f23-5e79aec1e737
document_version_independent_id: 5e5e40a2-037e-c15f-4cb6-7ae0a72fc6a3
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/manage/AD-DS-Troubleshooting.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/manage/ad-ds-troubleshooting
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/manage/AD-DS-Troubleshooting.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
platformId: 3b723c60-39ea-c584-605a-46c37d669558
---

# AD DS Troubleshooting | Microsoft Learn

This section includes troubleshooting recommendations and procedures for diagnosing and fixing problems that may occur during Active Directory replication. It focuses on how to respond to Directory Service event log entries and how to interpret messages that tools such as Repadmin.exe and Dcdiag.exe might report.

Repadmin.exe and Dcdiag.exe are available on all domain controllers that run Windows Server 2012 R2 or later versions. For more information about how to use these tools to troubleshoot problems, see the following articles.

- [Configuring a Computer for Troubleshooting Active Directory](troubleshoot/configuring-a-computer-for-troubleshooting)
- [Troubleshooting Active Directory Replication Problems](troubleshoot/troubleshooting-active-directory-replication-problems)

Another useful technology is Event Tracing for Windows (ETW). You can use ETW to troubleshoot LDAP communications among the domain controllers. For more information, see [Using ETW to troubleshoot LDAP connections](troubleshoot/troubleshoot-ldap-using-etw).

You can also install Remote Server Administration Tools (RSAT) on a member server that is running Windows 10. For information about how to install RSAT, see [Remote Server Administration Tools](../../../remote/remote-server-administration-tools).