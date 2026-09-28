---
layout: Conceptual
title: How to use the admin service - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/adminservice/usage
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
description: Learn how you can use the administration service in custom scenarios.
ms.date: 2020-07-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 4eed1add-4e7a-1103-2dcd-2f20c3dc6ad9
document_version_independent_id: 025e21a1-28ed-8a7c-422f-fa2293a65751
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/adminservice/usage.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/adminservice/usage
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/adminservice/usage.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/d3197845-b4ce-44c6-a237-cd4be160e76c
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/aea905fb-0a9d-4d46-b30f-e9cbaf772d1b
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: e504a36a-8c52-8c50-0b27-aa019fe700d6
---

# How to use the admin service - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Configuration Manager uses the administration service REST API in several native [scenarios](overview#scenarios). You can also use the administration service for your own custom scenarios.

Note

The examples in this article all use the FQDN of the server that hosts the SMS Provider role. If you access the administration service remotely through a CMG, use the CMG endpoint instead of the SMS Provider FQDN. For more information, see [Enable internet access](set-up#enable-internet-access).

## Direct query

There are several ways that you can directly query the administration service:

- Web browser
- PowerShell
- A third-party tool to send HTTPS GET or PUT requests to the web service

The next sections cover the first two methods.

Important

The administration service class names are case-sensitive. Make sure to use the proper capitalization. For example, `SMS_Site`.

### Web browser

You can use a web browser to easily query the administration service. When you specify a query URI as the browser's URL, the administration service processes the GET request, and returns the result in JSON format. Some web browsers may not display the result in an easy to read format.

### PowerShell

Make direct calls to this service with the Windows PowerShell cmdlet [Invoke-RestMethod](/en-us/powershell/module/microsoft.powershell.utility/invoke-restmethod).

For example:

```powershell
Invoke-RestMethod -Method 'Get' -Uri "https://SMSProviderFQDN/AdminService/wmi/SMS_Site" -UseDefaultCredentials
```

This command returns the following output:

```output
@odata.context                                                value
--------------                                                -----
https://SMSProviderFQDN/AdminService/wmi/$metadata#SMS_Site   {@{@odata.etag=FC1; __LAZYPROPERTIES=System.Objec...
```

The following example drills down to more specific values:

```powershell
((Invoke-RestMethod -Method 'Get' -Uri "https://SMSProviderFQDN/AdminService/wmi/SMS_Site" -UseDefaultCredentials).value).Version
```

The output of this command is the specific version of the site: `5.00.8968.1000`

#### Call PowerShell from a task sequence

You can use the **Invoke-RestMethod** cmdlet in a PowerShell script from the **Run PowerShell Script** task sequence step. This action lets you query the administration service during a task sequence.

For more information, see [Task sequence steps - Run PowerShell Script](../../osd/understand/task-sequence-steps#BKMK_RunPowerShellScript).

## Power BI Desktop

You can use Power BI Desktop to query data in Configuration Manager via the administration service. For more information, see [What is Power BI Desktop?](/en-us/power-bi/desktop-what-is-desktop)

1. In Power BI Desktop, in the ribbon, select **Get Data**, and select **OData feed**.
2. For the **URL**, specify the administration service route. For example, `https://smsprovider.contoso.com/AdminService/wmi/`
3. Choose **Windows Authentication**.
4. In the **Navigator** window, select the items to use in your Power BI dashboard or report.

[![Screenshot of Navigator window in Power BI Desktop](media/powerbi-desktop-navigator.png)](media/powerbi-desktop-navigator.png#lightbox)

## Example queries

### Get more details about a specific device

`https://<ProviderFQDN>/AdminService/wmi/SMS_R_System(<ResourceID>)`

For example: `https://smsprovider.contoso.com/AdminService/wmi/SMS_R_System(16777219)`

### v1 Device class examples

- Get all devices: `https://<ProviderFQDN>/AdminService/v1.0/Device`
- Get single device: `https://<ProviderFQDN>/AdminService/v1.0/Device(<ResourceID>)`
- Run CMPivot on a device:

    ```rest
    Verb: POST
    URI: https://<ProviderFQDN>/AdminService/v1.0/Device(<ResourceID>)/AdminService.RunCMPivot
    Body: {"InputQuery":"<CMPivot query to run>"}
    ```
- See CMPivot job result:

    ```rest
    Verb: GET
    URI: https://<ProviderFQDN>/AdminService/v1.0/Device(<ResourceID>)/AdminService.CMPivotResult(OperationId=<Operation ID of the CM Pivot job>)
    ```
- See which collections a device belongs to: `https://<ProviderFQDN>/AdminService/v1.0/Device(16777219)/ResourceCollectionMembership?$expand=Collection&$select=Collection`

### Filter results with startswith

This example URI only shows collections whose names start with `All`.

`https://<ProviderFQDN>/AdminService/wmi/SMS_Collection?$filter=startswith(Name,'All') eq true`

### Run a static WMI method

This example invokes the **GetAdminExtendedData** method on the **SMS\_AdminClass** that takes parameter named **Type** with value `1`.

```rest
Verb: Post
URI: https://<ProviderFQDN>/AdminService/wmi/SMS_Admin.GetAdminExtendedData
Body: {"Type":1}
```