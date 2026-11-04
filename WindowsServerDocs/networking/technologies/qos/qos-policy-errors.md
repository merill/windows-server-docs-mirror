---
layout: Conceptual
title: QoS Policy Error and Event Messages | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/technologies/qos/qos-policy-errors
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: This topic provides a list of error and event messages for Quality of Service (QoS) Policy in Windows Server 2016.
ms.topic: error-reference
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: 5c759428-43ab-34e4-37c4-f0c2b96c1a15
document_version_independent_id: a444c186-7be5-900e-8aad-af44c1b1a953
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/technologies/qos/qos-policy-errors.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/technologies/qos/qos-policy-errors
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/technologies/qos/qos-policy-errors.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
platformId: dc7c652b-b952-e64b-8298-46aa5d791292
---

# QoS Policy Error and Event Messages | Microsoft Learn

Following are the error and event messages that are associated with QoS Policy.

## Informational Messages

Following is a list of QoS Policy informational messages.

| Attribute | Value |
| --- | --- |
| **MessageId** | 16500 |
| **Severity** | Informational |
| **SymbolicName** | EVENT\_EQOS\_INFO\_MACHINE\_POLICY\_REFRESH\_NO\_CHANGE |
| **Language** | English |
| **Message** | Computer QoS policies successfully refreshed. No changes detected. |

| Attribute | Value |
| --- | --- |
| **MessageId** | 16501 |
| **Severity** | Informational |
| **SymbolicName** | EVENT\_EQOS\_INFO\_MACHINE\_POLICY\_REFRESH\_WITH\_CHANGE |
| **Language** | English |
| **Message** | Computer QoS policies successfully refreshed. Policy changes detected. |

| Attribute | Value |
| --- | --- |
| **MessageId** | 16502 |
| **Severity** | Informational |
| **SymbolicName** | EVENT\_EQOS\_INFO\_USER\_POLICY\_REFRESH\_NO\_CHANGE |
| **Language** | English |
| **Message** | User QoS policies successfully refreshed. No changes detected. |

| Attribute | Value |
| --- | --- |
| **MessageId** | 16503 |
| **Severity** | Informational |
| **SymbolicName** | EVENT\_EQOS\_INFO\_USER\_POLICY\_REFRESH\_WITH\_CHANGE |
| **Language** | English |
| **Message** | User QoS policies successfully refreshed. Policy changes detected. |

| Attribute | Value |
| --- | --- |
| **MessageId** | 16504 |
| **Severity** | Informational |
| **SymbolicName** | EVENT\_EQOS\_INFO\_TCP\_AUTOTUNING\_NOT\_CONFIGURED |
| **Language** | English |
| **Message** | The Advanced QoS Setting for inbound TCP throughput level successfully refreshed. Setting value is not specified by any QoS policy. Local computer default will be applied. |

| Attribute | Value |
| --- | --- |
| **MessageId** | 16505 |
| **Severity** | Informational |
| **SymbolicName** | EVENT\_EQOS\_INFO\_TCP\_AUTOTUNING\_OFF |
| **Language** | English |
| **Message** | The Advanced QoS Setting for inbound TCP throughput level successfully refreshed. Setting value is Level 0 (minimum throughput). |

| Attribute | Value |
| --- | --- |
| **MessageId** | 16506 |
| **Severity** | Informational |
| **SymbolicName** | EVENT\_EQOS\_INFO\_TCP\_AUTOTUNING\_HIGHLY\_RESTRICTED |
| **Language** | English |
| **Message** | The Advanced QoS Setting for inbound TCP throughput level successfully refreshed. Setting value is Level 1. |

| Attribute | Value |
| --- | --- |
| **MessageId** | 16507 |
| **Severity** | Informational |
| **SymbolicName** | EVENT\_EQOS\_INFO\_TCP\_AUTOTUNING\_RESTRICTED |
| **Language** | English |
| **Message** | The Advanced QoS Setting for inbound TCP throughput level successfully refreshed. Setting value is Level 2. |

