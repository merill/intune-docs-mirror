---
layout: Conceptual
title: Deploy resource access profiles - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/protect/deploy-use/deploy-wifi-vpn-email-cert-profiles
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
description: Learn how to deploy Wi-Fi, VPN, and certificate profiles in Configuration Manager.
ms.date: 2022-03-29T00:00:00.0000000Z
ms.subservice: protect
ms.topic: install-set-up-deploy
ms.collection: tier3
locale: en-us
document_id: e2c35a72-03ec-76af-55db-85cb919b6b61
document_version_independent_id: 34681260-7a0e-33ee-acbc-f7f9b6113605
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/protect/deploy-use/deploy-wifi-vpn-email-cert-profiles.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/protect/deploy-use/deploy-wifi-vpn-email-cert-profiles
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/protect/deploy-use/deploy-wifi-vpn-email-cert-profiles.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/2bb407c5-c939-4f7a-9174-27da19279675
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/6eda2a8b-e231-4335-b766-c055ea6025a6
platformId: 0c0bf0c2-c5c3-1759-7974-f58e22abba89
---

# Deploy resource access profiles - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Important

Starting in version 2203, this company resource access feature is no longer supported. For more information, see [Frequently asked questions about resource access deprecation](../plan-design/resource-access-deprecation-faq).

After you create one of the following resource access profiles, deploy it to one or more collections:

- [Wi-Fi](create-wifi-profiles)
- [VPN](create-vpn-profiles)
- [Certificate](create-certificate-profiles)

When you deploy these profiles, you specify the target collection, and specify how often the client evaluates the profile for compliance.

## Deploy a profile

1. In the Configuration Manager console, go to the **Assets and Compliance** workspace. Expand **Compliance Settings**, expand **Company Resource Access**, and then choose the appropriate profile node. For example, **Wi-Fi Profiles**.
2. In the list of profiles, select the profile that you want to deploy. Then in the **Home** tab of the ribbon, in the **Deployment** group, select **Deploy**.
3. In the deploy profile window, specify the following information:

    - **Collection**: Select the collection where you want to deploy the profile.
    - **Generate an alert**: Enable this option to configure an alert. The site generates this alert if the profile compliance is less than the specified percentage by the specified date and time. You can also select whether you want an alert to be sent to System Center Operations Manager.
    - **Random delay (hours)**: For certificate profiles that contain Simple Certificate Enrollment Protocol (SCEP) settings, specify a delay window to avoid excessive processing on the Network Device Enrollment Service (NDES). The default value is `64` hours.
    - **Specify the compliance evaluation schedule for this...profile**: Specify how often the client evaluates compliance for this profile. Select a **Simple schedule** or configure a **Custom schedule**. By default, the simple schedule is every `12` hours.
4. Select **OK** to close the window and create the deployment.

## Delete a deployment

If you want to delete a deployment, select it from the list. In the details pane, switch to the **Deployments** tab. Select the deployment, and then in the **Deployment** tab of the ribbon, select **Delete**.

Important

When you remove a VPN profile deployment, Configuration Manager doesn't remove the VPN profile from Windows. If you want to remove the profile from devices, manually remove it.