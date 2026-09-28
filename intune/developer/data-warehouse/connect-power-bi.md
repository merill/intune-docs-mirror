---
layout: Conceptual
title: Connect to the Data Warehouse With Power BI - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/developer/data-warehouse/connect-power-bi
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
description: You can download a file for use with Microsoft Power BI that allows you to load interactive, dynamically generated reports for your Microsoft Intune tenant.
ms.date: 2026-03-31T00:00:00.0000000Z
ms.topic: reference
ai-usage: ai-assisted
locale: en-us
document_id: 4dc8ebc2-6eb5-ac5d-657a-ef9b861811bd
document_version_independent_id: 4dc8ebc2-6eb5-ac5d-657a-ef9b861811bd
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/developer/data-warehouse/connect-power-bi.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: developer/data-warehouse/connect-power-bi
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/developer/data-warehouse/connect-power-bi.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/d3197845-b4ce-44c6-a237-cd4be160e76c
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/aea905fb-0a9d-4d46-b30f-e9cbaf772d1b
platformId: 1dcf4b2a-e983-1300-b452-3b7a6b89fb95
---

# Connect to the Data Warehouse With Power BI - Microsoft Intune | Microsoft Learn

Important

The Intune Data Warehouse (beta) connector in Power BI (connector v1) is being retired. Power BI reports that use connector v1 need to be migrated to the Intune connector v2 or the OData Feed connector. Power BI reports created after November 2025 already use connector v2 and aren't affected. For migration steps, see Migrate from connector v1.

You can use the Power BI Compliance app to load interactive, dynamically generated reports for your Intune tenant. Additionally, you can load your tenant data in Power BI using the OData link. Intune provides connection settings to your tenant so that you can view the following sample reports and charts related to:

- Devices
- Enrollment
- App protection policy
- Compliance policy
- Device configuration profiles
- Software updates
- Device inventory logs

There are also trends highlighted for the enrollment, compliance, device configuration profile, and software updates. Sample charts and reports apply user-friendly filters to the canvas. To use advanced filters, check out the **Filter** pane in Power BI Desktop.

Note

