---
layout: Conceptual
title: Steps for Configuring the Test Lab with OTP Authentication and RSA SecurID | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-access/directaccess/tlg-otp-securid/steps-for-configuring-the-test-lab-2
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote
ms.update-cycle: 1095-days
description: Learn about configuring the Remote Access infrastructure, configure the Remote Access server and client, and test DirectAccess connectivity from the Homenet and Internet subnets.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: f2aea13c-e1cc-4914-b4f7-61c31e4e9cb5
document_version_independent_id: f740fcad-8af4-8b1a-eab1-d21ea101d67b
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-access/directaccess/tlg-otp-securid/Steps-for-Configuring-the-Test-Lab-2.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-access/directaccess/tlg-otp-securid/steps-for-configuring-the-test-lab-2
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-access/directaccess/tlg-otp-securid/Steps-for-Configuring-the-Test-Lab-2.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: d19cb772-8601-816b-589b-7b0f173eec11
---

# Steps for Configuring the Test Lab with OTP Authentication and RSA SecurID | Microsoft Learn

The following steps describe how to configure the Remote Access infrastructure, configure the Remote Access server and client, and test DirectAccess connectivity from the Homenet and Internet subnets.

In this test lab guide you will build a Remote Access with OTP environment by performing the following steps:

- [STEP 1: Complete the DirectAccess Configuration](assetId:///4dbf877f-02fb-439b-907a-f5b3f1d8afa6). Complete all the steps in the [Test Lab Guide: Demonstrate DirectAccess Single Server Setup with Mixed IPv4 and IPv6](https://go.microsoft.com/fwlink/p/?LinkId=237004).
- [STEP 2: Configure APP1](assetId:///c1bb590f-91d4-4ed5-bceb-b0e36eabd4ff). Configure APP1 with OTP certificate templates for use by EDGE1.
- [STEP 3: Configure DC1](assetId:///904a6edc-a771-45ed-9630-a34a680bb522). Verify User Principal Name defined on DC1.
- [STEP 7: Install and configure RSA](assetId:///baa4c28c-add7-42e2-8afd-ccc7a559406a). Install and Configure RSA, a RADIUS and OTP server, and configure EDGE1 for OTP.
- [STEP 11: Verify OTP Health on EDGE1](assetId:///3b397a4a-8478-47f2-a932-9e8e048c14ba). Make sure that the status of OTP is healthy on the Remote Access server.
- [STEP 8: Test DirectAccess connectivity from the Homenet subnet](assetId:///ba1652a6-0692-4add-91ca-34a84956ba14). Test DirectAccess OTP functionality from behind a NAT device.
- [STEP 10: Test DirectAccess connectivity from the Internet](assetId:///321149eb-5f23-4a0b-b8fb-1244540126e9). Test DirectAccess client connectivity from the Internet.
- [STEP 12: Snapshot the configuration](assetId:///8a51ed3c-9c32-402f-85d1-617ce46845b4). After completing the test lab, take a snapshot of the working DirectAccess with OTP configuration so that you can return to it later to test additional scenarios.