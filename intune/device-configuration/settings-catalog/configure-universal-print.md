---
layout: Conceptual
title: Configure Universal Print Policy Using Settings Catalog - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/settings-catalog/configure-universal-print
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
description: Learn how to configure a Universal Print policy using the settings catalog in Microsoft Intune to automatically install printers on managed Windows devices.
ms.date: 2026-05-13T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: laarrizz, mayurjadhav
locale: en-us
document_id: 76b07d40-c604-6ebf-487e-d6b0e4de7dfd
document_version_independent_id: 76b07d40-c604-6ebf-487e-d6b0e4de7dfd
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/settings-catalog/configure-universal-print.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/settings-catalog/configure-universal-print
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/settings-catalog/configure-universal-print.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
platformId: 378a0381-a9f4-7a6c-73cc-254048fc9056
---

# Configure Universal Print Policy Using Settings Catalog - Microsoft Intune | Microsoft Learn

Many organizations are moving their printer infrastructure to the cloud. [Universal Print](/en-us/universal-print/fundamentals/universal-print-whatis) is a cloud-based printing solution in Microsoft 365. It uses built-in cloud printers, built-in legacy printers, and runs entirely in Microsoft Azure.

When you deploy Universal Print with Universal Print-compatible printers, it doesn't require any on-premises infrastructure. For a guided simulation, see [Universal Print guided simulation](https://regale.cloud/Microsoft/viewer/1265/index.html#/0/0).

By using the settings catalog in Intune, you can create a printer policy and deploy the policy to your managed users and devices. Then, on their devices, end users select the printer from a list of registered Universal Print printers to print. These settings use the [UniversalPrint CSP](/en-us/windows/client-management/mdm/universalprint-csp).

This feature applies to:

- Windows

This article shows you how to create a Universal Print policy in Microsoft Intune. To learn more about Universal Print and onboarding, see [What is Universal Print](/en-us/universal-print/fundamentals/universal-print-whatis) and [Set up Universal Print](/en-us/universal-print/fundamentals/universal-print-getting-started).

Tip

The **PrintProvisioning** tool and the **printers.csv** file process are deprecated. Be sure to use the steps in this article to install Universal Print printers.

## Prerequisites

![](../../media/icons/16/licensing.svg)**Licensing requirements**

> 
> To use this feature, you need the following subscriptions:
> 
> - **Universal Print**: For more specific information, go to [License Universal Print](/en-us/universal-print/fundamentals/universal-print-license).
> - **Microsoft Intune**: For more specific information, go to [Microsoft Intune licensing](../../fundamentals/licensing).
> 

![](../../media/icons/16/configuration.svg)**Device configuration requirements**

> 
> - Every printer must be registered in the Universal Print service (UP), which uses Microsoft Entra ID. For more information, go to [What is printer registration?](/en-us/universal-print/fundamentals/universal-print-printer-registration).
> - To create the Intune policy, you need the following printer information. Get this information from the Printer Administrator in your organization:
> 
>     - Device ID
>     - Printer shared ID
>     - Printer shared name
> 

![](../../media/icons/16/rbac.svg)**Roles requirements**

> 
> **Admins** need the following roles/licenses:
> 
> - **Policy and Profile Manager** role: Needed to create and assign Intune policies. For information on this role, go to [Role-based access control (RBAC) with Microsoft Intune](../../fundamentals/role-based-access-control/overview)
> - An assigned Universal Print license.
> 
> 
> **End users** need the following permissions/licenses:
> 
> - An assigned Universal Print license
> - Access rights to the printer service and the Universal Print service
> 
> 
> If you assign the profile to a Microsoft Entra user or user group that can't access the printers because of permissions, Intune grants the assigned user or user group the permissions.

## Create the policy

This policy includes your printer information. When you assign the policy, the printers are automatically installed. Then, on their devices, users select a printer that you added.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** &gt; **Manage devices** &gt; **Configuration** &gt; **Create** &gt; **New policy**.
3. Enter the following properties:

    - **Platform**: Select **Windows 10 and later**.
    - **Profile type**: Select **Settings catalog**.
4. Select **Create**.
5. In **Basics**, enter the following properties:

    - **Name**: Enter a descriptive name for the profile. Name your profiles so you can easily identify them later. For example, a good profile name is **Win11: Universal Print policy**.
    - **Description**: Enter a description for the profile. This setting is optional, but recommended.
