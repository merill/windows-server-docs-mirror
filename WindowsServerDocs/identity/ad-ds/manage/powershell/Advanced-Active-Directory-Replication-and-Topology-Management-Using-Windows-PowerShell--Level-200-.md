---
layout: Conceptual
title: Advanced Active Directory Replication and Topology Management Using Windows PowerShell (Level 200) | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/powershell/advanced-active-directory-replication-and-topology-management-using-windows-powershell--level-200-
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: 'Learn more about: Advanced Active Directory Replication and Topology Management Using Windows PowerShell (Level 200)'
author: robinharwood
ms.author: roharwoo
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: concept-article
ms.custom: sfi-image-nochange
locale: en-us
document_id: b36ee03c-dc9c-7d59-c46c-d2bd7b8c3f3f
document_version_independent_id: 5842894b-5eb9-8fee-1b6e-72c4b87ad5be
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/manage/powershell/Advanced-Active-Directory-Replication-and-Topology-Management-Using-Windows-PowerShell--Level-200-.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/manage/powershell/advanced-active-directory-replication-and-topology-management-using-windows-powershell--level-200-
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/manage/powershell/Advanced-Active-Directory-Replication-and-Topology-Management-Using-Windows-PowerShell--Level-200-.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: a276540e-a16b-960d-19fd-c3324b89a6e2
---

# Advanced Active Directory Replication and Topology Management Using Windows PowerShell (Level 200) | Microsoft Learn

This topic explains the AD DS replication and topology management cmdlets in more detail, and provides additional examples. For an introduction, see [Introduction to Active Directory Replication and Topology Management Using Windows PowerShell (Level 100)](introduction-to-active-directory-replication-and-topology-management-using-windows-powershell--level-100-).

