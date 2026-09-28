---
layout: Conceptual
title: Technical preview 2204 - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/2022/technical-preview-2204
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
description: Learn about new features available in the Configuration Manager technical preview branch version 2204.
ms.date: 2022-04-29T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: whats-new
ms.collection: tier3
locale: en-us
document_id: 720cad58-2e90-ac2a-5d2c-334f417178f8
document_version_independent_id: 720cad58-2e90-ac2a-5d2c-334f417178f8
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/get-started/2022/technical-preview-2204.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/get-started/2022/technical-preview-2204
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/get-started/2022/technical-preview-2204.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/68ec7f3a-2bc6-459f-b959-19beb729907d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/90370425-aca4-4a39-9533-d52e5e002a5d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
platformId: 39c93d35-ddf3-4166-b529-42484d2e4eaf
---

# Technical preview 2204 - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (technical preview branch)*

This article introduces the features that are available in the technical preview for Configuration Manager, version 2204. Install this version to update and add new features to your technical preview site.

Review the [technical preview](../technical-preview) article before installing this update. That article familiarizes you with the general requirements and limitations for using a technical preview, how to update between versions, and how to provide feedback.

The following sections describe the new features to try out in this version:

## Administration Service Management option

When configuring Azure Services, a new option called **Administration Service Management** is now added for enhanced security. Selecting this option allows administrators to segment their admin privileges between [cloud management gateway (CMG)](../../clients/manage/cmg/overview) and [administration service](../../../develop/adminservice/overview). By enabling this option, access is restricted to only administration service endpoints. Configuration Management clients will authenticate to the site using Microsoft Entra ID.

![Screenshot of administration service management option in the Azure Service Wizard.](media/12952905-administration-service-management-azure-services.png)

### Try it out!

Try to complete the tasks. Then send [Feedback](../../understand/product-feedback) with your thoughts on the feature.

Generate a Microsoft Entra token and call the administration service by using a PowerShell script. The sample script and details can be found in the [Microsoft/configmgr-hub GitHub repository](https://aka.ms/cmadminservicetokensample).

## Folders for automatic deployment rules (ADRs)

Admins can now organize ADRs by using folders. This change allows for better categorization and management of ADRs. Folder management for ADRs is also supported with PowerShell cmdlets.

[![Screenshot of right-click menu displaying folder options for the automatic deployment rules node.](media/13507410-sum-adrdeployment.png)](media/13507410-sum-adrdeployment.png#lightbox)

### Try it out!

Try to complete the tasks. Then send [Feedback](../../understand/product-feedback) with your thoughts on the feature.

1. Open the Configuration Manager console, go to the **Software Library** workspace, and then go to **Automatic Deployment Rules**.
2. From the ribbon or right-click menu, and in the **Automatic Deployment Rules**select from the following options:
    - **Create Folder**
    - **Delete Folder**
    - **Rename Folder**
    - **Move Folders**
    - **Set Security Scopes**