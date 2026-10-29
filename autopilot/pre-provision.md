---
layout: Conceptual
title: Windows Autopilot for Pre-provisioned Deployment | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/pre-provision
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
description: Windows Autopilot helps organizations provision new devices by using the preinstalled manufacturer image and drivers. Learn how users get their devices ready.
ms.date: 2026-10-21T00:00:00.0000000Z
ms.collection:
- M365-modern-desktop
ms.topic: how-to
locale: en-us
document_id: 09ef523f-5ca7-b537-3ce5-b55c2e856c2c
document_version_independent_id: 09ef523f-5ca7-b537-3ce5-b55c2e856c2c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/pre-provision.md
site_name: Docs
depot_name: MSDN.autopilot
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.autopilot/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: pre-provision
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/pre-provision.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
platformId: c669f37f-e0c0-3964-74a8-672da8263b19
---

# Windows Autopilot for Pre-provisioned Deployment | Microsoft Learn

Windows Autopilot helps organizations easily provision new devices by using the preinstalled OEM image and drivers. This functionality lets end users get their devices business-ready by using a simple process.

![Diagram shows the OEM process, which includes the OEM and the end user.](images/wg01.png)

Windows Autopilot can also provide a *pre-provisioning* service that helps partners or IT staff pre-provision a fully configured and business-ready Windows PC. From the end user's perspective, the Windows Autopilot user-driven experience is unchanged, but getting their device to a fully provisioned state is faster.

By using **Windows Autopilot for pre-provisioned deployment**, you can split the provisioning process. IT, partners, or hardware manufacturers complete the time-consuming portions. The end user completes a few necessary settings and policies and then can begin using their device.

![Diagram shows the OEM process with partner between the OEM and the end user.](images/wg02.png)

Pre-provisioned deployments use Microsoft Intune in currently supported versions of Windows. Such deployments build on existing Windows Autopilot [user-driven scenarios](user-driven) and support user-driven mode scenarios for both Microsoft Entra joined and Microsoft Entra hybrid joined devices.

## Requirements

Important

A device can't automatically re-enroll through Windows Autopilot after an initial deployment with pre-provisioning mode. Instead, delete the device record in the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431). From the Microsoft Intune admin center, select **Devices** &gt; **All devices** &gt; select the devices to delete &gt; **Delete**. For more information, see [Updates to the Windows Autopilot sign-in and deployment experience](https://techcommunity.microsoft.com/t5/intune-customer-success/updates-to-the-windows-autopilot-sign-in-and-deployment/ba-p/2848452).

In addition to [Windows Autopilot requirements](requirements), Windows Autopilot for pre-provisioned deployment also requires:

- A currently supported version of Windows.
- Windows Pro, Enterprise, or Education editions.
- An Intune subscription.
- Physical devices that support Trusted Platform Module (TPM) 2.0 and device attestation. Virtual machines aren't supported. The pre-provisioning process uses Windows Autopilot self-deploying capabilities, so TPM 2.0 is required. The TPM attestation process also requires access to a set of HTTPS URLs that are unique for each TPM provider. For more information, see the entry for Windows Autopilot self-Deploying mode and Windows Autopilot pre-provisioning in [Networking requirements](requirements?tabs=networking#windows-autopilot-self-deploying-mode-and-windows-autopilot-pre-provisioning).
- Network connectivity. Using wireless connectivity requires selecting region, language, and keyboard before you can connect and start provisioning.
- An enrollment status page (ESP) profile must be targeted to the device.

Important

