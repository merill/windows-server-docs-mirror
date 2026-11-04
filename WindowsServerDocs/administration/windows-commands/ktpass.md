---
layout: Conceptual
title: ktpass | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/ktpass
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the ktpass command, which configures the server principal name for the host or service in AD DS and generates a .keytab file that contains the shared secret key of the service.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: eea3421f-ca9a-066d-a4e8-f5cda2ff4f21
document_version_independent_id: e669a297-4c4d-fdd0-4e19-6a0a7fd30be5
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/ktpass.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/ktpass
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/ktpass.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
platformId: 12c9f901-437d-28d0-0371-29fe77121afa
---

# ktpass | Microsoft Learn

Configures the server principal name for the host or service in Active Directory Domain Services (AD DS) and generates a .keytab file that contains the shared secret key of the service. The .keytab file is based on the Massachusetts Institute of Technology (MIT) implementation of the Kerberos authentication protocol. The ktpass command-line tool allows non-Windows services that support Kerberos authentication to use the interoperability features provided by the Kerberos Key Distribution Center (KDC) service.

## Syntax

```
ktpass
[/out <filename>]
[/princ <principalname>]
[/mapuser <useraccount>]
[/mapop {add|set}] [{-|+}desonly] [/in <filename>]
[/pass {password|*|{-|+}rndpass}]
[/minpass]
[/maxpass]
[/crypto {DES-CBC-CRC|DES-CBC-MD5|RC4-HMAC-NT|AES256-SHA1|AES128-SHA1|All}]
[/itercount]
[/ptype {KRB5_NT_PRINCIPAL|KRB5_NT_SRV_INST|KRB5_NT_SRV_HST}]
[/kvno <keyversionnum>]
[/answer {-|+}]
[/target]
[/rawsalt] [{-|+}dumpsalt] [{-|+}setupn] [{-|+}setpass <password>]  [/?|/h|/help]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /out `<filename>` | Specifies the name of the Kerberos version 5 .keytab file to generate. **Note:** This is the .keytab file you transfer to a computer that isn't running the Windows operating system, and then replace or merge with your existing .keytab file, */Etc/Krb5.keytab*. |
| /princ `<principalname>` | Specifies the principal name in the form host/computer.contoso.com@CONTOSO.COM. **Warning:** This parameter is case-sensitive. |
| /mapuser `<useraccount>` | Maps the name of the Kerberos principal, which is specified by the **princ** parameter, to the specified domain account. |
| /mapop `{add|set}` | Specifies how the mapping attribute is set.<br>- **Add** - Adds the value of the specified local user name. This is the default.<br>- **Set** - Sets the value for Data Encryption Standard (DES)-only encryption for the specified local user name. |
| `{-|+}`desonly | DES-only encryption is set by default.<br>- **+** Sets an account for DES-only encryption.<br>- **-** Releases restriction on an account for DES-only encryption. **Important:** Windows doesn't support DES by default. |
| /in `<filename>` | Specifies the .keytab file to read from a host computer that is not running the Windows operating system. |
| /pass `{password|*|{-|+}rndpass}` | Specifies a password for the principal user name that is specified by the **princ** parameter. Use `*` to prompt for a password. |
| /minpass | Sets the minimum length of the random password to 15 characters. |
| /maxpass | Sets the maximum length of the random password to 256 characters. |
| /crypto `{DES-CBC-CRC|DES-CBC-MD5|RC4-HMAC-NT|AES256-SHA1|AES128-SHA1|All}` | Specifies the keys that are generated in the keytab file:<br>- **DES-CBC-CRC** - Used for compatibility.<br>- **DES-CBC-MD5** - Adheres more closely to the MIT implementation and is used for compatibility.<br>- **RC4-HMAC-NT** - Employs 128-bit encryption.<br>- **AES256-SHA1** - Employs AES256-CTS-HMAC-SHA1-96 encryption.<br>- **AES128-SHA1** - Employs AES128-CTS-HMAC-SHA1-96 encryption.<br>- **All** - States that all supported cryptographic types can be used.<br><br><br>**Note:** Because the default settings are based on older MIT versions, you should always use the `/crypto` parameter. |
| /itercount | Specifies the iteration count that is used for AES encryption. The default ignores **itercount** for non-AES encryption and sets AES encryption to 4,096. |
| /ptype `{KRB5_NT_PRINCIPAL|KRB5_NT_SRV_INST|KRB5_NT_SRV_HST}` | Specifies the principal type.<br>- **KRB5\_NT\_PRINCIPAL** - The general principal type (recommended).<br>- **KRB5\_NT\_SRV\_INST** - The user service instance<br>- **KRB5\_NT\_SRV\_HST** - The host service instance |
| /kvno `<keyversionnum>` | Specifies the key version number. The default value is 1. |
| /answer `{-|+}` | Sets the background answer mode:<br>- **-** Answers reset password prompts automatically with **NO**.<br>- **+** Answers reset password prompts automatically with **YES**. |
| /target | Sets which domain controller to use. The default is for the domain controller to be detected, based on the principal name. If the domain controller name doesn't resolve, a dialog box will prompt for a valid domain controller. |
| /rawsalt | forces ktpass to use the rawsalt algorithm when generating the key. This parameter is optional. |
| `{-|+}dumpsalt` | The output of this parameter shows the MIT salt algorithm that is being used to generate the key. |
| `{-|+}setupn` | Sets the user principal name (UPN) in addition to the service principal name (SPN). The default is to set both in the .keytab file. |
| `{-|+}setpass <password>` | Sets the user's password when supplied. If rndpass is used, a random password is generated instead. |
| /? | Displays Help for this command. |

#### Remarks

- Services running on systems that aren't running the Windows operating system can be configured with service instance accounts in AD DS. This allows any Kerberos client to authenticate to services that are not running the Windows operating system by using Windows KDCs.
- The **/princ** parameter isn't evaluated by ktpass and is used as provided. There's no check to see if the parameter matches the exact case of the **userPrincipalName** attribute value when generating the Keytab file. Case-sensitive Kerberos distributions using this Keytab file might have problems if there's no exact case match, and could even fail during pre-authentication. To check and retrieve the correct **userPrincipalName** attribute value from a LDifDE export file. For example:

    ```
    ldifde /f keytab_user.ldf /d CN=Keytab User,OU=UserAccounts,DC=contoso,DC=corp,DC=microsoft,DC=com /p base /l samaccountname,userprincipalname
    ```

### Examples

To create a Kerberos .keytab file for a host computer that isn't running the Windows operating system, you must map the principal to the account and set the host principal password.

1. Use the active directory **User and computers** snap-in to create a user account for a service on a computer that is not running the Windows operating system. For example, create an account with the name *User1*.
2. Use the **ktpass** command to set up an identity mapping for the user account by typing:

    ```
    ktpass /princ host/User1.contoso.com@CONTOSO.COM /mapuser User1 /pass MyPas$w0rd /out machine.keytab /crypto all /ptype KRB5_NT_PRINCIPAL /mapop set
    ```

    Note

    You cannot map multiple service instances to the same user account.
3. Merge the .keytab file with the */Etc/Krb5.keytab* file on a host computer that isn't running the Windows operating system.

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)