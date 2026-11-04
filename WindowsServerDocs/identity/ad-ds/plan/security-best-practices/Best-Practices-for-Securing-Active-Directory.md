---
layout: Conceptual
title: Best practices for securing Active Directory | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/security-best-practices/best-practices-for-securing-active-directory
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: Learn more about best practices for securing Active Directory.
author: robinharwood
ms.author: roharwoo
ms.date: 2025-05-21T00:00:00.0000000Z
ms.topic: best-practice
locale: en-us
document_id: 2c1a07a2-6191-0e09-748d-c3f526e0ed00
document_version_independent_id: 636f4465-11b0-5a12-2f12-0d05f6b05b86
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/plan/security-best-practices/Best-Practices-for-Securing-Active-Directory.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/plan/security-best-practices/best-practices-for-securing-active-directory
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/plan/security-best-practices/Best-Practices-for-Securing-Active-Directory.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
platformId: 52deeaf9-5bbf-60f2-cc2d-7584616a52a2
---

# Best practices for securing Active Directory | Microsoft Learn

Attacks against computing infrastructure have increased over the last decade in all parts of the world. We live in an age of cyber-warfare, cybercrime, and hacktivism. As a result, organizations of all sizes all over the world have had to deal with information leaks, theft of intellectual property (IP), denial-of-service (DDoS) attacks, or even destroyed infrastructure.

However, as the threat landscape has changed over the years, the security landscape has also adapted to counter these threats. While no organization with an information technology (IT) infrastructure is ever perfectly immune to attack, the ultimate goal of security isn't preventing attack attempts altogether, but protecting the IT infrastructure from attacks. With the right policies, processes, and controls, you can protect key parts of your IT infrastructure from compromise.

In this article, we describe the most common types of vulnerabilities we've observed in Active Directory (AD) deployments. Next, we arm you with recommendations for how to protect these weak points from compromises. We designed these recommendations based on the expertise of our Microsoft IT (MSIT) and Microsoft Information Security and Risk Management (ISRM) organizations. We also show you steps you can take to reduce how much vulnerable infrastructure, or attack surface, on your AD is exposed to the outside world. We also include suggestions for how to recover vital data and infrastructure function if there's a security compromise.

## Common security vulnerabilities

In order to learn how to best protect your infrastructure, you first need to understand where attacks are most likely to strike and how they work. This article only covers general recommendations, but if you want to go into more detail, we've included links to more thorough articles.

Now, let's look at the most common security vulnerabilities.

### Common entry points

Initial breach targets, or entry points, are areas where attackers can most easily enter your IT infrastructure. Entry points are usually gaps in security or updates that attackers can exploit to gain access to a system within your infrastructure. Attackers usually start with one or two systems at a time, then escalate their attack as they spread their influence across more systems undetected.

The most common vulnerabilities are:

- Gaps in antivirus and antimalware deployments
- Incomplete patching
- Outdated applications and operating systems
- Misconfiguration
- Lack of secure application development practices

### Credential theft

Credential theft attacks are when an attacker gains privileged access to a computer on a network by using tools to extract credentials from sessions of accounts that are currently signed in. Attackers often go for specific accounts that already have elevated privileges. The attacker steals the credentials of this account to mimic its identity to gain access to the system.

Credential thieves usually target these kinds of accounts:

- Permanently privileged accounts
- VIP accounts
- Privilege-attached Active Directory accounts
- Domain controllers
- Other infrastructure services that affect identity, access, and configuration management, such as public key infrastructure (PKI) servers or systems management servers

Users with highly privileged accounts raise the risk of having their credentials stolen by engaging in the following behaviors:

- Signing into their privileged accounts on unsecured computers
- Browsing the internet while signed in to a privileged account

You should also avoid poor and risky configurations to protect the credential security of your system, such as:

- Configuring local privileged accounts with the same credentials across all systems.
- Assigning too many users to privileged domain groups, encouraging overuse.
- Insufficiently managing domain controller security.

For more information about vulnerable accounts, see [Attractive accounts for credential theft](attractive-accounts-for-credential-theft).

## Reduce Active Directory attack surface

You can prevent attacks by reducing the *attack surface* on your Active Directory deployment. In other words, you make your deployment safer by closing up gaps in security that we mentioned in the previous section.

### Avoid granting excessive privileges

Credential theft attacks depend on admins granting certain accounts excessive privileges. You can prevent these attacks is to do the following things:

- Remember there are three built-in groups that have the highest privileges in Active Directory by default: Enterprise Admins, Domain Admins, and Administrators. Make sure you take steps to protect those three groups, along with any other groups your organization gave elevated privileges to.
- Implement a least-privilege administrative model. Don't use highly privileged accounts for everyday administrative tasks if you can avoid it. Also, make sure your admin accounts only have the baseline privileges required to do their jobs, with no extra privileges they don't need. Avoid giving excessive privileges to user accounts that don't need them. Make sure you don't accidentally give an account the same privileges across systems unless they absolutely need them.
- Check the following areas of your infrastructure to make sure you aren't granting excessive privileges to user accounts:

    - Active Directory
    - Member servers
    - Workstations
    - Applications
    - Data repositories

