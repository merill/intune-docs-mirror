---
layout: Conceptual
title: Intune Data Warehouse API Endpoint - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/developer/data-warehouse/ref-api-endpoints
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
description: This reference topic describes the Microsoft Intune Data Warehouse API URL structure. Filter examples are provided.
ms.date: 2024-10-30T00:00:00.0000000Z
ms.topic: reference
locale: en-us
document_id: 0a85b6ee-50e3-f580-2221-7cd3bdeb3c05
document_version_independent_id: 0a85b6ee-50e3-f580-2221-7cd3bdeb3c05
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/developer/data-warehouse/ref-api-endpoints.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: developer/data-warehouse/ref-api-endpoints
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/developer/data-warehouse/ref-api-endpoints.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
platformId: 69366782-fa2a-c381-e8ca-4b8bd97bed82
---

# Intune Data Warehouse API Endpoint - Microsoft Intune | Microsoft Learn

You can use the Intune Data Warehouse API with an account with specific role-based access controls and Microsoft Entra credentials. You will then authorize your REST client with Microsoft Entra ID using OAuth 2.0. And finally, you will form a meaningful URL to call a data warehouse resource.

## Microsoft Entra ID and Intune credential requirements

Authentication and authorization are based on Microsoft Entra credentials and Intune role-based access control (RBAC). All Intune Administrators for your tenant have access to the Data warehouse by default. Use Intune roles to provide access for more users by giving them access to the **Intune data warehouse** resource.

Requirements for accessing the Intune Data Warehouse (including the API) are:

- User must have a minimum of one of the following roles:
    - An Intune service administrator
    - User with role-based access to **Intune data warehouse** resource
    - User-less authentication using [application-only authentication](configure-app-only-auth)

Important

To be assigned an Intune role and access the Intune Data Warehouse, the user must have an Intune license. For more information, see [Role-based access control (RBAC) with Microsoft Intune](../../fundamentals/role-based-access-control/overview) and [Microsoft Intune licensing](../../fundamentals/licensing).

## Authorization

Microsoft Entra ID uses OAuth 2.0 to enable you to authorize access to web applications and web APIs in your Microsoft Entra tenant. This guide is language independent, and describes how to send and receive HTTP messages without using any open-source libraries. The OAuth 2.0 authorization code flow is described in [section 4.1](https://tools.ietf.org/html/rfc6749#section-4.1) of the OAuth 2.0 specification.

For more information, see [Authorize access to web applications using OAuth 2.0 and Microsoft Entra ID](/en-us/azure/active-directory/develop/active-directory-protocols-oauth-code).

## API URL structure

The Data Warehouse API endpoints read the entities for each set. The API supports a **GET** HTTP verb, and a subset of query options.

The URL for Intune uses the following format: `https://fef.{location}.manage.microsoft.com/ReportingService/DataWarehouseFEService/{entity-collection}?api-version={api-version}`

Note

In the above URL, replace `{location}`, `{entity-collection}`, and `{api-version}` based on the details provided in the table below.

The URL contains the following elements:

| Element | Example | Description |
| --- | --- | --- |
| location | msua06 | The base URL can be found by viewing the Data Warehouse API blade in the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431#blade/Microsoft_Intune_Enrollment/ReportingMenu/dataWarehouse). |
| entity-collection | devicePropertyHistories | The name of the OData entity collection. For more information on collections and entities in the data model, see [Data Model](ref-data-model). |
| api-version | beta | Version is the version of the API to access. For more information, see [Version](ref-api-endpoints#api-version-information). |
| maxhistorydays | 7 | (Optional) The maximum number of days of history to retrieve. This parameter can be supplied to any collection, but will only take effect for collections that include `dateKey` as a part of their key property. See [DateKey Range Filters](ref-api-endpoints#datekey-range-filters) for more information. |

## API version information

You can now use the v1.0 version of the Intune Data Warehouse by setting the query parameter `api-version=v1.0`. Updates to collections in the Data Warehouse are additive in nature and do not break existing scenarios.

You can try out the latest functionality of the Data Warehouse by using the beta version. To use the beta version, your URL must contain the query parameter `api-version=beta`. The beta version offers features before they are made generally available as a supported service. As Intune adds new features, the beta version may change behavior and data contracts. Any custom code or reporting tools dependent on the beta version may break with ongoing updates.

## OData query options

The current version supports the following OData query parameters: `$filter`, `$select`, `$skip,` and `$top`. In `$filter`, only `DateKey` or `RowLastModifiedDateTimeUTC` may be supported when the columns are applicable, and other properties would trigger a bad request.

## DateKey Range Filters

`DateKey` range filters may be used to limit the amount of data to download for some of the collections with `dateKey` as a key property. The `DateKey` filter can be used to optimize service performance by providing the following `$filter` query parameter:

1. `DateKey` alone in the `$filter`, supporting the `lt/le/eq/ge/gt` operators and joining with the logic operator `and`, where they can be mapped to a begin date and/or end date.
2. `maxhistorydays` is supplied as custom query option.

## Filter examples

Note

The filter examples assume today is 2/21/2018.

| Filter | Performance Optimization | Description |
| --- | --- | --- |
| `maxhistorydays=7` | Full | Return data with `DateKey` between 20180214 and 20180221. |
| `$filter=DateKey eq 20180214` | Full | Return data with `DateKey` equal to 20180214. |
| `$filter=DateKey ge 20180214 and DateKey lt 20180221` | Full | Return data with `DateKey` between 20180214 and 20180220. |
| `maxhistorydays=7&$filter=DateKey eq 20180214` | Full | Return data with `DateKey` equal to 20180214. `maxhistorydays` is ignored. |
| `$filter=RowLastModifiedDateTimeUTC ge 2018-02-21T23:18:51.3277273Z` | Full | Return data with `RowLastModifiedDateTimeUTC` is greater than or equal to `2018-02-21T23:18:51.3277273Z` |