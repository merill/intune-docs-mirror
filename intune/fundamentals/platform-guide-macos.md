---
layout: Conceptual
title: Deployment guide to manage macOS devices in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/fundamentals/platform-guide-macos
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
ms.subservice: fundamentals
description: Learn the recommended processes to manage macOS devices in Microsoft Intune.
ms.date: 2025-07-31T00:00:00.0000000Z
ms.topic: install-set-up-deploy
ms.reviewer: beflamm
locale: en-us
document_id: 7cf9b8e9-2e2b-123e-4531-6b6bf6fcc722
document_version_independent_id: 7cf9b8e9-2e2b-123e-4531-6b6bf6fcc722
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/fundamentals/platform-guide-macos.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: fundamentals/platform-guide-macos
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/fundamentals/platform-guide-macos.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
platformId: 1b01a23e-d1ca-6083-fc51-864faec8cfe1
---

# Deployment guide to manage macOS devices in Microsoft Intune - Microsoft Intune | Microsoft Learn

Secure access to work email, data, and apps on macOS devices. This article guides you through macOS-specific tasks to help you enable Intune mobile device management for macOS, configure policies, and deploy apps.

## Prerequisites

Complete the following prerequisites to enable macOS device management in Intune:

- [Add users](tenant-administration/add-users) and [groups](tenant-administration/add-groups)
- [Assign licenses to users](assign-licenses)
- [Set mobile device management authority](setup-mdm-authority)
- [Set up Apple MDM push (APNs) certificate](../device-enrollment/apple/create-mdm-push-certificate)

We recommend you use the least privileged role that's needed to complete tasks. For example, the least privileged role that can complete device enrollment tasks is the built-in **Policy and Profile Manager** Intune role.

For more information on the built-in roles and what they can do, see [Role-based access control (RBAC) with Intune](role-based-access-control/overview) and [Built-in role permissions for Intune](role-based-access-control/ref-built-in-roles).

For more detailed information about how to do the initial setup, onboard, or move to Microsoft Intune, see the [Intune setup deployment guide](setup-migration).

## Plan for your deployment

Use the [Microsoft Intune planning guide](planning-guide) to define your device management goals, use-case scenarios, and requirements. It will also help you plan for rollout, communication, support, testing, and validation. For example, because the Company Portal app for macOS isn't available in the App Store, we recommend having a communication plan so that end users know how to install Company Portal and enroll their devices.

## Enroll devices

Configure the enrollment methods and experience for company-owned and personal macOS devices. This step ensures that devices receive Intune policies and configurations after they enroll. Intune supports Bring Your Own Device (BYOD) enrollment, Apple Automated Device Enrollment, and direct enrollment for corporate devices. For information about each enrollment method and how to choose one that's right for your organization, see the [macOS device enrollment guide for Microsoft Intune](../device-enrollment/apple/guide-macos).

