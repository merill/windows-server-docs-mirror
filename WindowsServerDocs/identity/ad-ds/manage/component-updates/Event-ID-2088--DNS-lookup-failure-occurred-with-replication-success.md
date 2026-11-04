---
layout: Conceptual
title: Event ID 2088 - DNS lookup failure occurred with replication success | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/component-updates/event-id-2088--dns-lookup-failure-occurred-with-replication-success
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: 'Learn more about: Event ID 2088: DNS lookup failure occurred with replication success'
author: robinharwood
ms.author: roharwoo
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: troubleshooting-error-codes
locale: en-us
document_id: 7d3e82a6-3f32-087a-a030-435de5571889
document_version_independent_id: e81eb13d-58e9-60e0-ed04-23f177f87aa7
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/manage/component-updates/Event-ID-2088--DNS-lookup-failure-occurred-with-replication-success.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/manage/component-updates/event-id-2088--dns-lookup-failure-occurred-with-replication-success
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/manage/component-updates/Event-ID-2088--DNS-lookup-failure-occurred-with-replication-success.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
platformId: 90ad9862-b87b-699c-3668-80c478d3130d
---

# Event ID 2088 - DNS lookup failure occurred with replication success | Microsoft Learn

When a destination domain controller running Windows Server 2003 with Service Pack 1 (SP1) receives Event ID 2088 in the Directory Service event log, attempts to resolve the globally unique identifier (GUID) in the alias (CNAME) resource record to an IP address for the source domain controller failed. However, the destination domain controller tried other means to resolve the name and succeeded by using either the fully qualified domain name (FQDN) or the NetBIOS name of the source domain controller. Although replication was successful, the Domain Name System (DNS) problem should be diagnosed and resolved.

The following is an example of the event text:

```
Log Name: Directory Service
Source: Microsoft-Windows-ActiveDirectory_DomainService
Date: 3/15/2008  9:20:11 AM
Event ID: 2088
Task Category: DS RPC Client
Level: Warning
Keywords: Classic
User: ANONYMOUS LOGON
Computer: DC3.contoso.com
Description:
Active Directory could not use DNS to resolve the IP address of the source domain controller listed below. To maintain the consistency of Security groups, group policy, users and computers and their passwords, Active Directory Domain Services successfully replicated using the NetBIOS or fully qualified computer name of the source domain controller.
```

Invalid DNS configuration may be affecting other essential operations on member computers, domain controllers or application servers in this Active Directory Domain Services forest, including logon authentication or access to network resources.

You should immediately resolve this DNS configuration error so that this domain controller can resolve the IP address of the source domain controller using DNS.

Alternate server name: DC1 Failing DNS host name: 4a8717eb-8e58-456c-995a-c92e4add7e8e.\_msdcs.contoso.com

NOTE: By default, only up to 10 DNS failures are shown for any given 12 hour period, even if more than 10 failures occur. To log all individual failure events, set the following diagnostics registry value to 1:

Registry Path: HKLM\System\CurrentControlSet\Services\NTDS\Diagnostics\22 DS RPC Client

User Action:

1. If the source domain controller is no longer functioning or its operating system has been reinstalled with a different computer name or NTDSDSA object GUID, remove the source domain controller's metadata with ntdsutil.exe, using the steps outlined in MSKB article 216498.
2. Confirm that the source domain controller is running Active Directory and is accessible on the network by typing "net view &lt;source DC name&gt;" or "ping &lt;source DC name&gt;".
3. Verify that the source domain controller is using a valid DNS server for DNS services, and that the source domain controller's host record and CNAME record are correctly registered, using `DCDIAG.EXE`. For more information, see [Dcdiag](/en-us/windows-server/administration/windows-commands/dcdiag).

dcdiag /test:dns

1. Verify that this destination domain controller is using a valid DNS server for DNS services, by running the DNS Enhanced version of DCDIAG.EXE command on the console of the destination domain controller, as follows:

dcdiag /test:dns

1. For further analysis of DNS error failures see KB 824449: https://support.microsoft.com/?kbid=824449

```
Additional Data
Error value:
11004 The requested name is valid, but no data of the requested
type was found</code>
  </introduction>
  <section>
    <title>Diagnosis</title>
    <content>
      <para>Failure to resolve the source domain controller name by using the alias (CNAME) resource record in DNS can be due to DNS misconfigurations or delays in DNS data propagation.</para>
    </content>
  </section>
  <section>
    <title>Resolution</title>
    <content>
      <para>Proceed with DNS testing as described in &quot;<link xlink:href="85b1d179-f53e-4f95-b0b8-5b1c096a8076">Event ID 2087: DNS lookup failure caused replication to fail</link>.&quot;</para>
    </content>
  </section>
  <relatedTopics />
</developerConceptualDocument>
>>>>>>> d3d5e1df7545fc05a0fe34e8d31a7bf943b585ae
```