---
layout: Conceptual
title: How users enroll devices - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/mdm/deploy-use/user-enroll-devices-on-premises-mdm
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
description: Understand how users enroll devices with on-premises mobile device management (MDM) in Configuration Manager.
ms.date: 2020-01-13T00:00:00.0000000Z
ms.subservice: mdm
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: ef72aff0-e284-f4e9-84b6-310b4c0ad5c3
document_version_independent_id: 2ca014c3-91f9-b24a-4fa3-9f8e36f1bbd3
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/mdm/deploy-use/user-enroll-devices-on-premises-mdm.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/mdm/deploy-use/user-enroll-devices-on-premises-mdm
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/mdm/deploy-use/user-enroll-devices-on-premises-mdm.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/e0ffb20c-01c6-407b-a9bd-29111652a1dc
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/3904bce4-d817-48cf-85fd-b6146fca83b7
platformId: ecee42b3-922b-eef9-59f1-f522483b261c
---

# How users enroll devices - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

With Configuration Manager on-premises mobile device management (MDM), users can enroll their devices. There are two prerequisites:

- With client settings, you grant the user permission to enroll.
- You install the required trusted root certificate on the device.

For more information on how to set up enrollment, see [Set up device enrollment for on-premises MDM](../get-started/set-up-device-enrollment-on-premises-mdm).

## Enroll Windows 10

1. On a Windows 10 computer, go to **Settings**.
2. Select **Accounts**, and then select **Access work or school**.
3. Select **Connect**, enter your user principal name (UPN), and select **Continue**. The UPN may be the same as your email address, for example, jdoe@contoso.com.
4. Enter the fully qualified domain name (FQDN) of the enrollment proxy point, and select **Continue**.
5. Enter your password, and select **Sign in**.
6. Windows doesn't need to remember the sign-in info for this action, so select **Skip**.

After a short time, the device enrolls with Configuration Manager.

## Enroll Windows 10 Mobile

1. On a Windows 10 Mobile device, go to **Settings**.
2. Select **Accounts**, and then select **Work access**.
3. Select **Connect**.
4. Enter your UPN and the FQDN of the enrollment proxy point. Then select **Connect**.
5. On the next screen, enter your UPN and password, and then select **Sign-in**.

After a short time, the device enrolls with Configuration Manager. Select **Done**.

## Verify enrollment

Use the Configuration Manager console to verify that devices are enrolled successfully. In the Configuration Manager console, go to the **Assets and Compliance** workspace, and select **Devices**. Browse or search for the enrolled device in the list of devices.