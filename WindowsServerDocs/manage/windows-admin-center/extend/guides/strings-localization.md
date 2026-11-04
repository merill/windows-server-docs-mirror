---
layout: Conceptual
title: Strings and localization in Windows Admin Center | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/manage/windows-admin-center/extend/guides/strings-localization
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-admin-center
ms.update-cycle: 365-days
feedback_product_url: https://aka.ms/wacfeedback
description: Learn about getting your strings ready for localization in Windows Admin Center SDK (Project Honolulu)
ms.topic: concept-article
author: robinharwood
ms.author: roharwoo
ms.date: 2018-06-18T00:00:00.0000000Z
locale: en-us
document_id: c148af76-1727-0f80-6eee-acf12e7b762a
document_version_independent_id: 63432638-b57c-35d1-3b96-634d2de2eddc
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/manage/windows-admin-center/extend/guides/strings-localization.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: manage/windows-admin-center/extend/guides/strings-localization
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/manage/windows-admin-center/extend/guides/strings-localization.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
platformId: 4be5f78c-9c79-8664-c1ef-346f69cda4b1
---

# Strings and localization in Windows Admin Center | Microsoft Learn

Let's go more in-depth into the Windows Admin Center Extensions SDK and talk about strings and localization.

To enable localization of all strings that are rendered on the presentation layer, take advantage of the strings.resjson file under /src/resources/strings - it's already set up. When you need to add a new string to your extension, add it to this resjson file as a new entry. The existing structure follows this format:

```ts
"<YourExtensionName>_<Component>_<Accessor>": "Your string value goes here.",
```

You can use any format you like for the strings, but be aware that the generation process (the process that takes the resjson and outputs the usable TypeScript class) converts underscore (\_) to periods (.).

For example, this entry:

```ts
"HelloWorld_cim_title": "CIM Component",
```

Generates the following accessor structure:

```ts
MsftSme.resourcesStrings<Strings>().HelloWorld.cim.title;
```

## Add Other Languages for Localization

For localization to other languages, a strings.resjson file needs to be created for each language. These files need to be placed in `\loc\output\{!LanguageFolder}\strings.resjson`. The available languages with corresponding folders are:

| Language | Folder |
| --- | --- |
| Čeština | cs-CZ |
| Deutsch | de-DE |
| English | en-US |
| Español | es-ES |
| Français | fr-FR |
| Magyar | hu-HU |
| Italiano | it-IT |
| 日本語 | ja-JP |
| 한국어 | ko-KR |
| Nederlands | nl-NL |
| Polski | pl-PL |
| Português (Brasil) | pt-BR |
| Português (Portugal) | pt-PT |
| Русский | ru-RU |
| Svenska | sv-SE |
| Türkçe | tr-TR |
| 中文(简体) | zh-CN |
| 中文(繁體) | zh-TW |

Note

If your file structure needs are different inside of loc/output, you will need to adjust the localeOffset for the gulp task ‘generate-resjson-json-localized' that is in the gulpfile.js. This offset is how deep into the loc folder it should start searching for strings.resjson files.

Each strings.resjson file will be formatted in the same way as previously mentioned at the top of this guide.

For example, to include a localization for Español include this entry in `\loc\output\HelloWorld\es-ES\strings.resjson`:

```json
"HelloWorld_cim_title": "CIM Componente",
```

Anytime that you added localized strings, gulp generate must be ran again in order to have them appear. Run:

```cmd
gulp generate
```

To confirm that your strings have been generated navigate to `\src\app\assets\strings\{!LanguageFolder}\strings.resjson`. Your newly added entry will appear in this file. Now if you switch the language option in Windows Admin Center, you will be able to see the localized strings in your extension.