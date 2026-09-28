---
layout: Conceptual
title: Configure Endpoint protection settings in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/endpoint-security/configure-endpoint-protection
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
- endpoint-protection
- sub-secure-endpoints
ms.subservice: configuration
description: Create Endpoint protection settings when you create a macOS or Windows device profile in Microsoft Intune.
ms.date: 2024-09-19T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: mattcall
locale: en-us
document_id: dd23d4af-c246-0db8-131a-4a1300b6d30d
document_version_independent_id: dd23d4af-c246-0db8-131a-4a1300b6d30d
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/endpoint-security/configure-endpoint-protection.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/endpoint-security/configure-endpoint-protection
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/endpoint-security/configure-endpoint-protection.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 64ef8446-5d92-ef59-7bd3-6916280d98de
---

# Configure Endpoint protection settings in Microsoft Intune - Microsoft Intune | Microsoft Learn

With Intune, you can use device configuration profiles to manage common Endpoint protection security features on devices, including:

- Firewall
- BitLocker
- Allowing and blocking apps
- Microsoft Defender and encryption

For example, you can create an Endpoint protection profile that only allows macOS users to install apps from the Mac App Store. Or, enable Windows SmartScreen when running apps on Windows devices.

Before you create a profile, review the following articles that detail the Endpoint protection settings Intune can manage for each supported platform:

- [macOS settings](ref-endpoint-protection-macos)
- [Windows settings](ref-endpoint-protection-settings-windows)

## Create a device profile containing Endpoint protection settings

Important

The macOS endpoint protection template has been deprecated. Existing policies remain unchanged, but you can no longer create new policies using this template. We recommend using the settings catalog to create new configuration policies for FileVault, Firewall, and System Policy Control (Gatekeeper) payloads. For more information, see [macOS settings catalog](../settings-catalog/).

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** &gt; **Manage devices** &gt; **Configuration** &gt; **Create**.
3. Enter the following properties:

    - **Platform**: Choose the platform of your devices. Your options:

        - **macOS**
        - **Windows 10 and later**
    - **Profile**: Select **Templates** &gt; **Endpoint protection**.
4. Select **Create**.
5. In **Basics**, enter the following properties:

    - **Name**: Enter a descriptive name for the policy. Name your policies so you can easily identify them later. For example, a good policy name might include the profile type and platform.
    - **Description**: Enter a description for the policy. This setting is optional, but recommended.

    Select **Next**.
6. In **Configuration settings**, depending on the platform you chose, the settings you can configure are different. Choose your platform for detailed settings:

    - [macOS settings](ref-endpoint-protection-macos)
    - [Windows settings](ref-endpoint-protection-settings-windows)
7. Select **Next**.
8. In **Assignments**, select the users or groups that will receive your profile. For more information on assigning profiles, see [Assign user and device profiles](../assign-device-profile).

    Select **Next**.
9. In **Applicability Rules**, use the **Rule**, **Property**, and **Value** options to define how this profile applies within assigned groups. Intune applies the profile to devices that meet the rules you enter. For more information about applicability rules, see [Applicability rules](../create-device-profile).

    Select **Next**.
10. In **Review + create**, review your settings. When you select **Create**, your changes are saved, and the profile is assigned. The policy is also shown in the profiles list.

## Add custom Firewall rules for Windows devices

When you configure the Windows Firewall as part of a profile that includes endpoint protection rules for Windows, you can configure custom rules for Firewalls. Custom rules let you expand on the pre-defined set of Firewall rules supported for Windows devices.

When you plan for profiles with custom Firewall rules, consider the following information, which could affect how you choose to group firewall rules in your profiles:

- Each profile supports up to 150 firewall rules. When you use more than 150 rules, create additional profiles, each limited to 150 rules.
- For each profile, if a single rule fails to apply, all rules in that profile are failed and none of the rules are applied to the device.
- When a rule fails to apply, all rules in the profile are reported as failed. Intune cannot identify which individual rule failed.

The Firewall rules that Intune can manage are detailed in the Windows [Firewall configuration service provider](/en-us/windows/client-management/mdm/firewall-csp) (CSP). To review the list of custom firewall settings for Windows devices that Intune supports, see [Custom Firewall rules](ref-endpoint-protection-settings-windows#firewall-rules).

### To add custom firewall rules to an Endpoint protection profile

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** &gt; **Manage devices** &gt; **Configuration** &gt; **Create**.
3. Enter the following properties:

    - **Platform**: Choose **Windows 10 and later**.
    - **Profile**: Select **Templates** &gt; **Endpoint protection**.
4. Select **Create**.
5. In **Basics**, enter the following properties:

    - **Name**: Enter a descriptive name for the policy. Name your policies so you can easily identify them later. For example, a good policy name might include the profile type and platform.
    - **Description**: Enter a description for the policy. This setting is optional, but recommended.

    Select **Next**.
6. In **Configuration settings**, expand **Windows Firewall**. Next, for *Firewall rules*, select **Add** to open the **Create Rule** page.
7. Specify settings for the Firewall rule, and then select **Save** to save it. To review the available custom firewall rule options in documentation, see [Custom Firewall rules](ref-endpoint-protection-settings-windows#firewall-rules).

    1. The rule appears on the *Windows Firewall* page in the list of rules.
    2. To modify a rule, select the rule from the list, to open the **Edit Rule** page.
    3. To delete a rule from a profile, select the ellipsis **(…)** for the rule, and then select **Delete**.
    4. To change the order in which rules display, select the *up arrow, down arrow* icon at the top of the rule list.

    Select **Next**.
8. In **Assignments**, select the device groups that will receive this profile. For more information on assigning profiles, see [Assign user and device profiles](../assign-device-profile).

    Select **Next**.
9. In **Applicability Rules**, use the **Rule**, **Property**, and **Value** options to define how this profile applies within assigned groups. Intune applies the profile to devices that meet the rules you enter. For more information about applicability rules, see [Applicability rules](../create-device-profile).

    Select **Next**.
10. In **Review + create**, review your settings. When you select **Create**, your changes are saved, and the profile is assigned. The policy is also shown in the profiles list.