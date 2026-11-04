---
layout: Conceptual
title: Manage OpenSSH with Group Policy | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/openssh/openssh-group-policy
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: administration
ms.update-cycle: 1095-days
ms.date: 2024-02-12T00:00:00.0000000Z
contributor: damaerte
keywords: OpenSSH, SSH, Win32-OpenSSH
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
description: Learn how to create a Group Policy object for OpenSSH
locale: en-us
document_id: 220973cf-6a46-e14d-b092-8c1829937428
document_version_independent_id: 220973cf-6a46-e14d-b092-8c1829937428
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/OpenSSH/openssh-group-policy.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/openssh/openssh-group-policy
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/OpenSSH/openssh-group-policy.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 88824917-65fa-091b-f1f9-33c117652cbf
---

# Manage OpenSSH with Group Policy | Microsoft Learn

Group Policy allows you to specify managed configurations for users and computers. This page will help you create a Group Policy object to manage the OpenSSH Server component.

## Prerequisites

Before you start, the following prerequisites must be met:

- You have administrator rights on the local device and the appropriate permissions to update Group Policy on your domain controller
- You are managing the in-box version of OpenSSH
- You are managing Operating Systems where both OpenSSH and Group Policy are present

## Create a Group Policy Object

To create a Group Policy to manage OpenSSH perform the following steps:

1. Open the Group Policy Management tool.
2. In the navigation pane, expand `Forest: your forest name`, expand `Domains`, expand your domain.
3. Select `Group Policy Objects`.
4. Right-click `Group Policy Objects`, then select New to create a new Object.
5. Name the Object so that it can be identified as managing OpenSSH. ![Screenshot of OpenSSH Group Policy.](media/openssh-gpo.png)
6. Double-click the new Object.
7. Navigate to the `Settings` tab.
8. Right-click on `Computer Configuration`, then select `Edit...`.
9. In the navigation pane, expand `Computer Configuration`, expand `Policies`, expand `Windows Settings`, expand `Security Settings`, then select `System Services`.
10. Double-click `OpenSSH SSH Server` in the services list.
11. Click the checkmark `Define this policy setting`.
12. Select the desired service startup mode; `Automatic`, `Manual`, `Disabled`. ![Screenshot of OpenSSH Group Policy Object.](media/openssh-policy.png)
13. Select `Apply`.