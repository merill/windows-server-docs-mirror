---
layout: Conceptual
title: Use Regular Expressions in NPS | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/technologies/nps/nps-crp-reg-expressions
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: This topic explains the use of regular expressions for pattern matching in NPS in Windows Server. You can use this syntax to specify the conditions of network policy attributes and RADIUS realms.
ms.topic: concept-article
ms.author: roharwoo
author: robinharwood
ms.date: 2019-08-16T00:00:00.0000000Z
locale: en-us
document_id: b2191ccb-751c-fb92-0552-9aec680f04ca
document_version_independent_id: 5b56ba6d-2b5f-84cd-5d40-0fd2390f155d
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/technologies/nps/nps-crp-reg-expressions.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/technologies/nps/nps-crp-reg-expressions
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/technologies/nps/nps-crp-reg-expressions.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/8b896464-3b7d-4e1f-84b0-9bb45aeb5f64
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1d2d671-9549-46e8-918c-24349120dbf5
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 26f6bb4f-1e67-ca4d-66a8-c274a85a80f8
---

# Use Regular Expressions in NPS | Microsoft Learn

This topic explains the use of regular expressions for pattern matching in NPS in Windows Server. You can use this syntax to specify the conditions of network policy attributes and RADIUS realms.

Note

The NPS Console and the NPS MMC snap-in have a 256 character limit for all settings that take a string value. That includes all settings that can be configured using regular expressions. To configure string values that exceed 256 characters, use NETSH NPS commands. Configured string values exceeding 256 characters can't be edited in the NPS Console or the NPS MMC snap-in without invalidating them.

## Pattern-matching reference

You can use the following table as a reference source when creating regular expressions with pattern-matching syntax. Note that regular expression patterns are often surrounded by forward slashes (/).

| Character | Description | Example |
| --- | --- | --- |
| `\ ` | Indicates that the character that follows is a special character, or should be interpreted literally. | `/n/ matches the character "n" while the sequence /\n/ matches a line feed or newline character.` |
| `^` | Matches the beginning of the input or line. |  |
| `$` | Matches the end of the input or line. |  |
| `*` | Matches the preceding character zero or more times. | `/zo*/ matches either "z" or "zoo."` |
| `+` | Matches the preceding character one or more times. | `/zo+/ matches "zoo" but not "z."` |
| `?` | Matches the preceding character zero or one times. | `/a?ve?/ matches the "ve" in "never."` |
| `.` | Matches any single character except a newline character. |  |
| `(pattern)` | Matches "pattern" and remembers the match.To match the literal characters `(` and `)` (parentheses), use `\(` or `\)`. |  |
| `x | y ` | Matches either x or y. |  |
| `{n} ` | Matches exactly n times (n is a non-negative integer). | `/o{2}/ does not match the "o" in "Bob," but matches the first two instances of the letter o in "foooood."` |
| `{n,}` | Matches at least n times (n is a non-negative integer). | `/o{2,}/ does not match the "o" in "Bob" but matches all of the instances of the letter o in "foooood." /o{1,}/ is equivalent to /o+/.` |
| `{n,m}` | Matches at least n and at most m times (m and n are non-negative integers). | `/o{1,3}/ matches the first three instances of the letter o in "fooooood."` |
| `[xyz]` | Matches any one of the enclosed characters (a character set). | `/[abc]/ matches the "a" in "plain."` |
| `[^xyz]` | Matches any characters that are not enclosed (a negative character set). | `/[^abc]/ matches the "p" in "plain."` |
| `\b` | Matches a word boundary (for example, a space). | `/ea*r\b/ matches the "er" in "never early."` |
| `\B` | Matches a nonword boundary. | `/ea*r\B/ matches the "ear" in "never early."` |
| `\d` | Matches a digit character (equivalent to digits from 0 to 9). |  |
| `\D` | Matches a nondigit character (equivalent to `[^0-9]`). |  |
| `\f` | Matches a form feed character. |  |
| `\n` | Matches a line feed character. |  |
| `\r` | Matches a carriage return character. |  |
| `\s` | Matches any white space character including space, tab, and form feed (equivalent to `[ \f\n\r\t\v]`). |  |
| `\S` | Matches any non-white space character (equivalent to `[^ \f\n\r\t\v]`). |  |
| `\t` | Matches a tab character. |  |
| `\v` | Matches a vertical tab character. |  |
| `\w` | Matches any word character, including underscore (equivalent to `[A-Za-z0-9_]`). |  |
| `\W` | Matches any non-word character, excluding underscore (equivalent to `[^A-Za-z0-9_]`). |  |
| `\num` | Refers to remembered matches (`?num`, where num is a positive integer). This option can be used only in the **Replace** text box when configuring attribute manipulation. | `\1` replaces what is stored in the first remembered match. |
| `/n/ ` | Allows the insertion of ASCII codes into regular expressions (`?n`, where n is an octal, hexadecimal, or decimal escape value). |  |

## Examples for network policy attributes

The following examples describe the use of the pattern-matching syntax to specify network policy attributes:

- To specify all phone numbers within the 899 area code, the syntax is:

    `899.*`
- To specify a range of IP addresses that begin with 192.168.1, the syntax is:

    `192\.168\.1\..+`

## Examples for manipulation of the realm name in the User Name attribute

Note

Realm manipulation does not work with PEAP. The desired behaviour might be accomplished by either switching to EAP-TLS or EAP-MSCHAPv2 for authentication or [adding an UPN suffix to the domain](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc772007%28v=ws.11%29) for each additional domain name you need to resolve.

The following examples describe the use of the pattern-matching syntax to manipulate realm names for the User Name attribute, which is located on the **Attribute** tab in the properties of a connection request policy.

**To remove the realm portion of the User Name attribute**

In an outsourced dial-up scenario in which an Internet service provider (ISP) routes connection requests to an organization NPS, the ISP RADIUS proxy might require a realm name to route the authentication request. However, the NPS might not recognize the realm name portion of the user name. Therefore, the realm name must be removed by the ISP RADIUS proxy before it is forwarded to the organization NPS.

- Find: @microsoft\.com
- Replace:

**To replace *user@example.microsoft.com* with *example.microsoft.com\user***

- Find:`(.*)@(.*)`
- Replace:`$2\$1`

**To replace *domain\user* with *specific\_domain\user***

- Find:`(.*)\\(.*)`
- Replace: *specific\_domain*`\$2`

**To replace *user* with *user@specific\_domain***

- Find:`$`
- Replace: @*specific\_domain*

## Example for RADIUS message forwarding by a proxy server

You can create routing rules that forward RADIUS messages with a specified realm name to a set of RADIUS servers when NPS is used as a RADIUS proxy. Following is a recommended syntax for routing requests based on realm name.

- **NetBIOS name**: `WCOAST`
- **Pattern**: `^wcoast\\`

In the following example, wcoast.microsoft.com is a unique user principal name (UPN) suffix for the DNS or Active Directory domain wcoast.microsoft.com. Using the supplied pattern, the NPS proxy can route messages based on domain NetBIOS name or UPN suffix.

- **NetBIOS name**: `WCOAST`
- **UPN suffix**: `wcoast.microsoft.com`
- **Pattern**: `^wcoast\\|@wcoast\.microsoft\.com$`

For more information about managing NPS, see [Manage Network Policy Server](nps-manage-top).

For more information about NPS, see [Network Policy Server (NPS)](nps-top).