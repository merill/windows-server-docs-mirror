---
layout: Conceptual
title: LDAP considerations in ADDS performance tuning | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/performance-tuning/role/active-directory-server/ldap-considerations
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: administration
ms.update-cycle: 1095-days
description: LDAP considerations in Active Directory workloads
ms.topic: best-practice
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 9d29a789-1da4-15fe-b147-ee7d26c8fbe2
document_version_independent_id: 88861372-bef7-0dd4-1859-25fb5f18d28b
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/performance-tuning/role/active-directory-server/ldap-considerations.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/performance-tuning/role/active-directory-server/ldap-considerations
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/performance-tuning/role/active-directory-server/ldap-considerations.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/12ed19f9-ebdf-4c8a-8bcd-7a681836774d
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3a764584-4f97-452b-8f1d-36f19b12f6ae
platformId: fd423e7b-d5bc-94ca-2c93-44822747e11b
---

# LDAP considerations in ADDS performance tuning | Microsoft Learn

Important

The following is a summary of the key recommendations and considerations to optimize server hardware for Active Directory workloads covered in greater depth in the [Capacity Planning for Active Directory Domain Services](capacity-planning-for-active-directory-domain-services) article. Readers are highly encouraged to review [Capacity Planning for Active Directory Domain Services](capacity-planning-for-active-directory-domain-services) for a greater technical understanding and implications of these recommendations.

## Verify LDAP queries

Verify that LDAP queries conform with the creating efficient queries recommendations.

There is extensive documentation on MSDN about how to properly write, structure, and analyze queries for use against Active Directory. For more info, see [Creating More Efficient Microsoft Active Directory-Enabled Applications](/en-us/previous-versions/ms808539%28v=msdn.10%29).

## Optimize LDAP page sizes

When returning results with multiple objects in response to client requests, the domain controller has to temporarily store the result set in memory. Increasing page sizes will cause more memory usage and can age items out of cache unnecessarily. In this case, the default settings are optimal. There are several scenarios where recommendations were made to increase the page size settings. We recommend using the default values unless specifically identified as inadequate.

When queries have many results, a limit of similar queries concurrently executed may be encountered. This occurs as the LDAP server may deplete a global memory area known as the cookie pool. It may be necessary to increase the size of the pool as discussed in [How LDAP Server Cookies Are Handled](../../../../identity/ad-ds/manage/how-ldap-server-cookies-are-handled).

To tune these settings, see [Windows Server 2008 and newer domain controller returns only 5000 values in a LDAP response](https://support.microsoft.com/kb/2009267).

## Determine whether to add indices

Indexing attributes is useful when searching for objects that have the attribute name in a filter. Indexing can reduce the number of objects that must be visited when evaluating the filter. However, this reduces the performance of write operations because the index must be updated when the corresponding attribute is modified or added. It also increases the size of the directory database, though the benefits often outweigh the cost of storage. Logging can be used to find the expensive and inefficient queries. Once identified, consider indexing some attributes that are used in the corresponding queries to improve the search performance. For more info on how Active Directory Searches work, see [How Active Directory Searches Work](/en-us/previous-versions/windows/it-pro/windows-server-2003/cc755809%28v=ws.10%29).

### Scenarios that benefit in adding indices

- Client load in requesting the data is generating significant CPU usage and the client query behavior cannot be changed or optimized.
- The client load is generating significant disk I/O on a server due to an unindexed attribute and the client query behavior cannot be changed or optimized.
- A query is taking a long time and is not completing in an acceptable timeframe to the client due to lack of covering indices.
- Large volumes of queries with high durations are causing consumption and exhaustion of ATQ LDAP Threads. Monitor the following performance counters:

    - **NTDS\Request Latency** – This is subject to how long the request takes to process. Active Directory times out requests after 120 seconds (default), however, the majority should run much faster and extremely long running queries should get hidden in the overall numbers. Look for changes in this baseline, rather than absolute thresholds.

        Note

        High values here can also be indicators of delays in "proxying" requests to other domains and CRL checks.
    - **NTDS\Estimated Queue Delay** – This should ideally be near 0 for optimal performance as this means that requests spend no time waiting to be serviced.

These scenarios can be detected using one or more of the following approaches:

- [Determining Query Timing with the Statistics Control](/en-us/previous-versions/ms808539%28v=msdn.10%29)
- [Tracking Expensive and Inefficient Searches](/en-us/previous-versions/ms808539%28v=msdn.10%29)
- Active Directory Diagnostics Data Collector Set in Performance Monitor ([Son of SPA: AD Data Collector Sets in Win2008 and beyond](/en-us/archive/blogs/askds/son-of-spa-ad-data-collector-sets-in-win2008-and-beyond))
- Searches using any filter besides "(objectClass=\*)" that use the Ancestors Index.

### Other index considerations

- Ensure that creating the index is the right solution to the problem after tuning the query has been exhausted as an option. Sizing hardware properly is very important. Indices should be added only when the right fix is to index the attribute, and not an attempt to obfuscate hardware problems.
- Indices increase the size of the database by a minimum of the total size of the attribute being indexed. An estimate of database growth can therefore be evaluated by taking the average size of the data in the attribute and multiplying by the number of objects that will have the attribute populated. Generally this is about a 1% increase in database size. For more info, see [How the Data Store Works](/en-us/previous-versions/windows/it-pro/windows-server-2003/cc772829%28v=ws.10%29).
- If search behavior is predominantly done at the organization unit level, consider indexing for containerized searches.
- Tuple indices are larger than normal indices, but it is much harder to estimate the size. Use normal indices size estimates as the floor for growth, with a maximum of 20%. For more info, see [How the Data Store Works](/en-us/previous-versions/windows/it-pro/windows-server-2003/cc772829%28v=ws.10%29).
- If search behavior is predominantly done at the organization unit level, consider indexing for containerized searches.
- Tuple Indices are needed to support medial search strings and final search strings. Tuple indices are not needed for initial search strings.

    - Initial Search String – (samAccountName=MYPC\*)
    - Medial Search String - (samAccountName=\*MYPC\*)
    - Final Search String – (samAccountName=\*MYPC$)
- Creating an index will generate disk I/O while the index is being built. This is done on a background thread with lower priority and incoming requests will be prioritized over the index build. If capacity planning for the environment has been done correctly, this should be transparent. However, write-heavy scenarios or an environment where the load on the domain controller storage is unknown could degrade client experience and should be done off-hours.
- Affects to replication traffic is minimal since building indices occurs locally.

For more info, see the following:

- [Creating More Efficient Microsoft Active Directory-Enabled Applications](/en-us/previous-versions/ms808539%28v=msdn.10%29)
- [Searching in Active Directory Domain Services](/en-us/windows/win32/ad/searching-in-active-directory-domain-services)
- [Indexed Attributes](/en-us/windows/win32/ad/indexed-attributes)

## Additional References

- [Performance tuning Active Directory Servers](./)
- [Hardware considerations](hardware-considerations)
- [Proper placement of domain controllers and site considerations](site-definition-considerations)
- [Troubleshooting ADDS performance](troubleshoot)
- [Capacity Planning for Active Directory Domain Services](capacity-planning-for-active-directory-domain-services)