| Attribute | Value |
| --- | --- |
| **MessageId** | 16508 |
| **Severity** | Informational |
| **SymbolicName** | EVENT\_EQOS\_INFO\_TCP\_AUTOTUNING\_NORMAL |
| **Language** | English |
| **Message** | The Advanced QoS Setting for inbound TCP throughput level successfully refreshed. Setting value is Level 3 (maximum throughput). |

| Attribute | Value |
| --- | --- |
| **MessageId** | 16509 |
| **Severity** | Informational |
| **SymbolicName** | EVENT\_EQOS\_INFO\_APP\_MARKING\_NOT\_CONFIGURED |
| **Language** | English |
| **Message** | The Advanced QoS Setting for DSCP marking overrides successfully refreshed. Setting value is not specified. Applications can set DSCP values independently of QoS policies. |

| Attribute | Value |
| --- | --- |
| **MessageId** | 16510 |
| **Severity** | Informational |
| **SymbolicName** | EVENT\_EQOS\_INFO\_APP\_MARKING\_IGNORED |
| **Language** | English |
| **Message** | The Advanced QoS Setting for DSCP marking overrides successfully refreshed. Application DSCP marking requests will be ignored. Only QoS policies can set DSCP values. |

| Attribute | Value |
| --- | --- |
| **MessageId** | 16511 |
| **Severity** | Informational |
| **SymbolicName** | EVENT\_EQOS\_INFO\_APP\_MARKING\_ALLOWED |
| **Language** | English |
| **Message** | The Advanced QoS Setting for DSCP marking overrides successfully refreshed. Applications can set DSCP values independently of QoS policies. |

| Attribute | Value |
| --- | --- |
| **MessageId** | 16512 |
| **Severity** | Informational |
| **SymbolicName** | EVENT\_EQOS\_INFO\_LOCAL\_SETTING\_DONT\_USE\_NLA |
| **Language** | English |
| **Message** | Selective application of QoS policies based on domain network category has been disabled. QoS policies will be applied to all network interfaces. |

## Warning Messages

Following is a list of QoS Policy warning messages.

| Attribute | Value |
| --- | --- |
| **MessageId** | 16600 |
| **Severity** | Warning |
| **SymbolicName** | EVENT\_EQOS\_WARNING\_TEST\_1 |
| **Language** | English |
| **Message** | EQOS: \*\*\*Testing\*\*\*[, with one string] "%2". |

| Attribute | Value |
| --- | --- |
| **MessageId** | 16601 |
| **Severity** | Warning |
| **SymbolicName** | EVENT\_EQOS\_WARNING\_TEST\_2 |
| **Language** | English |
| **Message** | EQOS: \*\*\*Testing\*\*\*[, with two strings, string1 is] "%2"[, string2 is] "%3". |

| Attribute | Value |
| --- | --- |
| **MessageId** | 16602 |
| **Severity** | Warning |
| **SymbolicName** | EVENT\_EQOS\_WARNING\_MACHINE\_POLICY\_VERSION |
| **Language** | English |
| **Message** | The computer QoS policy "%2" has an invalid version number. This policy will not be applied. |

| Attribute | Value |
| --- | --- |
| **MessageId** | 16603 |
| **Severity** | Warning |
| **SymbolicName** | EVENT\_EQOS\_WARNING\_USER\_POLICY\_VERSION |
| **Language** | English |
| **Message** | The user QoS policy "%2" has an invalid version number. This policy will not be applied. |

| Attribute | Value |
| --- | --- |
| **MessageId** | 16604 |
| **Severity** | Warning |
| **SymbolicName** | EVENT\_EQOS\_WARNING\_MACHINE\_POLICY\_PROFILE\_NOT\_SPECIFIED |
| **Language** | English |
| **Message** | The computer QoS policy "%2" does not specify a DSCP value or throttle rate. This policy will not be applied. |

| Attribute | Value |
| --- | --- |
| **MessageId** | 16605 |
| **Severity** | Warning |
| **SymbolicName** | EVENT\_EQOS\_WARNING\_USER\_POLICY\_PROFILE\_NOT\_SPECIFIED |
| **Language** | English |
| **Message** | The user QoS policy "%2" does not specify a DSCP value or throttle rate. This policy will not be applied. |

