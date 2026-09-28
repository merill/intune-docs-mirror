---
layout: Conceptual
title: Use Microsoft Entra ID for co-management - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/comanage/quickstart-hybrid-aad
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
description: With Microsoft Entra ID you can take advantage of improved productivity for your users and security for your resources, across both cloud and on-prem environments
ms.date: 2021-11-08T00:00:00.0000000Z
ms.subservice: co-management
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: a1ab9611-f71e-41fb-08ce-18cb7a3d8e4e
document_version_independent_id: 8928c988-e002-b331-6584-b6b35b1b156b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/comanage/quickstart-hybrid-aad.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/comanage/quickstart-hybrid-aad
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/comanage/quickstart-hybrid-aad.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
platformId: 5c52c528-80a6-4265-956f-8d82a52c881b
---

# Use Microsoft Entra ID for co-management - Configuration Manager | Microsoft Learn

In the cloud, identity is the new control plane. Microsoft Entra ID allows you to link your users, devices, and applications across both cloud and on-premises environments. Registering your devices to Microsoft Entra ID enables you to improve productivity for your users and security for your resources. Having devices in Microsoft Entra ID is the foundation for both co-management and device-based Conditional Access.

For more information on device-based Conditional Access, see [How To: Require managed devices for cloud app access with Conditional Access](/en-us/azure/active-directory/conditional-access/require-managed-devices).

In the following video, senior program manager Sandeep Deo and product marketing manager Adam Harbour discuss and demo Microsoft Entra ID for co-management:

Microsoft Entra ID provides two options for company-owned devices to suit your organization's needs:

- **Microsoft Entra joined device**: Join your Windows 10 or later devices to Microsoft Entra ID without needing to join them to your on-premises Active Directory

    - Supports Windows 10 or later
    - Set up without requiring any additional configuration to your on-premises environments
    - By enabling a few settings in Microsoft Entra ID, you can enable your users to join devices to Microsoft Entra ID through the Windows setup experience (OOBE)
    - For more information, see [How to: Plan your Microsoft Entra join implementation](/en-us/azure/active-directory/devices/azureadjoin-plan)
- **Microsoft Entra hybrid joined device**: Join your existing domain-joined devices to Azure A

    - Supports Windows 10 or later, or Windows 8.1
    - Set up using AD FS claims or Microsoft Entra Connect
    - For Windows 10 or later, the join happens in the machine context, so users don't have to take extra steps
    - For more information, see [How to plan your Microsoft Entra hybrid join implementation](/en-us/azure/active-directory/devices/hybrid-azuread-join-plan)

Both options provide similar functionality for users. It's flexible for you to choose either one based on your needs. For example, you can [access your on-premises resources](/en-us/azure/active-directory/devices/azuread-join-sso) from Microsoft Entra joined machines even though they aren't joined to Active Directory.

You can join devices to Microsoft Entra ID in various environments, no matter your [authentication method](/en-us/azure/active-directory/hybrid/choose-ad-authn). For example, federated authentication, or cloud authentication.

If you already have an on-premises Active Directory, setting up either option is straightforward.

## Benefits

Joining devices to Microsoft Entra ID provides the following benefits to your organization:

### Single sign-on to cloud resources

On devices joined to Microsoft Entra ID, you get an integrated experience accessing any cloud or on-premises resources. Once you sign in to a Windows machine that's joined to Microsoft Entra ID, you get single sign-on to all applications without any additional sign-in prompts.

### Windows Hello for Business

Windows Hello for Business brings strong password-less authentication to Windows. By joining your devices to Microsoft Entra ID, you can enable Windows Hello for Business across your user base for both cloud and on-premises resources. Windows Hello for Business eliminates the problem of remembering complex passwords or inadvertently exposing them. Its sign-in process is both simple and secure.

For more information, see [Windows Hello for Business](/en-us/windows/security/identity-protection/hello-for-business/hello-identity-verification).

### Device-based Conditional Access

Enable Conditional Access based on the device state to better protect your organization's data. Device-based Conditional Access requires a managed device. This device must be a compliant device or a Microsoft Entra hybrid joined device. For Microsoft Entra joined devices, you need Intune to mark the device as compliant. But for Microsoft Entra hybrid joined devices, the device state itself is used to evaluate Conditional Access. Co-management provides you the additional advantage of evaluating compliance through Intune for Microsoft Entra hybrid joined devices. This feature makes sure the device configuration is intact.

For more information on device-based Conditional Access, see [How To: Require managed devices for cloud app access with Conditional Access](/en-us/azure/active-directory/conditional-access/require-managed-devices).

### Automatic device licensing

All Windows devices joined to Microsoft Entra go through license checks. These checks enable you to automatically upgrade them from Pro to Enterprise through the Microsoft cloud. When you remove the relevant subscription from the user, the device automatically downgrades its license. This feature provides a single pane of control for managing Windows licenses, without any complicated processes or on-premises systems.

### Self-service functionality

Self-service functionality includes self-service password reset and BitLocker recovery key. Microsoft Entra ID also provides you with direct options to reset your password or access BitLocker recovery keys. You can use Microsoft Entra ID to reset your password directly from the Windows lock screen, instead of from a web browser. These features reduce friction for users and help cut helpdesk costs for your organization.

For more information, see [Tutorial: Enable users to unlock their account or reset passwords using Microsoft Entra self-service password reset](/en-us/azure/active-directory/authentication/tutorial-enable-sspr).

### Enterprise state roaming

All devices joined to Microsoft Entra ID can sync their settings to the cloud. Any device to which a user signs in syncs all their settings for a more productive experience.

## Value proposition

Joining your devices to Microsoft Entra ID through either method accelerates your digital transformation. It enables more functionality provided by Microsoft 365. You'll have better experiences, and you'll have greater security for your data.

Microsoft Entra ID provides several options to ease your work load, for example:

- Manage all the device identities in your organization from a single place.
- Lower your helpdesk costs by enabling self-service password reset. Then you users can reset your password from the Windows lock screen on your device at any time.

## Configure

If you already have an on-premises Active Directory environment, and you want to join your domain-joined devices to Microsoft Entra ID, configure Microsoft Entra hybrid joined devices. For more information, [How To: Plan your Microsoft Entra hybrid join implementation](/en-us/azure/active-directory/devices/hybrid-azuread-join-plan).

Configuration Manager has a client setting to [Automatically register new Windows 10 or later domain-joined devices with Microsoft Entra ID](../core/clients/deploy/about-client-settings#automatically-register-new-windows-10-or-later-domain-joined-devices-with-azure-active-directory). For more information on configuring client settings, see [How to configure client settings](../core/clients/deploy/configure-client-settings).

If you want to configure Microsoft Entra join for your devices without also joining them to your on-premises domain, review the considerations for Microsoft Entra join in your environment. Once you decided to go with Microsoft Entra join, you have many options to deploy it based on your organization's needs. For more information, see the following articles:

- [How to: Plan your Microsoft Entra join implementation](/en-us/azure/active-directory/devices/azureadjoin-plan)
- [Understand your provisioning options](/en-us/azure/active-directory/devices/azureadjoin-plan#understand-your-provisioning-options)