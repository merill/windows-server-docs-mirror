---
layout: Conceptual
title: Configure the Server Certificate Template for Network Remote Access | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/core-network-guide/cncg/server-certs/configure-server-certificate-template-remote-access-network-policy-server
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Learn how to configure the server certificate template in Active Directory Certificate Services for Remote Access and Network Policy Server.
ms.topic: how-to
ai-usage: ai-assisted
ms.author: roharwoo
author: robinharwood
ms.date: 2025-06-17T00:00:00.0000000Z
locale: en-us
document_id: 9594eb59-ea60-45c0-12d0-f34065fd7e11
document_version_independent_id: 3115c60a-aa2c-5253-2851-8ad3ab9db14e
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/core-network-guide/cncg/server-certs/configure-server-certificate-template-remote-access-network-policy-server.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/core-network-guide/cncg/server-certs/configure-server-certificate-template-remote-access-network-policy-server
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/core-network-guide/cncg/server-certs/configure-server-certificate-template-remote-access-network-policy-server.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
platformId: be8a4e54-0418-0a2d-9dcf-fc7bce84ede2
---

# Configure the Server Certificate Template for Network Remote Access | Microsoft Learn

This article describes how to configure a server certificate template in Active Directory Certificate Services (AD CS) for use with Remote Access, including RAS Gateway servers, and Network Policy Server (NPS). By following these steps, you can set up automatic certificate enrollment for servers running Remote Access or NPS services, simplifying certificate management and enhancing network security.

When you configure this template, you can specify the servers by Active Directory security group that should automatically receive a server certificate from AD CS.

## Prerequisites

Before you begin, ensure the following prerequisites are met:

- Active Directory Certificate Services (AD CS) is installed and configured with at least one Enterprise Certification Authority (CA).
- A user account that is a member of both the **Enterprise Admins** and the root domain's **Domain Admins** group.
- Servers running the Remote Access service or NPS that are members of the **RAS and IAS Servers** security group in Active Directory.

## Configure the server certificate template

To configure the server certificate template for Remote Access and NPS, follow these steps:

1. On your AD CS server, in Server Manager, select **Tools**, then select **Certification Authority**. The Certification Authority Microsoft Management Console (MMC) opens.
2. In the MMC, double-click the CA name, right-click **Certificate Templates**, then select **Manage**.
3. The Certificate Templates console opens. All of the certificate templates are displayed in the details pane.
4. In the details pane, select the template **RAS and IAS Server**.
5. Select the **Action** menu, then select **Duplicate Template**. The template **Properties** dialog box opens.
6. Select the **Security** tab.
7. On the **Security** tab, for **Group or user names**, select **RAS and IAS servers**.
8. In **Permissions for RAS and IAS servers**, for **Allow**, ensure that **Enroll** is selected, then select the check box for **Autoenroll**. Select **OK**, and close the Certificate Templates MMC.
9. In the Certification Authority MMC, select **Certificate Templates**. On the **Action** menu, select **New**, then select **Certificate Template to Issue**. The **Enable Certificate Templates** dialog box opens.
10. In **Enable Certificate Templates**, select the name of the certificate template that you configured, then select **OK**. For example, if you didn't change the default certificate template name, select **Copy of RAS and IAS Server**, then select **OK**.
11. Close the Certification Authority MMC.

You configured the server certificate template for Remote Access and NPS. This template allows servers in the **RAS and IAS Servers** security group to automatically enroll for a server certificate from the AD CS.