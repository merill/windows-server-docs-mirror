---
layout: Conceptual
title: Fault tolerance and storage efficiency on Azure Local and Windows Server clusters | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/storage-spaces/fault-tolerance
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage-spaces
ms.update-cycle: 1095-days
description: A discussion of resiliency options in Storage Spaces Direct including mirroring and parity.
author: robinharwood
ms.author: roharwoo
ms.topic: concept-article
ms.date: 2023-04-17T00:00:00.0000000Z
locale: en-us
document_id: 0bb04b6e-7fac-4e7f-b78e-b712815010d5
document_version_independent_id: 0bb04b6e-7fac-4e7f-b78e-b712815010d5
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/storage-spaces/fault-tolerance.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/storage-spaces/fault-tolerance
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/storage-spaces/fault-tolerance.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/289b8734-3abd-4162-bc19-e661c3f4c940
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6a94795e-9024-410d-b38e-b67941440893
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
platformId: a463cf12-dc80-e9cf-8df9-0a7e6bba9ced
---

# Fault tolerance and storage efficiency on Azure Local and Windows Server clusters | Microsoft Learn

This article explains the resiliency options available and outlines the scale requirements, storage efficiency, and general advantages and tradeoffs of each.

## Overview

Storage Spaces Direct provides fault tolerance, often called "resiliency," for your data. Its implementation is similar to RAID, except distributed across servers and implemented in software.

As with RAID, there are a few different ways Storage Spaces can do this, which make different tradeoffs between fault tolerance, storage efficiency, and compute complexity. These broadly fall into two categories: "mirroring" and "parity," the latter sometimes called "erasure coding."

## Mirroring

