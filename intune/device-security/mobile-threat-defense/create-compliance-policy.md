---
layout: Conceptual
title: Create Mobile Threat Defense compliance policies in Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/create-compliance-policy
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
description: Create an Intune device compliance policy that uses your MTD partner threat levels to determine if a mobile device can access company resources.
ms.date: 2024-09-30T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: f39e90b8-1d1b-4980-8e5a-1a201ce5b63a
document_version_independent_id: f39e90b8-1d1b-4980-8e5a-1a201ce5b63a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-security/mobile-threat-defense/create-compliance-policy.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-security/mobile-threat-defense/create-compliance-policy
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-security/mobile-threat-defense/create-compliance-policy.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: 757481f4-7603-d2da-6f56-6c43b0b06bb7
---

# Create Mobile Threat Defense compliance policies in Intune - Microsoft Intune | Microsoft Learn

Intune supports integrating a Mobile Threat Defense (MTD) partner to help you detect threats and assess risk on mobile devices. With MTD integration, your Intune device compliance policies can use rules to assess a devices risk based on the information from that MTD partner to determine if a device is compliant or not. With compliance policy risk assessed, you can then use [Conditional Access policy](/en-us/entra/identity/conditional-access/policy-all-users-device-compliance) to block access to services from devices that fail to meet the requirements of your device compliance policy.

## Before you begin

Before you create Intune device compliance policies that use MTD partner date, you must complete setup and Integration of that MTD partner with Intune.

View the list of [Mobile Threat Defense partners that Intune supports](overview#mobile-threat-defense-partners) in the *Mobile Threat Defense integration with Intune* article.

- Each link in the supported partner list opens guidance specific to that partner that can help you understand that partners supported the platforms and capabilities.
- Each partner specific article has a companion article that can help you complete the partner integration with Intune and to configure that partner's Intune connector.
- In addition to configuring integration with Intune, use the partner product and console to create policies to classify the threats that the partner identifies. The policies classify threats as having various threat levels like high, medium, and low.

With integration complete and the partner policy in place, you can then create Intune device compliance policies that successfully use the partner threat-level classifications.

## To create an MTD device compliance policy in Intune

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Endpoint security** &gt; **Device compliance** &gt; **Create policy**.
3. Select the **Platform**:

    - For most platforms, the *Profile type* is automatically set. If not automatically set, select the appropriate Profile type.
    - To continue, select **Create**.
4. On **Basics**, specify a device compliance policy **Name**, and **Description** (optional). Select **Next** to continue.
5. On **Compliance settings**, expand and configure **Device Health**. Choose a threat-level from the drop-down list for **Require the device to be at or under the Device Threat Level**.

    - **Clear**: This level is the most secure. The device can't have any threats present and still access company resources. If any threats are found, the device is evaluated as noncompliant.
    - **Low**: The device is compliant if only low-level threats are present. Anything higher puts the device in a noncompliant status.
    - **Medium**: The device is compliant if the threats found on the device are low or medium level. If high-level threats are detected, the device is determined as noncompliant.
    - **High**: This threat level is the least secure as it allows all threat levels and uses Mobile Threat Defense for reporting purposes only. Devices are required to have the MTD app activated with this setting.

    To continue, select **Next**.
6. On the **Actions for noncompliance** tab, specify a sequence of actions to apply automatically to devices that don't meet this compliance policy.

    You can add multiple actions and configure schedules and other details for some actions. For example, you might change the schedule of the default action *Mark device noncompliant* to occur after one day. You can then add an action to send an email to the user when the device isn't compliant to warn them of that status. You can also add actions that lock or retire devices that remain noncompliant.

    For information about the actions you can configure, see [Add actions for noncompliant devices](../compliance/configure-noncompliance-actions), including how to create notification emails to send to your users.
7. On the **Assignments** tab, assign the policy to applicable *user* groups, and then select **Next** to continue.

    Important

    The **Require the device to be at or under the Device Threat Level** setting supports only **user groups**. Targeting *device groups* with this setting is not supported.
8. On the **Review + create** page, when you're done, choose **Create**. The new profile is displayed in the list when you select the policy type for the profile you created.

## Monitoring risk score sent by Mobile Threat Defense partner

Your Mobile Threat Defense partner can send a risk score for each device for which the MTD app is installed. You can view this under **Reports** &gt; **Device compliance** &gt; **Reports** &gt; **Device Compliance**. Make sure **Device threat level** is selected when opening the **Columns** tab, this may require you to hit **Generate** first.

Important

Conditional Access policies for Microsoft 365 or other services also evaluate device compliance results, which include the threat-level configuration. Any noncompliant device can be blocked from accessing corporate resources until that devices threat-level is remediated to bring the device into compliance with your policies and that status is successfully reported to Intune via the MTD vendor.