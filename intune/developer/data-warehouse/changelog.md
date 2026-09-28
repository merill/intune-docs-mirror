---
layout: Conceptual
title: Intune Data Warehouse Change Log - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/developer/data-warehouse/changelog
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
description: This topic provides a list of changes for the Microsoft Intune Data Warehouse API.
ms.date: 2024-11-18T00:00:00.0000000Z
ms.topic: reference
locale: en-us
document_id: 6b126b0e-79b4-b7fa-3b68-157fa0e8c148
document_version_independent_id: 6b126b0e-79b4-b7fa-3b68-157fa0e8c148
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/developer/data-warehouse/changelog.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: developer/data-warehouse/changelog
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/developer/data-warehouse/changelog.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/1dd701e0-441f-4b0a-9806-aa47decc4e35
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/0a2fc935-5977-4aa6-9f55-0be03bd2acb8
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 4d0856ad-1cbc-312b-15fe-e596bf55e2bd
---

# Intune Data Warehouse Change Log - Microsoft Intune | Microsoft Learn

Keep current on updates to the Intune Data Warehouse.

## 2202

*Released February 2022*

The `applicationInventory` entity has been removed from the Intune Data Warehouse. A new dataset is now available in the UI and via Intune's export API. For related information, see [Export Intune reports using Graph APIs](../../device-management/reports/export-graph-apis).

## 2105

*Released May 2021*

The `IntuneAosp` property value is now supported in the `managementAgentType` enum. The `ManagementAgentTypeID` value for this property is `2048`. It represents the device type that is managed by Intune's MDM for AOSP (Android Open Source Project) devices. For related information, see [managementAgentType](ref-devices#managementagenttypes) in the beta section of the Intune Data Warehouse API.

## 2103

*Released March 2021*

The `applicationInventory` entity will be removed from the Intune Data Warehouse with the 2107 update of Intune. We are introducing a more complete and accurate dataset that will be available in the UI and via our export API. For related information, see [Export Intune reports using Graph APIs](../../device-management/reports/export-graph-apis).

## 2007

*Released July 2020*

### v1.0 changes