1. [Introduction](advanced-active-directory-replication-and-topology-management-using-windows-powershell--level-200-#BKMK_Intro)
2. [Replication and Metadata](advanced-active-directory-replication-and-topology-management-using-windows-powershell--level-200-#BKMK_Repl)
3. [Get-ADReplicationAttributeMetadata](advanced-active-directory-replication-and-topology-management-using-windows-powershell--level-200-#BKMK_ReplAttrMD)
4. [Get-ADReplicationPartnerMetadata](advanced-active-directory-replication-and-topology-management-using-windows-powershell--level-200-#BKMK_PartnerMD)
5. [Get-ADReplicationFailure](advanced-active-directory-replication-and-topology-management-using-windows-powershell--level-200-#BKMK_ReplFail)
6. [Get-ADReplicationQueueOperation and Get-ADReplicationUpToDatenessVectorTable](advanced-active-directory-replication-and-topology-management-using-windows-powershell--level-200-#BKMK_ReplQueue)
7. [Sync-ADObject](advanced-active-directory-replication-and-topology-management-using-windows-powershell--level-200-#BKMK_Sync)
8. [Topology](advanced-active-directory-replication-and-topology-management-using-windows-powershell--level-200-#BKMK_Topo)

## Introduction

The following table lists replication and topology cmdlets added to the Active Directory Windows PowerShell module:

| Cmdlet | Explanation |
| --- | --- |
| Get-ADReplicationAttributeMetadata | Returns attribute replication metadata for an object |
| Get-ADReplicationConnection | Returns domain controller connection object details |
| Get-ADReplicationFailure | Returns the most replication recent failure for a domain controller |
| Get-ADReplicationPartnerMetadata | Returns replication configuration of a domain controller |
| Get-ADReplicationQueueOperation | Returns the current replication queue backlog |
| Get-ADReplicationSite | Returns site information |
| Get-ADReplicationSiteLink | Returns site link information |
| Get-ADReplicationSiteLinkBridge | Returns site link bridge information |
| Get-ADReplicationSubnet | Returns AD subnet information |
| Get-ADReplicationUpToDatenessVectorTable | Returns the UTD vector for a domain controller |
| Get-ADTrust | Returns information about an inter-domain or inter-forest trust |
| New-ADReplicationSite | Creates a new site |
| New-ADReplicationSiteLink | Creates a new site link |
| New-ADReplicationSiteLinkBridge | Creates a new site link bridge |
| New-ADReplicationSubnet | Creates a new AD subnet |
| Remove-ADReplicationSite | Deletes a site |
| Remove-ADReplicationSiteLink | Deletes a site link |
| Remove-ADReplicationSiteLinkBridge | Deletes a site link bridge |
| Remove-ADReplicationSubnet | Deletes an AD subnet |
| Set-ADReplicationConnection | Modifies a connection |
| Set-ADReplicationSite | Modifies a site |
| Set-ADReplicationSiteLink | Modifies a site link |
| Set-ADReplicationSiteLinkBridge | Modifies a site link bridge |
| Set-ADReplicationSubnet | Modifies an AD subnet |
| Sync-ADObject | Forces replication of a single object |

Most of these cmdlets have their basis in Repadmin.exe. Other cmdlets (not listed) handle features like Dynamic Access Control and Group Managed Service Accounts.

For a complete list of all Active Directory Windows PowerShell cmdlets, run:

```
Get-Command -module ActiveDirectory
```

For a complete list of all Active Directory Windows PowerShell cmdlet arguments, reference the help. For example:

```
Get-Help New-ADReplicationSite
```

Use the `Update-Help` cmdlet to download and install help files

### Replication and Metadata

Repadmin.exe validates the health and consistency of Active Directory replication. Repadmin.exe offers simple data manipulation options - some arguments support CSV outputs, for example - but automation generally required parsing through text file outputs. The Active Directory module for Windows PowerShell is the first attempt at offering an option that allows real control over the returned data; prior to this, you had to create scripts or use third-party tools.

Additionally, the following cmdlets implement a new parameter set of **Target**, **Scope**, and **EnumerationServer**:

- **Get-ADReplicationFailure**
- **Get-ADReplicationPartnerMetadata**
- **Get-ADReplicationUpToDatenessVectorTable**

The **Target** argument accepts a comma-separated list of strings that identify the target servers, sites, domains, or forests specified by the **Scope** argument. An asterisk (\*) is also permissible and means all servers within the specified scope. If no scope is specified, it implies all servers in the current user's forest. The **Scope** argument specifies the latitude of the search. Acceptable values are **Server**, **Site**, **Domain**, and **Forest**. The **EnumerationServer** specifies the server that enumerates the list of domain controllers specified in **Target** and **Scope**. It operates the same as the **Server** argument and requires the specified server run the Active Directory Web Service.

To introduce the cmdlets, here are some sample scenarios showing capabilities impossible to repadmin.exe; armed with these illustrations, the administrative possibilities become obvious. Review the cmdlet help for specific usage requirements.

### Get-ADReplicationAttributeMetadata

This cmdlet is similar to **repadmin.exe /showobjmeta**. It enables you to return replication metadata, such as when an attribute changed, the originating domain controller, the version and USN information, and attribute data. This cmdlet is useful for auditing where and when a change occurred.

Unlike Repadmin, Windows PowerShell gives flexible search and output control. For example, you can output the metadata of the Domain Admins object, ordered as a readable list:

```
Get-ADReplicationAttributeMetadata -object "cn=domain admins,cn=users,dc=corp,dc=contoso,dc=com" -server dc1.corp.contoso.com -showalllinkedvalues | format-list
```

![Screenshot that shows the metadata output of the Domain Admins Object ordered as a readable list.](media/advanced-active-directory-replication-and-topology-management-using-windows-powershell--level-200-/adds_psgetadreplattrmd.png)

Alternatively, you can arrange the data to look like repadmin, in a table:

```
Get-ADReplicationAttributeMetadata -object "cn=domain admins,cn=users,dc=corp,dc=contoso,dc=com" -server dc1.corp.contoso.com -showalllinkedvalues | format-table -wrap
```

![Screenshot that shows the data arranged to look like repadmin in a table.](media/advanced-active-directory-replication-and-topology-management-using-windows-powershell--level-200-/adds_psgetadreplattrmdtable.png)

Alternatively, you can get metadata for an entire class of objects, by pipelining the **Get-Adobject** cmdlet with a filter, such as all groups - then combine that with a specific date. The pipeline is a channel used between multiple cmdlets to pass data. To see all groups modified in some fashion on January 13th, 2012:

```
Get-ADObject -filter 'objectclass -eq "group"' | Get-ADReplicationAttributeMetadata -server dc1.corp.contoso.com | where-object {$_.lastoriginatingchangetime -like "*1/13/2012*" -and $_.attributename -eq "name"} | format-table object
```

![Screenshot that shows how to see all groups modified in some fashion on January 13th, 2012.](media/advanced-active-directory-replication-and-topology-management-using-windows-powershell--level-200-/adds_psgetadreplattrmdclass.png)

For more information about more Windows PowerShell operations with pipelines, see [Piping and the Pipeline in Windows PowerShell](/en-us/previous-versions/windows/it-pro/windows-powershell-1.0/ee176927%28v=technet.10%29).

Alternatively, to find out every group that has Tony Wang as a member and when the group was last modified:

```
Get-ADObject -filter 'objectclass -eq "group"' | Get-ADReplicationAttributeMetadata -server dc1.corp.contoso.com -showalllinkedvalues | where-object {$_.attributevalue -like "*tony wang*"} | format-table object,LastOriginatingChangeTime,version -auto

```

![Screenshot that shows how to find out every group that has Tony Wang as a member and when the group was last modified.](media/advanced-active-directory-replication-and-topology-management-using-windows-powershell--level-200-/adds_psgetadreplattrmdfilter.png)

Alternatively, to find all objects authoritatively restored using a system state backup in the domain, based on their artificially high version:

```
Get-ADObject -filter 'objectclass -like "*"' | Get-ADReplicationAttributeMetadata -server dc1.corp.contoso.com | where-object {$_.version -gt "100000" -and $_.attributename -eq "name"} | format-table object,LastOriginatingChangeTime
```

![Screenshot that shows how to find all objects authoritatively restored using a system state backup in the domain, based on their artificially high version.](media/advanced-active-directory-replication-and-topology-management-using-windows-powershell--level-200-/adds_psgetadreplattrmdfilter2.png)

Alternatively, send all user metadata to a CSV file for later examination in Microsoft Excel:

```
Get-ADObject -filter 'objectclass -eq "user"' | Get-ADReplicationAttributeMetadata -server dc1.corp.contoso.com -showalllinkedvalues | export-csv allgroupmetadata.csv
```

### Get-ADReplicationPartnerMetadata

This cmdlet returns information about the configuration and state of replication for a domain controller, allowing you to monitor, inventory, or troubleshoot. Unlike Repadmin.exe, using Windows PowerShell means you see only the data that is important to you, in the format you want.

For example, the readable replication state of a single domain controller:

```
Get-ADReplicationPartnerMetadata -target dc1.corp.contoso.com
```

![Screenshot that shows how to get the readable replication state of a single domain controller.](media/advanced-active-directory-replication-and-topology-management-using-windows-powershell--level-200-/adds_psgetadreplpartnermd.png)

Alternatively, the last time a domain controller replicated inbound and its partners, in a table format:

```
Get-ADReplicationPartnerMetadata -target dc1.corp.contoso.com | format-table lastreplicationattempt,lastreplicationresult,partner -auto
```

![Screenshot that shows the last time a domain controller replicated inbound and its partners, in a table format.](media/advanced-active-directory-replication-and-topology-management-using-windows-powershell--level-200-/adds_psgetadreplpartnermdtable.png)

Alternatively, contact all domain controllers in the forest and display any whose last attempted replication failed for any reason:

```
Get-ADReplicationPartnerMetadata -target * -scope server | where {$_.lastreplicationresult -ne "0"} | ft server,lastreplicationattempt,lastreplicationresult,partner -auto
```

![Screenshot that shows how to contact all domain controllers in the forest and display any whose last attempted replication failed for any reason.](media/advanced-active-directory-replication-and-topology-management-using-windows-powershell--level-200-/adds_psgetadreplpartnermdfail.png)

### Get-ADReplicationFailure

This cmdlet can be used to returns information about recent errors in replication. It is analogous to **Repadmin.exe /showreplsum**, but again, with much more control thanks to Windows PowerShell.

For example, you can return a domain controller's most recent failures and the partners it failed contacting:

```
Get-ADReplicationFailure dc1.corp.contoso.com
```

![Screenshot that shows how you can return a domain controller's most recent failures and the partners he failed contacting.](media/advanced-active-directory-replication-and-topology-management-using-windows-powershell--level-200-/adds_psgetadreplfail.png)

Alternatively, return a table view for all servers in a specific AD logical site, ordered for easier viewing and containing only the most critical data:

```
Get-ADReplicationFailure -scope site -target default-first-site-name | format-table server,firstfailuretime,failurecount,lasterror,partner -auto
```

![Screenshot that shows how to return a table view for all servers in a specific AD logical site, ordered for easier viewing and containing only the most critical data.](media/advanced-active-directory-replication-and-topology-management-using-windows-powershell--level-200-/adds_psgetadreplfailscoped.png)

### Get-ADReplicationQueueOperation and Get-ADReplicationUpToDatenessVectorTable

Both of these cmdlets return further aspects of domain controller and whether it's up to date, which includes pending replication and version vector information.

### Sync-ADObject

This cmdlet is analogous to running **Repadmin.exe /replsingleobject**. It is very useful when you make changes that require out of band replication, especially to fix an issue.

For example, if someone deleted the CEO's user account and then restored it with the Active Directory Recycle Bin, you probably want it replicated to all domain controllers immediately. You also probably want to do this without forcing replication of all the other object changes made; after all, that is why you have a replication schedule - to avoid overloading WAN links.

```
Get-ADDomainController -filter * | foreach {Sync-ADObject -object "cn=tony wang,cn=users,dc=corp,dc=contoso,dc=com" -source dc1 -destination $_.hostname}
```

![Screenshot that shows how to replicate a deleted account from the Active Directory Recycle Bin to all domain controllers without forcing replication of all the other object changes made.](media/advanced-active-directory-replication-and-topology-management-using-windows-powershell--level-200-/adds_pssyncad.png)

### Topology

While Repadmin.exe is good at returning information about replication topology like sites, site links, site link bridges, and connections, it does not have a comprehensive set of arguments to make changes. In fact, there has never been scriptable, in-box Windows utility designed specifically for administrators to create and modify AD DS topology. As Active Directory has matured in millions of customer environments, the need to bulk modify Active Directory logical information becomes apparent.

For example, after a rapid expansion of new branch offices, combined with the consolidation of others, you might have a hundred site changes to make based on physical locations, network changes, and new capacity requirements. Rather than using Dssites.msc and Adsiedit.msc to make changes, you can automate. This is especially compelling when you start with a spreadsheet of data provided by your network and facilities teams.

The **Get-Adreplication\**\* cmdlets return information about replication topology and are useful for pipelining into the **Set-Adreplication\**\* cmdlets in bulk. **Get** cmdlets do not change data, they only show data or to create Windows PowerShell session objects that can be pipelined to **Set-Adreplication\**\* cmdlets. The **New** and **Remove** cmdlets are useful for creating or removing Active Directory topology objects.

For example, you can create new sites using a CSV file:

```
Import-Csv -path C:\newsites.csv | new-adreplicationsite
```

![Screenshot that shows the Notepad interface.](media/advanced-active-directory-replication-and-topology-management-using-windows-powershell--level-200-/adds_psnewsitescsv.png)

![Screenshot that shows how to create new sites using a CSV file.](media/advanced-active-directory-replication-and-topology-management-using-windows-powershell--level-200-/adds_psimportcsv.png)

Alternatively, create a new site link between two existing sites with a custom replication interval and site cost:

```
New-ADReplicationSiteLink -name "chicago<-->waukegan" -sitesincluded chicago,waukegan -cost 50 -replicationfrequencyinminutes 15
```

![Screenshot that shows create a new site link between two existing sites with a custom replication interval and site cost.](media/advanced-active-directory-replication-and-topology-management-using-windows-powershell--level-200-/adds_psnewadreplsite.png)

Alternatively, find every site in the forest and replace their **Options** attributes with the flag to enable inter-site change notification, in order to replicate at maximum speed with compression:

```
Get-ADReplicationSiteLink -filter * | set-adobject -replace @{options=$($_.options -bor 1)}
```

![advanced management with powershell](media/advanced-active-directory-replication-and-topology-management-using-windows-powershell--level-200-/adds_psnewadreplsitelink.gif)

Important

Set **-bor 5** to disable compression on those site links as well.

Alternatively, find all sites missing subnet assignments, in order to reconcile the list with the actual subnets of those locations:

```
Get-ADReplicationSite -filter * -property subnets | where-object {!$_.subnets -eq "*"} | format-table name
```

![Screenshot that shows how to find all sites missing subnet assignments, in order to reconcile the list with the actual subnets of those locations.](media/advanced-active-directory-replication-and-topology-management-using-windows-powershell--level-200-/adds_psnewadreplsitefiltrer.png)