6. Select **Next**.
7. In **Configuration settings**, select **Add settings**. In the settings picker, select **Printer Provisioning**, and select the settings you want to configure.

    ![Screenshot that shows how to select printer provisioning in the settings catalog to create a Universal Print policy in Microsoft Intune and Intune admin center.](media/configure-universal-print/settings-picker-printer-provisioning.png)

    Close the settings picker.
8. Configure the settings:

    - **Action**: Select **Install** to install a printer. When users receive the policy, the printer automatically installs.
    - **Cloud Device ID**: Enter the printer ID. This ID is created when the printer is registered in Microsoft Entra ID using the Universal Print service. To get the ID, use the [Universal Print portal](/en-us/universal-print/reference/portal/navigate-azure-portal).
    - **Printer Shared ID**: Enter the Shared ID of the printer. To get the ID, use the [Universal Print portal](/en-us/universal-print/reference/portal/navigate-azure-portal).
    - **Printer Shared Name**: Enter the Shared Name of the printer. To get the name, use the [Universal Print portal](/en-us/universal-print/reference/portal/navigate-azure-portal).

    You can add more printers using the **Add** button:

    ![Screenshot that shows how to add more printers to the Universal Print policy in the settings catalog in Microsoft Intune and Intune admin center.](media/configure-universal-print/add-printer.png)
9. Select **Next**.
10. In **Scope tags** (optional), assign a tag to filter the profile to specific IT groups. For more information about scope tags, see [Use RBAC roles and scope tags for distributed IT](../../fundamentals/role-based-access-control/scope-tags).

    Select **Next**.
11. In **Assignments**, select the users that will receive your profile.

    These user accounts need access rights to the printer and the Universal Print service. If the profile is assigned to a Microsoft Entra user or user group that can't access the printers because of permissions, Intune grants the assigned user or user group the permissions.

    If users don't have permissions, the following message is shown:

    `The selected groups may not have Universal Print permissions to selected printers. If this is the case, Intune will provide these groups with the correct permissions.`

    For more information on assigning profiles in Intune, go to [Assign user and device profiles](../assign-device-profile). For more information on user scope vs. device scope in the settings catalog, go to [Use the settings catalog to configure settings: Device scope vs. user scope settings](./#device-scope-vs-user-scope-settings).

    Select **Next**.
12. In **Review + create**, review your settings. When you select **Create**, your changes are saved, and the profile is assigned. The policy is also shown in the profiles list.

## Failures and reporting

After you assign the profile, you can monitor its status. The Intune reports show if a profile is successfully applied, failed, has conflicts, and more. For more specific information, see [Monitor device configuration profiles in Microsoft Intune](../monitor-device-profile).

For information on the reporting data you can view, see [Intune reports](../../device-management/reports/overview).

### Common issues

- When you deploy the printer policy, you might get a `Error 0x8007007f (ERROR_PROC_NOT_FOUND)` message.

    The `ERROR_PROC_NOT_FOUND` error is common, and is typically associated with missing `DelayLoaded` DLLs or missing APIs.

    To resolve this error, make sure your Windows OS client version is supported. The supported versions are listed at the top of this article.
- If you remove a printer from the Universal Print service, unshare it, or remove permissions, the Intune policy fails to install the printer.
- Make sure the printer is discoverable on the device. If users can't discover or install the printer manually, the Intune policy also fails to install the printer.
- Make sure you enter the **SharedID** and **PrinterID** correctly in the Intune policy.

    In some cases, the PrinterID and SharedID are reversed, which prevents the printer from being discovered. For more information on these settings, see Create the policy (in this article).
- The Application event log can show errors related to Universal Print.

### Enable tracing for Universal Print issues

If the common issues (in this article) don't resolve your issue, you can use TSS (Troubleshooting Script for Support) together with `UPPrinterInstaller.exe` to capture client-side traces for the Intune installation of the Universal Print printer. You can review these logs for possible issues. You can also work with the Intune support team to review and analyze these logs.

For more information and specific steps, see [Universal Print troubleshooting guide - Use TSS and UPPrinterInstaller](/en-us/universal-print/fundamentals/universal-print-troubleshooting-support-howto#use-tss-and-upprinterinstaller).