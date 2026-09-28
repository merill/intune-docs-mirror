---
layout: Conceptual
title: What's new in version 2409 - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/changes/whats-new-in-version-2409
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
description: Get details about changes and new capabilities introduced in version 2409 of Configuration Manager current branch.
ms.date: 2024-12-03T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: whats-new
ms.collection: tier3
ms.custom: sfi-ga-nochange
locale: en-us
document_id: dcc2e030-743e-6d6d-c2d5-c06b4b63dd39
document_version_independent_id: dcc2e030-743e-6d6d-c2d5-c06b4b63dd39
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/plan-design/changes/whats-new-in-version-2409.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/plan-design/changes/whats-new-in-version-2409
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/plan-design/changes/whats-new-in-version-2409.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/19ec6774-09b8-473e-a17e-b17b518bbad7
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/12ed19f9-ebdf-4c8a-8bcd-7a681836774d
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ade36b61-c646-4bd8-87ee-f3a843461962
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3a764584-4f97-452b-8f1d-36f19b12f6ae
platformId: d3566f71-f240-0792-4bf3-780e4256a0af
---

# What's new in version 2409 - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Update 2409 for Configuration Manager current branch is available as an in-console update. Apply this update on sites that run version 2309 or later.  This article summarizes the changes and new features in Configuration Manager, version 2409.

Always review the latest checklist for installing this update. For more information, see [Checklist for installing update 2409](../../servers/manage/checklist-for-installing-update-2409). After you update a site, also review the [Post-update checklist](../../servers/manage/checklist-for-installing-update-2409#post-update-checklist).

To take full advantage of new Configuration Manager features, after you update the site, also update clients to the latest version. While new functionality appears in the Configuration Manager console when you update the site and console, the complete scenario isn't functional until the client version is also the latest.

## Site infrastructure

### Configuration Manager now supports SQL Extended Protection for Authentication

Configuration Manager now supports SQL extended protection for authentication. It's a security feature that enhances protection against MITM attacks, making SQL server more secure when connections are made using extended protection. These enhancements collectively reduce the risk of unauthorized access and protect sensitive data managed by the SQL Server database engine.

For more information, see [Connect to the Database Engine Using Extended Protection](/en-us/sql/database-engine/configure-windows/connect-to-the-database-engine-using-extended-protection).

### Introducing Centralized Search - Desired Workspace Selection

The centralized search box now enables the option to select the desired workspace for searching. Users can easily refine their search results by selecting the desired workspace from the dropdown menu.

[![Screenshot of centralized search workspace selection in console.](media/27679763-search-workspace.png)](media/27679763-search-workspace.png#lightbox)

### Configuration Manager does not support SQL Server 2012 and 2014

Starting with version 2409, Configuration Manager no longer supports SQL Server 2012 and 2014. Upgrade to the latest SQL Server version or at least SQL Server 2016. If you don't upgrade, CM upgrades are blocked, and you see an error during the prereq check. For more information, see [Supported SQL Server versions for Configuration Manager](../configs/support-for-sql-server-versions).

### Operating System support added for Windows 11 24H2 and Windows Server 2025

With this version of Configuration Manager, support is added for Windows 11 24H2 and Windows Server 2025.

- Windows 11 24H2 & Windows Server 2025 are added to the Product lifecycle dashboard and supported platform.
- Windows 11 24H2 & Windows Server 2025 client support is added.
- Boot image creation in CM on Windows Server 2025 now supports latest Windows ADK.
- Windows upgrade readiness dashboard now supports Windows 11 24H2 for upgrading clients.

Note

Windows Server and Windows 11 24H2 do not support Firewall Rules. This will result in a non-compliant status in the Configuration Manager applet.

### Software metering support in Arm64 devices

The Configuration Manager now supports Software metering for Arm64 devices. Software metering is used to monitor Windows PC desktop apps with a filename ending in .exe. For more information, see [Software metering in Configuration Manager](../../../apps/deploy-use/monitor-app-usage-with-software-metering).

## OS deployment

### BitLocker support in Arm64 devices

Configuration Manager now supports BitLocker task sequence steps for Arm64 devices. In BitLocker Management, policies that include OS drive encryption with a TPM protector and fixed drive encryption with the Auto-Unlock option are supported on Arm64 devices.

For more information, see [Bitlocker Supported configurations](../../../protect/plan-design/bitlocker-management#supported-configurations).

## Cloud-attached management

### CMG Entra Application secret key renewal

The 'Renew Secret Key' feature now opens a dialog with four options for the validity period. This update also prevents applications older than 800 days (approximately two years) from renewing their secret keys. The same options are available when creating a new app.

![Screenshot of secret window selection in console.](media/27297018-secret-window.png)

Sign in using the tenant [Microsoft Entra Global Administrator](/en-us/entra/identity/role-based-access-control/permissions-reference#global-administrator) credentials and then click on the **Renew** button.

Important

The [Microsoft Entra Global Administrator](/en-us/entra/identity/role-based-access-control/privileged-roles-permissions) role is a highly privileged role and should only be used when another role can't be used. This feature requires the Global Administrator role. For other features, Microsoft recommends using roles with the fewest permissions. To learn more, see [Fundamentals of role-based administration for Configuration Manager](../../understand/fundamentals-of-role-based-administration).

### CMG Enhanced security option

CMG Setup now uses managed Identities and third-party **Server App** to interact with CMG's Azure Storage account, instead of storage account keys.

- Hence storage account key access is disabled for new CMG setup.
- For sessions upgrading from earlier versions to 2409, the 'CMG enhanced security' button is shown as enabled.

    [![Screenshot of Cmg enhanced window selection in console.](media/27297018-cmg-enhanced.png)](media/27297018-cmg-enhanced.png#lightbox)

## Known Issues

- Upgrade SQL 2012 or 2014 Express, Standard, Enterprise edition to SQl 2016 or latest version. **VC++ Redistributable Version** need to be upgraded to latest version on **Secondary sites**. [Download Latest Microsoft Visual C++ Redistributable Version](https://aka.ms/vs/17/release/vc_redist.x64.exe).

## Other Updates

### Performance Enhancement of policy processing and collection evaluation

The performance of policy processing and collection evaluation has been enhanced. Previously, blocking chains from sp\_ProcessPolicyChanges, called by PolicyPv, would run for hours, disrupting multiple workloads including collection management and policy processing.

## Deprecated features

Learn about support changes before they're implemented in [removed and deprecated items](deprecated/removed-and-deprecated).

- MDT Integration with CM and Standalone is no longer supported with Configuration Manager deprecation first announced in December 2024 and planned end of support the first release after Oct 10, 2025. Customers should remove MDT Task sequence steps, followed by removing MDT integration, to avoid TS corruption and modification failures.

For more information, see [Removed and deprecated features for Configuration Manager.](deprecated/removed-and-deprecated-cmfeatures).