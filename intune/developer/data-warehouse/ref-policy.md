---
layout: Conceptual
title: Reference for Policy Entities - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/developer/data-warehouse/ref-policy
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: nicholasswhite
ms.author: nwhite
ms.collection:
- M365-identity-device-management
ms.reviewer: jamiesil
ms.subservice: developer
description: Reference topic for the Policy category of entity collections in the Intune Data Warehouse API.
ms.date: 2024-10-30T00:00:00.0000000Z
ms.topic: reference
locale: en-us
document_id: 54bbba4c-8640-f37d-bf77-50afa616efe7
document_version_independent_id: 54bbba4c-8640-f37d-bf77-50afa616efe7
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/developer/data-warehouse/ref-policy.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: developer/data-warehouse/ref-policy
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/developer/data-warehouse/ref-policy.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/80beb97b-18aa-44f8-9420-8f2a4cd448eb
- https://authoring-docs-microsoft.poolparty.biz/devrel/e0ffb20c-01c6-407b-a9bd-29111652a1dc
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/8c09e0ef-0fde-4b6d-bf1b-b517e4db7f80
- https://authoring-docs-microsoft.poolparty.biz/devrel/3904bce4-d817-48cf-85fd-b6146fca83b7
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
platformId: f2286d4c-3c21-6bd0-4cdd-246d24f0b86e
---

# Reference for Policy Entities - Microsoft Intune | Microsoft Learn

The **policies** category contains entities for mobile devices that track information such as:

- Inventory of device configuration profiles, app configuration profiles, and compliance policies
- Number of devices in the succeeded, pending, failed, or error state per day
- Number of users in the succeeded, pending, failed, or error state per day
- Cumulative number of devices in the succeeded, pending, failed, or error state

## policies

The **policy** entity lists device configuration profiles, app configuration profiles, and compliance policies. You can assign the policies with Mobile Device Management (MDM) to a group in your enterprise.

| Property | Description | Example |
| --- | --- | --- |
| policyKey | Unique Key to represent the policy in the data warehouse. | 123 |
| policyId | Unique identifier of the Policy in the data warehouse. | b66bc706-ffff-7437-0340-032819502773 |
| policyName | Name of the Policy. | "Windows 10 Baseline" |
| policyVersion | Version of the Policy. When the policy is edited or changed, a newer version is created. | 1, 2, 3 |
| isDeleted | Indicates whether the Policy record has been updated. True- policy has a new record with updated fields. False- the latest record for the policy. | True/False |
| startDateInclusiveUTC | Date and time in UTC when the policy was created in the data warehouse. | 11/23/2016 12:00:00 AM |
| deletedDateUTC | Date and time in UTC when IsDeleted changed to True. | 11/23/2016 12:00:00 AM |
| rowLastModifiedDateTimeUTC | Date and time in UTC when the policy was last modified in the data warehouse. | 11/23/2016 12:00:00 AM |

## policyTypes

The **policyType** entity lists types of device configuration profiles, app configuration profiles, and Compliance policies. You can assign the policies with Mobile Device Management (MDM) to a group in your enterprise.

| Property | Description | Example |
| --- | --- | --- |
| policyTypeId | Unique identifier of the policy in the source system. | 123 |
| policyTypeKey | Unique identifier of the policy in the data warehouse. | 1 |
| policyTypeName | Name of the policy type. | Windows 10 Compliance policy. |

## Device Configuration

The **deviceConfigurationProfileDeviceActivity** entity lists the number of **devices** in the succeeded, pending, failed, or error state per day. The number reflects the Device configuration profiles assigned to the entity. For example, if a **device** is in the succeeded state for all its assigned policies, it increments the succeeded counter up one for that day. If a device has two profiles assigned to it, one in the succeeded state and another in an error state, the entity increments the Succeeded counter and place the device in the error state. The entity lists how many devices are in which state on a given day over the last 30 days.

| Property | Description | Example |
| --- | --- | --- |
| dateKey | Date Key when the Device Configuration Profile check-in was recorded in the data warehouse. | 20160703 |
| pending | Number of unique Devices in pending state. | 123 |
| succeeded | Number of unique Devices in success state. | 12 |
| error | Number of unique Devices in error state. | 10 |
| failed | Number of unique Devices in failed state. | 2 |

The **deviceConfigurationProfileUserActivity** entity lists the number of **users** in the succeeded, pending, failed, or error state per day. The number reflects the Device configuration profiles assigned to the entity. For example, if a **user** is in the succeeded state for all their assigned policies, it moves up the succeeded counter by one for that day. If a user has two profiles assigned to them, one in the succeeded state and the other is in an error state, the user in the error state is counted. The **deviceConfigurationProfileUserActivity** entity lists how many users are in which state on a given day over the last 30 days.

| Property | Description | Example |
| --- | --- | --- |
| dateKey | Date Key when the Device Configuration Profile check-in was recorded in the data warehouse. | 20160703 |
| pending | Number of unique Users in pending state. | 123 |
| succeeded | Number of unique Users in success state. | 12 |
| error | Number of unique Users in error state. | 10 |
| failed | Number of unique Users in failed state. | 2 |

## policyTypeActivities

