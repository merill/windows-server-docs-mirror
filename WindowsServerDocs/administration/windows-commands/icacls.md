---
layout: Conceptual
title: icacls | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/icacls
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the icacls command, which displays or modifies discretionary access control lists (DACL) on specified files, and applies stored DACLs to files in specified directories.
ms.topic: reference
author: robinharwood
ms.author: roharwoo
ms.date: 2025-06-06T00:00:00.0000000Z
locale: en-us
document_id: 5906879b-e678-e3da-c404-07a437b42cc2
document_version_independent_id: 0779c597-9e20-38e0-3ae7-40126f5c2bcb
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/icacls.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/icacls
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/icacls.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/97159432-14a9-4307-a469-d2f2c75f0e33
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/50565c62-5f6b-4687-be38-323113c72c2e
platformId: ada4965d-1307-932a-ccb8-9865c95843ca
---

# icacls | Microsoft Learn

Displays or modifies discretionary access control lists (DACLs) on specified files and applies stored DACLs to files in specified directories.

Note

This command replaces the deprecated [cacls command](cacls).

## Syntax

```
icacls name [/save aclfile] [/setowner user] [/findsid Sid] [/verify] [/reset] [/T] [/C] [/L] [/Q]
icacls name [/grant[:r] Sid:perm[...]] [/deny Sid:perm [...]] [/remove[:g|:d]] Sid[...]]] [/setintegritylevel Level:policy[...]] [/T] [/C] [/L] [/Q]
icacls directory [/substitute SidOld SidNew [...]] [/restore aclfile] [/C] [/L] [/Q]
```

### Parameters

| Parameter | Description |
| --- | --- |
| &lt;name&gt; | Specifies the file for which to display or modify DACLs. |
| &lt;directory&gt; | Specifies the directory for which to display or modify DACLs. |
| /t | Performs the operation on all specified files in the current directory and its subdirectories. |
| /c | Continues the operation even if file errors occur. Error messages are still shown. |
| /l | Performs the operation on a symbolic link instead of its destination. |
| /q | Suppresses success messages. |
| /save &lt;ACLfile&gt; | Stores DACLs for all matching files into an access control list (ACL) file for later use with `/restore`. |
| /setowner &lt;user&gt; | Changes the owner of all matching files to the specified user. |
| /findsid &lt;sid&gt; | Finds all matching files that contain a DACL explicitly mentioning the specified security identifier (SID). |
| /verify | Finds all files with ACLs that aren't canonical or have lengths inconsistent with access control entry (ACE) counts. |
| /reset | Replaces ACLs with default inherited ACLs for all matching files. |
| /grant[:r] &lt;sid&gt;:&lt;perm&gt; | Grants specified user access rights. Permissions replace previously granted explicit permissions. Not adding **:r** means that permissions are added to any previously granted explicit permissions. |
| /deny &lt;sid&gt;:&lt;perm&gt; | Explicitly denies specified user access rights. An explicit deny ACE is added for the stated permissions and the same permissions in any explicit grant are removed. |
| /remove: g | d &lt;sid&gt; | Removes all occurrences of the specified SID from the DACL. This command can also use:- **g** - Removes all occurrences of granted rights to the specified SID<br>- **d** - Removes all occurrences of denied rights to the specified SID |
| /setintegritylevel &lt;perm&gt;&lt;level&gt; | Explicitly adds an integrity ACE to all matching files. The level can be specified as:- **l** - Low<br>- **m** - Medium<br>- **h** - High<br>Inheritance options for the integrity ACE may precede the level and are applied only to directories. |
| /substitute &lt;sidold&gt; &lt;sidnew&gt; | Replaces an existing SID (*sidold*) with a new SID (*sidnew*). Requires using with the `<directory>` parameter. |
| /restore &lt;ACLfile&gt; /c | /l | /q | Applies stored DACLs from `<ACLfile>` to files in the specified directory. Requires using with the `<directory>` parameter. |
| /inheritancelevel: e | d | r | Sets the inheritance level, which can be:- **e** - Enables inheritance<br>- **d** - Disables inheritance and copies the ACEs<br>- **r** - Disables inheritance and removes only inherited ACEs |

## Remarks

- SIDs may be in either numerical or friendly name form. If you use a numerical form, affix the wildcard character **\*** to the beginning of the SID.
- This command preserves the canonical order of ACE entries as:

    - Explicit denials
    - Explicit grants
    - Inherited denials
    - Inherited grants
- The `<perm>` option is a permission mask that can be specified for basic rights, advanced rights, or inheritance rights:

    - A sequence of simple rights (basic permissions) without the need to use parenthesis:

        - **N** - No access
        - **F** - Full access
        - **M** - Modify access
        - **RX** - Read and execute access
        - **R** - Read-only access
        - **W** - Write-only access
        - **D** - Delete access
    - A comma-separated list of specific rights (advanced permissions) which must use parenthesis:

        - **DE** - Delete
        - **RC** - Read control (read permissions)
        - **WDAC** - Write DAC (change permissions)
        - **WO** - Write owner (take ownership)
        - **S** - Synchronize
        - **AS** - Access system security
        - **MA** - Maximum allowed
        - **GR** - Generic read
        - **GW** - Generic write
        - **GE** - Generic execute
        - **GA** - Generic all
        - **RD** - Read data/list directory
        - **WD** - Write data/add file
        - **AD** - Append data/add subdirectory
        - **REA** - Read extended attributes
        - **WEA** - Write extended attributes
        - **X** - Execute/traverse
        - **DC** - Delete child
        - **RA** - Read attributes
        - **WA** - Write attributes
    - A sequence of inheritance rights which must use parenthesis:

        - **(I)** - Inherit. ACE inherited from the parent container.
        - **(OI)** - Object inherit. Objects in this container inherits this ACE. Applies only to directories.
        - **(CI)** - Container inherit. Containers in this parent container inherits this ACE. Applies only to directories.
        - **(IO)** - Inherit only. ACE inherited from the parent container, but doesn't apply to the object itself. Applies only to directories.
        - **(NP)** - Don't propagate inherit. ACE inherited by containers and objects from the parent container, but doesn't propagate to nested containers. Applies only to directories.

## Examples

To save the DACLs for all files in the C:\Windows directory and its subdirectories to the ACLFile file, type:

```
icacls c:\windows\* /save aclfile /t
```

To restore the DACLs for every file within ACLFile that exists in the C:\Windows directory and its subdirectories, type:

```
icacls c:\windows\ /restore aclfile
```

To grant the user User1 Delete and Write DAC permissions to a file named Test1, type:

```
icacls test1 /grant User1:(d,wdac)
```

To grant the user defined by SID S-1-1-0 Delete and Write DAC permissions to a file named TestFile, type:

```
icacls TestFile /grant *S-1-1-0:(d,wdac)
```

To apply a *high* integrity level to a directory and ensure that both its files and subdirectories inherit this level, type:

```
icacls "myDirectory" /setintegritylevel (CI)(OI)H
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)