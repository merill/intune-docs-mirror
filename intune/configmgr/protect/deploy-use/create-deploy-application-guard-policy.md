---
layout: Conceptual
title: Manage Application Guard policies - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/protect/deploy-use/create-deploy-application-guard-policy
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
description: Learn how to create and deploy Microsoft Defender Application Guard policies
ms.date: 2022-12-05T00:00:00.0000000Z
ms.subservice: protect
ms.topic: install-set-up-deploy
ms.collection: tier3
locale: en-us
document_id: 330e5473-cbfa-ea69-9229-a1fdfe5441cc
document_version_independent_id: a7d72a14-5cec-47c1-1e16-117c481b46fc
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/protect/deploy-use/create-deploy-application-guard-policy.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/protect/deploy-use/create-deploy-application-guard-policy
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/protect/deploy-use/create-deploy-application-guard-policy.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c671beaa-a830-4c9f-aceb-97379ee031ca
- https://authoring-docs-microsoft.poolparty.biz/devrel/e0ffb20c-01c6-407b-a9bd-29111652a1dc
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/8921374c-4dbe-4ed0-b011-a39e18bfbd98
- https://authoring-docs-microsoft.poolparty.biz/devrel/3904bce4-d817-48cf-85fd-b6146fca83b7
platformId: f490e490-92e8-2059-e720-82fe39b56d32
---

# Manage Application Guard policies - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

You can create and deploy [Microsoft Defender Application Guard (Application Guard)](/en-us/windows/security/threat-protection/microsoft-defender-application-guard/md-app-guard-overview) policies by using the Configuration Manager endpoint protection. These policies help protect your users by opening untrusted web sites in a secure isolated container that isn't accessible by other parts of the operating system.

## Prerequisites

To create and deploy a Microsoft Defender Application Guard policy, you must use Windows 10 1709 or later. The Windows 10 or later devices to which you deploy the policy must be configured with a [network isolation policy](/en-us/windows/security/threat-protection/microsoft-defender-application-guard/configure-md-app-guard#network-isolation-settings). For more information, see the [Microsoft Defender Application Guard overview](/en-us/windows/security/threat-protection/microsoft-defender-application-guard/md-app-guard-overview).

## Create a policy, and to browse the available settings

1. In the Configuration Manager console, choose **Assets and Compliance**.
2. In the **Assets and Compliance** workspace, choose **Overview** &gt; **Endpoint Protection** &gt; **Microsoft Defender Application Guard**.
3. In the **Home** tab, in the **Create** group, click **Create Microsoft Defender Application Guard Policy**.
4. Using the [article](/en-us/windows/security/threat-protection/microsoft-defender-application-guard/configure-md-app-guard) as a reference, you can browse and configure the available settings. Configuration Manager allows you to set certain policy settings:

    - Application behavior
    - Host interaction settings
5. On the **Network Definition** page, specify the corporate identity, and define your corporate network boundary.

    Note

    Windows 10 or later PCs store only one network isolation list on the client. You can create two different kinds of network isolation lists and deploy them to the client:

    - one from Windows Information Protection
    - one from Microsoft Defender Application Guard

    If you deploy both policies, these network isolation lists must match. If you deploy lists that don't match to the same client, the deployment will fail. For more information, see the [Windows Information Protection documentation](/en-us/windows/security/information-protection/windows-information-protection/create-wip-policy-using-configmgr).
6. When you're finished, complete the wizard, and deploy the policy to one or more Windows 10 1709 or later devices.

### Application behavior

Configures interactions between host devices and the Application Guard container. Before Configuration Manager version 1802, both application behavior and host interaction were under the **Settings** tab.

- **Clipboard**- Under settings prior to Configuration Manager 1802
    - Permitted content type
        - Text
        - Images
- **Printing:**
    - Enable printing to XPS
    - Enable printing to PDF
    - Enable printing to local printers
    - Enable printing to network printers
- **Graphics:**(starting with Configuration Manager version 1802)
    - Virtual graphics processor access
- **Files:**(starting with Configuration Manager version 1802)
    - Save downloaded files to host
- **Policies:**(starting with Configuration Manager version 2207)
    - Enable or disable cameras and microphones
    - Certificate matching the thumbprints to the isolated container

### Host interaction settings

Configures application behavior inside the Application Guard session. Before Configuration Manager version 1802, both application behavior and host interaction were under the **Settings** tab.

- **Other:**
    - Retain user-generated browser data
    - Audit security events in the isolated application guard session

To edit Application Guard settings, expand **Endpoint Protection** in the **Assets and Compliance** workspace, then click on the **Microsoft Defender Application Guard** node. Right-click on the policy you want to edit, then select **Properties**.

## Known issues

*Applies to version 2203 or earlier*

Devices running Windows 10, version 2004 will show failures in compliance reporting for Microsoft Defender Application Guard File Trust Criteria. This issue occurs because some subclasses were removed from the WMI class `MDM_WindowsDefenderApplicationGuard_Settings01` in Windows 10, version 2004. All other Microsoft Defender Application Guard settings will still apply, only File Trust Criteria will fail. Currently, there are no workarounds to bypass the error. 

*Applies to version 2207 or later*

Enabling the policy doesn't install Microsoft Defender Application Guard feature by default. Deploy a PowerShell script via ConfigMgr to all applicable machines.

Use the following commands to enable feature. Enable-WindowsOptionalFeature -online -FeatureName "Windows-Defender-ApplicationGuard"