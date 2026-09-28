---
layout: Conceptual
title: Get started with Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/fundamentals/get-started
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.collection:
- M365-identity-device-management
- essentials-get-started
ms.subservice: fundamentals
description: See an overview of the steps to start using Intune. Plan your move and deployment of Intune, determine your licensing needs and any platform requirements, use compliance and Conditional Access, deploy apps, create device configuration profiles, and enroll your devices to be managed. Get more information on mobile application management for BYOD or personal devices.
ms.date: 2025-02-19T00:00:00.0000000Z
ms.topic: overview
ms.reviewer: 
locale: en-us
document_id: 59abb248-66d1-4892-48f4-2373a2e9bb56
document_version_independent_id: 59abb248-66d1-4892-48f4-2373a2e9bb56
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/fundamentals/get-started.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: fundamentals/get-started
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/fundamentals/get-started.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
- https://authoring-docs-microsoft.poolparty.biz/devrel/1dd701e0-441f-4b0a-9806-aa47decc4e35
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
- https://authoring-docs-microsoft.poolparty.biz/devrel/0a2fc935-5977-4aa6-9f55-0be03bd2acb8
platformId: c3d78121-773d-551e-d5b8-26784bba90b8
---

# Get started with Microsoft Intune - Microsoft Intune | Microsoft Learn

Microsoft Intune is a cloud-based service that helps you manage your devices and apps. For more information about what Microsoft Intune can do for your organization, go to [What is Microsoft Intune](what-is-intune).

This article provides an overview of the steps to start your Intune deployment.

![Diagram that shows the different steps to get started with Microsoft Intune, including set up, adding apps, using compliance &amp; Conditional Access, configuring device features, and then enrolling devices to be managed.](media/get-started/get-started-overview.png)

Tip