For more information, see [Implementing least-privilege administrative models](implementing-least-privilege-administrative-models).

### Use secure administrative hosts

Secure administrative hosts are computers configured to support administration for Active Directories and other connected systems. These hosts don't run nonadministrative software like email applications, web browsers, or productivity software like Microsoft Office.

When configuring a secure administrative host, you must follow these general principles:

- Never administer a trusted system from a less-trusted host.
- Require multifactor authentication when using privileged accounts or doing administrative tasks.
- Physical security for your administrative hosts is as important as system and network security.

For more information, see [Implementing secure administrative hosts](implementing-secure-administrative-hosts).

### Keep your domain controllers secure

If an attacker gains privileged access to a domain controller, they can modify, corrupt, and destroy the AD database. An attack on the domain controller potentially threatens all AD-managed systems and accounts within your organization. Therefore, it's important you take the following measures to keep your domain controllers safe:

- Keep your domain controllers physically secure within their datacenters, branch offices, and remote locations.
- Become familiar with your domain controller operating system.
- Configure your domain controllers with built-in and freely available configuration tools to make security configuration baselines you can enforce with group policy objects (GPOs).

For more information, see [Securing domain controllers against attack](securing-domain-controllers-against-attack).

## Monitor Active Directory for signs of attack or compromise

Another way you can keep your AD deployment secure is to monitor it for signs of malicious attacks or security compromises. You can use legacy audit categories and audit policy subcategories, or use Advanced Audit Policy. For more information, see [Audit Policy Recommendations](audit-policy-recommendations).

## Plan for security compromises

While you can protect your AD from outside attacks, no defense is ever truly perfect. It's important that in addition to taking preventative measures that you also plan for worst-case scenarios. When planning for security breaches, you should follow the guidelines in [Planning for compromise](planning-for-compromise), particularly the section [Rethinking the approach](planning-for-compromise#rethinking-the-approach), You should also read [Maintaining a more secure environment](maintaining-a-more-secure-environment).

Here's a brief summary of things you should do when planning for security compromises, as described in more detail in [Maintaining a more secure environment](maintaining-a-more-secure-environment):

- Maintain a more secure environment
- Create business-centric security practices for AD
- Assign business ownership to AD data
- Implement business-driven lifecycle management
- Classify all AD data as systems, applications, or users

To continue reading more detail about these practices, see [Maintaining a more secure environment](maintaining-a-more-secure-environment).

## Security measure summary table

The following table summarizes the recommendations listed in this article, listed in order of priority. The ones closer to the bottom of the table are the ones you and your organization should prioritize when setting up your Active Directory. However, you're also free to adjust the priority order and how you implement each measure based on your organization's unique needs.

Each measure is also categorized based on whether it's tactical, strategic, preventative, or detective. *Tactical* measures focus on specific components of AD and any related infrastructure. *Strategic* measures are more comprehensive and therefore require more planning to implement. *Preventative* measures prevent attacks from bad actors. *Detective* measures help you detect security breaches as they happen, before they can spread to other systems.

| Security measure | Tactical or Strategic | Preventative or Detective |
| --- | --- | --- |
| Patch applications. | Tactical | Preventative |
| Patch operating systems. | Tactical | Preventative |
| Deploy and promptly update antivirus and antimalware software across all systems and monitor for attempts to remove or disable it. | Tactical | Both |
| Monitor sensitive Active Directory objects for modification attempts and Windows for events that might indicate attempted compromise. | Tactical | Detective |
| Protect and monitor accounts for users who have access to sensitive data | Tactical | Both |
| Prevent powerful accounts from being used on unauthorized systems. | Tactical | Preventative |
| Eliminate permanent membership in highly privileged groups. | Tactical | Preventative |
| Implement controls to grant temporary membership in privileged groups when needed. | Tactical | Preventative |
| Implement secure administrative hosts. | Tactical | Preventative |
| Use application allowlists on domain controllers, administrative hosts, and other sensitive systems. | Tactical | Preventative |
| Identify critical assets, and prioritize their security and monitoring. | Tactical | Both |
| Implement least-privilege, role-based access controls for administration of the directory, its supporting infrastructure, and domain-joined systems. | Strategic | Preventative |
| Isolate legacy systems and applications. | Tactical | Preventative |
| Decommission legacy systems and applications. | Strategic | Preventative |
| Implement secure development lifecycle programs for custom applications. | Strategic | Preventative |
| Implement configuration management, review compliance regularly, and evaluate settings with each new hardware or software version. | Strategic | Preventative |
| Migrate critical assets to pristine forests with stringent security and monitoring requirements. | Strategic | Both |
| Simplify security for end users. | Strategic | Preventative |
| Use host-based firewalls to control and secure communications. | Tactical | Preventative |
| Patch devices. | Tactical | Preventative |
| Implement business-centric lifecycle management for IT assets. | Strategic | N/A |
| Create or update incident recovery plans. | Strategic | N/A |