---
layout: Conceptual
title: Step 3. Integrate Mobile Threat Defense for App Protection Policy - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/solutions/edge-data-security/threat-defense-step-3
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: nicholasswhite
ms.author: nwhite
ms.collection:
- FocusArea_Apps_AppManagement
ms.reviewer: samarti
ms.subservice: apps
description: Step 3. Integrate Mobile Threat Defense signals with Microsoft Edge for Business app protection policies in Microsoft Intune.
ms.date: 2026-04-30T00:00:00.0000000Z
ms.topic: how-to
ms.custom: 
locale: en-us
document_id: 4fc4bf3a-0c8e-4bb5-8b1a-6cafc6ac0787
document_version_independent_id: 4fc4bf3a-0c8e-4bb5-8b1a-6cafc6ac0787
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/solutions/edge-data-security/threat-defense-step-3.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: solutions/edge-data-security/threat-defense-step-3
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/solutions/edge-data-security/threat-defense-step-3.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/691e3042-55ad-4ce1-b5e9-649b1cc47b5c
- https://authoring-docs-microsoft.poolparty.biz/devrel/8e3fdb08-a059-4277-98f6-c0e21e940707
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/b7d11190-096c-4ddb-87db-63764f603aac
- https://authoring-docs-microsoft.poolparty.biz/devrel/88291526-9c74-4f87-878c-de0a82134421
platformId: f9f175b0-a5b2-9ec1-9896-43b4703d1ea4
---

# Step 3. Integrate Mobile Threat Defense for App Protection Policy - Microsoft Intune | Microsoft Learn

The Microsoft Mobile Threat Defense (MTD) connector is a feature in Microsoft Intune that creates a channel of communication between Intune and your chosen MTD vendor, regardless of the device’s operating system. There are many supported MTD partners for both Windows and mobile devices. Intune integrates data from an MTD vendor as an information source for device compliance policies, device Conditional Access rules can act on this information to protect corporate resources, such as Exchange and SharePoint online data, by blocking access from compromised devices.

Mobile Application Management (MAM) threat detection can be integrated with various MTD partners, including Windows Security Center. This integration provides a client device health assessment to Intune app protection policies via a service-to-service connector. This assessment supports gating the flow and access to organizational data on personal unmanaged devices.

The health assessment and state includes the following details:

- **User, app, and device identifiers**
- **A predefined health state**
- **The time of last health state update**

Only users enrolled in MAM send health state data. If end users want to stop sending data, they can sign out of their organization account in protected applications. Similarly, administrators can stop data transmission by removing the MTD connector from Microsoft Intune.

## Intune app protection policies

Intune app protection policies help secure organizational data and help ensure client devices are healthy. It also can perform other client health verification via Windows Security Center. This involves designating the Windows Security Center risk level for allowing end users to access corporate resources. In addition, it also involves setting up tenant-based connectors to Microsoft Intune for Windows Security Center.

- **Apps**: Select the apps that you want to target from app protection policies. For this feature set, these apps are blocked or selectively wiped based on device risk assessment from your chosen Mobile Threat Defense vendor.
- **Health Checks**: Under **Device conditions** you can select **Max allowed device threat level**.

Important

Configure your [Mobile Threat Defense connectors](../../device-security/mobile-threat-defense/overview#mobile-threat-defense-partners) before onboarding users to these policies. If your tenant uses both Microsoft Defender for Endpoint and another MTD partner and you don't designate a primary connector, Intune defaults to Microsoft Defender for Endpoint. For guidance on protecting unenrolled devices, see [Mobile Threat Defense for unenrolled devices](../../device-security/mobile-threat-defense/enable-unenrolled-devices).

### Options for the threat level

You can select one of the following threat level values:

- **Secured**: This level is the most secure. The device can't have any threats present and still access company resources. If any threats are found, the device is evaluated as noncompliant.
- **Low**: The device is compliant if only low-level threats are present. Anything higher puts the device in a noncompliant status.
- **Medium**: The device is deemed compliant if the threats found on the device are of low or medium level. If high-level threats are detected, the device is marked as noncompliant.
- **High**: This level is the least secure and allows all threat levels, using Mobile Threat Defense for reporting purposes only. Devices are required to have the MTD app activated with this setting.

### Options for Action

You can select one of the following **Action** options:

- **Block access:** Prevents the users from performing any activity until they're back in compliance.
- **Wipe data:** This removes any information stored in the application related to the corporate data. It doesn't affect personal data on the personal profile.

### Assignments

Assign the policy to groups of users. The devices used by the group's members are evaluated for access to corporate data on targeted apps via Intune app protection.

### Recommended device condition settings

Use the conditional launch settings to maintain progressive security across the Secure Enterprise Browser levels. Configure the following values where the platform supports the setting.

#### Level 1 – Basic

- **Offline grace period (Block access)**: Set to **10080** minutes.
- **Offline grace period (Wipe data)**: Set to **90** days.
- **Max allowed device threat level**: Select **High**, with the **Block access** action.

#### Level 2 – Enhanced

- **Disabled account**: Set to **Block access**.
- **Min OS version**: Enter **10.0.22621.2506** and select **Block access**.
- **Max allowed device threat level**: Select **Low**, with the **Block access** action.
- **Offline grace period (Wipe data)**: Set to **30** days.

#### Level 3 – High

App conditions:

- **Offline grace period (Block access)**: Set to **1440** minutes.
- **Offline grace period (Wipe data)**: Set to **30** days.

Device conditions:

- **Min OS version**: Enter **10.0.22621.2506** and select **Block access**.
- **Max OS version**: Enter **10.0.22641** and select **Warn**.
- **Max allowed device threat level**: Select **Secured**, with the **Block access** action.
- **Device threat level**: Select **High**, with the **Block access** action.
- **Mobile Threat Defense apps**: Set to **Enabled/Required**, with the **Block access** action to enforce broker activation.
- **SafetyNet device attestation**: Set to **Pass**, with the **Block access** action. This option appears for Android devices.
- **Require device lockout remediation**: Set to **Enabled**, with the **Block access** action.

Tip

These thresholds align with the Secure Enterprise Browser framework's Level 3 (High) posture. Use scope tags and assignments to target the correct Entra ID groups for each level.

Important

If you create an app protection policy for any protected app, the device's threat level is assessed. Depending on the configuration, devices that don't meet the configured threat level are either blocked or corporate data is selectively wiped through conditional launch. If blocked, they're prevented from accessing corporate resources until the threat on the device is resolved and reported to Intune by the chosen MTD vendor.

## Configure the MTD Connector

Use the following steps to configure the MTD Connector.

1. Navigate to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Tenant Administrator** &gt; **Connectors and tokens** &gt; **Mobile Threat Defense**.
3. Select **Create** to display the **Add Connector** pane.
4. From the **Select the Mobile Threat Defense connector to setup** dropdown box, select **Windows Security Center**.

    Note

    In this example, you select **Windows Security Center**. For the full list of MTD Partners, see [Mobile Threat Defense partners](../../device-security/mobile-threat-defense/overview#mobile-threat-defense-partners).
5. Select **Create** to create the connector.
6. From the connector list, select the **Windows Security Center** connector to open its edit view, turn on the **Connect Windows devices for MAM** toggle, and save your changes.

Note

The connector's **Connection status** is **Available** after creation, and changes to **Enabled** when you turn on the **Connect Windows devices for MAM** toggle. For more information about each state, see [Connector status](../../device-security/mobile-threat-defense/overview#connector-status).