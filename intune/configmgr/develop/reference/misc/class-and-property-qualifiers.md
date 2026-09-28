---
layout: Conceptual
title: Class and Property Qualifiers - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: configuration-manager
manager: laurawi
feedback_product_url: https://feedbackportal.microsoft.com/feedback/forum/4669adfc-ee1b-ec11-b6e7-0022481f8472
author: sccmavenger
ms.author: dannygu
ms.reviewer:
- umaikhan
- brianhun
- payur
- hugowu
- qiani
description: This table shows the qualifiers that are specific to Microsoft Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: ff1921a5-c91e-d399-2321-9d090f3adeb2
document_version_independent_id: ebac2341-9b74-68e2-6589-994fc1ab3612
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/misc/class-and-property-qualifiers.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/misc/class-and-property-qualifiers
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/misc/class-and-property-qualifiers.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4c50f262-d533-4ba4-9d4a-08899ec3a3d1
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6a8c83be-f1de-4e90-bde0-bd097999a60c
platformId: c7eeb2a6-b0e5-2e5b-4c0f-56b9624e2079
---

# Class and Property Qualifiers - Configuration Manager | Microsoft Learn

The following table shows the qualifiers that are specific to Microsoft Configuration Manager.

| Qualifier | Description |
| --- | --- |
| `Bits` (property) | A bit position of a Boolean flag in a bit field. |
| `Embedded` (class) | A textual description that indicates that the class is used as an embedded object. Individual instances of embedded classes can't be created. |
| `Enumeration` (property) | A list of valid string names for a discrete enumeration. |
| `Lazy` (property) | A property that is returned only for a `GetObject` operation (that is, omitted from the result class instance for an enumeration or a query). |
| `Range` (property) | A range of permitted values for a string or integer that has the following format:`<Low Value>-<High Value>` |
| `ResID` (class or property) | **Important:** This qualifier isn't used in Configuration Manager.  A string identifier in a resource DLL that contains the localized class or property name. The `ResID` qualifiers always used with `ResDLL`. |
| `ResIDValueLookup` | **Important:** This qualifier isn't used in Configuration Manager.  A qualifier that assists in the translation of an enumeration property to a localized string representation found in a DLL. To use this qualifier, query `SMS_ResIDValueLookup` with the `ResIDValueLookup` value and the property value (`IntLookupValue` for integers and `StringLookupValue` for strings). The `ResDLL` property of the resulting `ResIDValueLookup` instance will contain the resource DLL name containing the localized string, and the `ResID` property will be set to the string ID in the DLL. |
| `ResDLL` (class/property) | **Important:** This qualifier isn't used in Configuration Manager.  The name of the resource DLL that contains the localized class property name. |
| `Secured` (class) | An indicator that a class requires special rights to read or manipulate. |
| `SecurityVerbs` (instance) | **Important:** This qualifier isn't used in Configuration Manager. This functionality has been superseded by the role-based administration security model.  A bit field used on instances of secured objects to describe the rights that a requesting user has on the object. The meanings of the bits are the same as those found in the `AvailableInstancePermissions` property of the `SMS_SecuredObject` class. |
| `SizeLimit` (property) | The size limit of the data, which depends on the property data type:`<low length>-<high length>` or`<specific length>` |