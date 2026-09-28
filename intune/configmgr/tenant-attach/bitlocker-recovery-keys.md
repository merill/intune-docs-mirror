---
layout: Conceptual
title: Tenant attach - BitLocker recovery keys - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/bitlocker-recovery-keys
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
description: View BitLocker recovery keys for tenant-attached devices from the Microsoft Intune admin center.
ms.date: 2022-01-25T00:00:00.0000000Z
ms.topic: how-to
ms.subservice: core-infra
ms.collection: tier3
locale: en-us
document_id: 875edf49-7aac-7af0-0ee3-0cda59c7824c
document_version_independent_id: 95f03c89-c8a7-96fc-0f88-9fc1392d6a00
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/tenant-attach/bitlocker-recovery-keys.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/tenant-attach/bitlocker-recovery-keys
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/tenant-attach/bitlocker-recovery-keys.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 4ef7f969-5406-9665-24cd-135ae36e2bab
---

# Tenant attach - BitLocker recovery keys - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

You can get BitLocker recovery keys for a tenant-attached device from the Microsoft Intune admin center. For example, a help desk technician who doesn't have access to Configuration Manager could use the web-based admin center to help an end user get a recovery key for their device.

## Prerequisites

- Configuration Manager site version 2107 or later

    To support devices that are joined to Microsoft Entra ID, install the [update rollup](../hotfix/2107/11121541) for Configuration Manager version 2107.
- Apply a Configuration Manager [BitLocker management](../protect/deploy-use/bitlocker/deploy-management-agent) policy to the device.

## Permissions

The administrative user needs the following permissions:

- On the **Collection** object that's scoped to a collection that includes the device:

    - **Read**
    - **Read BitLocker Recovery Key**
- An [Intune role](../../fundamentals/role-based-access-control/overview) assigned to the user

## View recovery keys

1. In a browser, go to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. In the admin center, select **Devices** and then **All Devices**.
3. Select a device that's synced from Configuration Manager via [tenant attach](device-sync-actions).
4. Select **Recovery keys** in the device menu. You'll see the list of encrypted drives on the device.
5. To display a recovery key for a drive, select **Show recovery key**. This action reveals the recovery key, which causes the device to rotate its recovery key. Select **Yes** to continue and view the key.
6. A pane to the right displays the device information, including the BitLocker recovery key. Select the copy icon to copy the key to the clipboard. This action makes it easier to share with a user.

![Recovery Keys pane in the Microsoft Intune admin center.](media/6979225-bitlocker-recovery-key.png)