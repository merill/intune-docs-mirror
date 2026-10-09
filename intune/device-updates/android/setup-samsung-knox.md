---
layout: Conceptual
title: Integrate Samsung Knox E-FOTA with Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-updates/android/setup-samsung-knox
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.subservice: protect
description: Learn how to integrate Samsung Knox E-FOTA with Microsoft Intune to register Samsung devices, configure firmware updates, and monitor campaigns.
ms.date: 2026-10-02T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: grwilso
ai-usage: ai-generated
ms.custom: msecd-doc-authoring-1017
locale: en-us
document_id: 8222de5b-1057-587a-c8fe-9f1ca9542297
document_version_independent_id: 8222de5b-1057-587a-c8fe-9f1ca9542297
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-updates/android/setup-samsung-knox.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-updates/android/setup-samsung-knox
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-updates/android/setup-samsung-knox.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: b1e5c6a8-7105-c673-c3de-9ad5fbd8d8c3
---

# Integrate Samsung Knox E-FOTA with Microsoft Intune - Microsoft Intune | Microsoft Learn

Samsung Knox E-FOTA (Firmware Over-the-Air) lets IT administrators remotely deploy firmware updates to corporate-owned Samsung devices. Administrators can select firmware versions and schedule downloads and installations to reduce device downtime. After registration, firmware deployments don't require user interaction.

The Microsoft Intune integration brings Knox E-FOTA capabilities into the admin center. Before you begin, review the device, network, licensing, role, tenant, and cloud prerequisites. With this integration, you can:

- Launch, manage, and monitor firmware update campaigns for Samsung devices from the admin center.
- Lock devices to a specific operating system (OS) version or selected firmware.
- Schedule download and install windows to minimize device downtime.

## Prerequisites

![](../../media/icons/16/devices.svg)**Device platform requirements**

