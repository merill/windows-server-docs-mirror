---
layout: Conceptual
title: NPS Templates | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/technologies/nps/nps-templates
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: This topic provides an overview of Network Policy Server Templates in Windows Server 2016.
ms.topic: concept-article
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: 329eda3a-bde5-b3b8-88f1-36a131a44982
document_version_independent_id: f74762fe-1068-b734-5025-0e99faecd4a1
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/technologies/nps/nps-templates.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/technologies/nps/nps-templates
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/technologies/nps/nps-templates.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 604b1eda-8b6b-fe56-d651-7c1d48ffadd7
---

# NPS Templates | Microsoft Learn

Network Policy Server (NPS) templates allow you to create configuration elements, such as Remote Authentication Dial-In User Service (RADIUS) clients or shared secrets, that you can reuse on the local NPS and export for use on other NPSs.

NPS templates are designed to reduce the amount of time and cost that it takes to configure NPS on one or more servers. The following NPS template types are available for configuration in Templates Management:

- Shared Secrets
- RADIUS Clients
- Remote RADIUS Servers
- IP Filters
- Remediation Server Groups

Configuring a template is different than configuring the NPS directly. Creating a template does not affect the NPS's functionality. It is only when you select the template in the appropriate location in the NPS console that the template affects the NPS functionality.

For example, if you configure a RADIUS client in the NPS console under RADIUS Clients and Servers, you have altered the NPS configuration and taken one step in configuring NPS to communicate with one of your network access servers (NAS's). (The next step would be to configure the NAS to communicate with NPS.) However, if you configure a new RADIUS Clients template in the NPS console under **Templates Management** rather than creating a new RADIUS client under **RADIUS Clients and Servers**, you have created a template, but you have not altered the NPS functionality yet. To alter the NPS functionality, you must select the template from the correct location in the NPS console.

## Creating templates

To create a template, open the NPS console, right-click a template type, such as **IP Filters**, and then click **New**. A new template properties dialog box opens that allows you to configure your template.

## Using templates locally

You can use a template that you've created in **Templates Management** by navigating to a location in the NPS console where the template can be applied. For example, if you create a new Shared Secrets template that you want to apply to a RADIUS client configuration, in **RADIUS Clients and Servers** and **RADIUS Clients**, open the RADIUS client properties. In **Select an existing Shared Secrets template**, select the template you previously created from the list of available templates.

For more information about NPS, see [Network Policy Server (NPS)](nps-top).