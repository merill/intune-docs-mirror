---
layout: Conceptual
title: Requirements for Windows Autopilot device association | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/device-preparation/device-association/requirements
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
description: Software, networking, licensing, and RBAC requirements for Windows Autopilot device association.
ms.date: 2026-08-25T00:00:00.0000000Z
ms.collection:
- M365-modern-desktop
ms.topic: article
locale: en-us
document_id: db5eb83f-c5da-eb12-2197-90ffc59398e6
document_version_independent_id: db5eb83f-c5da-eb12-2197-90ffc59398e6
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/device-preparation/device-association/requirements.md
site_name: Docs
depot_name: MSDN.autopilot
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.autopilot/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-preparation/device-association/requirements
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/device-preparation/device-association/requirements.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/19ec6774-09b8-473e-a17e-b17b518bbad7
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ade36b61-c646-4bd8-87ee-f3a843461962
platformId: 53ceb5ed-3bd4-c8a2-7ebc-5f0bf88555f6
---

# Requirements for Windows Autopilot device association | Microsoft Learn

The list of requirements for Windows Autopilot device association is organized into four categories:

- **Software** - OS requirements.
- **Networking** - Networking requirements.
- **Licensing** - Licensing requirements.
- **RBAC** - RBAC permissions required for Windows Autopilot device association.

Select the appropriate tab to see the relevant requirements:

# [Software](#tab/software)
### Software requirements

Important

Device association requires a **physical device**. Virtual machines aren't supported.

#### Windows 11

- Windows 11, version 25H2 with [KB5120998](https://support.microsoft.com/help/5120998) or later.
- Windows 11, version 24H2 with [KB5120998](https://support.microsoft.com/help/5120998) or later.

The following editions are supported:

- Windows 11 Pro.
- Windows 11 Pro Education.
- Windows 11 Pro for Workstations.
- Windows 11 Enterprise.
- Windows 11 Education.
- [Windows 11 Enterprise LTSC](/en-us/windows/whats-new/ltsc/overview).

#### Trusted Platform Module (TPM)

Device association requires a **physical device**—virtual machines aren't supported. Each device must have **TPM 2.0**, enabled and in a good state. The TPM shouldn't be in **Reduced Functionality Mode**. TPM attestation is enforced during association: device association uses the TPM to attest the device's identity before enrollment.

# [Networking](#tab/networking)
### Networking requirements

Device association builds on Windows Autopilot device preparation and has the same baseline networking requirements. For the full list of endpoints and network configuration, see [Windows Autopilot device preparation requirements](../requirements?tabs=networking).

In addition to the baseline requirements, allow HTTPS access over TCP port 443 to the following endpoints:

- `https://ztd.dds.microsoft.com`
- `https://peapdamaa1.eus2.attest.azure.net`
- `https://peapdamaa2.wus2.attest.azure.net`
- `https://peapdamaa3.cus.attest.azure.net`
- `https://peapdamaa5.cus.attest.azure.net`
- `https://peapdamaa6.neu.attest.azure.net`
- `https://peapdamaa7.weu.attest.azure.net`
- `https://peapdamaa8.sasia.attest.azure.net`
- `https://peapdamaa9.eau.attest.azure.net`
- `https://peapdamaa19.wus2.attest.azure.net`
- `https://peapdamaa86.cin.attest.azure.net`
- `https://peapdamaa89.jpe.attest.azure.net`
- `https://peapdamaa93.weu.attest.azure.net`

# [Licensing](#tab/licensing)
### Licensing requirements

Device association is part of Windows Autopilot device preparation and has the same licensing requirements. For the full list of supported subscriptions, see [Windows Autopilot device preparation requirements](../requirements?tabs=licensing).

# [RBAC](#tab/rbac)
### Required RBAC permissions

The following role-based access control (RBAC) permissions are required in an Intune role for Windows Autopilot device association.

#### Required for configuring the device preparation policy

- **Device configurations**
    - Read
    - Delete
    - Create
    - Update
- **Enrollment programs**
    - Enrollment time device membership assignment
- **Managed apps**
    - Read
- **Mobile apps**
    - Read
- **Organization**
    - Read

#### Required for managing associated devices

- **Enrollment programs**
    - Read device
    - Create device
    - Delete device
- **Device configurations**
    - Assign

To create a custom role with these permissions for use with Windows Autopilot device association:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Tenant administration** &gt; **Roles**.
3. Select **Create** &gt; **Intune role**.
4. On the **Basics** page, enter a name and description for the custom role, and then select **Next**.
5. On the **Permissions** page, set each of the permissions listed previously to **Yes**. Leave all other permissions at the default of **No**.
6. On the **Scope tags** page, select **Next**.
7. On the **Review + create** page, verify that all permissions are correct, and then select **Create**.

The new custom role can now be assigned to users who manage Windows Autopilot device association. For more information, see [Role-based access control (RBAC) with Microsoft Intune](/en-us/intune/fundamentals/role-based-access-control/overview).

---