---
layout: Conceptual
title: Verify Client Computer Settings | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/branchcache/deploy/verify-client-computer-settings
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Learn how to verify that the client computer is correctly configured for BranchCache.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2021-01-05T00:00:00.0000000Z
locale: en-us
document_id: 0713e488-0b7d-af7a-a3d6-2d822ea2a037
document_version_independent_id: 3f01550c-0eb1-5fc3-e1ac-8e018d1091e3
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/branchcache/deploy/Verify-Client-Computer-Settings.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/branchcache/deploy/verify-client-computer-settings
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/branchcache/deploy/Verify-Client-Computer-Settings.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c783a8fb-cf36-41ad-90c6-0692a0540484
platformId: 9d501250-ea96-0376-4117-bbfdfa55da58
---

# Verify Client Computer Settings | Microsoft Learn

You can use this procedure to verify that the client computer is correctly configured for BranchCache.

Note

This procedure includes steps for manually updating Group Policy and for restarting the BranchCache service. You do not need to perform these actions if you reboot the computer, as they will occur automatically in this circumstance.

You must be a member of **Administrators**, or equivalent to perform this procedure.

### To verify BranchCache client computer settings

1. To refresh Group Policy on the client computer whose BranchCache configuration you want to verify, run Windows PowerShell as an Administrator, type the following command, and then press ENTER.

    `gpupdate /force`
2. For client computers that are configured in hosted cache mode and are configured to automatically discover hosted cache servers by service connection point, run the following commands to stop and restart the BranchCache service.

    `net stop peerdistsvc`

    `net start peerdistsvc`
3. Inspect the current BranchCache operational mode by running the following command.

    `Get-BCStatus`
4. In Windows PowerShell, review the output of the **Get-BCStatus** command.

    The value for **BranchCacheIsEnabled** should be **True**.

    In **ClientSettings**, the value for **CurrentClientMode** should be **DistributedClient** or **HostedCacheClient**, depending on the mode that you configured using this guide.

    In **ClientSettings**, if you configured hosted cache mode and provided the names of your hosted cache servers during configuration, or if the client has automatically located hosted cache servers using service connection points, **HostedCacheServerList** should have a value that is the same as the name or names of your hosted cache servers. For example, if your hosted cache server is named HCS1 and your domain is corp.contoso.com, the value for **HostedCacheServerList** is **HCS1.corp.contoso.com**.
5. If any of the BranchCache settings listed above do not have the correct values, use the steps in this guide to verify the Group Policy or Local Computer Policy settings, as well as the firewall exceptions, that you configured, and ensure that they are correct. In addition, either restart the computer or follow the steps in this procedure to refresh Group Policy and restart the BranchCache service.