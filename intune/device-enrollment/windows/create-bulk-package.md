---
layout: Conceptual
title: Bulk Enrollment for Windows Devices - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-enrollment/windows/create-bulk-package
author: maholdaa
ms.author: maholdaa
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
ms.collection:
- M365-identity-device-management
ms.subservice: enrollment
description: Windows bulk enrollment lets you join corporate devices to Microsoft Entra ID and Intune at scale. Create a provisioning package and start enrolling.
ms.date: 2026-11-05T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 2f7a3d73-6b8d-29dd-6ead-2f658936709a
document_version_independent_id: 2f7a3d73-6b8d-29dd-6ead-2f658936709a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-enrollment/windows/create-bulk-package.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-enrollment/windows/create-bulk-package
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-enrollment/windows/create-bulk-package.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
platformId: adde4fd5-06b5-6111-25e2-96c97fe00ce4
---

# Bulk Enrollment for Windows Devices - Microsoft Intune | Microsoft Learn

Join new Windows devices to Microsoft Entra ID and Intune. To bulk enroll devices for your Microsoft Entra tenant, create a provisioning package by using the Windows Configuration Designer (WCD) app. When you apply the provisioning package to corporate-owned devices, you join the devices to your Microsoft Entra tenant and enroll them for Intune management. After you apply the package, the devices are ready for your Microsoft Entra users to sign in.

Microsoft Entra users are standard users on these devices and receive assigned Intune policies and required apps. Windows devices that are enrolled into Intune by using Windows bulk enrollment can use the Company Portal app to install available apps.

## Requirements

![](../../media/icons/16/devices.svg)**Device platform requirements**

> 
> This enrollment method supports the following platforms:
> 
> - Windows (supported versions)
> 

![](../../media/icons/16/tenant-administration.svg)**Tenant configuration requirements**

