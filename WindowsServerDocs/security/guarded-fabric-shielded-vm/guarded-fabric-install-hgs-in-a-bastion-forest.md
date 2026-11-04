---
layout: Conceptual
title: Install HGS in an existing bastion forest | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/security/guarded-fabric-shielded-vm/guarded-fabric-install-hgs-in-a-bastion-forest
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: 'Learn more about: Install HGS in an existing bastion forest'
ms.topic: install-set-up-deploy
author: robinharwood
ms.author: roharwoo
ms.date: 2018-08-29T00:00:00.0000000Z
locale: en-us
document_id: c7119b3d-2f59-932f-23e4-717735018fc4
document_version_independent_id: 00f22c40-9020-d970-06d6-a175b68522cb
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/security/guarded-fabric-shielded-vm/guarded-fabric-install-hgs-in-a-bastion-forest.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: security/guarded-fabric-shielded-vm/guarded-fabric-install-hgs-in-a-bastion-forest
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/security/guarded-fabric-shielded-vm/guarded-fabric-install-hgs-in-a-bastion-forest.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/d7c01134-b8f3-438c-822d-13471e513908
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/82fff6b2-939d-4e9a-8f9c-d1c41a59749b
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
platformId: 28283683-e384-4b9d-71b1-4033e98eba7e
---

# Install HGS in an existing bastion forest | Microsoft Learn

## Join the HGS server to the root domain

In an existing bastion forest, HGS must be added to the root domain. Use Server Manager or [Add-Computer](/en-us/powershell/module/Microsoft.PowerShell.Management/Add-Computer?viewFallbackFrom=powershell-5.0) to join your HGS server to the root domain.

## Add the HGS server role

Run all commands in this topic in an elevated PowerShell session.

Add the Host Guardian Service role by running the following command:

```powershell
Install-WindowsFeature -Name HostGuardianServiceRole -IncludeManagementTools -Restart
```

If your datacenter has a secure bastion forest where you want to join HGS nodes, follow these steps. You can also use these steps to configure 2 or more independent HGS clusters that are joined to the same domain.

## Join the HGS server to the desired domain

Use Server Manager or [Add-Computer](/en-us/powershell/module/Microsoft.PowerShell.Management/Add-Computer?viewFallbackFrom=powershell-5.0) to join the HGS servers to the desired domain.

## Prepare Active Directory objects

Create a group managed service account and 2 security groups. You can also pre-stage the cluster objects if the account you are initializing HGS with does not have permission to create computer objects in the domain.

## Group managed service account

The group managed service account (gMSA) is the identity used by HGS to retrieve and use its certificates. Use [New-ADServiceAccount](/en-us/powershell/module/activedirectory/new-adserviceaccount) to create a gMSA. If this is the first gMSA in the domain, you will need to add a Key Distribution Service root key.

Each HGS node will need to be permitted to access the gMSA password. The easiest way to configure this is to create a security group that contains all of your HGS nodes and grant that security group access to retrieve the gMSA password.

You must reboot your HGS server after adding it to a security group to ensure it obtains its new group membership.

```powershell
# Check if the KDS root key has been set up
if (-not (Get-KdsRootKey)) {
    # Adds a KDS root key effective immediately (ignores normal 10 hour waiting period)
    Add-KdsRootKey -EffectiveTime ((Get-Date).AddHours(-10))
}

# Create a security group for HGS nodes
$hgsNodes = New-ADGroup -Name 'HgsServers' -GroupScope DomainLocal -PassThru

# Add your HGS nodes to this group
# If your HGS server object is under an organizational unit, provide the full distinguished name instead of "HGS01"
Add-ADGroupMember -Identity $hgsNodes -Members "HGS01"

# Create the gMSA
New-ADServiceAccount -Name 'HGSgMSA' -DnsHostName 'HGSgMSA.yourdomain.com' -PrincipalsAllowedToRetrieveManagedPassword $hgsNodes
```

