---
layout: Conceptual
title: Tenant attach - Deploy endpoint firewall from the Microsoft Intune admin center - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/deploy-firewall-policy
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
description: Create and deploy firewall policies from the Microsoft Intune admin center and for Configuration Manager collections.
ms.date: 2021-09-27T00:00:00.0000000Z
ms.topic: install-set-up-deploy
ms.subservice: core-infra
ms.collection: tier3
locale: en-us
document_id: bc9a9935-a686-2627-3f88-55248d5869e8
document_version_independent_id: 030de40f-1ffe-96d5-3a2d-a7b3379ebe16
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/tenant-attach/deploy-firewall-policy.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/tenant-attach/deploy-firewall-policy
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/tenant-attach/deploy-firewall-policy.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 1c962afb-a82f-0c3d-2cb1-d0fda6f7515a
---

# Tenant attach - Deploy endpoint firewall from the Microsoft Intune admin center - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Create Windows Firewall policies in the Microsoft Intune admin center and deploy them to Configuration Manager collections.

## Prerequisites

- Access to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
- An environment that's [tenant attached with uploaded devices](device-sync-actions).
- A supported version of Configuration Manager and the corresponding version of the console installed.
    - Upgrade the target devices to the latest version of the Configuration Manager client.
- At least one Configuration Manager collection that's [available for assigning Endpoint security policies](endpoint-security-get-started#bkmk_collections)
- Windows Devices that [support this profile for tenant attached devices](endpoint-security-get-started#bkmk_supportedprofiles)

## Assign firewall policies to a collection

1. Go to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Endpoint security** &gt; **Firewall** then **Create Policy**.
3. Create a profile with the following settings:

    - **Platform**: Windows 10 and later
        - Only Windows 10 clients can be targeted with firewall policies currently.
    - **Profile**: Microsoft Defender Firewall (ConfigMgr)
4. Select **Create** then give the profile a **Name** and a **Description**.
5. On the **Configuration settings** page, set the firewall settings for the devices. For more information about the available settings, see [Settings for firewall policy for tenant attached devices](../../device-configuration/endpoint-security/ref-firewall-settings-tenant-attach?toc=/mem/configmgr/tenant-attach/toc.json&amp;bc=/mem/configmgr/tenant-attach/breadcrumb/toc.json)
6. On the **Assignments** page, select the collections to include for the policy assignment then choose **Next**.
7. Review the settings on the **Review + Create** page and select **Create** when you're done.

## Device Status

You can review the status of endpoint security policies for tenant attached devices. The **Device Status** page can be accessed for all endpoint security policy types for tenant-attached clients. To display the **Device Status** page:

1. Select a policy that's targeted to **ConfigMgr** devices to display the **Overview** page for the policy.
2. Select **Device Status** to display a list of devices targeted by the policy.
3. The **Device Name**, **Compliance State**, and **SMS ID** are displayed for each of the devices on the **Device Status** page.