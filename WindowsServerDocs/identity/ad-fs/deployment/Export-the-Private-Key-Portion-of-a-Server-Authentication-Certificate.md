---
layout: Conceptual
title: Export the Private Key Portion of a Server Authentication Certificate | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/deployment/export-the-private-key-portion-of-a-server-authentication-certificate
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Export the Private Key Portion of a Server Authentication Certificate'
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 54c116b9-6c1a-67a4-b2f9-f289d1255147
document_version_independent_id: 9349bcb8-d5c3-263d-72e9-1c95548f74fa
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/deployment/Export-the-Private-Key-Portion-of-a-Server-Authentication-Certificate.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/deployment/export-the-private-key-portion-of-a-server-authentication-certificate
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/deployment/Export-the-Private-Key-Portion-of-a-Server-Authentication-Certificate.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: f0966d93-29f5-4495-acf7-b6713b0c2642
---

# Export the Private Key Portion of a Server Authentication Certificate | Microsoft Learn

Every federation server in an Active Directory Federation Services (AD FS) farm must have access to the private key of the server authentication certificate. If you are implementing a server farm of federation servers or Web servers, you must have a single authentication certificate. This certificate must be issued by an enterprise certification authority (CA), and it must have an exportable private key. The private key of the server authentication certificate must be exportable so that it can be made available to all the servers in the farm.

This same concept is true of federation server proxy farms in the sense that all federation server proxies in a farm must share the private key portion of the same server authentication certificate.

Note

The AD FS Management snap-in refers to server authentication certificates for federation servers as service communication certificates.

Depending on which role this computer will play, use this procedure on the federation server computer or federation server proxy computer where you installed the server authentication certificate with the private key. When you finish the procedure, you can then import this certificate on the Default Web Site of each server in the farm. For more information, see [Import a Server Authentication Certificate to the Default Web Site](import-a-server-authentication-certificate-to-the-default-web-site).

Membership in **Administrators**, or equivalent, on the local computer is the minimum required to complete this procedure. Review details about using the appropriate accounts and group memberships at [Local and Domain Default Groups](/en-us/previous-versions/orphan-topics/ws.10/dd728026%28v=ws.10%29).

### To export the private key portion of a server authentication certificate

1. On the **Start** screen, type**Internet Information Services (IIS) Manager**, and then press ENTER.
2. In the console tree, click **ComputerName**.
3. In the center pane, double-click **Server Certificates**.
4. In the center pane, right-click the certificate that you want to export, and then click **Export**.
5. In the **Export Certificate** dialog box, click the **…** button.
6. In **File name**, type **C:\***NameofCertificate*, and then click **Open**.
7. Type a password for the certificate, confirm it, and then click **OK**.
8. Validate the success of your export by confirming that the file you specified is created at the specified location.

    Important

    So that this certificate can be imported to the local certificate store on the new server, you must transfer the file to physical media and protect its security during transport to the new server. It is extremely important to guard the security of the private key. If this key is compromised, the security of your entire AD FS deployment (including resources within your organization and in resource partner organizations) is compromised.
9. Import the exported server authentication certificate into the certificate store on the new server before you install the Federation Service. For information about how to import the certificate, see Import a Server Certificate ([http://go.microsoft.com/fwlink/?LinkId=108283](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732785%28v=ws.10%29)).

## Additional references

[Checklist: Setting Up a Federation Server](checklist--setting-up-a-federation-server)

[Checklist: Setting Up a Federation Server Proxy](checklist--setting-up-a-federation-server-proxy)

[Certificate Requirements for Federation Servers](../design/certificate-requirements-for-federation-servers)

[Certificate Requirements for Federation Server Proxies](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dd807054%28v=ws.11%29)