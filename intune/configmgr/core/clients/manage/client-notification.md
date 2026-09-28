---
layout: Conceptual
title: Client notification - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/client-notification
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
description: Manage clients by taking immediate action from the central Configuration Manager console.
ms.date: 2022-04-08T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 971935f4-ea20-555f-e232-4c496a498e86
document_version_independent_id: b8868418-6d27-9526-364b-bbb4a756a812
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/manage/client-notification.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/manage/client-notification
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/manage/client-notification.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/e0ffb20c-01c6-407b-a9bd-29111652a1dc
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/3904bce4-d817-48cf-85fd-b6146fca83b7
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: d8c2b0ef-262c-c781-def0-9cee1fd5fafd
---

# Client notification - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

To take immediate action on remote clients, send a client notification action from the Configuration Manager console. Start these actions on an individual device or on a collection of devices.

## Actions

The following actions are on the ribbon in the Device or Collection group of the Home tab.

### Install client

Opens the **Install Client Wizard**. This wizard uses client push installation to install a Configuration Manager client. For more information, see [Client push installation](../deploy/deploy-clients-to-windows-computers#BKMK_ClientPush).

#### Permissions - Install client

This action requires the **Modify Resource** and **Read** permissions on the **Collection** object.

The following built-in roles have these permissions by default:

- Application Administrator
- Full Administrator
- Infrastructure Administrator
- Operations Administrator
- OS Deployment Manager

Add these permissions to any custom roles that need to push the client.

### Run script

Opens the **Run Script** wizard to run a PowerShell script on all of the clients in the collection. For more information, see [Create and run PowerShell scripts](../../../apps/deploy-use/create-deploy-scripts).

#### Permissions - Run script

This action requires the **Run Script** permission on the **Collection** object.

The following built-in roles have this permission by default:

- Full Administrator
- Infrastructure Administrator
- Operations Administrator

Add this permission to any custom roles that need to run scripts.

### Start CMPivot

Starts **CMPivot**, which runs real-time queries against the targeted devices. For more information, see [CMPivot](../../servers/manage/cmpivot).

#### Permissions - Start CMPivot

This action requires the **Run CMPivot** permission on the **Collection** object.

## Client notification

These actions are under the **Client notification** menu, on the ribbon in the Device or Collection group of the Home tab. You can start a **Client Notification** from the **Devices** node or within a collection membership view.

Note

Starting in version 2203, you can perform client notification actions, including **Run Scripts**, from the **Deployment Status** view. Use the right-click menu on either a group of clients in a **Category** or a single client in the **Asset details** pane to display the client notification actions.

#### Permissions - Client notification

Client notification actions require the **Notify Resource** permission on the Collection object. This permission applies to all actions under the **Client notification** menu.

The following built-in roles have this permission by default:

- Full Administrator
- Operations Administrator

Add this permission to any custom roles that need to use client notification actions.

### Download computer policy

Refresh the device policy. For more information, see [Initiate policy retrieval for a Configuration Manager client](manage-clients#start-policy-retrieval).

### Download user policy

Refresh the user policy.

### Collect discovery data

Trigger clients to send a discovery data record (DDR). For more information, see [Heartbeat discovery](../../servers/deploy/configure/about-discovery-methods#bkmk_aboutHeartbeat).

### Collect software inventory

Trigger clients to run a software inventory cycle. For more information, see [Introduction to software inventory](inventory/introduction-to-software-inventory).

### Collect hardware inventory

Trigger clients to run a hardware inventory cycle. For more information, see [Introduction to hardware inventory](inventory/introduction-to-hardware-inventory).

### Evaluate application deployments

Trigger clients to run an application deployment evaluation cycle. For more information, see [Schedule re-evaluation for deployments](../deploy/about-client-settings#schedule-re-evaluation-for-deployments).

### Evaluate software update deployments

Trigger clients to run a software updates deployment evaluation cycle. For more information, see [Introduction to software updates](../../../sum/understand/software-updates-introduction).

### Switch to the next software update point

Trigger clients to switch to the next available software update point. For more information, see [Software update point switching](../../../sum/plan-design/plan-for-software-updates#BKMK_SUPSwitching).

### Evaluate device health attestation

Trigger Windows 10 or later clients to check and send their latest device health state. For more information, see [Health attestation](../../servers/manage/health-attestation).

### Check Conditional Access compliance

Trigger clients to check compliance for Conditional Access policies. For more information, see [Conditional Access](../../../comanage/quickstart-conditional-access).

### Wake Up

Trigger devices configured to support Wake-on-LAN to wake up using other devices on the same subnet to send the Wake-on-LAN package. For more information, see [How to configure Wake on LAN](../deploy/configure-wake-on-lan).

### Restart

Trigger the selected devices to restart. For more information, see [Restart clients](manage-clients#restart-clients).

## Client diagnostics

Use the following actions to help troubleshoot clients:

- **Enable verbose logging**: Change the global log level for the CCM component to verbose, and enable debug logging.
- **Disable verbose logging**: Change the global log level to default, and disable debug logging.
- **Collect Client Logs**: The site sends a client notification message to the selected clients to gather the CCM logs. The client sends the logs to the management point using the same channel as software inventory file collection.  You don't need to enable software inventory in client settings.

    - The size limit for the compressed client logs is 100 MB.
    - Use [Resource Explorer](inventory/use-resource-explorer-to-view-software-inventory#bkmk_diag) manage and view these files.

    [![Collect client logs from the console.](media/4226618-collect-client-logs.png)](media/4226618-collect-client-logs.png#lightbox)

Important

- These actions only change the log verbosity, not the size or history. More verbose logging can generate more log content.
- The management point role also uses the CCM component. If the targeted device is also a management point, this action also applies to that role.

For more information about these settings, see [About log files](../../plan-design/hierarchy/about-log-files#client-and-management-point-logging-options).

Track the status of the task in the **diagnostics.log** on the client. When client logs are collected, additional information is logged in **MP\_SinvCollFile.log** on the management point and **sinvproc.log** on the site server.

Note

Starting in version 2107, you can inventory client log file settings such as log levels and size. Enable the hardware inventory class, **Client Diagnostics (CCM\_ClientDiagnostics)**. For more information, see [Enable or disable existing hardware inventory classes](inventory/extend-hardware-inventory#enable-or-disable-existing-classes).

### Prerequisites - Client diagnostics

- Update the target client to the latest version.
- Your Configuration Manager administrative user needs the **Notify resource** permission.

    The following built-in roles have this permission by default:

    - Full Administrator
    - Infrastructure Administrator

    Add this permission to any custom roles that need to use client notification actions.

### Cleanup aged client diagnostic files

Collected client logs are stored according to the software inventory file collection settings. The files are stored on the site server in the **Inboxes\sinv.box\FileCol** directory. There's no defined limit to the number of versions.

The maintenance task to delete aged diagnostic files varies depending on your Configuration Manager version:

- Version 2010 and later uses the **Delete Aged Collected Diagnostic Files** site maintenance task to delete diagnostic files.
- Version 2006 and earlier uses the **Delete Aged Collected Files** site maintenance task to delete diagnostic files.

For more information, see [Reference for maintenance tasks in Configuration Manager](../../servers/manage/reference-for-maintenance-tasks#delete-aged-collected-files).

## Endpoint Protection

The following actions are under the **Endpoint Protection** menu. This menu is on the ribbon in the Collection group of the Home tab. When you select one or more devices, these actions are on the **Selected Object** tab of the ribbon.

For more information, see [Endpoint Protection in Configuration Manager](../../../protect/deploy-use/endpoint-protection).

### Permissions - Endpoint Protection

This action requires the **Enforce Security** permission on the **Collection** object.

The following built-in roles have this permission by default:

- Full Administrator
- Endpoint Protection Manager
- Operations Administrator

Add this permission to any custom roles that need to trigger Endpoint Protection actions.

### Full Scan

Trigger Endpoint Protection or Windows Defender to run a *full* antimalware scan.

### Quick Scan

Trigger Endpoint Protection or Windows Defender to run a *quick* antimalware scan.

### Download Definition

Trigger Endpoint Protection or Windows Defender to download the latest antimalware definitions.

## Monitor client operations

Monitor the operations sent to clients by using the **Client Operations** node under the **Monitoring** workspace. For some instances, you can cancel the operation by using the **Cancel** option in the ribbon. Use the **Delete** option to remove the operation from the console's view.

[![Client Operations node in the Monitoring workspace.](media/client-operations-node.png)](media/client-operations-node.png#lightbox)