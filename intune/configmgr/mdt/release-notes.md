---
layout: Conceptual
title: MDT release notes - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/mdt/release-notes
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
description: Understand supported platforms, prerequisites, and limitations of the Microsoft Deployment Toolkit (MDT).
ms.date: 2022-08-12T00:00:00.0000000Z
ms.subservice: mdt
ms.topic: release-notes
ms.collection: tier3
locale: en-us
document_id: df86617a-8915-afa6-3bf0-db1f846b4dc5
document_version_independent_id: 1901d959-5e4a-a233-19fc-2f9c48d17d33
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/mdt/release-notes.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/mdt/release-notes
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/mdt/release-notes.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/e0ffb20c-01c6-407b-a9bd-29111652a1dc
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/e3e53a21-5c86-4f87-b1fb-893b77a777ba
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/3904bce4-d817-48cf-85fd-b6146fca83b7
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/383e0c27-53d0-4bef-b930-1e0b0ae37c07
platformId: dc9589cb-958a-8e76-73a3-e9ce79eaf700
---

# MDT release notes - Configuration Manager | Microsoft Learn

This article provides details on the latest release of the Microsoft Deployment Toolkit (MDT). These details include supported platforms, prerequisites, and any limitations. It assumes familiarity with MDT version concepts, features, and capabilities.

Caution

### **Microsoft Deployment Toolkit (MDT) is retired.**

> 
> **Microsoft Deployment Toolkit (MDT) is retired.** MDT integration with Configuration Manager and MDT Standalone are **no longer supported**. Customers should **remove all MDT task sequence steps** and then **remove MDT integration** to prevent task sequence corruption and modification failures. **Consider moving to modern provisioning solutions such as Windows Autopilot**, which provides cloud‑driven, zero‑touch provisioning for Windows devices. Learn more about Autopilot: [here](/en-us/windows/deployment/windows-autopilot/windows-autopilot). For customers with on-premises infrastructure and existing Configuration Manager environments, **OSD** remains a fully supported option.

> 
> For full details on this retirement, see the **[Removed and Deprecated Features](../core/plan-design/changes/deprecated/removed-and-deprecated-cmfeatures)** page.

## Latest release

**MDT build 8456** is the latest version available on the [Microsoft Download Center](https://aka.ms/mdtdownload).

This update begins support for Windows 10, version 1809, and Windows Server 2019. For more information, see the supported platforms section.

## Significant changes

Here is a summary of the significant changes in MDT build 8456.

### Supported configuration updates

- Windows ADK for Windows 10, version 1809
- Windows 10, version 1809
- Configuration Manager, version 1810

### Major changes

The following list is a summary of the major changes in this version:

- Nested task sequence support for LTI scenario
- Modern language pack support ^[Known issue](known-issues#modern-language-pack-support)^
- Support for Configuration Manager version 1810
- IsVM evaluates to False on Parallels VMs
- IsVM = False when VMware VM is configured with EFI boot firmware
- Gather doesn't recognize All-in-One chassis type
- MDT doesn't automatically install BitLocker on Windows Server 2016
- BDEDisablePreProvisioning typo in ZTIGather.xml

## Supported platforms

MDT releases are no longer tagged with year or update version. To align better with the current branches of Windows 10 and Configuration Manager, and to simplify the branding and release process, it's now simply **Microsoft Deployment Toolkit**. The build number is used to distinguish each release. For example, the latest build available for download is 8456.

Unlike Configuration Manager with a predetermined release schedule, MDT only releases as required to support new versions of Windows, the Windows ADK, or Configuration Manager current branch. Any [known issues](known-issues) with these components will be documented in this article as necessary.

The following OS versions are supported for deployment with this build of MDT:

- Windows 10, version 1809
- Windows 10, version 1803
- Windows 10, version 1709
- Other [supported versions](/en-us/windows/release-information/) of Windows 10
- Windows Server 2019
- Windows Server 2016

Note

MDT doesn't support Windows 10 ARM64 devices or any Windows versions released after those listed above.

FAQ: [Is this release only supported with Windows 10, Windows ADK, or Configuration Manager version *X*?](faq#what-s-the-mdt-support-life-cycle-)

## Prerequisites

MDT requires the following components, which are included in Windows:

- Microsoft .NET Framework 4.0
- Windows PowerShell version 3.0

MDT requires the latest [Windows ADK for Windows 10](/en-us/windows-hardware/get-started/adk-install). MDT also requires the **Windows PE add-on** for the Windows ADK.

Note

Windows recommends using the Windows ADK that matches the version of Windows you're deploying. For example, use the Windows ADK for Windows 10 version 1809 when deploying Windows 10 version 1809. For more information on Windows ADK component supportability, see [DISM supported platforms](/en-us/windows-hardware/manufacture/desktop/dism-supported-platforms) and [USMT requirements](/en-us/windows/deployment/usmt/usmt-requirements#bkmk-1).

When integrating MDT with Configuration Manager for ZTI and UDI scenarios, use the latest version of Configuration Manager current branch.

## Upgrade MDT

The MDT installation process removes any existing instances of MDT installed on the same computer. Existing deployment shares, distribution points, and databases are preserved during this process. They must be upgraded when the installation is complete.

The current release of MDT supports upgrading from the following versions of MDT:

- MDT build 8450

Tip

Create a backup of the existing MDT infrastructure before attempting an upgrade.

### LTI

After installing MDT, upgrade an existing deployment share by running the **Open Deployment Share Wizard** from the Deployment Shares node in the Deployment Workbench. Specify the path to the existing deployment share directory, and then select the **Upgrade** check box. This process also upgrades existing network deployment shares and media deployment shares, so those shares should be accessible. Don't upgrade with active deployments, because in-use files can cause upgrade problems.

### ZTI

Existing MDT task sequences present in Configuration Manager aren't modified during the installation process of MDT. They should continue to work without any issue. No mechanism is provided to upgrade these task sequences. If you want to use any of the new MDT capabilities, create new MDT-integrated task sequences in Configuration Manager.

When the upgrade process is complete:

- Run the **Configure ConfigMgr Integration Wizard** after the upgrade. It registers the new components and installs the updated ZTI task sequence templates.
- Create a new **Microsoft Deployment Toolkit Files** package for any new ZTI task sequences you create. You can use the existing MDT Files package for any ZTI task sequences created before the upgrade. Create a new MDT Files package for new ZTI task sequences.