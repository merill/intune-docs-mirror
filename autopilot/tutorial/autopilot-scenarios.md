---
layout: Conceptual
title: Windows Autopilot scenarios | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/tutorial/autopilot-scenarios
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
description: Describes the different Windows Autopilot scenarios.
ms.date: 2025-06-13T00:00:00.0000000Z
ms.topic: tutorial
ms.collection:
- essentials-get-started
locale: en-us
document_id: 88dcecf5-aa89-bee8-3eb3-12cf9b55081a
document_version_independent_id: 88dcecf5-aa89-bee8-3eb3-12cf9b55081a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/tutorial/autopilot-scenarios.md
site_name: Docs
depot_name: MSDN.autopilot
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.autopilot/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: tutorial/autopilot-scenarios
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/tutorial/autopilot-scenarios.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
platformId: 1cca9729-ccd6-814a-43e9-0dbf12ba54ce
---

# Windows Autopilot scenarios | Microsoft Learn

Due to different environments, different configurations, and different needs, Windows Autopilot offers several different scenarios. The following table summarizes the scenarios that are available in Windows Autopilot:

| **Scenario** | **Purpose** | **Description** |
| --- | --- | --- |
| **Windows Autopilot user-driven mode** | Device for a single user | User runs deployment |
| **Windows Autopilot for pre-provisioned** | Device for a single user | Deployment is split between IT admin/OEM/reseller and user |
| **Windows Autopilot self-deploying mode** | Kiosk device or device for multiple users | Deployment is completely automated |
| **Windows Autopilot for existing devices** | Prepare device where Windows OS needs to be reinstalled for a Windows Autopilot deployment | Utilizes Microsoft Configuration Manager to install a fresh Windows OS on an existing device before running a Windows Autopilot deployment |
| **Windows Autopilot Reset** | Resets an existing device back to the factory default installation of Windows | Utilizes the existing installation of Windows on a device to rebuild Windows and restore it back to the factory installation of Windows |

Note

This tutorial is for **Windows Autopilot**. For the **Windows Autopilot device preparation** tutorial, see [Windows Autopilot device preparation scenarios](../device-preparation/tutorial/scenarios).

## Scenario capabilities

The following table compares the different capabilities for each Windows Autopilot scenario:

| Scenario | **User-driven** | **Pre-provisioned** | **Self-deploying** | **Existing devices** | **Reset** |
| --- | --- | --- | --- | --- | --- |
| **Supports Microsoft Entra join** | Yes | Yes | Yes | Yes | Yes |
| **Supports Microsoft Entra hybrid join** | Yes | Yes | No | Yes | No |
| **Deployment requires interaction by user** | Yes | Yes | No | NA | Local reset |
| **Deployment requires interaction by IT admin/OEM/reseller** | No | Yes | No | Yes | Remote reset |
| **Supports assigning user to device** | Yes | Yes | No | NA | NA |
| **Minimizes time user interacts with deployment** | No | Yes | Yes | NA | NA |
| **User authenticates** | Yes | User flow | No | NA | Local reset |
| **TPM authenticates** | No | Technician flow | Yes | NA | NA |
| **Needs to be registered as a Windows Autopilot device before deployment** | Yes | Yes | Yes | No | Yes |

Note

The **Windows Autopilot for existing devices** scenario is a method to completely reinstall Windows on a device in preparation to run a Windows Autopilot deployment. However the Windows Autopilot for existing devices scenario itself isn't technically a Windows Autopilot deployment. After the Windows Autopilot for existing devices process completes, it automatically runs a Windows Autopilot scenario.

The above table lists what the Windows Autopilot for existing devices scenario can potentially support. However, a given Windows Autopilot scenario might not always be supported once the **Windows Autopilot for existing devices** scenario completes.

## Scenario pros and cons

The following table describes the pros and cons of each Windows Autopilot scenario during the deployment process.

