---
layout: Conceptual
title: SMB - File and printer sharing ports should be open | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/file-server/best-practices-analyzer/smb-open-file-sharing-ports
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: Learn how to keep file and printer sharing ports open for Server Message Block (SMB)-based network services and resolve the Best Practices Analyzer scan issue.
ms.date: 2023-03-20T00:00:00.0000000Z
author: robinharwood
ms.author: roharwoo
ms.topic: troubleshooting-problem-resolution
locale: en-us
document_id: 3de18f70-664d-1e0a-9f41-13ea5c74a422
document_version_independent_id: a21b8ac8-d637-9d15-bc8e-e2f43cd7f6cc
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/file-server/best-practices-analyzer/smb-open-file-sharing-ports.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/file-server/best-practices-analyzer/smb-open-file-sharing-ports
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/file-server/best-practices-analyzer/smb-open-file-sharing-ports.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 1d37b483-7037-70dd-640a-dee02aec3d02
---

# SMB - File and printer sharing ports should be open | Microsoft Learn

> 
> **Applies To**: Windows Server 2022, Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2

When a Best Practices Analyzer scan for Server Message Block (SMB)-based network services identifies that firewall ports for file and printer sharing aren't open, follow the steps in this article to resolve the issue.

| Operating system | Product/Feature | Severity | Category |
| --- | --- | --- | --- |
| Windows Server | File Services | Error | Configuration |

Note

This article addresses a specific issue identified by a Best Practices Analyzer scan. Apply the information in this article only to computers that have a File Services Best Practices Analyzer scan that reports the specific port issue. For more information about best practices and scans, see [Best Practices Analyzer](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd759260%28v=ws.11%29).

## Identify the issue

A File Services Best Practices Analyzer scan reports that firewall ports necessary for file and printer sharing aren't open (ports 445 and 139).

The issue prevents computer access to shared folders and other SMB-based network services on the server.

## Resolve the issue

To resolve the issue, enable file and printer sharing to communicate through the computer's firewall. To complete the procedure, you must be a member of the **Administrators group** (or equivalent), at a minimum.

To open the firewall ports and enable file and printer sharing, complete the following steps:

1. Open Control Panel, select **System and Security**, and then select **Windows Defender Firewall**.
2. On the left, select **Advanced settings**. The Windows Defender Firewall console opens and shows the advanced settings.
3. In the Windows Defender Firewall console on the left, select **Inbound Rules**.
4. Under **Inbound Rules**, locate the following two rules:

    - **File and Printer Sharing (NB-Session-In)**
    - **File and Printer Sharing (SMB-In)**
5. For each rule, select and hold (or right-click) the rule, and then select **Enable Rule**.

Note

The preceding steps configure Windows Defender Firewall on a single server. If you manage applicable devices with Microsoft Intune, you can centrally deploy Windows Defender Firewall policy and firewall rules to multiple devices instead of configuring each server locally. Intune doesn't run the Best Practices Analyzer or convert its findings automatically. Instead, you define the equivalent inbound firewall rules for file and printer sharing in an endpoint security firewall policy. For the procedure, see [Firewall policy for endpoint security in Intune](/en-us/intune/device-configuration/endpoint-security/firewall).

## Related links

- [Firewall policy for endpoint security in Intune](/en-us/intune/device-configuration/endpoint-security/firewall)
- [Understanding shared folders and the Windows Firewall](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731402%28v=ws.11%29)