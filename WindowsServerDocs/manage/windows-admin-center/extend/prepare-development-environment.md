---
layout: Conceptual
title: Prepare your development environment | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/manage/windows-admin-center/extend/prepare-development-environment
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-admin-center
ms.update-cycle: 365-days
feedback_product_url: https://aka.ms/wacfeedback
description: Preparing your development environment Windows Admin Center SDK (Project Honolulu)
ms.topic: how-to
author: davannaw-msft
ms.author: dawhite
ms.localizationpriority: medium
ms.date: 2026-08-17T00:00:00.0000000Z
locale: en-us
document_id: 3c1ca48c-bed3-ec92-de57-937a96695526
document_version_independent_id: 638dfd52-44a5-a090-7cc6-d72c46cdb8a9
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/manage/windows-admin-center/extend/prepare-development-environment.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: manage/windows-admin-center/extend/prepare-development-environment
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/manage/windows-admin-center/extend/prepare-development-environment.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: c1d2ee7c-55fe-540d-c2b0-2fda094b1f88
---

# Prepare your development environment | Microsoft Learn

Let's get started developing extensions with the Windows Admin Center SDK! In this document, we'll cover the process to get your environment up and running to build and test an extension for Windows Admin Center.

Note

New to the Windows Admin Center SDK? Learn more about [Extensions for Windows Admin Center](extensibility-overview)

Tip

Create a folder to store all your Windows Admin Center extension development files to reduce command execution.

To prepare your development environment, perform the following steps:

## Install prerequisites

To begin developing with the SDK, download and install the following prerequisites:

- [Windows Admin Center](../overview) (GA or preview version)
- Visual Studio or [Visual Studio Code](https://code.visualstudio.com)
- [Node.js version 24.18.1](https://nodejs.org/en/download) (download and install the LTS version)
- [Node Package Manager](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm) (6.14.5 or later)
- [NuGet](https://www.nuget.org/downloads) (for publishing extensions)
- [Git for Windows](https://git-scm.com/install/windows) (includes OpenSSL for generating self-signed certificates)

To bypass signature validation which occurs during extension installation in Windows Admin Center versions running with .NET 8, you should also switch your Windows Admin Center operation mode to "Development." To configure development mode, you must:

- Open your Windows Admin Center instance's `appsettings.json` file. This can be found by default at `C:\Program Files\WindowsAdminCenter\service\appsettings.json`.
- Modify the `OperationMode` field under the `WindowsAdminCenter/System` section to read "Development" instead of "Production."

## Install global dependencies

Next, install or update dependencies required for your projects by using Node Package Manager. Install these dependencies globally so all projects can access them.

```powershell
npm install -g @angular/cli@20.3.25

npm install -g gulp
npm install -g typescript
npm install -g eslint
npm install -g @microsoft/windows-admin-center-sdk@latest
```

Note

You can install a later version of `@angular/cli`. However, if you install a version greater than 20.3.25, you see a warning during the gulp build step that the local CLI version doesn't match the installed version.

## Prepare your environment for sideloading

After you create your extension, you want to sideload it in Windows Admin Center for testing. To do so, perform the following one-time steps for your extension development directory:

1. Open PowerShell **as an administrator** and create a certificate directory: 

    ```powershell
    New-Item -ItemType Directory -Path "C:<path>\certificate"
    ```
2. Generate a self-signed certificate by using Git's OpenSSL: 

    ```powershell
    & "C:\Program Files\Git\usr\bin\openssl.exe" req -x509 -newkey rsa:2048 -nodes -keyout C:\<path-to-extension-directory>\certificate\localhost.key -out C:\<path-to-extension-directory>\certificate\localhost.cert -days 365 -subj "/CN=localhost" -addext "subjectAltName=DNS:localhost"
    ```
3. Import the new certificate into your Trusted Root: 

    ```powershell
     Import-Certificate -FilePath "C:\<path-to-extension-directory>\certificate\localhost.cert" -CertStoreLocation "Cert:\LocalMachine\Root"
    ```
4. Open `C:\Program Files\WindowsAdminCenter\Service\appsettings.json` in Visual Studio Code as administrator.
5. Find the `corsSites` array and add the sideloading URL (port 4200 is the default). 

    ```json
     "CorsSites": [
       "https://localhost:4200"
     ]
    ```
6. Find the `CSPFrameAncestors` array and add the sideloading URL (port 4200 is the default). 

    ```json
     "CSPFrameAncestors": [
       "'self'",
       ... existing entries ...
       "https://localhost:4200"
     ]
    ```
7. Save the file, and then restart the Windows Admin Center service in your administrator PowerShell window by running: 

    ```powershell
      Restart-Service WindowsAdminCenter
    ```

Important

These instructions reference self-signed certificates for development and testing. Don't use self-signed certificates on production machines for production workloads.

### Sideloading by using fully qualified domain name

To sideload your Windows Admin Center extension through a URL that includes your machine's fully qualified domain name (FQDN), follow these additional configuration steps:

1. Use Git's OpenSSL to generate a self-signed certificate that contains subject alternate names for both `localhost` and the FQDN: 

    ```powershell
    & "C:\Program Files\Git\usr\bin\openssl.exe" req -x509 -newkey rsa:2048 -nodes -keyout C:\<path-to-extension-directory>\certificate\localhost.key -out C:\<path-to-extension-directory>\certificate\localhost.cert -days 365 -subj "/CN=localhost" -addext "subjectAltName=DNS:localhost,DNS:<FQDN>"
    ```
2. Import the new certificate into your Trusted Root: 

    ```powershell
     Import-Certificate -FilePath "C:\<path-to-extension-directory>\certificate\localhost.cert" -CertStoreLocation "Cert:\LocalMachine\Root"
    ```
3. Update `C:\Program Files\WindowsAdminCenter\Service\appsettings.json` to include URLs with the FQDN origin: 

    ```json
     "CorsSites": [
       "https://localhost:4200",
       "https://<FQDN>:4200"
     ],
     "CSPFrameAncestors": [
       "'self'",
       ... existing entries ...
       "https://localhost:4200",
       "https://<FQDN>:4200"
     ]
    ```
4. Save the file, and then restart the Windows Admin Center service in your administrator PowerShell window by running: 

    ```powershell
      Restart-Service WindowsAdminCenter
    ```