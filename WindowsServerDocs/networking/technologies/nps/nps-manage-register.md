---
layout: Conceptual
title: Register an NPS in an Active Directory Domain | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/technologies/nps/nps-manage-register
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Learn how to register a server running Network Policy Server in Windows Server 2016 in the NPS default domain or in another domain.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: d63d3244-4290-d5af-5f03-45549fbb45cf
document_version_independent_id: 52e55a0d-5c2c-8614-dde3-66360519da1b
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/technologies/nps/nps-manage-register.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/technologies/nps/nps-manage-register
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/technologies/nps/nps-manage-register.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: b380eefa-5120-8e15-e412-f415e1660c8c
---

# Register an NPS in an Active Directory Domain | Microsoft Learn

You can use this topic to register a server running Network Policy Server in Windows Server 2016 in the NPS default domain or in another domain.

## Register an NPS in its Default Domain

You can use this procedure to register an NPS in the domain where the server is a domain member.

NPSs must be registered in Active Directory so that they have permission to read the dial-in properties of user accounts during the authorization process. Registering an NPS adds the server to the **RAS and IAS Servers** group in Active Directory.

Membership in **Administrators**, or equivalent, is the minimum required to perform these procedures.

### To register an NPS in its default domain

1. On the NPS, in Server Manager, click **Tools**, and then click **Network Policy Server**. The Network Policy Server console opens.
2. Right-click **NPS (Local)**, and then click **Register Server in Active Directory**. The **Network Policy Server** dialog box opens.
3. In **Network Policy Server**, click **OK**, and then click **OK** again.

## Register an NPS in Another Domain

To provide an NPS with permission to read the dial-in properties of user accounts in Active Directory, the NPS must be registered in the domain where the accounts reside.

You can use this procedure to register an NPS in a domain where the NPS is not a domain member.

Membership in **Administrators**, or equivalent, is the minimum required to perform these procedures.

### To register an NPS in another domain

1. On the domain controller, in Server Manager, click **Tools**, and then click **Active Directory Users and Computers**. The Active Directory Users and Computers console opens.
2. In the console tree, navigate to the domain where you want the NPS to read user account information, and then click the **Users** folder.
3. In the details pane, right-click **RAS and IAS Servers**, and then click **Properties**. The **RAS and IAS Servers Properties** dialog box opens.
4. In the **RAS and IAS Servers Properties** dialog box, click the **Members** tab, add each of the NPSs that you want to register in the domain, and then click **OK**.

### To register an NPS in another domain by using Netsh commands for NPS

1. Open Command Prompt or windows PowerShell.
2. Type the following at the command prompt: **netsh nps add registeredserver***domain* *server*, and then press ENTER.

Note

In the preceding command, *domain* is the DNS domain name of the domain where you want to register the NPS, and *server* is the name of the NPS computer.