---
layout: Conceptual
title: Install a policy module with the Network Device Enrollment Service in Windows Server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-cs/install-policy-module-network-device-enrollment-service
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: Learn how to install, configure, and uninstall a policy module with the Network Device Enrollment Service.
author: robinharwood
ms.topic: how-to
ms.author: roharwoo
ms.date: 2025-03-27T00:00:00.0000000Z
locale: en-us
document_id: dda2915d-7e73-dbee-72fb-832c36a859d6
document_version_independent_id: dda2915d-7e73-dbee-72fb-832c36a859d6
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-cs/install-policy-module-network-device-enrollment-service.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-cs/install-policy-module-network-device-enrollment-service
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-cs/install-policy-module-network-device-enrollment-service.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: 096bdd89-f1fe-7015-13c4-6db668c77ff0
---

# Install a policy module with the Network Device Enrollment Service in Windows Server | Microsoft Learn

[Network Device Enrollment Service(NDES) for Active Directory Certificate Services](/en-us/windows-server/identity/ad-cs/network-device-enrollment-service-overview) support a policy module that provides extra security for the Simple Certificate Enrollment Protocol (SCEP). Using a policy module the NDES requires extra authentication to ensure that the certificate is issued to the right user.

This article covers how-to install and configure a policy module with the Network Device Enrollment Service (NDES).

## Prerequisites

- NDES role service is installed
- NDES is configured
- Read [Use a policy module with Network Device Enrollment Service](/en-us/windows-server/identity/ad-cs/use-policy-module-with-network-device-enrollment-service)

## How to install and uninstall the policy module

Before you can install the policy module, you must first install and configure NDES, and verify that the service communicate successfully with an issuing certification authority.

If you have a software solution that includes the policy module, follow the installation and configuration instructions for the software rather than the instructions in this section. For example, Configuration Manager provides its own wizard, and the Configuration Manager Policy Module Setup wizard, to install and configure the policy module.

If there are no accompanying instructions, or you developed your own policy module, use the following steps.

### Install and configure the policy module

1. Copy the .dll file for the policy module onto the server that runs the NDES.
2. Register the policy module by using the Regsvr32.exe command from an elevated command prompt.

    For example, if your policy module is named ndespol.dll, type **Regsvr32 ndespol.dll** and press ENTER.
3. Run the following Windows PowerShell cmdlets to update the registry path HKEY\_LOCAL\_MACHINE\SOFTWARE\Microsoft\Cryptography\MSCEP:

    ```powershell
    Invoke-Item -Path HKLM:\SOFTWARE\Microsoft\Cryptography\MSCEP\Modules
    ```

    This command creates the new \Modules key.

    ```powershell
    New-ItemProperty HKLM:\SOFTWARE\Microsoft\Cryptography\MSCEP\Modules\ -Name Policy -PropertyType String -Value "NDESPolicy.OTA.1"
    ```

    This command specifies the policy module name, using **NDESPolicy.OTA.1** as an example. Replace **NDESPolicy.OTA.1** with the name of your own policy module.
4. Restart Internet Information Services (IIS) by typing **IISReset** from an elevated command prompt.

NDES supports only one registered policy module. After you register it, it's always used with NDES. To remove the policy module, manually uninstall it by updating the registry and unregistering the policy module.

Important

Removing the NDES role service doesn't uninstall the policy module.

### Uninstall the policy module

1. Run the following Windows PowerShell cmdlet to remove the registry settings:

    ```powershell
    Remove-Item -Path HKLM:\SOFTWARE\Microsoft\Cryptography\MSCEP\Modules -Recurse
    ```
2. From an elevated command prompt, run the regsvr32.exe command with the /u option to unregister the policy module.

    For example, if the policy module name is ndespol.dll, type **regsvr32 ndespol.dll /u** and press ENTER.