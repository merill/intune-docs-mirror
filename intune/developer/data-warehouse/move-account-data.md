---
layout: Conceptual
title: Move Your Intune Data Warehouse Account Data - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/developer/data-warehouse/move-account-data
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
description: Understand how to back up your Intune Data Warehouse data when moving your account.
ms.date: 2025-06-09T00:00:00.0000000Z
ms.topic: reference
locale: en-us
document_id: 2547d94d-a3af-8c1c-6dc9-5c35d428d357
document_version_independent_id: 2547d94d-a3af-8c1c-6dc9-5c35d428d357
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/developer/data-warehouse/move-account-data.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: developer/data-warehouse/move-account-data
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/developer/data-warehouse/move-account-data.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: d7a0080c-2873-b902-3ccc-5aecc6f423a5
---

# Move Your Intune Data Warehouse Account Data - Microsoft Intune | Microsoft Learn

By requesting an account move, you're requesting that your data center is changed to another location. After the move, your Data Warehouse will reset and begin recording data at the new location based on the specified day your move begins. To back up your previous Data Warehouse data, complete the following steps **prior** to your account move. Most Data Warehouse tables retain data for 30 days, so any data gap in these tables will no longer be available 30 days after your account move. To learn more about the retention periods for specific tables, see [Data Warehouse data model](ref-data-model).

## Back up your Data Warehouse data

To back up your Data Warehouse data, you must save your Data Warehouse data into a *.csv* file using the Data Warehouse API:

1. Follow the one-time process in [Get data from the Intune Data Warehouse API with a REST client](setup-rest-client) if you’re using the Data Warehouse API for the first time.
2. Download all your data as CSV files by using the PowerShell sample [Access the Intune Data Warehouse with PowerShell](https://github.com/Microsoft/Intune-Data-Warehouse/tree/master/Samples/PowerShell).

## Back up your trend charts from the Microsoft Intune admin center

Some trend charts in your view of the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) resets. You can back up these charts by running the following script in **Graph**: 

### Terms & Conditions Acceptance reports

1. In the[Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Tenant administration** &gt; **Terms & Conditions**.
2. For each **Terms & Condition** item that you select, select **Acceptance Report** &gt; **Export**.
3. Save the report locally.

### App Protection reports

1. Select **Apps** -&gt; **Monitor** -&gt; **App protection status** in the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. To save each report, select the download icon ( ⤓ ).

### Device Configuration charts

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Devices** &gt; **Manage devices** &gt; **Configuration** &gt; **Export**.
2. Using Microsoft [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer), download the data behind the charts.

    - For deployment status of all device configuration profiles for all devices, see [Device deployment status](https://graph.microsoft.com/beta/reports/deviceConfigurationDeviceActivity/content).
    - For deployment status of all device configuration profiles for all users, see [User deployment status](https://graph.microsoft.com/beta/reports/deviceConfigurationUserActivity/content).
    - For profile deployment status, see [Provide deployment status](https://graph.microsoft.com/beta/deviceManagement/deviceConfigurations?$select=id,displayName,lastModifiedDateTime,deviceStatusOverview&amp;$expand=deviceStatusOverview).

    Note

    You must have a valid authentication token to access the device configuration and deployment status information.

## Device Enrollment charts

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Devices** &gt; **Monitor** &gt; **Assignment status** &gt; **Export**.
2. Using Microsoft [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer), download the data behind the charts.

    - For enrollment status, copy this [enrollment status query](https://graph.microsoft.com/beta/reports/managedDeviceEnrollmentFailureTrends%28%29/content) and paste it into [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer).
    - For top enrollment failures this week, copy this [enrollment failures query](https://graph.microsoft.com/beta/reports/managedDeviceEnrollmentTopFailures%28period=null%29/content) and paste it into [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer).

    Note

    You must have a valid authentication token to access the device enrollment data.

## After a Data Warehouse account move

After the Data Warehouse account move, you'll see in Intune that the Data Warehouse was reset. You need to update your Intune Data Warehouse API URL with the new tenant location for data to refresh. See [API URL structure](ref-api-endpoints#api-url-structure).

## Data Warehouse move example

Customer X requests an account move to begin on January 6, 2018. In response to the request, the customer receives a link to see documentation detailing steps to take if they wish to back up their previous Data Warehouse. On January 6, 2018, the Data Warehouse and the charts it supports will reset and begin storing data in the new data center.