---
layout: Conceptual
title: Access Permission | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/technologies/nps/nps-np-access
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: This topic provides an overview of network policy access permission for Network Policy Server in Windows Server 2016.
ms.topic: concept-article
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: e00bd1f3-41db-172e-ca7f-33bf1c395b43
document_version_independent_id: 9db2ab73-d0bd-f037-d8f3-56b335050963
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/technologies/nps/nps-np-access.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/technologies/nps/nps-np-access
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/technologies/nps/nps-np-access.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: 2d4c9bea-2591-536f-fa12-f0db8f964e6b
---

# Access Permission | Microsoft Learn

Access permission is configured on the **Overview** tab of each network policy in Network Policy Server (NPS).

This setting allows you to configure the policy to either grant or deny access to users if the conditions and constraints of the network policy are matched by the connection request.

Access permission settings have the following effect:

- **Grant access**. Access is granted if the connection request matches the conditions and constraints that are configured in the policy.
- **Deny access**. Access is denied if the connection request matches the conditions and constraints that are configured in the policy.

Access permission is also granted or denied based on your configuration of the dial-in properties of each user account.

Note

User accounts and their properties, such as dial-in properties, are configured in either the Active Directory Users and Computers or the Local Users and Groups Microsoft Management Console (MMC) snap-in, depending on whether you have Active Directory® Domain Services (AD DS) installed.

The user account setting **Network Access Permission**, which is configured on the dial-in properties of user accounts, overrides the network policy access permission setting. When network access permission on a user account is set to the **Control access through NPS Network Policy** option, the network policy access permission setting determines whether the user is granted or denied access.

Note

In Windows Server 2016, the default value of **Network Access Permission** in AD DS user account dial-in properties is **Control access through NPS Network Policy**.

When NPS evaluates connection requests against configured network policies, it performs the following actions:

- If the conditions of the first policy are not matched, NPS evaluates the next policy, and continues this process until either a match is found or all policies have been evaluated for a match.
- If the conditions and constraints of a policy are matched, NPS either grants or denies access, depending on the value of the Access Permission setting in the policy.
- If the conditions of a policy match but the constraints in the policy do not match, NPS rejects the connection request.
- If the conditions of all policies do not match, NPS rejects the connection request.

## Ignore user account dial-in properties

You can configure NPS network policy to ignore the dial-in properties of user accounts by selecting or clearing the **Ignore user account dial-in properties** check box on the **Overview** tab of a network policy.

Normally when NPS performs authorization of a connection request, it checks the dial-in properties of the user account, where the network access permission setting value can affect whether the user is authorized to connect to the network. When you configure NPS to ignore the dial-in properties of user accounts during authorization, network policy settings determine whether the user is granted access to the network.

The dial-in properties of user accounts contain the following:

- Network access permission
- Caller-ID
- Callback options
- Static IP address
- Static routes

To support multiple types of connections for which NPS provides authentication and authorization, it might be necessary to disable the processing of user account dial-in properties. This can be done to support scenarios in which specific dial-in properties are not required.

For example, the caller-ID, callback, static IP address, and static routes properties are designed for a client that is dialing into a network access server (NAS), not for clients that are connecting to wireless access points. A wireless access point that receives these settings in a RADIUS message from NPS might not be able to process them, which can cause the wireless client to be disconnected.

When NPS provides authentication and authorization for users who are both dialing in and accessing your organization network through wireless access points, you must configure the dial-in properties to support either dial-in connections (by setting dial-in properties) or wireless connections (by not setting dial-in properties).

You can use NPS to enable dial-in properties processing for the user account in some scenarios (such as dial-in) and to disable dial-in properties processing in other scenarios (such as 802.1X wireless and authenticating switch).

You can also use **Ignore user account dial-in properties** to manage network access control through groups and the access permission setting on the network policy. When you select the **Ignore user account dial-in properties** check box, network access permission on the user account is ignored.

The only disadvantage to this configuration is that you cannot use the additional user account dial-in properties of caller-ID, callback, static IP address, and static routes.

For more information about NPS, see [Network Policy Server (NPS)](nps-top).