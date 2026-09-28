---
layout: Conceptual
title: Linux device enrollment guide for Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-enrollment/guide-linux
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
ms.subservice: enrollment
description: Enroll Linux devices in Intune using the Intune app. Set an overview of the administrator and end user tasks to enroll devices.
ms.date: 2026-03-31T00:00:00.0000000Z
ms.topic: article
ms.reviewer: arnab
locale: en-us
document_id: 690c7db4-4afc-52c1-3aca-5f8afc42e96a
document_version_independent_id: 690c7db4-4afc-52c1-3aca-5f8afc42e96a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-enrollment/guide-linux.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-enrollment/guide-linux
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-enrollment/guide-linux.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
platformId: 0eae5012-6bf7-1742-1b08-9ad2d2cc8bf2
---

# Linux device enrollment guide for Microsoft Intune - Microsoft Intune | Microsoft Learn

Linux devices can be enrolled in Intune. Once they're enrolled, they receive the policies you create. Users can use the Microsoft Edge browser to access organization resources.

This article includes an overview of the administrator and user tasks required to enroll Linux devices.

## Before you begin

For all Intune-specific prerequisites and configurations needed to prepare your tenant for enrollment, go to [Enrollment guide: Microsoft Intune enrollment](guide).

## Linux enrollment

Use for personal/BYOD and organization-owned devices running Linux.

| Feature | Use this enrollment option when |
| --- | --- |
| You use Ubuntu Desktop (Ubuntu 26.04 LTS and 24.04 LTS on x86/64). | ✅ |
| You use Ubuntu Server. | ❌ |
| You use RedHat Enterprise Linux 9 or 10. | ✅ |
| Devices are owned by the organization or school. | ✅ |
| Devices are personal or BYOD. | ✅ |
| You have new or existing devices. | ✅ |
| Need to enroll a few devices, or a large number of devices (bulk enrollment). | ❌  Bulk enrollment isn't supported. Each device needs to be enrolled using the Microsoft Intune App. |
| Devices are associated with a single user. | ✅ |
| Devices are user-less, such as kiosk or dedicated device. | ❌  The enrollment requires a user to sign in with an organization account. |
| Devices are managed by another MDM provider. | ❌  It might be possible to enroll Linux devices in Intune that are already enrolled in another MDM provider. This scenario hasn't been tested by Microsoft. |
| You use the device enrollment manager (DEM) account. | ❌  DEM accounts don't apply to Linux. |

## Administrator tasks

Other than having Intune setup, there are minimal administrator tasks with Linux enrollment.

- Be sure your devices are [supported](../fundamentals/ref-supported-platforms).
- Intune admins don't do anything to enable Linux enrollment in the Microsoft Intune admin center. It's automatically enabled. When users enroll their Linux devices, you see them in the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) &gt; **Devices** &gt; **By platform** &gt; **Linux**.
- Versions 2.0.2 and later of the Microsoft Identity Broker included with the Microsoft Intune app for Linux introduce a major architectural change from the previous Java‑based broker. When Linux devices update from earlier broker versions, Intune automatically re‑registers and re‑enrolls the devices and creates new Intune device IDs and Microsoft Entra device IDs for them. This behavior requires no user action, but we recommend that admins review device‑based assignments, filters, and Microsoft Entra ID group memberships that rely on device IDs to ensure that policies apply correctly.

## End user tasks

The following steps provide an overview. For the specific steps, go to [Enroll a Linux device in Intune](../user-help/enrollment/enroll-linux).

Tip

When end users install the OS, it's recommended to enable encryption on the hard disk. After the OS is installed, it can be difficult to enable encryption.

1. [Download and install Microsoft Edge browser](https://www.microsoft.com/edge) version 102.x and newer.
2. [Download and install the Microsoft Intune app for Linux](../user-help/company-portal/intune-app-linux). The install can take several minutes and requires a reboot. This app registers the device with Intune.
3. Users open the Intune app, and sign in with their organization account (`user@contoso.com`). After they sign in, the enrollment process starts. It's possible users might be prompted to configure other settings based on your compliance policies.
4. Users open Microsoft Edge and sign in with their organization account (`user@contoso.com`). After they sign in, they can access your organization's resources, like internal websites and Microsoft 365 apps.