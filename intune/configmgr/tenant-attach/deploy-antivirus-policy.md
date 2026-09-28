---
layout: Conceptual
title: Tenant attach - Create and deploy Antivirus policies from the admin center - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/deploy-antivirus-policy
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
description: Create and deploy Antivirus policies from the Microsoft Intune admin center and for Configuration Manager collections.
ms.date: 2023-03-28T00:00:00.0000000Z
ms.topic: install-set-up-deploy
ms.subservice: core-infra
ms.collection: tier3
ms.custom: sfi-image-nochange
locale: en-us
document_id: f910bbc4-4987-7f08-f57e-7e9b4ac323fd
document_version_independent_id: 31c34fdc-55b1-6286-944b-2030f8f84398
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/tenant-attach/deploy-antivirus-policy.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/tenant-attach/deploy-antivirus-policy
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/tenant-attach/deploy-antivirus-policy.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c671beaa-a830-4c9f-aceb-97379ee031ca
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/8921374c-4dbe-4ed0-b011-a39e18bfbd98
platformId: 0c0ac548-6ed9-4bd1-7691-050b658c9d54
---

# Tenant attach - Create and deploy Antivirus policies from the admin center - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Create Microsoft Defender antivirus policies in the Microsoft Intune admin center and deploy them to Configuration Manager collections.

## Prerequisites

- Access to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
- An environment that's [tenant attached with uploaded devices](device-sync-actions).
- A supported version of Configuration Manager and the corresponding version of the console installed.
    - Upgrade the target devices to the latest version of the Configuration Manager client.