Power BI template apps enable Power BI partners to build Power BI apps with little or no coding, and deploy them to any Power BI customer. For example, you can use the Power BI compliance report template in V2.0. V2.0 includes an improved design, as well as changes to the calculations and data that is being surfaced as part of the template. For more information, see [Update a template app](/en-us/power-bi/service-template-apps-install-distribute#update-a-template-app), [Intune Compliance (Data Warehouse) app](https://appsource.microsoft.com/product/power-bi/pbi_intune.intune_compliance_dw_app-preview?flightCodes=65ede247-5273-43b8-8a25-b89c7d211fbd), and [What are Power BI template apps?](/en-us/power-bi/service-template-apps-overview)

The following steps show you how to download the Power BI file and how to use the OData link with Power BI.

## Microsoft Entra ID and Intune credential requirements

Authentication and authorization are based on Microsoft Entra credentials and Intune role-based access control (RBAC). All Intune Administrators for your tenant have access to the Data warehouse by default. Use Intune roles to provide access for more users by giving them access to the **Intune data warehouse** resource.

Requirements for accessing the Intune Data Warehouse (including the API) are:

- User must have a minimum of one of the following roles:
    - An Intune service administrator
    - User with role-based access to **Intune data warehouse** resource
    - User-less authentication using [application-only authentication](configure-app-only-auth)

Important

To be assigned an Intune role and access the Intune Data Warehouse, the user must have an Intune license. For more information, see [Role-based access control (RBAC) with Microsoft Intune](../../fundamentals/role-based-access-control/overview) and [Microsoft Intune licensing](../../fundamentals/licensing).

## Install Power BI

Install the latest version of [Power BI Desktop](https://aka.ms/intune/datawarehouseapi/installpowerbi). For more information, see [Power BI Desktop](https://powerbi.microsoft.com/desktop).

## Load the data and reports using the Power BI Intune Compliance Data Warehouse App

The Power BI [Intune Compliance (Data Warehouse)](https://aka.ms/intune/datawarehouseapi/getpowerbiapp) app contains information for your tenant and a set of prebuilt reports based on the Data Warehouse data model.

Note

The Power BI Intune Compliance Data Warehouse app is not supported for Azure Government cloud environments.

1. Navigate to the **AppSource** page of the [Intune Compliance (Data Warehouse)](https://aka.ms/intune/datawarehouseapi/getpowerbiapp) app to begin the installation process.
2. Click the **Get It Now** button, and then click **Continue**.
3. When prompted to install the Power BI app, click **Install**.
4. After the installation completes, click on the **Intune Compliance (Data Warehouse)** app tile.
5. Click the **Connect** button. The **Connect to Intune Compliance (Data Warehouse)** dialog is displayed.
6. Click the **Sign in** button.
7. Sign in with a user account that has access to the Intune Data Warehouse for the tenant that has reports you want to view.
8. To view the included dashboard, click the **Dashboards** tab, then click the **Compliance Overview** dashboard.
9. To view all the available reports, click the **Reports** tab, then click the **Compliance V1.0** report. Browse through the report pages by clicking on the tabs at the bottom.
10. To make it easy to navigate back to these reports later, click the star next to the **Compliance V1.0** report. This will add the report to your Power BI favorites.

Alternatively, you can install the app from the Microsoft Intune admin center:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Reports** &gt; **Intune Data warehouse** &gt; **Data warehouse**.
3. Select **Get Power BI App** to access and share pre-created Power BI reports for your tenant in the browser.
4. Follow steps 2-10 above.

## Load the data in Power BI using the OData link

With a client authenticated to Microsoft Entra ID, the OData URL connects to the RESTful endpoint in the Data Warehouse API that exposes the data model to your reporting client. Follow these instructions to use Power BI Desktop to connect and create your own reports. You are not limited to Power BI Desktop, but can use your favorite analytic tool with the OData URL provided the client supports OAUTH2.0 authentication and the OData v4.0 standard.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Reports** &gt; **Intune Data warehouse** &gt; **Data warehouse**.
3. Retrieve the custom feed URL from the reporting blade, for example:`https://fef.{yourtenant}.manage.microsoft.com/ReportingService/DataWarehouseFEService/dates?api-version=v1.0`
4. Open **Power BI Desktop**.
5. Choose **File** &gt; **Get Data**. Select **OData feed**.
6. Choose **Basic**.
7. Type or paste the **OData URL** into the URL box.
8. Select **OK**.
9. If you have not authenticated to Microsoft Entra ID for your tenant from the Power BI desktop client, type your credentials. To gain access to your data, you must authorize with Microsoft Entra ID using OAuth 2.0.
    1. Select **Organizational account**.
    2. Type your username and password.
    3. Select **Sign In.**
    4. Select **Connect**.
10. Select **Load**.

## Migrate from connector v1

If your Power BI reports use the Intune connector v1, follow these steps to migrate to the OData Feed connector:

1. Open the report in **Power BI Desktop**.
2. Select **Transform data** in the toolbar.
3. For each query that uses an Intune data source, select **Advanced Editor**.
4. If the data source shows `Intune.Contents(x)`, the report uses connector v1 and needs to be updated.
5. Replace the data source with the following OData Feed connection:

    ```
    Source = OData.Feed("<reporting_service_endpoint>", null, [Implementation="2.0", Query=[#"api-version"="v1.0"]])
    ```

    To find your reporting service endpoint, sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) and go to **Reports** &gt; **Intune Data warehouse** &gt; **Data warehouse**. When you copy the endpoint, don't include the `api-version` segment.
6. Optionally, append the `maxHistoryDays` parameter to the endpoint to limit historical data:

    ```
    Source = OData.Feed("<reporting_service_endpoint>?maxHistoryDays=7", null, [Implementation="2.0", Query=[#"api-version"="v1.0"]])
    ```