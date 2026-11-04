---
layout: Conceptual
title: Add a Claim Description | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/operations/add-a-claim-description
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Add a Claim Description'
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: how-to
ms.custom: sfi-image-nochange
locale: en-us
document_id: 4f576ee6-1b6c-ef9b-b2f8-7efe8cb7246f
document_version_independent_id: eacc95bc-cb0f-5f21-18a9-41f1f228a42d
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/operations/Add-a-Claim-Description.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/operations/add-a-claim-description
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/operations/Add-a-Claim-Description.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: 6c548421-0497-34cd-a026-92cf03721d81
---

# Add a Claim Description | Microsoft Learn

In an account partner organization, administrators create claims to represent a user's membership in a group or role or to represent some data about a user, for example, a user's employee identification number.

In a resource partner organization, administrators create corresponding claims to represent groups and users that can be recognized as resource users. Because outgoing claims in the account partner organization map to incoming claims in the resource partner organization, the resource partner is able to accept the credentials that the account partner provides.

You can use the following procedure to add a claim.

Membership in **Administrators**, or equivalent, on the local computer is the minimum required to complete this procedure. Review details about using the appropriate accounts and group memberships at [Local and Domain Default Groups](/en-us/previous-versions/orphan-topics/ws.10/dd728026%28v=ws.10%29).

## To add a claim description

1. In Server Manager, click **Tools**, and then select **AD FS Management**.
2. Expand **Service** and on the right click **Add Claim Description**. ![Screenshot that highlights Add Claim Description.](media/add-a-claim-description/claimdesc1.png)
3. On the Add a Claim Description dialog box, in **Display name**, type a unique name that identifies the group or role for this claim.
4. Add a **Short Name**.
5. In **Claim identifier**, type a URI that is associated with the group or role of the claim that you will be using.
6. Under **Description**, type text that best describes the purpose of this claim.
7. Depending on the needs of your organization, select either of the following check boxes, as appropriate, to publish this claim into federation metadata:

```
- To publish this claim to make partners aware that this server can accept this claim, click **Publish this claim in federation metadata as a claim type that this Federation Service can accept**.
- To publish this claim to make partners aware that this server can issue this claim, click **Publish this claim in federation metadata as a claim type that this Federation Service can send**.
```

1. Click **OK**.

![add claim description](media/add-a-claim-description/claimdesc2.png)