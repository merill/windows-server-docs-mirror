---
layout: Conceptual
title: Import a Server Authentication Certificate to the Default Web Site | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/deployment/import-a-server-authentication-certificate-to-the-default-web-site
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Import a Server Authentication Certificate to the Default Web Site'
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: c541a347-9ab6-27ae-a956-e115f576820a
document_version_independent_id: 9f271da1-4e69-1ef9-eb35-e9c044679e5b
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/deployment/Import-a-Server-Authentication-Certificate-to-the-Default-Web-Site.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/deployment/import-a-server-authentication-certificate-to-the-default-web-site
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/deployment/Import-a-Server-Authentication-Certificate-to-the-Default-Web-Site.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: 894ade5c-ca24-6fc9-9328-279447c058f2
---

# Import a Server Authentication Certificate to the Default Web Site | Microsoft Learn

After you obtain a server authentication certificate from a certification authority (CA), you must manually install that certificate on the Default Web Site for each federation server or federation server proxy in a server farm.

For Web servers, you must manually install the server authentication certificate on the appropriate Web site or virtual directory where your federated application resides.

If you are setting up a farm, be sure to perform this procedure identically—using the exact same settings—on each of the servers in your farm.

Note

The AD FS Management snap-in refers to server authentication certificates for federation servers as service communication certificates.

Membership in **Administrators**, or equivalent, on the local computer is the minimum required to complete this procedure. Review details about using the appropriate accounts and group memberships at [Local and Domain Default Groups](/en-us/previous-versions/orphan-topics/ws.10/dd728026%28v=ws.10%29).

### To import a server authentication certificate to the Default Web Site

1. On the **Start** screen, type**Internet Information Services (IIS) Manager**, and then press ENTER.
2. In the console tree, click **ComputerName**.
3. In the center pane, double-click **Server Certificates**.
4. In the **Actions** pane, click **Import**.
5. In the **Import Certificate** dialog box, click the **…** button.
6. Browse to the location of the pfx certificate file, highlight it, and then click **Open**.
7. Type a password for the certificate, and then click **OK**.

## Additional references

[Checklist: Setting Up a Federation Server](checklist--setting-up-a-federation-server)

[Checklist: Setting Up a Federation Server Proxy](checklist--setting-up-a-federation-server-proxy)

[Certificate Requirements for Federation Servers](../design/certificate-requirements-for-federation-servers)

[Certificate Requirements for Federation Server Proxies](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dd807054%28v=ws.11%29)