> 
> Samsung Knox E-FOTA updates are supported on Android Enterprise devices enrolled in Intune. This support includes the following enrollment types:
> 
> - Android Enterprise corporate-owned dedicated (COSU)
> - Android Enterprise corporate-owned fully managed (COBO)
> - Android Enterprise corporate-owned with a work profile (COPE)
> 
> 
> For information about which devices are supported by Samsung Knox, see [Devices Secured by Knox](https://www.samsungknox.com/knox-platform/supported-devices).

![](../../media/icons/16/network-connectivity.svg)**Network and connectivity requirements**

> 
> For information about service ports and endpoints used by Samsung Knox, see [Samsung Knox firewall exceptions](https://docs.samsungknox.com/admin/knox-admin-portal/get-started/samsung-knox-firewall-exceptions/#knox-e-fota).

![](../../media/icons/16/licensing.svg)**Licensing requirements**

> 
> You need a Samsung Knox E-FOTA license to use the service. For more information, see [Samsung Knox E-FOTA](https://docs.samsungknox.com/admin/knox-efota/).
> 
> You also need at least a Microsoft 365 E3 plan to use the service.

![](../../media/icons/16/rbac.svg)**Roles requirements**

> 
> The required permissions depend on the task.
> 
> To **set up the Samsung connector**, sign in with an account assigned the [Intune Administrator](/en-us/entra/identity/role-based-access-control/permissions-reference#intune-administrator) role.
> 
> You also need a *Samsung Knox administrator* account to connect Intune to Samsung Knox E-FOTA. For more information, see [Manage admins](https://docs.samsungknox.com/admin/knox-admin-portal/how-to-guides/admins-and-roles/manage-admins/).
> 
> If your organization uses [Microsoft Entra Privileged Identity Management (PIM)](/en-us/entra/id-governance/privileged-identity-management/pim-configure), activate the Intune Administrator role only when you configure the connector.
> 
> To configure devices and manage Samsung Knox E-FOTA deployments, use an account with at least the following permissions:
> 
> - [Android FOTA](/en-us/intune/fundamentals/role-based-access-control/create-custom-role#android-fota) (to register devices with Samsung Knox E-FOTA and manage their firmware updates)
> - [Mobile apps](/en-us/intune/fundamentals/role-based-access-control/create-custom-role#mobile-apps) (to deploy the required apps to the devices)
> - [Device configurations](/en-us/intune/fundamentals/role-based-access-control/create-custom-role#device-configurations) (to configure the devices by using an OEM configuration template)
> 

![](../../media/icons/16/tenant-administration.svg)**Tenant configuration requirements**

> 
> You must configure Managed Google Play for your tenant. For setup instructions, see [Set up Managed Google Play](../../device-enrollment/android/connect-managed-google-play).

![](../../media/icons/16/cloud.svg)**Cloud requirements**

> 
> Samsung Knox E-FOTA updates are supported in the public cloud and in U.S. Government Community Cloud (GCC) High.

## Process overview

The process for using Samsung Knox E-FOTA through Intune is as follows:

1. Set up the Samsung connector.
2. Deploy the required apps to the devices.
3. Configure the devices by using an OEM configuration template.
4. Sync devices with Samsung.
5. Complete device registration.

After the devices are registered with Samsung, you can create an E-FOTA deployment to manage firmware updates for the devices.

### ![](media/setup-samsung-knox/connector.svg) Set up the Samsung connector

In the Microsoft Intune admin center, link Intune and Samsung Knox E-FOTA by creating a connector. The connector allows Intune to communicate with Samsung Knox E-FOTA and manage firmware updates for eligible Samsung devices.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **[Tenant administration](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/TenantAdminMenu/%7E/tenantStatus)** &gt; **[Connectors and tokens](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/TenantAdminMenu/%7E/connectorsAndTokens)** &gt; **[Firmware over-the-air update](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/TenantAdminConnectorsMenu/%7E/fotaUpdate)**.
3. Select **Samsung**.
4. Select **Connect**, and then select **Connect** again to confirm. The Samsung Knox E-FOTA portal opens. Sign in with a Samsung Knox administrator account and authorize the connection.
5. After the connection is established, you're redirected to the Intune admin center. The connector is listed as **Connected**.

### ![](media/setup-samsung-knox/app.svg) Deploy the required apps to the devices

Samsung Knox requires the following apps on each device to enroll it in the E-FOTA service:

- **Knox E-FOTA** (`com.samsung.android.knox.efota`)
- **Knox Service Plugin** (`com.samsung.android.knox.kpu`)

Add both apps to your tenant through Managed Google Play. Assign the apps as **Required** to the security groups that contain the Samsung devices you want to register. Intune then deploys the apps to those devices.

For more information, see [Add and assign Managed Google Play apps to Android Enterprise devices](../../app-management/deployment/add-managed-google-play).

### ![](media/setup-samsung-knox/configure.svg) Configure the devices by using an OEM configuration template

To manage firmware updates through the E-FOTA service, configure the devices by using an OEM configuration template.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** &gt; **Configuration**.
3. Under **Policies**, select **Create**.
4. In **Create profile**, use the following settings and select **Create**:
    - **Platform**: Android Enterprise
    - **Profile type**: Templates
    - **Template name**: OEMConfig
5. Under **Configuration settings**, select:
    - **Enable device policy controls**: true
    - **Enable firmware controls**: true
    - **Enable E-FOTA client installation & launch**: true
6. Assign the device configuration to the same security group that contains the devices you registered with Samsung.
7. Select **Next**.

### ![](media/setup-samsung-knox/registration.svg) Sync devices with Samsung

To manage firmware updates for Samsung devices with Intune, register the devices with Samsung Knox E-FOTA. Assign the security groups that contain these devices to the Samsung connector.

To register the devices with Samsung:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **[Tenant administration](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/TenantAdminMenu/%7E/tenantStatus)** &gt; **[Connectors and tokens](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/TenantAdminMenu/%7E/connectorsAndTokens)** &gt; **[Firmware over-the-air update](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/TenantAdminConnectorsMenu/%7E/fotaUpdate)**.
3. Select **Samsung** to open the Samsung Knox E-FOTA connector setup.
4. Select **Add groups**, and then select the security groups that contain the Samsung devices to manage by using E-FOTA.
5. Select **Register**.
6. The devices are uploaded to Samsung. Use the Samsung Knox administrator account to view them in the Knox Admin Portal.

### ![](media/setup-samsung-knox/registration-complete.svg) Complete device registration

On each targeted Samsung device, open the **Knox E-FOTA** app. A device user must accept the terms and conditions to complete registration with Samsung Knox E-FOTA.

## Create an E-FOTA update campaign

After you register the devices with Samsung Knox E-FOTA, you can create a deployment to manage the firmware updates for the devices you registered. Samsung Knox E-FOTA deployments are also called *campaigns*.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** &gt; **Android** &gt; **Manage updates** &gt; **Android FOTA deployments**.
3. Select **Create**.
4. In the **Create deployment - Basics** pane, select the device model, sales code, CSC, and firmware version.
5. In the **Create deployment - Settings** pane, configure the **deployment schedule**, **installation schedule**, and **device condition**.
6. Assign the deployment to the group of devices you registered with Samsung.
7. On the **Monitor** tab, review the campaign summary and status. From the summary, you can edit, cancel, or delete the campaign and open the campaign report. Status data from Samsung refreshes every hour.

You can also review the campaign in the Knox Admin Portal. After you assign the campaign, verify its status on a targeted Samsung device in the Knox E-FOTA app.

## Device registration status report

You can view the device registration status for devices registered with Samsung Knox E-FOTA in the Intune admin center. The report refreshes every hour with device status from Samsung.

To view the device registration status report:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **[Tenant administration](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/TenantAdminMenu/%7E/tenantStatus)** &gt; **[Connectors and tokens](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/TenantAdminMenu/%7E/connectorsAndTokens)** &gt; **[Firmware over-the-air update](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/TenantAdminConnectorsMenu/%7E/fotaUpdate)**.
3. Select **Samsung**.
4. Select the **Monitor** tab to view the device registration status report.
5. To view the list of devices registered with Samsung, select **View devices**. The device registration status report shows the following information for each device:
    - **Device name**
    - **Registration status**
    - **Status detail**
    - **Last status update (UTC)**

## Disconnect the Samsung connector

To disconnect the Samsung connector, follow these steps:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **[Tenant administration](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/TenantAdminMenu/%7E/tenantStatus)** &gt; **[Connectors and tokens](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/TenantAdminMenu/%7E/connectorsAndTokens)** &gt; **[Firmware over-the-air update](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/TenantAdminConnectorsMenu/%7E/fotaUpdate)**.
3. Select **Samsung**.
4. Select **Disconnect** and confirm the disconnection. This action disconnects your Intune tenant from Samsung Knox E-FOTA.