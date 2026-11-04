---
layout: Conceptual
title: Windows LAPS passwords and passphrases | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/laps/laps-concepts-passwords-passphrases
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: Documents password and passphrase details for Windows Local Administrator Password Solution (Windows LAPS).
author: jay98014
ms.author: roharwoo
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: ba2b2d9d-7220-d273-0e1e-53692fce4ac2
document_version_independent_id: ba2b2d9d-7220-d273-0e1e-53692fce4ac2
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/laps/laps-concepts-passwords-passphrases.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/laps/laps-concepts-passwords-passphrases
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/laps/laps-concepts-passwords-passphrases.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 82bb3023-c8ae-06d6-8d1b-262b1d2e2d84
---

# Windows LAPS passwords and passphrases | Microsoft Learn

Learn about how passwords and passphrases are created for Windows Local Administrator Password Solution (Windows LAPS).

## Overview

The primary purpose of Windows LAPS is regularly rotate the password of a local Windows account. It's important to understand how Windows LAPS generates random passwords (or random passphrases).

## Password character sets

Windows LAPS supports five different complexity settings that can be used to generate random passwords. The PasswordComplexity policy setting is used to choose which character sets are used when creating a password.

| PasswordComplexity setting | Description | Character sets | Example |
| --- | --- | --- | --- |
| 1 | Large letters | "ABCDEFGHIJKLMNOPQRSTUVWXYZ" | "OZKTIQHCKHRWOX" |
| 2 | Large letters + small letters | "ABCDEFGHIJKLMNOPQRSTUVWXYZ""abcdefghijklmnopqrstuvwxyz" | "fOiMbhmcVFHzmI" |
| 3 | Large letters + small letters + numbers | "ABCDEFGHIJKLMNOPQRSTUVWXYZ""abcdefghijklmnopqrstuvwxyz""0123456789" | "logqQVGs53R4vY" |
| 4 | Large letters + small letters + numbers + specials | "ABCDEFGHIJKLMNOPQRSTUVWXYZ""abcdefghijklmnopqrstuvwxyz""0123456789"",.-+;!#&@{}[]$/()%" | "P5QWg43.1lA}ra" |
| 5 | Large letters + small letters + numbers + specials (improved readability) | "ABCDEFGHJKLMNPRSTUVWXYZ""abcdefghijkmnpqrstuvwxyz""23456789""!#%+@:=?\*" | "vnJ!!?MTb5=U7Y" |

When a complexity setting with multiple character sets is chosen, Windows LAPS ensures that the resultant password contains at least one character randomly chosen from each character set.

The length of passwords is controlled using the PasswordLength policy setting. Passwords created by Windows LAPS default to 14 characters in length, and can be configured to be anywhere from 8-64 characters in length.

Password complexity setting five is equivalent to password complexity setting four, with the following modifications made to improve readability and avoid confusion. The differences between setting four and setting five are as follows:

- Removes the letters 'I', 'O', 'Q', 'l', and 'o'
- Removes the numbers '0' and '1'
- Removes the symbols ',', '.', '&', '{', '}', '[', ']', '(', ')', and ';'
- Adds the symbols ':', '=', '?', and '\*'

Important

The PasswordComplexity setting of '5' is only supported in Windows 11 24H2, Windows Server 2025, and later releases. It isn't required to deploy any Windows Server 2025 domain controllers in order to use this new setting.

## Passphrase word lists

Windows LAPS supports three different complexity settings that can be used to generate random passphrases. The PasswordComplexity policy setting is used to choose which word lists are used when creating a passphrase:

| PasswordComplexity setting | Description | Number of words in list | Example |
| --- | --- | --- | --- |
| 6 | Long words | 7776 | "SedimentWaffleEpilogueArrivalWorseningRecent" |
| 7 | Short words | 1276 | "CauseGraveBossFilthHashCleft" |
| 8 | Short words with unique prefixes | 1276 | "GongDazzlerNumbingAdmitMowerEvidence" |

The length of passphrases is controlled using the PassphraseLength policy setting. Passphrases created by Windows LAPS default to six words in length, and can be configured to be anywhere from three to 10 terms in length. The first character of each word is always capitalized for improved readability. No punctuation or other dividing characters are used between words.

Passphrase word lists were taken from ["Deep Dive: EFF's New Wordlists for Random Passphrases"](https://www.eff.org/deeplinks/2016/07/new-wordlists-random-passphrases) by [Electronic Frontier Foundation](https://www.eff.org/), and are used under a CC-BY-3.0 Attribution license. The specific contents of all Windows LAPS passphrase word lists can be downloaded from [Windows LAPS Passphrase Word Lists](https://go.microsoft.com/fwlink/?linkid=2255471). Microsoft made slight modifications to the original word lists; all changes are detailed in the downloadable lists.

Important

Windows LAPS passphrase support is only supported in Windows 11 24H2, Windows Server 2025, and later releases. It isn't required to deploy Windows Server 2025 domain controllers in order to use this new setting.

## Entropy considerations

Windows LAPS creates truly random passwords and passphrases (no human bias is possible). It's therefore simple to calculate the resultant bits of entropy for a password\passphrase of a given length. The following table lists the resulting bits of entropy across a sample set of password\passphrase lengths.

The supported password complexity settings are listed across the top of the table, and password\passphrase lengths are listed down the left hand side. The entropy values for the *default* policy length settings are **bolded**:

| PasswordComplexity setting -&gt;Password or passphrase lengthV | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 3 |  |  |  |  |  | 39 | 31 | 31 |
| 4 |  |  |  |  |  | 52 | 41 | 41 |
| 5 |  |  |  |  |  | 65 | 52 | 52 |
| **6** |  |  |  |  |  | **78** | **62** | **62** |
| 7 |  |  |  |  |  | 90 | 72 | 72 |
| 8 | 38 | 46 | 48 | 51 | 48 | 103 | 83 | 83 |
| 9 | 42 | 51 | 54 | 57 | 54 | 116 | 93 | 93 |
| 10 | 47 | 57 | 60 | 63 | 60 | 129 | 103 | 103 |
| 11 | 52 | 63 | 65 | 70 | 66 |  |  |  |
| 12 | 56 | 68 | 71 | 76 | 72 |  |  |  |
| 13 | 61 | 74 | 77 | 82 | 78 |  |  |  |
| **14** | **66** | **80** | **83** | **89** | **84** |  |  |  |
| 20 | 94 | 114 | 119 | 126 | 120 |  |  |  |
| 40 | 188 | 228 | 238 | 253 | 240 |  |  |  |
| 60 | 282 | 342 | 357 | 379 | 360 |  |  |  |

At the higher end of the allowable length ranges, the entropy levels could be considered excessive for most normal IT environments. Consider that there's usually a security versus usability tradeoff involved. For example, it's difficult for human beings to read and type long and complex passwords. Switching to passphrases is a useful way to improve these issues while still retaining a reasonable amount of entropy. If maximizing security is a paramount concern you might instead consider alternative protections, for example maintaining the managed account in a disabled state by default.