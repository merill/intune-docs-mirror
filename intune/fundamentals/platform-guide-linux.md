---
layout: Conceptual
title: Deployment guide for Linux device management - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/fundamentals/platform-guide-linux
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
description: Use our platform deployment guide to set up Linux device management in Microsoft Intune.
ms.date: 2024-11-04T00:00:00.0000000Z
ms.topic: install-set-up-deploy
ms.reviewer: 
locale: en-us
document_id: 648dc729-75ea-5bf1-863e-13e68682042b
document_version_independent_id: 648dc729-75ea-5bf1-863e-13e68682042b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/fundamentals/platform-guide-linux.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: fundamentals/platform-guide-linux
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/fundamentals/platform-guide-linux.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
- https://authoring-docs-microsoft.poolparty.biz/devrel/5287f575-02f0-405f-92b7-800456526b0c
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
- https://authoring-docs-microsoft.poolparty.biz/devrel/06e86142-34c2-4b94-ab9c-9477c21f7152
platformId: 1597143b-3a9c-a749-4a5b-a87a2ad048b4
---

# Deployment guide for Linux device management - Microsoft Intune | Microsoft Learn

This guide describes everything you need to do to protect and manage Linux apps and endpoints using Microsoft Intune, including how to:

- Prepare your tenant for device enrollment.
- Create Linux device compliance policies.
- Add custom compliance settings.
- Enforce Conditional Access policies in Microsoft Edge.
- Support employees and students enrolling their desktops.

For each section in this guide, review the associated tasks. Some tasks are required and some, like setting up Conditional Access, are optional. Select the provided links in each section to go to our recommended help docs on Microsoft Learn, where you can find more detailed information and how-to instructions.

## Step 1: Prerequisites

Microsoft Intune, Microsoft Entra ID, and Microsoft Edge power the feature and capabilities for Linux desktop management. Microsoft Intune powers the device management and compliance capabilities. Microsoft Entra ID powers Conditional Access, which is used alongside Microsoft Intune compliance policies. Microsoft Edge is the web browser app used to provide protected access to Microsoft 365 web apps.

Complete the following prerequisites as an Intune administrator to enable your tenant's endpoint management capabilities:

- [Add users](tenant-administration/add-users) and [groups](tenant-administration/add-groups)
- [Assign licenses to users](assign-licenses)
- [Set mobile device management authority](setup-mdm-authority)

We recommend you use the least privileged role that's needed to complete tasks. For example, the least privileged role that can complete device enrollment tasks is the built-in **Policy and Profile Manager** Intune role.

For more information on the built-in roles and what they can do, see [Role-based access control (RBAC) with Intune](role-based-access-control/overview) and [Built-in role permissions for Intune](role-based-access-control/ref-built-in-roles).

For more details and recommendations about how to prepare your organization, onboard, or adopt Intune for mobile device management, see the [Intune setup deployment guide](setup-migration).

## Step 2: Plan for your deployment

Use the [Microsoft Intune planning guide](planning-guide) to define your device management goals, use-case scenarios, and requirements. It will also help you plan for rollout, communication, support, testing, and validation. For example, because you don't have to be there when employees and students are enrolling their devices, we recommend having a communication plan so that people know where to find information about installing and using Company Portal and Microsoft Edge.

## Step 3: Create device compliance policies

Create a device compliance policy to ensure that Linux devices accessing your data are secure and meet your organization's standards. The final stage of the enrollment process is the compliance evaluation, which verifies that the settings on the device meet your policies. Device users must resolve all compliance issues to get access to protected resources. Intune marks devices that fall short of compliance requirements as *noncompliant* and takes additional action (such as sending the user a notification, restricting access, or wiping the device) according to your *action for noncompliance* configurations.

You can enforce device compliance policies based on Linux distribution type, version, device encryption, or password complexity. All available compliance settings for Linux are in the Microsoft Intune settings catalog. You can use Microsoft Entra Conditional Access policies in conjunction with device compliance policies to control access to Microsoft 365 web apps in Microsoft Edge. For example, if an employee tries to access Microsoft Teams in Edge without first enrolling or securing their device, they won't be able to sign in.

Tip

