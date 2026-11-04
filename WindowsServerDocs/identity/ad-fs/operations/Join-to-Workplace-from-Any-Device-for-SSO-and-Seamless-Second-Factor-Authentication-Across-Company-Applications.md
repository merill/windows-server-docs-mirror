---
layout: Conceptual
title: Join to Workplace from Any Device for SSO and Seamless Second Factor Authentication Across Company Applications | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/operations/join-to-workplace-from-any-device-for-sso-and-seamless-second-factor-authentication-across-company-applications
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Join to Workplace from Any Device for SSO and Seamless Second Factor Authentication Across Company Applications'
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: d7c159dc-3245-def5-11ab-35fc48df45c4
document_version_independent_id: f7f2ba06-24cb-ad8d-ce67-62683742092b
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/operations/Join-to-Workplace-from-Any-Device-for-SSO-and-Seamless-Second-Factor-Authentication-Across-Company-Applications.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/operations/join-to-workplace-from-any-device-for-sso-and-seamless-second-factor-authentication-across-company-applications
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/operations/Join-to-Workplace-from-Any-Device-for-SSO-and-Seamless-Second-Factor-Authentication-Across-Company-Applications.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/54918a83-0404-4863-9c91-715186c1f582
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b26f5f7a-0913-4a95-8337-ed7543902f2d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: b6dddcde-8f79-720c-2d85-9279a93e4b35
---

# Join to Workplace from Any Device for SSO and Seamless Second Factor Authentication Across Company Applications | Microsoft Learn

The rapid increase in the number of consumer devices and ubiquitous information access is changing the way that people perceive their technology. The constant use of information technology throughout the day, along with easy access of information, is blurring traditional boundaries between work and home life. These shifting boundaries are accompanied by a belief that personal technology-selected and customized to fit users' personalities, activities, and schedules-should extend into the workplace. To accommodate the growing requirement of personal consumer devices to be connected to enterprise networks, we are introducing the following value propositions:

- Administrators can control who has access to company resources that are based on application, user, device, and location.
- Employees can access applications and data everywhere, on any device. Employees can use Single Sign-On in browser applications or enterprise applications.

## Key concepts introduced in the solution

### Workplace Join

By using Workplace Join, information workers can join their personal devices with their company's workplace computers to access company resources and services. When you join your personal device to your workplace, it becomes a known device and provides seamless second factor authentication and Single Sign-On to workplace resources and applications. When a device is joined by Workplace Join, attributes of the device can be retrieved from the directory to drive conditional access for the purpose of authorizing issuance of security tokens for applications. Windows 8.1 and iOS 6.0+, and Android 4.0+ devices can be joined by using Workplace Join.

### Microsoft Entra Device Registration service

Workplace Join is made possible by the Microsoft Entra Device Registration service. When a device is joined by Workplace Join, the service provisions a device object in Microsoft Entra ID and then sets a key on the local device that is used to represent the device identity. This device identity can then be used with access control rules for applications that are hosted in the cloud and on-premises.

For more details, see [Introduction to device management in Microsoft Entra ID](/en-us/azure/active-directory/device-management-introduction).

### Workplace Join as a seamless second factor authentication

Companies can manage the risk that is related to information access and drive governance and compliance while granting consumer devices access to corporate resources. Workplace Join on devices provides the following capabilities to administrators:

- Identifies known devices with device authentication. Administrators can use this information to drive conditional access and control access to resources.
- Provides a more seamless sign-in experience for users to access company resources from trusted devices.

### Single Sign-On

Single Sign-On (SSO) in the context of this scenario is the functionality that reduces the number of password prompts that the end user has to enter to access company resources from known devices. This functionality implies that users are prompted only one time during the lifetime of SSO to access company applications and resource from this device. If a device uses Workplace Join, the user who is registered to use this device gets persistent SSO, by default for seven days. This user has a seamless sign-in experience in the same session or in new sessions.

## Solution Overview

As part of this solution, you learn how to use Workplace Join on a supported device and experience Single Sign-On to a company resource.

Note

To support Windows 8.1, iOS 6.0+, and Android 4.0+ devices, you MUST configure Microsoft Entra Device Registration along with device object write-back, see [Step-by-Step Guide for On-premises Conditional Access using Microsoft Entra Device Registration Service](/en-us/previous-versions/azure/dn788908%28v=azure.100%29)

This solution guides takes you through the following walkthrough steps:

1. [Walkthrough: Workplace Join with a Windows Device](walkthrough--workplace-join-with-a-windows-device)
2. [Walkthrough: Workplace Join with an iOS Device](walkthrough--workplace-join-with-an-ios-device)
3. [Walkthrough: Workplace Join with an Android Device](walkthrough--workplace-join-to-an-android-device)