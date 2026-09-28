---
layout: Conceptual
title: Windows Update Management Overview - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-updates/windows/
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.subservice: protect
description: Learn how to manage Windows updates with Intune. Control update settings, define rollout strategies, and ensure consistent device security across your organization.
ms.date: 2026-03-27T00:00:00.0000000Z
ms.topic: overview
locale: en-us
document_id: ebd63f80-fadd-c5ee-8f98-d94b47fabb70
document_version_independent_id: ebd63f80-fadd-c5ee-8f98-d94b47fabb70
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-updates/windows/index.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-updates/windows/index
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-updates/windows/index.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 0b895f78-1e03-9f6d-9ed0-46b21fef822c
---

# Windows Update Management Overview - Microsoft Intune | Microsoft Learn

Keeping Windows devices secure and up to date is one of the most important responsibilities for any organization. Microsoft Intune provides a **cloud-based approach to Windows update management**, giving you control, predictability, and minimal disruption for users.

This overview explains how Intune manages Windows updates, the policy types available, and how these pieces fit together into a complete update strategy.

## What you can do with Intune

- Configure update settings on devices without managing individual patches.
- Define update rings to control rollout timing and reduce risk.
- Prevent devices from installing new feature versions until you're ready, while still applying security and quality updates.

Intune stores only the policy assignments, not the updates themselves. When you save a policy, Intune sends configuration details to Windows Autopatch, which determines which updates are approved for deployment. Devices download approved updates directly from Windows Update, installing and applying those changes in accordance with Windows Update client policies.

## Windows update management capabilities

The following policy types help you manage Windows updates in Intune:

#### Windows Update client policy

> 
> **![](icons/client-policy.svg)**
> 
> Configures the underlying [Update policy CSP](/en-us/windows/client-management/mdm/policy-csp-update). Intune surfaces these settings through update rings and the Settings Catalog, giving administrators flexibility to apply granular update behaviors at the device level.

#### Update ring policy

> 
> **![](icons/update-ring.svg)**
> 
> Applies Windows Update client policies to groups of devices. Update rings control deferral periods, deadlines, restart behavior, and user experience settings, enabling phased rollout across your environment.

#### Feature update policy

> 
> **![](icons/feature-update.svg)**
> 
> Locks devices to a specific Windows version (for example, Windows 11 24H2). These policies prevent devices from upgrading beyond the targeted release, ensuring consistency and control over major OS upgrades.

#### Quality update policy

> 
> **![](icons/quality-update.svg)**
> 
> Delivers monthly cumulative updates for security and reliability. Supports:
> 
> - **Hotpatch**: Control if eligible devices receive security patches without a reboot.
> - **Expedite policies**: Push critical security updates immediately by overriding deferral settings.
> 

#### Hotpatch security updates

> 
> **![](icons/quality-update.svg)**
> 
> Secures devices more quickly by delivering eligible security patches without a reboot. Rebootless updates are the default way monthly Windows security updates are delivered.

#### Driver update policy

**![](icons/driver-update.svg)**

> 
> Manages the delivery of hardware driver updates from Windows Update. Driver update policies help ensure device compatibility and stability by controlling when and how drivers are installed.

## Windows Autopatch

Windows Autopatch controls which Windows Update content is approved for deployment to Windows devices, keeping them up to date and secure. If a device isn't targeted by an Autopatch policy for a given content type, then all the latest content from Windows Update is deployed.

Microsoft Intune leverages Windows Autopatch to enable the management of feature updates, quality updates, and driver updates. To enable those workflows, there is a policy for each of those content types.

When a device is assigned to a policy, it is enrolled in Autopatch for that content type, and only approved content is deployed to that device. Administrators can approve updates in a policy either automatically or manually, depending on what works best for their organization.

Beyond policy, there are several other powerful Intune features powered by Autopatch:

1. Autopatch Groups enable dynamic device grouping, gradual rollouts of updates, as well as multi-policy creation and edit flows.
2. Autopatch reports provide deep insight into update readiness, compliance, and alerts.
3. For eligible Windows editions, it also enables cloud-powered update scenarios like hotpatch and expedited updates with minimal manual configuration.

The following table compares how update management differs when you use manual Autopatch configuration with policies and using Autopatch Groups:

| **Feature** | **When using Autopatch Policies** | **When using Autopatch Groups** |
| --- | --- | --- |
| **Update coordination** | Manually distribute devices into Entra Groups to assign update policies. | Automate distribution of devices into multiple Entra Groups based on your preferences. Pin specific groups to the start or end of a deployment. |
| **Update ring policy** | You configure update ring policies in Intune to control deferrals, deadlines, and restart behavior. | You configure multiple update rings simultaneously to get a full picture of deferrals, deadlines, and restart behavior across the entire release.Autopatch Groups have optional presets that provide recommended settings for common use cases. |
| **Feature update policy** | You use feature update policies to lock or schedule OS versions. | You set the minimum feature update version for all devices in an Autopatch Group. You schedule gradual feature update rollouts when you want to upgrade. |
| **Quality update policy** | You configure quality update policies, expedited updates, and hotpatch settings manually. | You configure quality update policies, expedited updates, and hotpatch settings manually. |
| **Driver update policy** | You use driver update policies to review and approve drivers either manually or automatically for all assigned devices. | Review and approve drivers either manually or automatically, starting a gradual rollout to all devices in the Autopatch Group. |

### Service Defaults

Windows Autopatch enables hotpatch security updates by default to help secure devices faster. This default behavior applies to all eligible devices in Microsoft Intune. Applying security fixes without waiting for a restart can get organizations to 90% compliance in half the time.

You can opt out of hotpatch security updates at any time for either your whole tenant or groups devices with quality update policies.

## Prerequisites

Each policy type has specific prerequisites, detailed in their respective documentation. In general:

- Devices must be enrolled in Intune.
- Devices must be Microsoft Entra joined or hybrid joined. 

> 
> Microsoft Entra registered devices aren't supported for any policy type that uses the same backend service as Windows Autopatch—including Feature updates, Quality updates, and Driver updates. For Entra registered devices, update management remains limited to Windows Update client policies and update ring policies.
- Devices must have access to Microsoft update endpoints.

Feature update policies, quality update policies, and driver update policies are orchestrated by Windows Autopatch. The prerequisites are the same across these three policy types:

- **Licensing**: A Windows license that includes the [Autopatch entitlement](/en-us/windows/deployment/windows-autopatch/prepare/windows-autopatch-prerequisites#licenses-and-entitlements).

> 
> If you're blocked when creating new policies for capabilities that require Windows Autopatch and you get your licenses to use Windows Update client policies through an Enterprise Agreement (EA), contact the source of your licenses such as your Microsoft account team or the partner who sold you the licenses. The account team or partner can confirm that your tenants' licenses meet the Windows Autopatch license requirements. See [Enable subscription activation with an existing EA](/en-us/windows/deployment/deploy-enterprise-licenses#enable-subscription-activation-with-an-existing-ea).
> 
> Important
> 
> [Enable subscription activation with an existing EA](/en-us/windows/deployment/deploy-enterprise-licenses#enable-subscription-activation-with-an-existing-ea) isn't applicable to GCC and GCC High/DoD cloud environments for Windows Autopatch capabilities.
- **Telemetry**: Diagnostic data set to *Required* level.
- **Services**: Microsoft Account Sign-In Assistant enabled.

> 
> If the service is blocked or set to *Disabled*, it fails to receive the update. For more information, see [Feature updates aren't being offered while other updates are](/en-us/windows/deployment/update/windows-update-troubleshooting#feature-updates-are-not-being-offered-while-other-updates-are). By default, the service is set to *Manual (Trigger Start)*, which allows it to run when needed.