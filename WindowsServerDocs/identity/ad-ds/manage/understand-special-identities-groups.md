---
layout: Conceptual
title: Special Identity Groups | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/understand-special-identities-groups
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: Learn about Windows Server special identity groups that are used for Windows access control.
author: robinharwood
ms.author: roharwoo
ms.topic: concept-article
ms.date: 2025-07-08T00:00:00.0000000Z
locale: en-us
document_id: 7309b02e-02fa-7cb7-1a4e-0ba3ef8cd0f9
document_version_independent_id: 7309b02e-02fa-7cb7-1a4e-0ba3ef8cd0f9
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/manage/understand-special-identities-groups.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/manage/understand-special-identities-groups
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/manage/understand-special-identities-groups.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: f3c36244-72b2-de15-a2eb-17e762498777
---

# Special Identity Groups | Microsoft Learn

Learn about Windows Server special identity groups (sometimes called *security groups*) that are used for Windows access control.

## What is a special identity group?

Special identity groups are similar to the Active Directory security groups that are listed in the Active Directory Users and BuiltIn containers. Special identity groups can provide an efficient way to assign access to resources in your network. By using special identity groups, you can:

- Assign user rights to security groups in Active Directory.
- Assign permissions to security groups to access resources.

## How special identity groups work in Windows Server

If a server is running one of the versions of the Windows Server operating system shown in **Applies to** at the beginning of this article, the server has several special identity groups. These special identity groups don't have specific memberships that you can modify, but they can represent different users at different times, depending on the circumstances.

Although you can assign rights and permissions for specific resources to a special identity group, you can't view or modify the membership of a special identity group. Group scopes don't apply to special identity groups. Users are automatically assigned to special identity groups when they sign in or access a specific resource.

For information about Active Directory security groups and group scopes, see [Active Directory security groups](understand-security-groups).

## Default special identity groups

The following sections describe the default special identity groups in Windows Server.

- Anonymous Logon
- Attested key property
- Authenticated Users
- Authentication authority asserted identity
- Batch
- Console logon
- Creator Group
- Creator Owner
- Dialup
- Digest Authentication
- Enterprise Domain Controllers
- Enterprise Read-only Domain Controllers
- Everyone
- Fresh Public Key identity
- Interactive
- IUSR
- Key trust
- Local Service
- LocalSystem
- MFA key property
- Network
- Network Service
- NTLM Authentication
- Other Organization
- Owner Rights
- Principal Self
- Proxy
- Read-only Domain Controllers
- Remote Interactive Logon
- Restricted
- SChannel Authentication
- Service
- Service asserted identity
- Terminal Server User
- This Organization
- Window Manager\Window Manager Group

### Anonymous Logon

Any user who accesses the system through an anonymous logon has the Anonymous Logon identity. This identity allows anonymous access to resources, like to a webpage that's published on a corporate server. The Anonymous Logon group isn't a member of the Everyone group by default.

| Attribute | Value |
| --- | --- |
| Well-known SID/RID | S-1-5-7 |
| Object class | Foreign Security Principal |
| Default location in Active Directory | CN=WellKnown Security Principals, CN=Configuration, DC=&lt;forestRootDomain&gt; |
| Default user rights | None |

### Attested key property

A security identifier (SID) that means the key trust object had the attestation property.

| Attribute | Value |
| --- | --- |
| Well-known SID/RID | S-1-18-6 |
| Object class | Foreign Security Principal |
| Default location in Active Directory | CN=WellKnown Security Principals, CN=Configuration, DC=&lt;forestRootDomain&gt; |
| Default user rights | None |

### Authenticated Users

Any user who accesses the system through a sign-in process has the Authenticated Users identity. This identity allows access to shared resources within the domain, such as files in a shared folder that should be accessible to all the employees in the organization. Membership is controlled by the operating system.

