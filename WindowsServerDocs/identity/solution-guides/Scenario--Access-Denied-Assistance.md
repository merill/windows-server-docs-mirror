---
layout: Conceptual
title: Scenario Access-Denied Assistance | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/solution-guides/scenario--access-denied-assistance
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: 'Learn more about: Scenario: Access-Denied Assistance'
author: robinharwood
ms.author: roharwoo
ms.date: 2023-06-06T00:00:00.0000000Z
ms.topic: example-scenario
locale: en-us
document_id: b425f69f-cfa7-d0e2-a2a5-687336655688
document_version_independent_id: 2aad22a4-5360-2d4a-7d65-939672595184
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/solution-guides/Scenario--Access-Denied-Assistance.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/solution-guides/scenario--access-denied-assistance
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/solution-guides/Scenario--Access-Denied-Assistance.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6c57776-ab71-4356-880c-c5ff411d7fe1
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/e2d3fbf8-36df-4730-9ac5-e1c53887f039
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 7539e788-5fc9-ab0f-2110-aad382ffa573
---

# Scenario Access-Denied Assistance | Microsoft Learn

Users will get an access-denied message when they try to access shared files and folders on a file server for which they do not have permissions. Administrators often do not have the appropriate context to troubleshoot the access issue, which makes it hard to resolve the issue.

## Scenario description

Access-denied assistance is a new feature in Windows Server 2012, which provides the following ways to troubleshoot issues that are related to access to files and folders:

- **Self-assistance.** If a user can determine the issue and remediate the problem so that they can get the requested access, the impact to the business is low, and no special exceptions are needed in the central access policy. Access-denied assistance provides an access-denied message that file server administrators can customize with information specific to their organizations. For example, an administrator could set the message so that users can request access from a data owner without involving the file server administrator.
- **Assistance by the data owner.** You can define a distribution list for shared folders, and configure it so that the folder owner receives an email notification when a user needs access. If the data owner does not know how to help the user get access, the owner can forward this information to the file server administrator.
- **Assistance by the file server administrator.** This type of assistance is available when the user cannot fix an issue and the data owner cannot help. Windows Server 2012 provides a user interface where file server administrators can view the effective permissions for a user on a file or folder so that it is easier to troubleshoot access issues.

Access-denied assistance in Windows Server 2012 provides file server administrators the relevant access details so that they can determine the issue and appropriate tools so that they can make configuration changes to satisfy the access request. For example, a user might follow this process to access a file that they currently do not have access to:

- The user attempts to read a file in the \\financeshares shared folder, but the server displays an access-denied message.
- Windows Server 2012 displays the access-denied assistance information to the user with an option to request assistance.
- If the user requests access to the resource, the server sends an email with the access request information to the folder owner.

You can find planning information for configuring access-denied assistance in [Plan for Access-Denied Assistance](/en-us/previous-versions/orphan-topics/ws.11/jj574182%28v=ws.11%29?redirectedfrom=MSDN).

You can find steps about configuring access-denied assistance in [Deploy Access-Denied Assistance (Demonstration Steps)](deploy-access-denied-assistance--demonstration-steps-).

## In this scenario

This scenario is part of the Dynamic Access Control scenario. For more information about Dynamic Access Control, see:

- [Dynamic Access Control: Scenario Overview](dynamic-access-control--scenario-overview)

## Practical applications

Access-denied assistance in Windows Server 2012 contributes to Dynamic Access Control by giving users the ability to request access to shared files and folders directly from an access-denied message.

## Features included in this scenario

The following table lists the features that are part of this scenario and describes how they support it.

| Feature | How it supports this scenario |
| --- | --- |
| [File Server Resource Manager Overview](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831701%28v=ws.11%29) | Access-denied assistance can be configured by using the File Server Resource Manager console on the file server. |
| [File and Storage Services Overview](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831487%28v=ws.11%29) | File Server Resource Manager is a File and Storage Services role service, and it is comprised of a set of features that can be used to administer the file servers on your network. |