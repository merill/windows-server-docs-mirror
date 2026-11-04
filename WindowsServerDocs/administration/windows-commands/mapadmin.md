---
layout: Conceptual
title: mapadmin | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/mapadmin
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the mapadmin command, which manages User Name Mapping for Microsoft Services for Network File System.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: faacc0c5-92fc-fc79-aa3e-576d899e43f1
document_version_independent_id: e104e508-da7d-b184-98a3-275a8fdb3400
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/mapadmin.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/mapadmin
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/mapadmin.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: ab44dc79-e5a0-0d2a-fda7-6b3695bd23f7
---

# mapadmin | Microsoft Learn

The **mapadmin** command-line utility administers User Name Mapping on the local or remote computer running Microsoft Services for Network File System. If you are logged on with an account that does not have administrative credentials, you can specify a user name and password of an account that does.

## Syntax

```
mapadmin [<computer>] [-u <user> [-p <password>]]
mapadmin [<computer>] [-u <user> [-p <password>]] {start | stop}
mapadmin [<computer>] [-u <user> [-p <password>]] config <option[...]>
mapadmin [<computer>] [-u <user> [-p <password>]] add -wu <windowsuser> -uu <UNIXuser> [-setprimary]
mapadmin [<computer>] [-u <user> [-p <password>]] add -wg <windowsgroup> -ug <UNIXgroup> [-setprimary]
mapadmin [<computer>] [-u <user> [-p <password>]] setprimary -wu <Windowsuser> [-uu <UNIXuser>]
mapadmin [<computer>] [-u <user> [-p <password>]] setprimary -wg <Windowsgroup> [-ug <UNIXgroup>]
mapadmin [<computer>] [-u <user> [-p <password>]] delete <option[...]>
mapadmin [<computer>] [-u <user> [-p <password>]] list <option[...]>
mapadmin [<computer>] [-u <user> [-p <password>]] backup <filename>
mapadmin [<computer>] [-u <user> [-p <password>]] restore <filename>
mapadmin [<computer>] [-u <user> [-p <password>]] adddomainmap -d <Windowsdomain> {-y <<NISdomain>> | -f <path>}
mapadmin [<computer>] [-u <user> [-p <password>]] removedomainmap -d <Windowsdomain> -y <<NISdomain>>
mapadmin [<computer>] [-u <user> [-p <password>]] removedomainmap -all
mapadmin [<computer>] [-u <user> [-p <password>]] listdomainmaps
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<computer>` | Specifies the remote computer running the User Name Mapping service that you want to administer. You can specify the computer using a Windows Internet Name Service (WINS) name or a Domain Name System (DNS) name, or by Internet Protocol (IP) address. |
| -u `<user>` | Specifies the user name of the user whose credentials are to be used. It might be necessary to add the domain name to the user name in the form *domain\username*. |
| -p `<password>` | Specifies the password of the user. If you specify the **-u** option but omit the **-p** option, you are prompted for the user's password. |
| `start | stop` | Starts or stops the User Name Mapping service. |
| config | Specifies general settings for User Name Mapping. The following options are available with this parameter:<br>- **-r `<dddd>:<hh>:<mm>`:** Specifies the refresh interval for updating from the Windows and NIS databases in days, hours, and minutes. The minimum interval is 5 minutes.<br>- **-i `{yes | no}`:** Turns simple mapping on (**yes**) or off (**no**). By default, mapping is turned on. |
| add | Creates a new mapping for a user or group. The following options are available with this parameter:<br>- **-wu `<name>`:** Specifies the name of the Windows user for which a new mapping is being created.<br>- **-uu `<name>`:** Specifies the name of the UNIX user for which a new mapping is being created.<br>- **-wg `<group>`:** Specifies the name of the Windows group for which a new mapping is being created.<br>- **-ug `<group>`:** Specifies the name of the UNIX group for which a new mapping is being created.<br>- **-setprimary:** Specifies that the new mapping is the primary mapping. |
| setprimary | Specifies which mapping is the primary mapping for a UNIX user or group with multiple mappings. The following options are available with this parameter:<br>- **-wu `<name>`:** Specifies the Windows user of the primary mapping. If more than one mapping for the user exists, use the **-uu** option to specify the primary mapping.<br>- **-uu `<name>`:** Specifies the UNIX user of the primary mapping.<br>- **-wg `<group>`:** Specifies the Windows group of the primary mapping. If more than one mapping for the group exists, use the **-ug** option to specify the primary mapping.<br>- **-ug `<group>`:** Specifies the UNIX group of the primary mapping. |
| delete | Removes the mapping for a user or group. The following options are available for this parameter:<br>- **-wu `<user>`:** Specifies the Windows user for which the mapping will be deleted, specified as `<windowsdomain>\<username>`.<br>    You must specify either the **-wu** or the **-uu** option, or both. If you specify both options, the particular mapping identified by the two options will be deleted. If you specify only the **-wu** option, all mappings for the specified user will be deleted.<br>- **-uu `<user>`:** Specifies the UNIX user for whom the mapping will be deleted, specified as `<username>`.<br>    You must specify either the **-wu** or the **-uu** option, or both. If you specify both options, the particular mapping identified by the two options will be deleted. If you specify only the **-uu** option, all mappings for the specified user will be deleted.<br>- **-wg `<group>`:** Specifies the Windows group for which the mapping will be deleted, specified as `<windowsdomain>\<username>`.<br>    You must specify either the **-wg** or the **-ug** option, or both. If you specify both options, the particular mapping identified by the two options will be deleted. If you specify only the **-wg** option, all mappings for the specified group will be deleted.<br>- **-ug `<group>`:** Specifies the UNIX group for which the mapping will be deleted, specified as `<groupname>`.<br>    You must specify either the **-wg** or the **-ug** option, or both. If you specify both options, the particular mapping identified by the two options will be deleted. If you specify only the **-ug** option, all mappings for the specified group will be deleted. |
| list | Displays information about user and group mappings. The following options are available with this parameter:<br>- **-all:** Lists both simple and advanced mappings for users and groups.<br>- **-simple:** Lists all simple mapped users and groups.<br>- **-advanced:** Lists all advanced mapped users and groups. Maps are listed in the order in which they are evaluated. Primary maps, marked with an asterisk (\*), are listed first, followed by secondary maps, which are marked with a carat `(^)`.<br>- **-wu `<name>`:** Lists the mapping for a specified Windows user.<br>- **-wg `<group>`:** Lists the mapping for a Windows group.<br>- **-uu `<name>`:** Lists the mapping for a UNIX user.<br>- **-ug `<group>`:** Lists the mapping for a UNIX group. |
| backup | Saves User Name Mapping configuration and mapping data to the file specified by `<filename>`. |
| restore | Replaces configuration and mapping data with data from the file (specified by `<filename>`) that was created using the **backup** parameter. |
| adddomainmap | Adds a simple map between a Windows domain and an NIS domain or password and group files. The following options are available for this parameter:<br>- **-d `<windowsdomain>`:** Specifies the Windows domain to be mapped.<br>- **-y `<NISdomain>`:** Specifies the NIS domain to be mapped. You must use the **-n `<NISserver>`** parameter to specify the NIS server for the NIS domain specified by the **-y** option.<br>- **-f `<path>`:** Specifies the fully-qualified path of directory containing the password and group files to be mapped. The files must be located on the computer being managed, and you can't use **mapadmin** to manage a remote computer to set up maps based on password and group files. |
| removedomainmap | Removes a simple map between a Windows domain and an NIS domain. The following options and argument are available for this parameter:<br>- **-d `<windowsdomain>`:** Specifies the Windows domain of the map to be removed.<br>- **-y `<NISdomain>`:** Specifies the NIS domain of the map to be removed.<br>- **-all:** Specifies that all simple maps between Windows and NIS domains are to be removed. This will also remove any simple map between a Windows domain and password and group files. |
| listdomainmaps | Lists the Windows domains that are mapped to NIS domains or password and group files. |

#### Remarks

- If you don't specify any paramters, the **mapadmin** command displays the current settings for User Name Mapping.
- For all options that specify a user or group name, the following formats can be used:

    - For Windows users, use the formats: `<domain>\<username>`, `\\<computer>\<username>`, `\<computer>\<username>`, or `<computer>\<username>`
    - For Windows groups, use the formats: `<domain>\<groupname>`, `\\<computer>\<groupname>`, `\<computer>\<groupname>`, or `<computer>\<groupname>`
    - For UNIX users, use the formats: `<NISdomain>\<username>`, `<username>@<NISdomain>`, `<username>@PCNFS`, or `PCNFS\<username>`
    - For UNIX groups, use the formats: `<NISdomain>\<groupname>`, `<groupname>@<NISdomain>`, `<groupname>@PCNFS`, or `PCNFS\<groupname>`

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)