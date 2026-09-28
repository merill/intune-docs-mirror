---
layout: Conceptual
title: Enable the Mobile Threat Defense connector for unenrolled devices - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/enable-unenrolled-devices
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
- sub-mtd-apps
ms.reviewer: ilwu
ms.subservice: protect
description: Enable the Mobile Threat Defense connector in Microsoft Intune for unenrolled devices.
ms.date: 2024-08-20T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 0b33177b-995e-b2dd-5399-270beed2c713
document_version_independent_id: 0b33177b-995e-b2dd-5399-270beed2c713
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-security/mobile-threat-defense/enable-unenrolled-devices.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-security/mobile-threat-defense/enable-unenrolled-devices
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-security/mobile-threat-defense/enable-unenrolled-devices.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/8b9ae643-2e85-42b8-beb2-eef4bae8c4bc
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/e047e27d-b5f3-43a8-b4b0-4f6dca95e7c9
platformId: e6b4f6d1-67a8-c37b-4ecf-fb4b42a6b1df
---

# Enable the Mobile Threat Defense connector for unenrolled devices - Microsoft Intune | Microsoft Learn

During Mobile Threat Defense (MTD) setup, you've configured a policy for classifying threats in your Mobile Threat Defense partner console and you've created the app protection policy in Intune. If you've already configured the Intune connector in the MTD partner console, you can now enable the MTD connection for MTD partner applications.

Note

This article applies to all Mobile Threat Defense partners that support app protection policies:

- Better Mobile (Android, iOS/iPadOS)
- BlackBerry Mobile (CylancePROTECT for Android, iOS/iPadOS)
- Check Point Harmony Mobile (Android, iOS/iPadOS)
- Jamf (Android, iOS/iPadOS)
- Lookout for Work (Android, iOS/iPadOS)
- Microsoft Defender for Endpoint (Android, iOS/iPadOS, Windows)
- SentinelOne (Android, iOS/iPadOS)
- Symantec Endpoint Security (Android, iOS/iPadOS)
- Trellix Mobile Security (Android, iOS/iPadOS)
- Windows Security Center (Windows) - *For information about the Windows versions that support this connector, see [Data protection for Windows MAM](../../app-management/protection/enable-mam-windows).*
- Zimperium (Android, iOS/iPadOS)

## Classic Conditional Access policies for Mobile Threat Defense (MTD) apps

When you integrate a new Mobile Threat Defense application with Intune and enable the connection to Intune, Intune creates a classic Conditional Access policy in Microsoft Entra ID. Each third-party MTD partner you integrate with creates a new classic Conditional Access policy. These policies can be ignored, but shouldn't be edited, deleted, or disabled.

Note

As of the August 2023 Intune service release (2308), classic Conditional Access (CA) policies are no longer created for the **Microsoft Defender for Endpoint** connector. If your tenant has a classic CA policy that was previously created for integration with Microsoft Defender for Endpoint, it can be deleted. Classic CA policies continue to be needed for 3rd party MTD partners.

If the classic policy is deleted, delete the connection to Intune that was responsible for its creation and then set it up again. This process recreates the classic policy. It isn't supported to migrate classic policies for MTD apps to the new policy type for Conditional Access.

Classic Conditional Access policies for MTD apps:

- Are used by Intune MTD to require that devices are registered in Microsoft Entra ID, and that they have a device ID before they communicate with the MTD partner. The ID is required so that devices and can successfully report their status to Intune.
- Have no effect on any other Cloud apps or Resources.
- Are distinct from Conditional Access policies you might create to help manage MTD.
- By default, don't interact with other Condition

To view classic Conditional Access policies, in [Azure](https://portal.azure.com/#home), go to **Microsoft Entra ID** &gt; **Conditional Access** &gt; **Classic policies**.

## To enable the Mobile Threat Defense connector

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Tenant administration** &gt; **Connectors and tokens** &gt; **Mobile Threat Defense**. To set up an integration with a third-party Mobile Threat Defense vendor, your account must be assigned the *Endpoint Security Manager* built-in admin role for Intune, or be assigned a custom role that includes the *Read* and *Modify* rights for the Intune *Mobile Threat Defense* permission.
3. On the **Mobile Threat Defense** pane, select **Add**.
4. For **Mobile Threat Defense connector to setup**, select your MTD partner solution from the drop-down list..
5. Enable the toggle options according to your organization's requirements. The toggle options that are visible can vary depending on the MTD partner.

## Mobile Threat Defense toggle options

Note

Ensure your tenant's MDM Authority is [set to Intune](../../fundamentals/setup-mdm-authority#set-mdm-authority-to-intune) to see the full list of toggle options.

You can decide which MTD toggle options you need to enable according to your organization's requirements. Here are more details:

**App Protection Policy Settings**:

- **Connect Android devices of version 4.4 and above to *&lt;MTD partner name&gt;* for app protection policy evaluation**: When you enable this option, app protection policies using the Device Threat Level rule evaluate devices including data from this connector.
- **Connect iOS devices version 11 and above to *&lt;MTD partner name&gt;* for app protection policy evaluation**: When you enable this option, app protection policies using the Device Threat Level rule evaluate devices including data from this connector.

**Common Shared Settings**:

- **Number of days until partner is unresponsive**: Number of days of inactivity before Intune considers the partner to be unresponsive because the connection is lost. Intune ignores compliance state for unresponsive MTD partners.

Tip

You can see the **Connection status** and the **Last synchronized** time between Intune and the MTD partner from the Mobile Threat Defense pane.