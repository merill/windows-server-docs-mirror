---
layout: Conceptual
title: Develop a tool extension | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/manage/windows-admin-center/extend/develop-tool
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-admin-center
ms.update-cycle: 365-days
feedback_product_url: https://aka.ms/wacfeedback
description: Develop a tool extension Windows Admin Center SDK (Project Honolulu)
ms.topic: how-to
author: davannaw-msft
ms.author: dawhite
ms.date: 2026-08-17T00:00:00.0000000Z
locale: en-us
document_id: 6d5eb994-82f2-a292-02fd-e21cf2d8f97f
document_version_independent_id: 80fcfe9d-4f12-287e-09ef-52d46a34b05a
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/manage/windows-admin-center/extend/develop-tool.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: manage/windows-admin-center/extend/develop-tool
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/manage/windows-admin-center/extend/develop-tool.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: 3187f05c-89f9-67b8-e221-40e0291beb58
---

# Develop a tool extension | Microsoft Learn

A tool extension is the primary way that users interact with Windows Admin Center to manage a connection, such as a server or cluster. When you click on a connection in the Windows Admin Center home screen and connect, you will then be presented with a list of tools in the left navigation pane. When you click on a tool, the tool extension is loaded and displayed in the right pane.

When a tool extension is loaded, it can execute WMI calls or PowerShell scripts on a target server or cluster and display information in the UI or execute commands based on user input. Tool extensions define which solutions it should be displayed for, resulting in a different set of tools for each solution.

Note

Not familiar with the different extension types? Learn more about the [extensibility architecture and extension types](understand-extensions).

## Prepare your environment

If you haven't already, [prepare your environment](prepare-development-environment) by installing dependencies and global prerequisites required for all projects.

## Create a new tool extension with the Windows Admin Center SDK

Once you have all the dependencies installed, you are ready to create your new tool extension. Create or browse to a folder that contains your project files, open a command prompt, and set that folder as the working directory. Using the Windows Admin Center SDK that was installed previously, create a new extension with the following syntax:

```console
wac create --company "{!Company Name}" --tool "{!Tool Name}" --version latest
```

| Value | Explanation | Example |
| --- | --- | --- |
| `{!Company Name}` | Your company name (with spaces) | `Contoso Inc` |
| `{!Tool Name}` | Your tool name (with spaces) | `Manage Foo Works` |

Here's an example usage:

```console
wac create --company "Contoso Inc" --tool "Manage Foo Works" --version latest
```

By using Windows Admin Center SDK versions 6.0.0 and higher, you can also create React-based tool extensions. Create a new React-based tool extension by using the following syntax:

```console
wac create-react --company "{!Company Name}" --tool "{!Tool Name}" --version latest
```

| Value | Explanation | Example |
| --- | --- | --- |
| `{!Company Name}` | Your company name (with spaces) | `Contoso Inc` |
| `{!Tool Name}` | Your tool name (with spaces) | `Manage Foo Works` |

Here's an example:

```console
wac create-react --company "Contoso Inc" --tool "Manage Foo Works" --version latest
```

This creates a new folder inside the current working directory using the name you specified for your tool, copies all the necessary template files into your project, and configures the files with your company and tool name.

Note

The --version flag in this command specifies which version of the Windows Admin Center SDK you'd like to target. Read about how to [target a different version](target-sdk-version) of the Windows Admin Center SDK to keep up your extension up to date with the latest SDK and platform changes.

Next, change directory into the folder just created, then install required local dependencies by running the following command:

```console
npm install
```

Once this completes, you've set up everything you need to load your new extension into Windows Admin Center.

## Add content to your extension

Now that you've created an extension with the Windows Admin Center SDK, you are ready to customize content. See these guides for examples of what you can do:

- Add an [empty module](guides/add-module)
- Add an [iFrame](guides/add-iframe)

Even more examples can be found in our Developer Guide. The Developer Guide is a fully functioning solution extension that can be side-loaded into Windows Admin Center, and contains a rich collection of sample functionality and tool examples that you can browse and use in your own extension.

Enable the Developer Guide extension on the **Advanced** page of your Windows Admin Center settings.

## Customize your extension's icon

You can customize the icon that shows for your extension in the tool list. To do this, modify all `icon` entries in `manifest.json` for your extension:

```json
"icon": "{!icon-uri}",
```

| Value | Explanation | Example uri |
| --- | --- | --- |
| `{!icon-uri}` | The location of your icon resource | `assets/foo-icon.svg` |

NOTE: Currently, custom icons aren't visible when side loading your extension in dev mode. As a workaround, remove the contents of `target` as follows:

```json
"target": "",
```

This configuration is only valid for side loading in dev mode, so it's important to preserve the value contained in `target` and then restore it before publishing your extension.

## Build and side load your extension

Next, build and sideload your extension into Windows Admin Center. Open a command window and change directory to your source directory.

- To build and serve the extension, run the following command:

    ```console
    npm run build
    npm start
    ```

Keep this terminal running.

By default, the extension sideloads on port **4200**. To change the port, modify your extension's `package.json` and `appsettings.json` files. Ensure you don't use the port that Windows Admin Center is running on.

To sideload your project into a local instance of Windows Admin Center for testing, attach the locally served project.

- Launch Windows Admin Center in a web browser
- Open the debugger (F12)
- Open the Console and type the following command for sideloading with localhost:

    ```console
    MsftSme.sideLoad("http://localhost:4200")
    ```

    If you followed the [instructions to sideload by using an FQDN](prepare-development-environment#sideloading-by-using-fully-qualified-domain-name), open the console and type the following command:

    ```console
    MsftSme.sideLoad("http://<FQDN>:4200")
    ```
- Refresh the web browser.

Your project now appears in the **Tools** list with (side loaded) next to the name.