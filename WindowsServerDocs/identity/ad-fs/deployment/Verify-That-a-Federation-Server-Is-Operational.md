---
layout: Conceptual
title: Verify That a Federation Server Is Operational | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/deployment/verify-that-a-federation-server-is-operational
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Verify That a Federation Server Is Operational'
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: c72b22d1-fa48-0f88-8ec2-182727dba357
document_version_independent_id: 24fbb684-90ff-55aa-a24c-6bb7bfd1aee2
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/deployment/Verify-That-a-Federation-Server-Is-Operational.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/deployment/verify-that-a-federation-server-is-operational
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/deployment/Verify-That-a-Federation-Server-Is-Operational.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/aebdc4a3-c54b-4eea-94e3-663d5e166f57
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/1baec8e6-ab38-4b56-bb59-f6282d94f311
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 3e66347c-10b6-e046-f73a-3a4ff35a7e21
---

# Verify That a Federation Server Is Operational | Microsoft Learn

You can use the following procedures to verify that a federation server is operational; that is, that any client on the same network can reach a new federation server.

Membership in **Users**, **Backup Operators**, **Power Users**, **Administrators** or equivalent, on the local computer is the minimum required to complete this procedure. Review details about using the appropriate accounts and group memberships at [Local and Domain Default Groups](/en-us/previous-versions/orphan-topics/ws.10/dd728026%28v=ws.10%29).

### Procedure 1: To verify that a federation server is operational

1. To verify that Internet Information Services (IIS) is configured correctly on the federation server, log on to a client computer that is located in the same forest as the federation server.
2. Open a browser window, in the address bar type the federation server's DNS host name, and then append /adfs/fs/federationserverservice.asmx to it for the new federation server, for example:

    `https://fs1.fabrikam.com/adfs/fs/federationserverservice.asmx`
3. Press ENTER, and then complete the next procedure on the federation server computer. If you see the message **There is a problem with this website's security certificate**, click **Continue to this website**.

    The expected output is a display of XML with the service description document. If this page appears, IIS on the federation server is operational and serving pages successfully.

Membership in **Administrators**, or equivalent, on the local computer is the minimum required to complete this procedure. Review details about using the appropriate accounts and group memberships at [Local and Domain Default Groups](/en-us/previous-versions/orphan-topics/ws.10/dd728026%28v=ws.10%29).

### Procedure 2: To verify that a federation server is operational

1. Log on to the new federation server as an administrator.
2. On the **Start** screen, type **Event Viewer**, and then press ENTER.
3. In the details pane, double-click **Applications and Services Logs**, double-click **AD FS Eventing**, and then click **Admin**.
4. In the **Event ID** column, look for event ID 100. If the federation server is configured properly, you see a new event—in the Application log of Event Viewer—with the event ID 100. This event verifies that the federation server was able to successfully communicate with the Federation Service.

## Additional references

[Checklist: Setting Up a Federation Server](checklist--setting-up-a-federation-server)