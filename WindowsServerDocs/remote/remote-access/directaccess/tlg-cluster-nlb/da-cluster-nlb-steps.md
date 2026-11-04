---
layout: Conceptual
title: Steps for Configuring the DirectAccess Cluster-NLB Test Lab | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-access/directaccess/tlg-cluster-nlb/da-cluster-nlb-steps
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote
ms.update-cycle: 1095-days
description: Learn how to configure the Remote Access infrastructure, configure the Remote Access servers and clients, and test DirectAccess connectivity from the Internet and Homenet subnets.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: cdd59001-f632-5c0e-122c-4e8abb1fa33d
document_version_independent_id: 7c51cb1a-141f-b42a-6fad-664308f58586
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-access/directaccess/tlg-cluster-nlb/da-cluster-nlb-steps.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-access/directaccess/tlg-cluster-nlb/da-cluster-nlb-steps
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-access/directaccess/tlg-cluster-nlb/da-cluster-nlb-steps.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 1af752f0-7c6c-f556-075c-5b066d81d612
---

# Steps for Configuring the DirectAccess Cluster-NLB Test Lab | Microsoft Learn

The following steps describe how to configure the Remote Access infrastructure, configure the Remote Access servers and clients, and test DirectAccess connectivity from the Internet and Homenet subnets.

In this test lab guide you will build a Network Load Balancing (NLB) enabled Remote Access cluster by performing the following steps:

- [STEP 1 Complete the DirectAccess Configuration](step-1-complete-the-directaccess-configuration). Complete all the steps in the [Test Lab Guide: Demonstrate DirectAccess Single Server Setup with Mixed IPv4 and IPv6](https://go.microsoft.com/fwlink/p/?LinkId=237004).
- [STEP 2: Configure EDGE1](step-2-configure-edge1). Configure the Remote Access role on EDGE1 for load balancing.
- [STEP 3: Install and configure EDGE2](step-3-install-and-configure-edge2). EDGE2 acts as the second Remote Access server in a Remote Access cluster.
- [STEP 4: Create the network load balanced Remote Access cluster](step-4-create-the-network-load-balanced-remote-access-cluster)-EDGE1 is configured as the first server in a Remote Access cluster. EDGE2 is joined to the cluster and NLB is configured for the cluster.
- [STEP 5: Test DirectAccess connectivity from the Internet and through the cluster](step-5-test-directaccess-connectivity-from-the-internet-and-through-the-cluster). After NLB and cluster configuration is complete you can test DirectAccess client connectivity through the load balanced cluster.
- [STEP 6: Test DirectAccess client connectivity from behind a NAT device](step-6-test-directaccess-client-connectivity-from-behind-a-nat-device). Move the client computer behind a NAT device to simulate testing DirectAccess client connectivity from behind a home router.
- [STEP 7: Test connectivity when returning to the Corpnet](step-7-test-connectivity-when-returning-to-the-corpnet). Make sure that the client computer can still access corporate resources when returning to Corpnet.
- [STEP 8: Snapshot the configuration](da-cluster-nlb-s8-snapshot). After completing the test lab, take a snapshot of the working Remote Access NLB cluster so that you can return to it later to test additional scenarios.