| Attribute | Value |
| --- | --- |
| Well-known SID/RID | S-1-5-11 |
| Object class | Foreign Security Principal |
| Default location in Active Directory | CN=WellKnown Security Principals, CN=Configuration, DC=&lt;forestRootDomain&gt; |
| Default user rights | [Access this computer from the network](/en-us/windows/device-security/security-policy-settings/access-this-computer-from-the-network): SeNetworkLogonRight<br>[Add workstations to domain](/en-us/windows/device-security/security-policy-settings/add-workstations-to-domain): SeMachineAccountPrivilege<br><br>[Bypass traverse checking](/en-us/windows/device-security/security-policy-settings/bypass-traverse-checking): SeChangeNotifyPrivilege |

### Authentication authority asserted identity

An SID that means the client's identity is asserted by an authentication authority based on proof of possession of client credentials.

| Attribute | Value |
| --- | --- |
| Well-known SID/RID | S-1-18-1 |
| Object class | Foreign Security Principal |
| Default location in Active Directory | CN=WellKnown Security Principals, CN=Configuration, DC=&lt;forestRootDomain&gt; |
| Default user rights | None |

### Batch

Any user or process that accesses the system as a batch job or through the batch queue has the Batch identity. This identity allows batch jobs to run scheduled tasks, such as a nightly cleanup job that deletes temporary files. Membership is controlled by the operating system.

| Attribute | Value |
| --- | --- |
| Well-known SID/RID | S-1-5-3 |
| Object class | Foreign Security Principal |
| Default location in Active Directory | CN=WellKnown Security Principals, CN=Configuration, DC=&lt;forestRootDomain&gt; |
| Default user rights | None |

### Console logon

A group that includes users who are logged on to the physical console. This SID can be used to implement security policies that grant different rights based on whether a user has been granted physical access to the console.

| Attribute | Value |
| --- | --- |
| Well-known SID/RID | S-1-2-1 |
| Object class | Foreign Security Principal |
| Default location in Active Directory | CN=WellKnown Security Principals, CN=Configuration, DC=&lt;forestRootDomain&gt; |
| Default user rights | None |

### Creator Group

The person who created a file or directory is a member of this special identity group. The Windows Server operating system uses this identity to automatically grant access permissions to the creator of a file or directory.

A placeholder SID is created in an inheritable access control entry (ACE). When the ACE is inherited, the system replaces this SID with the SID for the primary group of the object’s current owner. The primary group is used only by the POSIX subsystem.

| Attribute | Value |
| --- | --- |
| Well-known SID/RID | S-1-3-1 |
| Object class | Foreign Security Principal |
| Default location in Active Directory | CN=WellKnown Security Principals, CN=Configuration, DC=&lt;forestRootDomain&gt; |
| Default user rights | None |

### Creator Owner

The person who created a file or directory is a member of this special identity group. The Windows Server operating system uses this identity to automatically grant access permissions to the creator of a file or directory. A placeholder SID is created in an inheritable ACE. When the ACE is inherited, the system replaces this SID with the SID for the object’s current owner.

| Attribute | Value |
| --- | --- |
| Well-known SID/RID | S-1-3-0 |
| Object class | Foreign Security Principal |
| Default location in Active Directory | CN=WellKnown Security Principals, CN=Configuration, DC=&lt;forestRootDomain&gt; |
| Default user rights | None |

### Dialup

Any user who accesses the system through a dial-up connection has the Dialup identity. This identity distinguishes dial-up users from other types of authenticated users.

| Attribute | Value |
| --- | --- |
| Well-known SID/RID | S-1-5-1 |
| Object class | Foreign Security Principal |
| Default location in Active Directory | CN=WellKnown Security Principals, CN=Configuration, DC=&lt;forestRootDomain&gt; |
| Default user rights | None |

### Digest Authentication

| Attribute | Value |
| --- | --- |
| Well-known SID/RID | S-1-5-64-21 |
| Object class | Foreign Security Principal |
| Default location in Active Directory | CN=WellKnown Security Principals, CN=Configuration, DC=&lt;forestRootDomain&gt; |
| Default user rights | None |

### Enterprise Domain Controllers

