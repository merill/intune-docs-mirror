---
layout: Conceptual
title: Troubleshoot tenant attach and device actions - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/troubleshoot
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
description: Troubleshoot tenant attach and device actions for Configuration Manager.
ms.date: 2022-07-11T00:00:00.0000000Z
ms.topic: troubleshooting
ms.subservice: core-infra
ms.collection: tier3
locale: en-us
document_id: d7ecedd8-c416-069c-e521-e049921da402
document_version_independent_id: 1076480c-bfa1-5ed4-2ac9-132e73ef1a8b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/tenant-attach/troubleshoot.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/tenant-attach/troubleshoot
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/tenant-attach/troubleshoot.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: 05848870-6c7b-e665-e59f-c87035ea19b8
---

# Troubleshoot tenant attach and device actions - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Configuration Manager clients can be synced to Microsoft Intune admin center. Some client actions can be run from the Microsoft Intune admin center on the synchronized clients.

The available actions are:

- Sync Machine Policy
- Sync User Policy
- App Evaluation Cycle

[![Device overview in Microsoft Intune admin center](media/3555758-device-overview-actions.png)](media/3555758-device-overview-actions.png#lightbox)

When an admin runs an action from Microsoft Intune admin center, the notification request is forwarded to Configuration Manager site, and from the site to the client.

## Log files

Use the following logs located on the service connection point:

- **CMGatewaySyncUploadWorker.log**
- **CMGatewayNotificationWorker.log**

Use the following logs located on the management point:

- **BgbServer.log**

Use the following logs located on the client:

- **CcmNotificationAgent.log**

## Review your upload

1. Open **CMGatewaySyncUploadWorker.log** from &lt;ConfigMgr install directory&gt;\Logs.
2. The next sync time is noted by log entries similar to `Next run time will be at approximately: 02/28/2020 16:35:31`.
3. For device uploads, look for log entries similar to `Batching N records`. **N** is the number of changed devices uploaded since the last upload.
4. The upload occurs every 15 minutes for changes. Once changes are uploaded, it may take an additional 5 to 10 minutes for client changes to appear in **Microsoft Intune admin center**.

## Configuration Manager components and log flow

- **SMS\_SERVICE\_CONNECTOR**: Uses the Gateway Notification Worker for processing the notification from Microsoft Intune admin center.
- **SMS\_NOTIFICATION\_SERVER**: Gets the notification and creates a client notification.
- **BgbAgent**: The client gets task and runs the requested action.

### SMS\_SERVICE\_CONNECTOR

When an action is initiated from the Microsoft Intune admin center, **CMGatewayNotificationWorker.log** processes the request.

```text
Received new notification. Validating basic notification details...
Validating device action message content...
Authorized to perform client action. TemplateID: RequestMachinePolicy TenantId: aaaabbbb-0000-cccc-1111-dddd2222eeee AADUserID:     aaaabbbb-0000-cccc-1111-dddd2222eeee
Forwarded BGB remote task. TemplateID: 1 TaskGuid: a43dd1b3-a006-4604-b012-5529380b3b6f TaskParam: TargetDeviceIDs: 1
```

1. A notification is received from Microsoft Intune admin center.

    ```text
    Received new notification. Validating basic notification details..
    ```
2. User and device actions are validated.

    ```text
    Validating device action message content...
    Authorized to perform client action. TemplateID: RequestMachinePolicy TenantId: aaaabbbb-0000-cccc-1111-dddd2222eeee AADUserID:     aaaabbbb-0000-cccc-1111-dddd2222eeee
    ```
3. The remote task is forwarded to the SMS\_NOTIFICATION\_SERVER.

    ```text
    Forwarded BGB remote task. TemplateID: 1 TaskGuid: a43dd1b3-a006-4604-b012-5529380b3b6f TaskParam: TargetDeviceIDs: 1
    ```

### SMS\_NOTIFICATION\_SERVER

Once the message is sent to the SMS\_NOTIFICATION\_SERVER, a task is sent from the management point to the corresponding client. You'll see the below in the **BgbServer.log**, which is on the management point:

```text
Get one push message from database.
Starting to send push task (PushID: 7 TaskID: 8 TaskGUID: A43DD1B3-A006-4604-B012-5529380B3B6F TaskType: 1 TaskParam: ) to 1 clients  with throttling (strategy: 1 param: 42)
```

### BgbAgent

The last step occurs on the client and can be seen in the **CcmNotificationAgent.log**. Once the task is received, it will request scheduler to perform the action. When the action is performed, you'll see a confirmation message:

```text
Receive task from server with pushid=7, taskid=8, taskguid=A43DD1B3-A006-4604-B012-5529380B3B6F, tasktype=1 and taskParam=

Send Task response message <BgbResponseMessage TimeStamp="2020-01-21T15:43:43Z"><PushID>8</PushID><TaskID>9</TaskID><ReturnCode>1</ReturnCode></BgbResponseMessage> successfully.
```

## Common issues

### Unauthorized to perform client action

If the account that is logged into the Microsoft Intune Admin Center doesn't have the required permissions in Configuration Manager, you'll see an `Unauthorized` response in the **CMGatewayNotificationWorker.log**.

```text
Received new notification. Validating basic notification details..
Validating device action message content...
Unauthorized to perform client action. TemplateID: RequestMachinePolicy TenantId: aaaabbbb-0000-cccc-1111-dddd2222eeee AADUserID: bbbbcccc-1111-dddd-2222-eeee3333ffff
```

Ensure the user running the action from the Microsoft Intune admin center has the required permissions on Configuration Manager site. For more information, see [Microsoft Intune tenant attach prerequisites](prerequisites).

## Known issues

### Data synchronization failures

If you have issues viewing the tenant attach details in the Microsoft Intune admin center, it may be because of an issue with the hierarchy onboarding configuration. This issue can be caused by onboarding a hierarchy that's already onboarded.

You can also detect this issue from entries in the **GenericUploadWorker.log** and **CMGatewayNotificationWorker.log** files. For more information, see Example errors in log files that require resetting the tenant attach configuration.

#### Workaround for data synchronization failures

To reset the tenant attach configuration:

1. Offboard the hierarchy. For more information, see [Offboard from tenant attach](device-sync-actions#bkmk_offboard).
2. Wait at least two hours for the service to clean up the existing record.
3. Onboard the hierarchy again. For more information, see [Enable tenant attach](device-sync-actions).

#### Example errors in log files that require resetting the tenant attach configuration

##### Errors for AccountOnboardingInfo and DevicePost requests in GenericUploadWorker.log

```log
[OnboardScenario] Creating web request to: https://us.gateway.configmgr.manage.microsoft.com/api/gateway/AccountOnboardingInfo Method: POST Activity ID: ccccdddd-2222-eeee-3333-ffff4444aaaa Timeout: 00:02:00
[OnboardScenario] Response from https://us.gateway.configmgr.manage.microsoft.com/api/gateway/AccountOnboardingInfo is: 400 (Bad Request)
Response status code: 400 (BadRequest) Activity ID: a579728b-eca0-4144-80ac-eea25ee5bcf6
Unexpected exception for worker GenericUploadWorker
Exception details:
[Critical][GenericUploadWorker][0][System.Net.WebException][0x80131509]
The remote server returned an error: (400) Bad Request.    at Microsoft.ConfigurationManager.ServiceConnector.ExtensionMethods.<GetResponseAsync>d__13.MoveNext()

[UploadDelta_HelpdeskUpload] Response from https://us.gateway.configmgr.manage.microsoft.com/api/gateway/DevicePost is: 401 (Unauthorized)
Response status code: 401 (Unauthorized) Activity ID: 6daac983-5f94-464e-b1bd-9b634a051d1d
[WebException]: Failed to upload data to 'https://us.gateway.configmgr.manage.microsoft.com/api/gateway/DevicePost'
Exception details:
[Warning][GenericUploadWorker][0][System.Net.WebException][0x80131509]
The remote server returned an error: (401) Unauthorized.    at Microsoft.ConfigurationManager.ServiceConnector.ExtensionMethods.<GetResponseAsync>d__13.MoveNext()
```

##### Errors for device actions in CMGatewayNotificationWorker.log

```log
[GetNotifications] Response from https://us.gateway.configmgr.manage.microsoft.com/api/gateway/Notification is: 401 (Unauthorized)
Response status code: 401 (Unauthorized) Activity ID: 4c536a72-fd7f-4d08-948a-3e65d2129e44
Web exception when getting new notification
Exception details:
[Warning][CMGatewayNotificationWorker][0][System.Net.WebException][0x80131509]
The remote server returned an error: (401) Unauthorized.    at Microsoft.ConfigurationManager.ServiceConnector.ExtensionMethods.<GetResponseAsync>d__13.MoveNext()
Response in the web exception: {"Message":"An error has occurred."}
```

### Specific devices don't synchronize

It's possible that specific devices, which are Configuration Manager clients, won't be uploaded to the service.

**Impacted devices:** If a device is a distribution point that uses the same PKI certificate for both the distribution point functionality and its client agent, then the device won't be included in the tenant attach device sync.

**Behavior:** When performing tenant attach during the on-boarding phase, a full sync is performed the first time. Subsequent sync cycles are delta synchronizations. Any update to the impacted devices will cause the device to be removed from the sync.

### When the Configuration Manager site is configured to require multi-factor authentication, most tenant attach features don't work

**Scenario:** If the [SMS provider](../core/plan-design/hierarchy/plan-for-the-sms-provider) machine that communicates with the [service connection point](../core/servers/deploy/configure/about-the-service-connection-point) is configured to use multi-factor authentication, you can't install applications, run CMPivot queries, and perform other actions from the admin console. You receive an error code 403, forbidden.

**Workaround:** The current workaround is to configure the on-premises hierarchy to the default authentication level of **Windows authentication**. For more information, see the [Authentication section in the SMS provider article](../core/plan-design/hierarchy/plan-for-the-sms-provider#authentication).