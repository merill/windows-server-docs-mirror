---
layout: Conceptual
title: Use Windows PowerShell to Configure Non-Domain Member Client Computers | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/branchcache/deploy/use-windows-powershell-to-configure-non-domain-member-client-computers
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Learn how to manually configure a BranchCache client computer for distributed cache mode or hosted cache mode.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2021-01-05T00:00:00.0000000Z
locale: en-us
document_id: ffcd9d13-bc69-b230-f133-48f536400849
document_version_independent_id: 89d74340-d9cc-9e54-71d8-169870312797
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/branchcache/deploy/Use-Windows-PowerShell-to-Configure-Non-Domain-Member-Client-Computers.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/branchcache/deploy/use-windows-powershell-to-configure-non-domain-member-client-computers
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/branchcache/deploy/Use-Windows-PowerShell-to-Configure-Non-Domain-Member-Client-Computers.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: e97f6132-c2d6-d71b-0cdd-58a8980d87c4
---

# Use Windows PowerShell to Configure Non-Domain Member Client Computers | Microsoft Learn

You can use this procedure to manually configure a BranchCache client computer for distributed cache mode or hosted cache mode.

Note

If you have configured BranchCache client computers using Group Policy, the Group Policy settings override any manual configuration of client computers to which the policies are applied.

Membership in **Administrators**, or equivalent is the minimum required to perform this procedure.

### To enable BranchCache distributed or hosted cache mode

1. On the BranchCache client computer that you want to configure, run Windows PowerShell as an Administrator, and then do one of the following.

    - To configure the client computer for BranchCache distributed cache mode, type the following command, and then press ENTER.

        `Enable-BCDistributed`
    - To configure the client computer for BranchCache hosted cache mode, type the following command, and then press ENTER.

        `Enable-BCHostedClient`

        Tip

        If you want to specify the available hosted cache servers, use the `-ServerNames` parameter with a comma separated list of your hosted cache servers as the parameter value. For example, if you have two hosted cache servers named HCS1 and HCS2, configure the client computer for hosted cache mode with the following command.

        `Enable-BCHostedClient -ServerNames HCS1,HCS2`