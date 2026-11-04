---
layout: Conceptual
title: Windows Logon Scenarios | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/security/windows-authentication/windows-logon-scenarios
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: Learn about common Windows logon and sign-in scenarios.
ms.topic: concept-article
ms.author: roharwoo
author: robinharwood
ms.date: 2025-06-30T00:00:00.0000000Z
ms.custom: sfi-image-nochange
locale: en-us
document_id: 5e9d28a8-09f3-ab47-5c3f-cd580d10e3fe
document_version_independent_id: d297c961-be04-4c2b-c7d8-2ba412e76936
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/security/windows-authentication/windows-logon-scenarios.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: security/windows-authentication/windows-logon-scenarios
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/security/windows-authentication/windows-logon-scenarios.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 240dc420-e484-053c-0c78-d8f445f309c8
---

# Windows Logon Scenarios | Microsoft Learn

This reference article for IT professionals summarizes common Windows logon and sign-in scenarios.

Windows operating systems require all users to log on to the computer with a valid account to access local and network resources. Windows-based computers secure resources by implementing the logon process, in which users are authenticated. After a user is authenticated, authorization and access control technologies implement the second phase of protecting resources: determining if the authenticated user is authorized to access a resource.

The contents of this article apply to versions of Windows designated in the **Applies to** list at the beginning of this article.

In addition, applications and services can require users to sign in to access the resources that are offered by the application or service. The sign-in process is similar to the logon process, in that a valid account and correct credentials are required, but logon information is stored in the Security Account Manager (SAM) database on the local computer and in Active Directory where applicable. Sign-in account and credential information is managed by the application or service, and optionally can be stored locally in Credential Locker.

To understand how authentication works, see [Windows Authentication Concepts](windows-authentication-concepts).

This article describes the following scenarios:

- Interactive logon
- Network logon
- Smart card logon
- Biometric logon

Caution

When a user performs a local logon, their credentials are verified locally against a cached copy before being authenticated with an identity provider over the network. If the cache verification is successful, the user gains access to the desktop even if the device is offline. However, if the user changes their password in the cloud, the cached verifier isn't updated, which means that they can still access their local machine by using their old password.

## Interactive logon

The logon process begins when a user enters credentials in the credentials entry dialog, when the user inserts a smart card into the smart card reader, or when the user interacts with a biometric device. Users can perform an interactive logon by using a local user account or a domain account to log on to a computer.

The following diagram shows the interactive logon elements and logon process.

![Diagram showing the interactive logon elements and logon process.](../media/windows-logon-scenarios/authn_lsa_architecture_client.gif)

### Local and domain logon

Credentials that the user presents for a domain logon contain all the elements necessary for a local logon, such as account name and password or certificate, and Active Directory domain information. The process confirms the user's identification to the security database on the user's local computer or to an Active Directory domain. This mandatory logon process can't be turned off for users in a domain.

Users can perform an interactive logon to a computer in two ways:

- Locally, when the user has direct physical access to the computer, or when the computer is part of a network of computers.

    A local logon grants a user permission to access Windows resources on the local computer. A local logon requires that the user has a user account in Security Accounts Manager (SAM) on the local computer. SAM protects and manages user and group information in the form of security accounts stored in the local computer registry. The computer can have network access, but it's not required. Local user account and group membership information is used to manage access to local resources.

    A network logon grants a user permission to access Windows resources on the local computer in addition to any resources on networked computers, as defined by the credential's access token. Both a local logon and a network logon require that the user has a user account in Security Accounts Manager (SAM) on the local computer. Local user account and group membership information is used to manage access to local resources, and the access token for the user defines what resources can be accessed on networked computers.

    A local logon and a network logon aren't sufficient to grant the user and computer permission to access and to use domain resources.
- Remotely, through Terminal Services or Remote Desktop Services (RDS), in which case the logon is further qualified as remote interactive.

After an interactive logon, Windows runs applications on behalf of the user, and the user can interact with those applications.

A local logon grants a user permission to access resources on the local computer or resources on networked computers. If the computer is joined to a domain, the Winlogon functionality attempts to log on to that domain.

A domain logon grants a user permission to access local and domain resources. A domain logon requires that the user has a user account in Active Directory. The computer must have an account in the Active Directory domain and be physically connected to the network. Users must also have the user rights to log on to a local computer or a domain. Domain user account information and group membership information are used to manage access to domain and local resources.

### Remote logon

In Windows, accessing another computer through remote logon relies on Remote Desktop Protocol (RDP). Because the user must already have successfully logged on to the client computer before attempting a remote connection, interactive logon processes have successfully finished.

RDP manages the credentials that the user enters by using the Remote Desktop client. Those credentials are intended for the target computer, and the user must have an account on that target computer. In addition, the target computer must be configured to accept a remote connection. The target computer credentials are sent to attempt to perform the authentication process. If authentication is successful, the user is connected to local and network resources that are accessible by using the supplied credentials.

## Network logon

A network logon can only be used after user, service, or computer authentication has occurred. During network logon, the process doesn't use the credentials entry dialog boxes to collect data. Instead, previously established credentials or another method to collect credentials is used. This process confirms the user's identity to any network service that the user is attempting to access. This process is typically invisible to the user unless alternative credentials have to be provided.

To provide this type of authentication, the security system includes these authentication mechanisms:

- Kerberos version 5 protocol
- Public key certificates
- Secure Sockets Layer/Transport Layer Security (SSL/TLS)
- Digest
- NTLM, for compatibility with Microsoft Windows NT 4.0-based systems

For information about the elements and processes, see the interactive logon diagram earlier in this article.

## Smart card logon

Smart cards can be used to log on only to domain accounts, not local accounts. Smart card authentication requires the use of the Kerberos authentication protocol. Starting in Windows 2000 Server, in Windows-based operating systems a public key extension to the Kerberos protocol's initial authentication request is implemented. In contrast to shared secret key cryptography, public key cryptography is asymmetric. That is, two different keys are needed: one to encrypt, another to decrypt. Together, the keys that are required to perform both operations make up a private/public key pair.

To initiate a typical logon session, a user must prove their identity by providing information known only to the user and the underlying Kerberos protocol infrastructure. The secret information is a cryptographic shared key derived from the user's password. A shared secret key is symmetric, which means that the same key is used for both encryption and decryption.

The following diagram shows the elements and processes required for smart card logon.

![Diagram showing the elements and processes required for smart card logon.](../media/windows-logon-scenarios/smartcardcredarchitecture.gif)

When a smart card is used instead of a password, a private/public key pair stored on the user's smart card is substituted for the shared secret key, which is derived from the user's password. The private key is stored only on the smart card. The public key can be made available to anyone with whom the owner wants to exchange confidential information.

For more information about the smart card logon process in Windows, see [How smart card logon works in Windows](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ff404285%28v=ws.10%29).

## Biometric logon

A device is used to capture and build a digital characteristic of an artifact, such as a fingerprint. This digital representation is then compared to a sample of the same artifact, and when the two match, authentication can occur. Computers running any of the operating systems designated in the **Applies to** list at the beginning of this article can be configured to accept this form of logon. However, if biometric logon is only configured for local logon, the user needs to present domain credentials when accessing an Active Directory domain.