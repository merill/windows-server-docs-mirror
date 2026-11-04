---
layout: Conceptual
title: Add an Attribute Store | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/operations/add-an-attribute-store
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Add an Attribute Store'
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: how-to
ms.custom: sfi-image-nochange
locale: en-us
document_id: e7d24ae0-a2bf-8db0-7076-41ce5c629785
document_version_independent_id: 8ad36418-59b2-3cc1-d468-b1b766cb464c
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/operations/Add-an-Attribute-Store.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/operations/add-an-attribute-store
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/operations/Add-an-Attribute-Store.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: ac62a37d-ce2a-830e-51aa-4f9d6e618c8e
---

# Add an Attribute Store | Microsoft Learn

User accounts and computer accounts that require access to a resource that is protected by Active Directory Federation Services (AD FS) are stored in an attribute store, such as Active Directory Domain Services (AD DS). The claims issuance engine uses attribute stores to gather data that is necessary to issue claims. Data from the attribute stores is then projected as claims.

You can use the following procedure to add an attribute store to the Federation Service.

Membership in **Administrators**, or equivalent, on the local computer is the minimum required to complete this procedure. Review details about using the appropriate accounts and group memberships at [Local and Domain Default Groups](/en-us/previous-versions/orphan-topics/ws.10/dd728026%28v=ws.10%29).

#### To add an attribute store

1. Open **AD FS Management**.
2. Under **Actions** click **Add an attribute store**.

![Screenshot that highlights the Add Attribute Store action.](media/add-an-attribute-store/addstore1.png)

1. In the **Add an attribute store** dialog box, configure the following properties for the attribute store that you want to add:

    - In **Display name**, type the name that you want to use to identify the attribute store.
    - In **Attribute store type**, select a supported attribute store type, either **Active Directory**, **LDAP**, or **SQL**.
    - In **Connection string**, if you have selected either a Lightweight Directory Access Protocol (LDAP) store or a Structured Query Language (SQL) store, enter the string that you used to establish a connection to the attribute store. For Active Directory attribute stores, no connection string is necessary; therefore, this field is disabled.

        Note

        AD FS automatically creates an Active Directory attribute store, by default.

![add attribute store](media/add-an-attribute-store/addstore2.png)

1. Click **OK**.

## Additional references

[AD FS Operations](../ad-fs-operations)

[The Role of Attribute Stores](../technical-reference/the-role-of-attribute-stores)