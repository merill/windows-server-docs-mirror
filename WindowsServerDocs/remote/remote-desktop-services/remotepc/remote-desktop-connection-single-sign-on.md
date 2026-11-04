---
layout: Conceptual
title: Connect to a Remote PC with Single Sign-On Using Microsoft Entra Authentication | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-desktop-services/remotepc/remote-desktop-connection-single-sign-on
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote-desktop-services
ms.update-cycle: 1095-days
description: Learn how to connect to remote PCs seamlessly with Microsoft Entra single sign-on authentication using Remote Desktop Connection (MSTSC). Follow our step-by-step guide.
ms.topic: how-to
ai-usage: ai-assisted
ms.author: roharwoo
author: robinharwood
ms.date: 2025-07-07T00:00:00.0000000Z
locale: en-us
document_id: 0f500e19-09ec-a998-20d7-8450991b1a56
document_version_independent_id: 0f500e19-09ec-a998-20d7-8450991b1a56
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-desktop-services/remotepc/remote-desktop-connection-single-sign-on.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-desktop-services/remotepc/remote-desktop-connection-single-sign-on
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-desktop-services/remotepc/remote-desktop-connection-single-sign-on.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ddab3cd8-636f-4a91-896e-1c23f399a6bd
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f409bb5d-e203-40c5-9d95-0ee717231beb
platformId: 107f19f5-3367-779f-a185-66485cb70273
---

# Connect to a Remote PC with Single Sign-On Using Microsoft Entra Authentication | Microsoft Learn

The Remote Desktop Connection app (MSTSC) supports single sign-on with Microsoft Entra authentication, enabling seamless connections to remote PCs without repeated credential entry. This authentication method streamlines remote access by automatically passing through your Microsoft Entra credentials when you're signed in to your local device, improving productivity and user experience.

This article shows you how to configure and use single sign-on with Microsoft Entra authentication in the Remote Desktop Connection app to connect to remote PCs.

## Prerequisites

To connect to a remote PC using single sign-on with Microsoft Entra authentication, you need:

- The remote PC and your local device must be running one of the following operating systems:

    - Windows 11 with [2022-10 Cumulative Updates for Windows 11 (KB5018418)](https://support.microsoft.com/kb/KB5018418) or later installed.
    - Windows 10, version 20H2 or later with [2022-10 Cumulative Updates for Windows 10 (KB5018410)](https://support.microsoft.com/kb/KB5018410) or later installed.
    - Windows Server 2022 with [2022-10 Cumulative Update for Microsoft server operating system (KB5018421)](https://support.microsoft.com/kb/KB5018421) or later installed.
- Remote Desktop needs to be enabled in your remote PC. You can follow the steps in [Enable Remote Desktop on your PC](remote-desktop-allow-access) to enable Remote Desktop.
- The remote PC must be network addressable by hostname, resolving to the IP address of the remote PC. Using an IP address directly isn't supported.
- The remote PC must be Microsoft Entra joined or Microsoft Entra hybrid joined. There's no requirement for the local device to be joined to a domain or Microsoft Entra. As a result, this method allows you to connect to the remote PC from:

    - Microsoft Entra joined or Microsoft Entra hybrid joined devices.
    - Active Directory domain joined devices.
    - Workgroup devices.
- If you're accessing an Azure VM, ensure the Microsoft Entra account is assigned the **Virtual Machine Administrator Login** or **Virtual Machine User Login** role. For more information, see [Steps to assign an Azure role](/en-us/azure/role-based-access-control/role-assignments-steps).
- If your organization is using [Microsoft Entra Conditional Access](/en-us/azure/active-directory/conditional-access/overview), your local device must satisfy the Conditional Access requirements to allow connection to the remote computer. Conditional Access policies can be applied to the application **Microsoft Remote Desktop** with ID **a4a365df-50f1-4397-bc59-1a1564b8bb9c** to control access to the remote PC when single sign-on is enabled.

    Important

    We recommend that you [enforce multifactor authentication Conditional Access](/en-us/azure/active-directory/conditional-access/howto-conditional-access-policy-all-users-mfa) and configure a periodic reauthentication policy using [Sign-in frequency control](/en-us/azure/active-directory/conditional-access/howto-conditional-access-session-lifetime) for added security.

## Connect to a remote PC using single sign-on with Microsoft Entra authentication

Here's how to connect to a remote PC using single sign-on with Microsoft Entra authentication

1. Launch the Remote Desktop Connection app on your local device from the Start menu, or by running `mstsc.exe` from a command prompt.
2. Select **Show Options** to expand the Remote Desktop Connection client, then select the **Advanced** tab.
3. Under **User authentication**, check the box **Use a web account to sign in to the remote computer**. This option is equivalent to the `enablerdsaadauth` RDP property. For more information, see [Supported RDP properties with Remote Desktop Services](/en-us/windows-server/remote/remote-desktop-services/clients/rdp-files).
4. Select the **General** tab and enter the NetBIOS domain name or fully qualified domain name (FQDN) of the remote PC in the **Computer** field. The name you enter must match the hostname of the remote PC in Microsoft Entra ID and be network addressable, resolving to the IP address of the remote PC. Using an IP address directly isn't supported.
5. Select **Connect**.
6. If you're prompted for credentials, your user account in Microsoft Entra ID might be automatically selected. If your account isn't automatically selected, specify the user name for your account in the format `user@domain.com` (the User Principal Name (UPN)).
7. Select **OK** to connect. You're prompted to allow the remote desktop connection when connecting to a new remote PC. Microsoft Entra remembers up to 15 hosts for 30 days before prompting again. If you see this dialogue, select **Yes** to connect.

## Session disconnection when locked

The Windows lock screen in the remote session doesn't support Microsoft Entra authentication tokens or passwordless authentication methods like FIDO keys. The lack of support for these authentication methods means that users can't unlock their screens in a remote session. When you try to lock a remote session, either through user action or system policy, the service instead disconnects the session and sends a message to the user explaining they were disconnected.

Disconnecting the session also ensures that when the connection is relaunched after a period of inactivity, Microsoft Entra ID reevaluates the applicable conditional access policies.