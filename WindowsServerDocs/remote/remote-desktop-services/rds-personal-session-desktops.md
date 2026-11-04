---
layout: Conceptual
title: Use personal session desktops with Remote Desktop Services | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-desktop-services/rds-personal-session-desktops
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote-desktop-services
ms.update-cycle: 1095-days
description: Learn how to share personalized, assigned desktops through RDS.
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
ms.date: 2024-07-03T00:00:00.0000000Z
locale: en-us
document_id: 6500ee1a-f33d-1ab5-141c-3cee25b3cc0c
document_version_independent_id: 0654a3b0-0fef-a23b-9bf7-39fe28735045
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-desktop-services/rds-personal-session-desktops.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-desktop-services/rds-personal-session-desktops
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-desktop-services/rds-personal-session-desktops.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ddab3cd8-636f-4a91-896e-1c23f399a6bd
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f409bb5d-e203-40c5-9d95-0ee717231beb
platformId: c26d9c50-8c38-3ec6-c86a-f0080f059b5c
---

# Use personal session desktops with Remote Desktop Services | Microsoft Learn

You can deploy server-based personal desktops in a cloud-computing environment by using personal session desktops. (A cloud-computing environment has a separation between the fabric Hyper-V servers and the guest virtual machines, such as Microsoft Azure Cloud or the Microsoft Cloud Platform.) The personal session desktop capability extends the session-based desktop deployment scenario in Remote Desktop Services to create a new type of session collection where each user is assigned to their own personal session host with administrative rights.

Use the following information to create and manage a personal session desktop collection.

## Create a personal session desktop collection

Use the New-RDSessionCollection cmdlet to create a personal session desktop collection. The following three parameters provide the configuration information required for personal session desktops:

- **-PersonalUnmanaged** - Specifies the type of session collection that lets you assign users to a personal session host server. If you don't specify this parameter, then the collection is created as a traditional RD Session Host collection, where users are assigned to the next available session host when they sign in.
- **-GrantAdministrativePrivilege** - If you use **-PersonalUnmanaged**, specifies that the user assigned to the session host be given administrative privileges. If you don't use this parameter, users are granted only standard user privileges.
- **-AutoAssignUser** - If you use **-PersonalUnmanaged**, specifies that new users connecting through the RD Connection Broker are automatically assigned to an unassigned session host. If there are no unassigned session hosts in the collection, the user will see an error message. If you don't use this parameter, you have to manually assign users to a session host before they sign in.

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