As a companion to this article, the Microsoft 365 admin center also has some setup guidance. The guide customizes your experience based on your environment. To access this deployment guide, go to the [Microsoft Intune setup guide in the Microsoft 365 admin center](https://go.microsoft.com/fwlink/?linkid=2224812), and sign in with the **Global Reader** (at a minimum). For more information on these deployment guides and the roles needed, go to [Advanced deployment guides for Microsoft 365 and Office 365 products](/en-us/microsoft-365/enterprise/setup-guides-for-microsoft-365).

## Before you begin

- To help plan your Intune deployment, use the [Planning guide to move to Microsoft Intune](planning-guide). It covers personal devices, licensing considerations, creating a rollout plan, communicating changes to your users, and more.

    The following articles are good resources:

    - [Move to cloud-native endpoints](../solutions/cloud-native-endpoints/overview)
    - [Planning guide to move to Microsoft Intune](planning-guide)
    - [Deployment guide: Set up or move to Microsoft Intune](setup-migration)
    - [Protection and configuration levels](protection-configuration-levels)
    - [Zero Trust deployment approach](zero-trust-deployment)
    - [Microsoft Intune fundamentals online training](/en-us/training/paths/endpoint-manager-fundamentals/)
- Determine your license needs and any other prerequisites for your Intune deployment. The following list provides some of the most common prerequisites:

    - **[Intune subscription](licensing)**: Included with some Microsoft 365 subscriptions. You also get access to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), which is a web-based console for managing your devices, apps, and users.
    - **[Microsoft 365 apps](https://www.microsoft.com/licensing/product-licensing/microsoft-365-apps)**: Included with Microsoft 365 and is used for productivity apps, including Outlook and Teams.
    - **[Microsoft Entra ID](https://www.microsoft.com/security/business/microsoft-entra-pricing)**: Microsoft Entra ID is used for the identity management for users, groups, and devices. It comes with your Intune subscription and possibly your Microsoft 365 subscription.

        Microsoft Entra ID P1 or P2, which might cost extra, gives you more features commonly used by organizations, including Conditional Access, multifactor authentication (MFA), and dynamic groups.
    - **[Windows Autopilot](/en-us/autopilot/requirements?tabs=licensing#licensing-requirements)**: Included with some Microsoft 365 subscriptions. Windows Autopilot gives you modern OS deployment for currently supported versions of Windows client devices.
    - **Platform specific prerequisites**: Depending on the platforms of your devices, there are other requirements.

        For example, if you manage iOS/iPadOS and macOS devices, you need an Apple MDM push certificate and possibly an Apple token. If you manage Android devices, you might need a managed Google Play account. If you use certificate authentication, you might need a SCEP or PKCS certificate.

        For more information, go to:

        - [**Android** enrollment guide](../device-enrollment/android/guide)
        - [**iOS/iPadOS** enrollment guide](../device-enrollment/apple/guide-ios-ipados)
        - [**macOS** enrollment guide](../device-enrollment/apple/guide-macos)
        - [**Windows** enrollment guide](../device-enrollment/windows/guide)
- Review and determine [Network endpoints](endpoints) necessary for the successful deployment and management of Microsoft Intune. Review the IP addresses, port settings, and domain names that need to be configured to allow communication between managed devices and Intune services.

## Step 1 - Set up Intune

In this step:

![](../media/icons/16/check.svg)**Confirm your devices are supported, create your Intune tenant, add users & groups, assign licenses**, and more.

This step focuses on setting up Intune and getting it ready for you to manage your user identities, apps, and devices. Intune uses many features in Microsoft Entra ID, including your domain, your users, and your groups.

For more information, go to [Step 1 - Set up Microsoft Intune](deploy-setup-step-1).

## Step 2 - Add and protect apps

In this step:

![](../media/icons/16/check.svg)**On devices that will enroll** in Intune, create a baseline of apps that devices must have, and then assign these app policies during enrollment. On apps that need extra security, also use app protection policies.

![](../media/icons/16/check.svg)**On devices that won't enroll** in Intune, use app protection policies and multifactor authentication (MFA):

- App protection policies help protect organization data on personal devices.
- MFA helps protect your organization's data from unauthorized access.

For more information, go to [Step 2 - Add, configure, and protect apps with Intune](deploy-protect-apps-step-2).

Every organization has a base set of apps that should be installed on devices. Before users enroll their devices, you can use Intune to assign these apps to their devices. During enrollment, the app policies are automatically deployed. When enrollment completes, the apps install and are ready to use.

If you prefer, you can enroll your devices, and then assign apps. It's your choice. The next time users check for new apps, they'll see the new apps available.

If users with their own personal devices access organization resources, then you need to protect any apps that access your organization data using mobile application management (MAM), at a minimum. You can create MAM policies for Outlook, Teams, SharePoint, and other apps. The [Microsoft Intune planning guide](planning-guide) has some guidance on managing personal devices.

Note

MFA is a feature of Microsoft Entra ID that must be enabled in your Microsoft Entra tenant. Then, you configure MFA for your apps. For more information, go to:

- [How it works: Microsoft Entra multifactor authentication](/en-us/entra/identity/authentication/concept-mfa-howitworks)
- [Tutorial: Secure user sign-in events with Microsoft Entra multifactor authentication](/en-us/entra/identity/authentication/tutorial-enable-azure-mfa)

## Step 3 - Check for compliance and turn on Conditional Access

In this step:

![](../media/icons/16/check.svg)**Create a baseline of compliance policies** that devices must have, and then assign these compliance policies during enrollment.

![](../media/icons/16/check.svg)**Enable Conditional Access** to enforce your compliance policies.

For more information, go to [Step 3 – Plan for compliance policies](deploy-compliance-step-3).

MDM solutions like Intune can set rules that devices should meet, and can report the compliance states of these rules. These rules are called compliance policies. When you combine compliance policies with Conditional Access, you can require devices meet certain security requirements before they can access your organization's data.

When users enroll their devices in Intune, the enrollment process can automatically deploy your compliance policies. When enrollment completes, admins can check the compliance status and get a list of devices that don't meet your rules.

If you prefer, you can enroll your devices before checking compliance. It's your choice. At the next Intune check-in, the compliance policies are assigned.

Note

Conditional Access is a feature of Microsoft Entra ID that must be enabled in your Microsoft Entra tenant. Then, you can create Conditional Access policies for your user identities, apps, and devices. For more information, go to:

- [Learn about Conditional Access and Intune](../device-security/conditional-access-integration/overview)
- [App-based Conditional Access with Intune](../device-security/conditional-access-integration/app-based-policies)
- [Conditional Access scenarios](../device-security/conditional-access-integration/scenarios)

## Step 4 - Configure device features

In this step:

![](../media/icons/16/check.svg)**Create baseline of security features and device features** that should be enabled or blocked. Assign these profiles during enrollment.

For more information, go to [Step 4 - Create device configuration profiles to secure devices and access organization resources](deploy-configuration-step-4).

Your organization can have a base set of device and security features that should be configured or should be blocked. These settings are added to device configuration and endpoint security profiles. Microsoft recommends you assign key security and device configuration policies during enrollment. When enrollment starts, the device configuration profiles are automatically assigned. When enrollment completes, these device and security features are configured.

If you prefer, you can enroll your devices before creating the configuration profiles. It's your choice. At the next Intune check-in, the profiles are assigned.

In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), you can create different profiles based on your device platform - Android, iOS/iPadOS, macOS, and Windows.

The following articles are good resources:

- [Apply features and settings on your devices using device profiles](../device-configuration/overview)
- [Use the settings catalog to configure settings](../device-configuration/settings-catalog/)
- [Manage endpoint security in Microsoft Intune](../device-security/endpoint-security-policies)
- [Windows security baselines](/en-us/windows/security/threat-protection/windows-security-baselines)

## Step 5 - Enroll your devices

In this step:

![](../media/icons/16/check.svg)**Enroll your devices** in Intune.

For more specific information, go to [Step 5 - Enrollment guidance: Enroll devices in Microsoft Intune](../device-enrollment/guide).

To fully manage devices, the devices must be enrolled in Intune to receive the compliance & Conditional Access policies, app policies, device configuration policies, and security policies you create. As an admin, you create enrollment policies for your users and devices. Each device platform (Android, iOS/iPadOS, Linux, macOS, and Windows) has different enrollment options. You choose what's best for your environment, your scenarios, and how your devices are used.

Depending on the enrollment option you choose, users can enroll themselves. Or, you can automate enrollment so users only need to sign in to the device with their organization account.

When a device enrolls, the device is issued a secure MDM certificate. This certificate communicates with the Intune service.

Different platforms have different enrollment requirements. The following articles can help you learn more about device enrollment, including platform-specific guidance:

- [Enrollment guidance: Enroll devices in Microsoft Intune](../device-enrollment/guide)
    - [Enrollment guide: Enroll Android devices](../device-enrollment/android/guide)
    - [Enrollment guide: Enroll iOS/iPadOS devices](../device-enrollment/apple/guide-ios-ipados)
    - [Enrollment guide: Enroll Linux desktop devices](../device-enrollment/guide-linux)
    - [Enrollment guide: Enroll macOS devices](../device-enrollment/apple/guide-macos)
    - [Enrollment guide: Enroll Windows devices](../device-enrollment/windows/guide)

## Cloud attach with Configuration Manager

Microsoft Configuration Manager helps protect on-premises Windows Server, devices, apps, and data. If you need to manage a combination of cloud and on-premises endpoints, you can cloud attach your Configuration Manager environment to Intune.

If you use Configuration Manager, then there are two steps to cloud attach your on-premises devices:

1. [Tenant attach](../configmgr/tenant-attach/prerequisites): Register your Intune tenant with your Configuration Manager deployment. Your Configuration Manager devices are shown in the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431). On these devices, you can run different actions, including installing apps and run Windows PowerShell scripts using the web-based Intune admin center.
2. [Co-management](../configmgr/comanage/overview): Manage Windows client devices with Configuration Manager and Microsoft Intune. Configuration Manager manages some workloads, and Intune manages other workloads.

    For example, you can use Configuration Manager to manage Windows updates, and use Intune to manage compliance & Conditional Access policies.

If you currently use Configuration Manager, you get immediate value through tenant attach, and you get more value through co-management.

For guidance on the Microsoft Intune setup that's right for your organization, go to [Deployment guide: Set up or move to Microsoft Intune](setup-migration).