> 
> - Enable [Windows automatic enrollment](enable-automatic-mdm#enable-windows-automatic-enrollment).
> - Ensure the service principal for Microsoft.Azure.SyncFabric (AppID 00000014-0000-0000-c000-000000000000) is present in your Microsoft Entra tenant. In a command line, use the `Get-MgServicePrincipal -Filter "AppId eq '00000014-0000-0000-c000-000000000000'"` command to check for the [service principal](/en-us/entra/identity-platform/developer-glossary#service-principal-object). Without the service principal, Windows Configuration Designer can't retrieve the bulk enrollment token, which results in an error.
> 
>     To register the service principal, use the `New-MgServicePrincipal -AppId "00000014-0000-0000-c000-000000000000"` command. To learn more about this command, see [New-MgServicePrincipal](/en-us/powershell/module/microsoft.graph.applications/new-mgserviceprincipal).
> 

![](../../media/icons/16/rbac.svg)**Roles requirements**

> 
> To create a bulk enrollment token, use an account with one of the following Microsoft Entra roles. The account must not be scoped to an administrative unit in Microsoft Entra ID:
> 
> - Cloud Device Administrator
> - Intune Administrator
> - Password Administrator
> 
> 
> For more information, see [Microsoft Entra built-in roles](/en-us/entra/identity/role-based-access-control/permissions-reference).

Important

On October 14, 2025, [Windows 10 reached end of support](/en-us/lifecycle/announcements/windows-10-end-of-support) and won't receive quality and feature updates. Windows 10 is an **allowed** version in Intune. Devices running this version can still enroll in Intune and use eligible features, but functionality won't be guaranteed and can vary.

## Create a provisioning package

1. Install [Windows Configuration Designer (WCD)](https://www.microsoft.com/p/windows-configuration-designer/9nblggh4tx22) from the Microsoft Store.
2. Open the **Windows Configuration Designer** app and select **Provision desktop devices**.

    ![Screenshot of selecting Provision desktop devices in the Windows Configuration Designer app.](media/create-bulk-package/bulk-enroll-select.png)
3. A **New project** window opens where you specify the following information:

    - **Name** - A name for your project
    - **Project folder** - Save location for the project
    - **Description** - An optional description of the project

    ![Screenshot of specifying name, project folder, and description in the Windows Configuration Designer app.](media/create-bulk-package/bulk-enroll-name.png)
4. Enter a unique name for your devices. Names can include a serial number (%SERIAL%) or a random set of characters. Optionally, enter a product key if you're upgrading the edition of Windows. You can also configure the device for shared use and remove preinstalled software.

    ![Screenshot of specifying name and product key in the Windows Configuration Designer app.](media/create-bulk-package/bulk-enroll-device.png)
5. Optionally, you can configure the Wi-Fi network devices connect to when they first start. If the network devices aren't configured, a wired network connection is required when the device is first started.

    ![Screenshot of enabling Wi-Fi including Network SSID and Network type options in the Windows Configuration Designer app.](media/create-bulk-package/bulk-enroll-network.png)
6. Select **Enroll in Azure AD**, enter a **Bulk Token Expiry** date, and then select **Get Bulk Token**. The token validity period is 90 days.

    Note

    After you create a provisioning package, you can revoke it before it expires by removing the associated `package_{GUID}` user account from Microsoft Entra ID.

    Because the bulk enrollment process uses the `package_{GUID}` user account, tenants that use Conditional Access policies with MFA must set an exclusion or disable MFA for this process. MFA isn't supported for this scenario.
7. Provide your Microsoft Entra credentials to get a bulk token. Ensure you authenticate by using password or CBA authentication, since the app doesn't support other methods of authentication for this operation.

    ![Screenshot of signing in to the Windows Configuration Designer app.](media/create-bulk-package/bulk-enroll-cred.png)

    Note

    - The account you use to request the bulk enrollment token in the Windows Configuration Designer app must be included in the [MDM user scope](enable-automatic-mdm#enable-windows-automatic-enrollment) in Microsoft Entra ID. If you remove this account from a group that's tied to the MDM user scope, bulk enrollment stops working.
    - Bulk token retrieval doesn't work for federated user accounts enabled for staged rollouts.
8. In the **Stay signed in to all your apps** page, select **No, sign in to this app only**. If you keep the checkbox selected and select **OK**, the device you're using becomes managed by your organization. If you don't intend for your device to be managed, select **No, sign in to this app only**.
9. Select **Next** when **Bulk Token** is fetched successfully.
10. Optionally, **Add applications** and **Add certificates**. The app and certificates are provisioned on the device.
11. Optionally, password protect your provisioning package. Select **Create**.

    ![Screenshot of package protection in the Windows Configuration Designer app.](media/create-bulk-package/bulk-enroll-create.png)

## Provision devices

1. Access the provisioning package in the location specified in **Project folder** in the app.
2. Choose how to apply the provisioning package to the device. You can apply a provisioning package to a device in one of the following ways:

    - Place the provisioning package on a USB drive, insert the USB drive into the device you want to bulk enroll, and apply it during initial setup.
    - Place the provisioning package on a network folder, and apply it after initial setup.

    For step-by-step instructions on applying a provisioning package, see [Apply a provisioning package](/en-us/windows/configuration/provisioning-packages/provisioning-apply-package).
3. After you apply the package, the device automatically restarts in one minute.

    ![Screenshot of project folder, specifying name, and description in the Windows Configuration Designer app.](media/create-bulk-package/bulk-enroll-add.png)
4. When the device restarts, it connects to Microsoft Entra ID and enrolls in Microsoft Intune.

## Troubleshooting Windows bulk enrollment

### Provisioning issues

Use provisioning on new Windows devices. Provisioning failures might require a wipe of the device or device recovery from a boot image. These examples describe some reasons for provisioning failures:

- A provisioning package that attempts to join an Active Directory domain or Microsoft Entra tenant but doesn't create a local account could make the device unreachable if the domain-join process fails due to lack of network connectivity.
- Scripts run by the provisioning package run in system context. The scripts can make arbitrary changes to the device file system and configurations. A malicious or bad script could put the device in a state that can only be recovered by reimaging or wiping the device.

Check for success or failure of the settings in your package in the **Provisioning-Diagnostics-Provider** Admin log in Event Viewer.

Note

Bulk enrollment is a userless enrollment method. Because of this characteristic, only the **Default** enrollment restriction in Intune applies during enrollment. Ensure Windows platform is allowed in the default restriction; otherwise, the enrollment fails. To check the capabilities alongside other Windows enrollment methods, see [Intune enrollment method capabilities for Windows devices](guide).

### Bulk enrollment with Wi-Fi

When you don't use an open network, use [device-level certificates](../../fundamentals/certificates/overview) to initiate connections. Bulk enrolled devices can't use user-targeted certificates for network access.

### Conditional Access

Conditional Access is available for devices enrolled by using bulk enrollment running Windows 11 or Windows 10, version 1803 and later.

Important

On October 14, 2025, [Windows 10 reached end of support](/en-us/lifecycle/announcements/windows-10-end-of-support) and won't receive quality and feature updates. Windows 10 is an **allowed** version in Intune. Devices running this version can still enroll in Intune and use eligible features, but functionality won't be guaranteed and can vary.