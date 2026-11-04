---
layout: Conceptual
title: Set up email discovery to subscribe to your RDS feed | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-desktop-services/rds-email-discovery
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote-desktop-services
ms.update-cycle: 1095-days
description: Learn how to set up email discovery in your RDS deployment.
ms.author: roharwoo
ms.date: 2024-07-03T00:00:00.0000000Z
ms.topic: how-to
author: robinharwood
locale: en-us
document_id: ca8081a3-ec92-8aa5-2a51-1c10a298fdd1
document_version_independent_id: 6c33184e-2ef8-0b7c-8666-50d4c4b16c7e
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-desktop-services/rds-email-discovery.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-desktop-services/rds-email-discovery
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-desktop-services/rds-email-discovery.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ddab3cd8-636f-4a91-896e-1c23f399a6bd
- https://authoring-docs-microsoft.poolparty.biz/devrel/7814ca69-56be-4667-8a46-86327796c328
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f409bb5d-e203-40c5-9d95-0ee717231beb
- https://authoring-docs-microsoft.poolparty.biz/devrel/f15dfcd0-2664-48ba-bb88-f1f86eadbfd1
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 25745cc5-7cc5-7015-a5e5-cbde9c775c9c
---

# Set up email discovery to subscribe to your RDS feed | Microsoft Learn

Have you ever had trouble getting your end users connected to their published RDS feed, either because of a single missing character in the feed URL or because they lost the email with the URL? Nearly all Remote Desktop client applications support finding your subscription by entering your email address, making it easier than ever to get your users connected to their RemoteApps and desktops.

Before you set up email discovery, do the following:

- Make sure you have permission to add a TXT record to the domain associated with your email (for example, if your users have @contoso.com email addresses, you would need permissions for the contoso.com domain).
- Create an RD Web feed URL (`https://<rdweb-dns-name>.<domain>/RDWeb/Feed/webfeed.aspx`), such as `https://rdweb.contoso.com/RDWeb/Feed/webfeed.aspx`.

Note

If you're using Azure Virtual Desktop instead of Remote Desktop, you'll want to use these URLs instead:

- If you're using Azure Virtual Desktop (classic): `https://rdweb.wvd.microsoft.com/api/feeddiscovery/webfeeddiscovery.aspx`
- If you're using Azure Virtual Desktop: `https://rdweb.wvd.microsoft.com/api/arm/feeddiscovery`

Now, follow these steps to set up email discovery:

1. In your browser, connect to the website of the domain name registrar where your domain is registered.
2. Navigate to the appropriate page for your registered domain where you can view, add, and edit DNS records.
3. Enter a new DNS record with the following properties:

    - **Host:** \_msradc
    - **Text:** &lt;RD Web Feed URL&gt;
    - **TTL:** 300 seconds

    The names of the DNS records fields vary by domain name registrar, but this process will result in a TXT record named \_msradc.&lt;domain\_name&gt; (such as \_msradc.contoso.com) that has a value of the full RD Web feed.

That's it! Now, launch the Remote Desktop application on your device and subscribe yourself!