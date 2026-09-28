---
layout: Conceptual
title: Setting the BitLocker encryption algorithm for Windows Autopilot devices | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/bitlocker
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
description: Microsoft Intune provides a comprehensive set of configuration options to manage BitLocker on Windows devices.
ms.date: 2025-04-02T00:00:00.0000000Z
ms.collection:
- M365-modern-desktop
ms.topic: how-to
locale: en-us
document_id: 3603e723-6fc8-5046-6167-bd366f528dc8
document_version_independent_id: 3603e723-6fc8-5046-6167-bd366f528dc8
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/bitlocker.md
site_name: Docs
depot_name: MSDN.autopilot
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.autopilot/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: bitlocker
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/bitlocker.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 7b0cedc4-2377-e288-cc3d-030a27513a6f
---

# Setting the BitLocker encryption algorithm for Windows Autopilot devices | Microsoft Learn

BitLocker [automatically encrypts](/en-us/windows-hardware/design/device-experiences/oem-bitlocker#bitlocker-automatic-device-encryption) internal drives during the out-of-box experience (OOBE) for devices that support [Modern Standby](/en-us/windows-hardware/design/device-experiences/modern-standby) or meet the [Hardware Security Testability Specification (HSTI)](/en-us/windows-hardware/test/hlk/testref/hardware-security-testability-specification). By default, BitLocker uses XTS-AES 128-bit used space only for automatic encryption.

With Windows Autopilot, BitLocker encryption settings can be configured to apply before automatic encryption starts. This configuration makes sure the default encryption algorithm or type isn't applied automatically. A device that receives these settings after encrypting automatically needs to be decrypted before changing the encryption algorithm.

## Encryption algorithm

BitLocker uses the specified BitLocker encryption algorithm when BitLocker is first enabled. During Windows Autopilot, BitLocker will be enabled after the device setup portion of the [enrollment status page](enrollment-status). The following encryption algorithms are available:

- AES-CBC 128-bit.
- AES-CBC 256-bit.
- XTS-AES 128-bit (default).
- XTS-AES 256-bit.

For more information about the recommended encryption algorithms to use, see [BitLocker Configuration Service Provider (CSP)](/en-us/windows/client-management/mdm/bitlocker-csp).

## Full disk or used space-only encryption

There are two types of encryption, full disk or used space-only. Configuration of [silent enablement](/en-us/intune/device-configuration/endpoint-security/encrypt-bitlocker-windows#silently-enable-bitlocker-on-devices) and hardware support for modern standby automatically determines the type of encryption used. The type of encryption used can be enforced by configuring the [SystemDrivesEncryptionType](/en-us/windows/client-management/mdm/bitlocker-csp) setting. Like the encryption algorithm, BitLocker uses the encryption type when BitLocker is first enabled. For more information on the expected encryption type behavior, see [Manage BitLocker policy](/en-us/intune/device-configuration/endpoint-security/encrypt-bitlocker-windows#full-disk-vs-used-space-only-encryption).

## Configure a BitLocker policy for Windows Autopilot devices

To make sure both the desired BitLocker encryption algorithm and the encryption are set before automatic encryption occurs for Windows Autopilot devices, follow these steps:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. In the **Home** screen, select **Endpoint security** in the left hand pane.
3. In the **Endpoint security | Overview** screen, expand **Manage**, and then select **Disk encryption**.
4. In the **Endpoint security | Disk encryption** screen. Select **+ Create Policy**.
5. In the **Create a profile** page that opens:

    1. Under **Platform**, select **Windows**.
    2. Under **Profile**, select **BitLocker**.
    3. Select the **Create** button.
6. In the **Basics** page of the **Create Policy** screen, enter a **Name** and optional **Description**, and then select the **Next** button.
7. In the **Configuration settings** page, configure the various BitLocker settings as desired, including the **Encryption method and cipher** and **Encryption type** settings:

    - **Encryption method and cipher**

        1. Expand the **BitLocker Drive Encryption** section.
        2. For **Choose drive encryption method and cipher strength**, select **Enabled**.
        3. For each of the drive types (Fixed data drives, Operating system drive, Removable data drives), select the desired encryption method and cipher from the drop-down menu. The default for each type is **XTS-AES 128-bit**.
    - **Encryption type**

        1. Expand the **Operating System Drives** section.
        2. For **Enforce drive encryption type on operating system drives**, select **Enabled**.
        3. For **Select the drive encryption type**, select the desired encryption type, either **Full encryption** or **Used Space Only encryption**, from the drop-down menu. The default is **Allow user to choose**.

    Once all BitLocker settings are configured as desired, select the **Next** button.
8. In the **Scope tags** page, select the **Next** button.

    Note

    **Scope tags** are optional. If a custom scope tag needs to be specified, do so at this page. For more information about scope tags, see [Use role-based access control and scope tags for distributed IT](/en-us/intune/fundamentals/role-based-access-control/scope-tags).
9. In the **Assignments** page, use the **Search by group name...** search box to find and add the Windows Autopilot device group. Once the Windows Autopilot device group is added and is listed under **Group**, make sure **Target type** is set to **Include**, and then select the **Next** button. For more information about assigning a policy, see [Assign policies in Microsoft Intune](/en-us/intune/device-configuration/assign-device-profile).

    Important

    Make sure that the Windows Autopilot device group selected in this step is a device group and not a user group.
10. In the **Review + create** page, review the settings to verify they're configured as desired, and then select the **Save** button.
11. Configure and assign an [Enrollment Status page (ESP)](enrollment-status) for the Windows Autopilot device. If an ESP isn't enabled, the BitLocker policy doesn't apply before encryption starts. For more information, see one of the following articles:

    - [Windows Autopilot Enrollment Status Page](enrollment-status).
    - [User-driven Microsoft Entra join: Configure and assign the Enrollment Status Page (ESP)](tutorial/user-driven/azure-ad-join-esp).
    - [User-driven Microsoft Entra hybrid join: Configure and assign the Enrollment Status Page (ESP)](tutorial/user-driven/hybrid-azure-ad-join-esp).
    - [Pre-provision Microsoft Entra join: Configure and assign the Enrollment Status Page (ESP)](tutorial/pre-provisioning/azure-ad-join-esp).
    - [Pre-provision Microsoft Entra hybrid join: Configure and assign the Enrollment Status Page (ESP)](tutorial/pre-provisioning/hybrid-azure-ad-join-esp).
    - [Self-deploying mode: Configure and assign the Enrollment Status Page (ESP)](tutorial/self-deploying/self-deploying-esp).