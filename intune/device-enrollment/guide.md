---
layout: Conceptual
title: Device enrollment guide for Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-enrollment/guide
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
description: Enroll Android, Android Enterprise, iOS, iPadOS, Linux, macOS, and Windows devices in Intune. Decide which enrollment method to use, and get an overview of the administrator and end user tasks to enroll devices.
ms.date: 2024-06-24T00:00:00.0000000Z
ms.topic: article
locale: en-us
document_id: cdb05047-a308-c9d6-15a9-3846841a6d11
document_version_independent_id: cdb05047-a308-c9d6-15a9-3846841a6d11
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-enrollment/guide.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-enrollment/guide
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-enrollment/guide.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: be250584-0d70-d262-9a6d-4da1831038a1
---

# Device enrollment guide for Microsoft Intune - Microsoft Intune | Microsoft Learn

Microsoft Intune, together with Microsoft Entra ID, facilitates a secure, streamlined process for registering and enrolling devices that want access to your internal resources. Once users and devices are registered within your Microsoft Entra ID (also called a *tenant*), then you can utilize Intune for its endpoint management capabilities. The process that enables device management for a device is called **device enrollment**.

During enrollment, Intune installs a Mobile Device Management (MDM) certificate on the enrolling device. The MDM certificate communicates with the Intune service, and enables Intune to start enforcing your organization's policies, like:

- Enrollment policies that limit the number or type of devices someone can enroll.
- Compliance policies that help users and devices meet your rules.
- Configuration policies that configure work-appropriate features and settings on devices.

![Diagram that shows the device enrolls, the object is created in Microsoft Entra ID, and the MDM certificate is pushed to these devices in Microsoft Intune.](media/guide/mdm-certificate.png)

Typically, policies are deployed during enrollment. Some groups, depending on their roles in your organization, can require stricter policies than others. Many organizations start by creating a baseline of required policies for users and devices. Then, add to this baseline as needed for different groups and use cases.

You can enroll devices running on the following platforms. For a list of supported versions, go to [Supported operating systems](../fundamentals/ref-supported-platforms).

- Android
- iOS/iPadOS
- Linux
- macOS
- Windows

Enrollment is enabled for all platforms by default, but you can restrict specific platforms from enrolling by using an Intune [enrollment restriction policy](restrictions).

This article describes the supported device scenarios and enrollment prerequisites, has information about using other MDM providers, and includes links to platform-specific enrollment guidance.

## Supported device scenarios

Microsoft Intune enables mobile device management for:

- Personal devices, including personally owned phones, tablets, and PCs.
- Corporate-owned devices, including phones, tablets, and PCs owned by your organization and distributed to employees and students for use at work or school.

### Personal devices

Devices in bring-your-own-device (BYOD) scenarios can be MDM enrolled in Intune. The supported enrollment methods enable employees and students to use their personal devices for work or school tasks.

As the admin, you add device users in the Microsoft Intune admin center, configure their enrollment experience, and set up Intune policies. In the Intune Company Portal app, the device user starts and completes the enrollment.

