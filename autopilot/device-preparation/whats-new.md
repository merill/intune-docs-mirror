---
layout: Conceptual
title: What's new in Windows Autopilot device preparation | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/device-preparation/whats-new
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
description: News and resources about the latest updates of Windows Autopilot device preparation.
ms.date: 2026-09-14T00:00:00.0000000Z
ms.collection:
- M365-modern-desktop
ms.topic: whats-new
locale: en-us
document_id: a225158e-ab11-11a9-3949-4c7cd4127d2c
document_version_independent_id: a225158e-ab11-11a9-3949-4c7cd4127d2c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/device-preparation/whats-new.md
site_name: Docs
depot_name: MSDN.autopilot
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.autopilot/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-preparation/whats-new
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/device-preparation/whats-new.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/72cb4d1c-66f7-4281-99d5-e04a64d084fc
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/d9ebaec0-4879-449e-9781-0afdce99fe0a
platformId: c16b0f6b-13b8-70a0-0b3b-3f1fdf0ef059
---

# What's new in Windows Autopilot device preparation | Microsoft Learn

Tip

RSS can be used to notify when new features for Windows Autopilot device preparation are added to this page. For example, the following RSS link includes this article:

```url
https://learn.microsoft.com/api/search/rss?search=%22News+and+resources+about+the+latest+updates+of+Windows+Autopilot+device+preparation.%22&locale=en-us&%24filter=
```

This example includes the `&locale=en-us` variable. The `locale` variable is required, but it can be changed to another supported locale. For example, `&locale=es-es`.

