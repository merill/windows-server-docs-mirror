---
layout: Conceptual
title: Verify That a Federation Server Proxy Is Operational | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/deployment/verify-that-a-federation-server-proxy-is-operational
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Verify That a Federation Server Proxy Is Operational'
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: f717adae-d699-3958-615e-88dd29b8bff7
document_version_independent_id: 30c5c43d-af3a-b2a5-cdeb-56f22f4230c7
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/deployment/Verify-That-a-Federation-Server-Proxy-Is-Operational.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/deployment/verify-that-a-federation-server-proxy-is-operational
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/deployment/Verify-That-a-Federation-Server-Proxy-Is-Operational.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 1d9d7668-39a1-0a01-5f88-fbfdbdc64d0c
---

# Verify That a Federation Server Proxy Is Operational | Microsoft Learn

You can use the following procedure to verify that the federation server proxy can communicate with the Federation Service in Active Directory Federation Services (AD FS). You run this procedure after you run the **AD FS Federation Server Proxy Configuration Wizard** to configure the computer to run in the federation server proxy role. For more information about how to run this wizard, see [Configure a Computer for the Federation Server Proxy Role](configure-a-computer-for-the-federation-server-proxy-role).

Important

The result of this test is the successful generation of a specific event in Event Viewer on the federation server proxy computer.

Membership in **Administrators**, or equivalent, on the local computer is the minimum required to complete this procedure. Review details about using the appropriate accounts and group memberships at [Local and Domain Default Groups](/en-us/previous-versions/orphan-topics/ws.10/dd728026%28v=ws.10%29).

### To verify that a federation server proxy is operational

1. Log on to the federation server proxy as an administrator.
2. On the **Start** screen, type**Event Viewer**, and then press ENTER.
3. In the details pane, double-click **Applications and Services Logs**, double-click **AD FS Eventing**, and then click **Admin**.
4. In the **Event ID** column, look for event ID 198.

    If the federation server proxy is configured properly, you see a new event in the Application log of Event Viewer, with the event ID 198. This event verifies that the federation server proxy service was started successfully and now is online.

## Additional references

[Checklist: Setting Up a Federation Server Proxy](checklist--setting-up-a-federation-server-proxy)