- Because the manufacturer or vendor performs the pre-provisioning process, this process **doesn't require access to an end-user's on-prem domain infrastructure**. The pre-provisioning process is unlike a typical Microsoft Entra hybrid joined scenario because restarting the device is postponed. The device is resealed before the time when connectivity to a domain controller is expected. Instead the domain network is contacted when the device is unboxed on-premises by the end-user.
- To review known issues, see [Windows Autopilot known issues](known-issues) and [Troubleshooting Windows Autopilot device import and enrollment](troubleshooting-faq#troubleshooting-windows-autopilot-device-import-and-enrollment).

## Preparation

Devices slated for pre-provisioning are registered for Windows Autopilot by using the normal registration process.

To be ready to try out Windows Autopilot for pre-provisioned deployment, ensure that you can successfully use existing Windows Autopilot user-driven scenarios:

- User-driven Microsoft Entra join. Ensure that you can deploy devices by using Windows Autopilot and join them to a Microsoft Entra ID tenant.
- User-driven with Microsoft Entra hybrid join. To enable the features of Microsoft Entra hybrid join, ensure that you can perform the following actions:

    - Deploy devices by using Windows Autopilot.
    - Join the devices to an on-premises Active Directory domain.
    - Register the devices with Microsoft Entra ID.

    Important

    Microsoft recommends deploying new devices as cloud-native by using Microsoft Entra join. Deploying new devices as Microsoft Entra hybrid join devices isn't recommended, including through Windows Autopilot. For more information, see [Microsoft Entra joined vs. Microsoft Entra hybrid joined in cloud-native endpoints: Which option is right for your organization](/en-us/intune/solutions/cloud-native-endpoints/azure-ad-joined-hybrid-azure-ad-joined#which-option-is-right-for-your-organization).

If these scenarios can't be completed, Windows Autopilot for pre-provisioned deployment also doesn't succeed since it builds on top of these scenarios.

Before the pre-provisioning process can be started in the provisioning service facility, another Windows Autopilot profile setting must be configured. A detailed tutorial on how to configure a Windows Autopilot profile for pre-provisioning is available in the following articles:

- [Step by step tutorial for Windows Autopilot for pre-provisioned deployment Microsoft Entra join in Intune](tutorial/pre-provisioning/azure-ad-join-workflow)
- [Step by step tutorial for Windows Autopilot for pre-provisioned deployment Microsoft Entra hybrid join in Intune](tutorial/pre-provisioning/hybrid-azure-ad-join-workflow)

The pre-provisioning process applies all device-targeted policies from Intune. Those policies include certificates, security templates, settings, apps, and anything targeting the device. Additionally, it installs any Win32 or line-of-business (LOB) apps that meet the following conditions:

- Configured to install in the device context.
- Assigned to either the device or to the user preassigned to the Windows Autopilot device.

Important

Don't target both Win32 and LOB apps to the same device. If you need to target both Win32 and LOB apps to the device, consider using [Windows Autopilot device preparation](device-preparation/overview). For more information, see [Add a Windows line-of-business app to Microsoft Intune](/en-us/intune/app-management/deployment/add-lob-windows).

Note

To ensure easy access into pre-provisioning mode, select the language mode as user specified in Windows Autopilot profiles. The pre-provisioning technician phase installs all device-targeted apps and any user-targeted, device-context apps that are targeted to the assigned user. If there's no assigned user, it only installs the device-targeted apps. The process doesn't apply other user-targeted policies until the user signs in to the device. To verify these behaviors, be sure to create appropriate apps and policies targeted to devices and users.

## Scenarios

Windows Autopilot for pre-provisioned deployment supports two distinct scenarios:

- User-driven deployments with Microsoft Entra join. The device is joined to a Microsoft Entra tenant.
- User-driven deployments with Microsoft Entra hybrid join. The device is joined to an on-premises Active Directory domain, and separately registered with Microsoft Entra ID.

    Important

    Microsoft recommends deploying new devices as cloud-native using Microsoft Entra join. Deploying new devices as Microsoft Entra hybrid join devices isn't recommended, including through Windows Autopilot. For more information, see [Microsoft Entra joined vs. Microsoft Entra hybrid joined in cloud-native endpoints: Which option is right for your organization](/en-us/intune/solutions/cloud-native-endpoints/azure-ad-joined-hybrid-azure-ad-joined#which-option-is-right-for-your-organization).

Each of these scenarios consists of two parts, a *technician flow* and a *user flow*. At a high level, these parts are the same for Microsoft Entra join and Microsoft Entra hybrid join. The differences are primarily seen by the end user in the authentication steps.

### Technician flow

After the customer or IT admin targets all the apps and settings they want for their devices through Intune, the pre-provisioning technician can begin the pre-provisioning process. The technician can be a member of the IT staff, a services partner, or a manufacturer. Each organization can decide who should perform these activities. Regardless of the scenario, the process done by the technician is the same:

- Boot the device.
- From the first out-of-box experience (OOBE) screen, which can be a language selection, locale selection screen, or the Microsoft Entra sign-in page, don't select **Next**. Instead, press the Windows key five times to view another options dialog. From that screen, select the **Windows Autopilot provisioning** option and then select **Continue**.
- On the **Windows Autopilot Configuration** screen, it displays the following information about the device:

    - The Windows Autopilot profile assigned to the device.
    - The organization name for the device.
    - The user assigned to the device, if there's one.
    - A QR code that contains a unique identifier for the device. Use this code to look up the device in Intune, which you might need to make configuration changes. For example, assign a user or add the device to groups needed for app or policy targeting.
- Validate the information displayed. If you need any changes, make the changes, and then select **Refresh** to redownload the updated Windows Autopilot profile details.
- Select **Provision** to begin the provisioning process.

If the pre-provisioning process completes successfully:

- A success status screen appears with information about the device, including the same details presented previously. For example, Windows Autopilot profile, organization name, assigned user, and QR code. The elapsed time for the pre-provisioning steps is also provided.
- Select **Reseal** to shut down the device. At that point, you can ship the device to the end user.

Note

Technician flow inherits behavior from [self-deploying mode](self-deploying). Self-Deploying Mode uses the Enrollment Status Page to hold the device in a provisioning state. The device being in a provisioning state prevents the user from proceeding to the desktop after enrollment but before software and configuration are done applying. As such, if the Enrollment Status Page is disabled, the reseal button can appear before software and configuration is done applying. This behavior can allow proceeding to the user flow before the technician flow provisioning is complete. The success screen validates that enrollment was successful, not that the technician flow is necessarily complete.

If the pre-provisioning process fails:

- An error status screen appears with information about the device, including the same details presented previously. For example, Windows Autopilot profile, organization name, assigned user, and QR code. The elapsed time for the pre-provisioning steps is also provided.
- You can gather diagnostic logs from the device, and then it can be reset to start the process over again.

### User flow

Important

- Wait at least 90 minutes after running the technician flow before you run the user flow. Waiting ensures tokens refresh properly between the technician flow and the user flow. This scenario mainly affects lab and testing scenarios when you run the user flow within 90 minutes after the technician flow finishes.
- Run the user flow within six months after the technician flow finishes. Waiting more than six months can cause the certificates used by the Intune Management Engine (IME) to no longer be valid, which leads to errors such as:

    `Error code: [Win32App][DetectionActionHandler] Detection for policy with id: <policy_id> resulted in action status: Failed and detection state: NotComputed.`
- Compliance in Microsoft Entra ID is reset during the user flow. Devices might show as compliant in Microsoft Entra ID after the technician flow completes, but then show as noncompliant once the user flow starts. Allow enough time after the user flow completes for compliance to reevaluate and update.

If the pre-provisioning process finishes successfully and the device is resealed, deliver the device to the end user. The end user completes the normal Windows Autopilot user-driven process by following these steps:

- Power on the device.
- Select the appropriate language, locale, and keyboard layout.
- Connect to a network, if using Wi-Fi. Internet access is always required. If using Microsoft Entra hybrid join, there must also be connectivity to a domain controller.
- If using Microsoft Entra join, on the branded sign-in screen, enter the user's Microsoft Entra credentials.
- If using Microsoft Entra hybrid join, the device restarts. After the restart, enter the user's Active Directory credentials.

    Note

    In certain circumstances, Microsoft Entra credentials might also be prompted for during a Microsoft Entra hybrid join scenario. For example, if Active Directory Federation Service (ADFS) isn't being used.
- More policies and apps are delivered to the device, with progress tracked by the Enrollment Status Page (ESP). When complete, the user can access the desktop.

The device ESP reruns during the user flow so that both device and user ESP run when the user signs in. This behavior allows the ESP to install other policies that are assigned to the device after the device finishes the technician phase.

Note

If you disable the Microsoft Account Sign-In Assistant (wlidsvc) during the technician flow, the Microsoft Entra sign-in option might not show. Instead, users are asked to accept the EULA and create a local account, which might not be the desired behavior.

## Deploying a device

For more information about starting a deployment on a device when using Windows Autopilot for pre-provisioned devices, see the technician flow and user flow steps in the Windows Autopilot for pre-provisioned deployment tutorials:

- [Microsoft Entra join](tutorial/pre-provisioning/azure-ad-join-workflow):

    - [Technician flow](tutorial/pre-provisioning/azure-ad-join-technician-flow)
    - [User flow](tutorial/pre-provisioning/azure-ad-join-user-flow)
- [Microsoft Entra hybrid](tutorial/pre-provisioning/hybrid-azure-ad-join-workflow):

    - [Technician flow](tutorial/pre-provisioning/hybrid-azure-ad-join-technician-flow)
    - [User flow](tutorial/pre-provisioning/hybrid-azure-ad-join-user-flow)