| Task | Detail |
| --- | --- |
| [Set up enrollment for user-owned (BYOD) devices](../device-enrollment/apple/methods-macos) | Complete the prerequisites in this article to enable enrollment for user-owned devices. You'll also find enrollment resources and links to share with device users so that they're supported throughout the enrollment experience. This enrollment method is for organizations that have *Bring Your Own Device* (BYOD) policies. BYOD lets people use their personal devices for work-related things. |
| [Set up Apple Automated Device Enrollment (ADE)](../device-enrollment/apple/setup-automated-macos) | Set up an out-of-the-box enrollment experience that automates enrollment on corporate-owned devices purchased through Apple School Manager or Apple Business. This method is ideal for organizations that have a large number of devices to enroll, because it eliminates the need to touch and configure each device individually.  When you use macOS ADE enrollment policies, we recommend configuring [macOS account configuration with LAPS](../device-security/laps/setup-macos) to enable newly enrolled devices to have a local admin and standard account and encrypted admin password that you can manage with Intune. |
| [Set up direct enrollment for corporate devices](../device-enrollment/apple/setup-direct-macos) | Set up an enrollment experience for corporate-owned devices that are unaffiliated with a single user, like devices used in a shared space or retail setting. Direct enrollment doesn't wipe the device so it's ideal to use when devices don't need access to local user data. You'll need to transfer the enrollment profile to the Mac directly, which requires a USB connection to a Mac computer running Apple Configurator. |
| [Add a device enrollment manager](../device-enrollment/setup-enrollment-manager) | People designated as device enrollment managers (DEM) can enroll up to 1,000 corporate-owned mobile devices at a time. DEM accounts are useful in organizations that enroll and prepare devices before handing them out to users. |
| [Identify devices as corporate-owned](../device-enrollment/add-corporate-identifiers) | You can assign corporate-owned status to devices to enable more management and identification capabilities in Intune. Corporate-owned status cannot be assigned to devices enrolled through Apple Business. |
| [Change device ownership](../device-enrollment/add-corporate-identifiers#change-device-ownership) | After a device has been enrolled, you can change its ownership label in Intune to corporate-owned or personal-owned. This adjustment changes the way you can manage the device. |
| [Troubleshoot enrollment problems](/en-us/troubleshoot/mem/intune/troubleshoot-device-enrollment-in-intune) | Troubleshoot and find resolutions to problems that occur during enrollment. |

## Create compliance rules

Create compliance policies to define the rules and conditions that users and devices must meet to access your protected resources. This is how you ensure that devices accessing your data meet your standards. Intune marks devices that fall short of your requirements as *noncompliant* and takes action (such as sending the user a notification, restricting access, or wiping the device) according to your configurations.

If you create a Conditional Access policy, it can work alongside your device compliance results to block access to resources from noncompliant devices. For a detailed explanation about compliance policies and how to get started, see [Use compliance policies to set rules for devices you manage with Intune](../device-security/compliance/overview).

| Task | Detail |
| --- | --- |
| [Create a compliance policy](../device-security/compliance/create-policy) | Get step-by-step guidance on how to create and assign a compliance policy to user and device groups. |
| [Add actions for noncompliance](../device-security/compliance/configure-noncompliance-actions) | Choose what happens when devices no longer meet the conditions of your compliance policy. You can add actions for noncompliance when you configure a device compliance policy, or later by editing the policy. |
| Create [a device-based](/en-us/entra/identity/conditional-access/policy-all-users-device-compliance) or [app-based](../device-security/conditional-access-integration/create-app-based-policy) Conditional Access policy | Specify the app or services you want to protect and define the conditions for access. |
| [Block access to apps that don't use modern authentication](../device-security/conditional-access-integration/block-no-modern-auth) | Create an app-based Conditional Access policy to block apps that use authentication methods other than OAuth2; for example, those apps that use basic and form-based authentication. Before you block access, however, sign in to Microsoft Entra ID and review the [authentication methods activity report](/en-us/azure/active-directory/authentication/howto-authentication-methods-activity) to see if users are using basic authentication to access essential things you forgot about or are unaware of. For example, things like meeting room calendar kiosks use basic authentication. |

## Configure device settings

Use Microsoft Intune to enable or disable settings and features on macOS devices being used for work. To configure and enforce these settings, create a device configuration profile and then assign the profile to groups in your organization.

| Task | Detail |
| --- | --- |
| [Create a device profile in Microsoft Intune](../device-configuration/create-device-profile) | Learn about the different types of device profiles you can create for your organization. |
| [Configure device features](../device-configuration/templates/configure-device-features-apple) | Configure common macOS features and functionality. For a description of the settings in this area, see the [device features reference](../device-configuration/templates/ref-device-features-apple). |
| [Configure Wi-Fi profile](../device-configuration/templates/configure-wifi) | This profile enables people to find and connect to your organization's Wi-Fi network. For a description of the settings in this area, see the [Wi-Fi settings reference](../device-configuration/templates/ref-wifi-settings-apple). |
| [Configure wired network profile](../device-configuration/templates/configure-wired-networks) | This profile enables people on desktop computers to connect to your organization's wired network. For a description of the settings in this area, see the [wired network reference](../device-configuration/templates/ref-wifi-settings-apple). |
| [Configure VPN profile](../device-configuration/templates/configure-vpn) | Set up a secure VPN option, such as Microsoft Tunnel, for people connecting to your organization's network. For a description of the settings in this area, see the [VPN settings reference](../device-configuration/templates/ref-vpn-settings-apple). |
| [Restrict device features](../device-configuration/templates/configure-device-restrictions) | Protect users from unauthorized access and distractions by limiting the device features they can use at work or school. For a description of the settings in this area, see the [device restrictions reference](../device-configuration/templates/ref-device-restrictions-apple). |
| [Configure custom profile](../device-configuration/templates/configure-custom-settings-apple) | Add and assign device settings and features that aren't built into Intune. |
| [Add and manage macOS extensions](../device-configuration/templates/configure-kernel-extensions-macos) | Add kernel extensions and system extensions, which enable users to install app extensions that extend the native capabilities of the operating system. For a description of the settings in this area, see the [macOS extensions reference](../device-configuration/templates/ref-kernel-extensions-settings-macos). |
| [Customize branding and enrollment experience](../app-management/configuration/configure-company-portal) | Customize the Intune Company Portal and Microsoft Intune app experience with your organization's own words, branding, screen preferences, and contact information. |

## Configure endpoint security

Use the Intune endpoint security features to configure device security and to manage security tasks for devices at risk.

| Task | Detail |
| --- | --- |
| [Manage devices with endpoint security features](../device-management/manage-endpoint-security-devices) | Use the endpoint security settings in Intune to effectively manage device security and remediate issues for devices. |
| [Use Conditional Access to limit access to Microsoft Tunnel](../device-security/microsoft-tunnel/conditional-access) | Use Conditional Access policies to gate device access to your Microsoft Tunnel VPN gateway. |
| [Add endpoint protection settings](../device-security/microsoft-tunnel/conditional-access) | Configure common endpoint protection security features, including Firewall, Gatekeeper, and FileVault. For a description of the settings in this area, see the [endpoint protection settings reference](../device-configuration/endpoint-security/ref-endpoint-protection-macos). |

## Set up secure authentication methods

Set up authentication methods in Intune to ensure that only authorized people access your internal resources. Intune supports multi-factor authentication, certificates, and derived credentials. Certificates can also be used for signing and encryption of email using S/MIME.

| Task | Detail |
| --- | --- |
| [Require multi-factor authentication (MFA)](../device-enrollment/configure-multifactor-authentication) | Require people to supply two forms of credentials at time of enrollment. |
| [Create a trusted certificate profile](../device-configuration/certificates/trusted-root-profiles) | Create and deploy a trusted certificate profile before you create a SCEP, PKCS, or PKCS imported certificate profile. The trusted certificate profile deploys the trusted root certificate to devices and users using SCEP, PKCS, and PKCS imported certificates. |
| [Use SCEP certificates with Intune](certificates/scep-infrastructure) | Learn what's needed to use SCEP certificates with Intune, and configure the required infrastructure. After you do that, you can [create a SCEP certificate profile](../device-configuration/certificates/scep-profiles) or [set up a third-party certification authority with SCEP](certificates/third-party-ca-scep). |
| [Use PKCS certificates with Intune](../device-configuration/certificates/pkcs-profiles) | Configure required infrastructure (such as on-premises certificate connectors), export a PKCS certificate, and add the certificate to an Intune device configuration profile. |
| [Use imported PKCS certificates with Intune](../device-configuration/certificates/imported-pfx-profiles) | Set up imported PKCS certificates, which enable you to [set up and use S/MIME to encrypt email](../device-security/certificates/s-mime). |

## Deploy apps

As you set up apps and app policies, think about your organization's requirements, such as the platforms you'll support, the tasks people do, the type of apps they need to complete those tasks, and who needs them. You can use Intune to manage the whole device (including apps) or use Intune to manage apps only.

| Task | Detail |
| --- | --- |
| [Add Intune Company Portal app](../app-management/deployment/add-company-portal-macos) | Learn how to get Company Portal on devices or instruct users how to do it on their own. |
| [Add Microsoft Edge](../app-management/deployment/add-edge-macos) | Add and assign Microsoft Edge in Intune. |
| [Add Microsoft 365](../app-management/deployment/add-microsoft-365-macos) | Add and assign Microsoft 365 apps in Intune. |
| [Add line-of-business apps](../app-management/deployment/add-lob-macos) | Add and assign macOS line-of-business (LOB) apps in Intune. |
| [Assign apps to groups](../app-management/deployment/assign-groups) | After you add apps to Intune, assign them to users and devices. |
| [Include and exclude app assignments](../app-management/deployment/configure-assignment-scope) | Control access and availability to an app by including and excluding selected groups from assignment. |
| [Use shell scripts on macOS devices](../device-management/tools/run-shell-scripts-macos) | Use shell scripts to extend device management capabilities in Intune beyond what's supported by the macOS operating system. |

## Run remote actions

After devices are set up, you can use remote actions in Intune to manage and troubleshoot macOS devices from a distance. The following articles introduce you to the remote actions in Intune. If an action is absent or disabled in the portal, then it isn't supported on macOS.

| Task | Detail |
| --- | --- |
| [Take remote action on devices](../device-management/actions/) | Learn how to drill down and remotely manage and troubleshoot individual devices in Intune. This article lists all remote actions available in Intune and links to those procedures. |
| [Use TeamViewer to remotely administer Intune devices](../device-management/tools/teamviewer-legacy) | Configure TeamViewer within Intune, and learn how to remotely administer a device. |
| [Use security tasks to view threats and vulnerabilities](../device-security/microsoft-defender/remediate-vulnerabilities) | Integrate Intune with Microsoft Defender for Endpoint to take advantage of Defender for Endpoint's threat and vulnerability management and use Intune to remediate endpoint weakness identified by Defender's vulnerability management capability. |