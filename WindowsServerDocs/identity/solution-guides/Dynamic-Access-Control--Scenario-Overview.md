---
layout: Conceptual
title: Dynamic Access Control Scenario Overview | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/solution-guides/dynamic-access-control--scenario-overview
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: 'Learn more about: Dynamic Access Control: Scenario Overview'
author: robinharwood
ms.author: roharwoo
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: 40e6de04-1a8e-5570-2ab3-75eb89674c85
document_version_independent_id: 87d8753e-a063-db17-3d4f-6f8eedf4b35d
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/solution-guides/Dynamic-Access-Control--Scenario-Overview.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/solution-guides/dynamic-access-control--scenario-overview
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/solution-guides/Dynamic-Access-Control--Scenario-Overview.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/68cb9039-df60-49b0-8ef8-89ad96497f63
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/725b6df3-93e8-472d-834e-e7e0d2953d35
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: c6d7a111-65bc-309a-dfa4-cb85110f3d6a
---

# Dynamic Access Control Scenario Overview | Microsoft Learn

In Windows Server 2012 , you can apply data governance across your file servers to control who can access information and to audit who has accessed information. Dynamic Access Control lets you:

- Identify data by using automatic and manual classification of files. For example, you could tag data in file servers across the organization.
- Control access to files by applying safety-net policies that use central access policies. For example, you could define who can access health information within the organization.
- Audit access to files by using central audit policies for compliance reporting and forensic analysis. For example, you could identify who accessed highly sensitive information.
- Apply Rights Management Services (RMS) protection by using automatic RMS encryption for sensitive Microsoft Office documents. For example, you could configure RMS to encrypt all documents that contain Health Insurance Portability and Accountability Act (HIPAA) information.

The Dynamic Access Control feature set is based on infrastructure investments that can be used further by partners and line-of-business applications, and the features can provide great value for organizations that use Active Directory. This infrastructure includes:

- A new authorization and audit engine for Windows that can process conditional expressions and central policies.
- Kerberos authentication support for user claims and device claims.
- Improvements to the File Classification Infrastructure (FCI).
- RMS extensibility support so partners can provide solutions that encrypt non-Microsoft files.

## In this scenario

The following scenarios and guidance are included as part of this content set:

## Dynamic Access Control Content Roadmap

