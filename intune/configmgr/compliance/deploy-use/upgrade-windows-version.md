---
layout: Conceptual
title: Upgrade Windows devices to a different version - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/compliance/deploy-use/upgrade-windows-version
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
description: Use Configuration Manager to automatically upgrade Windows 11 and Windows 10 devices to a different Windows edition.
ms.date: 2023-09-15T00:00:00.0000000Z
ms.subservice: compliance
ms.topic: upgrade-and-migration-article
ms.collection: tier3
locale: en-us
document_id: 1e835f3b-3591-b242-c7c3-2383a1702ded
document_version_independent_id: 28b0c836-b4b4-5fe5-1507-7702615c61f9
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/compliance/deploy-use/upgrade-windows-version.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/compliance/deploy-use/upgrade-windows-version
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/compliance/deploy-use/upgrade-windows-version.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/19ec6774-09b8-473e-a17e-b17b518bbad7
- https://authoring-docs-microsoft.poolparty.biz/devrel/e0ffb20c-01c6-407b-a9bd-29111652a1dc
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ade36b61-c646-4bd8-87ee-f3a843461962
- https://authoring-docs-microsoft.poolparty.biz/devrel/3904bce4-d817-48cf-85fd-b6146fca83b7
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 768668bc-a356-ef38-cce7-f9a889a6e992
---

# Upgrade Windows devices to a different version - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

The **Edition Upgrade Policy** lets you automatically upgrade Windows 11 and Windows 10 devices to a different edition.

The following upgrade paths are supported:

- From Windows 11 Pro to Windows 11 Enterprise
- From Windows 11 Home to Windows 11 Education
- From Windows 11 Pro N to Windows 11 Enterprise N
- From Windows 11 Home N to Windows 11 Education N
- From Windows 10 Pro to Windows 10 Enterprise
- From Windows 10 Home to Windows 10 Education
- From Windows 10 Mobile to Windows 10 Mobile Enterprise

The devices must run the Configuration Manager client software. Devices managed by [on-premises MDM](../../mdm/understand/manage-mobile-devices-with-on-premises-infrastructure) aren't supported.

## Before you start

Before you begin to upgrade devices to the latest version, review the following prerequisites:

- For desktop editions of Windows 11 and Windows 10: A valid product key for the new version of Windows on all devices you target with the policy. This product key can be a multiple activation key (MAK), or a generic volume licensing key (GVLK). A GVLK is also referred to as a key management service (KMS) client setup key. For more information, see [Plan for volume activation](/en-us/windows/deployment/volume-activation/plan-for-volume-activation-client). For a list of KMS client setup keys, see [Appendix A](/en-us/windows-server/get-started/kmsclientkeys) of the Windows Server activation guide.
- For Windows 10 Mobile: An XML license file from the Microsoft Volume Licensing Service Center (VLSC). This file contains the licensing information for the new version of Windows on all devices you target with the policy. Download the ISO file for **Windows 10 Mobile Enterprise**, which includes the licensing XML.
- To manage this policy type, you must be in the Configuration Manager **Full Administrator** security role.

## Configure the policy

1. In the Configuration Manager console, go to the **Assets and Compliance** workspace, expand **Compliance Settings**, and select the **Windows Edition Upgrade** node.
2. On the **Home** tab of the ribbon, in the **Create** group, select **Create Edition Upgrade Policy**.
3. Select **Create Policy**.
4. On the **General** page of the **Create Edition Upgrade Policy Wizard**, specify the following information:

    - **Name** - Enter a name for the edition upgrade policy
    - **Description** (optional) - Optionally, enter a description for the policy that helps you identify it in the Configuration Manager console
    - **SKU to upgrade device to** - From the drop-down list, select the target edition of Windows 11 and Windows 10 desktop or Windows 10 Mobile
    - **License information** - Select one of the following options:

        - **Product Key** - Enter a valid product key for the target Windows 11 & 10 desktop edition

            Note

            After you create a policy containing a product key, you can't edit the product key later. Configuration Manager obscures the key for security reasons. To change the product key, re-enter the entire key.
        - **License File** - Select **Browse** to choose a valid license file in XML format. Configuration Manager uses this license file to upgrade Windows 10 Mobile devices.
5. Complete the wizard.

## Deploy the policy

1. In the Configuration Manager console, go to the **Assets and Compliance** workspace, expand **Compliance Settings**, and select the **Windows Edition Upgrade** node.
2. Select the Windows edition upgrade policy you want to deploy. On the **Home** tab of the ribbon, in the **Deployment** group, select **Deploy**.
3. Choose the device collection to which you want to deploy the policy.
4. Select the schedule by which the client evaluates the policy.
5. Complete the wizard.