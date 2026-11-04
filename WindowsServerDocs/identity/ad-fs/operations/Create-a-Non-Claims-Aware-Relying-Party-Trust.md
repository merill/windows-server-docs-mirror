---
layout: Conceptual
title: Create a Non-Claims Aware Relying Party Trust | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/operations/create-a-non-claims-aware-relying-party-trust
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Create a Non-Claims-Aware Relying Party Trust'
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 99d03d12-4cb7-ab85-9087-27973f9f6b3c
document_version_independent_id: 5beb953d-1791-d556-487e-9c4727d8d11f
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/operations/Create-a-Non-Claims-Aware-Relying-Party-Trust.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/operations/create-a-non-claims-aware-relying-party-trust
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/operations/Create-a-Non-Claims-Aware-Relying-Party-Trust.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: c2f32f25-e428-ba32-d677-e157f92bfae5
---

# Create a Non-Claims Aware Relying Party Trust | Microsoft Learn

In the AD FS Management snap-in, non-claims-aware relying party trusts are objects that are created to represent the trust between the federation service and a single web-based application that is not claims-aware and that is accessed through the Web Application Proxy.

A non-claims-aware relying party trust is a relying party trust which consists of identifiers, names, and rules for authentication and authorization when the relying party trust is accessed through the Web Application Proxy. These web-based applications that do not rely on claims, in other words, these Integrated Windows Authentication-based applications, can have authorization rules that enforce access that is based on claims when the access is external to the corporate network through the Web Application Proxy.

To add a new non-claims-aware relying party trust, by using the AD FS Management snap-in, perform the following procedure.

Membership in **Administrators**, or equivalent, on the local computer is the minimum required to complete this procedure. Review details about using the appropriate accounts and group memberships at [Local and Domain Default Groups](/en-us/previous-versions/orphan-topics/ws.10/dd728026%28v=ws.10%29).

## To create a non-claims aware Relying Party Trust manually

1. In Server Manager, click **Tools**, and then select **AD FS Management**.
2. Under **Actions**, click **Add Relying Party Trust**. ![Screenshot that highlights the Add Relying Party Trust action.](media/create-a-relying-party-trust/addtrust1.png)
3. On the **Welcome** page, choose **Non claims aware** and click **Start**. ![Screenshot that highlights the Non claims aware option.](media/create-a-non-claims-aware-relying-party-trust/addnon1.png)
4. On the **Specify Display Name** page, type a name in **Display name**, under **Notes** type a description for this relying party trust, and then click **Next**. ![Screenshot that shows where to specify the name for the relying party trust.](media/create-a-non-claims-aware-relying-party-trust/addnon2.png)
5. On the **Configure Identifiers** page, specify one or more identifiers for this relying party, click **Add** to add them to the list, and then click **Next**. ![Screenshot that shows where to specify one or more identifiers for the relying party trust.](media/create-a-non-claims-aware-relying-party-trust/addnon3.png)
6. On the **Choose Access Control Policy** select a policy and click **Next**. For more information about Access Control Policies, see [Access Control Policies in AD FS](access-control-policies-in-ad-fs). ![Screenshot that shows where to select an Access Control Policy for the relying party trust.](media/create-a-non-claims-aware-relying-party-trust/addnon4.png)
7. On the **Ready to Add Trust** page, review the settings, and then click **Next** to save your relying party trust information. ![Screenshot that shows how to save your relying party trust information.](media/create-a-non-claims-aware-relying-party-trust/addnon5.png)
8. On the **Finish** page, click **Close**. This action automatically displays the **Edit Claim Rules** dialog box. ![relying party](media/create-a-non-claims-aware-relying-party-trust/addnon6.png)