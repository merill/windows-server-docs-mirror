---
layout: Conceptual
title: Develop a gateway plugin | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/manage/windows-admin-center/extend/develop-gateway-plugin
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-admin-center
ms.update-cycle: 365-days
feedback_product_url: https://aka.ms/wacfeedback
description: Develop a gateway plugin Windows Admin Center SDK (Project Honolulu)
ms.topic: how-to
author: davannaw-msft
ms.author: dawhite
ms.date: 2018-09-18T00:00:00.0000000Z
locale: en-us
document_id: 88afce9b-1d18-8717-cb21-badbf4b805a0
document_version_independent_id: 960d2997-127e-4e3a-c09d-44d9692f1ee2
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/manage/windows-admin-center/extend/develop-gateway-plugin.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: manage/windows-admin-center/extend/develop-gateway-plugin
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/manage/windows-admin-center/extend/develop-gateway-plugin.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: f3aee15e-4bbb-d42c-ab0e-216955c7ea22
---

# Develop a gateway plugin | Microsoft Learn

A Windows Admin Center gateway plugin enables API communication from the UI of your tool or solution to a target node. Windows Admin Center hosts a gateway service that relays commands and scripts from gateway plugins to be executed on target nodes. The gateway service can be extended to include custom gateway plugins that support protocols other than the default ones.

These gateway plugins are included by default with Windows Admin Center:

- PowerShell gateway plugin
- Windows Management Instrumentation (WMI) gateway plugin

If you would like to communicate with a protocol other than PowerShell or WMI, such as with REST, you can build your own gateway plugin. Gateway plugins are loaded into a separate AppDomain from the existing gateway process, but use the same level of elevation for rights.

Note

Not familiar with the different extension types? Learn more about the [extensibility architecture and extension types](understand-extensions).

Important

The Windows Admin Center SDK and developer tools have not yet been updated to support development of gateway plug-ins compatible with the [Windows Admin Center modernized gateway](../understand/modernized-gateway). Following this guide will not result in a .NET 8 extension compatible with the modernized gateway.

If you're interested in developing a gateway plug-in for the modernized gateway or upgrading your existing gateway plug-in, send an email to [wacextensionrequest@microsoft.com](mailto:wacextdevsupport@microsoft.com?subject=Windows%20Admin%20Center%20Extension%20Development%20Modernized%20Gateway).

Gateway plug-ins developed in .NET 6 while the backend update was in preview may not function correctly with the latest version of Windows Admin Center due to [breaking changes from .NET 6 to .NET 8](/en-us/dotnet/core/compatibility/8.0). We recommend upgrading your extension to .NET 8 as soon as possible.

## Prepare your environment

If you haven't already, [prepare your environment](prepare-development-environment) by installing dependencies and global prerequisites required for all projects.

## Create a gateway plugin (C# library)

To create a custom gateway plugin, create a new C# class that implements the `IPlugIn` interface from the `Microsoft.ManagementExperience.FeatureInterfaces` namespace.

Note

The `IFeature` interface, available in earlier versions of the SDK, is now flagged as obsolete. All gateway plugin development should use IPlugIn (or optionally the HttpPlugIn abstract class).

### Download sample from GitHub

To get started quickly with a custom gateway plugin, you can clone or download a copy of our [sample C# plugin project](https://github.com/Microsoft/windows-admin-center-sdk/tree/master/GatewayPluginExample/Plugin) from our Windows Admin Center SDK [GitHub site](https://aka.ms/wacsdk).

### Add content

Add new content to your cloned copy of the [sample C# plugin project](https://github.com/Microsoft/windows-admin-center-sdk/tree/master/GatewayPluginExample/Plugin) project (or your own project) to contain your custom APIs, then build your custom gateway plugin DLL file to be used in the next steps.

### Deploy plugin for testing

Test your custom gateway plugin DLL by loading it into Windows Admin Center gateway process.

Windows Admin Center looks for all plugins in a `plugins` folder in the Application Data folder of the current machine (using the CommonApplicationData value of the Environment.SpecialFolder enumeration). On Windows 10, this location is `C:\ProgramData\Server Management Experience`. If the `plugins` folder doesn't exist yet, you can create the folder yourself.

Note

You can override the plugin location in a debug build by updating the "StaticsFolder" configuration value. If you're debugging locally, this setting is in the App.Config of the Desktop solution.

Inside the plugins folder (in this example, `C:\ProgramData\Server Management Experience\plugins`)

- Create a new folder with the same name as the `Name` property value of the `Feature` in your custom gateway plugin DLL (in our sample project, the `Name` is "Sample Uno")
- Copy your custom gateway plugin DLL file to this new folder
- Restart the Windows Admin Center process

After the Windows Admin process restarts, you'll be able to exercise the APIs in your custom gateway plugin DLL by issuing a GET, PUT, PATCH, DELETE, or POST to `http(s)://{domain|localhost}/api/nodes/{node}/features/{feature name}/{identifier}`

### Optional: Attach to plugin for debugging

In Visual Studio 2017, from the Debug menu, select "Attach to Process." In the next window, scroll through the Available Processes list and select SMEDesktop.exe, then select "Attach." Once the debugger starts, you can place a breakpoint in your feature code, and then exercise through the URL format. For our sample project (feature name: "Sample Uno") the URL is: `"<http://localhost:6516/api/nodes/fake-server.my.domain.com/features/Sample%20Uno>"`

## Create a tool extension with the Windows Admin Center SDK

Now we need to create a tool extension from which you can call your custom gateway plugin. Create or browse to a folder where you want to store your project files, open a command prompt, and set that folder as the working directory. Using the Windows Admin Center SDK that was installed earlier, create a new extension with the following syntax:

```
wac create --company "{!Company Name}" --tool "{!Tool Name}"
```

| Value | Explanation | Example |
| --- | --- | --- |
| `{!Company Name}` | Your company name (with spaces) | `Contoso Inc` |
| `{!Tool Name}` | Your tool name (with spaces) | `Manage Foo Works` |

Here's an example usage:

```
wac create --company "Contoso Inc" --tool "Manage Foo Works"
```

This command creates a new folder inside the current working directory using the name you specified for your tool, copies all the necessary template files into your project, and configures the files with your company and tool name.

Next, change directory into the folder, then install required local dependencies by running the following command:

```
npm install
```

Once this command completes, you're set up with everything you need to load your new extension into Windows Admin Center.

## Connect your tool extension to your custom gateway plugin

Now that you've created an extension with the Windows Admin Center SDK, you're ready to connect your tool extension to your custom gateway plugin, by following these steps:

- Add an [empty module](guides/add-module)
- Use your [custom gateway plugin](guides/use-custom-gateway-plugin) in your tool extension

## Build and side load your extension

Next, build and side load your extension into Windows Admin Center. Open a command window, change directory to your source directory, then you're ready to build.

- Build and serve with gulp:

    ```
    gulp build
    gulp serve -p 4201
    ```

The port you choose must currently be free. Make sure you don't attempt to use the port that Windows Admin Center is running on.

Your project can be side loaded into a local instance of Windows Admin Center for testing by attaching the locally served project into Windows Admin Center.

- Launch Windows Admin Center in a web browser
- Open the debugger (F12)
- Open the Console and type the following command:

    ```
    MsftSme.sideLoad("http://localhost:4201")
    ```
- Refresh the web browser

Your project will now be visible in the Tools list with (side loaded) next to the name.

## Target a different version of the Windows Admin Center SDK

Keeping your extension up to date with SDK changes and platform changes is easy. Read about how to [target a different version](target-sdk-version) of the Windows Admin Center SDK.