---
layout: Conceptual
title: Virtualized Domain Controller Cloning Test Guidance for Application Vendors | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/reference/virtual-dc/virtualized-domain-controller-cloning-test-guidance-for-application-vendors
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: 'Learn more about: Virtualized Domain Controller Cloning Test Guidance for Application Vendors'
author: robinharwood
ms.author: roharwoo
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: 91a0982a-012e-496a-48a4-7d522d134ad3
document_version_independent_id: db0a1eac-7c54-22d0-d141-fd35721b1cb0
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/reference/virtual-dc/Virtualized-Domain-Controller-Cloning-Test-Guidance-for-Application-Vendors.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/reference/virtual-dc/virtualized-domain-controller-cloning-test-guidance-for-application-vendors
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/reference/virtual-dc/Virtualized-Domain-Controller-Cloning-Test-Guidance-for-Application-Vendors.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
platformId: ae120863-54dd-6828-1a13-725dbc167cb6
---

# Virtualized Domain Controller Cloning Test Guidance for Application Vendors | Microsoft Learn

This topic explains what application vendors should consider to help ensure their application continues to work as expected after the virtualized domain controller (DC) cloning process completes. It covers those aspects of the cloning process that interest application vendors and scenarios that may warrant additional testing. Application vendors who have validated that their application works on virtualized domain controllers that have been cloned are encouraged to list the name of the application in the Community Content at the bottom of this topic, along with a link to your organization's web site where users can learn more about the validation.

## Overview of virtualized DC cloning

The virtualized domain controller cloning process is described in detail in [Introduction to Active Directory Domain Services (AD DS) Virtualization (Level 100)](../../introduction-to-active-directory-domain-services-ad-ds-virtualization-level-100) and [Virtualized Domain Controller Technical Reference (Level 300)](../../deploy/virtual-dc/virtualized-domain-controller-technical-reference--level-300-). From an application vendor's perspective, these are some considerations to take into account when assessing the impact of cloning to your application:

- The original computer is not destroyed. It remains on the network, interacting with clients. Unlike a rename where the DNS records of the original computer are removed, the original records for the source domain controller remain.
- During the cloning process, the new computer is initially running for a brief period of time under the identity of the old computer until the cloning process is initiated and makes the necessary changes. Applications that create records about the host should ensure that the cloned computer does not overwrite records about the original host during the cloning process.
- Cloning is a specific deployment capability for only virtualized domain controllers, not a general purpose extension to clone other server roles. Some server roles are specifically not supported for cloning:

    - Dynamic Host Configuration Protocol (DHCP)
    - Active Directory Certificate Services (AD CS)
    - Active Directory Lightweight Directory Services (AD LDS)
- As part of the cloning process, the entire VM that represents the original DC is copied, so any application state on that VM is also copied. Validate that the application adapts to this change in state of the local host on the cloned DC, or if any intervention is required, such as a service restart.
- As part of cloning, the new DC gets a new machine identity and provisions itself as a replica DC in the topology. Validate whether the application depends on the machine identity, such as its name, account, SID, and so on. Does it automatically adapt to the change of machine identity on the clone? If that application caches data, ensure that it does not rely on machine identity data that may be cached.

## What is interesting for Application Vendors?

### CustomDCCloneAllowList.xml

A domain controller that runs your application or service cannot be cloned until the application or service is either:

- Added to the CustomDCCloneAllowList.xml file by using the Get-ADDCCloningExcludedApplicationList Windows PowerShell cmdlet

-Or-

- Removed from the domain controller

The first time the user runs the Get-ADDCCloningExcludedApplicationList cmdlet, it returns a list of services and applications that are running on the domain controller but are not in the default list of services and applications that are supported for cloning. By default, your service or application will not be listed. To add your service or application to the list of applications and services that can be safely cloned, the user runs Get-ADDCCloningExcludedApplicationList cmdlet again with the -GenerateXML option in order to add it to the CustomDCCloneAllowList.xml file. For more information, see [Step 2: Run Get-ADDCCloningExcludedApplicationList cmdlet](/en-us/powershell/module/activedirectory/get-addccloningexcludedapplicationlist).

### Distributed System Interactions

Usually services isolated to the local computer either pass or fail when participating in cloning. Distributed services have to be concerned about having two instances of the host computer on the network simultaneously for a brief period of time. This may manifest as a service instance trying to pull information from a partner system where the clone has registered as the new vendor of the identity. Or both instances of the service may push information into the AD DS database at the same time with different results. For example, it is not deterministic which computer will be communicated with when two computers that have Windows Testing Technologies (WTT) service are on the network with the domain controller.

For the distributed DNS Server service, the cloning process carefully avoids overwriting the DNS records of the source domain controller when the clone domain controller starts with a new IP address.

You should not rely on the computer to remove all of the old identity until the end of cloning. After the new domain controller is promoted inside the new context, select Sysprep providers are run to clean up the additional state of the computer. For example, it is at this point the old certificates of the computer are removed and the cryptography secrets that the computer can access are changed.

The greatest factor that varies the timing of the cloning is how many objects there are to replicate from the PDC. Older media increases the time required to complete cloning.

Because your service or application is unknown, it is left running. The cloning process does not change the state of non-Windows services.

Additionally, the new computer has a different IP address than the original computer. These behaviors may cause side effects to your service or application depending on how the service or application behaves in this environment.

## Additional scenarios suggested for testing

### Cloning Failure

Service vendors should test this scenario because when cloning fails the computer boots into Directory Services Repair Mode (DSRM), a form of Safe Mode. At this point the computer has not completed cloning. Some state may have changed and some state may remain from the original domain controller. Test this scenario to understand what impact it can have on your application.

To induce a cloning failure, try to clone a domain controller without granting it permission to be cloned. In this case, the computer will have only changed the IP addresses and still have the majority of its state from the original domain controller. For more information about granting a domain controller permission to be cloned, see [Step 1: Grant the source virtualized domain controller the permission to be cloned](../../get-started/virtual-dc/virtualized-domain-controller-deployment-and-configuration).

### PDC emulator cloning

Service and application vendors should test this scenario because there is an additional reboot when the PDC emulator is cloned. In addition, the majority of cloning is performed under a temporary identity to allow the new clone to interact with the PDC emulator during the cloning process.

### Writable versus read-only domain controllers

Service and application vendors should test cloning by using the same type of domain controller (that is, on a writable or read-only domain controller) that service is planned to run on.