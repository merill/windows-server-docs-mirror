---
layout: Conceptual
title: Locks and limits in Windows Server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/get-started/locks-limits
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: getting-started
ms.update-cycle: 365-days
description: In this article, you can compare the operating system locks and limits across the different editions of Windows Server.
ms.topic: product-comparison
author: robinharwood
ms.author: roharwoo
ms.date: 2025-06-27T00:00:00.0000000Z
zone_pivot_groups: windows-os-version
locale: en-us
document_id: b7367fa3-3f82-7dd4-1e7d-cd4fa0f96366
document_version_independent_id: b7367fa3-3f82-7dd4-1e7d-cd4fa0f96366
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/get-started/locks-limits.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: get-started/locks-limits
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/get-started/locks-limits.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 95b23455-97bc-df35-8c4b-ac80e278645a
---

# Locks and limits in Windows Server | Microsoft Learn

Choosing the right edition of Windows Server is essential for meeting your organization's technical and business requirements. This article provides a side-by-side comparison of key operating system locks and limits across supported Windows Server editions. Use these tables to compare key features across Windows Server editions, such as:

- Maximum number of users
- Connection limits
- Virtualization rights
- Hardware support

This information can help you choose the version that best fits your needs.

Select a Windows Server release to view its locks and limits.

## Locks and limits

::: zone pivot="windows-server-2025"

To view the locks and limits for Windows Server 2025, select the full comparison tab or the version differences tab.

# [Full Comparison](#tab/full-comparison)
| Locks and limits | Windows Server 2025 Standard | Windows Server 2025 Datacenter | Windows Server 2025 Datacenter: Azure Edition |
| --- | --- | --- | --- |
| Maximum number of users | Based on CALs | Based on CALs | Based on CALs |
| Maximum SMB connections | 16,777,216 | 16,777,216 | 16,777,216 |
| Maximum RRAS connections | Unlimited | Unlimited | Unlimited |
| Maximum IAS connections | 2,147,483,647 | 2,147,483,647 | 2,147,483,647 |
| Maximum RDS connections | 65,535 | 65,535 | 65,535 |
| Maximum number of 64-bit sockets | 64 | 64 | 64 |
| Maximum number of cores | Unlimited | Unlimited | 2,048 logical processors |
| Maximum RAM | - 4 PB for hosts that support 5-level paging<br>- 256 TB for hosts that support 4-level paging | - 4 PB for hosts that support 5-level paging<br>- 256 TB for hosts that support 4-level paging | - 240 TB for a generation 2 virtual machine<br>- 1 TB for a generation 1 virtual machine |
| Can be used as virtualization guest | Yes; 2 virtual machines, plus one Hyper-V host per license | Yes; **unlimited virtual machines**, plus one Hyper-V host per license | Yes; **unlimited virtual machines**, plus one Hyper-V host per license |
| Windows Server Containers | Unlimited | Unlimited | Unlimited |
| Virtual OSE/Hyper-V isolated Containers | 2 | Unlimited | Unlimited |
| Windows Server Containers | Unlimited Windows containers and up to two Hyper-V containers | Unlimited Windows containers and Hyper-V containers | Unlimited Windows containers and Hyper-V containers |
| Storage Replica | 1 partnership and 1 resource group with a single 2TB volume | **Unlimited** | **Unlimited** |

# [Version Differences](#tab/version-differences)
| Locks and limits | Windows Server 2025 Standard | Windows Server 2025 Datacenter | Windows Server 2025 Datacenter: Azure Edition |
| --- | --- | --- | --- |
| Maximum number of cores | Unlimited | Unlimited | 2,048 logical processors |
| Maximum RAM | - 4 PB for hosts that support 5-level paging<br>- 256 TB for hosts that support 4-level paging | - 4 PB for hosts that support 5-level paging<br>- 256 TB for hosts that support 4-level paging | - 240 TB for a generation 2 virtual machine<br>- 1 TB for a generation 1 virtual machine |
| Can be used as virtualization guest | Yes; 2 virtual machines, plus one Hyper-V host per license | Yes; **unlimited virtual machines**, plus one Hyper-V host per license | Yes; **unlimited virtual machines**, plus one Hyper-V host per license |
| Virtual OSE/Hyper-V isolated Containers | 2 | Unlimited | Unlimited |
| Windows Server Containers | Unlimited Windows containers and up to two Hyper-V containers | Unlimited Windows containers and Hyper-V containers | Unlimited Windows containers and Hyper-V containers |
| Storage Replica | 1 partnership and 1 resource group with a single 2TB volume | **Unlimited** | **Unlimited** |

---

::: zone-end

::: zone pivot="windows-server-2022"

To view the locks and limits for Windows Server 2022, select the full comparison tab or the version differences tab.