To determine if enrolling personal devices in Intune is right for your organization, go to [Intune planning guide: Personal devices vs Organization-owned devices](../fundamentals/planning-guide#personal-devices-vs-organization-owned-devices).

Note

Intune marks devices that are [Microsoft Entra registered](/en-us/entra/identity/devices/concept-device-registration) as personally-owned devices.

### Corporate-owned devices

Microsoft Intune offers more granular settings and policies for devices classified as **corporate-owned** or **organization-owned**. There are more password settings available for corporate-owned devices. So, you can enforce stricter password requirements.

Microsoft Intune automatically marks devices that meet certain criteria as corporate-owned. For more information, go to [Identify devices as corporate-owned](add-corporate-identifiers).

## Prerequisites

- Intune is set up, and ready to enroll users and devices. Be sure:

    - The [MDM Authority](../fundamentals/setup-mdm-authority) is set to Intune, even when using [co-management](../configmgr/comanage/overview) with Intune + Configuration Manager.
    - [Intune licenses are assigned](../fundamentals/assign-licenses).

    For more information, go to the [Intune setup deployment guide](../fundamentals/setup-migration).
- Your devices [are supported](../fundamentals/ref-supported-platforms). This requirement includes devices that are co-managed, or Microsoft Entra hybrid joined devices.
- Sign in as a member of the **Policy and Profile Manager** built-in Intune role. For information on the permissions in this role, go to [Built-in role permissions for Microsoft Intune - Policy and Profile manager](../fundamentals/role-based-access-control/ref-built-in-roles#policy-and-profile-manager).

    It's possible some enrollment platforms might require a more privileged Microsoft Entra role, like the **Intune Administrator** built-in role. For information on this role, go to [Microsoft Entra built-in roles - Intune Administrator](/en-us/entra/identity/role-based-access-control/permissions-reference#intune-administrator).
- Different platforms can have other requirements. For example, iOS/iPadOS and macOS devices require an [MDM push certificate from Apple](apple/create-mdm-push-certificate). Any other platform requirements are listed.

    | Platform | Other requirements |
    | --- | --- |
    | Android | none |
    | Android Enterprise | none |
    | iOS/iPadOS | [MDM push certificate](apple/create-mdm-push-certificate)Apple ID |
    | Linux | none |
    | macOS | [MDM push certificate](apple/create-mdm-push-certificate) |
    | Windows | none |
- Have your user groups and device groups ready to receive your enrollment policies. If you haven't reviewed or created your group structure, and want some guidance, then go to [Planning Guide: Step 4 - Review existing policies and infrastructure](../fundamentals/planning-guide#step-4---review-existing-policies-and-infrastructure).
- If you're bulk enrolling devices, consider creating the **Device enrollment manager** (DEM) account. The DEM account can enroll up to 1,000 mobile devices. Use this account to enroll and configure the devices before giving them to users. The DEM account is an Intune permission that applies to a Microsoft Entra user account. This type of account isn't compatible with all enrollment methods, like Apple automated device enrollment.

    For more information, go to [Enroll devices using a DEM account](setup-enrollment-manager).

## Unenroll from existing MDM and factory reset

If devices are currently enrolled in another MDM provider, then unenroll the devices from the existing MDM provider. Typically, unenrolling doesn't remove existing features and settings you configured. Most MDM providers have remote actions that remove organization-specific data from devices. Before enrolling in Intune, you can remove organization-specific data from these devices. But, it isn't required.

Depending on the platform, a factory reset might be required before enrolling in Intune.

| Platform | Factory reset required? |
| --- | --- |
| Android Enterprise personally owned devices with a work profile (BYOD) | No |
| Android Enterprise corporate-owned work profile (COPE) | Yes |
| Android Enterprise fully managed (COBO) | Yes |
| Android Enterprise dedicated devices (COSU) | Yes |
| Android device administrator (DA) | No |
| iOS/iPadOS | Yes |
| Linux | No |
| macOS | Yes |
| Windows | No |

On the platforms that don't require a factory reset, when these devices enroll in Intune, they start receiving your Intune policies. If you don't configure a setting in Intune, then Intune doesn't change or update that setting. So, it's possible previously configured settings remain configured on devices.

## Choose your platform enrollment guide

There's an enrollment guide for every platform. Choose your scenario, and get started:

- [Application management without enrollment](../app-management/protection/mam-without-enrollment)
- [Android](android/guide)
- [Apple mobile](apple/guide-ios-ipados)
- [Linux](guide-linux)
- [macOS](apple/guide-macos)
- [Windows](windows/guide)

## Download the visual enrollment guide

There's also a visual guide of the different enrollment options for each platform:

[![A visual representation of Intune enrollment options by platform](media/guide/msft-intune-enrollment-options-thumb-landscape.png)](https://download.microsoft.com/download/e/6/2/e6233fdd-a956-4f77-93a5-1aa254ee2917/msft-intune-enrollment-options.pdf)[Download PDF version](https://download.microsoft.com/download/e/6/2/e6233fdd-a956-4f77-93a5-1aa254ee2917/msft-intune-enrollment-options.pdf) | [Download Visio version](https://download.microsoft.com/download/e/6/2/e6233fdd-a956-4f77-93a5-1aa254ee2917/msft-intune-enrollment-options.vsdx)

## Pilot groups

When assigning your policies, start small, and use a staged approach. Assign the enrollment policy to a pilot or test group. After initial testing, add more users to the pilot group. Then, assign the enrollment policy to more pilot groups.

For more information and suggestions, go to the [Planning guide: Step 5 - Create a rollout plan](../fundamentals/planning-guide#step-5---create-a-rollout-plan).

## Mobile device record cleanup

The MDM certificate renews automatically as long as enrolled devices are communicating with the Microsoft Intune service. The MDM certificate doesn't renew for devices that are wiped, or devices that fail to sync with Microsoft Intune for an extended period of time. Microsoft Intune deletes idle devices from record 180 days after the MDM certificate expires.

## Reporting and troubleshooting

- [Incomplete user enrollments](monitor-reports)
- [Troubleshoot device enrollment](/en-us/troubleshoot/mem/intune/troubleshoot-device-enrollment-in-intune)