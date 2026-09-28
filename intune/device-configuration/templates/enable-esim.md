---
layout: Conceptual
title: Enable eSIM data connections in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/templates/enable-esim
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.collection:
- M365-identity-device-management
ms.subservice: configuration
description: Add or use eSIM to get internet and data access using different data plans. In Intune, add or import activation codes, and then assign these activation codes using a configuration profile. You can also monitor the eSIM profiles and check the status of the eSIM-enabled devices.
keywords: 
ms.date: 2024-06-25T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: nicolezhao, hejimenez
locale: en-us
document_id: 1b9d04ef-38d9-cd9b-b9b9-6ed108af313a
document_version_independent_id: 1b9d04ef-38d9-cd9b-b9b9-6ed108af313a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/templates/enable-esim.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/templates/enable-esim
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/templates/enable-esim.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/e0ffb20c-01c6-407b-a9bd-29111652a1dc
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/3904bce4-d817-48cf-85fd-b6146fca83b7
platformId: fba6badc-0ab4-5014-1541-1d0e72e9d498
---

# Enable eSIM data connections in Microsoft Intune - Microsoft Intune | Microsoft Learn

eSIM is an embedded SIM chip, and lets you connect to the Internet over a cellular data connection on an eSIM-capable device, such as the [Surface LTE Pro](https://www.microsoft.com/surface/business/surface-pro). With an eSIM, you don't need to get a SIM card from your mobile operator. As a global traveler, you can also switch between mobile operators and data plans to always stay connected.

For example, you have a cellular data plan for work, and another data plan with a different mobile operator for personal use. When traveling, you can get Internet access by finding mobile operators with data plans in that area.

This feature applies to:

- Windows

In Intune, you can bulk activate eSIM codes using the following options:

| Option | Platform support | Description |
| --- | --- | --- |
| **Import activation codes using a CSV file (this article)** | ![check-icon](../../media/icons/16/check.svg) Windows 11 (**supported, but not recommended**) - [Use an eSIM download server](configure-esim-download-server) instead![check-icon](../../media/icons/16/check.svg) Windows 10 | In an eSIM policy, import one-time-use activation codes. The eSIM hardware uses the activation codes to contact the mobile operator, download the eSIM policy, and configure cellular activation. Requires individual activation codes given to you by the mobile operator. |
| **[eSIM download server](configure-esim-download-server)** | ![check-icon](../../media/icons/16/check.svg) Windows 11 (**recommended**) ![error-icon](../../media/icons/16/error.svg) Windows 10 | In a settings catalog policy, add your mobile operator's download server FQDN. The device contacts the download server, authenticates, and receives eSIM connection info. No individual activation codes needed. |

This article describes how to import the activation codes in bulk, and then deploy these codes to your eSIM-capable devices. This feature is in [public preview](../../fundamentals/public-preview).

Note

You can create a custom OMA-URI profile using the [eUICCs CSP](/en-us/windows/client-management/mdm/euiccs-csp). Be sure to deploy one custom profile for each device. The profile must include the device ICCID and matching activation code from the carrier for each device.

## Prerequisites

To deploy eSIM to your devices using Intune, you need the following prerequisites:

- **Windows** devices that are enrolled and MDM managed by Intune. For information on the enrollment options for Windows devices, go to [Windows enrollment guide for Microsoft Intune](../../device-enrollment/windows/guide).

    Important

    On October 14, 2025, [Windows 10 reached end of support](/en-us/lifecycle/announcements/windows-10-end-of-support) and won't receive quality and feature updates. Windows 10 is an **allowed** version in Intune. Devices running this version can still enroll in Intune and use eligible features, but functionality won't be guaranteed and can vary.
- **eSIM capable devices**, like the Surface LTE. To determine if your Windows device supports eSIM, go to [Use an eSIM to get a cellular data connection on your Windows PC](https://support.microsoft.com/help/4020763/windows-10-use-esim-for-cellular-data). If you're unsure if your devices support eSIM, then you can also contact your device manufacturer.
- **Activation codes** provided by your mobile operator. These one time-use activation codes are added to Intune, and deployed to your eSIM capable devices. Contact your mobile operator to acquire eSIM activation codes.
- Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) with an account that has the **[Policy and Profile Manager](../../fundamentals/role-based-access-control/ref-built-in-roles#policy-and-profile-manager)** built-in role. For more information on the built-in roles, go to [Role-based access control for Microsoft Intune](../../fundamentals/role-based-access-control/overview).

## Deploy eSIM to devices - overview

To deploy eSIM to devices, an Administrator completes the following tasks:

1. Import activation codes provided by your mobile operator
2. Create a Microsoft Entra device group that includes your eSIM capable devices
3. Assign the Microsoft Entra group to your imported subscription pool
4. Monitor the deployment

This article guides you through these steps.

## Step 1 - Add cellular activation codes

Cellular activation codes are provided by your mobile operator in a comma-separated file (csv). When you have this file, add it to Intune using the following steps:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** &gt; **Manage devices** &gt; **eSIM cellular profiles** &gt; **Add**.
3. Select the CSV file that has your activation codes.
4. Select **OK** to save your changes.

### CSV file requirements

When working with the `csv` file with the activation codes, be sure you or your mobile operator follows the requirements:

- The file must be in `csv` format (`filename.csv`).
- The file structure must adhere to a strict format. Otherwise, the import fails. Intune checks the file on import, and fails if errors are found.
- Activation codes are used only once. It's not recommended to import activation codes that you previously imported, as it can cause problems when you deploy to the same or different device.
- Each file should be specific to a single mobile operator, and all activation codes specific to the same billing plan. Intune randomly distributes the activation codes to targeted devices. There isn't any guarantee which device gets a specific activation code.
- A maximum of 1,000 activation codes can be imported in one `csv` file.

### CSV file example

1. The first row and first cell of the `csv` is the URL of the mobile operator eSIM activation service, which is called SM-DP+ (Subscription Manager Data Preparation server). The URL should be a fully qualified domain name (FQDN) without any commas.
2. The second and all later rows are unique one-time use activation codes that include two values:

    1. First column is the unique ICCID (the identifier of the SIM chip)
    2. Second column is the Matching ID with only a comma separating them (no comma at the end). See the following example:

        ![Mobile operator activation code sample csv file.](media/enable-esim/url-activation-code-examples.png)
3. The cellular subscription becomes the first part of the SMDP of your mobile operator. For example, in the previous image, the first row includes the `smdp.skynet.mobile` URL of the mobile operator. Intune names the cellular subscription pool name as `smdp`:

    ![Cellular subscription pool is named the activation code sample csv file name.](media/enable-esim/subscription-pool-name-csv-file.png)

Important

You can't have two lists with the same provider. If you try to upload two lists with the same provider, you may get a `The request is invalid` error message.

To add more devices with the same provider or carrier, then you must:

- Remove the current `.csv`.
- Upload a new `.csv` that has all the old device/ICCID pairs and has the new devices you want to add.

## Step 2 - Create a Microsoft Entra device group

Create a device group that includes the eSIM capable devices. [Add groups](../../fundamentals/tenant-administration/add-groups) lists the steps.

Note

- Only devices are targeted, users aren't targeted.
- We recommend creating a static Microsoft Entra device group that includes your eSIM devices. Using a group confirms you target only eSIM devices.

## Step 3 - Assign eSIM activation codes to devices

Assign the profile to the Microsoft Entra group that includes your eSIM devices.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** &gt; **Manage devices** &gt; **eSIM cellular profiles**.
3. In the list of profiles, select the eSIM cellular subscription pool you want to assign, and then select **Assignments**.
4. Choose to **Include** groups or **Exclude** groups, and then select the groups.

    ![Include the device group to assign the profile in Microsoft Intune.](media/enable-esim/include-exclude-groups.png)
5. When you select your groups, you're choosing a Microsoft Entra group. To select multiple groups, use the **Ctrl** key, and select the groups.
6. When done, **Save** your changes.

eSIM activation codes are used once. After Intune installs an activation code on a device, the eSIM module contacts the mobile operator to download the cellular profile. This contact finishes registering the device with the mobile operator network.

## Step 4 - Monitor deployment

### Review the deployment status

After you assign the profile, you can monitor the deployment status of a subscription pool.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** &gt; **Manage devices** &gt; **eSIM cellular profiles**. All of your existing eSIM cellular subscription pools are listed.
3. Select a subscription, and review the **Deployment Status**.

### Check the profile status

After you create your device profile, Intune provides graphical charts. These charts display the status of a profile, such as it being successfully assigned to devices, or if the profile shows a conflict.

1. Select **Devices** &gt; **Manage devices** &gt; **eSIM cellular profiles** &gt; Select an existing subscription.
2. In the **Overview** tab, the top graphical chart shows the number of devices assigned to the specific eSIM cellular subscription pool deployment.

    It also shows the number of devices for other platforms that are assigned the same device profile.

    Intune shows the delivery and installation status for the activation code targeted to devices.

    - **Device not synced**: The targeted device hasn't synced with the Intune service since the eSIM deployment policy was created. The device must check in with Intune to receive any policy.
    - **Activation pending**: A transient state when Intune is actively installing the activation code on the device
    - **Active**: Activation code installation successful
    - **Activation fail**: Activation code installation failed; Go to Best practices & troubleshooting (in this article).

#### View the detailed device status

In **Device Status**, you can monitor and view a detailed list of devices you can view.

1. Select **Devices** &gt; **Manage devices** &gt; **eSIM cellular profiles** &gt; Select an existing subscription.
2. Select **Device Status**. Intune shows more details about the device:

    - **Device Name**: Name of the device that is targeted
    - **User**: User of the enrolled device
    - **ICCID**: Unique code provided by the mobile operate within the activation code installed on the device
    - **Activation Status**: Intune delivery and installation status of the activation code on the device
    - **Cellular status**: State provided by the mobile operator. Follow up with mobile operator to troubleshoot.
    - **Last Check-In**: Date the device last communicated with Intune

### Monitor eSIM profile details on the actual device

1. On your device, open **Settings** &gt; go to **Network & Internet**.
2. Select **Cellular** &gt; **Manage eSIM profiles**.
3. The eSIM profiles are listed:

    ![View the eSIM profiles in your device settings.](media/enable-esim/device-settings-cellular-profiles.png)

## Remove the eSIM profile from device

When you remove the device from the Microsoft Entra group, the eSIM profile is also removed. Be sure to:

1. Confirm you're using the eSIM devices Microsoft Entra group.
2. Go to the Microsoft Entra group, and remove the device from the group.
3. When the removed device contacts Intune, the updated policy is evaluated, and the eSIM profile removed.

The eSIM profile is also removed when:

- The device is [retired](../../device-management/actions/retire).
- The user unenrolls the device from Intune.
- The [reset device remote action](../../device-management/actions/wipe) runs on the device.

Note

Removing the profile might not stop billing. Contact your mobile operator to check the billing status for your device.

## Best practices & troubleshooting

- Be sure your `.csv` file is properly formatted. Confirm the file doesn't include duplicate codes, doesn't include multiple mobile operators, or doesn't include different data plans. Remember, each file must be unique to a mobile operator and cellular data plan.
- Create a static device Microsoft Entra group that only includes the eSIM devices that are targeted.
- If there's an issue with the deployment status, check the following settings:

    - **File format not proper**: To properly format your file, go to **Step 1 - Add cellular activation codes** (in this article).
    - **Cellular activation failure, contact mobile operator**: The activation code might not be activated within their network. Or, the profile download and cellular activation failed.

## Resources

[Configure device profiles](../overview)