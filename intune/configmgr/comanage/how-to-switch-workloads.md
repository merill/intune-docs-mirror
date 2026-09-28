---
layout: Conceptual
title: Switch co-management workloads - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/comanage/how-to-switch-workloads
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
description: Learn how to switch workloads currently managed by Configuration Manager to Microsoft Intune.
ms.subservice: co-management
ms.date: 2021-10-05T00:00:00.0000000Z
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 405b6221-1ae4-bb22-2352-fe8afadc8a88
document_version_independent_id: 1fd26b13-4706-b171-1977-2f70b3858422
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/comanage/how-to-switch-workloads.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/comanage/how-to-switch-workloads
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/comanage/how-to-switch-workloads.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/e0ffb20c-01c6-407b-a9bd-29111652a1dc
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/3904bce4-d817-48cf-85fd-b6146fca83b7
platformId: 7cf45d3f-4ee2-8933-248d-00806ccda826
---

# Switch co-management workloads - Configuration Manager | Microsoft Learn

One of the benefits of co-management is switching workloads from Configuration Manager to Microsoft Intune. When a Windows 10 or later device has the Configuration Manager client and is enrolled to Intune, you get the benefits of both services. You control which workloads, if any, you switch the authority from Configuration Manager to Intune. Configuration Manager continues to manage all other workloads, including those workloads that you don't switch to Intune, and all other features of Configuration Manager that co-management doesn't support.

If you switch a workload to Intune, but later change your mind, you can switch it back to Configuration Manager.

For more information on the supported workloads, see [Workloads](workloads).

## Switch workloads

You can configure different pilot collections for each of the co-management workloads. Being able to use different pilot collections allows you to take a more granular approach when shifting workloads. You can switch workloads when you enable co-management, or later when you're ready. If you haven't already enabled co-management, do that first. For more information, see [How to enable co-management](how-to-enable). After you enable co-management, modify the settings in the co-management properties.

1. In the Configuration Manager console, go to the **Administration** workspace, expand **Cloud Services**, and select the **Cloud Attach** node. For version 2103 and earlier, select the **Co-management** node.
2. Select the co-management object, and then choose **Properties** in the ribbon.
3. Switch to the **Workloads** tab. By default, all workloads are set to the **Configuration Manager** setting. To switch a workload, move the slider control for that workload to the desired setting.

    ![Screenshot of Workloads tab on co-management properties page](media/3555750-co-management-workloads-tab.png)

    - **Configuration Manager**: Configuration Manager continues to manage this workload.
    - **Pilot Intune**: Switch this workload only for the devices in the pilot collection. You can change the **Pilot collections** on the **Staging** tab of the co-management properties page.
    - **Intune**: Switch this workload for all Windows devices enrolled in co-management.

Note

When Pilot Intune is selected for Endpoint Protection and Device Configuration Policies, Intune only deploys the policies and doesn't perform policy removal upon unassignment. For policy removal from the device when the policy is unassigned, the workload must be switched to Intune.

1. Go to the **Staging** tab and change the **Pilot collection** for any of the workloads if needed.

    ![Screenshot of Staging tab on co-management properties page](media/3555750-co-management-staging-tab.png)

Important

Before you switch any workloads, make sure you properly configure and deploy the corresponding workload in Intune. Make sure that workloads are always managed by one of the management tools for your devices. When you switch a co-management workload, the co-managed devices automatically synchronize MDM policy from Microsoft Intune.