For more information on using RSS for notifications, see [How to use the docs](/en-us/intune/use-docs#notifications) in the Intune documentation.

## Performance and reliability improvements for Windows Autopilot device preparation

Date added: *September 14, 2026*

We've added the following performance and reliability improvements to help reduce provisioning failures and onboarding time during the out-of-box experience (OOBE):

- The default 128-bit BitLocker encryption policy is no longer applied during OOBE. Admin-configured BitLocker policies are prioritized, helping devices use the configured encryption method.
- The Microsoft Intune Management Extension (IME) initiates a sync immediately after OOBE, helping apps and policies that depend on IME be delivered sooner.
- Device check-in is more resilient following a loss of network connectivity during OOBE, helping devices resume syncing faster after connectivity is restored.

## Windows Autopilot device association

Date added: *August 27, 2026*

Windows Autopilot device preparation now supports device association, which binds a physical Windows 11 device to your organization before enrollment. Associated devices are automatically marked as corporate-owned and can receive device-targeted policy assignments, device naming, and additional out-of-box experience (OOBE) customizations.

For requirements, lifecycle information, and setup guidance, see [Overview of Windows Autopilot device association](device-association/overview).

## Windows Autopilot device preparation in automatic mode for Windows 365 general availability

**Date added:** May 11, 2026 

Use Windows Autopilot device preparation policies in the automatic flow to provision Cloud PCs at creation. This feature is generally available for:

- Windows 365 Enterprise
- Windows 365 Flex (dedicated)
- Windows 365 Flex (shared)
- Windows 365 Cloud Apps

This feature is in public preview for Windows 365 Reserve.

You can include Windows Autopilot device preparation policies in your Cloud PC provisioning policy. Policies apply immediately after you create a Cloud PC, and deliver apps, scripts, and configurations automatically before users sign in. This ensures each device is ready to use with all required apps and settings from the start.

You can monitor deployment status in the [Windows Autopilot device preparation deployment report](reporting-monitoring). For a tutorial, see [Step by step tutorial for Windows Autopilot device preparation in automatic mode for Windows 365 in Intune](tutorial/automatic/automatic-workflow).

For related information, see the following articles: 

- [Create provisioning policies for Windows 365](/en-us/windows-365/enterprise/create-provisioning-policy)
- [Windows 365 Cloud Apps](/en-us/windows-365/enterprise/cloud-apps)
- [Use Autopilot device preparation with Cloud PCs](/en-us/windows-365/enterprise/autopilot-device-preparation)

## Managed installer policy support during Windows Autopilot device preparation

Date added: *April 10, 2026*

Microsoft Intune now supports the managed installer policy for apps during Windows Autopilot device preparation. The policy will be applied during the out-of-box experience (OOBE) before Win32, Microsoft Store, and Enterprise App Catalog apps install. These app types were previously skipped to prevent app installation conflicts and deployment failures. This update helps ensure supported apps install reliably during user-driven and automatic Autopilot scenarios.

## Admins can configure up to 25 apps to install during Autopilot device preparation

Date added: *January 30, 2026*

The maximum number of apps that can be configured in a Windows Autopilot device preparation policy has been increased to 25. This update supports organizations that require more apps to be delivered during the out-of-box experience (OOBE). The increased limit applies to both user-driven and automatic modes, including all Cloud PC offerings. Review and adjust your deployment timeout settings as needed to help avoid unexpected timeouts. For more information about assigning apps, see:

- [Windows Autopilot device preparation user-driven Microsoft Entra join: Assign applications and PowerShell scripts to device group](tutorial/user-driven/entra-join-assign-apps-scripts)
- [Windows Autopilot device preparation in automatic mode: Assign applications and PowerShell scripts to device group](tutorial/automatic/automatic-assign-apps-scripts)

## Windows Autopilot device preparation in automatic mode for Windows 365 Enterprise, Windows 365 Frontline in dedicated mode, and Windows 365 Cloud Apps is in public preview

Date added: *November 21, 2025*

Use Windows Autopilot device preparation policies in automatic flow to provision Windows 365 Enterprise, Windows 365 Frontline in dedicated mode, and Windows 365 Cloud Apps. The policy can be included in the Cloud PC provisioning policy and applies immediately after the Cloud PCs are created to deliver apps and scripts to the device before a user logs in. You can monitor deployment status in the [Windows Autopilot device preparation deployment report](reporting-monitoring). For a tutorial, see [Step by step tutorial for Windows Autopilot device preparation in automatic mode for Windows 365 in Intune](tutorial/automatic/automatic-workflow).

For related information, see the following articles:

- [Create provisioning policies for Windows 365](/en-us/windows-365/enterprise/create-provisioning-policy)
- [Windows 365 Cloud Apps](/en-us/windows-365/enterprise/cloud-apps)
- [Use Autopilot device preparation with Cloud PCs](/en-us/windows-365/enterprise/autopilot-device-preparation)

## Installation of monthly security update releases during Windows Autopilot device preparation

Date added: *September 3, 2025* Date updated: *September 9, 2025*

Important

As of September 9, 2025, this capability is delayed to help ensure delivery of the best possible experience. Automatic installation of monthly security update isn't available yet. This post will be updated with a revised timeline as soon as it's available.

[Monthly security update releases](/en-us/windows/deployment/update/release-cycle#monthly-security-update-release), also known as Windows quality updates, are installed during a Windows Autopilot device preparation deployment as part of the Windows out-of-box experience (OOBE). The monthly security update releases are installed after the device preparation page completes. These updates can't be disabled for Windows Autopilot device preparation deployments. Installation of monthly security update releases during OOBE normally adds 20-40 minutes to the provisioning process. Installation of monthly security update releases also might require restarts.

More details regarding automatic installation of monthly security update releases can be found in the article [Install Windows monthly security update releases](/en-us/intune/intune-service/enrollment/windows-enrollment-status#windows-monthly-security-update-release-details). However, this article is in regards to using the Enrollment Status Page (ESP) with Windows Autopilot. Windows Autopilot device preparation doesn't use the ESP, so the **Install Windows quality updates (might restart the device)** setting mentioned in this article isn't applicable to Windows Autopilot device preparation.

For more information, see [Get ready for Windows quality updates out of the box](https://techcommunity.microsoft.com/blog/windows-itpro-blog/get-ready-for-windows-quality-updates-out-of-the-box/4434498).

## Deliver Enterprise App Catalog (EAM) apps during Autopilot device preparation

Date added: *June 26, 2025*

Autopilot device preparation now supports Enterprise App Catalog apps. Microsoft Intune Enterprise App Management enables IT admins to easily manage applications from the Enterprise App Catalog. With Intune's 2506 release, you can now select apps from the Enterprise App Catalog in the device preparation policy. This allows you to ensure those apps are delivered before the user can access the desktop.

For related information, see [Add an Enterprise App Catalog app to Microsoft Intune](/en-us/intune/app-management/deployment/add-enterprise-catalog-app).

## Windows Autopilot device preparation in automatic mode for Windows 365 Frontline in shared mode is in public preview

Date added: *April 2, 2025*

We've introduced a new flow for Windows Autopilot device preparation which can be used to provision [Windows 365 Frontline in shared mode](/en-us/windows-365/enterprise/introduction-windows-365-frontline). Admins can now choose **Automatic** when creating a Windows Autopilot device preparation policy to prepare a policy for Cloud PCs. The policy can then be included in the Cloud PC provisioning policy to ensure the policy is assigned to all Cloud PCs after they're created. The new Automatic policy allows admins to select up to 10 apps and up to 10 scripts which are delivered before a user accesses the Cloud PC. Deployments can then be monitored in the [Windows Autopilot device preparation deployment report](reporting-monitoring).

With the new mode, admins can make sure their Cloud PCs are secured with required software and scripts before the end user logs in!

For a tutorial on Windows Autopilot device preparation in automatic mode for Windows 365, see [Step by step tutorial for Windows Autopilot device preparation in automatic mode for Windows 365 in Intune](tutorial/automatic/automatic-workflow).

For more information, see the following articles:

- [Windows 365 Frontline Cloud PC in shared mode - Quick Start Guide](https://techcommunity.microsoft.com/discussions/windows365discussions/windows-365-frontline-cloud-pc-in-shared-mode-%E2%80%93-quick-start-guide/4399905).
- [Use automated Autopilot device preparation with Windows 365 Frontline Cloud PCs in shared mode (preview)](/en-us/windows-365/enterprise/autopilot-device-preparation).

## Diagnostics logs automatically available in Windows Autopilot device preparation deployment status report

Date added: *October 9, 2024*

Admins can now download diagnostics logs for failed Autopilot device preparation deployments directly from the **Windows Autopilot device preparation deployment status** report. Logs are available for download in the **Device deployment details** when you select a failed deployment under the **Device** tab. Logs are automatically collected when an error occurs during deployment.

## Windows Autopilot Device Preparation Support in Intune operated by 21Vianet in China

Date added: *September 18, 2024*

As part of the 2409 Intune release, we're announcing support for Windows Autopilot Device Preparation policy in [Intune operated by 21Vianet in China](/en-us/intune/fundamentals/china) cloud. Customers with tenants located in China can now provision devices and manage through Microsoft Intune. For an overview, see [Overview of Windows Autopilot device preparation](overview). For a tutorial on how to set up Windows Autopilot device preparation, see [Windows Autopilot device preparation scenarios](tutorial/scenarios).

## enrollmentProfileName property is now populated with the Device preparation policy name

Date added: *September 13, 2024*

As part of the 2409 Intune release, the **enrollmentProfileName** property is now populated with the Device preparation policy name during Autopilot device preparation deployments. The Enrollment profile property of Intune and Microsoft Entra device objects are automatically populated with the name of the Device preparation policy that was applied to the device during provisioning. The **enrollmentProfileName** property enables admins to configure assignment filters and dynamic groups based on the **enrollmentProfileName** property for configurations post-enrollment.

## Windows Autopilot device preparation deployment status report available in the Monitor tab under Enrollment

Date added: *August 21, 2024*

In addition to the [Devices | Monitor](reporting-monitoring#accessing-reports-and-near-real-time-monitoring) page, admins can now easily access the **Windows Autopilot device preparation deployment status** report from the **Monitor** tab in the **Devices | Enrollment** page. The report can be found using the following steps:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Navigate to **Home** &gt; **Devices** &gt; **Device onboarding | Enrollment**.
3. Select the **Monitor** tab in the **Devices | Enrollment** page.

## Corporate identifiers can now be used with Windows Autopilot device preparation

Date added: *July 8, 2024*

Customers who are blocking personal device enrollments can now use Windows Autopilot device preparation by pre-uploading the model, manufacturer, and serial number for all devices which deploys with Windows Autopilot device preparation. For more information, see [Add Windows corporate identifiers](/en-us/intune/intune-service/enrollment/corporate-identifiers-add#add-windows-corporate-identifiers).

## Additional role-based access control (RBAC) permissions for Managed apps and Mobile apps

Date added: *June 18, 2024*

We added additional RBAC permissions for **Managed apps** and **Mobile apps** for the Windows Autopilot device preparation administrator role. For more information, see [Required RBAC permissions](requirements?tabs=rbac#required-rbac-permissions).

## Initial release of Windows Autopilot device preparation

Date added: *June 3, 2024*

Windows Autopilot device preparation is generally available. For an overview, see [Overview of Windows Autopilot device preparation](overview). For a tutorial on how to set up Windows Autopilot device preparation, see [Windows Autopilot device preparation scenarios](tutorial/scenarios).