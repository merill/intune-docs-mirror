---
layout: Conceptual
title: Prepare for in-console updates - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/prepare-in-console-updates
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
description: Prepare to install updates to Configuration Manager from the Microsoft cloud
ms.date: 2024-12-04T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 0b7a7e93-80ef-ff04-6edc-92390f594eb6
document_version_independent_id: 9f1561ec-6800-a7d7-1cd5-e25fe2c4de75
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/servers/manage/prepare-in-console-updates.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/servers/manage/prepare-in-console-updates
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/servers/manage/prepare-in-console-updates.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/486161dc-fa28-4625-9b1c-1a21d690bc8d
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/5dd28c86-729c-4723-ab5a-57e26fcec2a8
platformId: 229b871e-0cb5-c8c4-9a8a-4e2721c87ea0
---

# Prepare for in-console updates - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Configuration Manager synchronizes with the Microsoft cloud service to get updates. Use the steps in this article to prepare your environment.

## Get available updates

The site only downloads updates that apply to your infrastructure and version. This synchronization can be automatic or manual, depending on how you configure the service connection point for your hierarchy:

- In **online mode**, the service connection point automatically connects to the Microsoft cloud service and downloads applicable updates.

    By default, Configuration Manager checks for new updates every 24 hours. Manually check for updates in the Configuration Manager console. Go to the **Administration** workspace, select the **Updates and Servicing** node, and choose **Check for Updates** in the ribbon.
- In **offline mode**, the service connection point doesn't connect to the Microsoft cloud service. To download and then import available updates, [use the Service Connection Tool](use-the-service-connection-tool).

Note

If necessary, import out-of-band fixes into your console. To do so, use the [update registration tool](use-the-update-registration-tool-to-import-hotfixes). These out-of-band fixes supplement the updates you get when you synchronize with the Microsoft cloud service.

After updates synchronize, view them in the Configuration Manager console. Go to the **Administration** workspace and select the **Updates and Servicing** node.

- Updates you haven't installed display as **Available**.
- Updates you've installed display as **Installed**. Only the most recently installed update is shown. To view previously installed updates, select **History** in the ribbon.

Before you configure the service connection point, understand and plan for its use. The following uses might affect how you configure this site system role:

- The site uses the service connection point to upload usage information about your site. This information helps the Microsoft cloud service identify the updates that are available for the current version of your infrastructure. For more information, see [Diagnostics and usage data](../../plan-design/diagnostics/diagnostics-and-usage-data).

To better understand what happens when updates are downloaded, see the following flowcharts:

- [Flowchart - Download updates](download-updates-flowchart)
- [Flowchart - Update replication](update-replication-flowchart)

## Permissions

To view updates in the console, a user must have a role-based administration security role that includes the security class **Update packages**. This class grants access to view and manage updates in the Configuration Manager console.

### About the Update packages class

By default, the **Update packages** class (SMS\_CM\_Updatepackages) is part of the following built-in security roles with the listed permissions:

- **Full Administrator** with **Modify** and **Read** permissions:

    - A user with this security role and access to the **All** security scope can view and install updates. The user can also enable features during the installation, and enable individual features after the site updates.
    - A user with this security role and access to the **Default** security scope can view and install updates. The user can also enable features during the installation, and view features after the site updates. But this user can't enable the features after the site updates.
- **Read-only Analyst** with **Read** permissions:

    - A user with this security role and access to the **Default** scope can view updates but not install them. This user can also view features after the site updates, but can't enable them.

### Permissions required for updates and servicing

- Use an account to which you assign a security role that includes the **Update packages** class with both **Modify** and **Read** permissions.
- Assign the account to the **Default** scope.

### Permissions to only view updates

- Use an account to which you assign a security role that includes the **Update packages** class with only the **Read** permission.
- Assign the account to the **Default** scope.

### Permissions required to enable features after the site updates

- Use an account to which you assign a security role that includes the **Update packages** class with both **Modify** and **Read** permissions.
- Assign the account to the **All** scope.

## Before you install an in-console update

Review the following steps before you install an update from within the Configuration Manager console.

### Step 1: Review the update checklist

Review the applicable update checklist for actions to take before you start the update:

- [Checklist for installing update 2409](checklist-for-installing-update-2409)
- [Checklist for installing update 2403](checklist-for-installing-update-2403)
- [Checklist for installing update 2309](checklist-for-installing-update-2309)
- [Checklist for installing update 2303](checklist-for-installing-update-2303)

### Step 2: Run the prerequisite checker before installing an update

Before you install an update, run the prerequisite checks for that update. If you run the checks before installing an update:

- The site replicates update files to other sites before installing the update.
- When you choose to install the update, the prerequisite check automatically runs again.

Note

When you start a prerequisite check and then view the status, the **Installation** phase appears to be active. However, the site isn't actually installing the update. To run the prerequisite check, the update process extracts the package from the content library. It then puts the package into a staging folder where it can access the current prerequisite checks. When you install an update, this same process runs. This behavior is why the Installation phase shows as **In progress**. Only the *Extract Update package* step is shown in the Installation category.

Later, when you install the update, you can configure the update to ignore prerequisite check warnings.

#### Process to run the prerequisite checker before installing an update

1. In the Configuration Manager console, go to the **Administration** workspace, and select the **Updates and Servicing** node.
2. Select the update package for which you want to run the prerequisite check.
3. Select **Run prerequisite check** in the ribbon.

    When you run the prerequisite check, content for the update replicates to child sites. View the **distmgr.log** on the site server to confirm that content replicates successfully.
4. To view the results of the prerequisite check:

    1. In the Configuration Manager console, go to the **Monitoring** workspace.
    2. Select the **Updates and Servicing Status** node and look for the prerequisite status.
    3. For more information, see the **ConfigMgrPrereq.log** on the site server.