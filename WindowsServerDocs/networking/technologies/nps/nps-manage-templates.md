---
layout: Conceptual
title: Manage NPS Templates | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/technologies/nps/nps-manage-templates
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: This topic provides instructions on how to create, apply, export, and import NPS templates for Network Policy Server in Windows Server 2016.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: 2009d884-dc85-9d80-093d-0078de87c79d
document_version_independent_id: be4a28fc-1c9a-5311-94e0-1035aa3baaf4
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/technologies/nps/nps-manage-templates.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/technologies/nps/nps-manage-templates
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/technologies/nps/nps-manage-templates.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: c5ad60df-c6ed-bb88-ce5d-1b33226e0646
---

# Manage NPS Templates | Microsoft Learn

You can use Network Policy Server (NPS) templates to create configuration elements, such as Remote Authentication Dial-In User Service (RADIUS) clients or shared secrets, that you can reuse on the local NPS and export for use on other NPSs.

Templates Management provides a node in the NPS console where you can create, modify, delete, duplicate, and view the use of NPS templates. NPS templates are designed to reduce the amount of time and cost that it takes to configure NPS on one or more servers.

The following NPS template types are available for configuration in Templates Management.

- **Shared Secrets**. This template type makes it possible for you to specify a shared secret that you can reuse (by selecting the template in the appropriate location in the NPS console) when you configure RADIUS clients and servers.
- **RADIUS Clients**. This template type makes it possible for you to configure RADIUS client settings that you can reuse by selecting the template in the appropriate location in the NPS console.
- **Remote RADIUS Servers**. This template makes it possible for you to configure remote RADIUS server settings that you can reuse by selecting the template in the appropriate location in the NPS console.
- **IP Filters**. This template makes it possible for you to create Internet Protocol version 4 (IPv4) and Internet Protocol version 6 (IPv6) filters that you can reuse (by selecting the template in the appropriate location in the NPS console) when you configure network policies.

## Create an NPS Template

Configuring a template is different than configuring the NPS directly. Creating a template does not affect the NPS's functionality. It is only when you select the template in the appropriate location in the NPS console and apply the template that the template affects the NPS functionality.

For example, if you configure a RADIUS client in the NPS console under **RADIUS Clients and Servers**, you alter the NPS configuration and take one step in configuring NPS to communicate with one of your network access servers. (The next step is to configure the network access server (NAS) to communicate with NPS.)

However, if you configure a new **RADIUS Clients** template in the NPS console under **Templates Management** rather than creating a new RADIUS client under **RADIUS Clients and Servers**, you have created a template, but you have not altered the NPS functionality yet. To alter the NPS functionality, you must apply the template from the correct location in the NPS console.

The following procedure provides instructions on how to create a new template.

Membership in **Administrators**, or equivalent, is the minimum required to complete this procedure.

### To create an NPS template

1. On the NPS, in Server Manager, click **Tools**, and then click **Network Policy Server**. The NPS console opens.
2. In the NPS console, expand **Templates Management**, right-click a template type, such as **RADIUS Clients**, and then click **New**.
3. A new template properties dialog box opens that you can use to configure your template.

## Apply an NPS Template

You can use a template that you have created in **Templates Management** by navigating to a location in the NPS console where you can apply the template. For example, if you want to apply a Shared Secrets template to a RADIUS client configuration, you can use the following procedure.

Membership in **Administrators**, or equivalent, is the minimum required to complete this procedure.

### To apply an NPS template

1. On the NPS, in Server Manager, click **Tools**, and then click **Network Policy Server**. The NPS console opens.
2. In the NPS console, expand **RADIUS Clients and Servers**, and then expand **RADIUS Clients**.

3.In **RADIUS Clients**, in the details pane, right-click the RADIUS client to which you want to apply the NPS template, and then click **Properties**.

1. In the properties dialog box for the RADIUS client, in **Select an existing Shared Secrets template**, select the template that you want to apply from the list of templates.

## Export or Import NPS Templates

You can export templates for use on other NPSs, or you can import templates into **Templates Management** for use on the local computer.

Membership in **Administrators**, or equivalent, is the minimum required to complete this procedure.

### To export or import NPS templates

1. To export NPS templates, in the NPS console, right-click **Templates Management**, and then click **Export Templates to a File**.
2. To import NPS templates, in the NPS console, right-click **Templates Management**, and then click **Import Templates from a Computer** or **Import Templates from a File**.