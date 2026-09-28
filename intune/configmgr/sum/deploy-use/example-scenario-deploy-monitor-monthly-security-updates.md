---
layout: Conceptual
title: Example scenario to deploy and monitor updates - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/sum/deploy-use/example-scenario-deploy-monitor-monthly-security-updates
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
description: How to use software updates in Configuration Manager to deploy and monitor monthly software updates.
ms.date: 2019-10-21T00:00:00.0000000Z
ms.topic: install-set-up-deploy
ms.subservice: software-updates
ms.collection: tier3
locale: en-us
document_id: b6951e73-4be6-95f8-6fb5-3a11bfd7185c
document_version_independent_id: ab2f402b-d2e7-7017-65a5-a2821a17911e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/sum/deploy-use/example-scenario-deploy-monitor-monthly-security-updates.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/sum/deploy-use/example-scenario-deploy-monitor-monthly-security-updates
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/sum/deploy-use/example-scenario-deploy-monitor-monthly-security-updates.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: 0aa8aa46-72fe-8887-778a-8f0a5e08c5c0
---

# Example scenario to deploy and monitor updates - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

This topic provides an example scenario of how you can use software updates in Configuration Manager to deploy and monitor the security software updates that Microsoft releases monthly.

In this scenario, we follow the actions of the Configuration Manager administrator at Woodgrove Bank. The administrator needs to create a software update deployment strategy with the following conditions and requirements:

- Active software update deployment occurs one week after Microsoft releases the security software updates on the second Tuesday of each month. This event is typically referred to as Patch Tuesday.
- Software updates are downloaded and staged on distribution points. Then a deployment is tested to a subset of clients before the ConfigMgr Admin fully deploys the software updates in his production environment.
- The administrator must be able to monitor the software updates' compliance by month or by year.

    This scenario assumes that the software update point infrastructure has already been implemented. Use the following information to plan for and configure software updates in Configuration Manager.

| Process | Reference |
| --- | --- |
| Review the key concepts for software updates. | [Introduction to software updates](../understand/software-updates-introduction) |
| Plan for software updates. This information helps you to plan for capacity considerations, determine the software update point infrastructure, software update point installation, synchronization settings, and client settings for software updates. | [Plan for software updates](../plan-design/plan-for-software-updates) |
| Configure software updates. This information helps you to install and configure software update points in your hierarchy and helps to configure and synchronize software updates. In this scenario, our ConfigMgr Admin configures the software updates synchronization schedule to occur on the second Wednesday of each month to ensure that they retrieve the latest security software updates from Microsoft. | [Synchronize software updates](../get-started/synchronize-software-updates) |

The following sections in this topic provide example steps to help you to deploy and monitor Configuration Manager security software updates in your organization.

## Step 1: Create a software update group for yearly compliance

The Configuration Manager administrator creates a software update group that can be used to monitor compliance for all of the security software updates that they release in 2016. The admin performs the steps in the following table.

| Process | Reference |
| --- | --- |
| From the **All Software Updates** node in the Configuration Manager console, the Configuration Manager administrator adds criteria to display only security software updates that are released or revised in year 2015 that meet the following criteria:<br>- **Criteria**: Date Released or Revised<br>- **Condition**: is greater than or equal to specific date**Value**: 1/1/2015<br>- **Criteria**: Update Classification**Value**: Security Updates<br>- **Criteria**: Expired **Value**: No | No additional information |
| ConfigMgr Administrator adds all of the filtered software updates to a new software update group with the following requirements:<br>- **Name**: Compliance Group - Microsoft Security Updates 2015<br>- **Description**: Software updates | [Add software updates to an update group](add-software-updates-to-an-update-group) |

## Step 2: Create an automatic deployment rule for the current month

The Configuration Manager administrator creates an automatic deployment rule for the security software updates that are released by Microsoft for the current month. The admin performs the steps in the following table.

