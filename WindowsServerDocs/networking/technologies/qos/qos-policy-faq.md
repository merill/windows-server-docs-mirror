---
layout: FAQ
title: QoS frequently asked questions | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/technologies/qos/qos-policy-faq
summary: >
  <blockquote>

  </blockquote>

  <p>Following are frequently asked questions – and answers to those questions – for QoS Policy.</p>
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: This topic provides answers to questions about Quality of Service (QoS) Policy in Windows Server 2016.
ms.topic: faq
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: 0dd8d0b3-db73-4b3e-92e3-6e8223e4c27d
document_version_independent_id: afd3f8e6-7a63-0bde-9c7a-616a7256ffb8
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/technologies/qos/qos-policy-faq.yml
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: faq
toc_rel: ../../toc.json
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/technologies/qos/qos-policy-faq
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/technologies/qos/qos-policy-faq.yml
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 7c72543b-a551-38bf-b5f3-b674a9f94800
---

# QoS frequently asked questions | Microsoft Learn

Following are frequently asked questions – and answers to those questions – for QoS Policy.

## What operating system does my domain controller need to be running to use QoS Policy?

Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2, or Windows Server 2008

## What operating systems support the application of QoS Policy to the user or computer?

You can apply QoS policies to users or computers running Windows Server 2016, Windows 10, Windows Server 2012 R2, Windows 8.1, Windows Server 2012, Windows 8, Windows Server 2008 R2, Windows Server 2008, and Windows Vista.

## Do QoS policies apply to the sender or receiver of traffic?

QoS policies must be applied on the sending computer to affect its outbound traffic. In order to affect the bidirectional traffic of two computers, QoS policies need to be applied to both computers.

## What happens if conflicting QoS policies are deployed to the same computer?

If multiple policies apply, the more specific QoS policy takes precedence. For example, a policy that states a host address (192.168.4.12) gets applied instead of a less specific network address (192.168.0.0/16). If a computer-level and user-level policy have the same specificity, the user-level QoS policy is applied instead of the computer-level QoS policy.

## Is QoS Policy enabled by default?

No, QoS Policy is not enabled by default. You must create QoS policies manually to enable QoS. For more information, see [Manage QoS Policy](qos-policy-manage).

For the first topic in this guide, see [Quality of Service (QoS) Policy](qos-policy-top).