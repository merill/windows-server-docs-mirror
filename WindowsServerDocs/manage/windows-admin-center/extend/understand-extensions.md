---
layout: Conceptual
title: Understanding Windows Admin Center Extensions | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/manage/windows-admin-center/extend/understand-extensions
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-admin-center
ms.update-cycle: 365-days
feedback_product_url: https://aka.ms/wacfeedback
description: Understanding Windows Admin Center SDK Extensions (Project Honolulu)
ms.topic: concept-article
ms.author: roharwoo
author: robinharwood
ms.date: 2018-06-18T00:00:00.0000000Z
ms.custom: sfi-image-nochange
locale: en-us
document_id: 2a2afe1e-b896-2863-48a8-8cadf97247d9
document_version_independent_id: 64dc0897-4910-8ee7-018f-f0f432736ef6
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/manage/windows-admin-center/extend/understand-extensions.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: manage/windows-admin-center/extend/understand-extensions
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/manage/windows-admin-center/extend/understand-extensions.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: 2e394b38-1699-edc5-6d9d-1f5531819c9e
---

# Understanding Windows Admin Center Extensions | Microsoft Learn

In case you're not yet familiar with how Windows Admin Center works, let's start with the high-level architecture. Windows Admin Center is composed of two main components:

- Lightweight **web service** that serves Windows Admin Center UI web pages to web browser requests.
- **Gateway component** that listens for REST API requests from the web pages and relays WMI calls or PowerShell scripts to be executed on a target server or cluster.

![A diagram of a Windows Admin Center architecture.](../media/understand-extensions/wac-architecture-500px.png)

The Windows Admin Center UI web pages served by the web service have two main UI components from an extensibility perspective, solutions and tools, which are implemented as extensions, and, a third extension type called gateway plugins.

## Solution extensions

In the Windows Admin Center home screen, by default, you can add connections that are one of four types – Windows Server connections, Windows PC connections, server clusters connections and Azure VMs connections. Once a connection is added, the connection name and type will be displayed in the home screen. Clicking on the connection name will attempt to connect to the target server or cluster and then load the UI for the connection.

![Screenshot of the Add Connections feature of the Windows Admin Center.](../media/launch/use-get-started-5.png)

Each connection type maps to a solution, and solutions are defined through a type of extension called “solution” extensions. Solutions typically define a unique type of object you wish to manage through Windows Admin Center, such as servers, PCs or failover clusters. You could also define a new solution for connecting to and managing other devices such as network switches and Linux servers, or even services such as Remote Desktop Services.

## Tool extensions

When you click on a connection in the Windows Admin Center home screen and connect, the solution extension for the selected connection type will be loaded and you'll then be presented with the solution UI including a list of tools in the left navigation pane. When you click on a tool, the tool UI is loaded and displayed in the right pane.

![Windows Admin Center UI architecture](../media/understand-extensions/extend-understanding-extensions-2.png)

Each tool is defined through a second type of extension called “tool” extensions. When a tool is loaded, it can execute WMI calls or PowerShell scripts on a target server or cluster and display information in the UI or execute commands based on user input. A tool extension defines which solutions it should be displayed for, resulting in a different set of tools for each solution. If you're creating a new solution extension, you'll additionally need to write one or more tool extensions that provide functionality for the solution.

![List of tools for each solution](../media/understand-extensions/extend-understanding-extensions-3.png)

## Gateway plugins

The gateway service exposes REST APIs for the UI to call and relays commands and scripts to be executed on the target. The gateway service can be extended by gateway plugins that support different protocols. Windows Admin Center is pre-packaged with two gateway plugins, one for executing PowerShell scripts and the other for WMI commands. If you need to communicate with the target through a protocol other than PowerShell or WMI, such as REST, you can build a gateway plugin for this.