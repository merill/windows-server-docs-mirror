---
layout: Conceptual
title: Disjoint Namespace | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/disjoint-namespace
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: 'Learn more about: Disjoint Namespace'
author: robinharwood
ms.author: roharwoo
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: d46dcfac-1ec1-7fe4-52fa-fd405a30715d
document_version_independent_id: 1d71eb75-8f33-07c3-3543-c65d8289f4d5
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/plan/Disjoint-Namespace.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/plan/disjoint-namespace
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/plan/Disjoint-Namespace.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
platformId: b697f8ca-bf1b-7bac-8567-0bb3f348765f
---

# Disjoint Namespace | Microsoft Learn

A disjoint namespace occurs when one or more domain member computers have a primary Domain Name Service (DNS) suffix that does not match the DNS name of the Active Directory domain of which the computers are members. For example, a member computer that uses a primary DNS suffix of corp.fabrikam.com in an Active Directory domain named na.corp.fabrikam.com is using a disjoint namespace.

A disjoint namespace is more complex to administer, maintain, and troubleshoot than a contiguous namespace. In a contiguous namespace, the primary DNS suffix matches the Active Directory domain name. Network applications that are written to assume that the Active Directory namespace is identical to the primary DNS suffix for all domain member computers do not function properly in a disjoint namespace.

## Support for disjoint namespaces

Domain member computers, including domain controllers, can function in a disjoint namespace. Domain member computers can register their host (A) resource record and IP version 6 (IPv6) host (AAAA) resource record in a disjoint DNS namespace. When domain member computers register their resource records in this way, domain controllers continue to register global and site-specific service (SRV) resource records in the DNS zone that is identical to the Active Directory domain name.

For example, assume that a domain controller for the Active Directory domain named na.corp.fabrikam.com that uses a primary DNS suffix of corp.fabrikam.com registers host (A) and IPv6 host (AAAA) resource records in the corp.fabrikam.com DNS zone. The domain controller continues to register global and site-specific service (SRV) resource records in the \_msdcs.na.corp.fabrikam.com and na.corp.fabrikam.com DNS zones, which makes service location possible.

Important

Although Windows operating systems may support a disjoint namespace, applications that are written to assume that the primary DNS suffix is the same as the Active Directory domain suffix may not function in such an environment. For this reason, you should test all applications and their respective operating systems carefully before you deploy a disjoint namespace.

A disjoint namespace should work (and is supported) in the following situations:

- When a forest with multiple Active Directory domains uses a single DNS namespace, which is also known as a DNS zone

    An example of this is a company that uses regional domains with names such as na.corp.fabrikam.com, sa.corp.fabrikam.com, and asia.corp.fabrikam.com and uses a single DNS namespace, such as corp.fabrikam.com.
- When a single Active Directory domain is split into separate DNS namespaces

    An example of this is a company with an Active Directory domain of corp.contoso.com that uses DNS zones such as hr.corp.contoso.com, production.corp.contoso.com, and it.corp.contoso.com.

A disjoint namespace does not work properly (and is not supported) in the following situations:

- A disjoint suffix used by domain members matches an Active Directory domain name in this or another forest. This breaks Kerberos name-suffix routing.
- The same disjoint suffix is used in another forest. This prevents routing these suffixes uniquely between forests.
- When a domain member certification authority (CA) server changes its fully qualified domain name (FQDN) so that it no longer use the same primary DNS suffix that is used by the domain controllers of the domain to which the CA server is a member. In this case, you may have problems validating certificates the CA server issued, depending on what DNS names are used in the CRL Distribution Points. But if you place a CA server in a stable disjoint namespace, it works properly and is supported.

## Considerations for disjoint namespaces

The following considerations may help you decide if you should use a disjoint namespace.

### Application compatibility

As previously mentioned, a disjoint namespace can cause problems for any applications and services that are written to assume that a computer primary DNS suffix is identical to the name of the domain name of which it is a member. Before you deploy a disjoint namespace, you must check applications for compatibility issues. Also, be sure to check the compatibility of all applications that you use when you perform your analysis. This includes applications from Microsoft and from other software developers.

### Advantages of disjoint namespaces

Using a disjoint namespace can have the following advantages:

