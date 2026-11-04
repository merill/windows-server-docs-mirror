---
layout: Conceptual
title: Configure DNSSEC rules using the Name Resolution Policy Table in Windows | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/dns/name-resolution-policy-table
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Configure the Name Resolution Policy Table (NRPT) in Windows Server and Windows client for DNSSEC deployment. Learn to enforce DNS security policies using Group Policy or PowerShell commands.
author: Orin-Thomas
ms.author: roharwoo
ms.topic: how-to
ms.date: 2025-08-01T00:00:00.0000000Z
ai-usage: ai-assisted
ms.custom:
- template-how-to, team=cloud_advocates
- ai-gen-docs-bap
- ai-gen-description
- ai-seo-date:07/07/2025
locale: en-us
document_id: b1632ef9-0b08-7b88-75b8-0f34721636d1
document_version_independent_id: b1632ef9-0b08-7b88-75b8-0f34721636d1
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/dns/name-resolution-policy-table.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/dns/name-resolution-policy-table
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/dns/name-resolution-policy-table.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 2da1d692-79bc-b0f8-9a3d-a432df5cbf24
---

# Configure DNSSEC rules using the Name Resolution Policy Table in Windows | Microsoft Learn

This article explains how to configure the Name Resolution Policy Table (NRPT) in Windows Server to enforce DNS security policies for specific namespaces. The NRPT enables system administrators to implement DNSSEC validation requirements, ensuring secure name resolution for critical domains in your organization.

The Name Resolution Policy Table (NRPT) in Windows Server enables you to enforce name resolution policies on security-aware DNS clients. You can create NRPT rules to require DNSSEC validation for specific namespaces, which is essential for securing DNS queries and responses. In this article, learn how to configure the NRPT using Group Policy or Windows PowerShell. The NRPT can be used to create different types of rules by choosing one of four available tabs. This article only discusses DNSSEC rules.

## NRPT namespaces

When the DNS Client service performs DNS name resolution, it checks the NRPT before it sends a DNS query. If a DNS query matches an entry in the NRPT, the service processes it according to settings in the policy. Queries that don't match an NRPT entry are processed normally. You can use the NRPT to enforce DNSSEC validation. This validation applies to DNS responses for queries. You can specify the namespaces where these rules apply.

The following table shows the options that you can use to configure the namespace to which a policy applies.

| Option | Usage |
| --- | --- |
| **Suffix** | The policy applies to any name that ends in `.contoso.com` and includes child domains. |
| **Prefix** | The policy applies only to a host name. This policy is triggered only if the host name portion of a DNS query matches the flat name configured in the rule. For example, if the rule specifies `server1`, it applies to queries like `server1.contoso.com` and `server1.nwtraders.com`. |
| **FQDN** | The policy applies only to the specified host. This fully qualified domain name (FQDN) isn't the FQDN of a domain, but an FQDN of a host computer. |
| **Subnet (IPv4)** | This option configures a policy, which applies to reverse IPv4 lookup queries. |
| **Subnet (IPv6)** | This option configures a policy, which applies to reverse IPv6 lookup queries. |
| **Any** | This option configures the default policy. |

## NRPT rule processing

NRPT rules can be configured in a local, site, domain, or organizational unit (OU)-linked Group Policy Object (GPO). Normal Group Policy processing rules apply. Beginning with the local GPO, site-linked GPOs, domain-linked GPOs, and finally organizational unit-linked GPOs. An example of the processing order is shown in the following diagram.

![Diagram that shows the processing order of NRPT rules in Group Policy, including local, site-linked, domain-linked, and organizational unit-linked GPOs.](../media/name-resolution-policy-table/processing-order.png)

If NRPT rules are present in multiple GPOs that apply to the same user or computer, the rules are merged, with more discrete rules taking precedence over more general rules. For example, a rule that applies to a child namespace takes precedence over a rule for the parent namespace, as shown in the following table.

| GPO name | Namespace | DNSSEC-enabled | Validation required |
| --- | --- | --- | --- |
| Default domain policy | `contoso.com` | ✅ | ❌ |
| NRPT\_settings | `secure.contoso.com` | ✅ | ✅ |

In this example, DNSSEC validation is required for DNS queries that have a suffix of `secure.contoso.com`, for example, `www.secure.contoso.com`. The validation includes queries in a child domain, for example, `www.corp.secure.contoso.com`. However, validation isn't required for `*.contoso.com` or `*.corp.contoso.com`. Therefore, if parent and child domains require a different name resolution policy, you must explicitly create policies for the child namespace.

Warning

NRPT rules don't overwrite each other. If two rules are created in two different GPOs that apply to the same namespace for the same user or computer, a conflict occurs. As a result, neither rule is applied. If the rules apply to the same user or computer for different namespaces, they're merged. This rule doesn't apply to local Group Policy, however. If any NRPT settings are configured in domain Group Policy, then all local Group Policy NRPT settings are ignored.

The NRPT can be configured to require or not require validation for specific segments of your namespace. For example, you might use a conditional forwarder to disable DNSSEC validation. Using this design, you can implement a conditional forwarder that directs client computers to an external, unsigned domain for a specific namespace, such as an FQDN. If the forwarded name is within a signed namespace in your organization, validation might be required unless you specifically disable it for that FQDN.

For example, you might have a signed internal domain, `contoso.com`, and you also have an external website `www.contoso.com` that isn't signed. In this scenario, the internal and external domains use different authoritative servers. A conditional forwarder is used to resolve the name `www.contoso.com`. The NRPT can be configured as follows to ensure client computers are able to reach the external website without requiring DNSSEC validation:

| Name | Conditional forwarder | DNSSEC-enabled | Validation required |
| --- | --- | --- | --- |
| `contoso.com` | none | ✅ | ✅ |
| `www.contoso.com` | `10.10.10.10` | ❌ | ❌ |

In this example, other names within the `contoso.com` namespace, such as `finance.contoso.com`, still require validation because they don't match the NRPT FQDN rule for `www.contoso.com`.

## Filter NRPT policy

By default, new domain-linked Group Policy Objects (GPOs) apply to the Authenticated Users group. You can apply NRPT policy to selected groups, users, and computers by removing the Authenticated Users group from **Security Filtering** and then adding a custom user, group, or computer.

## Prerequisites

To configure the NRPT, you need to have the following prerequisites.

- Membership in the **Administrators** group, or equivalent, is the minimum required to complete these procedures.
- You must have the Group Policy Management console feature installed the computer where you want to configure the NRPT using Group Policy.
- You must have rights to create or edit an existing Group Policy Object (GPO) in the domain where you want to configure the NRPT.

## Configure the NRPT

Use the following procedures to configure the Name Resolution Policy Table (NRPT). The examples that are provided demonstrate how to add a rule in an existing Group Policy Object (GPO) that requires DNSSEC validation for a namespace (zone).

You can configure the NRPT using either the Group Policy Management Console or Windows PowerShell. Select the method that best suits your environment and administrative preferences.

# [Group Policy Management Console](#tab/gpmc)
To configure the NRPT rules using the Group Policy Management Console (GPMC), follow these steps.

1. Sign in to a computer with the Group Policy Management feature installed.
2. Open the **Group Policy Management** console by selecting **Tools** on the Server Manager menu, and then selecting **Group Policy Management**.
3. Navigate to the Group Policy Object (GPO) that you want to configure in the Group Policy Management Console tree. Right-click the GPO, and then select **Edit**.
4. In the Group Policy Management Editor tree, navigate to **Computer Configuration &gt; Policies &gt; Windows Settings &gt; Name Resolution Policy**.
5. To create a new rule, under **Create Rules**, select the part of the namespace to which the rule applies from the drop-down list. For example, choose **Suffix** to create a rule that applies to all names that end in the text that you provide.
6. Select the type of namespace from the drop-down list and enter the namespace to which the rule applies. For example, to apply a rule to all devices in the `secure.contoso.com` DNS namespace, choose **Suffix** and type `secure.contoso.com`.
7. Enable DNSSEC validation by selecting the **Enable DNSSEC in this rule** check box, and then select the **Require DNS clients to check that name and address data has been validated by the DNS server** check box.
8. Select **Create** at the bottom of this section of the NRPT to create the rule.
9. Scroll down to view the configured rules in the **Name Resolution Policy Table** section, and verify that the new rule is displayed.

# [Windows PowerShell](#tab/powershell)
To configure the NRPT rules using Windows PowerShell, you can use the `Add-DnsClientNrptRule` cmdlet. This cmdlet allows you to add a DNSSEC rule to an existing Group Policy Object (GPO).

1. Open a PowerShell session with administrative privileges.
2. Create a new NRPT rule by using the `Add-DnsClientNrptRule` cmdlet. You need to specify the GPO name, namespace, and DNSSEC validation settings. The following example demonstrates how to add a rule that requires DNSSEC validation. Replace `<GpoName>` with the name of your GPO and `<NameSpace>` with the namespace you want to configure.

```powershell
Add-DnsClientNrptRule -GpoName <GpoName> -NameSpace <NameSpace> -DnsSecEnable -DnsSecValidationRequired
```

1. To validate that the NRPT rule was successfully configured, you can use the `Get-DnsClientNrptRule` cmdlet. This cmdlet retrieves the NRPT rules for a specified GPO. The following example shows how to check the NRPT settings for a specific GPO.

```powershell
Get-DnsClientNrptRule -GpoName <GpoName>
```

---

## View the current NRPT policy

You can use the [Get-DnsClientNrptPolicy](/en-us/powershell/module/dnsclient/get-dnsclientnrptpolicy) cmdlet to view NRPT policies. See the following example.

```
PS C:\> Get-DnsClientNrptPolicy -Effective

Namespace                        : .contoso.com
QueryPolicy                      : QueryIPv6Only
SecureNameQueryFallback          : FallbackPrivate
DirectAccessIPsecCARestriction   :
DirectAccessProxyName            :
DirectAccessDnsServers           :
DirectAccessEnabled              : False
DirectAccessProxyType            :
DirectAccessQueryIPsecEncryption :
DirectAccessQueryIPsecRequired   :
NameServers                      :
DnsSecIPsecCARestriction         :
DnsSecQueryIPsecEncryption       :
DnsSecQueryIPsecRequired         : False
DnsSecValidationRequired         : False
NameEncoding                     :

Namespace                        : .secure.contoso.com
QueryPolicy                      : QueryIPv6Only
SecureNameQueryFallback          : FallbackPrivate
DirectAccessIPsecCARestriction   :
DirectAccessProxyName            :
DirectAccessDnsServers           :
DirectAccessEnabled              : False
DirectAccessProxyType            :
DirectAccessQueryIPsecEncryption :
DirectAccessQueryIPsecRequired   :
NameServers                      :
DnsSecIPsecCARestriction         :
DnsSecQueryIPsecEncryption       :
DnsSecQueryIPsecRequired         : False
DnsSecValidationRequired         : True
NameEncoding                     :
```

The **Get-DnsClientNrptPolicy** cmdlet gets policy that applies to the local computer. In this example, the output indicates that DNSSEC validation is required for `*.secure.contoso.com`, and isn't required for `*.contoso.com`.