| Attribute | Value |
| --- | --- |
| **MessageId** | 16606 |
| **Severity** | Warning |
| **SymbolicName** | EVENT\_EQOS\_WARNING\_MACHINE\_POLICY\_QUOTA\_EXCEEDED |
| **Language** | English |
| **Message** | Exceeded the maximum number of computer QoS policies. The QoS policy "%2" and subsequent computer QoS policies will not be applied. |

| Attribute | Value |
| --- | --- |
| **MessageId** | 16607 |
| **Severity** | Warning |
| **SymbolicName** | EVENT\_EQOS\_WARNING\_USER\_POLICY\_QUOTA\_EXCEEDED |
| **Language** | English |
| **Message** | Exceeded the maximum number of user QoS policies. The QoS policy "%2" and subsequent user QoS policies will not be applied. |

| Attribute | Value |
| --- | --- |
| **MessageId** | 16608 |
| **Severity** | Warning |
| **SymbolicName** | EVENT\_EQOS\_WARNING\_MACHINE\_POLICY\_CONFLICT |
| **Language** | English |
| **Message** | The computer QoS policy "%2" potentially conflicts with other QoS policies. See documentation for rules about which policy will be applied. |

| Attribute | Value |
| --- | --- |
| **MessageId** | 16609 |
| **Severity** | Warning |
| **SymbolicName** | EVENT\_EQOS\_WARNING\_USER\_POLICY\_CONFLICT |
| **Language** | English |
| **Message** | The user QoS policy "%2" potentially conflicts with other QoS policies. See documentation for rules about which policy will be applied. |

| Attribute | Value |
| --- | --- |
| **MessageId** | 16610 |
| **Severity** | Warning |
| **SymbolicName** | EVENT\_EQOS\_WARNING\_MACHINE\_POLICY\_NO\_FULLPATH\_APPNAME |
| **Language** | English |
| **Message** | The computer QoS policy "%2" was ignored because the application path cannot be processed. The application path may be invalid, contain an invalid drive letter, or contain a network mapped drive. |

| Attribute | Value |
| --- | --- |
| **MessageId** | 16611 |
| **Severity** | Warning |
| **SymbolicName** | EVENT\_EQOS\_WARNING\_USER\_POLICY\_NO\_FULLPATH\_APPNAME |
| **Language** | English |
| **Message** | The user QoS policy "%2" was ignored because the application path cannot be processed. The application path may be invalid, contain an invalid drive letter, or contain a network mapped drive. |

## Error Messages

Following is a list of QoS Policy error messages.

| Attribute | Value |
| --- | --- |
| **MessageId** | 16700 |
| **Severity** | Error |
| **SymbolicName** | EVENT\_EQOS\_ERROR\_MACHINE\_POLICY\_REFERESH |
| **Language** | English |
| **Message** | Computer QoS policies failed to refresh. Error code: "%2". |

| Attribute | Value |
| --- | --- |
| **MessageId** | 16701 |
| **Severity** | Error |
| **SymbolicName** | EVENT\_EQOS\_ERROR\_USER\_POLICY\_REFERESH |
| **Language** | English |
| **Message** | User QoS policies failed to refresh. Error code: "%2". |

| Attribute | Value |
| --- | --- |
| **MessageId** | 16702 |
| **Severity** | Error |
| **SymbolicName** | EVENT\_EQOS\_ERROR\_OPENING\_MACHINE\_POLICY\_ROOT\_KEY |
| **Language** | English |
| **Message** | QoS failed to open the machine-level root key for QoS policies. Error code: "%2". |

| Attribute | Value |
| --- | --- |
| **MessageId** | 16703 |
| **Severity** | Error |
| **SymbolicName** | EVENT\_EQOS\_ERROR\_OPENING\_USER\_POLICY\_ROOT\_KEY |
| **Language** | English |
| **Message** | QoS failed to open the user-level root key for QoS policies. Error code: "%2". |

