---
layout: Conceptual
title: Manual registration of devices for Windows Autopilot | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/manual-registration
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
description: Manual registration overview.
ms.date: 2025-03-27T00:00:00.0000000Z
ms.topic: how-to
ms.collection:
- M365-modern-desktop
- m365initiative-coredeploy
locale: en-us
document_id: dd1c237d-d25d-e10b-f19e-e4cbd093e4e9
document_version_independent_id: dd1c237d-d25d-e10b-f19e-e4cbd093e4e9
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/manual-registration.md
site_name: Docs
depot_name: MSDN.autopilot
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.autopilot/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: manual-registration
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/manual-registration.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
platformId: ea01639a-c5be-424f-59e7-899b90998775
---

# Manual registration of devices for Windows Autopilot | Microsoft Learn

Ideally, the OEM, reseller, or distributor from which the device was purchased performs the registration of a device with Windows Autopilot. However it's also possible to register devices manually. A device might need to be registered manually if:

- The device was obtained from a non-participant device manufacturer or reseller.
- The device is a virtual machine (VM).
- The device doesn't otherwise qualify for automatic registration, such as an existing legacy device.

The following diagram shows how manual registration and OEM registration might be used to deploy both new and existing devices with Windows Autopilot.

![Screenshot that shows Windows Autopilot device registration process.](images/image2.png)

For a list of participant device manufacturers and device resellers, see [Windows Autopilot device manufacturers and resellers](https://www.microsoft.com/microsoft-365/windows/windows-autopilot).

To [manually register a device](add-devices), a device's hardware hash first has to be captured. Once this process is completed, the resulting hardware hash can be uploaded to the Windows Autopilot service. Because this process requires booting the device into Windows to obtain the hardware hash, manual registration is intended primarily for testing and evaluation scenarios.

Note

Customers can only register devices with a hardware hash. Other methods (PKID, tuple) are available through OEMs or CSP partners as described in the previous sections.

## Platforms for device registration

After the hardware hashes are captured from existing devices, they can be uploaded in any of the following ways:

- [Microsoft Intune](add-devices) - Intune is the preferred mechanism for all customers.

    - The [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) is used for Intune device enrollment.
- Partner Center - Partner Center is used by CSP partners to register devices on behalf of customers.
- Microsoft 365 Business & Office 365 Admin - Microsoft 365 Business & Office 365 Admin is typically used by small and medium businesses (SMBs) who manage their devices using Microsoft 365 Business.
- Microsoft Store for Business - Since Microsoft Store for Business is deprecated, use another method instead.

Important

Microsoft Store for Business and Microsoft Store for Education is deprecated. The current capabilities of free apps can be used while they're still available. For more information about this change, see [Evolving the Microsoft Store for Business and Education](https://techcommunity.microsoft.com/t5/windows-it-pro-blog/evolving-the-microsoft-store-for-business-and-education/ba-p/2569423) and [Microsoft Store for Business and Education](/en-us/microsoft-store/).

A summary of each platform's capabilities is provided in the following table:

| Platform/Portal | Register devices? | Create/Assign profile | Acceptable Device ID |
| --- | --- | --- | --- |
| OEM Direct API | YES - 1000 at a time max | NO | Tuple or PKID |
| [Partner Center](/en-us/partner-center/autopilot) | YES - 1000 at a time max | YES^3^ | Tuple or PKID or 4K HH |
| [Intune](add-devices) | YES - 500 at a time max | YES^12^ | 4K HH |
| [Microsoft Store for Business](/en-us/microsoft-store/add-profile-to-devices#manage-autopilot-deployment-profiles) | YES - 1000 at a time max | YES^4^ | 4K HH |
| [Microsoft 365 Business Premium](/en-us/microsoft-365/business/create-and-edit-autopilot-profiles) | YES - 1000 at a time max | YES^3^ | 4K HH |

- **^1^** Microsoft recommended platform to use.
- **^2^** Intune license required.
- **^3^** Feature capabilities are limited.
- **^4^** Device profile assignment will be retired from Microsoft Store for Business in the coming months.

For more information about device IDs, see the following articles:

- [Device identification](registration-overview#device-identification).
- [Windows Autopilot device guidelines](autopilot-device-guidelines).
- [Add devices to a customer account](/en-us/partner-center/autopilot).

## Manually register devices with Windows Autopilot

For a how to guide on how to register devices with Windows Autopilot, see one of the following links:

- [Manually register devices with Windows Autopilot](add-devices).
- [User-driven Microsoft Entra join: Register devices as Windows Autopilot devices](tutorial/user-driven/azure-ad-join-register-device).
- [User-driven Microsoft Entra hybrid join: Register devices as Windows Autopilot devices](tutorial/user-driven/hybrid-azure-ad-join-register-device).
- [Pre-provision Microsoft Entra join: Register devices as Windows Autopilot devices](tutorial/pre-provisioning/azure-ad-join-register-device).
- [Pre-provision Microsoft Entra hybrid join: Register devices as Windows Autopilot devices](tutorial/pre-provisioning/hybrid-azure-ad-join-register-device).
- [Self-deploying mode: Register devices as Windows Autopilot devices](tutorial/self-deploying/self-deploying-register-device).