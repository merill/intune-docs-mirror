---
layout: Conceptual
title: Co-manage internet-based devices - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/comanage/how-to-prepare-win10
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
description: Learn how to prepare your Windows internet-based devices for co-management.
ms.date: 2024-12-16T00:00:00.0000000Z
ms.topic: how-to
ms.subservice: co-management
ms.collection: tier3
locale: en-us
document_id: 875e279b-9029-d1e5-8a6c-0e93ce38ddba
document_version_independent_id: 80bc34d7-3ef7-1c4f-da41-0474b1c5f4a4
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/comanage/how-to-prepare-Win10.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/comanage/how-to-prepare-win10
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/comanage/how-to-prepare-Win10.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
platformId: 50606bfd-4b24-b5e0-7561-7368f1c052dc
---

# Co-manage internet-based devices - Configuration Manager | Microsoft Learn

This article focuses on the second path to co-management, for new internet-based devices. This scenario is when you have new Windows 10 or later devices that join Microsoft Entra ID and automatically enroll to Intune. You install the Configuration Manager client to reach a co-management state.

## Windows Autopilot

For new Windows devices, use the Windows Autopilot service to configure the out of box experience (OOBE). This process includes joining the device to Microsoft Entra ID, enrolling the device in Intune, installing the Configuration Manager client, and configuring co-management.

For more information, see [How to enroll with Windows Autopilot](autopilot-enrollment).

Note

As we talk with our customers that are using Microsoft Intune to deploy, manage, and secure their client devices, we often get questions regarding co-managing devices and Microsoft Entra hybrid joined devices. Many customers confuse these two topics. Co-management is a management option, while Microsoft Entra ID is an identity option. For more information, see [Understanding hybrid Microsoft Entra ID and co-management scenarios](https://techcommunity.microsoft.com/t5/microsoft-endpoint-manager-blog/understanding-hybrid-azure-ad-join-and-co-management/ba-p/2221201). This blog post aims to clarify Microsoft Entra hybrid join and co-management, how they work together, but aren't the same thing.

You can't deploy the Configuration Manager client while provisioning a new computer in Windows Autopilot user-driven mode for Microsoft Entra hybrid join. This limitation is due to the identity change of the device during the Microsoft Entra hybrid join process. Deploy the Configuration Manager client after the Windows Autopilot process. For alternative options to install the client, see [Client installation methods in Configuration Manager](../core/clients/deploy/plan/client-installation-methods).

### Gather information from Configuration Manager

Use Configuration Manager to collect and report the device information required by Intune. This information includes the device serial number, Windows product identifier, and a hardware identifier. It's used to register the device in Intune to support Windows Autopilot.

1. In the Configuration Manager console, go to the **Monitoring** workspace, expand the **Reporting** node, expand **Reports**, and select the **Hardware - General** node.
2. Run the report, **Windows Autopilot Device Information**, and view the results.
3. In the report viewer, select the **Export** icon, and choose the **CSV (comma-delimited)** option.
4. After saving the file, upload the data to Intune.

For more information, see [Manually register devices with Windows Autopilot](/en-us/autopilot/add-devices).

### Windows Autopilot for existing devices

*Windows Autopilot for existing devices* allows you to reimage and provision a Windows devices for [Windows Autopilot user-driven mode](/en-us/autopilot/user-driven) using a single, native Configuration Manager task sequence.

For more information, see [Windows Autopilot for existing devices](/en-us/autopilot/existing-devices).

## Install the Configuration Manager client

You no longer need to create and assign an Intune app to install the Configuration Manager client. The Intune enrollment policy automatically installs the Configuration Manager client as a first-party app. The device gets the client content from the Configuration Manager cloud management gateway (CMG), so you don't need to provide and manage the client content in Intune. For more information, see [How to enroll with Windows Autopilot](autopilot-enrollment).

You do still specify the Configuration Manager client command-line parameters in Intune.

Note

Make sure that the devices trust the CMG server authentication certificate. For more information, see [CMG server authentication certificate](../core/clients/manage/cmg/server-auth-cert). If a device doesn't trust the CMG server authentication certificate, you'll see a WINHTTP\_CALLBACK\_STATUS\_FLAG\_INVALID\_CA error in the ccmsetup.log on the client.

### Get the command line from Configuration Manager

1. In the Configuration Manager console, go to the **Administration** workspace, expand **Cloud Services**, and select the **Cloud Attach** node.

    Tip

    For version 2103 and earlier, select the **Co-management** node.
2. Select the co-management object, and then choose **Properties** in the ribbon.
3. On the **Enablement** tab, copy the command line. Paste it into Notepad to save for the next process. The command line only shows if you've met all of the prerequisites, such as a cloud management gateway.

The following command line is an example: `CCMSETUPCMD="CCMHOSTNAME=contoso.cloudapp.net/CCM_Proxy_MutualAuth/72186325152220500 SMSSITECODE=ABC"`

Decide which command-line properties you require for your environment:

- The following command-line properties are required in all scenarios:

    - `CCMHOSTNAME`
    - `SMSSITECODE`
- If devices use Microsoft Entra ID for client authentication and also have a PKI-based client authentication certificate, specify the following properties to use Microsoft Entra ID:

    - `AADCLIENTAPPID`
    - `AADRESOURCEURI`
- If the client roams back to the intranet, use the `SMSMP` property.
- If you use your own PKI certificate, and your CRL isn't published to the internet, use the `/NoCRLCheck` parameter. For more information, see [About client installation properties: /NoCRLCheck](../core/clients/deploy/about-client-installation-properties#nocrlcheck).

    Important

    Microsoft recommends publishing the CRL. For more information, see [Planning for CRLs](../core/plan-design/security/plan-for-certificates#pki-certificate-revocation).
- To bootstrap a task sequence immediately after client registration, use the `PROVISIONTS` property. For more information, see [About client installation properties: PROVISIONTS](../core/clients/deploy/about-client-installation-properties#provisionts).
- To make sure that internet-based devices get the latest version of the Configuration Manager client, use the `UPGRADETOLATEST` property. For more information, see [About client installation properties: `UPGRADETOLATEST`](../core/clients/deploy/about-client-installation-properties#upgradetolatest).

The site publishes other Microsoft Entra information to the cloud management gateway (CMG). A Microsoft Entra joined client gets this information from the CMG during the ccmsetup process, using the same tenant to which it's joined. This behavior further simplifies enrolling devices to co-management in an environment with more than one Microsoft Entra tenant. The only two required ccmsetup properties are `CCMHOSTNAME` and `SMSSITECODE`.

The following example includes all of these properties:

`CCMSETUPCMD="CCMHOSTNAME=CONTOSO.CLOUDAPP.NET/CCM_Proxy_MutualAuth/72186325152220500 SMSSITECODE=ABC AADCLIENTAPPID=7506ee10-f7ec-415a-b415-cd3d58790d97 AADRESOURCEURI=https://contososerver SMSMP=https://mp1.contoso.com PROVISIONTS=PRI20001"`

For more information, see [Client installation properties](../core/clients/deploy/about-client-installation-properties).

Important

If you customize this command line, make sure it isn't more than 1024 characters long. When the command line length is greater than 1024 characters, the client installation fails.