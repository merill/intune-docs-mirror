---
layout: Conceptual
title: Custom properties for devices - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/adminservice/custom-properties
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
description: Use the administration service to set custom property data on devices, for reporting or collections.
ms.date: 2021-12-01T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 49090bd8-b448-2859-9e69-3929c126de08
document_version_independent_id: f6934621-695c-fdb6-7b1c-a9dd0211a6e8
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/adminservice/custom-properties.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/adminservice/custom-properties
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/adminservice/custom-properties.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 1e0e8397-ae0d-100f-94be-fc6da4fa91a1
---

# Custom properties for devices - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Many customers have other data that's external to Configuration Manager but useful for deployment targeting, collection building, and reporting. This data is typically non-technical in nature, not discoverable on the client, and comes from a single external source. For example, a central IT Infrastructure Library (ITIL) system or asset database, which has some of the following device attributes:

- Physical location
- Organizational priority
- Category
- Cost center
- Department

Starting in version 2107, you can [use the administration service](usage) to set this data on devices. The site stores the property's name and its value in the site database as the **Device Custom Properties** class. You can then use the custom properties in Configuration Manager for reporting or to create collections.

Starting in version 2111, you can create and edit these custom properties in the Configuration Manager console. This new user interface makes it easier to view and edit these properties.

Note

You can use unicode characters for custom property *values*, but not the property *names*. For more information, see [Unicode and ASCII support in Configuration Manager](../../core/plan-design/hierarchy/unicode-and-ascii-support).

## Prerequisites

The account that makes the API calls requires the following permissions on a collection that contains the target device:

- To set properties: **Modify Resource**
- To view properties: **Read Resource**
- To remove properties: **Delete Resource**

## Set properties via UI

*Applies to version 2111 or later*

1. In the Configuration Manager console, go to the **Assets and Compliance** workspace, and select the **Devices** node.
2. Select a device, and then in the ribbon select **Properties**
3. Switch to the **Custom Properties** tab.
4. Select the gold star icon ![](media/new-icon.png) to create a new custom property. Provide a name for the property and set a value for this device. Select **OK** to save the properties.

![Custom Properties tab on a device with multiple values.](media/10642650-custom-device-properties.png)

## Set properties via API

*Applies to version 2107 or later*

To set properties on a device, use the **SetExtensionData** API. Make a POST call to the URI `https://<SMSProviderFQDN>/AdminService/v1.0/Device(<DeviceResourceID>)/AdminService.SetExtensionData` with a JSON body. The resource ID is an integer value, for example `16777345`.

This JSON example sets two name-value pairs for the device's asset tag and location:

```json
{
  "ExtensionData": {
    "AssetTag":"0580255",
    "Location":"Dublin"
  }
}
```

## View properties

Use the **GetExtensionData** API to view your custom properties.

To view properties on a *single* device, make a GET call to the URI `https://<SMSProviderFQDN>/AdminService/v1.0/Device(<DeviceResourceID>)/AdminService.GetExtensionData`.

To view properties on *all* devices, make a GET call to the URI `https://<SMSProviderFQDN>/AdminService/v1.0/Device/AdminService.GetExtensionData`. This call returns property values from devices to which you have read permission.

## Remove properties

To remove properties values from all devices, use the **DeleteExtensionData** API without a device ID. Include a device resource ID to only remove properties from a specific device. Make a POST call to the URI `https://<SMSProviderFQDN>/AdminService/v1.0/Device/AdminService.DeleteExtensionData`.

## Create a collection

Use the following steps to create a collection with a query rule based on the custom properties:

1. In the Configuration Manager console, [Create a collection](../../core/clients/manage/collections/create-collections).
2. On the Membership Rules page, in the **Add Rule** list, select **Query rule**.
3. In the Query Rule Properties window, specify a **Name** for the query. Then select **Edit Query Statement**.
4. In the Query Statement Properties window, switch to the **Criteria** tab. Then select the golden asterisk (`*`) to add new criteria.
5. In the Criterion Properties window, **Select** the following values:

    - Attribute class: **Device Custom Properties**
    - Attribute: **PropertyName**
6. Select an **Operator** and then specify the name of the property as the **Value**.

    At this point, the Criterion Properties window should look similar to the following image:

    ![Criterion Properties window for Device Custom Properties PropertyName.](media/8939867-property-name.png)

    Select **OK** to save the criterion.
7. Repeat the steps to add a criterion for the **PropertyValue** attribute.

    At this point, the collection Query Statement Properties window should look similar to the following image:

    ![Query Statement Properties window with both Device Custom Properties criteria.](media/8939867-query-statement-properties.png)
8. Select **OK** to close all property windows. Then complete the wizard to create the collection.

### Example WQL statement

You can also use the following sample query. In the query statement properties window, select **Show Query Language** to paste the query statement.

```sql
select SMS_R_SYSTEM.ResourceID,SMS_R_SYSTEM.ResourceType,SMS_R_SYSTEM.Name,SMS_R_SYSTEM.SMSUniqueIdentifier,SMS_R_SYSTEM.ResourceDomainORWorkgroup,SMS_R_SYSTEM.Client
from SMS_R_System inner join SMS_G_System_ExtensionData on SMS_G_System_ExtensionData.ResourceId = SMS_R_System.ResourceId
where SMS_G_System_ExtensionData.PropertyName = "AssetTag" and SMS_G_System_ExtensionData.PropertyValue = "0580255"
```

Note

To use custom properties WQL statements with incremental collection updates, use Configuration Manager version 2107 with the [update rollup](../../hotfix/2107/11121541) or later.