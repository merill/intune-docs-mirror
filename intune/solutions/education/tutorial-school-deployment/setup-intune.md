---
layout: Conceptual
title: Set up device management - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/solutions/education/tutorial-school-deployment/setup-intune
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: scottbreenmsft
ms.author: scbree
ms.subservice: education
description: Learn how to configure the Intune service and set up the environment for education.
ms.date: 2024-05-02T00:00:00.0000000Z
ms.topic: tutorial
zone_pivot_groups: platforms-windows-ios
locale: en-us
document_id: bfae49fe-bae1-f7f6-9f26-a5cd19c73252
document_version_independent_id: bfae49fe-bae1-f7f6-9f26-a5cd19c73252
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/solutions/education/tutorial-school-deployment/setup-intune.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: solutions/education/tutorial-school-deployment/setup-intune
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/solutions/education/tutorial-school-deployment/setup-intune.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: fd7f819e-a8e9-a03b-43fc-60a3d99bfbfc
---

# Set up device management - Microsoft Intune | Microsoft Learn

Without the proper tools and resources, managing hundreds or thousands of devices in a school environment can be a complex and time-consuming task. Microsoft Intune is a collection of services that simplifies the management of devices at scale.

The Microsoft Intune service can be managed in different ways.

- **Intune admin center** is the primary Intune interface that supports the entire device lifecycle, from the enrollment phase through retirement. IT administrators can manage all settings across all Intune supported platforms.
- **Intune for Education** is a curated view of Intune that supports the entire device lifecycle, from the enrollment phase through retirement. IT administrators can start managing classroom devices with bulk enrollment options and a streamlined deployment. At the end of the school year, IT admins can reset devices, ensuring they're ready for the next year.

    [![Intune for Education dashboard](media/setup-intune/intune-education-portal.png)](media/setup-intune/intune-education-portal.png#lightbox)

    For more information, see [Intune for Education documentation](/en-us/intune-education/what-is-intune-for-education).

Tip

**Intune** and **Intune for Education** both configure the **Intune** service. Changes made in one admin center are reflected in the other. However, **Intune for Education** only supports a subset of policies and apps curated to suit simple K-12 scenarios on Windows and iPadOS.

In this section you will:

- Review Intune's licensing prerequisites
- Configure the Intune service for education devices

## Prerequisites

![](../../../media/icons/16/check.svg) Check out the requirements for device management

Before configuring settings with Intune, consider the following prerequisites:

- **Intune subscription.**Microsoft Intune is licensed in three ways:
    - As a standalone service
    - As part of [Enterprise Mobility + Security](https://www.microsoft.com/microsoft-365/microsoft-365-enterprise)
    - As part of a [Microsoft 365 Education subscription](https://www.microsoft.com/licensing/product-licensing/microsoft-365-education)
- **Intune for Education device platforms.** Intune for Education can manage devices running a supported version of Windows, Windows 11 SE, and iPadOS
- **Intune device platforms.** Intune can manage devices running a supported version of Windows, Windows 11 SE, iOS, iPadOS, macOS, Android, and Linux
- **Network requirements.** Confirm all the required network endpoints can access without SSL inspection or any type of filtering. See [Network endpoints for Microsoft Intune](../../../fundamentals/endpoints) for a list of endpoints.

For more information, see [Intune licensing](../../../fundamentals/licensing) and [this comparison sheet](https://aka.ms/EDU-Plan-Comparison), which includes a table detailing the *Microsoft Modern Work Plan for Education*.

## Configure the Intune service for Education devices

The Intune service can be configured in different ways, depending on the needs of your school. In this section, you configure the Intune service using settings commonly implemented by K-12 school districts.

### Configure enrollment restrictions

![](../../../media/icons/16/check.svg) Restrict which devices can be managed

With enrollment restrictions, you control which devices can enroll and be managed by Intune. For example, you can prevent the enrollment of personal devices.

To block personally owned devices from enrolling:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** &gt; **Enroll devices** &gt; **Device platform restrictions**.
3. Select the tab for the platform you want to restrict.
4. Select **Create restriction**.
5. On the **Basics** page, provide a name for the restriction and, optionally, a description &gt; **Next**.
6. On the **Platform settings** page, in the **Personally owned devices** field, select **Block** &gt; **Next**. [![This screenshot is of the device enrollment restriction page in Microsoft Intune admin center.](media/setup-intune/enrollment-restrictions.png)](media/setup-intune/enrollment-restrictions.png#lightbox)
7. Optionally, on the **Scope tags** page, add scope tags &gt; **Next**.
8. On the **Assignments** page, select **Add groups**, and then use the search box to find and choose groups to which you want to apply the restriction &gt; **Next**.
9. On the **Review + create** page, select **Create** to save the restriction.

For more information, see [Create a device platform restriction](../../../device-enrollment/restrictions).

### Optional configuration

![](../../../media/icons/16/check.svg) Configure optional tenant configuration

- Customize branding according to organization policies. For more information, see [How to configure the Intune Company Portal apps, Company Portal website, and Intune app](../../../app-management/configuration/configure-company-portal).
- Create Terms and conditions according to organization policies. For more information, see [Terms and conditions for user access](../../../device-enrollment/create-terms-and-conditions).

::: zone pivot="windows"

### Configure Windows enrollment

![](../../../media/icons/16/check.svg) Configure which users can enroll Windows devices

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** &gt; **Enroll devices** &gt; **Automatic Enrollment**.
3. Set the **MDM user scope** to **All** or **Some** and select a group if you want to restrict enrollment to certain users. 
    Important

    The MDM user scope must be set to *All* if provisioning packages are used to enroll devices.
4. Set **MAM user scope** to **None**. [![A screenshot showing the MDM user scope and MAM user scope.](media/setup-intune/intune-windows-enrollment.png)](media/setup-intune/intune-windows-enrollment.png#lightbox)
5. Select **Save**.

For more information, see [Enable Windows automatic enrollment](../../../device-enrollment/windows/enable-automatic-mdm#enable-windows-automatic-enrollment).

### Disable Windows Hello for Business

![](../../../media/icons/16/check.svg) Disable functionality typically inaccessible to students

Windows Hello for Business is a biometric authentication feature that allows users to sign in to their devices using a PIN, password, or fingerprint. Windows Hello for Business is enabled by default on Windows devices, and to set it up, users must perform for multifactor authentication (MFA). As a result, this feature might not be ideal for students, who don't have MFA enabled.

Tip

**Passwordless for Students**

If you're interested in using Windows Hello for Business with students, then review our guidance on how you can use Temporary Access Pass. For more information, see [Passwordless for Students](/en-us/microsoft-365/education/deploy/protect-passwordless-students).

It's common for Windows Hello for Business to be disabled at the tenant level. Then, a policy can be targeted at users or devices that need it. For example, staff and teachers.

To disable Windows Hello for Business at the tenant level:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** &gt; **By platform** &gt; **Windows** &gt; **Device onboarding** &gt; **Enrollment**.
3. Select **Windows Hello for Business**.
4. Ensure that **Configure Windows Hello for Business** is set to **disabled**.
5. Select **Save**.

[![Disablement of Windows Hello for Business from Microsoft Intune admin center.](media/setup-intune/whfb-disable.png)](media/setup-intune/whfb-disable.png#lightbox)

For more information how to enable Windows Hello for Business on specific devices, see [Create a Windows Hello for Business policy](../../../device-security/identity-protection/configure-tenant-wide-policy).

### Configure Intune data collection policy

![](../../../media/icons/16/check.svg) Configure Endpoint analytics

Intune needs permission to collect data for Endpoint analytics on Windows devices.

To enable data collection:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Reports** &gt; **Endpoint analytics** &gt; **Settings**.
3. Under **Intune data collection policy**, select **Intune data collection policy**. [![Selecting the Intune data collection policy.](media/setup-intune/intune-data-collection-policy.png)](media/setup-intune/intune-data-collection-policy.png#lightbox)
4. Select **Properties**.
5. Under **Configuration settings** select **Edit**.
6. Set **Health Monitoring** to **Enable**.
7. Select **Scope** and tick **Endpoint analytics**. [![A screenshot showing the configuration of the Intune data collection policy.](media/setup-intune/intune-data-collection-policy-settings.png)](media/setup-intune/intune-data-collection-policy-settings.png#lightbox)
8. Select **Review + Save**.
9. Select **Save**.

For more information on data collection, see [Endpoint analytics data collection](../../../endpoint-analytics/ref-data-collection).

### Configure Windows data

![](../../../media/icons/16/check.svg) Configure tenant Windows data settings

Intune needs permission to collect certain data for Windows update reports on Windows devices.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Tenant administration** &gt; **Connectors and tokens** &gt; **Windows data**
3. Under **Windows data** select **On**.
4. Review the **Windows license verification** section and configure as per your licensing. [![A screenshot showing the configuration of the Intune Windows data settings.](media/setup-intune/intune-windows-data.png)](media/setup-intune/intune-windows-data.png#lightbox)
5. Select **Save**.

For more information, see [Enable use of Windows diagnostic data by Intune](../../../privacy/enable-windows-diagnostic-data).

### Configure Windows device diagnostics

![](../../../media/icons/16/check.svg) Allow remote retrieval of diagnostic information

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Tenant administration** &gt; **Device diagnostics**.
3. Configure settings as per your requirements.

This table provides the settings most commonly set by customers, but can be customized to suit your schools needs.

| Setting | Common configuration |
| --- | --- |
| Device diagnostics are available for corporate-managed devices running Windows. Diagnostics can include user identifiable information such as user or device name. | Enabled |
| Automatically capture diagnostics when devices experience a failure during the Windows Autopilot process on Windows. Diagnostics can include user identifiable information such as user or device name. | Enabled |

For more information, see [Collect diagnostics from a Windows device](../../../device-management/actions/collect-diagnostics).

### (Optional) Configure the Enrollment Status Page

Consider enabling the Enrollment Status Page if planning to use Windows Autopilot to enroll Windows devices in Intune.

The enrollment status page (ESP) displays the provisioning status to people enrolling Windows devices and signing in for the first time. You can configure the ESP to block device use until all required policies and applications are installed. Device users can look at the ESP to track how far along their device is in the setup process.

Additional information:

- [Windows Autopilot Enrollment Status Page](/en-us/autopilot/enrollment-status)
- [Set up the Enrollment Status Page](../../../device-enrollment/windows/setup-status-page)

This table provides the settings most commonly set by customers, but can be customized to suit your schools needs.

| **Blade** | **Configuration group** | **Setting** | **Value** |
| --- | --- | --- | --- |
| [Windows enrollment](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesEnrollmentMenu/%7E/windowsEnrollment) | General\Enrollment Status Page | Default\Show app and profile configuration progress | Yes |
| [Windows enrollment](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesEnrollmentMenu/%7E/windowsEnrollment) | General\Enrollment Status Page | Default\Show an error when installation takes longer than specified number of minutes | 120 |
| [Windows enrollment](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesEnrollmentMenu/%7E/windowsEnrollment) | General\Enrollment Status Page | Default\Show custom message when time limit or error occurs | Yes |
| [Windows enrollment](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesEnrollmentMenu/%7E/windowsEnrollment) | General\Enrollment Status Page | Default\Turn on log collection and diagnostics page for end users | Yes |
| [Windows enrollment](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesEnrollmentMenu/%7E/windowsEnrollment) | General\Enrollment Status Page | Default\Only show page to devices provisioned by out-of-box experience (OOBE) | Yes |
| [Windows enrollment](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesEnrollmentMenu/%7E/windowsEnrollment) | General\Enrollment Status Page | Enrollment Status Page\Default\Block device use until required apps are installed if they're assigned to the user/device | *All* or *Selected* with the minimum apps required. For example, Microsoft 365 apps or web content filtering software |

::: zone-end

::: zone pivot="ios"

### Set up Apple MDM Certificate

# [Intune](#tab/intune)
To set up an Apple MDM certificate, see [Get an Apple MDM push certificate](../../../device-enrollment/apple/create-mdm-push-certificate#steps-to-get-your-certificate).

# [Intune for Education](#tab/intune-for-education)
To set up an Apple MDM certificate in Intune for Education, see [Add an MDM push certificate](/en-us/intune-education/setup-ios-device-management)

---

Important

The Apple MDM certificate needs to be renewed yearly. Make a note in your calendar to renew the certificate in just under a year from when you add the certificate. You can view the expiry date in the admin center at any time.

### Configure Volume Purchase Program (VPP)

# [Intune](#tab/intune)
To set up an Apple VPP, see [How to manage iOS and macOS apps purchased through Apple Business with Microsoft Intune](../../../app-management/deployment/manage-vpp-apple).

# [Intune for Education](#tab/intune-for-education)
To set up an Apple VPP in Intune for Education, see [Configure VPP tokens](/en-us/intune-education/setup-ios-device-management#configure-vpp-tokens).

---

Important

The Apple VPP token needs to be renewed yearly. Make a note in your calendar to renew the token in just under a year from when you add the token. You can view the expiry date in the admin center at any time.

### Configure Automated Device Enrollment (ADE)

If you plan to integrate Apple School Manager and use Automated Device Enrollment, follow these steps.

# [Intune](#tab/intune)
To set up an Apple MDM certificate, see [Set up automated device enrollment in Intune](../../../device-enrollment/apple/setup-automated-ios).

# [Intune for Education](#tab/intune-for-education)
To set up an Apple ADE in Intune for Education, see [Configure enrollment program token](/en-us/intune-education/setup-ios-device-management#configure-enrollment-program-token).

---

Important

The Apple ADE token needs to be renewed yearly. Make a note in your calendar to renew the token in just under a year from when you add the token. You can view the expiry date in the admin center at any time.

::: zone-end