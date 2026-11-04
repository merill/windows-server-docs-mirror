---
layout: Conceptual
title: bitsadmin | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/bitsadmin
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the bitsadmin command, which is a command-line tool used to create, download, or upload jobs and monitor their progress.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 4ee43b9f-de87-dcf2-8aed-23ff82a990fc
document_version_independent_id: 6b7a8c9d-e4d1-8a34-cca8-c0a0c5c22fd6
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/bitsadmin.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/bitsadmin
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/bitsadmin.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: fb1f226d-aa82-f218-3316-b0565f97d87a
---

# bitsadmin | Microsoft Learn

Bitsadmin is a command-line tool used to create, download or upload jobs, and to monitor their progress. The bitsadmin tool uses switches to identify the work to perform. You can call `bitsadmin /?` or `bitsadmin /help` to get a list of switches.

Most switches require a `<job>` parameter, which you set to the job's display name, or GUID. A job's display name doesn't have to be unique. The **/create** and **/list** switches return a job's GUID.

By default, you can access information about your own jobs. To access information for another user's jobs, you must have administrator privileges. If the job was created in an elevated state, then you must run **bitsadmin** from an elevated window; otherwise, you'll have read-only access to the job.

Many of the switches correspond to methods in the [BITS interfaces](/en-us/windows/win32/bits/bits-interfaces). For additional details that may be relevant to using a switch, see the corresponding method.

Use the following switches to create a job, set and retrieve the properties of a job, and monitor the status of a job. For examples that show how to use some of these switches to perform tasks, see [bitsadmin examples](bitsadmin-examples).

## Available switches

