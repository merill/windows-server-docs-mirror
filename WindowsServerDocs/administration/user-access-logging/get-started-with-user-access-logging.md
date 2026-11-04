---
layout: Conceptual
title: Get Started with User Access Logging | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/user-access-logging/get-started-with-user-access-logging
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: administration
ms.update-cycle: 1095-days
description: Describes the User Access Logging feature and how to start using it.
ms.topic: get-started
author: robinharwood
ms.author: roharwoo
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: e08dc434-8973-ac3b-c7d1-2b438f47fbdb
document_version_independent_id: bd4b956e-4073-5c7a-ef17-0944ae8dd140
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/user-access-logging/get-started-with-user-access-logging.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/user-access-logging/get-started-with-user-access-logging
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/user-access-logging/get-started-with-user-access-logging.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: b497bed4-f515-c21d-ac54-b457ae9b8052
---

# Get Started with User Access Logging | Microsoft Learn

User Access Logging (UAL) is feature in Windows Server that aggregates client usage data by role and products on a local server. It helps Windows server administrators quantify requests from client computers for roles and services on a local server.

UAL is installed and enabled by default, and collects data in nearly real-time. No administrator configuration is required, although UAL can be disabled or enabled. For more information, see [Manage User Access Logging](manage-user-access-logging). The User Access Logging service aggregates client usage data by roles and products into local database files. IT administrators can later use Windows Management Instrumentation (WMI) or Windows PowerShell cmdlets to retrieve quantities and instances by server role (or software product), by user, by device, by the local server, and by date.

Note

UAL supports the [Microsoft Assessment and Planning Toolkit](https://go.microsoft.com/fwlink/?LinkID=111000).

## Practical applications

UAL aggregates unique client device and user request events that are logged into a local database. These records are then made available (through a query by a server administrator) to retrieve quantities and instances by server role, by user, by device, by the local server, and by date. In addition, UAL has been extended to enable non-Microsoft software developers to instrument their UAL events to be aggregated by Windows Server.

UAL can perform the following tasks:

- Quantify client user requests for local physical or virtual servers.
- Quantify client user requests for installed software products on a local physical or virtual server.
- Retrieve data on a local server running Hyper-V to identify periods of high and low demand on a Hyper-V virtual computer.
- Retrieve UAL data from multiple remote servers.

In addition, software developers can instrument UAL events that can then be aggregated and retrieved by using WMI and Windows PowerShell interfaces.

The following server roles and services can be supported by UAL:

- Active Directory Certificate Services (AD CS)
- Active Directory Rights Management Services (AD RMS)
- BranchCache
- Domain Name System (DNS)

    Note

    UAL collects DNS data every 24 hours, and there is a separate UAL cmdlet for this scenario.
- Dynamic Host Configuration Protocol (DHCP)
- Fax Server
- File Services
- File Transfer Protocol (FTP) Server
- Hyper-V

    Note

    UAL collects Hyper-V data every 24 hours, and there is a separate UAL cmdlet for this scenario.
- Web Server (IIS)

    Warning

    To use UAL with IIS, you must use iisual.exe. For more information, see [Analyzing Client Usage Data with IIS User Access Logging](https://www.iis.net/learn/manage/configuring-security/analyzing-client-usage-data-with-iis-user-access-logging).
- Microsoft Message Queue (MSMQ) Services
- Network Policy and Access Services
- Print and Document Services
- Routing and Remote Access Service (RRAS)
- Windows Deployment Services (WDS)
- Windows Server Update Services (WSUS)

Important

UAL is not recommended for use on servers that are connected directly to the Internet, such as web servers on an Internet-accessible address space, or in scenarios where extremely high performance is the primary function of the server (such as in HPC workload environments). UAL is primarily intended for small, medium, and enterprise intranet scenarios where high volume is expected, but not as high as deployments that serve Internet-facing traffic volume on a regular basis.

## Important functionality

The following table describes key functions of UAL and their potential value.

| Functionality | Value |
| --- | --- |
| Collect and aggregate client request event data in near real-time. | Up to three years of data can be saved. **Important:** Administrators need to enforce compliance of the data collected and data retention periods with the organization's privacy policy and local regulations. |
| Query UAL by using WMI or Windows PowerShell interfaces to retrieve client request data on a local or remote server. | UAL enables a single view of ongoing usage data. Server and enterprise administrators can retrieve this data and coordinate with business administrators to optimize use of their volume software licenses. |
| Enabled by default. | Server administrators do not need to configure or otherwise set up this feature for all core functionality to be available and working. |

## Data logged with UAL

The following user-related data is logged with UAL.

| Data | Description |
| --- | --- |
| **UserName** | The user name on the client that accompanies the UAL entries from installed roles and products, if applicable. |
| **ActivityCount** | The number of times a particular user accessed a role or service. |
| **FirstSeen** | The date and time when a user first accesses a role or service. |
| **LastSeen** | The date and time when a user last accessed a role or service. |
| **ProductName** | The name of the software parent product, such as Windows, that is providing UAL data. |
| **RoleGUID** | The UAL assigned or registered GUID that represents the server role or installed product. |
| **RoleName** | The name of the role, component, or subproduct that is providing UAL data. This is also associated with a ProductName and a RoleGUID. |
| **TenantIdentifier** | A unique GUID for a tenant client of an installed role or product that accompanies the UAL data, if applicable. |

The following device-related data is logged with UAL.

| Data | Description |
| --- | --- |
| **IPAddress** | The IP address of a client device that is used to access a role or service. |
| **ActivityCount** | The number of times a particular device accessed the role or service. |
| **FirstSeen** | The date and time when an IP address was first used to access a role or service. |
| **LastSeen** | The date and time when an IP address was last used to access a role or service. |
| **ProductName** | The name of the software parent product, such as Windows, that is providing UAL data. |
| **RoleGUID** | The UAL-assigned or registered GUID that represents the server role or installed product. |
| **RoleName** | The name of the role, component, or subproduct that is providing UAL data. This is also associated with a ProductName and a RoleGUID. |
| **TenantIdentifier** | A unique GUID for a tenant client of an installed role or product that accompanies the UAL data, if applicable. |

## Software requirements

UAL can be used on any computer running versions of Windows Server after Windows Server 2012.

## Additional References

[User Access Logging](/en-us/previous-versions/windows/desktop/ual/user-access-logging) on MSDN. [Manage User Access Logging](manage-user-access-logging)