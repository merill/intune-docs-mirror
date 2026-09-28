---
layout: Conceptual
title: Managed SMS Provider Fundamentals - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/managed-sms-provider-fundamentals-in-configuration-manager
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
description: The managed SMS Provider library is a .NET Framework library that wraps the System.Management classes, provides a Configuration Manager-centric object model, and provides a wrapper for accessing the Configuration Manager site control file.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 6ccaba70-3529-2577-014d-7c0e5152da93
document_version_independent_id: d7f60778-20ba-c484-b240-d894e7fb381b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/managed-sms-provider-fundamentals-in-configuration-manager.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/managed-sms-provider-fundamentals-in-configuration-manager
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/managed-sms-provider-fundamentals-in-configuration-manager.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
platformId: b0d311b9-c0b6-c2e1-8681-a38d04ba515b
---

# Managed SMS Provider Fundamentals - Configuration Manager | Microsoft Learn

The managed SMS Provider library is a .NET Framework library that wraps the System.Management classes and provides a Configuration Manager-centric object model. It also provides a wrapper for accessing the Configuration Manager site control file.

The library can be used outside of any code relating to the Configuration Manager console .NET Framework library, but is built on the same underlying architecture.

For information about using managed code with the Configuration Manager client, see [About Configuration Manager WMI Programming](../clients/programming/about-configuration-manager-wmi-programming).

## Configuration Manager Classes and Interfaces

The primary classes and interfaces for use with the managed SMS Provider are the following:

### WqlConnectionManager

The class `WqlConnectionManager` provides access to the Configuration Manager Windows Management Instrumentation (WMI) provider.

It is an implementation of the abstract base class [ConnectionManagerBase](/en-us/previous-versions/system-center/developer/cc147366%28v=msdn.10%29) that defines connections throughout the managed Configuration Manager libraries.

It is used to connect to the SMS Provider and query, or create, Configuration Manager object instances. The following tasks demonstrate the basic usage of WqlConnectionManager.

[How to Connect to a Configuration Manager Provider using Managed Code](how-to-connect-to-an-sms-provider-by-using-managed-code).

[How to Read a Configuration Manager Object Using Managed Code](how-to-read-a-configuration-manager-object-by-using-managed-code).

[How to Perform an Asynchronous Configuration Manager Query Using Managed Code](how-to-perform-an-asynchronous-query-by-using-managed-code)

### IResultObject

[IResultObject](/en-us/previous-versions/system-center/developer/cc147376%28v=msdn.10%29) is an interface that all result sets and objects expose. Through it, you can read, modify, delete, call methods on, and otherwise manipulate Configuration Manager objects. You typically get an `IResultObject` whenever you create an object or as a result of a query.

The following tasks demonstrate the basic use of `IResultObject`:

[How to Modify a Configuration Manager Object Using Managed Code](how-to-modify-a-configuration-manager-object-by-using-managed-code)

[How to Delete a Configuration Manager Object Using Managed Code](how-to-delete-a-configuration-manager-object-by-using-managed-code)

[How to Call a Configuration Manager Object Method Using Managed Code](how-to-call-a-configuration-manager-object-class-method-by-using-managed-code)

### QueryProcessor

QueryProcesor provides support for both synchronous and asynchronous queries against the SMS Provider. In asynchronous queries, [SmsBackgroundWorker](/en-us/previous-versions/system-center/developer/cc147429%28v=msdn.10%29) is used to provide thread support query results. The following tasks demonstrate queries:

[How to Perform an Asynchronous Configuration Manager Query Using Managed Code](how-to-perform-an-asynchronous-query-by-using-managed-code).

[How to Perform a Synchronous Configuration Manager Query Using Managed Code](how-to-perform-a-synchronous-configuration-manager-query-by-using-managed-code).

### IQueryPropertyItem

[IQueryPropertyItem](/en-us/previous-versions/system-center/developer/cc147375%28v=msdn.10%29) is a single property of the result object, supports data binding and get/set properties.

The following tasks demonstrate the use of `IQueryPropertyItem`:

[How to Modify a Configuration Manager Object Using Managed Code](how-to-modify-a-configuration-manager-object-by-using-managed-code).

## Assemblies

The assemblies that are required for using managed SMS Provider are:

microsoft.configurationmanagement.managementprovider

adminui.wqlqueryengine

The WMI implementation of the managed Configuration Manager libraries is provided by adminui.wqlqueryengine.