---
layout: Conceptual
title: Introducing Token Binding | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/security/token-binding/introducing-token-binding
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: 'Learn more about: Introducing Token Binding'
ms.topic: concept-article
author: robinharwood
ms.author: roharwoo
ms.date: 2025-05-12T00:00:00.0000000Z
locale: en-us
document_id: 8bce365a-a129-ed19-d9b2-da81dfcc04b4
document_version_independent_id: 680e5b0c-03e4-47a6-6b41-c92ed45abcfd
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/security/token-binding/introducing-token-binding.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: security/token-binding/introducing-token-binding
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/security/token-binding/introducing-token-binding.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/e0ffb20c-01c6-407b-a9bd-29111652a1dc
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/3904bce4-d817-48cf-85fd-b6146fca83b7
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: cc201f86-4905-7592-0f72-d1f5c29ae947
---

# Introducing Token Binding | Microsoft Learn

The Token Binding protocol allows applications and services to cryptographically bind their security tokens to the TLS layer to mitigate token theft and replay attacks. The long-lived, uniquely identifiable TLS [RFC5246] bindings can span multiple TLS sessions and connections.

Version support:

- Windows 10, version 1507 – Off by default
    - Token Binding Protocol added [\[draft-ietf-tokbind-protocol-01\]](https://datatracker.ietf.org/doc/draft-ietf-tokbind-protocol/01/)
    - WinInet & HTTP.SYS support of token binding over HTTP [\[draft-ietf-tokbind-https-01\]](https://datatracker.ietf.org/doc/draft-ietf-tokbind-https/01/)
- Windows 10, versions 1511 and 1607, and Windows Server 2016 – On by default
    - Token Binding Protocol updated [\[draft-ietf-tokbind-protocol-01\]](https://datatracker.ietf.org/doc/draft-ietf-tokbind-protocol/01/)
    - TLS extension for token binding negotiation added [\[draft-popov-tokbind-negotiation-00\]](https://tools.ietf.org/html/draft-popov-tokbind-negotiation-00)
    - WinInet & HTTP.SYS support of token binding over HTTP updated [\[draft-ietf-tokbind-https-02\]](https://datatracker.ietf.org/doc/draft-ietf-tokbind-https/02/)
- Windows 10, version 1507 with servicing update [KB4034668](https://support.microsoft.com/kb/KB4034668), Windows 10, version 1511 with servicing update [KB4034660](https://support.microsoft.com/kb/KB4034660), Windows 10, version 1607 and Windows Server 2016 with servicing update [KB4034658](https://support.microsoft.com/kb/KB4034658)support Token Binding Protocol version 0.10 – On by default
    - Token Binding Protocol updated [\[draft-ietf-tokbind-protocol-10\]](https://datatracker.ietf.org/doc/draft-ietf-tokbind-protocol/10/)
    - TLS extension for token binding negotiation added [\[draft-ietf-tokbind-negotiation-05\]](https://tools.ietf.org/html/draft-ietf-tokbind-negotiation-05)
    - WinInet & HTTP.SYS support of token binding over HTTP updated [\[draft-ietf-tokbind-https-06\]](https://datatracker.ietf.org/doc/draft-ietf-tokbind-https/06/)
- Windows 10, version 1703 supports Token Binding Protocol version 0.10 – On by default
    - Token Binding Protocol updated [\[draft-ietf-tokbind-protocol-10\]](https://datatracker.ietf.org/doc/draft-ietf-tokbind-protocol/10/)
    - TLS extension for token binding negotiation added [\[draft-ietf-tokbind-negotiation-05\]](https://tools.ietf.org/html/draft-ietf-tokbind-negotiation-05)
    - WinInet & HTTP.SYS support of token binding over HTTP updated [\[draft-ietf-tokbind-https-06\]](https://datatracker.ietf.org/doc/draft-ietf-tokbind-https/06/)
    - Windows devices with Virtualization-based security enabled will keep the token binding keys in a protected environment that is isolated from the running operating system

Information about ASP .NET support can be found at the [.NET Framework Reference Source](https://referencesource.microsoft.com/#System.Web/ITlsTokenBindingInfo.cs,4a5e5668f5c31170).

For information about .NET Framework, see the following topics:

- [Networking enhancements](https://blogs.msdn.microsoft.com/dotnet/2015/11/30/net-framework-4-6-1-is-now-available/#networking)
- [.NET TokenBinding class](/en-us/dotnet/api/system.security.authentication.extendedprotection.tokenbinding?view=netframework-4.8&amp;preserve-view=true)