For an overview of device compliance policies, see [Compliance overview](../device-security/compliance/overview#device-compliance-policies).

| Task | Detail |
| --- | --- |
| [Create a device compliance policy](../device-security/compliance/create-policy) | Get step-by-step guidance on how to create and assign a device compliance policy for Linux devices. |
| [Add custom compliance settings](../device-security/compliance/custom-settings) | With custom compliance settings, you can write your own Bash scripts to address compliance scenarios not yet included in the device compliance options built into Microsoft Intune. This article describes how to create, monitor, and troubleshoot custom compliance policies for Linux devices. Custom compliance settings require you to [create a custom script](../device-security/compliance/create-custom-script) that identifies the settings and value pairs. |
| [Add actions for noncompliance](../device-security/compliance/configure-noncompliance-actions) | Choose what happens when devices no longer meet the conditions of your compliance policy. Examples of actions include sending alerts, remotely locking devices, or retiring devices. You can add actions for noncompliance when you configure a device compliance policy, or later by editing the policy. |
| Create [a device-based](/en-us/entra/identity/conditional-access/policy-all-users-device-compliance) or [app-based](../device-security/conditional-access-integration/create-app-based-policy) Conditional Access policy | Set up a Conditional Access policy to protect and grant access to Microsoft 365 web apps in the Microsoft Edge browser for Linux. Conditional Access blocks noncompliant devices from accessing protected work apps in Edge, and grants access to compliant devices. You must have a device compliance policy for Conditional Access to work with Linux devices. |

## Step 4: Enroll devices

Enrollment is supported on Linux desktops running:

- Ubuntu LTS, version 26.04 and 24.04 LTS
- RedHat Enterprise Linux 9
- RedHat Enterprise Linux 10

Employees assigned Intune licenses can enroll their personal Linux devices into Microsoft Intune whenever they want. During enrollment, their device is registered with Microsoft Entra ID and evaluated for compliance. If you've applied a Conditional Access policy to Edge, users will be prompted to enroll their devices before they can access Microsoft 365 web apps with their work account.

As an Intune administrator, you don't need to do anything to enable enrollment for employees, other than what's described under [Prerequisites](platform-guide-linux#step-1-prerequisites). However, it's important to provide them with help resources in case they need guidance during enrollment.

Important

Versions 2.0.2 and later of the Microsoft Identity Broker included with the Microsoft Intune app for Linux introduce a major architectural change from the previous Java-based broker. When Linux devices update from earlier broker versions, Intune automatically re‑registers and re‑enrolls those devices and creates new Intune device IDs and Microsoft Entra device IDs for them. After devices update, be sure to review device‑based assignments, filters, and Microsoft Entra ID group memberships that rely on device IDs to ensure that policies apply correctly.

Tip

If you require device encryption, tell your employees prior to device enrollment so that, when possible, they can opt to encrypt their device during OS installation. It's easier and faster than encrypting the device after OS installation. Additionally, make your organization's operating system requirements and password complexity requirements easy to find on your website or in an onboarding email so that employees don't have to delay enrollment to seek out that information.

| Task | Detail |
| --- | --- |
| [Install Microsoft Intune app for Linux](../user-help/company-portal/intune-app-linux) | Employees must install the Microsoft Intune app on their personal device for enrollment. This article describes how to install, update, and remove the Microsoft Intune app for Linux in the Terminal app. |
| [Install Microsoft Edge web browser](https://www.microsoft.com/edge) | To access protected websites and files, employees must have Microsoft Edge web browser, version 102.*X* or later. After they enroll their device, employees can sign in to Microsoft Edge with their work account and access websites and files. |
| [Enroll Linux device in Intune](../user-help/enrollment/enroll-linux) | This article is for device users and describes how to enroll a device with the Microsoft Intune app, and includes system requirements, prerequisites, and next steps. During this step, Microsoft Intune registers the device with Microsoft Entra ID and creates a device record in Intune. After registration is complete, device compliance checks begin. |
| [Check device status and resolve compliance issues](../user-help/compliance/validate-status-linux) | This article is for device users and describes how to resolve compliance issues in the Microsoft Intune app. Compliance checks happen during enrollment and thereafter when the device checks in with Intune. The Intune app notifies employees when they have a noncompliant setting on their device. Intune determines compliance and actions for noncompliance by using your device compliance and Conditional Access policies. |