---
layout: Conceptual
title: Collect Device Properties With Intune Properties Catalog - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/collect-device-properties
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.collection:
- M365-identity-device-management
ms.subservice: configuration
description: Use Microsoft Intune properties catalog to collect device properties—including hardware, registry values, and security signals—from Windows devices.
ms.date: 2026-07-01T00:00:00.0000000Z
ms.topic: how-to
ai-usage: ai-assisted
ms.custom: msecd-doc-authoring-1018
ms.reviewer: abbystarr, madisoncooks
locale: en-us
document_id: ec88de52-6789-60f2-ebee-8569645d426b
document_version_independent_id: ec88de52-6789-60f2-ebee-8569645d426b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/collect-device-properties.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/collect-device-properties
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/collect-device-properties.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: d0b82056-01bc-078d-d535-d927bad40028
---

# Collect Device Properties With Intune Properties Catalog - Microsoft Intune | Microsoft Learn

In Microsoft Intune, use the **properties catalog** to collect device properties—including hardware details, configuration data, and application signals—from managed Windows devices.

For example, you can:

- Discover local AI agents, like OpenClaw, running on your Windows devices.
- Collect selected Windows registry key values from managed Windows devices, such as configuration settings, application state, or security posture signals.
- Get the BIOS version and TPM status to identify devices that might need firmware updates or aren't compliant with security policies.
- Identify devices that lack encryption, which might violate security policies.
- Identify devices that need to be replaced based on hardware properties, like disk size or memory.
- Detect outdated firmware or hardware that could expose vulnerabilities.
- Collect battery health information to help monitor device performance and lifespan.
- Retrieve network adapter configurations to troubleshoot connectivity issues.

This visibility helps you make informed decisions about device compliance, lifecycle management, and troubleshooting.

In this article, you'll learn how to create a properties catalog policy, view the collected data, and explore the available hardware properties. After creating a profile, you can assign it to your Windows devices.

## Prerequisites

![](../media/icons/16/devices.svg)**Device platform requirements**

> 
> This feature supports Windows devices only.
> 
> On Android and Apple devices, device properties are collected automatically.

![](../media/icons/16/configuration.svg)**Device configuration requirements**

> 
> This feature supports devices that are:
> 
> - Managed by Intune
> - Co-managed (Intune + Configuration Manager)
> - Microsoft Entra joined
> - Microsoft Entra hybrid joined
> 

![](../media/icons/16/rbac.svg)**Roles requirements**