- At least one Configuration Manager collection that's [available for assigning Endpoint security policies](endpoint-security-get-started#bkmk_collections)
- Windows Devices that [support this profile for tenant attached devices](endpoint-security-get-started#bkmk_supportedprofiles)

## Assign Microsoft Defender Antivirus policy to a collection

1. In a browser, go to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Endpoint security** then **Antivirus**.
3. Select **Create Policy**.
4. For the **Platform**, select **Windows 10, Windows 11, and Windows Server (ConfigMgr)**.
5. For the **Profile**, select **Microsoft Defender Antivirus** then **Create**.
6. Assign a **Name** and optionally a **Description** on the **Basics** page.
7. On the **Configuration settings** page, configure the settings you want to manage with this profile. When your done configuring settings, select **Next**. For more information about available policies, see [Antivirus policy settings for tenant attached devices](../../device-configuration/endpoint-security/ref-antivirus-defender-settings-windows-tenant-attach?toc=/mem/configmgr/tenant-attach/toc.json&amp;bc=/mem/configmgr/tenant-attach/breadcrumb/toc.json).
8. Assign the policy to a Configuration Manager collection on the **Assignments** page.

## Assign Windows Security experience policy to a collection

1. In a browser, go to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Endpoint security** then **Antivirus**.
3. Select **Create Policy**.
4. For the **Platform**, select **Windows 10, Windows 11, and Windows Server (ConfigMgr)**.
5. For the **Profile**, select **Windows Security experience** then **Create**.
6. Assign a **Name** and optionally a **Description** on the **Basics** page.
7. On the **Configuration settings** page, configure the settings you want to manage with this profile. When your done configuring settings, select **Next**. For more information about the available settings, see [Settings for Windows Security experience Antivirus policy for tenant attached devices](../../device-configuration/endpoint-security/ref-windows-security-settings-tenant-attach?toc=/mem/configmgr/tenant-attach/toc.json&amp;bc=/mem/configmgr/tenant-attach/breadcrumb/toc.json).
8. Assign the policy to a Configuration Manager collection on the **Assignments** page.

## Antivirus policy exclusions merge

*(Introduced in Configuration Manager 2103)*

Starting in Configuration Manager 2103, When a tenant attached device is targeted with two or more antivirus policies, the settings for antivirus exclusions will merge before being applied to the client. This change results in the client receiving the exclusions defined in each policy, allowing for more granular control of antivirus exclusions. For earlier versions of Configuration Manager, Antivirus exclusions from a single policy are applied. With this behavior, the last policy applied determines the effective exclusions. 

To use this functionality, create an antivirus policy from the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) that includes some [antivirus exclusions](../../device-configuration/endpoint-security/ref-antivirus-defender-settings-windows-tenant-attach?toc=/mem/configmgr/tenant-attach/toc.json&amp;bc=/mem/configmgr/tenant-attach/breadcrumb/toc.json#microsoft-defender-antivirus-exclusions). Create a second antivirus policy including only antivirus exclusions that are different from the first policy. Apply both antivirus policies to the same collection. Antivirus exclusions from both policies are applied on clients in the targeted collection.

## Device Status

You can review the status of endpoint security policies for tenant attached devices. The **Device Status** page can be accessed for all endpoint security policy types for tenant-attached clients. To display the **Device Status** page:

1. Select a policy that's targeted to **ConfigMgr** devices to display the **Overview** page for the policy.
2. Select **Device Status** to display a list of devices targeted by the policy.
3. The **Device Name**, **Compliance State**, and **SMS ID** are displayed for each of the devices on the **Device Status** page.

## Endpoint Security reports in Microsoft Intune admin center

Starting in Configuration Manager 2303 release, you can now see Tenant Attached devices data in Endpoint Security reports available in Microsoft Intune admin center.

If you are enabling cloud attach for first time, you can enable this feature in the [onboarding wizard](../cloud-attach/enable)

If you have enabled cloud attach currently, you need to use the cloud attach properties to enable data upload for Microsoft Defender for Endpoints reporting using the instructions below:

1. In the Configuration Manager admin console, go to **Administration** &gt; **Overview** &gt; **Cloud Services** &gt; **Cloud Attach**.
    - For version 2103 and earlier, select the **Co-management** node.
2. In the ribbon, select **Properties** for your co-management production policy.
3. In the **Configure upload** tab, select **Upload to Microsoft Endpoint Manager admin center**. Select **Apply**.
    - The default setting for device upload is **All my devices managed by Microsoft Endpoint Configuration Manager**. If needed, you can limit upload to a single device collection.
    - When a single collection is selected, its child collections are also uploaded.
4. Optionally, you can enable [Endpoint Analytics and Role-based Access Control](device-sync-actions#bkmk_edit)
5. In the **Configure upload** tab, select **Enable Uploading Microsoft Defender for Endpoint data for reporting on devices uploaded to Microsoft Intune admin center**. Select **Apply**. [![Screenshot of Cloud Attach properties tab showing option to upload Microsoft Defender for Endpoint data to Intune admin center.](media/9220597-data-upload-for-mde-reports.png)](media/9220597-data-upload-for-mde-reports.png#lightbox)

### Operational reports in Microsoft Intune admin center

1. In the Intune admin console, go to **Endpoint Security** &gt; **Antivirus**
2. Click on **Unhealthy endpoints**report where you can view the operational report for the thread agent status on devices and users to outline which are in a state that requires your attention.
    - Each record will tell you if malware protection, real-time protection and network protection are enabled or disabled.
    - You can view the state of the device and additional information found in the extra columns to help identify next steps for troubleshooting.
    - You can filter the devices based on management agent using the Managed By column and you can also export the report in csv format for further analysis. [![Screenshot of unhealthy endpoints operational report in Intune admin center.](media/9220597-ops-unhealthy-endpoints-report.png)](media/9220597-ops-unhealthy-endpoints-report.png#lightbox)
3. On the **Active malware** report, you can view the operational report to see the list of devices and users with detected malware with details of the malware category. This will show the malware, state of the device and counts of malware found on the device. [![Screenshot of active malware operational report in Intune admin center.](media/9220597-ops-active-malware-report.png)](media/9220597-ops-active-malware-report.png#lightbox)

### Organizational reports in Microsoft Intune admin center

1. In the Intune admin console, go to **Reports**, **Endpoint Security** &gt; **Microsoft Defender Antivirus**
2. Under the **Summary** section, you will see summary aggregates of Antivirus Agent Status [![Screenshot of Antivirus agent status Summary organizational report in Intune admin center.](media/9220597-org-summary-report.png)](media/9220597-org-summary-report.png#lightbox)
3. Click on **Reports** to access **Antivirus agent status** and **Detected malware** organizational reports.
4. The **Antivirus agent status** report shows the list of devices, users, and antivirus agent status information. [![Screenshot of Antivirus agent status organizational report in Intune admin center.](media/9220597-org-antivirus-agent-status-report.png)](media/9220597-org-antivirus-agent-status-report.png#lightbox)
5. The **Detected malware** report shows the list of devices and users with detected malware with details of the malware category. [![Screenshot of detected malware organizational report in Intune admin center.](media/9220597-org-detected-malware-report.png)](media/9220597-org-detected-malware-report.png#lightbox)

Both the reports can be filtered based on **Managed by** column and the data within these reports will remain in your console up to three days before requiring you to generate again.