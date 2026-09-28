---
layout: Conceptual
title: Support Center quickstart - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/support/support-center-quickstart
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
description: Quickly capture the state of a Configuration Manager client for troubleshooting.
ms.date: 2021-04-05T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: quickstart
ms.collection: tier3
locale: en-us
document_id: 31c3a60a-6d15-184f-da3d-d796ec8b4760
document_version_independent_id: 05f6e0fb-4366-0734-9959-50473af28b9a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/support/support-center-quickstart.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/support/support-center-quickstart
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/support/support-center-quickstart.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/c7ddd0ba-08b8-4055-8ab8-0da61f3dfbb3
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/2624a017-7337-44fa-9494-a407bb0e59fa
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/5cf7e60a-ca26-4c6f-befd-5e90eae977f5
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/a438284e-c3c3-4c36-ab0b-aa7c244b912c
platformId: 4b786149-5c7b-8672-2de7-de31bb96d124
---

# Support Center quickstart - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Support Center has powerful capabilities including troubleshooting and real-time log viewing. It can also be used in just a few minutes to capture the state of a Configuration Manager client computer. This ability includes accessing remote clients.

Create a complete *troubleshooting bundle* file (.zip) that captures the client state. The bundle doesn't only contain log files. It can include other types of data such as registry settings and client configurations. Provide the bundle to a support technician who uses Support Center Viewer.

## Prerequisites

- Local administrative rights to a Configuration Manager client
- The Support Center installer. This file is on the site server at `cd.latest\SMSSETUP\Tools\SupportCenter\SupportCenterInstaller.msi`. For more information, see [Support Center - Install](support-center#install).

## Step 1: Create a data bundle on a local client

1. Install Support Center on the Configuration Manager client.
2. Go to the **Start** menu, in the **Microsoft Endpoint Manager** group, select the option based on your site version:

    - For version 2103 and later: Select **Support Center Client Data Collector**.
    - For version 2010 and earlier: Select **Support Center**.
3. On the Home tab of the ribbon, select **Collect selected data**.

    By default, Support Center only collects the minimum data set:

    - **Client log files**: All log files from the Configuration Manager clients, by default in `C:\Windows\CCM\logs`. It also includes log files for client setup, by default in `C:\Windows\ccmsetup\Logs`.
    - **Client configuration**: Information from the Configuration Manager client. For example, the version, the assigned site and management point, and if it's internet facing. This option is always enabled.
    - **Operating system**: Information about the computer. For example, Windows install, network adapters, and system services. This option is always enabled.

    ![Collect selected data option in Support Center Client Data Collector](media/support-center-client-data-collector.png)
4. Save the troubleshooting bundle file (.zip) to a folder on the computer. By default, the file name is similar to the following example: `Support_c885cdfed3c7482bba4f9e662978ec07.zip`.

## Step 2: View the data bundle using Support Center Viewer

1. Start **Support Center Viewer**. This action can happen on any computer with Support Center.
2. Select **Open bundle**, browse to the bundle file, and select **Open**.

    ![Support Center Viewer with an open bundle](media/support-center-viewer.png)
3. After Support Center Viewer processes the file, switch to each available tab. View the types of data that Support Center collects by default:

    - **Configuration** tab

        - Configuration Manager client configuration
        - Operating system
        - Computer
        - Services
        - Network adapters
    - **Logs** tab: Choose one or more entries in the list, and select **Open**. This action opens the selected log files in Log Viewer. Use this feature to look up error codes, and use advanced filters to help you more quickly analyze log files.

## Collect more data

Beyond these basic capabilities, Support Center can also collect a wide variety of other client state information. Open **Support Center Client Data Collector** and select **Collect all data**. This process typically lasts several minutes, even on newer computers. Support Center collects the following data:

![Collect all data option in Support Center Client Data Collector](media/support-center-client-data-collector-all-data.png)

- **Policy**: Configuration Manager policy settings, including both the requested policy configuration and the actual policy configuration.
- **Client WMI**: Client configuration information from WMI. Support Center doesn't collect client policy.
- **Certificates**: Public key information for client certificates. Support Center doesn't collect certificate private keys.
- **Debug dumps**: Collect a debug dump of client and related processes. Debug dumps can be large. Only enable this option when troubleshooting issues with client performance.

    Warning

    Collecting debug dumps will cause data bundles to become very large. In some cases, the size can be several hundred MB.

    Debug dumps may contain sensitive information, including passwords, cryptographic secrets, or user data. Only collect debug dumps on the recommendation of Microsoft Support personnel. Carefully handle data bundles that contain debug dumps to protect them from unauthorized access.

    This data type isn't supported when you make a remote connection to another client.
- **Client registry**: Collects client configuration information from the registry. Support Center only collects Configuration Manager registry information.
- **Troubleshooting**: Real-time troubleshooting data to help diagnose common client problems with Active Directory, management points, networking, policy assignments, and registration.

    Note

    This data type isn't supported when you make a remote connection to another client.
- **Windows Update log files**: Collects log files for Windows Updates, which are necessary when troubleshooting issues with software updates.