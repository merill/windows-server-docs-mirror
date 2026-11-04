---
layout: Conceptual
title: Auditing Enhancements to AD FS in Windows Server 2016 | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/technical-reference/auditing-enhancements-to-ad-fs-in-windows-server
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Auditing Enhancements to AD FS in Windows Server 2016'
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: b3914a25-9e0b-bd12-746f-5afc783e151d
document_version_independent_id: e32609be-cbc2-c1d5-5037-bf0d0d7ac056
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/technical-reference/auditing-enhancements-to-ad-fs-in-windows-server.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/technical-reference/auditing-enhancements-to-ad-fs-in-windows-server
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/technical-reference/auditing-enhancements-to-ad-fs-in-windows-server.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 36273b5a-7c3e-ab45-0cca-ea2fb7c1aa2c
---

# Auditing Enhancements to AD FS in Windows Server 2016 | Microsoft Learn

Currently, in AD FS for Windows Server 2012 R2 there are numerous audit events generated for a single request and the relevant information about a log-in or token issuance activity is either absent (in some versions of AD FS) or spread across multiple audit events. By default the AD FS audit events are turned off due to their verbose nature.

With the release of AD FS in Windows Server 2016, auditing has become more streamlined and less verbose.

## Auditing levels in AD FS for Windows Server 2016

By default, AD FS in Windows Server 2016 has basic auditing enabled. With basic auditing, administrators will see 5 or less events for a single request. This marks a significant decrease in the number of events administrators have to look at, in order to see a single request. The auditing level can be raised or lowered using the PowerShell cmdlet: Set-AdfsProperties -AuditLevel. The table below explains the available auditing levels.

| Audit Level | PowerShell syntax | Description |
| --- | --- | --- |
| None | Set-AdfsProperties - AuditLevel None | Auditing is disabled and no events will be logged. |
| Basic (Default) | Set-AdfsProperties - AuditLevel Basic | No more than 5 events will be logged for a single request |
| Verbose | Set-AdfsProperties - AuditLevel Verbose | All events will be logged. This will log a significant amount of information per request. |

To view the current auditing level, you can use the PowerShell cmdlet: Get-AdfsProperties.

![Screenshot that shows how to use the Get-AdfsProperties cmdlet.](media/auditing-enhancements-to-ad-fs-in-windows-server-2016/adfs_audit_1.png)

The auditing level can be raised or lowered using the PowerShell cmdlet: Set-AdfsProperties -AuditLevel.

![audit enhancements](media/auditing-enhancements-to-ad-fs-in-windows-server-2016/adfs_audit_2.png)

## Types of Audit Events

AD FS Audit Events can be of different types, based on the different types of requests processed by AD FS. Each type of Audit Event has specific data associated with it. The type of audit events can be differentiated between login requests (i.e. token requests) versus system requests (server-server calls including fetching configuration information).

The table below describes the basic types of audit events.

| Audit Event Type | Event ID | Description |
| --- | --- | --- |
| Fresh Credential Validation Success | 1202 | A request where fresh credentials are validated successfully by the Federation Service. This includes WS-Trust, WS-Federation, SAML-P (first leg to generate SSO) and OAuth Authorize Endpoints. |
| Fresh Credential Validation Error | 1203 | A request where fresh credential validation failed on the Federation Service. This includes WS-Trust, WS-Fed, SAML-P (first leg to generate SSO) and OAuth Authorize Endpoints. |
| Application Token Success | 1200 | A request where a security token is issued successfully by the Federation Service. For WS-Federation, SAML-P this is logged when the request is processed with the SSO artifact. (such as the SSO cookie). |
| Application Token Failure | 1201 | A request where security token issuance failed on the Federation Service. For WS-Federation, SAML-P this is logged when the request was processed with the SSO artifact. (such as the SSO cookie). |
| Password Change Request Success | 1204 | A transaction where the password change request was successfully processed by the Federation Service. |
| Password Change Request Error | 1205 | A transaction where the password change request failed to be processed by the Federation Service. |
| Sign Out Success | 1206 | Describes a successful sign-out request. |
| Sign Out Failure | 1207 | Describes a failed sign-out request. |