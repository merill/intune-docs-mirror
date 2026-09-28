---
layout: Conceptual
title: Provisioning mode - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/osd/understand/provisioning-mode
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
description: Learn about client provisioning mode during the Configuration Manager task sequence.
ms.date: 2021-10-01T00:00:00.0000000Z
ms.subservice: osd
ms.topic: troubleshooting
ms.collection: tier3
locale: en-us
document_id: 57e0016e-cf49-89e2-6242-b67878fcbe9b
document_version_independent_id: 17fbd9cf-2c31-0778-6bad-fc656e5974fd
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/osd/understand/provisioning-mode.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/osd/understand/provisioning-mode
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/osd/understand/provisioning-mode.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/1ae5c491-970a-4062-8301-6336e69f9026
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/f2c3e52e-3667-4e8a-bf11-20b9eaccdc8c
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: ae1b8473-25cc-97db-fe2d-33169dc394be
---

# Provisioning mode - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

During an OS deployment task sequence, Configuration Manager places the client in provisioning mode. (An OS deployment task sequence includes in-place upgrade.) In this state, the client doesn't process policy from the site. This behavior allows the task sequence to run without risk of additional deployments running on the client. When the task sequence completes, either success or handled failure, it exits client provisioning mode.

If the task sequence unexpectedly fails, the client can be left in provisioning mode. For example, if the device restarts in the middle of task sequence processing, and it's unable to recover. An administrator must manually identify and fix clients in this state.

## Manually remove provisioning mode

If a client is left in provisioning mode, use this manual process to return the client to normal operation.

```PowerShell
Invoke-WmiMethod -Namespace root\CCM -Class SMS_Client -Name SetClientProvisioningMode -ArgumentList $false
```

Important

One of the changes made by this WMI method is setting a registry value, but it makes other changes as well. Just changing the registry value doesn't fully take the client out of provisioning mode. If you manually edit the registry, the client may exhibit unexpected behaviors.

## Client provisioning mode timeout

The task sequence sets a timestamp when it puts the client in provisioning mode. Every 60 minutes, a client in provisioning mode checks the duration of time since the timestamp. If it's been in provisioning mode for more than 48 hours, the client automatically exits provisioning mode and restarts its process.

48 hours is the default provisioning mode timeout value. You can adjust this timer on a device by setting the **ProvisioningMaxMinutes** value in the following registry key: `HKLM\Software\Microsoft\CCM\CcmExec`. The value is specified in minutes. If this value doesn't exist or is `0`, the client uses the default 48 hours.

The timestamp **ProvisioningEnabledTime** is located in the following registry key: `HKLM\Software\Microsoft\CCM\CcmExec`. The timestamp has a value of the last time the machine entered provisioning mode. The format is epoch (Unix timestamp) and is in UTC.

This timestamp is also reset to the current time when you manually place the machine in provisioning mode by using the following command:

```powershell
Invoke-WmiMethod -Namespace root\CCM -Class SMS_Client -Name SetClientProvisioningMode -ArgumentList $true
```

## Process flow diagrams

These diagrams show the process flow for the task sequence and the client.

### Task sequence

The following diagram shows how the task sequence sets provisioning mode:

![Flow diagram of task sequence setting provisioning mode.](media/3197824-ts-flow.png)

### Client remediation

The following diagram shows how the client exits provisioning mode:

![Flow diagram of client exiting provisioning mode.](media/3197824-client-flow.png)