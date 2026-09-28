---
layout: Conceptual
title: Tenant attach - Create and deploy Attack surface reduction policies from the admin center - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/deploy-asr-policy
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
description: Create and deploy Attack surface reduction policies from the Microsoft Intune admin center and for Configuration Manager collections.
ms.date: 2022-05-31T00:00:00.0000000Z
ms.topic: install-set-up-deploy
ms.subservice: core-infra
ms.collection: tier3
locale: en-us
document_id: f9e3b77e-e449-a9c3-2c6a-aaec8192d1e7
document_version_independent_id: 7db4d8f9-5200-e84d-ccd2-7e89247d1cf8
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/tenant-attach/deploy-asr-policy.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/tenant-attach/deploy-asr-policy
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/tenant-attach/deploy-asr-policy.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/062d60c9-ee0f-402e-a046-b4e67c3572d6
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/17d3b3f6-a66e-4c69-9774-14a73c38e669
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 8fa3c98e-2b0b-d562-edf2-3746d5a36c48
---

# Tenant attach - Create and deploy Attack surface reduction policies from the admin center - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Create Attack surface reduction policies in the Microsoft Intune admin center and deploy them to Configuration Manager collections.

## Prerequisites

- Access to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
- An environment that's [tenant attached with uploaded devices](device-sync-actions).
- A supported version of Configuration Manager and the corresponding version of the console installed.
    - Upgrade the target devices to the latest version of the Configuration Manager client.
- At least one Configuration Manager collection that's [available for assigning Endpoint security policies](endpoint-security-get-started#bkmk_collections)
- Windows Devices that [support this profile for tenant attached devices](endpoint-security-get-started#bkmk_supportedprofiles)

## Assign Attack surface reduction policy to a collection

1. In a browser, go to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Endpoint security** &gt; **Attack surface reduction** then **Create Policy**.
3. Create a profile with the following settings:

    - **Platform**: Windows 10 and later (ConfigMgr)
    - **Profile**: Choose one of the following profiles:
        - Attack Surface Reduction Rules (ConfigMgr)
        - Exploit Protection (ConfigMgr)
        - Web Protection (ConfigMgr)

Note

The Microsoft Edge installer, Attack Surface Reduction rules engine for tenant attach, and [CMPivot](../core/servers/manage/cmpivot) are currently signed with the **Microsoft Code Signing PCA 2011** certificate. If you set PowerShell execution policy to **AllSigned**, then you need to make sure that devices trust this signing certificate. You can export the certificate from a computer where you've installed the Configuration Manager console. View the certificate on `"C:\Program Files (x86)\Microsoft Endpoint Manager\AdminConsole\bin\CMPivot.exe"`, and then export the code signing certificate from the certification path. Then import it to the *machine*'s **Trusted Publishers** store on managed devices. You can use the process in the following blog, but make sure to export the *code signing certificate* from the certification path: [Adding a Certificate to Trusted Publishers using Intune](https://techcommunity.microsoft.com/t5/intune-customer-success/adding-a-certificate-to-trusted-publishers-using-intune/ba-p/1974488)

1. Assign a **Name** and optionally a **Description** on the **Basics** page.
2. On the **Configuration settings** page, configure the settings you want to manage with this profile. When your done configuring settings, select **Next**. For more information about available settings for both profiles, see [Attack surface reduction policy settings for tenant attached devices](../../device-configuration/endpoint-security/ref-attack-surface-reduction-settings?toc=/mem/configmgr/tenant-attach/toc.json&amp;bc=/mem/configmgr/tenant-attach/breadcrumb/toc.json#attack-surface-reduction-configmgr).
3. Assign the policy to a Configuration Manager collection on the **Assignments** page.

## Device Status

You can review the status of endpoint security policies for tenant attached devices. The **Device Status** page can be accessed for all endpoint security policy types for tenant-attached clients. To display the **Device Status** page:

1. Select a policy that's targeted to **ConfigMgr** devices to display the **Overview** page for the policy.
2. Select **Device Status** to display a list of devices targeted by the policy.
3. The **Device Name**, **Compliance State**, and **SMS ID** are displayed for each of the devices on the **Device Status** page.