Mirroring provides fault tolerance by keeping multiple copies of all data. This most closely resembles RAID-1. How that data is striped and placed is non-trivial (see [this blog](https://techcommunity.microsoft.com/t5/storage-at-microsoft/deep-dive-the-storage-pool-in-storage-spaces-direct/ba-p/425959) to learn more), but it's absolutely true to say that any data stored using mirroring is written, in its entirety, multiple times. Each copy is written to different physical hardware (different drives in different servers) that are assumed to fail independently.

You can choose between two flavors of mirroring – "two-way" and "three-way."

### Two-way mirror

Two-way mirroring writes two copies of everything. Its storage efficiency is 50 percent – to write 1 TB of data, you need at least 2 TB of physical storage capacity. Likewise, you need at least two [hardware 'fault domains'](/en-us/windows-server/failover-clustering/fault-domains) – with Storage Spaces Direct, that means two servers.

![two-way-mirror](media/fault-tolerance/two-way-mirror-180px.png)

Warning

If you have more than two servers, we recommend using three-way mirroring instead.

### Three-way mirror

Three-way mirroring writes three copies of everything. Its storage efficiency is 33.3 percent – to write 1 TB of data, you need at least 3 TB of physical storage capacity. Likewise, you need at least three hardware fault domains – with Storage Spaces Direct, that means three servers.

Three-way mirroring can safely tolerate at least two hardware problems (drive or server) at a time. For example, if you're rebooting one server when suddenly another drive or server fails, all data remains safe and continuously accessible.

![three-way-mirror](media/fault-tolerance/three-way-mirror-180px.png)

## Parity

Parity encoding, often called "erasure coding," provides fault tolerance using bitwise arithmetic, which can get [remarkably complicated](https://www.microsoft.com/research/wp-content/uploads/2016/02/LRC12-cheng20webpage.pdf). The way this works is less obvious than mirroring, and there are many great online resources (for example, this third-party [Dummies Guide to Erasure Coding](https://smahesh.com/dummies-guide-to-erasure-coding/)) that can help you get the idea. Sufficed to say it provides better storage efficiency without compromising fault tolerance.

Storage Spaces offers two flavors of parity – "single" parity and "dual" parity, the latter employing an advanced technique called "local reconstruction codes" at larger scales.

Important

We recommend using mirroring for most performance-sensitive workloads. To learn more about how to balance performance and capacity depending on your workload, see [Plan volumes](plan-volumes#choosing-the-resiliency-type).

### Single parity

Single parity keeps only one bitwise parity symbol, which provides fault tolerance against only one failure at a time. It most closely resembles RAID-5. To use single parity, you need at least three hardware fault domains – with Storage Spaces Direct, that means three servers. Because three-way mirroring provides more fault tolerance at the same scale, we discourage using single parity. But, it's there if you insist on using it, and it's fully supported.

Warning

We discourage using single parity because it can only safely tolerate one hardware failure at a time: if you're rebooting one server when suddenly another drive or server fails, you will experience downtime. If you only have three servers, we recommend using three-way mirroring. If you have four or more, see the next section.

### Dual parity

Dual parity implements Reed-Solomon error-correcting codes to keep two bitwise parity symbols, thereby providing the same fault tolerance as three-way mirroring (i.e. up to two failures at once), but with better storage efficiency. It most closely resembles RAID-6. To use dual parity, you need at least four hardware fault domains – with Storage Spaces Direct, that means four servers. At that scale, the storage efficiency is 50% – to store 2 TB of data, you need 4 TB of physical storage capacity.

![dual-parity](media/fault-tolerance/dual-parity-180px.png)

The storage efficiency of dual parity increases the more hardware fault domains you have, from 50 percent up to 80 percent. For example, at seven (with Storage Spaces Direct, that means seven servers) the efficiency jumps to 66.7 percent – to store 4 TB of data, you need just 6 TB of physical storage capacity.

![dual-parity-wide](media/fault-tolerance/dual-parity-wide-180px.png)

See the Summary section for the efficiency of dual party and local reconstruction codes at every scale.

### Local reconstruction codes

Storage Spaces introduces an advanced technique developed by Microsoft Research called "local reconstruction codes," or LRC. At large scale, dual parity uses LRC to split its encoding/decoding into a few smaller groups, to reduce the overhead required to make writes or recover from failures.

With hard disk drives (HDD) the group size is four symbols; with solid-state drives (SSD), the group size is six symbols. For example, here's what the layout looks like with hard disk drives and 12 hardware fault domains (meaning 12 servers) – there are two groups of four data symbols. It achieves 72.7 percent storage efficiency.

![local-reconstruction-codes](media/fault-tolerance/local-reconstruction-codes-180px.png)

We recommend this in-depth yet eminently readable walk-through of [how local reconstruction codes handle various failure scenarios, and why they're appealing](https://techcommunity.microsoft.com/t5/storage-at-microsoft/bg-p/FileCAB), by [Claus Joergensen](https://twitter.com/clausjor).

## Mirror-accelerated parity

A Storage Spaces Direct volume can be part mirror and part parity. Writes land first in the mirrored portion and are gradually moved into the parity portion later. Effectively, this is [using mirroring to accelerate erasure coding](https://techcommunity.microsoft.com/t5/storage-at-microsoft/bg-p/FileCAB).

To mix three-way mirror and dual parity, you need at least four fault domains, meaning four servers.

The storage efficiency of mirror-accelerated parity is in between what you'd get from using all mirror or all parity, and depends on the proportions you choose.

Important

We recommend using mirroring for most performance-sensitive workloads. To learn more about how to balance performance and capacity depending on your workload, see [Plan volumes](plan-volumes#choosing-the-resiliency-type).

## Summary

This section summarizes the resiliency types available in Storage Spaces Direct, the minimum scale requirements to use each type, how many failures each type can tolerate, and the corresponding storage efficiency.

### Resiliency types

| Resiliency | Failure tolerance | Storage efficiency |
| --- | --- | --- |
| Two-way mirror | 1 | 50.0% |
| Three-way mirror | 2 | 33.3% |
| Dual parity | 2 | 50.0% - 80.0% |
| Mixed | 2 | 33.3% - 80.0% |

### Minimum scale requirements

| Resiliency | Minimum required fault domains |
| --- | --- |
| Two-way mirror | 2 |
| Three-way mirror | 3 |
| Dual parity | 4 |
| Mixed | 4 |

Tip

Unless you are using [chassis or rack fault tolerance](/en-us/windows-server/failover-clustering/fault-domains), the number of fault domains refers to the number of servers. The number of drives in each server does not affect which resiliency types you can use, as long as you meet the minimum requirements for Storage Spaces Direct.

### Dual parity efficiency for hybrid deployments

This table shows the storage efficiency of dual parity and local reconstruction codes at each scale for hybrid deployments, which contain both hard disk drives (HDD) and solid-state drives (SSD).

| Fault domains | Layout | Efficiency |
| --- | --- | --- |
| 2 | – | – |
| 3 | – | – |
| 4 | RS 2+2 | 50.0% |
| 5 | RS 2+2 | 50.0% |
| 6 | RS 2+2 | 50.0% |
| 7 | RS 4+2 | 66.7% |
| 8 | RS 4+2 | 66.7% |
| 9 | RS 4+2 | 66.7% |
| 10 | RS 4+2 | 66.7% |
| 11 | RS 4+2 | 66.7% |
| 12 | LRC (8, 2, 1) | 72.7% |
| 13 | LRC (8, 2, 1) | 72.7% |
| 14 | LRC (8, 2, 1) | 72.7% |
| 15 | LRC (8, 2, 1) | 72.7% |
| 16 | LRC (8, 2, 1) | 72.7% |

### Dual parity efficiency for all-flash deployments

This table shows the storage efficiency of dual parity and local reconstruction codes at each scale for all-flash deployments, which contain only solid-state drives (SSD). The parity layout can use larger group sizes and achieve better storage efficiency in an all-flash configuration.

| Fault domains | Layout | Efficiency |
| --- | --- | --- |
| 2 | – | – |
| 3 | – | – |
| 4 | RS 2+2 | 50.0% |
| 5 | RS 2+2 | 50.0% |
| 6 | RS 2+2 | 50.0% |
| 7 | RS 4+2 | 66.7% |
| 8 | RS 4+2 | 66.7% |
| 9 | RS 6+2 | 75.0% |
| 10 | RS 6+2 | 75.0% |
| 11 | RS 6+2 | 75.0% |
| 12 | RS 6+2 | 75.0% |
| 13 | RS 6+2 | 75.0% |
| 14 | RS 6+2 | 75.0% |
| 15 | RS 6+2 | 75.0% |
| 16 | LRC (12, 2, 1) | 80.0% |

## Examples

Unless you have only two servers, we recommend using three-way mirroring and/or dual parity, because they offer better fault tolerance. Specifically, they ensure that all data remains safe and continuously accessible even when two fault domains – with Storage Spaces Direct, that means two servers - are affected by simultaneous failures.

### Examples where everything stays online

These six examples show what three-way mirroring and/or dual parity **can** tolerate.

- **1.** One drive lost (includes cache drives)
- **2.** One server lost

![fault-tolerance-examples-1-and-2](media/fault-tolerance/fault-tolerance-example-12.png)

- **3.** One server and one drive lost
- **4.** Two drives lost in different servers

![fault-tolerance-examples-3-and-4](media/fault-tolerance/fault-tolerance-example-34.png)

- **5.** More than two drives lost, so long as at most two servers are affected
- **6.** Two servers lost

![fault-tolerance-examples-5-and-6](media/fault-tolerance/fault-tolerance-example-56.png)

...in every case, all volumes stay online. (Make sure your cluster maintains quorum.)

### Examples where everything goes offline

Over its lifetime, Storage Spaces can tolerate any number of failures, because it restores to full resiliency after each one, given sufficient time. However, at most two fault domains can safely be affected by failures at any given moment. The following are therefore examples of what three-way mirroring and/or dual parity **cannot** tolerate.

- **7.** Drives lost in three or more servers at once
- **8.** Three or more servers lost at once

![fault-tolerance-examples-7-and-8](media/fault-tolerance/fault-tolerance-example-78.png)

## Usage

Check out [Create volumes](create-volumes).