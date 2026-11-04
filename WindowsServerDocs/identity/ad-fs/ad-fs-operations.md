---
layout: Conceptual
title: AD FS Operations | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/ad-fs-operations
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: AD FS Operations'
ms.date: 2025-04-08T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: 9119ff84-3285-5c38-d0db-40ae98051655
document_version_independent_id: 69857a32-0909-c508-e1ca-a7e982fd7071
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/ad-fs-operations.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/ad-fs-operations
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/ad-fs-operations.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: 7572b449-cfbe-b019-2283-d9e724d25441
---

# AD FS Operations | Microsoft Learn

Important

Instead of upgrading to the latest version of AD FS, Microsoft highly recommends migrating to Microsoft Entra ID. For more information, see [Resources for decommissioning AD FS](ad-fs-decommission)

This document contains a list of all of the documentation operations for AD FS.

## Service Configuration

- [Update SSL Certificates in AD FS and WAP 2016](operations/manage-ssl-certificates-ad-fs-wap)
- [AD FS Rapid Restore Tool](operations/ad-fs-rapid-restore-tool)
- [Configure alternate hostname binding for certificate authentication in AD FS](operations/ad-fs-support-for-alternate-hostname-binding-for-certificate-authentication)
- [Add an Attribute Store](operations/add-an-attribute-store)
- [Customize HTTP security response headers with AD FS 2019](operations/customize-http-security-headers-ad-fs)
- [Delegate AD FS Powershell Commandlet Access to Non-Admin Users](operations/delegate-ad-fs-pshell-access)
- [Fine tune SQL and address latency](operations/adfs-sql-latency)
- [AlwaysOn Availability Groups](operations/ad-fs-always-on)
- [What is KDFv2?](operations/what-is-kdfv2)

## Authentication Configuration

### Strong Authentication (MFA) & Password-less

- [Configure External Authentication providers as primary in AD FS (2019 or later)](operations/additional-authentication-methods-ad-fs)
- [Configure AD FS (2016 or later) and Azure MFA](operations/configure-ad-fs-and-azure-mfa)
- [Configure Additional Authentication Methods for AD FS](operations/configure-additional-authentication-methods-for-ad-fs)

### Lockout protection

- [Configure AD FS Extranet Soft Lockout Protection](operations/configure-ad-fs-extranet-soft-lockout-protection)
- [Configure AD FS Extranet Smart Lockout Protection](operations/configure-ad-fs-extranet-smart-lockout-protection)
- [Configure AD FS Extranet Banned IPs](operations/configure-ad-fs-banned-ip)

### Policy Configuration

- [Configure Authentication Policies](operations/configure-authentication-policies)
- [Configuring Alternate Login ID](operations/configuring-alternate-login-id)
- [Configure Microsoft Entra prompt login behavior to work with AD FS policy](operations/ad-fs-prompt-login)

### Kerberos & Certificate authentication

- [Enable AD DS claims & kerberos compound authentication in AD FS](operations/ad-fs-compound-authentication-and-ad-ds-claims)
- [Configure AD FS for User Certificate Authentication](operations/configure-user-certificate-authentication)
- [Configure alternate hostname binding for certificate authentication in AD FS](operations/ad-fs-support-for-alternate-hostname-binding-for-certificate-authentication)

### Device

- [Device Authentication Controls in AD FS](operations/device-authentication-controls-in-ad-fs)

## Authorization Configuration

- [Configure Access Control Policies in AD FS](operations/access-control-policies-in-ad-fs)
- [Configure Device-based Conditional Access on-Premises](operations/configure-device-based-conditional-access-on-premises)

## RPT & CPT configuration

- [Configure AD FS to authenticate users stored in LDAP directories](operations/configure-ad-fs-to-authenticate-users-stored-in-ldap-directories)
- [Configure Claim Rules](operations/configure-claim-rules)
- [Create a Claims Provider Trust](operations/create-a-claims-provider-trust)
- [Create a Non-Claims Aware Relying Party Trust](operations/create-a-non-claims-aware-relying-party-trust)
- [Create a Relying Party Trust](operations/create-a-relying-party-trust)
- [Configure AD FS to work with Aggregated federation provider (e.g. InCommon)](operations/improved-interoperability-with-saml-2.0)

## Sign-in Experience Configuration

- [Configure AD FS 2016 Single Sign On Settings](operations/ad-fs-single-sign-on-settings)
- [Configure AD FS Paginated sign-in](operations/ad-fs-paginated-sign-in)
- [Configure AD FS user sign-in customization](operations/ad-fs-user-sign-in-customization)
- [Configure AD FS to Send Password Expiry Claims](operations/configure-ad-fs-to-send-password-expiry-claims)
- [Configure intranet forms-based authentication for devices that do not support WIA](operations/configure-intranet-forms-based-authentication-for-devices-that-do-not-support-wia)

## Other

- [Join to Workplace from Any Device for SSO and Seamless Second Factor Authentication Across Company Applications](operations/join-to-workplace-from-any-device-for-sso-and-seamless-second-factor-authentication-across-company-applications)
- [Manage Risk with Additional Multi-Factor Authentication for Sensitive Applications](operations/manage-risk-with-additional-multi-factor-authentication-for-sensitive-applications)
- [Manage Risk with Conditional Access Control](operations/manage-risk-with-conditional-access-control)
- [Set up an AD FS lab environment](operations/set-up-an-ad-fs-lab-environment)
- [Walkthrough Guide: Manage Risk with Additional Multi-Factor Authentication for Sensitive Applications](operations/walkthrough-guide--manage-risk-with-additional-multi-factor-authentication-for-sensitive-applications)
- [Walkthrough Guide: Manage Risk with Conditional Access Control](operations/walkthrough-guide--manage-risk-with-conditional-access-control)
- [Walkthrough: Workplace Join with a Windows Device](operations/walkthrough--workplace-join-with-a-windows-device)
- [Walkthrough: Workplace Join with an iOS Device](operations/walkthrough--workplace-join-with-an-ios-device)