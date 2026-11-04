---
layout: Conceptual
title: Add a module to a tool extension | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/manage/windows-admin-center/extend/guides/add-module
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-admin-center
ms.update-cycle: 365-days
feedback_product_url: https://aka.ms/wacfeedback
description: Develop a tool extension in Windows Admin Center SDK (Project Honolulu) - Add a module to a tool extension.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2023-04-01T00:00:00.0000000Z
locale: en-us
document_id: 509069d6-f50c-b1e3-3212-642ba08ef69e
document_version_independent_id: 4b0f0790-d433-81da-c5e6-dccbfa1a4759
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/manage/windows-admin-center/extend/guides/add-module.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: manage/windows-admin-center/extend/guides/add-module
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/manage/windows-admin-center/extend/guides/add-module.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: 6c50f250-a851-17c0-7a9d-e7adbc12d8be
---

# Add a module to a tool extension | Microsoft Learn

In this article, add an empty module to a tool extension we've created with the Windows Admin Center CLI.

## Prepare your environment

If you haven't already done it, follow the directions in develop a [tool](../develop-tool) (or [solution](../develop-solution)) extension to prepare your environment and create a new, empty tool extension.

## Use the Angular CLI to create a module (and component)

If you're new to Angular, we encourage you to read the documentation on the Angular website to learn about Angular and NgModule. See [NgModule](https://angular.io/guide/ngmodule) for guidance.

To learn more:

- [Generating a new module in Angular CLI](https://github.com/angular/angular-cli/wiki/generate-module).
- [Generating a new component in Angular CLI](https://github.com/angular/angular-cli/wiki/generate-component).

Open a command prompt, change directory to .\src\app in your project, and then run the following commands, replacing `{!ModuleName}` with your module name (spaces removed).

```
cd .\src\app
ng generate module {!ModuleName}
ng generate component {!ModuleName}
```

| Value | Explanation | Example |
| --- | --- | --- |
| `{!ModuleName}` | Your module name (spaces removed) | `ManageFooWorksPortal` |

Example usage:

```powershell
cd .\src\app
ng generate module ManageFooWorksPortal
ng generate component ManageFooWorksPortal
```

## Add routing information

If you're new to Angular, we recommended you learn about Angular Routing and Navigation. The following sections define necessary routing elements that enable Windows Admin Center to navigate to your extension and between views in your extension in response to user activity. To learn more, see the [Router guidance](https://angular.io/guide/router)

Use the same module name that you used in the preceding step.

### Add content to new routing file

1. Browse to the module folder created by `ng generate` in the previous step.
2. Create a new file `{!module-name}.routing.ts`, following this naming convention:

    | Value | Explanation | Example filename |
    | --- | --- | --- |
    | `{!module-name}` | Your module name (lower case, spaces replaced with dashes) | `manage-foo-works-portal.routing.ts` |
3. Add this content to the file created:

    ```ts
    import { NgModule } from '@angular/core';
    import { RouterModule, Routes } from '@angular/router';
    import { {!ModuleName}Component } from './{!module-name}.component';
    
    const routes: Routes = [
        {
            path: '',
            component: {!ModuleName}Component,
            // if the component has child components that need to be routed to, include them in the children array.
            children: [
                {
                    path: '',
                    redirectTo: 'base',
                    pathMatch: 'full'
                }
            ]
    }];
    
    @NgModule({
        imports: [
            RouterModule.forChild(routes)
        ],
        exports: [
            RouterModule
        ]
    })
    export class Routing { }
    ```
4. Replace values in the file created with your desired values:

    | Value | Explanation | Example |
    | --- | --- | --- |
    | `{!ModuleName}` | Your module name (spaces removed) | `ManageFooWorksPortal` |
    | `{!module-name}` | Your module name (lower case, spaces replaced with dashes) | `manage-foo-works-portal` |

### Add content to new module file

1. Open file `{!module-name}.module.ts`, found with the following naming convention:

    | Value | Explanation | Example filename |
    | --- | --- | --- |
    | `{!module-name}` | Your module name (lower case, spaces replaced with dashes) | `manage-foo-works-portal.module.ts` |
2. Add content to the file:

    ```ts
    import { Routing } from './{!module-name}.routing';
    ```
3. Replace values in the content just added with your desired values:

    | Value | Explanation | Example |
    | --- | --- | --- |
    | `{!module-name}` | Your module name (lower case, spaces replaced with dashes) | `manage-foo-works-portal` |
4. Modify the imports statement to import Routing:

    | Original value | New value |
    | --- | --- |
    | `imports: [ CommonModule ]` | `imports: [ CommonModule, Routing ]` |
5. Make sure `import` statements are alphabetized by source.

### Add content to new component TypeScript file

1. Open file `{!module-name}.component.ts`, found with the following naming convention:

    | Value | Explanation | Example filename |
    | --- | --- | --- |
    | `{!module-name}` | Your module name (lower case, spaces replaced with dashes) | `manage-foo-works-portal.component.ts` |
2. Modify content in the file to match the following example.

    ```ts
    constructor() {
        // TODO
    }
    
    public ngOnInit() {
        // TODO
    }
    ```

### Update app-routing.module.ts

1. Open file `app-routing.module.ts`, and modify the default path so it loads the new module you created. Find the entry for `path: ''`, and update `loadChildren` to load your module instead of the default module:

    | Value | Explanation | Example |
    | --- | --- | --- |
    | `{!ModuleName}` | Your module name (spaces removed) | `ManageFooWorksPortal` |
    | `{!module-name}` | Your module name (lower case, spaces replaced with dashes) | `manage-foo-works-portal` |

    ```ts
        {
            path: '',
            loadChildren: 'app/{!module-name}/{!module-name}.module#{!ModuleName}Module'
        },
    ```

    Here's an example of an updated default path:

    ```ts
        {
            path: '',
            loadChildren: 'app/manage-foo-works-portal/manage-foo-works-portal.module#ManageFooWorksPortalModule'
        },
    ```

## Build and side load your extension

You have now added a module to your extension. Next, you can [build and side load](../develop-tool#build-and-side-load-your-extension) your extension in Windows Admin Center to see the results.