- [bitsadmin /addfile](bitsadmin-addfile)
- [bitsadmin /addfileset](bitsadmin-addfileset)
- [bitsadmin /addfilewithranges](bitsadmin-addfilewithranges)
- [bitsadmin /cache](bitsadmin-cache)
- [bitsadmin /cache /delete](bitsadmin-cache-and-delete)
- [bitsadmin /cache /deleteurl](bitsadmin-cache-and-deleteurl)
- [bitsadmin /cache /getexpirationtime](bitsadmin-cache-and-getexpirationtime)
- [bitsadmin /cache /getlimit](bitsadmin-cache-and-getlimit)
- [bitsadmin /cache /help](bitsadmin-cache-and-help)
- [bitsadmin /cache /info](bitsadmin-cache-and-info)
- [bitsadmin /cache /list](bitsadmin-cache-and-list)
- [bitsadmin /cache /setexpirationtime](bitsadmin-cache-and-setexpirationtime)
- [bitsadmin /cache /setlimit](bitsadmin-cache-and-setlimit)
- [bitsadmin /cache /clear](bitsadmin-cache-clear)
- [bitsadmin /cancel](bitsadmin-cancel)
- [bitsadmin /complete](bitsadmin-complete)
- [bitsadmin /create](bitsadmin-create)
- [bitsadmin /examples](bitsadmin-examples)
- [bitsadmin /getaclflags](bitsadmin-getaclflags)
- [bitsadmin /getbytestotal](bitsadmin-getbytestotal)
- [bitsadmin /getbytestransferred](bitsadmin-getbytestransferred)
- [bitsadmin /getclientcertificate](bitsadmin-getclientcertificate)
- [bitsadmin /getcompletiontime](bitsadmin-getcompletiontime)
- [bitsadmin /getcreationtime](bitsadmin-getcreationtime)
- [bitsadmin /getcustomheaders](bitsadmin-getcustomheaders)
- [bitsadmin /getdescription](bitsadmin-getdescription)
- [bitsadmin /getdisplayname](bitsadmin-getdisplayname)
- [bitsadmin /geterror](bitsadmin-geterror)
- [bitsadmin /geterrorcount](bitsadmin-geterrorcount)
- [bitsadmin /getfilestotal](bitsadmin-getfilestotal)
- [bitsadmin /getfilestransferred](bitsadmin-getfilestransferred)
- [bitsadmin /gethelpertokenflags](bitsadmin-gethelpertokenflags)
- [bitsadmin /gethelpertokensid](bitsadmin-gethelpertokensid)
- [bitsadmin /gethttpmethod](bitsadmin-gethttpmethod)
- [bitsadmin /getmaxdownloadtime](bitsadmin-getmaxdownloadtime)
- [bitsadmin /getminretrydelay](bitsadmin-getminretrydelay)
- [bitsadmin /getmodificationtime](bitsadmin-getmodificationtime)
- [bitsadmin /getnoprogresstimeout](bitsadmin-getnoprogresstimeout)
- [bitsadmin /getnotifycmdline](bitsadmin-getnotifycmdline)
- [bitsadmin /getnotifyflags](bitsadmin-getnotifyflags)
- [bitsadmin /getnotifyinterface](bitsadmin-getnotifyinterface)
- [bitsadmin /getowner](bitsadmin-getowner)
- [bitsadmin /getpeercachingflags](bitsadmin-getpeercachingflags)
- [bitsadmin /getpriority](bitsadmin-getpriority)
- [bitsadmin /getproxybypasslist](bitsadmin-getproxybypasslist)
- [bitsadmin /getproxylist](bitsadmin-getproxylist)
- [bitsadmin /getproxyusage](bitsadmin-getproxyusage)
- [bitsadmin /getreplydata](bitsadmin-getreplydata)
- [bitsadmin /getreplyfilename](bitsadmin-getreplyfilename)
- [bitsadmin /getreplyprogress](bitsadmin-getreplyprogress)
- [bitsadmin /getsecurityflags](bitsadmin-getsecurityflags)
- [bitsadmin /getstate](bitsadmin-getstate)
- [bitsadmin /gettemporaryname](bitsadmin-gettemporaryname)
- [bitsadmin /gettype](bitsadmin-gettype)
- [bitsadmin /getvalidationstate](bitsadmin-getvalidationstate)
- [bitsadmin /help](bitsadmin-help)
- [bitsadmin /info](bitsadmin-info)
- [bitsadmin /list](bitsadmin-list)
- [bitsadmin /listfiles](bitsadmin-listfiles)
- [bitsadmin /makecustomheaderswriteonly](bitsadmin-makecustomheaderswriteonly)
- [bitsadmin /monitor](bitsadmin-monitor)
- [bitsadmin /nowrap](bitsadmin-nowrap)
- [bitsadmin /peercaching](bitsadmin-peercaching)
- [bitsadmin /peercaching /getconfigurationflags](bitsadmin-peercaching-and-getconfigurationflags)
- [bitsadmin /peercaching /help](bitsadmin-peercaching-and-help)
- [bitsadmin /peercaching /setconfigurationflags](bitsadmin-peercaching-and-setconfigurationflags)
- [bitsadmin /peers](bitsadmin-peers)
- [bitsadmin /peers /clear](bitsadmin-peers-and-clear)
- [bitsadmin /peers /discover](bitsadmin-peers-and-discover)
- [bitsadmin /peers /help](bitsadmin-peers-and-help)
- [bitsadmin /peers /list](bitsadmin-peers-and-list)
- [bitsadmin /rawreturn](bitsadmin-rawreturn)
- [bitsadmin /removeclientcertificate](bitsadmin-removeclientcertificate)
- [bitsadmin /removecredentials](bitsadmin-removecredentials)
- [bitsadmin /replaceremoteprefix](bitsadmin-replaceremoteprefix)
- [bitsadmin /reset](bitsadmin-reset)
- [bitsadmin /resume](bitsadmin-resume)
- [bitsadmin /setaclflag](bitsadmin-setaclflag)
- [bitsadmin /setclientcertificatebyid](bitsadmin-setclientcertificatebyid)
- [bitsadmin /setclientcertificatebyname](bitsadmin-setclientcertificatebyname)
- [bitsadmin /setcredentials](bitsadmin-setcredentials)
- [bitsadmin /setcustomheaders](bitsadmin-setcustomheaders)
- [bitsadmin /setdescription](bitsadmin-setdescription)
- [bitsadmin /setdisplayname](bitsadmin-setdisplayname)
- [bitsadmin /sethelpertoken](bitsadmin-sethelpertoken)
- [bitsadmin /sethelpertokenflags](bitsadmin-sethelpertokenflags)
- [bitsadmin /sethttpmethod](bitsadmin-sethttpmethod)
- [bitsadmin /setmaxdownloadtime](bitsadmin-setmaxdownloadtime)
- [bitsadmin /setminretrydelay](bitsadmin-setminretrydelay)
- [bitsadmin /setnoprogresstimeout](bitsadmin-setnoprogresstimeout)
- [bitsadmin /setnotifycmdline](bitsadmin-setnotifycmdline)
- [bitsadmin /setnotifyflags](bitsadmin-setnotifyflags)
- [bitsadmin /setpeercachingflags](bitsadmin-setpeercachingflags)
- [bitsadmin /setpriority](bitsadmin-setpriority)
- [bitsadmin /setproxysettings](bitsadmin-setproxysettings)
- [bitsadmin /setreplyfilename](bitsadmin-setreplyfilename)
- [bitsadmin /setsecurityflags](bitsadmin-setsecurityflags)
- [bitsadmin /setvalidationstate](bitsadmin-setvalidationstate)
- [bitsadmin /suspend](bitsadmin-suspend)
- [bitsadmin /takeownership](bitsadmin-takeownership)
- [bitsadmin /transfer](bitsadmin-transfer)
- [bitsadmin /util](bitsadmin-util)
- [bitsadmin /util /enableanalyticchannel](bitsadmin-util-and-enableanalyticchannel)
- [bitsadmin /util /getieproxy](bitsadmin-util-and-getieproxy)
- [bitsadmin /util /help](bitsadmin-util-and-help)
- [bitsadmin /util /repairservice](bitsadmin-util-and-repairservice)
- [bitsadmin /util /setieproxy](bitsadmin-util-and-setieproxy)
- [bitsadmin /util /version](bitsadmin-util-and-version)
- [bitsadmin /wrap](bitsadmin-wrap)