This group includes all domain controllers in an Active Directory forest. Domain controllers with enterprise-wide roles and responsibilities have the Enterprise Domain Controllers identity. This identity allows domain controllers to perform certain tasks in the enterprise by using transitive trusts. Membership is controlled by the operating system.

| Attribute | Value |
| --- | --- |
| Well-known SID/RID | S-1-5-9 |
| Object class | Foreign Security Principal |
| Default location in Active Directory | CN=WellKnown Security Principals, CN=Configuration, DC=&lt;forestRootDomain&gt; |
| Default user rights | [Access this computer from the network](/en-us/windows/device-security/security-policy-settings/access-this-computer-from-the-network): SeNetworkLogonRight<br>[Allow log on locally](/en-us/windows/device-security/security-policy-settings/allow-log-on-locally): SeInteractiveLogonRight |

### Enterprise Read-only Domain Controllers

This group includes all Read-only Domain Controllers (RODC) in an Active Directory forest. An Enterprise RODC can replicate a larger subset of the Active Directory database, including the global catalog and read-only domain partitions for all domains in the forest. Membership is controlled by the operating system.

| Attribute | Value |
| --- | --- |
| Well-known SID/RID | S-1-5-21-&lt;RootDomain&gt;-498 |
| Object class | Group |
| Default location in Active Directory | CN=Users, DC=&lt;forestRootDomain&gt; |
| Default user rights | None |

### Everyone

All interactive, network, dial-up, and authenticated users are members of the Everyone group. This special identity group gives wide access to system resources. When a user logs on to the network, the user is automatically added to the Everyone group. Membership is controlled by the operating system.

On computers running Windows 2000 and earlier, the Everyone group includes the Anonymous Logon group as a default member. Beginning in Windows Server 2003, the Everyone group contains only Authenticated Users and Guest. The group no longer includes Anonymous Logon by default. To change the Everyone group setting to include the Anonymous Logon group, in the Registry Editor, go to the **Computer\HKEY\_LOCAL\_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa** key and set the value of the **everyoneincludesanonymous** DWORD to **1**.

| Attribute | Value |
| --- | --- |
| Well-known SID/RID | S-1-1-0 |
| Object class | Foreign Security Principal |
| Default location in Active Directory | CN=WellKnown Security Principals, CN=Configuration, DC=&lt;forestRootDomain&gt; |
| Default user rights | [Access this computer from the network](/en-us/windows/device-security/security-policy-settings/access-this-computer-from-the-network): SeNetworkLogonRight<br>[Bypass traverse checking](/en-us/windows/device-security/security-policy-settings/bypass-traverse-checking): SeChangeNotifyPrivilege |

### Fresh Public Key identity

An SID that means the client's identity is asserted by an authentication authority based on proof of current possession of client public key credentials.

| Attribute | Value |
| --- | --- |
| Well-known SID/RID | S-1-18-3 |
| Object class | Foreign Security Principal |
| Default location in Active Directory | CN=WellKnown Security Principals, CN=Configuration, DC=&lt;forestRootDomain&gt; |
| Default user rights | None |

### Interactive

Any user who is logged on to the local system has the Interactive identity. This identity allows only local users to access a resource. When a user accesses a specific resource on the computer to which they're currently logged on, the user is automatically added to the Interactive group. Membership is controlled by the operating system.

| Attribute | Value |
| --- | --- |
| Well-known SID/RID | S-1-5-4 |
| Object class | Foreign Security Principal |
| Default location in Active Directory | CN=WellKnown Security Principals, CN=Configuration, DC=&lt;forestRootDomain&gt; |
| Default user rights | None |

### IUSR

Internet Information Services (IIS) uses this account by default when anonymous authentication is enabled.

| Attribute | Value |
| --- | --- |
| Well-known SID/RID | S-1-5-17 |
| Object class | Foreign Security Principal |
| Default location in Active Directory | CN=WellKnown Security Principals, CN=Configuration, DC=&lt;forestRootDomain&gt; |
| Default user rights | None |

### Key trust

An SID that means the client's identity is based on proof of possession of public key credentials by using the key trust object.

