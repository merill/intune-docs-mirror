---
layout: Conceptual
title: Use direct enrollment for macOS devices - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-enrollment/apple/setup-direct-macos
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
ms.reviewer: scottbreenmsft
ms.subservice: enrollment
description: Deploy and enroll macOS devices in Microsoft Intune using direct enrollment with Apple Configurator.
ms.date: 2024-04-03T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: dd77e9ec-392d-7498-ad85-52eca980bce7
document_version_independent_id: dd77e9ec-392d-7498-ad85-52eca980bce7
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-enrollment/apple/setup-direct-macos.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-enrollment/apple/setup-direct-macos
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-enrollment/apple/setup-direct-macos.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: c7529b5f-c405-1ca2-3a8d-454340984d5d
---

# Use direct enrollment for macOS devices - Microsoft Intune | Microsoft Learn

Manually enroll new or existing corporate-owned Macs via *direct enrollment* with Apple Configurator. Direct enrollment is ideal for bulk enrollments and when you don't have access to Apple School Manager, Apple Business, or when you require a wired network connection. You must have physical access to the Macs to configure and deploy the enrollment profile.

Direct enrollment lets you enroll the device prior to distribution, and doesn't wipe the device upon enrollment. Devices enrolled this way aren't associated with a user so we recommend this option for shared or kiosk-style devices. These types of devices are purpose driven and commonly used in businesses by frontline workers to scan items, print tickets, get digital signatures, or manage inventory.

We recommend direct enrollment if you:

- Are in a region/country that doesn't support Apple Business or Apple School Manager.
- Don't want to use Apple Business or Apple School Manager because you want to limit admin control over devices, or because you don't want to set up all of the requirements.
- Need a wired internet connection to enroll devices, or have an unreliable internet connection.

You can use this method to enroll one or more Macs. If you have many devices, it will take some time to enroll them because you must transfer and open the enrollment profile on each Mac you're enrolling.

Devices are deployed without user affinity. If you need devices to have user affinity, enroll Macs in Intune via [Apple automated device enrollment](setup-automated-macos).

See the following visual guide for a summary of all enrollment options and features available for macOS:

[![A visual representation of Intune enrollment options by platform](../media/guide/msft-intune-enrollment-options-thumb-landscape.png)](https://download.microsoft.com/download/e/6/2/e6233fdd-a956-4f77-93a5-1aa254ee2917/msft-intune-enrollment-options.pdf)[Download PDF version](https://download.microsoft.com/download/e/6/2/e6233fdd-a956-4f77-93a5-1aa254ee2917/msft-intune-enrollment-options.pdf) | [Download Visio version](https://download.microsoft.com/download/e/6/2/e6233fdd-a956-4f77-93a5-1aa254ee2917/msft-intune-enrollment-options.vsdx)

## Apps

Apps requiring user affinity, such as the Intune Company Portal app, aren't supported on Macs enrolled via direct enrollment. The Company Portal app isn't used, needed, or supported for enrollments without user affinity. Be sure device users don't install the Company Portal app from the Apple App Store on enrolled devices.

## Certificates

This enrollment type supports the Automated Certificate Management Environment (ACME) protocol. When new devices enroll, the management profile from Intune receives an ACME certificate. The ACME protocol provides better protection than the SCEP protocol against unauthorized certificate issuance through robust validation mechanisms and automated processes, which helps reduce errors in certificate management.

Before you export the ACME certificate for Apple Configurator enrollment, first preload the device serial numbers into Intune, and then assign them to the enrollment profile. Otherwise, the direct enrollment profile will fail.

Devices that are already enrolled in Intune do not get an ACME certificate unless they re-enroll into Microsoft Intune. ACME is supported on devices running macOS 13.1 or later.

## Prerequisites

![](../../media/icons/16/devices.svg)**Device platform requirements**

> 
> This enrollment method supports the following platforms:
> 
> - macOS
> 

![](../../media/icons/16/tenant-administration.svg)**Tenant configuration requirements**

> 
> - Set [MDM authority](../../fundamentals/setup-mdm-authority).
> - [An Apple MDM push certificate](create-mdm-push-certificate).
> - Access to Microsoft Intune admin center and Apple Configurator.
> 

You also need:

- Physical access to [supported devices](../../fundamentals/ref-supported-platforms#apple)
- Administrator rights on the Macs you're enrolling

If the Mac you're setting up is enrolled in another MDM provider, you must unenroll it before you can enroll it in Intune.

Note

This enrollment method doesn't support device enrollment restrictions. Make sure you don't have device platform restrictions targeted at any Apple devices, because it will cause the enrollment profile download to fail. In this scenario, admins might see the following error during enrollment:

**File download error. Failed to dynamically fetch target download uri.**

Additionally, if an enrollment profile is downloaded before a restriction is configured and then used after the restriction is enabled, enrollment will fail.

## Step 1: Create enrollment profile

A device enrollment profile defines the settings applied during direct enrollment. These settings are applied only once. Follow these steps to create an Apple Configurator enrollment profile for the Macs you're enrolling.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Go to **Devices** &gt; **Enrollment**.
3. Select the **Apple** tab.
4. Under **Bulk Enrollment Methods**, select **Apple Configurator**.
5. Go to **Profiles** &gt; **Create**.
6. The **Create Enrollment Profile** page opens. For **Basics**, type a **Name** and **Description** for the profile. These details can help you quickly find your profile in the admin center. Device users don't see these details.

Tip

You can use the name field to create a dynamic membership rule for Microsoft Entra groups. The *enrollmentProfileName* parameter lets you quickly assign devices with this enrollment profile to the appropriate groups. For more information, see [Dynamic group rule syntax](/en-us/azure/active-directory/enterprise-users/groups-dynamic-membership#rules-for-devices).

1. For **User Affinity**, choose **Enroll without user affinity**. This configuration confirms that you're setting up devices without user association. Direct enrollment *with user affinity*, although available, isn't supported on Macs.
2. Select **Create** to save the profile.

## Step 2: Export enrollment profile

In this step, you export the enrollment profile.

1. After you create the profile in the admin center, go to **Profiles**.
2. Choose the profile you want to export. Then select **Export profile**.
3. A new pane opens. Under **Direct enrollment**, choose **Download profile**.
4. Save the `.mobileconfig` file. An enrollment profile file is only valid for two weeks. After that time, you must recreate it.

    Note

    You can download as many enrollment profiles as you need. Downloading a new profile does not render the previous one invalid, however, it also doesn't extend the expiration date for the previously downloaded file.

## Step 3: Install enrollment profile

In this step, you install the enrollment profile on the enrolling Mac.

1. Transfer the `.mobileconfig` file from your device to the Mac you want to enroll.
2. Double-click the file to open it.
3. When you're prompted to install the management profile, select **Install**.
4. Select **Install** again to confirm you want to install the management profile.
5. Sign in with an administrator account on the Mac, and then select **OK**.

The Mac is now enrolled in Microsoft Intune and ready-to-manage. Other profiles assigned to the device begin installing immediately.