- Because the primary DNS suffix of a computer can indicate different information, you can manage the DNS namespace separately from the Active Directory domain name.
- You can separate the DNS namespace based on business structure or geographical location. For example, you can separate the namespace based on business unit names or physical location such as continent, country/region, or building.

### Disadvantages of disjoint namespaces

Using a disjoint namespace can have the following disadvantages:

- You must create and manage separate DNS zones for each Active Directory domain in the forest that has member computers that use a disjoint namespace. (That is, it requires an additional and more complex configuration.)
- You must perform manual steps to modify and manage the Active Directory attribute that allows domain members to use specified, primary DNS suffixes.
- To optimize name resolution, you must perform manual steps to modify and maintain Group Policy to configure member computers with alternate primary DNS suffixes.

Note

The Windows Internet Name Service (WINS) could be used to offset this disadvantage by resolving single-label names. For more information about WINS, see the [WINS Technical Reference](/en-us/previous-versions/windows/it-pro/windows-server-2003/cc736411%28v=ws.10%29).

- When your environment requires multiple primary DNS suffixes, you must configure the DNS suffix search order for all of the Active Directory domains in the forest appropriately.

    To set the DNS suffix search order, you can use Group Policy objects or Dynamic Host Configuration Protocol (DHCP) Server service parameters. You can also modify the registry.
- You must carefully test all applications for compatibility issues.

For more information about steps that you can take to address these disadvantages, see [Create a Disjoint Namespace](/en-us/previous-versions/windows/it-pro/windows-server-2003/cc755926%28v=ws.10%29).

### Planning a namespace transition

Before you modify a namespace, review the following considerations, which apply to transitions from contiguous namespaces to disjoint namespaces (or the reverse):

- Manually configured Service Principal Names (SPNs) may no longer match DNS names after a namespace change. This can cause authentication failures.

    For more information, see [Service Logons Fail Due to Incorrectly Set SPNs](/en-us/previous-versions/windows/it-pro/windows-server-2003/cc772897%28v=ws.10%29).

    - If you use Windows Server 2003-based computers with constrained delegation, those computers may require you to manually edit the **msDS-AllowedToDelegateTo** attribute in Active Directory. For more information, see the [ms-DS-Allowed-To-Delegate-To attribute](/en-us/windows/win32/adschema/a-msds-allowedtodelegateto).
    - If you want to delegate permissions to modify SPNs to subordinate administrators, see [Delegating Authority to Modify SPNs](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc770439%28v=ws.10%29).
- If you use Lightweight Directory Access Protocol (LDAP) over Secure Sockets Layer (SSL) (known as LDAPS) with a CA in a deployment that has domain controllers that are configured in a disjoint namespace, you must use the appropriate Active Directory domain name and primary DNS suffix when you configure the LDAPS certificates.

    For more information about domain controller certificate requirements, see article 321051 in the Microsoft Knowledge Base, [How to enable LDAP over SSL with a third-party certification authority](https://support.microsoft.com/help/321051/).

    Note

    Domain controllers that use certificates for LDAPS may require you to redeploy their certificates. When you do so, domain controllers may not select an appropriate certificate until they are restarted. For more information about Lightweight Directory Access Protocol (LDAP) over Secure Sockets Layer (SSL) (LDAPS) authentication for Windows Server 2003, see article 938703 in the Microsoft Knowledge Base, [How to troubleshoot LDAP over SSL connection problems](https://support.microsoft.com/help/938703/).

### Planning for disjoint namespace deployments

Take the following precautions if you deploy computers in an environment that has a disjoint namespace:

1. Notify all software vendors with whom you do business that they must test and support a disjoint namespace. Ask them to verify that they support their applications in environments that use disjoint namespaces.
2. Test all versions of operating systems and applications in disjoint namespace lab environments. When you do, follow these recommendations:

    1. Resolve all software issues before you deploy the software into your environment.
    2. When possible, participate in beta tests of operating systems and applications that you plan to deploy in disjoint namespaces.
3. Ensure that administrators and helpdesk staff are aware of the disjoint namespace and its impact.
4. Create a plan that makes it possible for you to transition from a disjoint namespace to a contiguous namespace, if necessary.
5. Evangelize the importance of disjoint namespace support with operating system and application providers.