| Attribute | Value |
| --- | --- |
| Well-known SID/RID | S-1-18-4 |
| Object class | Foreign Security Principal |
| Default location in Active Directory | CN=WellKnown Security Principals, CN=Configuration, DC=&lt;forestRootDomain&gt; |
| Default user rights | None |

### Local Service

The Local Service account is similar to the Authenticated User account. Members of the Local Service account have the same level of access to resources and objects as members of the Users group. This limited access helps safeguard your system if individual services or processes are compromised. Services that run as the Local Service account access network resources as a null session with anonymous credentials. The name of the account is NT AUTHORITY\LocalService. This account doesn't have a password.

| Attribute | Value |
| --- | --- |
| Well-known SID/RID | S-1-5-19 |
| Object class | Foreign Security Principal |
| Default location in Active Directory | CN=WellKnown Security Principals, CN=Configuration, DC=&lt;forestRootDomain&gt; |
| Default user rights | [Adjust memory quotas for a process](/en-us/windows/device-security/security-policy-settings/adjust-memory-quotas-for-a-process): SeIncreaseQuotaPrivilege <br>[Bypass traverse checking](/en-us/windows/device-security/security-policy-settings/bypass-traverse-checking): SeChangeNotifyPrivilege<br><br>[Change the system time](/en-us/windows/device-security/security-policy-settings/change-the-system-time): SeSystemtimePrivilege<br><br>[Change the time zone](/en-us/windows/device-security/security-policy-settings/change-the-time-zone): SeTimeZonePrivilege<br><br>[Create global objects](/en-us/windows/device-security/security-policy-settings/create-global-objects): SeCreateGlobalPrivilege<br><br>[Generate security audits](/en-us/windows/device-security/security-policy-settings/generate-security-audits): SeAuditPrivilege<br><br>[Impersonate a client after authentication](/en-us/windows/device-security/security-policy-settings/impersonate-a-client-after-authentication): SeImpersonatePrivilege<br><br>[Replace a process level token](/en-us/windows/device-security/security-policy-settings/replace-a-process-level-token): SeAssignPrimaryTokenPrivilege |

### LocalSystem

The LocalSystem account is a service account that's used by the operating system. The LocalSystem account is a powerful account that has full access to the system and acts as the computer on the network. If a service logs on to the LocalSystem account on a domain controller, that service has access to the entire domain. Some services are configured by default to log on to the LocalSystem account. Don't change the default service setting. The name of the account is LocalSystem. This account doesn't have a password.

| Attribute | Value |
| --- | --- |
| Well-known SID/RID | S-1-5-18 |
| Object class | Foreign Security Principal |
| Default location in Active Directory | CN=WellKnown Security Principals, CN=Configuration, DC=&lt;forestRootDomain&gt; |
| Default user rights | None |

### MFA key property

An SID that means the key trust object had the multifactor authentication (MFA) property.

| Attribute | Value |
| --- | --- |
| Well-known SID/RID | S-1-18-5 |
| Object class | Foreign Security Principal |
| Default location in Active Directory | CN=WellKnown Security Principals, CN=Configuration, DC=&lt;forestRootDomain&gt; |
| Default user rights | None |

### Network

This group implicitly includes all users who are logged on through a network connection. Any user who accesses the system through a network has the Network identity. This identity allows only remote users to access a resource. When a user accesses a specific resource over the network, the user is automatically added to the Network group. Membership is controlled by the operating system.

| Attribute | Value |
| --- | --- |
| Well-known SID/RID | S-1-5-2 |
| Object class | Foreign Security Principal |
| Default location in Active Directory | CN=WellKnown Security Principals, CN=Configuration, DC=&lt;forestRootDomain&gt; |
| Default user rights | None |

### Network Service

The Network Service account is similar to the Authenticated User account. Members of the Network Service account have the same level of access to resources and objects as members of the Users group. This limited access helps safeguard your system if individual services or processes are compromised. Services that run as the Network Service account access network resources by using the credentials of the computer account. The name of the account is NT AUTHORITY\NetworkService. This account doesn't have a password.

