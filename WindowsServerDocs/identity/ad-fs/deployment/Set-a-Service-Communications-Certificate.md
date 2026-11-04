---
layout: Conceptual
title: Set a Service Communications Certificate | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/deployment/set-a-service-communications-certificate
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Set a Service Communications Certificate'
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 335ded4b-b969-8a44-ea7f-4bd55d25ab7c
document_version_independent_id: ce5d9bf6-e2de-c477-38ba-0843c675af98
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/deployment/Set-a-Service-Communications-Certificate.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/deployment/set-a-service-communications-certificate
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/deployment/Set-a-Service-Communications-Certificate.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 8b97deec-d2c3-b3a5-985c-256ac0693a4f
---

# Set a Service Communications Certificate | Microsoft Learn

Federation servers in Active Directory Federation Services (AD FS) use the service communications certificate to secure Web services traffic for Secure Sockets Layer (SSL) communication with Web clients or with federation server proxies.

Note

The Service Communications Certificate is not the same as an SSL Certificate. To change the AD FS SSL certificate, you will need to use Powershell. Follow the guidance in this [article](../operations/manage-ssl-certificates-ad-fs-wap).

You can use the following procedure to change the service communications certificate with the AD FS Management snap-in.

Note

The AD FS Management snap-in refers to server authentication certificates for federation servers as service communication certificates.

Membership in **Administrators**, or equivalent, on the local computer is the minimum required to complete this procedure. Review details about using the appropriate accounts and group memberships at [Local and Domain Default Groups](/en-us/previous-versions/orphan-topics/ws.10/dd728026%28v=ws.10%29) (http://go.microsoft.com/fwlink/?LinkId=83477).

### To set a service communications certificate

1. On the **Start** screen, type**AD FS Management**, and then press ENTER.
2. In the console tree, double-click **Service**, and then click **Certificates**.
3. In the **Actions** pane, click the **Set Service Communications Certificate** link.
4. In the **Select a service communications certificate** dialog box, navigate to the certificate file that you want to set as the service communications certificate, select the certificate file, and then click **Open**.

## Additional references

[Checklist: Setting Up a Federation Server](checklist--setting-up-a-federation-server)

[Certificate Requirements for Federation Servers](../design/certificate-requirements-for-federation-servers)