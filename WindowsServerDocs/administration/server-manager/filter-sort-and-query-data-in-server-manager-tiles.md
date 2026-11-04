---
layout: Conceptual
title: Filter, sort, and query Data in Server Manager Tiles | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/server-manager/filter-sort-and-query-data-in-server-manager-tiles
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: administration
ms.update-cycle: 1095-days
description: Learn how to use tiles in Server Manager to filter and sort data, and create and save custom queries.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 7bc5a4d2-957e-1395-cb2c-bb186940e897
document_version_independent_id: 25663bc3-54e5-640d-4b74-65c91b6b8ff5
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/server-manager/filter-sort-and-query-data-in-server-manager-tiles.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/server-manager/filter-sort-and-query-data-in-server-manager-tiles
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/server-manager/filter-sort-and-query-data-in-server-manager-tiles.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: c7e9e9e4-6386-6fc0-ba48-122aec35660f
---

# Filter, sort, and query Data in Server Manager Tiles | Microsoft Learn

In Windows Server, tiles in Server Manager let you filter and sort data, and create and save custom queries. You can sort, use keyword filters, and run queries on list entries in the Events, Performance, Best Practices Analyzer, Services, and Roles and Features tiles on server role or group pages in Server Manager.

This topic contains the following sections.

- Filter list entries in tiles
- sort list entries in tiles
- create and run custom queries on tile data

## Filter list entries in tiles

The **Filter** text box is a quick way of reducing the list of entries that are displayed in a tile to only those entries that contain a specified text string.

#### To apply a filter to the list of entries in a tile

1. Open a role or server group page in Server Manager.
2. In the **Filter** text box of an Events, Performance, Best Practices Analyzer, Services, or Roles and Features tile, type a string on which you want to filter.

    for example, if you want to see only events with an event ID of 1014, type **1014** in the **Filter** text box. All collected events that contain the string **1014** in at least one field are returned as results.
3. Note that the filter changes the description text under the tile title. Instead of **All** results, it says **Filtered results**.
4. To clear the filter, delete the string in the filter box, or click **X**.

## sort list entries in tiles

sort list entries in Server Manager tiles by clicking column headings. Clicking a column heading the first time sorts column values in ascending alphanumeric order (arrow pointing up); clicking again sorts column values in descending alphanumeric order (arrow pointing down).

## create and run custom queries on tile data

You can create custom queries in the Events, Performance, Best Practices Analyzer, Services, or Roles and Features tiles in Server Manager. By default, the area of the tile toolbar in which you select criteria to build a custom query is hidden; click **expand** (chevron button at right edge of tile toolbar) to display query criteria.

#### To create a custom query for tile data

1. Open a role or server group page in Server Manager.
2. In an Events, Performance, Best Practices Analyzer, Services, or Roles and Features tile, expand the query-building area by clicking **expand**.
3. Click **add criteria** to open a list of attributes (or fields) that apply to the entries in the tile.
4. select criteria to add. When you are finished, click **add**. Criteria that you selected are added to the query-building area.
5. Click the hypertext operator to select an operator. For numerical or date and time criteria, for example, the default is **less than or equal to**.
6. Specify acceptable values for the criteria. For example, if you selected **date and time**, provide a date in the format *m/d/yyyy*.
7. Repeat these steps from step 3 forward to add more criteria to your query.

    You can add duplicates of criteria that are already in your query, but the duplicates are added to the query with the **or** operator.

    for example, to query for event IDs 1003 or 1014, you would first add the ID criteria to your query, make the value of ID equal to **1003**, and then add a second ID criteria to your query, making the value of the second ID equal to **1014**. The resulting query is **and ID equals 1003 or ID equals 1014**.
8. When you are finished adding criteria and specifying operators and values, click **Save** to save the query.
9. Enter a friendly name for the query. For example, the query created in the preceding step can be named **Licensing events**.
10. When you are finished viewing query results, click **Clear All** to clear all filters and queries, and display all entries in the list.
11. To run a saved query, click **Saved Search Queries**, and click the name of the saved query that you want to run.
12. To delete a saved query, click **Saved Search Queries**, and then click **X** by the name of the saved query that you want to delete.