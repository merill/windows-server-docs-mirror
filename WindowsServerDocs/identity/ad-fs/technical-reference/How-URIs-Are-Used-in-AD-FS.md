---
layout: Conceptual
title: How URIs Are Used in AD FS | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/technical-reference/how-uris-are-used-in-ad-fs
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: How URIs Are Used in AD FS'
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: 82992476-4dc0-f5d6-f032-628e81c9d453
document_version_independent_id: 88068096-3473-f8b0-e2d5-e1685164c098
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/technical-reference/How-URIs-Are-Used-in-AD-FS.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/technical-reference/how-uris-are-used-in-ad-fs
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/technical-reference/How-URIs-Are-Used-in-AD-FS.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: 75abd434-7d68-7c3f-7ff8-320f57405f4e
---

# How URIs Are Used in AD FS | Microsoft Learn

A Uniform Resource Identifier (URI) is a string of characters that is used as a unique identifier. In AD FS, URIs are used to identify both partner network addresses and configuration objects. When used to identify partner network addresses, the URI is always a URL. When used to identify configuration objects, the URI may be a URN or a URL. For more general information about URIs, see [RFC 2396](https://go.microsoft.com/fwlink/?LinkId=48289) and [RFC 3986](https://go.microsoft.com/fwlink/?LinkId=90453).

## URIs as partner network addresses

The following are the network address URLs that are most often handled by administrators in AD FS.

- The URLs of the Federation Service, including WS-Federation, SAML, WS-Trust, Federation Metadata, WS-MetadataExchange, Privacy and Organization URLs
- The URLs of a relying party trust, including WS-Federation, SAML, and Federation Metadata URLs
- The URLs of a claims provider trust, including WS-Federation, SAML, and Federation Metadata URLs

## URIs as object identifiers

The following table describes the identifiers that are most often handled by administrators in AD FS.

| Identifier name | Description | Comparisons |
| --- | --- | --- |
| Federation Service identifier | This identifier is used to identify the Federation Service. It is used by relying parties that use claims from this Federation Service, as well as claims providers that issue claims to this Federation Service. | When a user requests claims from a claims provider for this Federation Service, the Federation Service identifier will be used to identify the target for the claims.<br>When this Federation Service receives the claims from a claims provider, it will check to ensure the claims are scoped for it by looking for its Federation Service identifier.<br><br>When a relying party is receiving claims from this Federation Service, the relying party will check that the issuer of the claims matches the Federation Service identifier. |
| Relying party identifier | This identifier is used to identify the relying party to this Federation Service. It is used when issuing claims to the relying party. | When a user requests claims from this Federation Service for the relying party, the relying party identifier will be used to identify the relying party for which the claims should be targeted. This comparison is done using prefix matching (see below).<br>When the relying party receives the claims, it will check for its identifier in the security token to ensure the claims are targeted for it. |
| Claims provider identifier | This identifier is used to identify the claims provider to this Federation Service. It is used when receiving claims from the claims provider. | When this Federation Service is receiving claims from the claims provider, this Federation Service will check that the issuer of the claims matches the claims provider identifier. |
| Claim type | This identifier is used to define the type of claim. It is used by this Federation Service, claims providers, and relying parties when sending and receiving claims. | When the Federation Service receives claims from a claims provider, the claim rules associated with the corresponding claims provider trust allow the administrator to compare claim types and process claims. The claim rules associated with a relying party trust also allow the administrator to compare claim types from the claims coming out of the claims provider trust rules, and decide which claims to issue. |

## URI prefix matching for relying party identifiers

The path syntax of a URI is organized hierarchically and is delimited by either all "/" characters or all ":"characters. Thus the path may be split into path sections based on the delimiting character. When prefix matching, each section must be a full match according to the matching rules (these rules govern the casing of matches). For more information about matching rules, see the RFC's mentioned above.

When a relying party is identified in a request to the Federation Service, AD FS uses prefix matching logic to determine if there is a matching relying party trust in the AD FS configuration database.

For example, if the relying party identifier in the AD FS configuration database (URI1) is a prefix to the relying party identifier in the incoming request (URI2), then the following must be true:

- Trailing delimiters (slashes and colons) of path sections or authorities must be ignored
- The scheme and authority parts of URI1 and URI2 must be a case insensitive exact match
- Each path section of URI1 must be an exact match (based on the case sensitivity chosen) to the corresponding path section of URI2
- URI2 may have more path sections than URI1, but URI1 must not have more path sections than URI2
- URI1 cannot have more path sections than URI2
- If URI1 has a fragment, it must match exactly to a URI2 fragment

Note

Query string parameters are not supported and will be ignored in relying party identifiers.

The following table provides additional examples.

| Relying party identifier in AD FS configuration database | Relying party identifier in request message | Request identifier matches the configuration identifier? | Reason |
| --- | --- | --- | --- |
| http://contoso.com | http://contoso.com | TRUE | Exact match |
| http://contoso.com/ | http://contoso.com | TRUE | Trailing slashes are ignored |
| http://contoso.com | http://contoso.com/ | TRUE | Trailing slashes are ignored |
| http://contoso.com | http://contoso.com/hr | TRUE | URI1 has no path and matches scheme and authority to URI2 |
| http://contoso.com/hr | http://contoso.com/hr/web | TRUE | First path sections match, URI1 has no second path section |
| http://contoso.com/hr/ | http://contoso.com/hrw/main | FALSE | URI1 path section 1 does not match URI2 path section 1 |
| http://contoso.com/hr | http://contoso.com | FALSE | URI1 has more path sections than URI2 |
| http://contoso.com/hr | http://contoso.com/hrweb | FALSE | First path sections do not match |
| https://contoso.com | http://contoso.com | FALSE | Scheme parts do not match |
| http://sts.contoso.com | http://contoso.com | FALSE | Authority parts do not match |
| http://contoso.com | http://sts.contoso.com | FALSE | Authority parts do not match |