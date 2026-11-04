---
layout: Conceptual
title: Distribute Certificates to Client Computers by Using Group Policy | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/deployment/distribute-certificates-to-client-computers-by-using-group-policy
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Distribute Certificates to Client Computers by Using Group Policy'
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: f13fd851-31ac-05a2-f1f1-642f5d59fcd7
document_version_independent_id: 35f0e42d-a950-ce93-0f7c-11784a6623fd
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/deployment/Distribute-Certificates-to-Client-Computers-by-Using-Group-Policy.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/deployment/distribute-certificates-to-client-computers-by-using-group-policy
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/deployment/Distribute-Certificates-to-Client-Computers-by-Using-Group-Policy.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 93351979-9531-55dc-56b7-23b71ceecb7c
---

# Distribute Certificates to Client Computers by Using Group Policy | Microsoft Learn

You can use the following procedure to push down the appropriate Secure Sockets Layer (SSL) certificates (or equivalent certificates that chain to a trusted root) for account federation servers, resource federation servers, and Web servers to each client computer in the account partner forest by using Group Policy.

Membership in **Domain Admins** or **Enterprise Admins**, or equivalent, in Active Directory Domain Services (AD DS) is the minimum required to complete this procedure. Review details about using the appropriate accounts and group memberships at [Local and Domain Default Groups](/en-us/previous-versions/orphan-topics/ws.10/dd728026%28v=ws.10%29) (http://go.microsoft.com/fwlink/?LinkId=83477).

### To distribute certificates to client computers by using Group Policy

1. On a domain controller in the forest of the account partner organization, start the **Group Policy Management** snap-in.
2. Find an existing Group Policy Object (GPO) or create a new GPO to contain the certificate settings. Ensure that the GPO is associated with the domain, site, or organizational unit (OU) where the appropriate user and computer accounts reside.
3. Right-click the GPO, and then click **Edit**.
4. In the console tree, open **Computer Configuration\Policies\Windows Settings\Security Settings\Public Key Policies**, right-click **Trusted Root Certification Authorities**, and then click **Import**.
5. On the **Welcome to the Certificate Import Wizard** page, click **Next**.
6. On the **File to Import** page, type the path to the appropriate certificate files (for example, \\fs1\c$\fs1.cer), and then click **Next**.
7. On the **Certificate Store** page, click **Place all certificates in the following store**, and then click **Next**.
8. On the **Completing the Certificate Import Wizard** page, verify that the information you provided is accurate, and then click **Finish**.
9. Repeat steps 2 through 6 to add additional certificates for each of the federation servers in the farm.