| Scenario | Evaluate | Plan | Deploy | Operate |
| --- | --- | --- | --- | --- |
| **Scenario: Central Access Policy**<br>Creating Central access policies for files allow organizations to centrally deploy and manage authorization policies that include conditional expressions using user claims, device claims, and resource properties. These polices are based on compliance and business regulatory requirements. These policies are created and hosted in Active Directory, therefore making it easier to manage and deploy.<br><br>**Deploying Claims Across Forests**<br><br>In Windows Server 2012 , the AD DS maintains a 'claims dictionary' in each forest and all claim types in use within the forest are defined at the Active Directory forest level. There are many scenarios where a principal may need to traverse a trust boundary. This scenario describes how a claim traverses a trust boundary. | [Dynamic Access Control: Scenario Overview](dynamic-access-control--scenario-overview)<br>[Deploy Claims Across Forests](deploy-claims-across-forests) | [Plan: A Central Access Policy Deployment](assetId:///0311a76d-d66c-4ddb-ade6-af586a2ad82f)<br>- [Process to map a business request to a central access policy](assetId:///0311a76d-d66c-4ddb-ade6-af586a2ad82f#BKMK_1)- [Delegating of administration for Dynamic Access Control](assetId:///0311a76d-d66c-4ddb-ade6-af586a2ad82f#BKMK_3.1)- [Exception Mechanisms for Planning Central Access Policies](assetId:///0311a76d-d66c-4ddb-ade6-af586a2ad82f#BKMK_3.2)<br><br>Best Practices for Using User Claims<br><br>- [Choosing the right configuration to enable claims in your user domain](assetId:///0311a76d-d66c-4ddb-ade6-af586a2ad82f#BKMK_DC_OP3)- [Operations to enable user claims](assetId:///0311a76d-d66c-4ddb-ade6-af586a2ad82f#BKMK_3.4.2)- [Considerations for using user claims in the file server discretionary ACLs without using Central Access Policies](assetId:///0311a76d-d66c-4ddb-ade6-af586a2ad82f#BKMK_5)<br><br>[Using Device Claims and Device Security Groups](assetId:///0311a76d-d66c-4ddb-ade6-af586a2ad82f#BKMK_DeviceClaims)<br><br>- [Considerations for using static device claims](assetId:///0311a76d-d66c-4ddb-ade6-af586a2ad82f#BKMK_4.1)- [Operations to enable device claims](assetId:///0311a76d-d66c-4ddb-ade6-af586a2ad82f#BKMK_4.3)<br><br>Tools for Deployment<br><br>- | [Deploy a Central Access Policy (Demonstration Steps)](deploy-a-central-access-policy--demonstration-steps-)<br>[Deploy Claims Across Forests (Demonstration Steps)](deploy-claims-across-forests--demonstration-steps-) | - Modeling a central access policy |
| **Scenario: File Access Auditing**<br>Security auditing is one of the most powerful tools to help maintain the security of an enterprise. One of the key goals of security audits is regulatory compliance. For example, industry standards such as Sarbanes Oxley, HIPAA, and Payment Card Industry (PCI) require enterprises to follow a strict set of rules related to data security and privacy. Security audits help establish the presence or absence of such policies; thereby, they prove compliance or noncompliance with these standards. Additionally, security audits help detect anomalous behavior, identify and mitigate gaps in security policy, and deter irresponsible behavior by creating a record of user activity that can be used for forensic analysis. | [Scenario: File Access Auditing](scenario--file-access-auditing) | [Plan for File Access Auditing](plan-for-file-access-auditing) | [Deploy Security Auditing with Central Audit Policies (Demonstration Steps)](deploy-security-auditing-with-central-audit-policies--demonstration-steps-) | - [Monitor the Central Access Policies that Apply on a File Server](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj574188%28v=ws.11%29)- [Monitor the Central Access Policies Associated with Files and Folders](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj574198%28v=ws.11%29)- [Monitor the Resource Attributes on Files and Folders](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj574208%28v=ws.11%29)- [Monitor Claim Types](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj574086%28v=ws.11%29)- [Monitor User and Device Claims During Sign-in](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj574082%28v=ws.11%29)- [Monitor Central Access Policy and Rule Definitions](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj574115%28v=ws.11%29)- [Monitor Resource Attribute Definitions](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj574155%28v=ws.11%29)- [Monitor the Use of Removable Storage Devices](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj574128%28v=ws.11%29). |
| **Scenario: Access-Denied Assistance**<br>Today, when users try to access a remote file on the file server, the only indication that they would get is that access is denied. This generates requests to helpdesk or IT administrators that need to figure out what the issue is and often the administrators have a hard time getting the appropriate context from users which makes it harder to resolve the issue. In Windows Server 2012 , the goal is to try and help the information worker and business owner of the data to deal with the access denied issue before IT gets involved and when IT gets involved, provide all the right information for a quick resolution. One of the challenges in achieving this goal is that there is no central way to deal with access denied and every application deals with it differently and thus in Windows Server 2012 , one of the goals is to improve the access-denied experience for Windows Explorer. | [Scenario: Access-Denied Assistance](scenario--access-denied-assistance) | [Plan for Access-Denied Assistance](assetId:///b169f0a4-8b97-4da8-ae4a-c8f1986d19e1)<br>- [Determine the access-denied assistance model](assetId:///b169f0a4-8b97-4da8-ae4a-c8f1986d19e1#BKMK_1.1)- [Determine who should handle access requests](assetId:///b169f0a4-8b97-4da8-ae4a-c8f1986d19e1#BKMK_12)- [Customize the access-denied assistance message](assetId:///b169f0a4-8b97-4da8-ae4a-c8f1986d19e1#BKMK_13)- [Plan for exceptions](assetId:///b169f0a4-8b97-4da8-ae4a-c8f1986d19e1#BKMK_1.4)- [Determine how access-denied assistance is deployed](assetId:///b169f0a4-8b97-4da8-ae4a-c8f1986d19e1#BKMK_1.5) | [Deploy Access-Denied Assistance (Demonstration Steps)](deploy-access-denied-assistance--demonstration-steps-) |  |
| **Scenario: Classification-Based Encryption for Office Documents**<br>Protection of sensitive information is mainly about mitigating risk for the organization. Various compliance regulations, such as HIPAA or Payment Card Industry Data Security Standard (PCI-DSS), dictate encryption of information, and there are numerous business reasons to encrypt sensitive business information. However, encrypting information is expensive, and it might impair business productivity. Thus, organizations tend to have different approaches and priorities for encrypting their information. To support this scenario, Windows Server 2012 provides the ability to automatically encrypt sensitive Windows Office files based on their classification. This is done through file management tasks that invoke Active Directory Rights Management Server (AD RMS) protection for sensitive documents a few seconds after the file is identified as being a sensitive file on the file server. | [Scenario: Classification-Based Encryption for Office Documents](scenario--classification-based-encryption-for-office-documents) | [Plan to deploy for classification-based encryption of documents](assetId:///14714ba6-d6a2-45e4-aae5-d3318817e52a) | [Deploy Encryption of Office Files (Demonstration Steps)](deploy-encryption-of-office-files--demonstration-steps-) |  |
| **Scenario: Get Insight into Your Data by Using Classification**<br>Reliance on data and storage resources has continued to grow in importance for most organizations. IT administrators face the growing challenge of overseeing larger and more complex storage infrastructures while simultaneously being tasked with the responsibility to ensure total cost of ownership is maintained at reasonable levels. Managing storage resources is not just about the volume or availability of data anymore, but also about the enforcement of company policies and knowing how storage is consumed to enable efficient utilization and compliance to mitigate risk. File Classification Infrastructure provides insight into your data by automating classification processes so that you can manage your data more effectively. The following classification methods are available with File Classification Infrastructure: manual, programmatically, and automatic. This scenario focuses on the automatic file classification method. | [Scenario: Get Insight into Your Data by Using Classification](scenario--get-insight-into-your-data-by-using-classification) | [Plan for Automatic File Classification](assetId:///e3c3bb4b-3034-42b7-b391-8ef5f5851955) | [Deploy Automatic File Classification (Demonstration Steps)](deploy-automatic-file-classification--demonstration-steps-) |  |
| **Scenario: Implement Retention of Information on File Servers**<br>A retention period is the amount of time that a document should be kept before it is expired. Depending on the organization, the retention period can be different. You can classify files in a folder as having a short, medium, or long-term retention period and then assign the timeframe for each period. You may want to keep a file indefinitely by putting it on legal hold. File Classification Infrastructure and File Server Resource Manager uses file management tasks and file classification to apply retention periods for a set of files. You can assign a retention period on a folder and then use a file management task to configure how long an assigned retention period is to last. When the files in the folder are about to expire, the owner of the file gets a notification email. You can also classify a file as being on legal hold so that the file management task will not expire the file. | [Scenario: Implement Retention of Information on File Servers](scenario--implement-retention-of-information-on-file-servers) | [Plan for Retention of Information on File Servers](assetId:///edf13190-7077-455a-ac01-f534064a9e0c) | [Deploy Implementing Retention of Information on File Servers (Demonstration Steps)](deploy-implementing-retention-of-information-on-file-servers--demonstration-steps-) |  |

Note

Dynamic Access Control is not supported on ReFS (Resilient File System).