| Process | Reference |
| --- | --- |
| ConfigMgr Admin creates an automatic deployment rule with the following requirements:<br>1. On the **General**tab, the ConfigMgr Admin configures the following:<br>    - Specifies **Monthly Security Updates** for the name.<br>    - Selects a test collection with limited clients.<br>    - Selects **Create a new Software Update Group**.<br>    - Verifies that **Enable the deployment after this rule is run** is not selected.<br>2. On the **Deployment Settings** tab, the ConfigMgr Admin selects the default settings.<br>3. On the **Software Updates**page, the ConfigMgr Admin configures the following property filters and search criteria:<br>    - Date Released or Revised **Last 1 month**.<br>    - Update Classification **Security Updates**.<br>4. On the **Evaluation** page, the ConfigMgr Admin enables the rule to run on a schedule for the **second Thursday** of every **month**. The ConfigMgr Admin also verifies that his synchronization schedule is set to run on the **second Wednesday** of every **month**.<br>5. The ConfigMgr Admin uses the default settings on the Deployment Schedule, User Experience, Alerts, and Download Settings pages.<br>6. On the **Deployment Package** page, the ConfigMgr Admin specifies a new deployment package.<br>7. The ConfigMgr Admin uses the default settings on the Download Location and Language Selection pages. | [Automatically deploy software updates](automatically-deploy-software-updates) |

## Step 3: Verify that software updates are ready to deploy

On the second Thursday of every month, the ConfigMgr Admin verifies that the software updates are ready to deploy. The admin performs the following step.

| Process | Reference |
| --- | --- |
| The ConfigMgr Admin verifies that software updates synchronization completed successfully. | [Software updates synchronization status](monitor-software-updates#BKMK_SUSyncStatus) |

## Step 4: Deploy the software update group

After the ConfigMgr Admin verifies that the software updates are ready to deploy, they deploy the software updates. The admin performs the steps in the following table.

| Process | Reference |
| --- | --- |
| The ConfigMgr Admin creates two test deployments for the new software update group. The admin considers the following environments for each deployment:**Workstation test deployment**: the ConfigMgr Admin considers the following for the workstation test deployment:<br>- Specifies a deployment collection that contains a subset of workstation clients to verify the deployment.<br>- Configures the deployment settings that are appropriate for the workstation clients in his environment.<br><br>**Server test deployment**: the ConfigMgr Admin considers the following for the server test deployment:<br>- Specifies a deployment collection that contains a subset of server clients to verify the deployment.<br>- Configures the deployment settings that are appropriate for the server clients in his environment. | [Deploy software updates](deploy-software-updates) |
| The ConfigMgr Admin verifies that the test deployments have successfully deployed. | [Software updates deployment status](monitor-software-updates#BKMK_SUDeployStatus) |
| The ConfigMgr Admin updates the two deployments with new collections that include his production workstations and servers. | No additional information |

## Step 5: Monitor compliance for deployed software updates

The ConfigMgr Admin monitors compliance of his software update deployments. The admin performs the step in the following table.

| Process | Reference |
| --- | --- |
| The ConfigMgr Admin monitors the software updates deployment status in the Configuration Manager console and checks the software update deployment reports available from the console. | [Monitor software updates](monitor-software-updates) |

## Step 6: Add monthly software updates to the yearly update group

The ConfigMgr Admin adds the software updates from the monthly software update group to the yearly software update group. The admin performs the step in the following table.

| Process | Reference |
| --- | --- |
| The ConfigMgr Admin selects the software updates from the monthly software update group and adds the software updates to the software updates group that were created for yearly compliance. The admin tracks the software update compliance and creates various reports for his management. | [Add software updates to a deployed update group](add-software-updates-to-an-update-group) |

The ConfigMgr Admin has successfully completed his monthly deployment for security software updates. The admin continues to monitor and report on software update compliance to ensure that the clients in his environment are within acceptable compliance levels.

## Recurring monthly process to deploy software updates

After the first month that our ConfigMgr Admin deploys software updates, the admin performs steps three through six to deploy the monthly security software updates released by Microsoft.