---
layout: Conceptual
title: Set up enrollment for on-premises MDM - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/mdm/get-started/set-up-device-enrollment-on-premises-mdm
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
description: Grant users permission to enroll their devices for on-premises mobile device management (MDM) in Configuration Manager.
ms.date: 2020-01-09T00:00:00.0000000Z
ms.subservice: mdm
ms.topic: install-set-up-deploy
ms.collection: tier3
locale: en-us
document_id: 27a893fe-950c-2f1e-20d2-249d906badec
document_version_independent_id: 2ad0a2ef-eeb8-06a9-40e2-03d02c39e997
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/mdm/get-started/set-up-device-enrollment-on-premises-mdm.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/mdm/get-started/set-up-device-enrollment-on-premises-mdm
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/mdm/get-started/set-up-device-enrollment-on-premises-mdm.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: 918146c1-3f63-3e94-a6b4-a6d980dcfd93
---

# Set up enrollment for on-premises MDM - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

The final step to set up on-premises mobile device management (MDM) is to enable users to enroll their devices. Use Configuration Manager client settings to grant users permission to enroll devices in on-premises MDM.

## Create an enrollment profile

To push the settings required to allow users to enroll mobile devices, add a new enrollment profile to the default client settings. This profile then applies to all users in the Configuration Manager site.

Note

This process uses the **Default Client Settings**, which will automatically apply to all devices and users. Alternatively, you can create custom client settings, and then deploy to collections of your choice. This alternative method requires at least two custom client settings, one for *device* settings and one for *user* settings. For more information, see [How to configure client settings](../../core/clients/deploy/configure-client-settings).

1. In the Configuration Manager console, go to the **Administration** workspace, and select the **Client Settings** node. Open **Default Client Settings** and select the **Enrollment** group.
2. Under Device Settings, specify the **Polling interval for modern devices (minutes)**. By default this interval is 60 minutes.
3. Under User Settings, enable the option to **Allow users to enroll modern devices**.
4. For the **Modern device enrollment profile**, select **Set Profile**. In the Enrollment Profile window, select **Create**.
5. In the Create Enrollment Profile window, specify the following information:

    - A unique and descriptive **Name** for the enrollment profile.
    - An optional **Description** to provide additional information about the profile.
    - Choose the **Management site code** that contains the device management point. Select **OK** to save and close.

## Configure additional client settings

There are additional client settings to configure devices after they've enrolled. For more general information, see [How to configure client settings](../../core/clients/deploy/configure-client-settings).

Configuration Manager supports the following client settings for on-premises MDM:

- **Client policy**: These settings specify the frequency for downloading client policy to the device. You can also enable settings for user policy. For more information, see [About client settings - Client Policy](../../core/clients/deploy/about-client-settings#client-policy).
- **Software deployment**: Set the interval for evaluating software deployments. For more information, see [About client settings - Software Deployment](../../core/clients/deploy/about-client-settings#software-deployment).

    Note

    For on-premises MDM, software deployment settings can only be used as default client settings.

## Discover users

For users to receive the client settings with the enrollment profile for on-premises MDM, the site discovers their user account in Active Directory. To make sure everyone that needs the enrollment profile gets it, run discovery for Active Directory users. For more information, see [Active Directory User Discovery](../../core/servers/deploy/configure/about-discovery-methods#bkmk_aboutUser).

## Install the trusted root certificate

Domain-joined devices get the trust root certificate for trusted communication with the servers hosting the site system roles. Active Directory Certificate Services automatically distributes the trusted root certificate. Non-domain joined computers and mobile devices need this certificate installed via other means to allow enrollment.

Note

If the web server certificates are issued by a public certificate authority, most devices already trusted these CAs. If your design includes use of one of these public CAs, you don't need to do this step.

After you [export the trusted root certificate](set-up-certificates-on-premises-mdm#bkmk_exportCert), you need to install it on devices that will need it to enroll. For example, devices that aren't joined to the domain and can't get it automatically from Active Directory. The process that you use will depend upon the following factors:

- Specific device types and technical capabilities
- OS version
- Your business, security, and user experience requirements

The following list includes some example methods to deliver and install the trusted root certificate on devices:

- File share
- Email attachment
- Memory card
- Tethered device
- Cloud storage (such as OneDrive)
- Near field communication (NFC) connection
- Barcode scanner
- Out of box experience (OOBE) provisioning package

### Manually install the trusted root certificate in Windows

1. On the device to be enrolled, browse in File Explorer to the trusted root certificate file (.cer), and **Open** it.
2. In the Certificate window, select **Install Certificate**.
3. In the Certificate Import Wizard, select **Local Machine**, and then select **Next** to continue as administrator.
4. On the Certificate Store page, select **Place all certificates in the following store**, and then select **Browse**.
5. In the Select Certificate Store window, select **Trusted Root Certification Authorities**, and select **OK**.
6. Complete and wizard.