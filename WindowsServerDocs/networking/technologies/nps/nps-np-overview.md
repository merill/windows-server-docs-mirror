---
layout: Conceptual
title: Network Policies | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/technologies/nps/nps-np-overview
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: This topic provides an overview of network policies for Network Policy Server in Windows Server 2016, and includes links to additional guidance about NPS.
ms.topic: concept-article
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: 61409086-a1d6-6d1b-2ba6-2e87ca21f2b1
document_version_independent_id: bee14d65-634e-799c-6ff9-b3943e629b71
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/technologies/nps/nps-np-overview.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/technologies/nps/nps-np-overview
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/technologies/nps/nps-np-overview.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: 73c242f1-5600-64f3-1d1f-b432eee84fae
---

# Network Policies | Microsoft Learn

You can use this topic for an overview of network policies in NPS.

Note

In addition to this topic, the following network policy documentation is available.

- [Access Permission](nps-np-access)
- [Configure Network Policies](nps-np-configure)

Network policies are sets of conditions, constraints, and settings that allow you to designate who is authorized to connect to the network and the circumstances under which they can or cannot connect.

When processing connection requests as a Remote Authentication Dial-In User Service (RADIUS) server, NPS performs both authentication and authorization for the connection request. During the authentication process, NPS verifies the identity of the user or computer that is connecting to the network. During the authorization process, NPS determines whether the user or computer is allowed to access the network.

To make these determinations, NPS uses network policies that are configured in the NPS console. NPS also examines the dial-in properties of the user account in Active Directory® Domain Services (AD DS) to perform authorization.

## Network Policies - An Ordered Set of Rules

Network policies can be viewed as rules. Each rule has a set of conditions and settings. NPS compares the conditions of the rule to the properties of connection requests. If a match occurs between the rule and the connection request, the settings defined in the rule are applied to the connection.

When multiple network policies are configured in NPS, they are an ordered set of rules. NPS checks each connection request against the first rule in the list, then the second, and so on, until a match is found.

Each network policy has a **Policy State** setting that allows you to enable or disable the policy. When you disable a network policy, NPS does not evaluate the policy when authorizing connection requests.

Note

If you want NPS to evaluate a network policy when performing authorization for connection requests, you must configure the **Policy State** setting by selecting the Policy enabled check box.

## Network policy properties

There are four categories of properties for each network policy:

### Overview

These properties allow you to specify whether the policy is enabled, whether the policy grants or denies access, and whether a specific network connection method, or type of network access server (NAS), is required for connection requests. Overview properties also allow you to specify whether the dial-in properties of user accounts in AD DS are ignored. If you select this option, only the settings in the network policy are used by NPS to determine whether the connection is authorized.

### Conditions

These properties allow you to specify the conditions that the connection request must have in order to match the network policy; if the conditions configured in the policy match the connection request, NPS applies the settings designated in the network policy to the connection. For example, if you specify the NAS IPv4 address as a condition of the network policy and NPS receives a connection request from a NAS that has the specified IP address, the condition in the policy matches the connection request.

### Constraints

Constraints are additional parameters of the network policy that are required to match the connection request. If a constraint is not matched by the connection request, NPS automatically rejects the request. Unlike the NPS response to unmatched conditions in the network policy, if a constraint is not matched, NPS denies the connection request without evaluating additional network policies.

### Settings

These properties allow you to specify the settings that NPS applies to the connection request if all of the network policy conditions for the policy are matched.

When you add a new network policy by using the NPS console, you must use the New Network Policy Wizard. After you have created a network policy by using the wizard, you can customize the policy by double-clicking the policy in the NPS console to obtain the policy properties.

For examples of pattern-matching syntax to specify network policy attributes, see [Use Regular Expressions in NPS](nps-crp-reg-expressions).

For more information about NPS, see [Network Policy Server (NPS)](nps-top).