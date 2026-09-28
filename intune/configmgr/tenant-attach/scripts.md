---
layout: Conceptual
title: Tenant attach - Run Scripts from the admin center - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/scripts
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
description: Run scripts for Configuration Manager devices from the admin center.
ms.date: 2022-07-11T00:00:00.0000000Z
ms.topic: how-to
ms.subservice: core-infra
ms.collection: tier3
ms.custom: sfi-image-nochange
locale: en-us
document_id: 01404d47-4083-b2ef-cfe6-20d6243a0cf2
document_version_independent_id: 98f48d8a-3f74-b35c-f851-56bef7c41a09
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/tenant-attach/scripts.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/tenant-attach/scripts
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/tenant-attach/scripts.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 5582b41c-6c2d-fd2f-f43f-13d89e4b1431
---

# Tenant attach - Run Scripts from the admin center - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Bring the power of the Configuration Manager on-premises Run Scripts feature to the Microsoft Intune admin center. Allow additional personas, like Helpdesk, to run PowerShell scripts from the cloud against an individual Configuration Manager managed device in real time. This gives all the traditional benefits of PowerShell scripts that have already been defined and approved by the Configuration Manager admin to this new environment.

[![Screenshot of script list in the admin center](media/6234688-scripts.png)](media/6234688-scripts.png#lightbox)

## Prerequisites

Running Scripts from the admin center requires the following items:

- All of the prerequisites for [Tenant attach: ConfigMgr client details](client-details#prerequisites)
- A supported version of Configuration Manager installed.
    - All sites in the hierarchy must meet the minimum Configuration Manager version requirement.
- Configuration Manager clients must be running the latest version client.
- To run PowerShell scripts, the client must be running PowerShell version 3.0 or later.
    - If a script you run contains functionality from a later version of PowerShell, the client on which you run the script must be running that later version of PowerShell.
- At least one script that is already created and approved in Configuration Manager.
    - Scripts that have parameters aren't supported at this time and won't be visible in the Microsoft Intune admin center.
    - Only scripts that are already created and approved appear in the admin center. For more information on approving scripts, see [Approve or deny a script](../apps/deploy-use/create-deploy-scripts#run-script-authors-and-approvers).

## Permissions

The user account needs the following permissions:

- The **Read** permission for the device's **Collection** in Configuration Manager.
- The **Read Resource** permission for the device's **Collection** in Configuration Manager.
- An [Intune role](../../fundamentals/role-based-access-control/overview) assigned to the user
- To use scripts, you must be a member of the appropriate Configuration Manager security role. For more information, see [Security scopes for run scripts](../apps/deploy-use/create-deploy-scripts#bkmk_ScriptRoles).
- To run scripts, the account must have **Run Script** permissions for **Collections**.

## Run a script

1. In a browser, go to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** then **All Devices**.
3. Select a device that is synced from Configuration Manager via [tenant attach](device-sync-actions).
4. Select **Scripts**.

    Scripts that were recently run that directly targeted the device will already be listed. The list includes scripts run from the admin center, SDK, or the Configuration Manager console. Scripts initiated from the on-premises console, against collections containing the device won't be shown, unless the scripts were also initiated specifically for the single device.

    [![Running the script from the admin center](media/6234688-run-script.png)](media/6234688-run-script.png#lightbox)
5. Choose **Run script**.

    Scripts that are available to the admin based on the scopes assigned in Configuration Manager will be listed.
6. Select **Run** to run the script.
7. You'll be notified your script has started. You don't have to wait for the script to finish before sending another to the device.
8. Select **Refresh** on the main page to update the list with latest script state, and last run time.
9. When the script completes, you can select the script to display the results in the **Output** pane. You can copy the text of the script output. Select **Re-run script** if you want the script to run again.

    [![Script output in the admin center](media/6234688-script-output.png)](media/6234688-script-output.png#lightbox)