---
layout: Conceptual
title: Create an Alias (CNAME) Record in DNS for WEB1 | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/core-network-guide/cncg/server-certs/create-an-alias-cname-record-in-dns-for-web1
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Learn how to add an Alias canonical name (CNAME) resource record for your Web server to a zone in DNS on your domain controller.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: 26b34a39-9089-b61b-41fa-6ff00e5dc964
document_version_independent_id: 94593fa0-9161-a52a-347e-62e6e7c940ae
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/core-network-guide/cncg/server-certs/Create-an-Alias-CNAME-Record-in-DNS-for-WEB1.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/core-network-guide/cncg/server-certs/create-an-alias-cname-record-in-dns-for-web1
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/core-network-guide/cncg/server-certs/Create-an-Alias-CNAME-Record-in-DNS-for-WEB1.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: ceb7b2bb-8e93-1d02-5885-0ed0492f4b13
---

# Create an Alias (CNAME) Record in DNS for WEB1 | Microsoft Learn

You can use this procedure to add an Alias canonical name (CNAME) resource record for your Web server to a zone in DNS on your domain controller. With CNAME records, you can use more than one name to point to a single host, making it easy to do such things as host both a File Transfer Protocol (FTP) server and a Web server on the same computer.

Because of this, you are free to use your Web server to host the certificate revocation list (CRL) for your certification authority (CA) as well as to perform additional services, such as FTP or Web server.

When you perform this procedure, replace **Alias name** and other variables with values that are appropriate for your deployment.

To perform this procedure, you must be a member of **Domain Admins**.

## To add an alias (CNAME) resource record to a zone

Note

To perform this procedure by using Windows PowerShell, see [Add-DnsServerResourceRecordCName](/en-us/powershell/module/dnsserver/add-dnsserverresourcerecordcname?view=winserver2012r2-ps&amp;preserve-view=true).

1. On DC1, in Server Manager, click **Tools** and then click **DNS**. The DNS Manager Microsoft Management Console (MMC) opens.
2. In the console tree, double-click **Forward Lookup Zones**, right-click the forward lookup zone where you want to add the Alias resource record, and then click **New Alias (CNAME)**. The **New Resource Record** dialog box opens.
3. In **Alias name**, type the alias name **pki**.
4. When you type a value for **Alias name**, the **Fully qualified domain name (FQDN)** auto-fills in the dialog box. For example, if your alias name is "pki" and your domain is corp.contoso.com, the value **pki.corp.contoso.com** is auto-filled for you.
5. In **Fully qualified domain name (FQDN) for target host**, type the FQDN of your Web server. For example, if your Web server is named WEB1 and your domain is corp.contoso.com, type **WEB1.corp.contoso.com**.
6. Click **OK** to add the new record to the zone.