The gMSA will require the right to generate events in the security log on each HGS server. If you use Group Policy to configure User Rights Assignment, ensure that the gMSA account is granted the [generate audit events privilege](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn221956%28v=ws.11%29) on your HGS servers.

Note

Group managed service accounts are available beginning with the Windows Server 2012 Active Directory schema. For more information, see [group managed service account requirements](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj128431%28v=ws.11%29).

## JEA security groups

When you set up HGS, a [Just Enough Administration (JEA)](/en-us/powershell/scripting/learn/remoting/jea/overview) PowerShell endpoint is configured to allow admins to manage HGS without needing full local administrator privileges. You are not required to use JEA to manage HGS, but it still must be configured when running Initialize-HgsServer. The configuration of the JEA endpoint consists of designating 2 security groups that contain your HGS admins and HGS reviewers. Users who belong to the admin group can add, change, or remove policies on HGS; reviewers can only view the current configuration.

Create 2 security groups for these JEA groups using Active Directory admin tools or [New-ADGroup](/en-us/powershell/module/activedirectory/new-adgroup).

```powershell
New-ADGroup -Name 'HgsJeaReviewers' -GroupScope DomainLocal
New-ADGroup -Name 'HgsJeaAdmins' -GroupScope DomainLocal
```

## Cluster objects

If the account you are using to set up HGS does not have permission to create new computer objects in the domain, you will need to pre-stage the cluster objects. These steps are explained in [Prestage Cluster Computer Objects in Active Directory Domain Services](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn466519%28v=ws.11%29).

To set up your first HGS node, you will need to create one Cluster Name Object (CNO) and one Virtual Computer Object (VCO). The CNO represents the name of the cluster, and is primarily used internally by Failover Clustering. The VCO represents the HGS service that resides on top of the cluster and will be the name registered with the DNS server.

Important

The user who will run `Initialize-HgsServer` requires **Full Control** over the CNO and VCO objects in Active Directory.

To quickly prestage your CNO and VCO, have an Active Directory admin run the following PowerShell commands:

```powershell
# Create the CNO
$cno = New-ADComputer -Name 'HgsCluster' -Description 'HGS CNO' -Enabled $false -Passthru

# Create the VCO
$vco = New-ADComputer -Name 'HgsService' -Description 'HGS VCO' -Passthru

# Give the CNO full control over the VCO
$vcoPath = Join-Path "AD:\" $vco.DistinguishedName
$acl = Get-Acl $vcoPath
$ace = New-Object System.DirectoryServices.ActiveDirectoryAccessRule $cno.SID, "GenericAll", "Allow"
$acl.AddAccessRule($ace)
Set-Acl -Path $vcoPath -AclObject $acl

# Allow time for your new CNO and VCO to replicate to your other Domain Controllers before continuing
```

## Security baseline exceptions

If you are deploying HGS into a highly locked down environment, certain Group Policy settings may prevent HGS from operating normally. Check your Group Policy objects for the following settings and follow the guidance if you are affected:

### Network Logon

**Policy Path:** Computer Configuration\Windows Settings\Security Settings\Local Policies\User Rights Assignments

**Policy Name:** Deny access to this computer from the network

**Required value:** Ensure the value does not block network logons for all local accounts. You can safely block local administrator accounts, however.

**Reason:** Failover Clustering relies on a non-administrator local account called CLIUSR to manage cluster nodes. Blocking network logon for this user will prevent the cluster from operating correctly.

### Kerberos Encryption

**Policy Path:** Computer Configuration\Windows Settings\Security Settings\Local Policies\Security Options

**Policy Name:** Network Security: Configure encryption types allowed for Kerberos

**Action**: If this policy is configured, you must update the gMSA account with [Set-ADServiceAccount](/en-us/powershell/module/activedirectory/set-adserviceaccount) to use only the supported encryption types in this policy. For instance, if your policy only allows AES128\_HMAC\_SHA1 and AES256\_HMAC\_SHA1, you should run `Set-ADServiceAccount -Identity HGSgMSA -KerberosEncryptionType AES128,AES256`.