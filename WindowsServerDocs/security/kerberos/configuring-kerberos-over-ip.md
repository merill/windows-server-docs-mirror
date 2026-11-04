---
layout: Conceptual
title: Configuring Kerberos for IP Address | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/security/kerberos/configuring-kerberos-over-ip
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: Kerberos support for IP-based SPNs
author: robinharwood
ms.author: roharwoo
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 5f88ac1e-b08d-affc-2931-130fb7fc0148
document_version_independent_id: 94062cd7-5db7-ae28-8bb8-dad7c2cff953
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/security/kerberos/configuring-kerberos-over-ip.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: security/kerberos/configuring-kerberos-over-ip
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/security/kerberos/configuring-kerberos-over-ip.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/e0ffb20c-01c6-407b-a9bd-29111652a1dc
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/3904bce4-d817-48cf-85fd-b6146fca83b7
platformId: 62dfd37f-7afe-1856-a0a2-f00ac7693cda
---

# Configuring Kerberos for IP Address | Microsoft Learn

Beginning with Windows 10 version 1507 and Windows Server 2016, Kerberos clients can be configured to support IPv4 and IPv6 hostnames in SPNs.

By default Windows will not attempt Kerberos authentication for a host if the hostname is an IP address. It will fall back to other enabled authentication protocols like NTLM. However, applications are sometimes hardcoded to use IP addresses which means the application will fall back to NTLM and not use Kerberos. This can cause compatibility issues as environments move to disable NTLM.

To reduce the impact of disabling NTLM a new capability was introduced that lets administrators use IP addresses as hostnames in Service Principal Names. This capability is enabled on the client through a registry key value.

```cmd
reg add "HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System\Kerberos\Parameters" /v TryIPSPN /t REG_DWORD /d 1 /f
```

To configure support for IP address hostnames in SPNs, create a TryIPSPN entry. This entry does not exist in the registry by default. After you have created the entry, change the DWORD value to 1. This registry value will need to be set on each client machine that needs to access Kerberos-protected resources by IP address.

## Configuring a Service Principal Name as IP Address

A Service Principal Name is a unique identifier used during Kerberos authentication to identify a service on the network. An SPN is composed of a service, hostname, and optionally a port in form of `service/hostname[:port]` such as `host/fs.contoso.com`. Windows will register multiple SPNs to a computer object when a machine is joined to Active Directory.

IP addresses are not normally used in place of hostnames because IP addresses are often temporary. This can lead to conflicts and authentication failures as address leases expire and renew. Therefore registering an IP address-based SPN is a manual process and should only be used when it's impossible to switch to a DNS-based hostname.

The recommended approach is to use the [Setspn.exe](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/cc731241%28v=ws.11%29) tool. Note that an SPN can only be registered to a single account in Active Directory at a time so it is recommended that IP addresses have static leases if DHCP is used.

```
Setspn -s <service>/ip.address> <domain-user-account>
```

Example:

```
Setspn -s host/192.168.1.1 server01
```