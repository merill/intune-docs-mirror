---
layout: Conceptual
title: Upgrade Readiness - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/upgrade-readiness
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
description: Integrate Upgrade Readiness with Configuration Manager to access Windows upgrade compatibility data and target devices for upgrade or remediation.
ms.date: 2020-01-31T00:00:00.0000000Z
ms.topic: integration
ms.subservice: core-infra
ms.collection: tier3
locale: en-us
document_id: 8d515817-4cf8-27ca-a0ba-c3e4fe67bb8a
document_version_independent_id: 185d6937-2ea9-dd26-ed23-bce913b58a74
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/manage/upgrade-readiness.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/manage/upgrade-readiness
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/manage/upgrade-readiness.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: d134dc37-6a9a-2125-9d11-7504dd44da88
---

# Upgrade Readiness - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Important

The Windows Analytics service is retired as of January 31, 2020. For more information, see [KB 4521815: Windows Analytics retirement on January 31, 2020](https://support.microsoft.com/help/4521815/windows-analytics-retirement).

If your Configuration Manager site had a connection to Upgrade Readiness, you need to remove it and reconfigure clients.

## Remove Upgrade Readiness connection

1. Open the Configuration Manager console as a user with the **Full administrator** role.
2. Go to the **Administration** workspace, expand **Cloud Services**, and select the **Azure Services** node.
3. Delete the Windows Analytics service.

## Reconfigure clients

### Unenroll devices

First, review the site's default or any custom client device settings in the **Windows Analytics** group. For example, disable the following setting: **Manage Windows telemetry settings with Configuration Manager**.

On enrolled devices, remove the CommercialID value from the following Windows Registry keys:

- `HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\DataCollection`
- `HKLM:\SOFTWARE\Policies\Microsoft\Windows\DataCollection`

### Windows diagnostic data configuration

If you don't want your devices to continue sending diagnostic data:

- Windows 10: set the diagnostic data level to **Security**
- Windows 7 SP1 or 8.1: disable the **Commercial Data Opt-in Key**

Set these values using one of the following methods:

- Group policy, in **Computer Configuration** &gt; **Administrative Templates** &gt; **Windows Components** &gt; **Data Collection and Preview Builds**
- Mobile device management (MDM), such as [Microsoft Intune](../../../../device-configuration/templates/ref-device-restrictions-windows)

For more information, see [Configure Windows diagnostic data in your organization](/en-us/windows/privacy/configure-windows-diagnostic-data-in-your-organization).

Note

When you apply these changes, devices immediately stop sending diagnostic data. It may take 24-48 hours for Microsoft to stop processing insights for your workspace. Microsoft deletes this data from its cloud services within 30 days or less.