> 
> Role requirements vary based on the tasks being performed.
> 
> To configure the properties catalog policy, use an account with at least one of the following Intune roles:
> 
> - [Policy and Profile Manager](../fundamentals/role-based-access-control/ref-built-in-roles#policy-and-profile-manager)
> - A [custom role](../fundamentals/role-based-access-control/create-custom-role)that includes the permissions:
>     - **Organization/Read** and **Managed Devices/Read** — Required for device visibility.
>     - **Device configurations/Create, Read, Assign** — Required to create and assign the data collection policy.
> 
> 
> To view the collected data, use an account with the permission **Managed Devices/Read**.

## Available and required properties

You can collect the following properties. To learn more about the different properties, see [Intune Data Platform Schema](../advanced-analytics/ref-data-platform-schema).

When you create the policy, select any of the following property categories to collect. The **required** properties are automatically collected when you collect any property in that category.

| Category | Required properties |
| --- | --- |
| Application Properties | App NameApp VersionArchitecturesInstall ScopeInstall Scope Platform User IDInstall Scope User IDPublisher |
| Battery | Instance Name |
| Bios Info | Bios NameSoftware Element IDSoftware Element StateTarget Operating System |
| CPU | Processor ID |
| Disk Drive | Drive ID |
| Encryptable Volume | Volume ID |
| Local AI Agent | Agent NameInstall LocationInstall Scope Microsoft recommends collecting **Host process**, as OpenClaw can run in different process names, like `node.exe`, `wsl.exe`, etc. |
| Logical Drive | Drive Identifier |
| Memory Info | — |
| Network Adapter | Identifier |
| OS Version | — |
| Sim Info | Windows eSIM ID |
| Registry | Registry keys |
| System Enclosure | Serial Number |
| System Info | — |
| Time | — |
| TPM | — |
| Video Controller | Identifier |
| Windows QFE | Hot Fix ID |

## Create the collection policy

Use the following steps to create a properties catalog profile and assign it to your Windows devices.

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Devices** &gt; **Windows**.
2. Under **Manage devices**, select **Configuration** &gt; **Create** &gt; **New Policy**.
3. Select the following properties and select **Create**:

    - **Platform**: Select **Windows 10 and later**.
    - **Profile type**: Select **Properties catalog**.
4. In **Basics**, enter the following properties and select **Next**:

    - **Name**: Enter a descriptive name for the new profile.
    - **Description**: Enter a description for the profile. This setting is optional, but recommended.
5. Select **Add properties** and select the properties you want to collect. You can select multiple properties from multiple categories.

    Some required properties are automatically added. For a list, see Required properties.

    Select **Next**.
6. Optional. In **Scope (Tags)**, select any scope tags you want to assign to the profile. To learn more about scope tags, see [Use scope tags for distributed IT](../fundamentals/role-based-access-control/scope-tags).

    Select **Next**.
7. In **Assignments**, select the groups that receive this profile. For more information on assigning profiles, see [Assign policies in Microsoft Intune](assign-device-profile).

    Select **Next**.
8. In **Review + create**, review your settings, and select **Create**.

When you select **Create**, the profile is assigned to the groups you specified. The profile is also created and shown in the list. The next time each device checks in with the Intune service, the policy applies.

Note

It can take up to 24 hours for the initial collection of inventory data.

## View collected data

Use the following steps to view the collected device inventory information:

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Devices** &gt; **Windows**.
2. From the devices list, select a device.
3. Under **Tools**, select **Device Inventory**.
4. Select a category to view the collected information.

## Feature details and usage

**Local AI agent**

> 
> Helps you discover OpenClaw running on your Windows devices. After you deploy the properties catalog policy and start collecting data, the next steps are:
> 
> - Use [Device Query](../advanced-analytics/device-query-multiple-devices) to view devices with a Local AI Agent.
> - Use the [Local AI Agent Baseline - OpenClaw](../device-security/security-baselines/ref-openclaw-settings) to block users from using OpenClaw.
> 

**Registry key inventory**

> 
> Lets you collect selected Windows registry data through the properties catalog for configuration visibility and troubleshooting. Here are some important details about this feature:
> 
> - Supported collection methods include a single value, all values directly under a key (non-recursive), and the same value across immediate subkeys.
> - Registry key inventory isn't intended to collect sensitive or confidential values and includes detection logic to help prevent potentially sensitive values from being ingested. If a value is flagged as potentially sensitive, it isn't collected.
> - To view collected registry data, use Device Inventory. Registry key inventory is accessible through existing device inventory permissions and may expose missed sensitive device configuration information; this is an accepted risk, and organizations should review security and privacy implications before enabling broad access.
> - Initial release limitations include HKLM-only collection and enforced value (6KB) and per-device (100 registry keys) collection limits.
> 

## Stop collecting properties

You can stop (delete) the collection of properties only at the category level. To stop collecting properties, go to the **properties catalog** profile, and remove the collection for every property in the category.

Note

If you delete a properties catalog policy, you can see the last-collected data in Device Inventory for up to 28 days.

## Troubleshooting

To troubleshoot issues with the properties catalog, review the client logs at `C:\Program Files\Microsoft Device Inventory Agent\Logs`. You can also collect the logs by using the [Device Action: Collect Diagnostics](../device-management/actions/collect-diagnostics).