The following table lists the added property to the [device](ref-collections#devices) entity in the Intune Data Warehouse.

| Collection | Change | Description information |
| --- | --- | --- |
| ethernetMacAddress | Added | The unique network identifier of this device. |
| office365Version | Added | The version of Microsoft 365 that is installed on the device. |

The following table lists the added property to the [devicePropertyHistories](ref-collections#devicepropertyhistories) entity in the Intune Data Warehouse.

| Collection | Change | Description information |
| --- | --- | --- |
| physicalMemoryInBytes | Added | The physical memory in bytes. |
| totalStorageSpaceInBytes | Added | Total storage capacity in bytes. |

## 2004

*Released April 2020*

### v1.0 changes

The following table lists the added property to the [devices](ref-collections#devices) entity in the Intune Data Warehouse.

| Collection | Change | Description information |
| --- | --- | --- |
| windowsOsEdition | Added | Windows Operating System edition. |

### Beta changes

The following table lists the added property to the **device** entity in the Intune Data Warehouse.

| Collection | Change | Description information |
| --- | --- | --- |
| windowsOsEdition | Added | Windows Operating System edition. |

## 2003

*Released March 2020*

### Beta changes

The following table lists the added properties to the **device** entity in the Intune Data Warehouse.

| Collection | Change | Description information |
| --- | --- | --- |
| ethernetMacAddress | Added | The unique network identifier of this device. |
| model | Added | The device model. |
| office365Version | Added | The version of Microsoft 365 that is installed on the device. |

The following table lists the added properties to the **devicePropertyHistory** entity in the Intune Data Warehouse.

| Collection | Change | Description information |
| --- | --- | --- |
| physicalMemoryInBytes | Added | The physical memory in bytes. |
| totalStorageSpaceInBytes | Added | Total Storage in bytes. |

## 1903 (Part 2)

*Released April 2019*

### Beta changes

The following table lists the recent removed collections and the replacements collections in the Intune Data Warehouse.

| Collection | Change | Additional information |
| --- | --- | --- |
| mobileAppDeviceUserInstallStatus | Removed | Use [mobileAppInstallStatusCounts](ref-collections#mobileappinstallstatuscounts) instead. |
| enrollmentTypes | Removed | Use [deviceEnrollmentTypes](ref-collections#deviceenrollmenttypes) instead. |
| mdmStatuses | Removed | Use [complianceStates](ref-collections#compliancestates) instead. |
| workPlaceJoinStateTypes | Removed | Use the `azureAdRegistered` property in the [devices](ref-collections#devices) and [devicePropertyHistories](ref-collections#devicepropertyhistories) collections instead. |
| clientRegistrationStateTypes | Removed | Use [deviceRegistrationStates](ref-collections#deviceregistrationstates) instead. |
| currentUser | Removed | Use the [users](ref-collections#users) collection instead. |
| mdmDeviceInventoryHistories | Removed | Many of the properties were redundant or can now be found in the [devicePropertyHistories](ref-collections#devicepropertyhistories) or [devices](ref-collections#devices) collections. Any **mdmDeviceInventoryHistories** properties not already listed with these two collections are no longer available. See details below. |

The following table lists the old properties formerly found in the **mdmDeviceInventoryHistories** collection and the change/replacement. Any properties that were in **mdmDeviceInventoryHistories** but not listed below have been removed.

| Old property | Change/replacement |
| --- | --- |
| cellularTechnology | cellularTechnology in devices collection |
| deviceClientId | deviceId in devices collection |
| deviceManufacturer | manufacturer in devices collection |
| deviceModel | model in devices collection |
| deviceName | deviceName in devices collection |
| deviceOsPlatform | deviceTypeKey in devices collection |
| deviceOsVersion | osVersion in devicePropertyHistories collection |
| deviceType | deviceTypeKey in devices collection, referencing deviceTypes collection |
| encryptionState | encryptionState property in the devices collection |
| exchangeActiveSyncId | easDeviceId property in the devices collection |
| exchangeDeviceId | easDeviceId in devices collection |
| imei | imei in devices collection |
| isSupervised | isSupervised property in the devices collection |
| jailBroken | jailBroken in devicePropertyHistories collection |
| meid | meid property in the devices collection |
| oem | manufacturer in devices collection |
| osName | deviceTypeKey in devices collection, referencing deviceTypes collection |
| phoneNumber | phoneNumber in devices collection |
| platformType | model in devices collection |
| product | deviceTypeKey in devices collection |
| productVersion | osVersion in devicePropertyHistories collection |
| serialNumber | serialNumber in devices collection |
| storageFree | freeStorageSpaceInBytes property in the devices collection |
| storageTotal | totalStorageSpaceInBytes property in the devices collection |
| subscriberCarrierNetwork | subscriberCarrier property in the devices collection |
| wifimac | wiFiMacAddress in devices collection |

The following table lists changes to properties found in the [devicePropertyHistories](ref-collections#devicepropertyhistories) collection:

| Old property | Change/replacement |
| --- | --- |
| categoryId | deviceCategoryKey, referencing deviceCategories collection |
| certExpirationDate | Removed |
| clientRegistrationStateKey | deviceRegistrationStateKey |
| createdDate | enrolledDateTime in devices collection |
| deviceTypeKey | deviceTypeKey in devices collection |
| easID | easDeviceId in devices collection |
| enrolledByUser | userId in devices collection |
| enrollmentTypeKey | deviceEnrollmentTypeKey in devices collection |
| graphDeviceIsCompliant | Removed |
| graphDeviceIsManaged | Removed |
| lastContact | lastSyncDateTime in devices collection |
| lastContactNotification | Removed |
| lastContactWorkplaceJoin | Removed |
| lastExchangeStatusUtc | Removed |
| lastModifiedDateTimeUTC | Removed |
| lastPolicyUpdateUtc | Removed |
| managementAgentKey | managementStateKey |
| manufacturer | manufacturer in devices collection |
| mdmStatusKey | complianceStateKey, referencing complianceStates collection |
| model | model in devices collection |
| osFamily | operatingSystem in devices collection |
| osRevisionNumber | osVersion in devices collection |
| processorArchitecture | Removed |
| referenceId | azureAdDeviceId in devices collection |
| serialNumber | serialNumber in devices collection |
| workplaceJoinStateKey | azureAdRegistered |

The following table lists changes to properties found in the [devices](ref-collections#devices) collection:

| Old property | Change/replacement |
| --- | --- |
| categoryId | deviceCategoryKey, referencing deviceCategories collection |
| certExpirationDate | Removed |
| clientRegistrationStateKey | deviceRegistrationStateKey |
| createdDate | enrolledDateTime |
| easId | easDeviceId |
| enrolledByUser | userId |
| enrollmentTypeKey | deviceEnrollmentTypeKey |
| graphDeviceIsCompliant | Removed |
| graphDeviceIsManaged | Removed |
| lastContact | lastSyncDateTime |
| lastContactNotification | Removed |
| lastContactWorkplaceJoin | Removed |
| lastExchangeStatusUtc | Removed |
| lastPolicyUpdateUtc | Removed |
| mdmStatusKey | complianceStateKey, referencing complianceStates collection |
| osFamily | operatingSystem |
| processorArchitecture | Removed |
| referenceId | azureAdDeviceId |
| workplaceJoinStateKey | azureAdRegistered |

The following table lists changes to properties found in the [enrollmentActivities](ref-collections#enrollmentactivities) collection:

| Old property | Change/replacement |
| --- | --- |
| enrollmentTypeKey | deviceEnrollmentTypeKey |

The following table lists changes to properties found in the [mamApplications](ref-collections#mamapplications) collection:

| Old property | Change/replacement |
| --- | --- |
| applicationKey | mamApplicationKey |
| applicationName | mamApplicationName |
| applicationId | mamApplicationId |

The following table lists changes to properties found in the [mamApplicationInstances](ref-collections#mamapplicationinstances) collection:

| Old property | Change/replacement |
| --- | --- |
| applicationId | mamApplicationId |
| deviceId | mamDeviceId |
| deviceType | mamDeviceType |
| deviceName | mamDeviceName |

The following table lists changes to properties found in the [mamCheckins](ref-collections#mamcheckins) collection:

| Old property | Change/replacement |
| --- | --- |
| applicationKey | mamApplicationKey |

The following table lists changes to properties found in the [users](ref-collections#users) collection:

| Old property | Change/replacement |
| --- | --- |
| startDateInclusiveUtc | Removed |
| endDateInclusiveUtc | Removed |
| isCurrent | Removed |

## 1903

*Released March 2019*

### V1.0 changes reflecting back to beta

When V1.0 was first introduced in 1808, it differed in some significant ways from the beta API. In 1903 those changes will be reflected back into the beta API version. If you have important reports that use the beta API version, we strongly recommend switching those reports to V1.0 to avoid breaking changes. Please refer to [API version information](ref-api-endpoints) for more information on Data Warehouse API versions and backwards compatibility.

## 1902

*Released February 2019*

### Power BI Compliance app

Access your Intune Data Warehouse in Power BI Online using the [Intune Compliance (Data Warehouse)](https://aka.ms/intune/datawarehouseapi/getpowerbiapp) app. With this Power BI app, you can now access and share pre-created reports without any setup and without leaving your web browser.

Note

There are two additional filters you can apply to the Intune Compliance app.

#### Add additional filters to the Intune Compliance app

1. Open the [Intune Compliance (Data Warehouse)](https://aka.ms/intune/datawarehouseapi/getpowerbiapp) app in your web browsers.
2. Click **Non-Compliant Devices** and select **Non-Compliant** in the **complianceStatus** filter.
3. Click on **Unknown Devices** and select **Not Yet Available** in the **complianceStatus** filter.

## 1812

*Released December 2018*

### Enrollment Activities Collection Released to v1.0

The Enrollment Activities collection is now available in v1.0. You can use this collection to understand enrollment failure volume and trends in your environment. For more information, see [enrollmentActivities](ref-collections#enrollmentactivities), [enrollmentEventStatuses](ref-collections#enrollmenteventstatuses), [enrollmentFailureCategories](ref-collections#enrollmentfailurecategories), and [enrollmentFailureReasons](ref-collections#enrollmentfailurereasons).

## 1808

*Released August 2018*

### v1.0 Collections

You can now use the v1.0 version of the Intune Data Warehouse by setting the query parameter `api-version=v1.0`. Updates to collections in the Data Warehouse are additive in nature and do not break existing scenarios.

### Enrollment Activities Collection Released to Beta

The new `Enrollment Activities` collection is released to beta. You can use this collection to understand how your enrollment is proceeding by viewing the most common failures.

## 1805

*Released May 2018*

### Correction to device count in **Devices** collection

A fix has been made to the **Devices** collection which may lower total device counts that filter by the attribute `isDeleted`. This drop is a result of the correction and is not an error. For more information regarding the **Devices** collection, see [Reference for device entities](ref-devices).

## 1801

*Released January 2018*

### Intune Data Warehouse application-only authentication

You can set up an application using Microsoft Entra ID and authenticate to the Intune Data Warehouse. For more information see, [Intune Data Warehouse application-only authentication](configure-app-only-auth).

### Microsoft Entra ID and Intune credential requirements

- An Intune license is no longer required to be assigned to the user when accessing the Intune Data Warehouse (including the API).
- The Intune role name has been changed from **Reports** to **Intune data warehouse**.

    For more information, see [Microsoft Entra ID and Intune credential requirements](ref-api-endpoints#microsoft-entra-id-and-intune-credential-requirements).

### OData query options

You can use `$select` as an OData query parameter. The current version supports the following OData query parameters: `$filter`, `$orderby`, `$select`, `$skip`, and `$top`. For more information, see [OData query options](ref-api-endpoints#odata-query-options).

### New entities in the in Data Warehouse data model

- The entity, [**MobileAppDeviceuserInstallStatus**](ref-application), has been added. The **MobileAppDeviceUserInstallStatus** represents a mobile app install status for a given device and user.
- The entity, [**MobileAppInstallStates**](ref-application#mobileappinstallstates), has been added. The **MobileAppInstallState** entity represents the install state for a mobile application after it has been assigned to a group containing devices, users, or both.

## 1710

*Released November 2017*

### A new entity collection named Current User is limited to currently active user data

The **Users** entity collection contains all the Microsoft Entra users with assigned licenses in your enterprise. These records include user states during the data collection period, even if the user has been removed. For example, a user may be added to Intune and then removed during the course of the last month. While this user is not present at the time of the report, the user and state are present in the data. You could create a report that would show the duration of the user's historic presence in your data.

In contrast, the new **Current User** entity collection only contains users who have not been removed. The **Current User** entity collection only contains currently active users. For information about the **current user** entity collection, see [Reference for current user entity](ref-data-model).

## 1709

*Released October 2017*

### User device association entity collection added to Intune Data Warehouse data model

You can now build reports and data visualizations using the user device association information that associates user and device entity collections. The data model can be accessed through the Power BI file (PBIX) retrieved from the Data Warehouse Intune page, through the OData endpoint, or by developing a custom client. For more information, see the [User Device Association](ref-user-device).

### New entities in the in Data Warehouse data model

- The entity, [**UserDeviceAssociation**](ref-user-device), added. **UserDeviceAssociation** contains user device associations in your organization. You can now build reports and data visualizations using the user device association information that associates user and device entity collections.
- The entity, [**IntuneManagementExtension**](ref-intune-management-extension), added. **IntuneManagementExtension** contains entities for mobile devices that track information such as version and installation status.