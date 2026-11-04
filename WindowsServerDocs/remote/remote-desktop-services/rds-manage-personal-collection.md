---
layout: Conceptual
title: Manage a personal desktop session collection in RDS | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-desktop-services/rds-manage-personal-collection
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote-desktop-services
ms.update-cycle: 1095-days
description: Learn how to manage a personal desktop session collection in Remote Desktop Services.
ms.author: roharwoo
ms.date: 2024-07-03T00:00:00.0000000Z
ms.topic: how-to
author: robinharwood
locale: en-us
document_id: e337a730-16ce-f801-423c-bcf1b6812032
document_version_independent_id: 91ca0f1d-00ad-188a-b76a-ad69f4211d41
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-desktop-services/rds-manage-personal-collection.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-desktop-services/rds-manage-personal-collection
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-desktop-services/rds-manage-personal-collection.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ddab3cd8-636f-4a91-896e-1c23f399a6bd
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f409bb5d-e203-40c5-9d95-0ee717231beb
platformId: d6943462-7c11-44db-d796-0bf3bb6307da
---

# Manage a personal desktop session collection in RDS | Microsoft Learn

Use the following information to manage a personal desktop session collection in Remote Desktop Services.

## Manually assign a user to a personal session host

Use the **Set-RDPersonalSessionDesktopAssignment** cmdlet to manually assign a user to a personal session host server in the collection. The cmdlet supports the following parameters:

-CollectionName &lt;string&gt;

-ConnectionBroker &lt;string&gt;

-User &lt;string&gt;

-Name &lt;string&gt;

- **–CollectionName** - specifies the name of the personal session desktop collection. This parameter is required.
- **–ConnectionBroker** - specifies the Remote Desktop Connection Broker (RD Connection Broker) server for your Remote Desktop deployment. If you don't supply a value, the cmdlet uses the fully qualified domain name (FQDN) of the local computer.
- **–User** - specifies the user account to associate with the personal session desktop, in DOMAIN\User format. This parameter is required.
- **–Name** - specifies the name of the session host server. This parameter is required. The session host identified here must be a member of the collection that the **-CollectionName** parameter specifies.

The **Import-RDPersonalSessionDesktopAssignment** cmdlet imports associations between user accounts and personal session desktops from a text file. The cmdlet supports the following parameters:

-CollectionName &lt;string&gt;

-ConnectionBroker &lt;string&gt;

-Path &lt;string&gt;

**–Path** specifies the path and file name of a file to import.

## Removing a User Assignment from a Personal Session Host

Use the **Remove-RDPersonalSessionDesktopAssignment** cmdlet to remove the association between a personal session desktop and a user. The cmdlet supports the following parameters:

-CollectionName &lt;string&gt;

-ConnectionBroker &lt;string&gt;

-Force

-Name &lt;string&gt;

-User &lt;string&gt;

**–Force** forces the command to run without asking for user confirmation.

## Query user assignments

Use the **Get-RDPersonalSessionDesktopAssignment** cmdlet to get a list of personal session desktops and associated user accounts. The cmdlet supports the following parameters:

-CollectionName &lt;string&gt;

-ConnectionBroker &lt;string&gt;

-User &lt;string&gt;

-Name &lt;string&gt;

You can run the cmdlet to query by collection name, user name, or by session desktop name. If you specify only the **–CollectionName** parameter, the cmdlet returns a list of session hosts and associated users. If you also specify the **–User** parameter, the session host associated with that user is returned. If you provide the **–Name** parameter, the user associated with that session host is returned.

The **Export-RDPersonalPersonalDesktopAssignment** cmdlet exports the current associations between users and personal virtual desktops to a text file. The cmdlet supports the following parameters:

-CollectionName &lt;string&gt;

-ConnectionBroker &lt;string&gt;

-Path &lt;string&gt;

All new cmdlets support the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable. For more information, see [about_CommonParameters](/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters).