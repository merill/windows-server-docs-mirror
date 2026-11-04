---
layout: Conceptual
title: Steps for Configuring the Test Lab | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-access/directaccess/tlg-multisite/steps-for-configuring-the-test-lab-4
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote
ms.update-cycle: 1095-days
description: Learn how to configure the Remote Access infrastructure, configure the Remote Access servers and clients and test DirectAccess connectivity from the Internet and Homenet subnets.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: dcb3f5fb-6a88-cb57-78c0-963c78a394ca
document_version_independent_id: 55d980df-e89d-615c-d1d3-d4ac2c0589fa
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-access/directaccess/tlg-multisite/Steps-for-Configuring-the-Test-Lab-4.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-access/directaccess/tlg-multisite/steps-for-configuring-the-test-lab-4
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-access/directaccess/tlg-multisite/Steps-for-Configuring-the-Test-Lab-4.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: f51db89a-1de8-41df-6b10-eb2bba46a36f
---

# Steps for Configuring the Test Lab | Microsoft Learn

The following steps describe how to configure the Remote Access infrastructure, configure the Remote Access servers and clients and test DirectAccess connectivity from the Internet and Homenet subnets.

In this test lab guide you will build a multisite Remote Access deployment by performing the following steps:

- [STEP 1: Complete the Base Configuration](step-1-complete-directaccess-configuration). Complete all the steps in the [Test Lab Guide: Demonstrate DirectAccess Single Server Setup with Mixed IPv4 and IPv6](https://go.microsoft.com/fwlink/p/?LinkId=237004).
- [STEP 2: Install and configure ROUTER1](step-2-install-and-configure-router1). ROUTER1 provides routing and forwarding functionality between the Corpnet and 2-Corpnet subnets.
- [STEP 3: Install and configure CLIENT2](step-3-install-and-configure-client2). CLIENT2 is a Windows 7 client computer that is used to demonstrate the backwards compatibility of a Windows Server 2016, Windows Server 2012 R2 or Windows Server 2012 Remote Access deployment.
- [STEP 4: Configure APP1](step-4-configure-app1). Configure APP1 with ROUTER1 as the default gateway and 2-DC1 as the alternate DNS server.
- [STEP 5: Configure DC1](step-5-configure-dc1). Configure DC1 with an additional Active Directory site and additional security groups for Windows 7 client computers.
- [STEP 6: Install and configure 2-DC1](step-6-install-and-configure-2-dc1). In a multisite deployment, you have two or more domains and sites. 2-DC1 provides domain controller and DNS services for the corp2.corp.contoso.com domain.
- [STEP 7: Install and configure 2-APP1](step-7-install-and-configure-2-app1). 2-APP1 is a web and file server in the 2-Corpnet network.
- [STEP 8: Configure INET1](step-8-configure-inet1). INET1 simulates the Internet in this test lab guide. You must configure a DNS entry that resolves to the public IP address of 2-EDGE1.
- [STEP 9: Configure EDGE1](step-9-configure-edge1). Configure the 2-Corpnet DNS server and routing on EDGE1.
- [STEP 10: Install and configure 2-EDGE1](step-10-install-and-configure-2-edge1). Two Remote Access servers are required in a multisite deployment. 2-EDGE1 provides Remote Access services for the second domain.
- [STEP 11: Configure multisite deployment](step-11-configure-the-multisite-deployment). After configuring both Remote Access servers, you can configure your multisite deployment.
- [STEP 12: Test DirectAccess connectivity](step-12-test-directaccess-connectivity). Test DirectAccess connectivity from both client computers from the Internet subnet through EDGE1 and 2-EDGE1.
- [STEP 13: Test DirectAccess connectivity from behind a NAT device](step-13-test-directaccess-connectivity-from-behind-a-nat-device). Test DirectAccess connectivity from behind a NAT device.
- [STEP 14: Snapshot the configuration](step-14-snapshot-the-configuration). After completing the test lab, take a snapshot of the working Remote Access multisite deployment so that you can return to it later to test additional scenarios.