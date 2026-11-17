---
layout: Conceptual
title: Google Workspace Sign-in with Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/settings-catalog/require-google-workspace-authentication-android
author: iceorbital
ms.author: acabello
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
ms.collection:
- M365-identity-device-management
ms.subservice: configuration
description: Require Google Workspace authentication on supported corporate-owned and personally owned Android Enterprise devices with Microsoft Intune policies.
ms.topic: how-to
ms.date: 2026-11-12T00:00:00.0000000Z
ai-usage: ai-generated
ms.custom: msecd-doc-authoring-1032
locale: en-us
document_id: 9ba2d20c-4d2e-d646-ad88-cd38ebd0f0da
document_version_independent_id: 9ba2d20c-4d2e-d646-ad88-cd38ebd0f0da
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/settings-catalog/require-google-workspace-authentication-android.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/settings-catalog/require-google-workspace-authentication-android
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/settings-catalog/require-google-workspace-authentication-android.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: c106a6ac-53a1-1e2f-ed5d-224e5240c195
---

# Google Workspace Sign-in with Microsoft Intune - Microsoft Intune | Microsoft Learn

Use a Microsoft Intune device configuration policy to require users to authenticate with a managed Google Account from your organization's Google Workspace domain. This policy gives users access to the Google apps and services assigned to their organizational account.

This feature supports corporate-owned fully managed devices, corporate-owned devices with a work profile, and personally owned devices with a work profile. Use the settings catalog for supported corporate-owned devices and a device configuration template for personally owned devices with a work profile. Corporate-owned dedicated devices aren't supported because they aren't associated with an individual user.

After a user authenticates, the managed Google Account replaces the device's managed Google Play account. The policy doesn't change the Microsoft Entra account associated with the managed device.

Before you create the policy, prepare a managed Google domain enterprise and managed Google Accounts. Review the prerequisites for domain verification and administrator roles.

## Prerequisites

- A managed Google domain enterprise connected to Intune. Upgrade an existing Managed Google Play enterprise if required. For connection and upgrade steps and required Intune permissions, see [Connect Intune to managed Google Play](../../device-enrollment/android/connect-managed-google-play#upgrade-to-a-managed-google-domain). The administrator performing the upgrade also needs the **Super Admin** role in Google Workspace during the upgrade.
- A verified Google Workspace domain. For instructions, see [Verify your domain for Google Workspace](https://knowledge.workspace.google.com/admin/domains/verify-your-domain-for-google-workspace).
- Managed Google Accounts for the users who receive the policy, in the enterprise's Google Workspace domain. If accounts don't exist, follow the **Domain verified** instructions in [Add an account for a new user](https://knowledge.workspace.google.com/admin/users/add-an-account-for-a-new-user).
- An Intune account with at least the **Policy and Profile Manager** role to create the device configuration policy.

## Create and assign the policy

For personally owned devices with a work profile, you must use a device configuration template instead of the settings catalog. For template creation and assignment steps, see [Create a device restrictions profile](../templates/configure-device-restrictions).

The following settings catalog steps apply to corporate-owned fully managed devices and corporate-owned devices with a work profile.

Assign the policy to groups containing the users who need to authenticate with managed Google Accounts. You can assign it before enrollment or to devices that are already enrolled. If assigned before enrollment, the authentication prompt appears after enrollment. For an enrolled device, the prompt appears after the device receives the policy.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Go to **Devices** &gt; **Manage devices** &gt; **Configuration** &gt; **Create** &gt; **New policy**.
3. Select the following properties, and then select **Create**:
    - **Platform**: **Android Enterprise**
    - **Profile type**: **Settings catalog**
4. In **Basics**, enter a name and an optional description, and then select **Next**.
5. In **Configuration settings**, select **Add settings**, and open **Device restrictions** &gt; **Users and Accounts**.
6. Select **Require users to authenticate with a Google Workspace account**, and close the settings picker.
7. Set the setting to **True**, and then select **Next**.
8. In **Scope tags**, optionally assign scope tags, and then select **Next**.
9. In **Assignments**, select the groups containing the users who need the policy, and then select **Next**.
10. In **Review + create**, review the policy, and then select **Create**.

For more information about creating policies, see [Use the Intune settings catalog to configure settings](./).

## Complete authentication on the device

After the device receives the policy, ask the user to complete these steps:

1. Open the **Sign in with your work account** prompt on the device.
2. Add a managed Google Account from your organization's enterprise domain, and complete authentication.

Until authentication is complete, the setting reports **Error** in Intune, and the Gmail app, if present, is disabled. This setting's noncompliance doesn't change the device's overall compliance state.

For user-facing instructions, see [Sign in with your Google Workspace account](../../user-help/enrollment/enroll-intune-app-android#sign-in-with-your-google-workspace-account).

## Verify deployment

Review the policy's reports and confirm that the user completed authentication.

1. In the Intune admin center, go to **Devices** &gt; **Manage devices** &gt; **Configuration** &gt; **Policies**.
2. Select the policy, and review **Device and user check-in status**, **Device assignment status**, and **Per setting status**.
3. If the setting reports **Error**, check whether the user has completed the authentication prompt.
4. After authentication, confirm that the managed Google Account is available on the device.