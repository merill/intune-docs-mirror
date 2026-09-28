---
layout: Conceptual
title: Windows Autopilot registration overview | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/registration-overview
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
description: Overview of Windows Autopilot device registration.
ms.date: 2025-03-25T00:00:00.0000000Z
ms.topic: how-to
ms.collection:
- M365-modern-desktop
- m365initiative-coredeploy
locale: en-us
document_id: 1111a24a-9142-fd58-ddaa-cc541d966a3f
document_version_independent_id: 1111a24a-9142-fd58-ddaa-cc541d966a3f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/registration-overview.md
site_name: Docs
depot_name: MSDN.autopilot
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.autopilot/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: registration-overview
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/registration-overview.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
platformId: 63e18905-6c75-fbf4-d4ff-bc9cff9bde9e
---

# Windows Autopilot registration overview | Microsoft Learn

Before a device is deployed using Windows Autopilot, the device must be registered with the Windows Autopilot deployment service.

Successful registration requires that two processes are complete:

1. The device's unique hardware identity (known as a hardware hash) is captured and uploaded to the Windows Autopilot service.
2. The device is associated to an Azure tenant ID.

Ideally, the OEM, reseller, or distributor performs both of these processes from which the devices were purchased. An OEM or other device provider uses the [registration authorization](registration-auth) process to perform device registration on behalf of the organization.

Registration can also be performed within the organization by collecting the hardware identity from new or existing devices and [uploading it manually](manual-registration). If devices meet certain requirements, they can also be configured for [automatic registration](automatic-registration) with Windows Autopilot. For more information about the ways in which devices can be registered with Windows Autopilot, see the following overview articles:

- [OEM registration](oem-registration)
- [Reseller, distributor, or partner registration](partner-registration)
- [Automatic registration](automatic-registration)
- [Manual registration](manual-registration)

When a Windows Autopilot device is registered, it automatically creates a Microsoft Entra object. The Windows Autopilot deployment process needs this object to identify the device before the user signs in. If the object is deleted, the device can fail to enroll through Windows Autopilot.

Important

The following type of devices shouldn't be registered as a Windows Autopilot device:

- [Microsoft Entra registered](/en-us/entra/identity/devices/concept-device-registration) devices, also known as "workplace joined" devices.
- [Intune MDM-only enrollment](/en-us/intune/device-enrollment/enroll-devices?tabs=byod-enrollment#windows-enrollment-methods) devices.

These options are intended for users to join personally owned devices to their organization's network. Windows Autopilot registered devices are registered as corporate owned devices.

If a device is already one of these two types of devices, to register is as a Windows Autopilot device, first remove it from Microsoft Intune and Microsoft Entra ID. For more information, see [Why is the join type for a device showing as "Microsoft Entra registered" instead of "Microsoft Entra joined"?](troubleshooting-faq#why-is-the-join-type-for-a-device-showing-as--microsoft-entra-registered--instead-of--microsoft-entra-joined--) and [Deregister a device](registration-overview#deregister-a-device).

If a profile isn't assigned to a Windows Autopilot device, it receives the default Windows Autopilot profile. If a device shouldn't go through Windows Autopilot, remove the Windows Autopilot registration.

## Terms

The following terms are used to refer to various steps in the registration process:

| **Term** | **Definition** |
| --- | --- |
| **Device registration** | Device registration happens when a device's hardware hash is associated with the Windows Autopilot service. This process can be automated for new enterprise devices manufactured by OEMs that are Windows Autopilot partners. |
| **Add devices** | Adding a device is the process of registering a device with the Windows Autopilot service (if it isn't already registered) **and associating it to a tenant ID**. |
| **Import devices** | Importing devices is the process of uploading a comma-separated-values (CSV) file that contains device information in order to manually add devices. The device information includes information such the model and serial number. |
| **Enroll devices** | Enrolling a device is the process of adding devices to Intune. |

## Device identification

To identify a device with Windows Autopilot, the device's unique hardware hash must be captured and uploaded to the service. As previously mentioned, this step is ideally done by the hardware vendor (OEM, reseller, or distributor) automatically associating the device with an organization. It's also possible to do identify a device with a [harvesting process](add-devices) that collects the device's hardware hash from within a running Windows installation.

The hardware hash contains details about the device, such as:

- Manufacturer.
- Model.
- Device serial number.
- Hard drive serial number.
- Details about when the ID was generated.
- Many other attributes that can be used to uniquely identify the device.

The hardware hash changes each time it's generated because it includes details about when it was generated. When the Windows Autopilot deployment service attempts to match a device, it considers changes like that. It also considers large changes such as a new hard drive, and is still able to match successfully. But large changes to the hardware, such as a motherboard replacement, wouldn't match, so a new hash would need to be generated and uploaded.

For more information about device IDs, see the following articles:

- [Windows Autopilot device guidelines](autopilot-device-guidelines).
- [Add devices to a customer account](/en-us/partner-center/autopilot).

## Windows Autopilot devices

Devices that are registered with the Windows Autopilot service are displayed in the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) under **Devices** &gt; **Enrollment** &gt; **Windows** &gt; **Windows Autopilot** &gt; **Devices**:

Note

Devices that are listed in Intune under **Devices** &gt; **Windows** &gt; **Windows devices** aren't the same as Windows Autopilot devices **Devices** &gt; **Enrollment** &gt; **Windows** &gt; **Windows Autopilot** &gt; **Devices**. Windows Autopilot devices are added to the list of **Windows devices** when both of the following are complete:

- The Windows Autopilot registration process is successful.
- A [licensed](requirements?tabs=licensing) user has signed in on the device.

## Deregister a device

Whenever a device permanently leaves an organization, the device should always be deregistered from Windows Autopilot. For example, the device leaves the organization for repair or because the device is at the end of its life cycle.

Below we describe the steps an admin would go through to deregister a device from Intune and Windows Autopilot.

### Delete from Intune

Before a device is deregistered from Windows Autopilot, it first has to be deleted from Intune. To delete a Windows Autopilot device from Intune:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. In the **Home** screen, select **Devices** in the left pane.
3. In the **Devices | Overview** screen, under **By platform**, select **Windows**.
4. Under **Device name**, find the device that needs to be deleted and then select the device. If necessary, use the **Search** box.
5. In the properties screen for the device, make a note of the serial number listed under **Serial number**.
6. After making a note of the serial number of the device, select **Delete** in the toolbar at the top of the page.
7. A warning dialog box appears to confirm the deletion of the device from Intune. Select **Yes** to confirm deleting the device.

### Deregister from Windows Autopilot using Intune

Once the device is deleted from Intune, it can then be deregistered from Windows Autopilot. This process includes required cleanup steps in Intune and Microsoft Entra ID to prevent orphaned or unrecoverable devices. To deregister a device from Windows Autopilot:

1. Make sure the device is deleted from Intune as described in the Delete from Intune section.
2. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
3. In the **Home** screen, select **Devices** in the left hand pane.
4. In the **Devices | Overview** screen, under **By platform**, select **Windows**.
5. In the **Windows | Windows devices** screen, under **Device onboarding**, select **Enrollment**.
6. In the **Windows | Windows enrollment** screen, under **Windows Autopilot**, select **Devices**.
7. In the **Windows Autopilot devices** screen that opens, under **Serial number**, find the device that needs to be deregistered by its serial number as determined in the Delete from Intune section. If necessary, use the **Search by serial number** box.
8. Select the device by selecting the checkbox next to the device.
9. Select the extended menu icon (`…`) on the far right end of the line containing the device. A menu appears with the option **Unassign user**.

    - If the **Unassign user** option is available and not greyed out, then select it. A warning dialog box appears confirming to unassign the user from the device. Select **OK** to confirm unassigning the device from the user.
    - If the **Unassign user** option isn't available and greyed out, then move on to the next step.
10. With the device still selected, select **Delete** in the toolbar at the top of the page.
11. A warning dialog box appears to confirm the deletion of the device from Windows Autopilot. Select **Yes** to confirm deleting the device.
12. The deregistration process might take some time. The process can be accelerated by selecting the **Sync** button in the toolbar at the top of the page.
13. Every few minutes select **Refresh** in the toolbar at the top of the page until the device is no longer present.

Important

- For Microsoft Entra joined devices, no additional steps are required after deregistering the device from Windows Autopilot using Intune. Avoid manually deleting the device from Microsoft Entra ID, as this can cause unexpected issues.
- For Microsoft Entra hybrid joined devices, delete the computer object from the on‑premises Active Directory Domain Services (AD DS) environment to prevent it from being resynced to Microsoft Entra ID. After this step, no additional actions are required in Intune or Windows Autopilot. Avoid manually deleting the device from Microsoft Entra ID.

For information about what to expect in Microsoft Entra ID after deregistration, see What happens to the Microsoft Entra device object after deregistration?

This process ensures that related records in Windows Autopilot, Intune, and Microsoft Entra ID are handled correctly. Skipping steps or removing records out of order can result in orphaned records or unrecoverable devices. If a device goes into an unrecoverable state, contact the appropriate [Microsoft support alias](autopilot-support) for assistance.

### What happens to the Microsoft Entra device object after deregistration?

Deregistering a device from Windows Autopilot removes the device’s registration from the Windows Autopilot deployment service. However, this action doesn’t always remove the corresponding Microsoft Entra device object.

What happens in Microsoft Entra ID depends on the device’s join and enrollment state:

- **Devices that aren’t currently enrolled in MDM:** Removing the Windows Autopilot registration can also result in the associated Microsoft Entra device object being removed.
- **Devices that are or were enrolled in MDM:** Removing the Windows Autopilot registration doesn’t automatically delete the Microsoft Entra device object. In this case, the device can remain in Microsoft Entra ID even though it’s no longer registered with Windows Autopilot.

Because this behavior varies, avoid manually deleting the device from Microsoft Entra ID unless a specific scenario requires it. The Windows Autopilot deployment process relies on the Microsoft Entra device object, and deleting it can cause enrollment failures.

### Deregister from Windows Autopilot using Microsoft 365 admin center

The device can be deregistered from Windows Autopilot in [Microsoft 365 admin center](https://admin.microsoft.com/) if using the Microsoft 365 admin center instead of Intune. To deregister a Windows Autopilot device from the Microsoft 365 admin center:

1. Sign in to to the [Microsoft 365 admin center](https://admin.microsoft.com/).
2. Navigate to **Devices** &gt; **Autopilot**.
3. Select the device to be deregistered and then select **Delete device**.

### Deregister from Windows Autopilot in Microsoft Partner Center (MPC)

To deregister a Windows Autopilot device from the Microsoft Partner Center (MPC), a Cloud Solution Partner (CSP) would:

1. Sign in to the Microsoft Partner Center (MPC).
2. Navigate to **Customer** &gt; **Devices**.
3. Select the device to be deregistered and then select **Delete device**.

    ![Screenshot of delete device](images/devices.png)

Partners deregistering a device from Windows Autopilot in Microsoft Partner Center (MPC) only deregisters the device from Windows Autopilot. It doesn't perform any of the following actions:

- Unenroll the device from the mobile device management (MDM) solution, such as Intune.
- Disjoin the device from Microsoft Entra ID.

For these reasons, the OEM or CSP should work with the customer IT administrators to have the device fully removed by following the steps in the Deregister a device section.

An OEM or CSP with integrated OEM Direct APIs can also deregister a device with the **AutopilotDeviceRegistration** API. Make sure the **TenantID** and **TenantDomain** fields are left blank.

Note

If an admin registered a device via another portal other than the Microsoft Partner Center (MPC) such as Intune or the [Microsoft 365 admin center](https://admin.microsoft.com/), the device doesn't show up in Microsoft Partner Center (MPC). For a partner to register a device in the Microsoft Partner Center (MPC), the devices first needs to be deregistered using the steps outlined in the Deregister a device section.