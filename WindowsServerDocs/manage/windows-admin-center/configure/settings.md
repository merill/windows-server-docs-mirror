---
layout: Conceptual
title: Settings | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/manage/windows-admin-center/configure/settings
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-admin-center
ms.update-cycle: 365-days
feedback_product_url: https://aka.ms/wacfeedback
description: Learn about settings in Windows Admin Center (Project Honolulu). User settings let users change their language/region and other preferences. Gateway settings let administrators configure the gateway.
ms.topic: concept-article
author: robinharwood
ms.author: roharwoo
ms.date: 2018-04-12T00:00:00.0000000Z
locale: en-us
document_id: d18b413e-74c7-9d71-63c6-360c0bcba261
document_version_independent_id: 546104d1-d9de-94f7-2183-8552832a0769
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/manage/windows-admin-center/configure/settings.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: manage/windows-admin-center/configure/settings
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/manage/windows-admin-center/configure/settings.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: ea7f3489-9c61-c69d-3d01-cdb4dbb2fcd2
---

# Settings | Microsoft Learn

Windows Admin Center settings consist of user-level and gateway-level settings. A change to a user-level setting only affects the current user's profile, while a change to a gateway-level setting affects all users on that Windows Admin Center gateway.

## User settings

User-level settings consist of the following sections:

- Account
- Language/Region
- Personalization
- Suggestions

In the **Account** tab, users can review the credentials they have used to authenticate to Windows Admin Center. If Microsoft Entra ID is configured to be the identity provider, the user can log out of their Microsoft Entra account from this tab.

In the **Language/Region** tab, users can change the language and region formats displayed by Windows Admin Center.

In the **Personalization** tab, users can toggle to a dark UI theme.

In the **Suggestions** tab, users can toggle suggestions about Azure services and new features.

## Development settings

Development settings in Windows Admin Center consist of the following sections:

- Advanced
- Performance profile

The **Advanced** tab gives Windows Admin Center extension developers additional capabilities.

The **Performance profile** tab lets you collect performance data about your Windows Admin Center session.

## Gateway settings

Gateway-level settings consist of the following sections:

- Access
- Diagnostics & feedback
- Extensions
- General
- Internet Access
- Proxy
- Register
- Updates
- Shared Connections
- WebSocket validation

Only gateway administrators are able to see and change these settings. Changes to these settings change the configuration of the gateway and affect all users of the Windows Admin Center gateway.

The **Access** tab lets administrators configure who can access the Windows Admin Center gateway, as well as the identity provider used to authenticate users. [Learn more about controlling access to the gateway.](user-access-control)

In the **Diagnostics & feedback** tab, users can choose how much diagnostic data they want to send to Microsoft.

In the **Extensions** tab, administrators can install, uninstall, or update gateway extensions. [Learn more about extensions.](using-extensions)

In the **General** tab, users can select to have their UI session of Windows Admin Center expire after some period of inactivity.

The **Internet Access** tab lets administrators configure who can access the Windows Admin Center gateway, as well as the identity provider used to authenticate users. [Learn more about controlling access to the gateway.](user-access-control)

The **Proxy** tab allows users to configure a proxy server to redirect all Windows Admin Center outbound traffic.

From the **Register** tab, administrators can register the gateway with Azure to enable [Azure integration features](../azure/azure-integration) in Windows Admin Center.

Using the **Updates** tab, users can see which version of Windows Admin Center is running and if this version is up to date.

Using the **Shared Connections** tab, administrators can configure a single list of connections to be shared across all users of the Windows Admin Center gateway. [Learn more about configuring connections once for all users of a gateway.](shared-connections)

For **WebSocket validation**, administrators can now validate their WebSocket connections and customize these settings to various conditions. [Learn more about WebSocket validation](websocket-validation)