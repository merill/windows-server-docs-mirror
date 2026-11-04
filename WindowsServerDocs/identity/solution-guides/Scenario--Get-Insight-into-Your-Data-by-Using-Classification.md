---
layout: Conceptual
title: Scenario Get Insight into Your Data by Using Classification | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/solution-guides/scenario--get-insight-into-your-data-by-using-classification
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: 'Learn more about: Scenario: Get Insight into Your Data by Using Classification'
author: robinharwood
ms.author: roharwoo
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: example-scenario
locale: en-us
document_id: 5ef184b8-2494-501b-d93f-bafea68c842d
document_version_independent_id: 4ea60495-8929-c347-9aa6-c840f61db878
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/solution-guides/Scenario--Get-Insight-into-Your-Data-by-Using-Classification.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/solution-guides/scenario--get-insight-into-your-data-by-using-classification
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/solution-guides/Scenario--Get-Insight-into-Your-Data-by-Using-Classification.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
- https://authoring-docs-microsoft.poolparty.biz/devrel/2624a017-7337-44fa-9494-a407bb0e59fa
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
- https://authoring-docs-microsoft.poolparty.biz/devrel/a438284e-c3c3-4c36-ab0b-aa7c244b912c
platformId: 901a5118-a1a1-758c-13fa-a212be7c5962
---

# Scenario Get Insight into Your Data by Using Classification | Microsoft Learn

Reliance on data and storage resources has continued to grow in importance for most organizations. IT administrators face the growing challenge of overseeing larger and more complex storage infrastructures, while simultaneously being tasked with the responsibility to ensure that total cost-of-ownership is maintained at reasonable levels. Managing storage resources is not only about the volume or availability of data; it is also about enforcing company policies and knowing how storage is consumed to enable efficient utilization and compliance to mitigate risk. File Classification Infrastructure provides insight into your data by automating classification processes so that you can manage your data more effectively. The following classification methods are available with File Classification Infrastructure: manual, programmatic, and automatic. This topic focuses on the automatic file classification method.

## Scenario description

File Classification Infrastructure uses classification rules to automatically scan files and classify them according to the contents of the file. Classification properties are defined centrally in Active Directory so that these definitions can be shared across file servers in the organization. You can create classification rules that scan files for a standard string or for a string that matches a pattern (regular expression). When a configured classification parameter is found in a file, that file is classified as configured in the classification rule. Some examples of classification rules include:

- Classify any file that contains the string "Contoso Confidential" as having high business impact
- Classify any file that contains at least 10 social security numbers as having personally identifiable information

When a file is classified, you can use a file management task to take action on any files that are classified a specific way. The actions in a file management task include protecting the rights associated with the file, expiring the file, and running a custom action (such as posting information to a web service).

You can find planning information for configuring automatic file classification in [Plan for Automatic File Classification](assetId:///e3c3bb4b-3034-42b7-b391-8ef5f5851955).

You can find steps for how to automatically classify files in [Deploy Automatic File Classification (Demonstration Steps)](deploy-automatic-file-classification--demonstration-steps-).

## In this scenario

This scenario is part of the Dynamic Access Control scenario. For additional information about Dynamic Access Control, see:

- [Dynamic Access Control: Scenario Overview](dynamic-access-control--scenario-overview)

## Practical applications

File Classification Infrastructure in Windows Server 2012 contributes to Dynamic Access Control by enabling business data owners to easily classify and label data. The classification information that is stored in the central access policy allows you to define access policies for data classes that are critical to business.

## Features included in this scenario

The following table lists the features that are part of this scenario and describes how they support it.

| Feature | How it supports this scenario |
| --- | --- |
| [File Server Resource Manager Overview](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831701%28v=ws.11%29) | File Classification Infrastructure is a feature that is included in File Server Resource Manager. |
| [File and Storage Services Overview](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831487%28v=ws.11%29) | File Server Resource Manager is a feature that is included with the File Services server role. |