# [Full Comparison](#tab/full-comparison)
| Locks and limits | Windows Server 2022 Standard | Windows Server 2022 Datacenter | Windows Server 2022 Datacenter: Azure Edition |
| --- | --- | --- | --- |
| Maximum number of users | Based on CALs | Based on CALs | Based on CALs |
| Maximum SMB connections | 16,777,216 | 16,777,216 | 16,777,216 |
| Maximum RRAS connections | Unlimited | Unlimited | Unlimited |
| Maximum IAS connections | 2,147,483,647 | 2,147,483,647 | 2,147,483,647 |
| Maximum RDS connections | 65,535 | 65,535 | 65,535 |
| Maximum number of 64-bit sockets | 64 | 64 | 64 |
| Maximum number of cores | Unlimited | Unlimited | 1,024 logical processors |
| Maximum RAM | - 4 PB for hosts that support 5-level paging<br>- 256 TB for hosts that support 4-level paging | - 4 PB for hosts that support 5-level paging<br>- 256 TB for hosts that support 4-level paging | - 240 TB for a generation 2 virtual machine<br>- 1 TB for a generation 1 virtual machine |
| Can be used as virtualization guest | Yes; 2 virtual machines, plus one Hyper-V host per license | Yes; **unlimited virtual machines**, plus one Hyper-V host per license | Yes; **unlimited virtual machines**, plus one Hyper-V host per license |
| Windows Server Containers | Unlimited | Unlimited | Unlimited |
| Virtual OSE/Hyper-V isolated Containers | 2 | Unlimited | Unlimited |
| Windows Server Containers | Unlimited Windows containers and up to two Hyper-V containers | Unlimited Windows containers and Hyper-V containers | Unlimited Windows containers and Hyper-V containers |
| Storage Replica | 1 partnership and 1 resource group with a single 2TB volume | **Unlimited** | **Unlimited** |

# [Version Differences](#tab/version-differences)
| Locks and limits | Windows Server 2022 Standard | Windows Server 2022 Datacenter | Windows Server 2022 Datacenter: Azure Edition |
| --- | --- | --- | --- |
| Can be used as virtualization guest | Yes; 2 virtual machines, plus one Hyper-V host per license | Yes; **unlimited virtual machines**, plus one Hyper-V host per license | Yes; **unlimited virtual machines**, plus one Hyper-V host per license |
| Virtual OSE/Hyper-V isolated Containers | 2 | Unlimited | Unlimited |
| Windows Server Containers | Unlimited Windows containers and up to two Hyper-V containers | Unlimited Windows containers and Hyper-V containers | Unlimited Windows containers and Hyper-V containers |
| Storage Replica | 1 partnership and 1 resource group with a single 2TB volume | **Unlimited** | **Unlimited** |

---

::: zone-end

::: zone pivot="windows-server-2019"

To view the locks and limits for Windows Server 2019, select the full comparison tab or the version differences tab.

# [Full Comparison](#tab/full-comparison)
| Locks and limits | Windows Server 2019 Standard | Windows Server 2019 Datacenter |
| --- | --- | --- |
| Maximum number of users | Based on CALs | Based on CALs |
| Maximum SMB connections | 16,777,216 | 16,777,216 |
| Maximum RRAS connections | Unlimited | Unlimited |
| Maximum IAS connections | 2,147,483,647 | 2,147,483,647 |
| Maximum RDS connections | 65,535 | 65,535 |
| Maximum number of 64-bit sockets | 64 | 64 |
| Maximum number of cores | Unlimited | Unlimited |
| Maximum RAM | 24 TB | 24 TB |
| Can be used as virtualization guest | Yes; 2 virtual machines, plus one Hyper-V host per license | Yes; **unlimited virtual machines**, plus one Hyper-V host per license |
| Windows Server Containers | Unlimited Windows containers and up to two Hyper-V containers | Unlimited Windows containers and Hyper-V containers |

# [Version Differences](#tab/version-differences)
| Locks and limits | Windows Server 2019 Standard | Windows Server 2019 Datacenter |
| --- | --- | --- |
| Can be used as virtualization guest | Yes; 2 virtual machines, plus one Hyper-V host per license | Yes; **unlimited virtual machines**, plus one Hyper-V host per license |
| Windows Server Containers | Unlimited Windows containers and up to two Hyper-V containers | Unlimited Windows containers and Hyper-V containers |

---

::: zone-end

::: zone pivot="windows-server-2016"

To view the locks and limits for Windows Server 2016, select the full comparison tab or the version differences tab.

# [Full Comparison](#tab/full-comparison)
| Locks and limits | Windows Server 2016 Standard | Windows Server 2016 Datacenter |
| --- | --- | --- |
| Maximum number of users | Based on CALs | Based on CALs |
| Maximum SMB connections | 16,777,216 | 16,777,216 |
| Maximum RRAS connections | Unlimited | Unlimited |
| Maximum IAS connections | 2,147,483,647 | 2,147,483,647 |
| Maximum RDS connections | 65,535 | 65,535 |
| Maximum number of 64-bit sockets | 64 | 64 |
| Maximum number of cores | Unlimited | Unlimited |
| Maximum RAM | 24 TB | 24 TB |
| Can be used as virtualization guest | Yes; 2 virtual machines, plus one Hyper-V host per license | Yes; **unlimited virtual machines**, plus one Hyper-V host per license |

# [Version Differences](#tab/version-differences)
| Locks and limits | Windows Server 2016 Standard | Windows Server 2016 Datacenter |
| --- | --- | --- |
| Can be used as virtualization guest | Yes; 2 virtual machines, plus one Hyper-V host per license | Yes; **unlimited virtual machines**, plus one Hyper-V host per license |

---

::: zone-end