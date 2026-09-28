---
layout: Conceptual
title: What's new in version 2509 - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/changes/whats-new-in-version-2509
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
description: Get details about changes and new capabilities introduced in version 2509 of Configuration Manager current branch.
ms.date: 2025-11-11T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: whats-new
ms.collection: tier3
locale: en-us
document_id: 5078b7db-f260-4867-128e-3b3cf420ae51
document_version_independent_id: 5078b7db-f260-4867-128e-3b3cf420ae51
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/plan-design/changes/whats-new-in-version-2509.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/plan-design/changes/whats-new-in-version-2509
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/plan-design/changes/whats-new-in-version-2509.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/19ec6774-09b8-473e-a17e-b17b518bbad7
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ade36b61-c646-4bd8-87ee-f3a843461962
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
platformId: d766c98c-6cb8-3ff9-b3a2-d3c8b36aec72
---

# What's new in version 2509 - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Update 2509 for Configuration Manager current branch is available as an in-console update. Apply this update on sites that run version 2403 or later.

Always review the latest checklist for installing this update. For more information, see [Checklist for installing update 2509](../../servers/manage/checklist-for-installing-update-2509). After you update a site, also review the [Post-update checklist](../../servers/manage/checklist-for-installing-update-2509#post-update-checklist).

To take full advantage of new Configuration Manager changes, after you update the site, also update clients to the latest version. New functionality appears in the Configuration Manager console when you update the site and console, but the complete scenario isn't functional until the client version is also the latest.

## General enhancements

As part of Microsoft's Secure Future Initiative (SFI) the 2509 version of Configuration Manager focuses on security and quality updates. For more information, see the [Microsoft Trust Center](https://www.microsoft.com/trust-center/security/secure-future-initiative). For a list of significant customer-reported issues resolved in this release, see the [Summary of changes in Configuration Manager version 2509](../../../hotfix/2509/35877153) knowledge base article.

### Windows 11 25H2 support

Windows 11, version 25H2 is supported for OS deployment and in-place upgrade scenarios. For more information about Windows 11 25H2, see the [Windows 11 release information](/en-us/windows/release-health/windows11-release-information).

### Boot images can be automatically updated to use latest Windows Boot Loader

A new checkbox, *Use Windows Boot Loader signed with Windows UEFI CA 2023*, is available in the Data Source tab of boot image properties. When enabled, it updates the boot image to use the boot loader signed with Windows UEFI CA 2023. The checkbox automates the mitigation steps described in [KB5025885](https://support.microsoft.com/topic/how-to-manage-the-windows-boot-manager-revocations-for-secure-boot-changes-associated-with-cve-2023-24932-41a975df-beb2-40c1-99a3-b3ff139f832d).

The new functionality only works on WDS-Less PXE-enabled Distribution Points.

### WinPE is now boundary‑aware

Starting in **Configuration Manager 2509**, Windows PE–based OSD scenarios now require **Boundary Group Management Point (MP) assignments**.

- For a successful OSD deployment, the **Boundary Group that the WinPE client belongs to must contain at least one Management Point**.
- If no MP is associated with the client's Boundary Group, WinPE will fail to retrieve policy. The **smsts.log** will show errors similar to the following:

> 
> Failed to query Management Point locator Exiting TSMediaWizardControl :: GetPolicy. QueryMPLocator: no valid MP locations are received

### Service Connection Tool improvements

The Service Connection Tool (SCT) is improved to provide better logging and error handling, specifically in the following areas:

- More detailed information about the actions it performs is recorded in both the console and log file. Error and warning messages in the console are highlighted with colors for better visibility.
- The SCT explicitly checks for prerequisites and fails if they're not met.
- Customers are directed to explore the relevant logs, such as ServiceConnectionTool.log and ConfigMgrSetup.log, when there's an error.
- If there's a download failure, the SCT "Connect" step stops execution thus preventing importing incomplete Update Package payloads.

### AdminService now rejects NTLM authentication

- AdminService now rejects NTLM authentication attempts. `AdminService.log` should write the below message when NTLM authentication is attempted:

> 
> Rejecting NTLM authentication.

## Known Issues

- Upgrade SQL 2012 or 2014 Express, Standard, Enterprise edition to SQL 2016 or latest version. **VC++ Redistributable Version** needs to be upgraded to latest version on **Secondary sites**. [Download Latest Microsoft Visual C++ Redistributable Version](https://aka.ms/vs/17/release/vc_redist.x64.exe).

### Microsoft ODBC redistributable

- The Microsoft ODBC redistributable component is updated to version **18.4.1.1** on all Site servers and Management Points.
- Prerequisite check throws an error stalling the upgrade if it detects a version lower than 18.4.1.1.

> 
> INFO: Microsoft ODBC Driver 18 for SQL Server is installed but it is older than the required version. SQL client prerequisite missing for Configuration Manager setup.; Error; Install the Microsoft ODBC driver 18 for SQL setup from https://go.microsoft.com/fwlink/?linkid=2299909. More information https://go.microsoft.com/fwlink/?linkid=2226618