---
layout: Conceptual
title: Create a Remote Desktop Services collection | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-desktop-services/rds-create-collection
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote-desktop-services
ms.update-cycle: 1095-days
description: Learn how to create a Remote Desktop Services session collection.
ms.author: roharwoo
ms.date: 2024-07-03T00:00:00.0000000Z
ms.topic: how-to
author: robinharwood
locale: en-us
document_id: 9753443d-2cf9-238f-7259-d9b12861e8a4
document_version_independent_id: 25afd194-f7d4-b3ce-c249-62ad6c3f537f
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-desktop-services/rds-create-collection.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-desktop-services/rds-create-collection
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-desktop-services/rds-create-collection.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ddab3cd8-636f-4a91-896e-1c23f399a6bd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f409bb5d-e203-40c5-9d95-0ee717231beb
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: baef2a97-ba30-f01a-7ca2-f19081d6e050
---

# Create a Remote Desktop Services collection | Microsoft Learn

Use the following steps to create a Remote Desktop Services session collection. A session collection holds the apps and desktops you want to make available to users. After you create the collection, publish it so users can access it.

Before you create a collection, you need to decide what kind of collection you need: pooled desktop sessions or personal desktop sessions.

- **Use pooled desktop sessions for session-based virtualization**: Leverage the compute power of Windows Server to provide a cost-effective multi-session environment to drive your users' everyday workloads
- **Use personal desktop sessions for to create a virtual desktop infrastructure (VDI)**: Leverage Windows client to provide the high performance, app compatibility, and familiarity that your users have come to expect of their Windows desktop experience.

With a pooled session, multiple users access a shared pool of resources, while with a personal desktop session, users are assigned their own desktop from within the pool. The pooled session provides lower overall cost, while personal sessions enable users to customize their desktop experience.

If you need to share graphics-intensive hosted applications, you can combine personal session desktops with the new Discrete Device Assignment (DDA) capability to also provide support for hosted applications that require accelerated graphics. Check out [Which graphics virtualization technology is right for you](rds-graphics-virtualization) for more information.

Regardless of the type of collection you choose, you'll populate those collections with RemoteApps - programs and resources that users can access from any supported device and work with as though the program was running locally.

## Create a pooled desktop session collection

1. In Server Manager, click **Remote Desktop Services &gt; Collections &gt; Tasks &gt; Create Session Collections**.
2. Enter a name for the collection, for example **ContosoAps**.
3. Select the RD Session Host server you created (for example, Contoso-Shr1).
4. Accept the default **User Groups**.
5. Enter the location of the file share you created for the user profile disks for this collection (for example, **\Contoso-Cb1\UserDisksr**).
6. Click **Create**. When the collection is created, click **Close**.

## Create a personal desktop session collection

Use the New-RDSessionCollection cmdlet to create a personal session desktop collection. The following three parameters provide the configuration information required for personal session desktops:

- **-PersonalUnmanaged** - Specifies the type of session collection that lets you assign users to a personal session host server. If you don't specify this parameter, then the collection is created as a traditional RD Session Host collection, where users are assigned to the next available session host when they sign in.
- **-GrantAdministrativePrivilege** - If you use **-PersonalUnmanaged**, specifies that the user assigned to the session host be given administrative privileges. If you don't use this parameter, users are granted only standard user privileges.
- **-AutoAssignUser** - If you use **-PersonalUnmanaged**, specifies that new users connecting through the RD Connection Broker are automatically assigned to an unassigned session host. If there are no unassigned session hosts in the collection, the user will see an error message. If you don't use this parameter, you have to [manually assign users to a session host](rds-manage-personal-collection#manually-assign-a-user-to-a-personal-session-host) before they sign in.

You can use PowerShell cmdlets to manage your personal desktop session collections. See [Manage your personal desktop session collections](rds-manage-personal-collection) for more information.

## Publish RemoteApp programs

Use the following steps to publish the apps and resources in your collection:

1. In Server Manager, select the new collection (**ContosoApps**).
2. Under RemoteApp Programs, click **Publish RemoteApp programs**.
3. Select the programs you want to publish, and then click **Publish**.