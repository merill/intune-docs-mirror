---
layout: Conceptual
title: Monitor orchestration groups - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/sum/deploy-use/monitor-orchestration-groups
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
description: Monitor and reset orchestration groups.
ms.date: 2022-07-11T00:00:00.0000000Z
ms.subservice: software-updates
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 6571742f-1ec8-ae37-efc0-a3350e678c5a
document_version_independent_id: 6571742f-1ec8-ae37-efc0-a3350e678c5a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/sum/deploy-use/monitor-orchestration-groups.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/sum/deploy-use/monitor-orchestration-groups
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/sum/deploy-use/monitor-orchestration-groups.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: fc9ef2d9-9ddc-9e0c-63c4-deb049cb73fe
---

# Monitor orchestration groups - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

After you create, edit, or start an orchestration group, you may need to monitor the group or its members. Using monitoring information along with the log files, can help you troubleshoot orchestration groups and group members.

## Monitor orchestration groups

From the **Assets and Compliance** workspace, select the **Orchestration Group** node. Add any of the following columns to get information about the groups:

- **Orchestration Name**: The name of your orchestration group.
- **Site Code**: Site code for the group.
- **Orchestration Type**: is one of the following types:

    - Number
    - Percentage
    - Sequence
- **Orchestration Value**: How many members or the percentage of members that can get a lock simultaneously. **Orchestration Value** is only populated when **Orchestration Type** is either *Number* or *Percentage*.
- **Orchestration State**: In progress during orchestration. Idle when not in progress.
- **Orchestration Start Time**: Date and time that the orchestration started.
- **Current Sequence Number**: Indicates for which member of the group orchestration is active. This number corresponds with the **Sequence Number** for the member.
- **Orchestration Timeout (in minutes)**: Value of **The Orchestration Group timeout (in minutes)** set on the **General** page when creating the group, or the **General** tab when editing the group.
- **Orchestration Group Member Timeout (in minutes)**: Value of **Orchestration Group member timeout (in minutes)** set on the **General** page when creating the group, or the **General** tab when editing the group.
- **Orchestration Group ID**: ID of the group, The ID is used in logs and the database.
- **Orchestration Group Unique ID**: Unique ID of the group, The Unique ID is used in logs and the database.
- **Last Modified Time**: The time the orchestration group was last modified (starting in version 2203).
- **Last Modified By**: The user that last modified the orchestration group (starting in version 2203).

## Orchestration groups details tabs

*(Introduced in version 2107*)

Starting in Configuration Manager version 2107, the following two tabs were added to the details pane for **Orchestration Groups** to assist you with monitoring the [script approval](create-orchestration-groups#approvals-for-orchestration-group-scripts): 

- **Summary**: Contains information about the selected orchestration group, including the **Approval State** of scripts.
- **Scripts**: Lists information about pre and post-scripts, including the timeout, approver, and approval state for each script.

## Monitor orchestration group members

In the **Orchestration Group** node, select an orchestration group. In the ribbon, select **Show Members**. You can see the members of the group, and their orchestration status. Add any of the following columns to get information about the members:

- **Name**: Device name of the orchestration group member
- **Current State**: Gives you the state of the member device.
    - **In progress** during orchestration.
    - **Waiting**: Indicates the client is waiting on the lock for its turn to install updates.
    - **Idle** when orchestration is complete or not running.
- **State Code**: You can right-click on the Orchestration Group member and select **Reset Orchestration Group Member**. This reset allows you to rerun orchestration. States include:
    - Idle
    - Waiting, the device is waiting its turn
    - In progress, installing an update
    - Failed
    - Reboot pending
- **Lock Acquired Time**: Locks are requested by the client based on its policy. Once the client acquires a lock, orchestration is triggered on it. -**Last State Reported Time**: Time the member last reported a state.
- **Sequence Number**: The client's location in the queue for installing updates.
- **Site Code**: The site code for the member.
- **Client Activity**: Tells you if the client is active or inactive.
- **Primary User(s)**: Which users are primary for the device.
- **Client Type**: What type of device the client is.
- **Currently Logged on User**: Which user is currently logged on to the device.
- **OG ID**: ID of the orchestration group the member belongs to.
- **OG Unique ID**: Unique ID of the orchestration group the member belongs to.
- **Resource ID**: Resource ID of the device.

## Alerts for orchestration groups

*(Introduced in version 2203)*

Starting in version 2203, if an orchestration group fails, an alert is generated. In the Configuration Manager console, go to the **Monitoring** workspace, expand **Alerts**, and then select **Active Alerts** or **All Alerts**. For more information about alerts, see [Configure alerts](../../core/servers/manage/configure-alerts).

## Log files

Use the following log files on the site server to help monitor and troubleshoot:

### Site server

- **Policypv.log**: shows that the site targets the orchestration group to the clients.
- **SMS\_OrchestrationGroup.log**: shows the behaviors of the orchestration group.

### Client

- **MaintenanceCoordinator.log**: Shows the lock acquisition, update installation, pre and post-scripts, and lock release process.
- **UpdateDeployment.log**: Shows the update installation process.
- **PolicyAgent.log**: Checks if the client is in an orchestration group.