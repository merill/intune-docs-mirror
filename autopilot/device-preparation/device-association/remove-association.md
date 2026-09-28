---
layout: Conceptual
title: Remove a Windows Autopilot device association | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/device-preparation/device-association/remove-association
author: lenewsad
ms.author: lanewsad
ms.reviewer: madakeva
manager: laurawi
ms.service: windows-client
ms.subservice: autopilot
ms.suite: ems
breadcrumb_path: /autopilot/breadcrumb/toc.json
feedback_product_url: https://feedbackportal.microsoft.com/feedback/forum/ef1d6d38-fd1b-ec11-b6e7-0022481f8472
feedback_system: Standard
permissioned-type: public
uhfHeaderId: MSDocsHeader-Windows
description: Remove a Windows Autopilot device association by deleting the device from the Device association list in Intune or by clearing the Device Link UEFI variables on the device.
ms.date: 2026-09-11T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 3b2f5a0c-8d7b-e67b-a939-03f12aa8b163
document_version_independent_id: 3b2f5a0c-8d7b-e67b-a939-03f12aa8b163
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/device-preparation/device-association/remove-association.md
site_name: Docs
depot_name: MSDN.autopilot
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.autopilot/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-preparation/device-association/remove-association
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/device-preparation/device-association/remove-association.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
platformId: 15ef006b-7e2f-e76b-82f2-0b1aaa47c974
---

# Remove a Windows Autopilot device association | Microsoft Learn

When a device permanently leaves your organization—for example, when it's decommissioned or transferred to another organization—remove its Windows Autopilot device association so the device is no longer tied to your tenant. For an associated device, removal clears the trusted tenant affiliation from the device's UEFI storage. How you remove the association depends on whether the device has completed association in the out-of-box experience (OOBE).

Note

Removing a device from the **Device association** list in Intune doesn't clear the tenant affinity that's stored on an already associated device. To fully remove the association from an associated device, clear the association information on the device itself, and then delete the device from the **Device association** list.

## Remove device in a pre-associated state

If the device hasn't completed association in OOBE yet (its state is **Pre-associated**), delete it directly from the device list:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Go to **Devices** &gt; **Enrollment** &gt; **Device association** &gt; **Devices**.
3. Select the device, and then select **Delete**.

The device is removed from the list immediately.

## Remove device in an associated state

If the device already completed association (its state is **Associated**), the tenant affinity is stored in the device's UEFI firmware. Clear the association information on the device first, and then delete the device from Intune.

Before clearing the association, make sure the device is no longer enrolled with its mobile device management (MDM) provider as part of your decommissioning process. If the device remains enrolled, the MDM provider attempts to re-associate it on its next check-in.

The association is stored in the **Device Link** UEFI namespace. Clear all of the following variables to remove the association:

| UEFI namespace | Variable |
| --- | --- |
| `{B3DE75DA-819C-4FD5-9F01-C3D49E8CBBD7}` | `DeviceLinkId` |
| `{B3DE75DA-819C-4FD5-9F01-C3D49E8CBBD7}` | `DeviceLinkJwtCompressed` |
| `{B3DE75DA-819C-4FD5-9F01-C3D49E8CBBD7}` | `DeviceLinkJwtLastWrite` |
| `{B3DE75DA-819C-4FD5-9F01-C3D49E8CBBD7}` | `DeviceLinkCreationTimeUtc` |

Important

Clearing the Device Link UEFI variables only removes the association. It doesn't reset the TPM, unenroll the device, or delete the device's Microsoft Entra ID or Intune records.

### Delete the device from Intune

After you clear the association information on the device, remove the device record from Intune:

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), go to **Devices** &gt; **Enrollment** &gt; **Device association** &gt; **Devices**.
2. Select the device. The **Association state** changes to **Pending removal**.
3. Select **Delete** to remove the device from the list.

    Note

    The **Pending removal** state indicates that the removal request was submitted. The device disappears from the list once the process completes.