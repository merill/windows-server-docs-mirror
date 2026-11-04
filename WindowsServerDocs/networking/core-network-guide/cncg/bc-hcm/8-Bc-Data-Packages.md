---
layout: Conceptual
title: Create Content Server Data Packages for Web and File Content (Optional) | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/core-network-guide/cncg/bc-hcm/8-bc-data-packages
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Learn how to prehash content on Web and file servers, and then create data packages to import on your hosted cache server.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: 89038717-1679-67bc-4073-b78d7344c079
document_version_independent_id: 9a32fc98-556d-42b5-ef60-7c77b0d5be0f
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/core-network-guide/cncg/bc-hcm/8-Bc-Data-Packages.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/core-network-guide/cncg/bc-hcm/8-bc-data-packages
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/core-network-guide/cncg/bc-hcm/8-Bc-Data-Packages.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 21069897-edd9-fbfa-7a39-9610f676f0a0
---

# Create Content Server Data Packages for Web and File Content (Optional) | Microsoft Learn

You can use this procedure to prehash content on Web and file servers, and then create data packages to import on your hosted cache server.

This procedure is optional because you are not required to prehash and preload content on your hosted cache servers. If you do not preload content, data is added to the hosted cache automatically as clients download it over the WAN connection.

This procedure provides instructions for prehashing content on both file servers and Web servers. If you do not have one of those types of content servers, you do not have to perform the instructions for that content server type.

Important

Before you perform this procedure, you must install and configure BranchCache on your content servers. In addition, if you plan on changing the server secret on a content server, do so before pre-hashing content – modifying the server secret invalidates previously-generated hashes.

To perform this procedure, you must be a member of the Administrators group.

## To create content server data packages

1. On each content server, locate the folders and files that you want to prehash and add to a data package. Identify or create a folder where you want to save your data package later in this procedure.
2. On the server computer, open Windows PowerShell with Administrator privileges.
3. Do one or both of the following, depending on the types of content servers that you have:

    Note

    The value for the –Path parameter is the folder where your content is located. You must replace the example values in the commands below with a valid folder location on your content server that contains data that you want to prehash and add to a package.

    - If the content that you want to prehash is on a file server, type the following command, and then press ENTER.

        ```
        Publish-BCFileContent -Path D:\share -StageData
        ```
    - If the content that you want to prehash is on a Web server, type the following command, and then press ENTER.

        ```
        Publish-BCWebContent –Path D:\inetpub\wwwroot -StageData
        ```
4. Create the data package by running the following command on each of your content servers. Replace the example value (D:\temp) for the –Destination parameter with the location that you identified or created at the beginning of this procedure.

    ```
    Export-BCDataPackage –Destination D:\temp
    ```
5. From the content server, access the share on your hosted cache servers where you want to preload content, and copy the data packages to the shares on the hosted cache servers.

To continue with this guide, see [Import Data Packages on the Hosted Cache Server (Optional)](9-bc-import-data).