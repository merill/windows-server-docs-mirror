---
layout: Conceptual
title: Configure Corporate DNS for the Federation Service and DRS | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/deployment/configure-corporate-dns-for-the-federation-service-and-drs
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Configure Corporate DNS for the Federation Service and DRS'
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: b8320628-e0a5-d684-395f-d254a04b473b
document_version_independent_id: 021ec8f3-93dc-11c3-2dd5-bd01cea3ef2f
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/deployment/Configure-Corporate-DNS-for-the-Federation-Service-and-DRS.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/deployment/configure-corporate-dns-for-the-federation-service-and-drs
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/deployment/Configure-Corporate-DNS-for-the-Federation-Service-and-DRS.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/f98c9a19-e481-4f15-8047-76b641e6ed57
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/f5685781-a4fd-40f1-8126-59abde4643bf
platformId: 8a74baf3-5cbd-5e1a-a881-ccc648bb0efd
---

# Configure Corporate DNS for the Federation Service and DRS | Microsoft Learn

## Step 6: Add a Host (A) and Alias (CNAME) Resource Record to Corporate DNS for the Federation Service and DRS

You must add the following resource records to corporate Domain Name System (DNS) for your federation service and Device Registration Service that you configured in previous steps.

| Entry | Type | Address |
| --- | --- | --- |
| federation\_service\_name | Host (A) | IP address of the AD FS server or the IP address of the load balancer that is configured in front of your AD FS server farm |
| enterpriseregistration | Alias (CNAME) | federation\_server\_name.contoso.com |

You can use the following procedure to add a host (A) and alias (CNAME) resource records to corporate DNS for the federation server and the Device Registration Service.

Membership in **Administrators**, or equivalent, is the minimum requirement to complete this procedure. Review details about using the appropriate accounts and group memberships at [Local and Domain Default Groups](/en-us/previous-versions/orphan-topics/ws.10/dd728026%28v=ws.10%29).

#### To add a host (A) and alias (CNAME) resource records to DNS for your federation server

1. On you domain controller, in Server Manager, on the **Tools** menu, click **DNS** to open the DNS snap-in.
2. In the console tree, expand the **domain\_controller\_name** node, expand **Forward Lookup Zones**, right-click **domain\_name**, and then click **New Host (A or AAAA)**.
3. In the **Name** box, type the name to use for your AD FS farm.
4. In the **IP address** box, type the IP address of your federation server. Click **Add Host**.
5. Right-click the **domain\_name** node, and then click **New Alias (CNAME)**.
6. In the **New Resource Record** dialog box, type **enterpriseregistration** in the **Alias name** box.
7. In the fully qualified domain name (FQDN) of the target host box, type **federation\_service\_farm\_name.domain\_name.com**, and then click **OK**.

    Important

    In a real world deployment, if your company has multiple User Principal Name (UPN) suffixes, you must create multiple CNAME records for each of those UPN suffixes in DNS.