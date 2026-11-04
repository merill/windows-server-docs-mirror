---
layout: Conceptual
title: Create the First Federation Server in a Federation Server Farm | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/deployment/create-the-first-federation-server-in-a-federation-server-farm
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Create the First Federation Server in a Federation Server Farm'
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: install-set-up-deploy
locale: en-us
document_id: 30ec9561-93e8-ecb1-b6b0-7df59d37b91a
document_version_independent_id: 1129bbdc-260c-0248-229f-a268627aeb09
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/deployment/Create-the-First-Federation-Server-in-a-Federation-Server-Farm.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/deployment/create-the-first-federation-server-in-a-federation-server-farm
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/deployment/Create-the-First-Federation-Server-in-a-Federation-Server-Farm.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: d358bbfe-af14-7054-a5b8-3bd0e6908c8f
---

# Create the First Federation Server in a Federation Server Farm | Microsoft Learn

After you install the Federation Service role service and configure the required certificates on a computer, you are ready to configure the computer to become a federation server. You can use the following procedure to set up the computer to become the first federation server in a new federation server farm using the AD FS Federation Server Configuration Wizard.

The act of creating the first federation server in a farm also creates a new Federation Service and makes this computer the primary federation server. This means that this computer will be configured with a read/write copy of the AD FS configuration database. All other federation servers in this farm must replicate any changes that are made on the primary federation server to their read-only copies of the AD FS configuration database that they store locally. For more information about this replication process, see [The Role of the AD FS Configuration Database](../technical-reference/the-role-of-the-ad-fs-configuration-database).

Note

For the Federated Web Single-Sign-On (SSO) design, you must have at least one federation server in the account partner organization and at least one federation server in the resource partner organization. For more information, see [Where to Place a Federation Server](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dd807127%28v=ws.11%29).

Membership in Domain Admins, or a delegated domain account that has been granted write access to the Program Data container in Active Directory, is the minimum required to complete this procedure.

### To create the first federation server in a federation server farm

1. There are two ways to start the AD FS Federation Server Configuration Wizard. To start the wizard, do one of the following:

    - After the Federation Service role service installation is complete, open the AD FS Management snap-in and click the **AD FS Federation Server Configuration Wizard** link on the **Overview** page or in the **Actions** pane.
    - Any time after the setup wizard is complete, open Windows Explorer, navigate to the **C:\Windows\ADFS** folder, and then double-click **FsConfigWizard.exe**.
2. On the **Welcome** page, verify that **Create a new Federation Service** is selected, and then click **Next**.
3. On the **Select Stand-Alone or Farm Deployment** page, click **New federation server farm**, and then click **Next**.
4. On the **Specify the Federation Service Name** page, verify that the **SSL certificate** that is showing is correct. If this is not the correct certificate, select the appropriate certificate from the **SSL certificate** list.

    This certificate is generated from the Secure Sockets Layer (SSL) settings for the Default Web Site. If the Default Web Site has only one SSL certificate configured, that certificate is presented and automatically selected for use. If multiple SSL certificates are configured for the Default Web Site, all those certificates are listed here and you must select from among them. If there are no SSL settings configured for the Default Web Site, the list is generated from the certificates that are available in the personal certificates store on the local computer.

    Note

    The wizard will not allow you to override the certificate if an SSL certificate is configured for IIS. This ensures that any intended prior IIS configuration for SSL certificates is preserved. To work around this restriction, you can remove the certificate or reconfigure it manually with the IIS Management Console.
5. If the AD FS database that you selected already exists, the **Existing AD FS Configuration Database Detected** page appears. If that page appears, click **Delete database**, and then click **Next**.

Caution

Select this option only when you are sure that the data in this AD FS database is not important or that it is not used in a production federation server farm.
6. On the **Specify a Service Account** page, click **Browse**. In the **Browse** dialog box, locate the domain account that will be used as the service account in this new federation server farm, and then click **OK**. Type the password for this account, confirm it, and then click **Next**.

    Note

    See [Manually Configure a Service Account for a Federation Server Farm](manually-configure-a-service-account-for-a-federation-server-farm) for more information about specifying a service account for a federation server farm. Each federation server in the federation server farm must specify the same service account for the farm to be operational. For example, if the service account that was created was contoso\ADFS2SVC, each computer that you configure for the federation server role and that will participate in the same farm must specify contoso\ADFS2SVC at this step in the Federation Server Configuration Wizard for the farm to be operational.
7. On the **Ready to Apply Settings** page, review the details. If the settings appear to be correct, click **Next** to begin configuring AD FS with these settings.
8. On the **Configuration Results** page, review the results. When all the configuration steps are finished, click **Close** to exit the wizard.

    Important

    For secure deployment purposes, artifact resolution and reply detection are disabled when you use the AD FS Federation Server Configuration Wizard to configure a federation server farm. This wizard automatically configures the Windows Internal Database for storing service configuration data. You might, however, mistakenly undo this change by enabling the Artifact Resolution endpoint using either the **Endpoints** node in the AD FS Management snap-in or the Enable-ADFSEndpoint cmdlet in Windows PowerShell. Be careful to not reconfigure the default setting so that this endpoint remains disabled when you use a federation server farm and the Windows Internal Database together.

## Additional references

[Checklist: Setting Up a Federation Server](checklist--setting-up-a-federation-server)