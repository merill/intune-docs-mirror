---
layout: Conceptual
title: Tenant attach - Onboard Configuration Manager clients to Microsoft Defender for Endpoint from the Microsoft Intune admin center - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/atp-onboard
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
description: Deploy Microsoft Defender for Endpoint Detection and Response (EDR) onboarding policies to Configuration Manager managed clients from the admin center.
ms.date: 2026-05-13T00:00:00.0000000Z
ms.topic: how-to
ai-usage: ai-assisted
ms.subservice: core-infra
ms.collection: tier3
locale: en-us
document_id: 44b3d306-a0f7-f980-7f45-73ac7d9e5e18
document_version_independent_id: 691bf0ea-5c5a-54c8-22e0-051990050153
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/tenant-attach/atp-onboard.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/tenant-attach/atp-onboard
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/tenant-attach/atp-onboard.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/8b9ae643-2e85-42b8-beb2-eef4bae8c4bc
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/e047e27d-b5f3-43a8-b4b0-4f6dca95e7c9
platformId: 7e874c3f-ec52-f845-f519-51a30016acc4
---

# Tenant attach - Onboard Configuration Manager clients to Microsoft Defender for Endpoint from the Microsoft Intune admin center - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

The Microsoft Intune family of products is an integrated solution for managing all of your devices. Microsoft brings together Configuration Manager and Intune into a single console called **Intune admin center**. You can deploy Defender for Endpoint onboarding policies to Configuration Manager managed clients. These clients don't require Microsoft Entra ID or MDM enrollment, and the policy is targeted at Configuration Manager collections rather than Microsoft Entra groups.

## Prerequisites

- Access to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
- An environment that's [tenant attached with uploaded devices](device-sync-actions).
- A supported version of Configuration Manager and the corresponding version of the console installed.
    - Upgrade the target devices to the latest version of the Configuration Manager client.
- At least one Configuration Manager collection that's [available for assigning Endpoint security policies](endpoint-security-get-started#bkmk_collections)
- Windows Devices that [support this profile for tenant attached devices](endpoint-security-get-started#bkmk_supportedprofiles)

- [Microsoft Intune and Microsoft Defender for Endpoint integration enabled](../../device-security/microsoft-defender/configure-integration#connect-defender-for-endpoint-to-intune)
- Client which meets the [minimum requirements for Microsoft Defender for Endpoint](/en-us/defender-endpoint/minimum-requirements#licensing-requirements) and is onboarded.

## Create Defender for Endpoint policies

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Endpoint security** &gt; **Endpoint detection and response** &gt; **Create Policy**.
3. Select the following platform and profile for your policy:

    - Platform: **Windows 10, Windows 11, and Windows Server (ConfigMgr)**
    - Profile: **Endpoint detection and response (ConfigMgr)**
4. Select **Create**.
5. On the **Basics** page, enter a name and description for the profile, and then choose **Next**.
6. On the **Configuration settings** page, configure the settings you want to manage with this profile. The onboarding package is automatically included and isn't something you can configure.

    When you're done configuring settings, select **Next**.
7. On the **Assignments** page, select the collections that receive this policy. Select collections from Configuration Manager that you synced to Intune admin center and enabled for Defender for Endpoint policy.

    You can choose not to assign collections at this time, and later edit the policy to add an assignment.

    When ready to continue, select **Next**.
8. On the **Review + create** page, when you're done, choose **Create**.

    The new profile is displayed in the list when you select the policy type for the profile you created.

## Device Status

You can review the status of endpoint security policies for tenant attached devices. The **Device Status** page can be accessed for all endpoint security policy types for tenant-attached clients. To display the **Device Status** page:

1. Select a policy that's targeted to **ConfigMgr** devices to display the **Overview** page for the policy.
2. Select **Device Status** to display a list of devices targeted by the policy.
3. The **Device Name**, **Compliance State**, and **SMS ID** are displayed for each of the devices on the **Device Status** page.