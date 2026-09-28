---
layout: Conceptual
title: Technical preview 2002.2 - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/2020/technical-preview-2002-2
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: configuration-manager
manager: laurawi
feedback_product_url: https://feedbackportal.microsoft.com/feedback/forum/4669adfc-ee1b-ec11-b6e7-0022481f8472
author: sccmavenger
ms.author: dannygu
ms.reviewer:
- umaikhan
- brianhun
- payur
- hugowu
- qiani
description: Learn about new features available in the Configuration Manager technical preview branch version 2002.2.
ms.date: 2020-02-28T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: whats-new
ROBOTS: NOINDEX
ms.collection: tier3
locale: en-us
document_id: 3c068804-a311-f56c-3878-57f72b823715
document_version_independent_id: 0b452ad0-3bd6-951f-d42c-5ffeb55aee9c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/get-started/2020/technical-preview-2002-2.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/get-started/2020/technical-preview-2002-2
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/get-started/2020/technical-preview-2002-2.md
platformId: 7da3b2b9-d380-80b9-949f-5e69f3946790
---

# Technical preview 2002.2 - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (technical preview branch)*

This article introduces the features that are available in the technical preview for Configuration Manager, version 2002.2. Install this version to update and add new features to your technical preview site.

Review the [technical preview](../technical-preview) article before installing this update. That article familiarizes you with the general requirements and limitations for using a technical preview, how to update between versions, and how to provide feedback.

The following sections describe the new features to try out in this version:

## Microsoft Intune tenant attach: Device sync and device actions

Microsoft Intune family of products is an integrated solution for managing all of your devices. Microsoft brings together Configuration Manager and Intune into a single console called **Microsoft Intune admin center**. Starting in this release you can upload your Configuration Manager devices to the cloud service and take actions from the **Devices** blade in the admin center.

### Prerequisites