| Attribute | Value |
| --- | --- |
| Well-known SID/RID | S-1-5-20 |
| Object class | Foreign Security Principal |
| Default location in Active Directory | CN=WellKnown Security Principals, CN=Configuration, DC=&lt;forestRootDomain&gt; |
| Default user rights | [Adjust memory quotas for a process](/en-us/windows/device-security/security-policy-settings/adjust-memory-quotas-for-a-process): SeIncreaseQuotaPrivilege<br>[Bypass traverse checking](/en-us/windows/device-security/security-policy-settings/bypass-traverse-checking): SeChangeNotifyPrivilege<br><br>[Create global objects](/en-us/windows/device-security/security-policy-settings/create-global-objects): SeCreateGlobalPrivilege<br><br>[Generate security audits](/en-us/windows/device-security/security-policy-settings/generate-security-audits): SeAuditPrivilege<br><br>[Impersonate a client after authentication](/en-us/windows/device-security/security-policy-settings/impersonate-a-client-after-authentication): SeImpersonatePrivilege<br><br>[Replace a process level token](/en-us/windows/device-security/security-policy-settings/replace-a-process-level-token): SeAssignPrimaryTokenPrivilege |

### NTLM Authentication

| Attribute | Value |
| --- | --- |
| Well-known SID/RID | S-1-5-64-10 |
| Object class | Foreign Security Principal |
| Default location in Active Directory | CN=WellKnown Security Principals, CN=Configuration, DC=&lt;forestRootDomain&gt; |
| Default user rights | None |

### Other Organization

This group implicitly includes all users who are logged on to the system through a dial-up connection. Membership is controlled by the operating system.

| Attribute | Value |
| --- | --- |
| Well-known SID/RID | S-1-5-1000 |
| Object class | Foreign Security Principal |
| Default location in Active Directory | CN=WellKnown Security Principals, CN=Configuration, DC=&lt;forestRootDomain&gt; |
| Default user rights | None |

### Owner Rights

The Owner Rights group represents the current owner of the object. When an ACE that carries this SID is applied to an object, the system ignores the implicit READ\_CONTROL and WRITE\_DAC permissions for the object owner.

| Attribute | Value |
| --- | --- |
| Well-known SID/RID | S-1-3-4 |
| Object class | Foreign Security Principal |
| Default location in Active Directory | CN=WellKnown Security Principals, CN=Configuration, DC=&lt;forestRootDomain&gt; |
| Default user rights | None |

### Principal Self

This identity is a placeholder in an ACE on a user, group, or computer object in Active Directory. When you grant permissions to Principal Self, you grant permissions to the security principal that's represented by the object. During an access check, the operating system replaces the SID for Principal Self with the SID for the security principal that's represented by the object.

| Attribute | Value |
| --- | --- |
| Well-known SID/RID | S-1-5-10 |
| Object class | Foreign Security Principal |
| Default location in Active Directory | CN=WellKnown Security Principals, CN=Configuration, DC=&lt;forestRootDomain&gt; |
| Default user rights | None |

### Proxy

Identifies a SECURITY\_NT\_AUTHORITY proxy.

| Attribute | Value |
| --- | --- |
| Well-known SID/RID | S-1-5-8 |
| Object class | Foreign Security Principal |
| Default location in Active Directory | CN=WellKnown Security Principals, CN=Configuration, DC=&lt;forestRootDomain&gt; |
| Default user rights | None |

### Read-only Domain Controllers

This group includes all RODCs in the domain with read-only rights to the Active Directory database. Except for account passwords, a RODC holds all the Active Directory objects and attributes that a writable domain controller holds. It allows domain controller deployment when physical security is scarce or not guaranteed. RODCs are explicit members of this group.

| Attribute | Value |
| --- | --- |
| Well-known SID/RID | S-1-5-21-&lt;domain&gt;-521 |
| Object class | Group |
| Default location in Active Directory | CN=Users, DC=&lt;rootDomain&gt; |
| Default user rights | None |

Note

