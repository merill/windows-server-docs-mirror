---
layout: Conceptual
title: Configure Performance Monitoring | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/deployment/configure-performance-monitoring
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Configure Performance Monitoring'
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 1d3ddae5-9fdd-25f9-f923-e2ef622b263d
document_version_independent_id: 662ba8de-9cf6-70e1-b9b1-2eab722369ee
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/deployment/Configure-Performance-Monitoring.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/deployment/configure-performance-monitoring
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/deployment/Configure-Performance-Monitoring.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: 6b53d985-c44b-19a5-b9c0-ccf1daae531b
---

# Configure Performance Monitoring | Microsoft Learn

AD FS includes its own dedicated performance counters to help you monitor the performance of both federation servers and federation server proxy computers. To use Performance Monitor to monitor the performance of your AD FS servers, it's useful to create a new data collector set and add the AD FS counters to that view. The following procedure describes how to configure performance monitoring for AD FS.

#### To configure performance monitoring for AD FS using Performance Monitor

1. On the **Start** screen, type **Performance Monitor**, and then press ENTER.
2. In the console tree, expand **Data Collector Sets**, right-click **User Defined**, point to **New**, and then click **Data Collector Set**.

    The Create New Data Collector Set Wizard appears.
3. In **Create New Data Collector Set**, for **Name** type a name for the new data collector set (such as "AD FS performance"), click **Create manually (Advanced)**, and then click **Next**.
4. For the type of data to include, verify that **Create data logs** is selected, and then click the check boxes for the following data types: **Performance counter**, **Event trace data**, **System configuration information**.
5. For performance counters, expand **AD FS** in the **Available counters** list, and then click **Add**.

    The AD FS performance counters should appear in the **Added counters** list.
6. When you are prompted to add event trace providers, click **Add**, select **AD FS Eventing** and **AD FS Tracing** from the list of providers.
7. When you are prompted to add registry keys to monitor, click **Next**.
8. When you are prompted to specify the location to save the performance data, you can accept the default location (**%systemdrive%\PerfLogs\Admin\***&lt;data\_collector\_set&gt;*, and then click **Next**.
9. When you are prompted to create the data collector set, select **Save and close**, and then click **Finish**.

    The new data collector set appears in the console tree under the **User Defined** node.
10. Use the following steps to work with the AD FS performance counters:

    - To begin performance monitoring using AD FS-related counters, right-click the data collector set that you added (such as "AD FS performance"), and then click **Start**.
    - To create a report to view the performance monitoring results, right-click the data collector set that you added (such as "AD FS performance"), and then click **Latest Report**.
    - To end a capture of performance data so that you can view the latest report, right-click the data collector set that you added (such as "AD FS performance"), and then click **Stop**.

    The latest report is added and numbered automatically (starting at 000001) under the **Report\User Defined***\&lt;data\_collector\_set&gt;* node in the console tree.

## AD FS performance counters

The following table lists the AD FS performance counters and describes how they are useful for monitoring activity that relates to either a federation server or federation server proxy.

| Counter | Description | Can be used on: |
| --- | --- | --- |
| Token Requests | Monitors the number of token requests sent to the federation server including SSOAuth token requests. | Federation Servers |
| Token Requests/sec | Monitors the number of token requests sent to the federation server including SSOAuth token requests per second. | Federation Servers |
| Federation Metadata Requests | Monitors the number of incoming federation metadata requests sent to the federation server. | Federation Servers |
| Federation Metadata Requests/sec | Monitors the number of incoming federation metadata requests per second that are sent to the federation server. | Federation Servers |
| Artifact Resolution Requests | Monitors the number of incoming federation metadata requests per second that are sent to the federation server. | Federation Servers |
| Artifact Resolution Requests/sec | Monitors the number of requests to the artifact resolution endpoint per second that are sent to the federation server. | Federation Servers |
| Proxy Requests | Monitors the number of incoming requests sent to the federation server proxy. | Federation Server Proxies |
| Proxy Requests/sec | Monitors the number of incoming requests per second that are sent to the federation server proxy. | Federation Server Proxies |
| Proxy MEX Requests | Monitors the number of incoming WS-Metadata Exchange (MEX) requests that are sent to the federation server proxy. | Federation Server Proxies |
| Proxy MEX Requests/sec | Monitors the number of incoming MEX requests per second that are sent to the federation server proxy. | Federation Server Proxies |