- An account that is a [Microsoft Entra Global Administrator](/en-us/entra/identity/role-based-access-control/permissions-reference#global-administrator) for signing in when applying this change.

    - Onboarding creates a third-party app and a first party service principal in your Microsoft Entra tenant.

    Important

    The [Microsoft Entra Global Administrator](/en-us/entra/identity/role-based-access-control/privileged-roles-permissions) role is a highly privileged role and should only be used when another role can't be used. This feature requires the Global Administrator role. For other features, Microsoft recommends using roles with the fewest permissions. To learn more, see [Fundamentals of role-based administration for Configuration Manager](../../understand/fundamentals-of-role-based-administration).
- An Azure public cloud environment.
- The user account triggering device actions has the following prerequisites:

    - Has been discovered with [Microsoft Entra user discovery](../../servers/deploy/configure/about-discovery-methods#azureaddisc)
    - Has been discovered with [Active Directory user discovery](../../servers/deploy/configure/about-discovery-methods#bkmk_aboutUser)
    - The **Notify Resource** permission under **Collections** object class in Configuration Manager.
- Enable this [pre-release feature](../../servers/manage/pre-release-features) from **Administration** &gt; **Overview** &gt; **Updates and Servicing** &gt; **Features**.

### Internet endpoints

- `https://aka.ms/configmgrgateway`
- `https://*.manage.microsoft.com`

### Log files

Use the following logs, located on the service connection point:

- **CMGatewaySyncUploadWorker.log**
- **CMGatewayNotificationWorker.log**

### Known issues

After onboarding, a restart of the SMS\_EXECUTIVE service is needed. The service restart is a one time action and only for this technical preview.

### Try it out!

Try to complete the tasks. Then send [Feedback](../../understand/product-feedback) with your thoughts on the feature.

#### Enable device upload

- If you have co-management enabled currently, Edit co-management properties to enable device upload.
- If you don't have co-management enabled, Use the **Configure co-management** wizardto enable device upload.
    - You can upload your devices without enabling automatic enrollment for co-management or switching workloads to Intune.
- All Devices managed by Configuration Manager that have **Yes** in the **Client** column will be uploaded. If needed, you can limit upload to a single device collection.

##### Edit co-management properties to enable device upload

If you have co-management enabled currently, edit co-management properties to enable device upload using the instructions below:

1. In the Configuration Manager admin console, go to **Administration** &gt; **Overview** &gt; **Cloud Services** &gt; **Co-management**.
2. Right-click your co-management settings and select **Properties**.
3. In the **Configure upload** tab, select **Upload to Microsoft Endpoint Manager admin center**. Click **Apply**.

    - The default setting for device upload is **All my devices managed by Microsoft Endpoint Configuration Manager**. If needed, you can limit upload to a single device collection.

    [![Co-management configure upload](media/3555758-configure-upload.png)](media/3555758-configure-upload.png#lightbox)
4. Sign in with your *Global Administrator* account when prompted.
5. Click **Yes** to accept the **Create Microsoft Entra Application** notification. This action provisions a service principal and creates a Microsoft Entra application registration to facilitate the sync.
6. Click **OK** to exit the co-management properties once you've done making changes.

##### Use the Configure co-management wizard to enable device upload

If you don't have co-management enabled, use the **Configure co-management** wizard to enable device upload. You can upload your devices without enabling automatic enrollment for co-management or switching workloads to Intune. Enable device upload using the instructions below:

1. In the Configuration Manager admin console, go to **Administration** &gt; **Overview** &gt; **Cloud Services** &gt; **Co-management**.
2. In the ribbon, click **Configure co-management** to open the wizard.
3. On the **Tenant onboarding** page, select **AzurePublicCloud** for your environment. Azure Government cloud isn't supported.
4. Click **Sign In**. Use your *Global Administrator* account to sign in.
5. Ensure the **Upload to Microsoft Endpoint Manager admin center** option is selected on the **Tenant onboarding** page.

    - Make sure the option **Enable automatic client enrollment for co-management** isn't checked if you don't want to enable co-management now. If you do want to enable co-management, select the option.
    - If you enable co-management along with device upload, you'll be given additional pages in the wizard to complete. For more information, see [Enable co-management](../../../comanage/how-to-enable).

    [![Co-management Configuration Wizard](media/3555758-comanagement-wizard.png)](media/3555758-comanagement-wizard.png#lightbox)
6. Click **Next** and then **Yes** to accept the **Create Microsoft Entra Application** notification. This action provisions a service principal and creates a Microsoft Entra application registration to facilitate the sync.
7. On the **Configure upload** page, select the recommended device upload setting for **All my devices managed by Microsoft Endpoint Configuration Manager**. If needed, you can limit upload to a single device collection.
8. Click **Summary** to review your selection, then click **Next**.
9. When the wizard is complete, click **Close**.

#### Review your upload and perform device actions

##### Review logs

1. Open **CMGatewaySyncUploadWorker.log** from &lt;ConfigMgr install directory&gt;\Logs.
2. The next sync time is noted by log entries similar to `Next run time will be at approximately: 02/28/2020 16:35:31`.
3. For device uploads, look for log entries similar to `Batching N records`. **N** is the number of devices uploaded to the cloud.
4. The upload occurs every 15 minutes for changes. Once changes are uploaded, it may take an additional 5 to 10 minutes for client changes to appear in **Microsoft Intune admin center**.

##### Perform device actions

1. In a browser, navigate to `https://intune.microsoft.com`.
2. Select **Devices** then **All devices** to see the uploaded devices. You'll see **ConfigMgr** in the **Managed by** column for uploaded devices. [![All devices in Microsoft Intune admin center](media/3555758-all-devices.png)](media/3555758-all-devices.png#lightbox)
3. Click on a device to load its **Overview** page.
4. Click on any of the following actions:

    - **Sync Machine Policy**
    - **Sync User Policy**
    - **App Evaluation Cycle**

    [![Device overview in Microsoft Intune admin center](media/3555758-device-overview-actions.png)](media/3555758-device-overview-actions.png#lightbox)

## Management insight rules for proper HTTPS configuration

This release includes other [management insight](../../servers/manage/management-insights) rules to help you configure your site for adding secure HTTPS communication:

- **Sites that don't have proper HTTPS configuration**: This rule lists sites in your hierarchy that aren't properly configured for HTTPS. This configuration prevents the site from [synchronizing collection membership results to Microsoft Entra groups](../../clients/manage/collections/create-collections#bkmk_aadcollsync). It may cause Azure AD Sync to not upload all devices. Management of these clients may not function properly.
- **Devices not uploaded to Microsoft Entra ID**: This rule lists devices that aren't uploaded to Microsoft Entra ID because the site isn't properly configured for HTTPS.

For either rule, configure [Enhanced HTTP](../../plan-design/hierarchy/enhanced-http), or enable at least one management point for HTTPS. These rules won't appear if you have previously configured the site for HTTPS communication.

## Improvements to BitLocker management

In [Configuration Manager current branch version 1910](../../../protect/plan-design/bitlocker-management#prerequisites), to integrate the BitLocker recovery service you had to HTTPS-enable a management point. The HTTPS connection is necessary to encrypt the recovery keys across the network from the Configuration Manager client to the management point. Configuring the management point and all clients for HTTPS can be challenging for many customers.

Starting in this version, the HTTPS requirement is for the IIS website that hosts the recovery service, not the entire management point role. This change relaxes the certificate requirements, and still encrypts the recovery keys in transit.

Now the **Client connections** property of the management point can be **HTTP** or **HTTPS**. If the management point is configured for **HTTP**, to support the BitLocker recovery service:

1. Acquire a server authentication certificate. Bind the certificate to the IIS website on the management point that hosts the BitLocker recovery service.
2. Configure clients to trust the server authentication certificate. There are two methods to accomplish this trust:

    - Use a certificate from a public and globally trusted certificate provider. Windows clients include trusted root certificate authorities (CAs) from these providers. By using a server authentication certificate that's issued by one of these providers, your clients should automatically trust it.
    - Use a certificate issued by a CA from your organization's public key infrastructure (PKI). Most PKI implementations add the trusted root CAs to Windows clients. For example, using Active Directory Certificate Services with group policy. If you issue the server authentication certificate from a CA that your clients don't automatically trust, add the CA trusted root certificate to clients.

Tip

The only clients that need to communicate with the recovery service are those clients that you plan to target with a BitLocker management policy and includes a **Client Management** rule .

On the client, use the **BitLockerManagementHandler.log** to troubleshoot this connection. For connectivity to the recovery service, the log shows the URL that the client is using. Locate an entry that starts with `Checking for Recovery Service at`.

## Improvements to support for ARM64 devices

This release improves upon the support for devices with the ARM64 processor. The **All Windows 10 (ARM64)** platform is now available in the list of supported OS versions on the following objects:

- Configuration item supported platforms
- Application deployment type requirements
- Package program requirements
- Task sequence advanced properties

Note

If you previously selected the top-level **Windows 10** platform, this action automatically selected both **All Windows 10 (64-bit)** and **All Windows 10 (32-bit)**. This new platform isn't automatically selected. If you want to add **All Windows 10 (ARM64)**, manually select it in the list.

For more information on Configuration Manager's support for ARM64 devices, see [Windows 10 on ARM64](../../plan-design/configs/support-for-windows-10#bkmk_arm64).

## Search all subfolders for configuration items and configuration baselines

Similar to improvements in previous releases, you can now use the **All Subfolders** search option from the **Configuration Items** and **Configuration Baselines** nodes.

![Screenshot of Configuration Manager console, Configuration Items node, Search tab](media/5891241-ci-node-search-all-subfolders.png)

## Support for 64-bit macOS Catalina

Configuration Manager now supports the 64-bit macOS Catalina version 10.15. For more information, see [Supported OS versions for clients and devices](../../plan-design/configs/supported-operating-systems-for-clients-and-devices#mac-computers).

You can also use Microsoft Intune to manage macOS devices. For more information, see [Deployment guide: Manage macOS devices in Microsoft Intune](../../../../fundamentals/platform-guide-macos).

## Improvements to extend and migrate on-premises site to Microsoft Azure

[Extend and migrate on-premises site to Microsoft Azure](../../support/azure-migration-tool) now supports provisioning multiple site system roles on a single Azure virtual machine. You can add site system roles after the initial Azure virtual machine deployment has completed. To add a new role to an existing virtual machine, do the following steps:

1. On the **Deployments in Azure** tab, click on a virtual machine deployment that has a **Completed** status.
2. Click the **Create new** button to add an additional role to the virtual machine.

## Microsoft Configuration Manager cloud features

When new cloud-based features are available in the Microsoft Intune admin center, or other attached cloud services for your on-premises Configuration Manager installation, you can now opt in to these new features in the Configuration Manager console. For more information on enabling features in the Configuration Manager console, see [Enable optional features from updates](../../servers/manage/optional-features).