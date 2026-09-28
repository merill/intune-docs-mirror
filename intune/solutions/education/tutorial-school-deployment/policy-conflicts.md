---
layout: Conceptual
title: Avoid policy conflicts - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/solutions/education/tutorial-school-deployment/policy-conflicts
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: scottbreenmsft
ms.author: scbree
ms.subservice: education
description: Learn how to avoid policy conflicts when creating and deploying new policies.
ms.date: 2024-07-11T00:00:00.0000000Z
ms.topic: tutorial
locale: en-us
document_id: 1a92dd42-8e55-53da-4bf4-a6e25c63de68
document_version_independent_id: 1a92dd42-8e55-53da-4bf4-a6e25c63de68
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/solutions/education/tutorial-school-deployment/policy-conflicts.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: solutions/education/tutorial-school-deployment/policy-conflicts
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/solutions/education/tutorial-school-deployment/policy-conflicts.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 4181b90e-7be8-fcbc-514d-9042ba4d0833
---

# Avoid policy conflicts - Microsoft Intune | Microsoft Learn

![](../../../media/icons/16/check.svg) Ensure policies apply effectively to devices

Devices and users targeted with the same setting from different policies cause conflicts. When conflicts occur, Intune generates an error and doesn't apply either setting. As a result, it's important to avoid or resolve conflicts to ensure the correct configuration is applied. Use the steps in this document when creating new policies to avoid or resolve policy conflicts.

Note

If you only use Intune for Education to manage your devices, you can easily update the settings or apps that you have deployed to existing groups or create new groups to apply new policies or apps. You don't need to do anything extra to prevent conflicts if the members of the new groups are different from the members of the existing groups.

## 1. Determine which users or devices need the new policy

Review the existing Microsoft Entra ID groups and determine if they're applicable for the new policy. Otherwise, create a new group and add users or devices.

## 2. Identify and review potentials sources of conflict

The key to avoiding policy conflicts is to understand if existing policies targeted at the same set of users or devices contain the same settings. If a new policy has settings that overlap with existing ones for the same users or devices, either exclude those users or devices from the old policies or remove the overlapping settings.

You can exclude groups of devices or users using the "exclude group" option or by excluding devices using [filters](../../../fundamentals/filters/overview).

Tip

For more information about grouping and targeting, see [Plan Education device grouping and targeting](grouping-and-targeting).

### Default policies for Education tenants

When Intune licenses are added to an Education tenant for the first time, a set of default policies are created. These policies can be viewed in the Configuration policies list in the Intune admin center. They should be reviewed for overlapping settings to determine if exclusions are required when targeting the same set of users or devices. By default, these policies are targeted to *All Devices*.

Default policy names:

- **Devices** &gt; **Windows** &gt; **Configuration**
    - Default Policies for EDU
    - Default Admx policy for EDU
    - Edition Upgrade
    - Shared PC Policy
- **Devices** &gt; **Windows** &gt; **Windows updates** &gt; **Update rings**
    - Windows Update Policy

Note

If you're using Intune for Education, you can see and change these settings by navigating to **Groups** and then selecting the group **All Devices** or **All Users** &gt; **Settings**. Select **Windows device settings** or **iOS device settings**.

### Policies created in the Intune for Education console

When you configure settings in Intune for Education, corresponding policies are created in the Intune service that can be viewed and edited from the Intune admin console. Configuration profiles created by Intune for Education have a recognizable naming template that always starts with the name of the group followed by a suffix based on the template type. The *&lt;GROUP NAME&gt;* part of each name represents the group that was selected in Intune for Education when the settings were configured.

This list provides examples of configuration profiles created by Intune for Education. They should be reviewed for overlapping settings to determine if exclusions are required when targeting the same set of users or devices.

- **Devices** &gt; **Windows** &gt; **Configuration**
    - *&lt;GROUP NAME&gt;* Windows10General
    - *&lt;GROUP NAME&gt;* GroupPolicyConfiguration
    - *&lt;GROUP NAME&gt;* Windows10EndpointProtection
    - *&lt;GROUP NAME&gt;* Windows10CustomDenyAdministrativeApps
    - *&lt;GROUP NAME&gt;* Windows10CustomDenyStore
    - *&lt;GROUP NAME&gt;* Windows10SharedPC
    - *&lt;GROUP NAME&gt;* Windows10EnterpriseModernAppManagement
    - *&lt;GROUP NAME&gt;* ConfigurationPolicy
- **Devices** &gt; **Windows** &gt; **Enrollment** &gt; **Windows Autopilot/Deployment Profiles**
    - *&lt;GROUP NAME&gt;* Windows10AutopilotProfile
- **Devices** &gt; **Windows** &gt; **Windows updates** &gt; **Update rings**
    - *&lt;GROUP NAME&gt;* Windows10UpdatesForBusiness
- **Devices** &gt; **Windows** &gt; **Windows updates** &gt; **Feature Updates**
    - *&lt;GROUP NAME&gt;* WindowsFeatureUpdates
- **Endpoint security** &gt; **Account protection**
    - *&lt;GROUP NAME&gt;*\_LocalUsersAndGroupsConfig\_EDU

## 3. Assign the policy to target group

Once all the potential sources of conflict are reviewed and any exclusions are configured, you can assign the new policy to the user or device groups. Assign the policy using "Included groups" and optionally use assignment filters.

## 4. Monitoring for policy conflicts

# [Intune](#tab/intune)
You can check for potential policy conflicts by going to **Devices** &gt; **Monitor** &gt; **Configuration policy assignment failure**. Find the new policy and review any conflicts in the report. The report can also be exported to CSV.

# [Intune for Education](#tab/intune-for-education)
You can check for potential policy conflicts by going to **Reports** &gt; **Settings error**.

---

If a conflict is found, remove the overlapping settings from the new policy or exclude the targeted users or devices from existing policies.