| Attribute | Value |
| --- | --- |
| **MessageId** | 16704 |
| **Severity** | Error |
| **SymbolicName** | EVENT\_EQOS\_ERROR\_MACHINE\_POLICY\_KEYNAME\_TOO\_LONG |
| **Language** | English |
| **Message** | A computer QoS policy exceeds the maximum allowed name length. The offending policy is listed under the machine-level QoS policy root key, with index "%2". |

| Attribute | Value |
| --- | --- |
| **MessageId** | 16705 |
| **Severity** | Error |
| **SymbolicName** | EVENT\_EQOS\_ERROR\_USER\_POLICY\_KEYNAME\_TOO\_LONG |
| **Language** | English |
| **Message** | A user QoS policy exceeds the maximum allowed name length. The offending policy is listed under the user-level QoS policy root key, with index "%2". |

| Attribute | Value |
| --- | --- |
| **MessageId** | 16706 |
| **Severity** | Error |
| **SymbolicName** | EVENT\_EQOS\_ERROR\_MACHINE\_POLICY\_KEYNAME\_SIZE\_ZERO |
| **Language** | English |
| **Message** | A computer QoS policy has a zero length name. The offending policy is listed under the machine-level QoS policy root key, with index "%2". |

| Attribute | Value |
| --- | --- |
| **MessageId** | 16707 |
| **Severity** | Error |
| **SymbolicName** | EVENT\_EQOS\_ERROR\_USER\_POLICY\_KEYNAME\_SIZE\_ZERO |
| **Language** | English |
| **Message** | A user QoS policy has a zero length name. The offending policy is listed under the user-level QoS policy root key, with index "%2". |

| Attribute | Value |
| --- | --- |
| **MessageId** | 16708 |
| **Severity** | Error |
| **SymbolicName** | EVENT\_EQOS\_ERROR\_OPENING\_MACHINE\_POLICY\_SUBKEY |
| **Language** | English |
| **Message** | QoS failed to open the registry subkey for a computer QoS policy. The policy is listed under the machine-level QoS policy root key, with index "%2". |

| Attribute | Value |
| --- | --- |
| **MessageId** | 16709 |
| **Severity** | Error |
| **SymbolicName** | EVENT\_EQOS\_ERROR\_OPENING\_USER\_POLICY\_SUBKEY |
| **Language** | English |
| **Message** | QoS failed to open the registry subkey for a user QoS policy. The policy is listed under the user-level QoS policy root key, with index "%2". |

| Attribute | Value |
| --- | --- |
| **MessageId** | 16710 |
| **Severity** | Error |
| **SymbolicName** | EVENT\_EQOS\_ERROR\_PROCESSING\_MACHINE\_POLICY\_FIELD |
| **Language** | English |
| **Message** | QoS failed to read or validate the "%2" field for the computer QoS policy "%3". |

| Attribute | Value |
| --- | --- |
| **MessageId** | 16711 |
| **Severity** | Error |
| **SymbolicName** | EVENT\_EQOS\_ERROR\_PROCESSING\_USER\_POLICY\_FIELD |
| **Language** | English |
| **Message** | QoS failed to read or validate the "%2" field for the user QoS policy "%3". |

| Attribute | Value |
| --- | --- |
| **MessageId** | 16712 |
| **Severity** | Error |
| **SymbolicName** | EVENT\_EQOS\_ERROR\_SETTING\_TCP\_AUTOTUNING |
| **Language** | English |
| **Message** | QoS failed to read or set inbound TCP throughput level, error code: "%2". |

| Attribute | Value |
| --- | --- |
| **MessageId** | 16713 |
| **Severity** | Error |
| **SymbolicName** | EVENT\_EQOS\_ERROR\_SETTING\_APP\_MARKING |
| **Language** | English |
| **Message** | QoS failed to read or set the DSCP marking override setting, error code: "%2". |

For the next topic in this guide, see [QoS Policy Frequently Asked Questions](qos-policy-faq).

For the first topic in this guide, see [Quality of Service (QoS) Policy](qos-policy-top).