The [Denied RODC Password Replication group](understand-security-groups#denied-rodc-password-replication) is created automatically when an RODC account is created in the forest. Passwords can't be replicated in the Denied RODC Password Replication group.

### Remote Interactive Logon

This identity represents all users who are currently logged on to a computer by using a Remote Desktop Protocol connection. This group is a subset of the Interactive group. Access tokens that contain the Remote Interactive Logon SID also contain the Interactive SID.

| Attribute | Value |
| --- | --- |
| Well-known SID/RID | S-1-5-14 |
| Object class | Foreign Security Principal |
| Default location in Active Directory | CN=WellKnown Security Principals, CN=Configuration, DC=&lt;forestRootDomain&gt; |
| Default user rights | None |

### Restricted

Users and computers with restricted capabilities have the Restricted identity. This identity group is used by a process that's running in a restricted security context, such as when you run an application with the RunAs service. When code runs at the Restricted security level, the Restricted SID is added to the user’s access token.

| Attribute | Value |
| --- | --- |
| Well-known SID/RID | S-1-5-12 |
| Object class | Foreign Security Principal |
| Default location in Active Directory | CN=WellKnown Security Principals, CN=Configuration, DC=&lt;forestRootDomain&gt; |
| Default user rights | None |

### SChannel Authentication

| Attribute | Value |
| --- | --- |
| Well-known SID/RID | S-1-5-64-14 |
| Object class | Foreign Security Principal |
| Default location in Active Directory | CN=WellKnown Security Principals, CN=Configuration, DC=&lt;forestRootDomain&gt; |
| Default user rights | None |

### Service

Any service that accesses the system has the Service identity. This identity group includes all security principals that are signed in as a service. This identity grants access to processes that Windows Server services are running. Membership is controlled by the operating system.

| Attribute | Value |
| --- | --- |
| Well-known SID/RID | S-1-5-6 |
| Object class | Foreign Security Principal |
| Default location in Active Directory | CN=WellKnown Security Principals, CN=Configuration, DC=&lt;forestRootDomain&gt; |
| Default user rights | [Create global objects](/en-us/windows/device-security/security-policy-settings/create-global-objects): SeCreateGlobalPrivilege<br>[Impersonate a client after authentication](/en-us/windows/device-security/security-policy-settings/impersonate-a-client-after-authentication): SeImpersonatePrivilege |

### Service asserted identity

An SID that means the client's identity is asserted by a service.

| Attribute | Value |
| --- | --- |
| Well-known SID/RID | S-1-18-2 |
| Object class | Foreign Security Principal |
| Default location in Active Directory | CN=WellKnown Security Principals, CN=Configuration, DC=&lt;forestRootDomain&gt; |
| Default user rights | None |

### Terminal Server User

Any user that's accessing the system through Terminal Services has the Terminal Server User identity. This identity allows users to access Terminal Server applications and to do other necessary tasks with Terminal Server services. Membership is controlled by the operating system.

| Attribute | Value |
| --- | --- |
| Well-known SID/RID | S-1-5-13 |
| Object class | Foreign Security Principal |
| Default location in Active Directory | CN=WellKnown Security Principals, CN=Configuration, DC=&lt;forestRootDomain&gt; |
| Default user rights | None |

### This Organization

| Attribute | Value |
| --- | --- |
| Well-known SID/RID | S-1-5-15 |
| Object class | Foreign Security Principal |
| Default location in Active Directory | CN=WellKnown Security Principals, CN=Configuration, DC=&lt;forestRootDomain&gt; |
| Default user rights | None |

### Window Manager\Window Manager Group

| Attribute | Value |
| --- | --- |
| Well-known SID/RID | S-1-5-90 |
| Object class | Foreign Security Principal |
| Default location in Active Directory | CN=WellKnown Security Principals, CN=Configuration, DC=&lt;forestRootDomain&gt; |
| Default user rights | [Bypass traverse checking](/en-us/windows/device-security/security-policy-settings/bypass-traverse-checking): SeChangeNotifyPrivilege<br>[Increase a process working set](/en-us/windows/device-security/security-policy-settings/increase-a-process-working-set): SeIncreaseWorkingSetPrivilege |