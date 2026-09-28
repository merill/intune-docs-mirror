---
layout: Conceptual
title: Multiple Managed Accounts for App Protection Policies - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/app-management/protection/multiple-managed-accounts
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: nicholasswhite
ms.author: nwhite
ms.collection:
- M365-identity-device-management
- highpri
ms.subservice: apps
description: Learn how the Multiple Managed Accounts (MMA) feature in Microsoft Intune MAM enables users to manage more than one work or school account within a single app.
ms.date: 2026-05-15T00:00:00.0000000Z
ms.topic: concept-article
ms.reviewer: cdemello
ai-usage: ai-assisted
locale: en-us
document_id: 08af3751-973d-d158-50ac-676be06ab150
document_version_independent_id: 08af3751-973d-d158-50ac-676be06ab150
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/app-management/protection/multiple-managed-accounts.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: app-management/protection/multiple-managed-accounts
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/app-management/protection/multiple-managed-accounts.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/3e34b70d-bca0-4369-a01b-71d1edfd427b
- https://authoring-docs-microsoft.poolparty.biz/devrel/63959238-cb90-4871-a33d-4a5519097e47
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/8ca32b3f-fa14-46df-b09a-9c4a591d6396
- https://authoring-docs-microsoft.poolparty.biz/devrel/78d87f42-5582-4a6b-90be-7db2f12b34e6
platformId: ca69a43f-5ae3-6855-4e8c-45c04290ee54
---

# Multiple Managed Accounts for App Protection Policies - Microsoft Intune | Microsoft Learn

The Multiple Managed Accounts (MMA) feature in Intune mobile application management (MAM) enables users to add and manage more than one MAM-enabled account within a single app. With MMA, app protection policies are enforced independently for each account, as defined by the admin. This is especially useful for scenarios such as consultants working across organizations, company acquisitions, or users managing multiple mailboxes within the same tenant.

Note

This feature is rolling out gradually and may not yet be available in your tenant.

## Key scenarios

- A consultant with managed accounts in two organizations can access both within the same app, with each account governed by its own app protection policy.
- Employees in transition (for example, during mergers) can use multiple managed accounts across tenants.
- Help desk or shared mailbox users can manage multiple accounts in the same tenant.

## Supported account types and apps

The following account configurations are supported with MMA:

- One account can be MDM+MAM managed; additional accounts are MAM-only. Multiple MDM isn't supported.
- All accounts can be MAM-only.
- Only apps that support multiple identities are in scope. For example, PowerApps is out of scope.

### Currently supported apps

Support for additional apps and platforms is coming soon.

| App | Platform | Minimum version |
| --- | --- | --- |
| Microsoft Teams | iOS/iPadOS | v8.10.0 or later |
| Microsoft Outlook | iOS/iPadOS | v5.2626.0 or later |

## Segmented views and mixed views

Apps that support MMA handle multiple managed accounts in one of two ways:

- **Segmented view**: The app shows data for one account at a time. All views are in the context of a single user, and the user switches between accounts. Policy enforcement (PIN, conditional launch, data transfer) applies to the active account. Teams is an example of a segmented view app.
- **Mixed view**: The app displays data from multiple accounts in a shared view, such as a combined inbox or calendar. Policy enforcement for app access and conditional launch applies when the app opens, and the policies for each account are evaluated independently. Outlook is an example of a mixed view app.

Important

Mixed views always enforce a full lockdown (most restrictive behavior), regardless of individual account policies. In a mixed view, cut, copy, and paste are fully blocked (including within the app view), screen capture and screenshots are blocked, and other data protection controls default to the most restrictive behavior. This applies even if a single managed account policy would otherwise allow these actions.

This behavior change also affects scenarios when there's a single managed account with unmanaged accounts in a mixed view (for example, an Outlook inbox or calendar).

## Frequently asked questions

### General

#### What is MMA from an admin perspective?

MMA allows supported apps to sign in with multiple managed identities in the same app instance. This is a capability, not a standalone policy setting, and requires app participation. Admins should expect MMA behaviors only in apps that explicitly support it.

#### Which apps support MMA?

Only apps that have completed MMA integration support multiple managed identities. Admins should verify app support and version requirements before troubleshooting MMA behavior. See Currently supported apps for the list.

#### Are Intune-wrapped apps supported?

No. MMA isn't supported for wrapped apps. Only apps integrated with the Intune SDK are in scope.

### Identity and sign-in behavior

#### Can users sign in with multiple managed accounts in all apps?

No. Users can sign in with multiple managed identities only in MMA-enabled apps. In apps that don't support MMA (single-identity or legacy multi-identity apps), users are limited to one managed account per app per app publisher. Attempting to add another managed account might prompt the user to remove an existing account.

#### What happens on MDM-enrolled devices?

On MDM-enrolled devices, MMA-enabled apps can sign in with managed accounts that don't match the MDM enrollment account. This behavior is expected when MMA is enabled. Non-MMA apps continue to require the MAM account to align with the MDM account when applicable.

### Limiting MMA usage

MMA doesn't currently provide first-class admin controls to explicitly enable or disable multiple managed accounts. However, some existing platform or MAM settings can indirectly restrict MMA behavior because they control account sign-in eligibility or app-level enforcement.

Platform-specific behavior applies:

- **iOS**: Enabling `IntuneMAMAllowedAccountsOnly` restricts an app to a single managed account on managed devices. While this setting wasn't designed for MMA, its effect is that MMA is effectively disabled, even in apps that otherwise support MMA.

### Biometrics and PIN

#### How are biometric and PIN prompts handled with multiple accounts?

- If all managed accounts require biometrics, the user is prompted once, based on the admin-configured prompt frequency.
- If accounts have different requirements (for example, one PIN, one biometric), users might see separate prompts for each method.
- Prompts are governed by admin configuration.

### Keyboards

#### How do third-party keyboards work with MMA?

- **iOS**: Third-party keyboards are blocked at the app level. This behavior is identity-agnostic and applies to all accounts, regardless of MMA or view type.

### Mobile Threat Defense (MTD)

#### How does MTD work with multiple managed accounts?

MTD device threat level is evaluated at the device level, not per managed account. The device threat level is associated with the Microsoft Entra device record (device ID), which affects how MTD behaves when multiple managed accounts are used.

**Same tenant scenarios**: If multiple managed accounts from the same tenant use the same MTD provider, they share the same device record. When one account signs into the MTD app and reports device threat level, all managed accounts from that tenant on the device might report the same device threat level. While the threat level might be shared, each managed account's app protection policy is evaluated independently, and the outcome is determined per account.

**Cross-tenant scenarios**: If managed accounts from different tenants use the same MTD provider, each tenant has a separate device record. In this case, an MTD provider might support multiple accounts by reporting device threat level separately for each tenant.

Important

MTD behavior depends on how the MTD provider integrates with Microsoft Entra ID and reports device threat level per Entra device record (device ID). Admins should validate supported MMA scenarios and security requirement handling with their MTD vendor before relying on MTD enforcement for multiple managed accounts.

## Troubleshooting

### A user can't add a second managed account

- Check whether the **Allow org accounts only** setting on iOS is restricting the ability to add a second managed account.
- Verify the user is attempting to sign in to an app that supports MMA. See Currently supported apps.

### Policies look more restrictive than expected

- Check whether the user is in a mixed view. Mixed views always enforce full lockdown (most restrictive) behavior.

### Logging support tickets

- For issues occurring on a managed device, support tickets must be logged from the tenant that manages the device.