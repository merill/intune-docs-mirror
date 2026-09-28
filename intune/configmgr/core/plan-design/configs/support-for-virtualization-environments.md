---
layout: Conceptual
title: Support for virtualization - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/configs/support-for-virtualization-environments
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: configuration-manager
manager: laurawi
feedback_product_url: https://feedbackportal.microsoft.com/feedback/forum/4669adfc-ee1b-ec11-b6e7-0022481f8472
author: sccmavenger
ms.author: dannygu
ms.reviewer:
- umaikhan
- brianhun
- payur
- hugowu
- qiani
description: The requirements for installing Configuration Manager client and site system roles in a virtualization environment.
ms.date: 2026-09-21T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 539358a4-cba0-c9f3-7349-05728da6a997
document_version_independent_id: d23dedbd-3645-9820-199e-4e6fb6ac76a9
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/plan-design/configs/support-for-virtualization-environments.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/plan-design/configs/support-for-virtualization-environments
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/plan-design/configs/support-for-virtualization-environments.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/68ec7f3a-2bc6-459f-b959-19beb729907d
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/90370425-aca4-4a39-9533-d52e5e002a5d
platformId: d5c8519b-375e-1b1d-db67-02e0b5f0aaae
---

# Support for virtualization - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Configuration Manager supports installing the client and site system roles on supported operating systems that run as a virtual machine (VM) in certain virtualization environments. This support exists even when the virtual host (virtualization environment) isn't supported as a client or site server.

For example, you use Microsoft Hyper-V Server 2016 to host a VM that runs Windows Server 2019. You can install the client or site system roles on the VM running Windows Server 2019. You can't install the client on the host running Microsoft Hyper-V Server 2016.

## Virtualization environments

- Windows Server 2022 (*starting in version 2107*)
- Windows Server 2019
- Windows Server 2016 ^Note 1^
- Microsoft Hyper-V Server 2016 ^Note 1^

Note

Configuration Manager doesn't support [nested virtualization](/en-us/windows-server/virtualization/hyper-v/What-s-new-in-Hyper-V-on-Windows#nested-virtualization-new), which is new with Windows Server 2016.

### Virtualization environment support

Each virtual computer needs the same or greater hardware and software requirements that you would use for a physical Configuration Manager computer.

To validate that Configuration Manager supports your virtualization environment, use the Server Virtualization Validation Program. It includes an online Virtualization Program Support Policy Wizard. For more information, see [Windows Server Virtualization Validation Program](https://www.windowsservercatalog.com/svvp/program-home).

Configuration Manager can't manage VMs if they're offline. The Configuration Manager client on the host computer can't manage an offline VM image. For example, it can't install software updates or collect hardware inventory.

In general, Configuration Manager gives no special consideration to VMs. For example, if you stop a VM, and don't save its state, Configuration Manager might not determine if it has to reinstall a software update.

To help with Configuration Manager client performance in virtual environments that support multiple user sessions, it disables user policy by default. Starting in version 1910, you can enable user policy in this scenario. For more information, see [About client settings - Enable user policy for multiple user sessions](../../clients/deploy/about-client-settings#enable-user-policy-for-multiple-user-sessions).

## Microsoft Azure VMs

Configuration Manager can run on infrastructure as a service (IaaS) VMs in Azure just as it runs on-premises within your data center. Use Configuration Manager with Azure VMs in the following scenarios:

- **Scenario 1**: Run Configuration Manager on an Azure VM. Use it to manage clients on other Azure VMs.
- **Scenario 2**: Run Configuration Manager on an Azure VM. Use it to manage clients that aren't running on Azure.
- **Scenario 3**: Run different Configuration Manager site system roles on Azure VMs. Run other roles in your on-premises data center, properly connected to Azure.

Note

These scenarios also apply to IaaS VMs on Azure Stack Hub.

The same Configuration Manager requirements for networks, supported configurations, and hardware requirements also apply to Azure VMs.

For more information, see [Configuration Manager on Azure FAQ](../../understand/configuration-manager-on-azure).

Important

Configuration Manager sites and clients that run on Azure VMs are subject to the same license requirements as on-premises installations.

## Azure Virtual Desktop

[Azure Virtual Desktop](/en-us/azure/virtual-desktop/) is a desktop and app virtualization service that runs on Microsoft Azure. Use Configuration Manager to manage these virtual devices running Windows in Azure. For more information, see [Supported operating systems for clients and devices](supported-operating-systems-for-clients-and-devices#azure-virtual-desktop).