| **Scenario** | **Pros** | **Cons** |
| --- | --- | --- |
| **User-driven** | • Requires no interaction from admin/OEM/reseller.  • Doesn't require [TPM attestation](/en-us/windows-server/identity/ad-ds/manage/component-updates/tpm-key-attestation) so works on physical devices and VMs. | • Takes longer for user than the pre-provisioned scenario since user has to go through both device ESP and user ESP. |
| **Pre-provisioned** | • Faster for user since IT admin/OEM/reseller handles bulk of device ESP during the technician flow. | • Requires interaction by IT admin/OEM/reseller.  • Requires [TPM attestation](/en-us/windows-server/identity/ad-ds/manage/component-updates/tpm-key-attestation) during technician flow so only works on physical devices with supported TPM (doesn't work in VMs even with virtual TPM). |
| **Self-deploying** | • Requires no interaction from user or admin/OEM/reseller. | • Can't assign a user to the device.  • User ESP doesn't run during the Windows Autopilot deployment since no user is assigned.  • Requires [TPM attestation](/en-us/windows-server/identity/ad-ds/manage/component-updates/tpm-key-attestation) so only works on physical devices with supported TPM (doesn't work in VMs even with virtual TPM).  • Doesn't support Microsoft Entra hybrid join devices. |
| **Existing devices** | • Can use custom images.  • Can use ConfigMgr task sequences.  • Can reinstall a fresh copy of Windows in cases of severe corruption in Windows installation.  • Good scenario to upgrade a device from domain joined or Microsoft Entra hybrid join to Microsoft Entra join. | • Requires Microsoft Configuration Manager.  • Not an actual Windows Autopilot deployment so doesn't work on its own - only works alongside one a supported Windows Autopilot scenario.  • Takes longer since device has to undergo both task sequence and Windows Autopilot deployment.  • JSON file only supports user-driven Windows Autopilot scenarios.  • Pre-provisioning and self-deploying AWindows utopilot scenarios are only supported when the device is already a Windows Autopilot device and there's a Windows Autopilot profile assigned to the device. |
| **Reset** | • Easily allows resetting an existing broken or repurposed device to a business ready state. | • Doesn't work if there's severe corruption in Windows installation.  • Doesn't support Microsoft Entra hybrid join devices. |

## Microsoft Entra join and Microsoft Entra hybrid join vs. Windows Autopilot scenarios

Microsoft Entra join and Microsoft Entra hybrid join aren't Windows Autopilot scenarios, but instead [device identity](/en-us/azure/active-directory/devices/overview) options. All Windows Autopilot scenarios support Microsoft Entra join, while only the **User-driven**, **Pre-provisioned**, and **Existing devices** scenarios support Microsoft Entra hybrid join. When deciding which Windows Autopilot scenario to use, keep in mind the following factors:

- Device identities currently being used in the environment.
- Device identities being used going forward.
- Possible device identities being used in the future.

Microsoft recommends deploying new devices as cloud-native using Microsoft Entra join. Deploying new devices as Microsoft Entra hybrid join devices isn't recommended, including through Windows Autopilot. Microsoft Entra join provides the best user experience. However, current environment configurations and restrictions might require the continued use of on-premises Active Directory. In scenarios where on-premises Active Directory is still needed, Microsoft Entra hybrid join can be used. However, consider moving new devices to Microsoft Entra join while keeping existing devices on Microsoft Entra hybrid join. Microsoft Entra hybrid join can also be seen as a way to transition from on-premises Active Directory to purely Microsoft Entra ID.

Also keep in mind that for the Windows Autopilot deployments that support Microsoft Entra hybrid join, Microsoft Entra hybrid join requires connectivity to a domain controller. If the device undergoing a Windows Autopilot deployment is a remote device and isn't able to connect to a domain controller either on-premises or via a VPN connection, then only Microsoft Entra join is an option.

For more information on Microsoft Entra join versus Microsoft Entra hybrid join, see the following articles:

- [Microsoft Entra joined vs. Microsoft Entry hybrid joined in cloud-native endpoints](/en-us/intune/solutions/cloud-native-endpoints/azure-ad-joined-hybrid-azure-ad-joined).
- [What is a device identity?](/en-us/azure/active-directory/devices/overview).
- [Learn more about cloud-native endpoints](/en-us/intune/solutions/cloud-native-endpoints/cloud-native-endpoints-overview).
- [Tutorial: Set up and configure a cloud-native Windows endpoint with Microsoft Intune](/en-us/intune/solutions/cloud-native-endpoints/cloud-native-windows-endpoints).
- [How to: Plan your Microsoft Entra join implementation](/en-us/azure/active-directory/devices/device-join-plan).
- [A framework for Windows endpoint management transformation](https://techcommunity.microsoft.com/t5/windows-it-pro-blog/a-framework-for-windows-endpoint-management-transformation/ba-p/2460684).
- [Understanding hybrid Azure AD and co-management scenarios](https://techcommunity.microsoft.com/t5/microsoft-endpoint-manager-blog/understanding-hybrid-azure-ad-join-and-co-management/ba-p/2221201).
- [Success with remote Windows Autopilot and hybrid Azure Active Directory join](https://techcommunity.microsoft.com/t5/intune-customer-success/success-with-remote-windows-autopilot-and-hybrid-azure-active/ba-p/2749353).

## Which Windows Autopilot scenario to use

Which Windows Autopilot scenario should be used depends on various factors including the environment and the needs of the organization. The first thing to account for is which type of device identity (Microsoft Entra ID or hybrid Microsoft Entra ID) is currently being used in the environment. Which device identity is being used may restrict which Windows Autopilot scenarios can be used in the environment.

The following guide makes general suggestions on which Windows Autopilot scenario to use:

### User-driven

- Windows Autopilot user-driven supports both Microsoft Entra join and Microsoft Entra hybrid join.
- The device is intended to be used primarily by a single user.
- If the device needs to be shipped and delivered directly to the end-user without IT admin intervention.
- If the OEM or reseller is unable to perform the technician flow of the Windows Autopilot pre-provision scenario.
- If virtual machines (VMs) need to undergo the Windows Autopilot deployment process.

### Pre-provisioned

- Windows Autopilot for pre-provisioned supports both Microsoft Entra join and Microsoft Entra hybrid join.
- The device is intended to be used primarily by a single user.
- The deployment time that the end-user experiences needs to be minimized.
- Is an IT admin, an OEM, or a reseller able to handle the technician flow and the first half of the deployment. If an IT admin handles the technician flow, then the device may need to be first shipped to the IT admin to perform the technician flow, followed by the device shipped or delivered to the end-user.
- In Microsoft Entra hybrid join scenarios, if the OEM or reseller is performing the technician flow, their environment must have connectivity to a domain controller for the organization.
- Windows Autopilot for pre-provisioned uses [TPM attestation](/en-us/windows-server/identity/ad-ds/manage/component-updates/tpm-key-attestation) for authentication during the technician flow so only devices that have a supported TPM are supported. For this reason, virtual machines (VMs) aren't supported even when the VM has a virtual TPM.

### Self-deploying mode

- Windows Autopilot self-deploying mode only supports Microsoft Entra join. It doesn't support Microsoft Entra hybrid join.
- The device is intended to be used as a kiosk device or by multiple users.
- If the device isn't going to be assigned to a user.
- The deployment needs to be automated as much as follow with no user interaction during the deployment process. For example, the end-user having to sign in to Microsoft Entra ID during the deployment process.
- Windows Autopilot self-deploying mode uses [TPM attestation](/en-us/windows-server/identity/ad-ds/manage/component-updates/tpm-key-attestation) for authentication during the technician flow so only devices that have a supported TPM are supported. For this reason, virtual machines (VMs) aren't supported even when the VM has a virtual TPM.

### Existing devices

- Windows Autopilot for existing devices isn't a Windows Autopilot deployment itself, but a method to prepare an existing device for a Windows Autopilot deployment. As part of the Windows Autopilot for existing devices deployment, a JSON file is added to the device. The JSON file defines which Windows Autopilot deployment to run once the Windows Autopilot for existing devices deployment completes.
- The device doesn't need to be a current Windows Autopilot device.
- On existing devices that are already part of the environment. For example, when repurposing a device and the Windows OS need to be reinstalled.
- On existing devices where the Windows OS needs to be reinstalled. For example, the previous Windows OS installation is corrupted and needs to be reinstalled, or if the hard drive of the device is replaced.
- For converting devices from Microsoft Entra hybrid join to Microsoft Entra join.
- When custom images of Windows installations are desired.
- When task sequences are desired to run complex application deployments.

### Reset

- Windows Autopilot Reset isn't a Windows Autopilot deployment itself, but a method to reset an existing Windows Autopilot device to a business ready state.
- The device needs to be registered as a Windows Autopilot device.
- Windows Autopilot Reset only supports existing Microsoft Entra join devices. It doesn't support existing Microsoft Entra hybrid join devices.
- When the current Windows installation is in a stable non-corrupted state. If the Windows installation is in a corrupted state, use Windows Autopilot for existing devices instead.
- When the device needs to repurposed, for example to a new user.
- When the device needs to be reset to resolve ongoing problems on the device. Sometimes it's better and quicker to reset a device than to troubleshoot and fix on going problems on the device.

## Next steps: Scenario walkthroughs

The following list contains links to Windows Autopilot scenario walkthroughs. The walkthroughs contain step by step instructions on how to configure each of the Windows Autopilot scenarios:

1. Windows Autopilot user-driven mode:
    1. [Microsoft Entra join](user-driven/azure-ad-join-workflow).
    2. [Microsoft Entra hybrid join](user-driven/hybrid-azure-ad-join-workflow).
2. Windows Autopilot for pre-provisioned deployment:
    1. [Microsoft Entra join](pre-provisioning/azure-ad-join-workflow).
    2. [Microsoft Entra hybrid join](pre-provisioning/hybrid-azure-ad-join-workflow).
3. [Windows Autopilot self-deploying mode](self-deploying/self-deploying-workflow).
4. [Windows Autopilot for existing devices](existing-devices/existing-devices-workflow).
5. [Windows Autopilot Reset](reset/autopilot-reset-overview).