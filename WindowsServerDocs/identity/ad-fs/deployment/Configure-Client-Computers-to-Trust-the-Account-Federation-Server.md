---
layout: Conceptual
title: Configure Client Computers to Trust the Account Federation Server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/deployment/configure-client-computers-to-trust-the-account-federation-server
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Configure Client Computers to Trust the Account Federation Server'
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 067da884-10d8-b49a-c912-74705e9aecc9
document_version_independent_id: 17e24561-44a4-0d7a-297d-b84a9ae88217
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/deployment/Configure-Client-Computers-to-Trust-the-Account-Federation-Server.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/deployment/configure-client-computers-to-trust-the-account-federation-server
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/deployment/Configure-Client-Computers-to-Trust-the-Account-Federation-Server.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 839cf887-7d1f-20d6-ce57-2c69e2a92892
---

# Configure Client Computers to Trust the Account Federation Server | Microsoft Learn

So that client computers can successfully access federated applications using Active Directory Federation Services (AD FS), you must first configure the Internet Explorer settings on each client computer so that the browser trusts the account federation server. You can do this manually or through Group Policy, depending on your administrative preference, by completing one of the following procedures.

## Configuring Internet Explorer settings manually

You can use the following procedure to manually configure each user's Internet Explorer settings to support federation through AD FS. If multiple users use a single computer, complete this procedure multiple times—once for each user profile.

To perform this procedure, log on as the user who will be accessing federated applications. This is a profile-specific setting. Therefore, it requires that you manually add this setting for each profile that exists on a specific computer.

#### To manually configure client computers to trust the account federation server

1. On the client computer, start Internet Explorer.
2. On the **Tools** menu, click **Internet Options**.
3. On the **Security** tab, click the **Local intranet** icon, and then click **Sites**.
4. Click **Advanced**, and in **Add this Web site to the zone**, type the full Domain Name System (DNS) name of the account federation server (for example, https://fs1.fabrikam.com), and then click **Add**.
5. Click **OK** three times.

## Configuring Internet Explorer settings by using Group Policy

For most deployments, we recommend that you use Group Policy to push the appropriate Internet Explorer settings to each client computer.

Membership in **Domain Admins** or **Enterprise Admins**, or equivalent, in Active Directory Domain Services (AD DS) is the minimum required to complete this procedure. Review details about using the appropriate accounts and group memberships at [Local and Domain Default Groups](/en-us/previous-versions/orphan-topics/ws.10/dd728026%28v=ws.10%29) (http://go.microsoft.com/fwlink/?LinkId=83477).

#### To configure client computers to trust the account federation server by using Group Policy

1. On a domain controller in the forest of the account partner organization, start the **Group Policy Management** snap-in.
2. Find the appropriate Group Policy Object (GPO), right-click it, and then click **Edit**.
3. In the console tree, open **User Configuration\Preferences\Windows Settings\Internet Explorer Maintenance**, and then click **Security**.
4. In the details pane, double-click **Security Zones and Content Ratings**.
5. Under **Security Zones and Privacy**, click **Import the current security zones and privacy settings**, and then click **Modify Settings**.
6. Click **Local intranet**, and then click **Sites**.
7. In **Add this Web site to the zone**, type the full DNS name of the account federation server (for example, https://fs1.fabrikam.com), click **Add**, and then click **Close**.
8. Click **OK** two times to apply these changes to Group Policy.