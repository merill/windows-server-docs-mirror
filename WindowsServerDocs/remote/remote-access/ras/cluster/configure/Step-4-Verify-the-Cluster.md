---
layout: Conceptual
title: Step 4 Verify the Cluster | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-access/ras/cluster/configure/step-4-verify-the-cluster
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote
ms.update-cycle: 1095-days
description: Learn how to verify that you have correctly configured your DirectAccess cluster deployment.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: bd76f607-df82-8ba3-5109-2ace53edcfc5
document_version_independent_id: 4d2295fd-d6e5-5c9c-add1-48dc2049baff
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-access/ras/cluster/configure/Step-4-Verify-the-Cluster.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-access/ras/cluster/configure/step-4-verify-the-cluster
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-access/ras/cluster/configure/Step-4-Verify-the-Cluster.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: f1e8d3da-3f73-d0b8-6652-c00c7d9f60e6
---

# Step 4 Verify the Cluster | Microsoft Learn

This topic describes how to verify that you have correctly configured your DirectAccess cluster deployment.

### To verify access to internal resources through the cluster

1. Connect a DirectAccess client computer to the corporate network and obtain the group policy.
2. Connect the client computer to the external network and attempt to access internal resources.

    You should be able to access all corporate resources.
3. Test connectivity through each server in the cluster by turning off, or disconnecting from the external network, all but one of the cluster servers. On the client computer, attempt to access corporate resources. Repeat the test on a different cluster server.

    You should be able to access all corporate resources through each cluster server.