The **policyTypeActivity** entity lists the cumulative number of devices in the succeeded, pending, failed, or error state. It lists these states with respect to a device configuration profile, app configuration profile, or compliance policy per day.

| Property | Description | Example |
| --- | --- | --- |
| dateKey | dateKey when the device Configuration profile check-in was recorded in the data warehouse. | 20160703 |
| policyKey | policyKey, can be joined with policy to get the policyName. | Windows 10 baseline |
| policyTypeKey | Type of Policy Key, can be joined with Policy Type to get the policy type name. | Windows10 Compliance Policy |
| pending | Number of unique devices in pending state. | 123 |
| succeeded | Number of unique devices in success state. | 12 |
| error | Number of unique devices in error state. | 10 |
| failed | Number of unique devices in failed state. | 2 |

## Compliance Policy

The Compliance Policy API Reference contains entities that provide status information about compliance policies assigned to devices.

### compliancePolicyStatusDeviceActivities

The following table summarizes the assignment status of compliance policies to devices. It lists the count of devices found in each compliance state.

| Property | Description | Example |
| --- | --- | --- |
| dateKey | Date key when the summary was created for the compliance policy. | 20161204 |
| unknown | Number of devices that are offline or failed to communicate with Intune or Microsoft Entra ID for other reasons. | 5 |
| notApplicable | Number of devices where device compliance policies targeted by the admin are not applicable. | 201 |
| compliant | Number of devices that successfully applied one or more device compliance policies targeted by the admin. | 4083 |
| inGracePeriod | Number of devices that are not compliant but that are in the grace-period defined by the admin. | 57 |
| nonCompliant | Number of devices that failed to apply one or more device compliance policies targeted by the admin or where the user hasn't complied with the policies targeted by the admin. | 43 |
| error | Number of devices that failed to communicate with Intune or Microsoft Entra ID, and returned an error message. | 3 |

### compliancePolicyStatusDevicePerPolicyActivities

The following table summarizes the assignment status of compliance policies to devices on a per policy and a per policy type basis. It lists the count of devices found in each compliance state for each assigned compliance policy.

| Property | Description | Example |
| --- | --- | --- |
| dateKey | Date key when the summary was created for the compliance policy. | 20161219 |
| policyKey | Key for the compliance policy for which the summary was created. | 10178 |
| policyPlatformKey | Key for the platform type of the compliance policy for which the summary was created. | 5 |
| unknown | Number of devices that are offline or failed to communicate with Intune or Microsoft Entra ID for other reasons. | 13 |
| notApplicable | Number of devices where device compliance policies targeted by the admin are not applicable. | 3 |
| compliant | Number of devices that successfully applied one or more device compliance policies targeted by the admin. | 45 |
| inGracePeriod | Number of devices that are not compliant but that are in the grace-period defined by the admin. | 3 |
| nonCompliant | Number of devices that failed to apply one or more device compliance policies targeted by the admin or where the user hasn't complied with the policies targeted by the admin. | 7 |
| error | Number of devices that failed to communicate with Intune or Microsoft Entra ID, and returned an error message. | 3 |

### policyPlatformTypes

The following table contains the platform types of all assigned policies. Policies platform types that have never been assigned to any devices are not present in this table.

| Property | Description | Example |
| --- | --- | --- |
| policyPlatformTypeKey | The unique key for the policy platform type. | 20170519 |
| policyPlatformTypeId | The unique identifier for the policy platform type. | 1 |
| policyPlatformTypeName | The name for the policy platform type. | AndroidForWork |

### policyDeviceActivities

The following table lists the number of devices in the succeeded, pending, failed, or error state per day. The number reflects the data per Policy Type profiles. For example, if a device is in the succeeded state for all its assigned policies, it increments the succeeded counter up one for that day. If a device has two profiles assigned to it, one in the succeeded state and another in an error state, the entity increments the Succeeded counter and place the device in the error state. The policyDeviceActivity entity lists how many devices are in which state on a given day over the last 30 days.

| Property | Description | Example |
| --- | --- | --- |
| dateKey | Date Key when the Device Configuration Profile check-in was recorded in the data warehouse. | 20160703 |
| pending | Number of unique Devices in pending state. | 123 |
| Succeeded | Number of unique Devices in success state. | 12 |
| policyKey | policyKey, can be joined with policy to get the policyName. | Windows 10 baseline |
| error | Number of unique Devices in error state. | 10 |
| failed | Number of unique Devices in failed state. | 2 |

### policyUserActivities

The following table lists the number of users in the succeeded, pending, failed, or error state per day. The number reflects the data per Policy Type profiles. For example, if a user is in the succeeded state for all their assigned policies, it moves up the succeeded counter by one for that day. If a user has two profiles assigned to them, one in the succeeded state and the other is in an error state, the user in the error state is counted. The PolicyUserActivity entity lists how many users are in which state on a given day over the last 30 days.

| Property | Description | Example |
| --- | --- | --- |
| dateKey | Date Key when the Device Configuration Profile check-in was recorded in the data warehouse. | 20160703 |
| pending | Number of unique Devices in pending state. | 123 |
| succeeded | Number of unique Devices in success state. | 12 |
| policyKey | policyKey, can be joined with policy to get the policyName. | Windows 10 baseline |
| error | Number of unique Devices in error state. | 10 |