---
layout: Conceptual
title: Verifying the Application Management Extension - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/apps/verifying-the-application-management-extension
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
description: Verifying the Application Management Extension. Verify the new Deployment Type is available in the console.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: e36aa219-98f9-1efe-2bbd-992082bb98ba
document_version_independent_id: 69451482-fa7d-dbcc-42e3-a939488cf60d
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/apps/verifying-the-application-management-extension.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/apps/verifying-the-application-management-extension
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/apps/verifying-the-application-management-extension.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: e3c13dc8-0fd8-2b6d-8717-94a1572290cb
---

# Verifying the Application Management Extension - Configuration Manager | Microsoft Learn

## Server

#### Verify the new Deployment Type is available in the console

1. In the Configuration Manager console, click **Software Library**.
2. In the **Software Library** workspace, expand **Application Management**, and then click **Applications**.
3. On the **Home** tab, in the **Create** group, click **Create Application**.
4. In the **Type** field, verify that the new deployment type is available in the pull-down menu.

    The image below shows an example from the RDP sample project.

    ![Screenshot showing successful registration](media/appmanregistrationscreenshot.gif)

Tip

For more information on using the Create Application Wizard, see [Create applications](../../apps/deploy-use/create-applications).

#### Create an application using the Create Application Wizard

1. In the Configuration Manager console, click **Software Library**.
2. In the **Software Library** workspace, expand **Application Management**, and then click **Applications**.
3. On the **Home** tab, in the **Create** group, click **Create Application**.
4. In the **Type** field, select the new deployment type from the pull-down menu.
5. Continue through the wizard until successful completion.

Tip

For more information on using the Create Application Wizard, see [Create applications](../../apps/deploy-use/create-applications).

#### Create a deployment type using the Create Deployment Type Wizard

1. In the Configuration Manager console, click **Software Library**.
2. In the **Software Library** workspace, expand **Application Management**, and then click **Applications**.
3. Select an application and then, on the **Home** tab, in the **Application** group, click **Create Deployment Type** to create a new deployment type for this application.
4. In the **Type** field, select the new deployment type from the pull-down menu.
5. Continue through the wizard until successful completion.

Tip

For more information on using the Create Application Wizard, see [Create applications](../../apps/deploy-use/create-applications).

#### Check the Deployment Type Properties

1. In the Configuration Manager console, click **Software Library**.
2. In the **Software Library** workspace, expand **Application Management**, and then click **Applications**.
3. Select an application and then select the **Deployment Type** tab, in the **Summary** group.
4. Select a deployment type and then select the **Deployment Type** tab, and then click **Properties** in the **Properties** group to display the deployment type properties.

#### Verify the corresponding SMS\_Application instance was created for the application

1. Load Windows Management Instrumentation Tester (WBEMTEST.EXE).
2. Connect to the root\sms\site\_&lt;*sitecode*&gt; namespace.
3. Click **Query**, and then enter the below query:

    ```
    SELECT * FROM SMS_Application WHERE LocalizedDisplayName = '<NameofApplication>'
    ```
4. The results should appear similar to the below list:

    SMS\_Application.CI\_ID=&lt;*Number*&gt;

#### Verify the digest associated with the Deployment Type contains the properties from the new technology

1. Connect to the CM\_&lt;*sitecode*&gt; database.
2. Load Microsoft SQL Server Management Studio, and click **New Query**.
3. Enter the below SQL query:

    ```
    SELECT SDMPackageDigest
    FROM CI_ConfigurationItems ci
    JOIN CI_LocalizedProperties lp ON (lp.CI_ID = ci.CI_ID)
    WHERE ci.CIType_ID = 21 AND lp.DisplayName = '<NameofApplication>'
    ```
4. The results should appear similar to the below list:

```text
     <AppMgmtDigest xmlns="http://schemas.microsoft.com/SystemCenterConfigurationManager/...
```

1. Double-click the result value to view the digest.

## Client

#### Deploy application to client using the corresponding Deployment Type

1. In the Configuration Manager console, click **Software Library**.
2. In the **Software Library** workspace, expand **Application Management**, and then click **Applications**.
3. In the **Applications** list, right-click the application you want to deploy and click **Deploy**.
4. Continue through the wizard until successful completion.

#### Force user and device policy to be retrieved on the client

1. On the client, in **Control Panel**, double-click the Configuration Manager icon, and then select the **Actions** tab.
2. Select **Machine Policy Retrieval & Evaluation Cycle**, and then click **Run Now**.
3. Select **User Policy Retrieval & Evaluation Cycle**, and then click **Run Now**.

#### Verify that synclets are distributed and compiled on the client (they will be stored in root\ccm\cimodels namespace)

1. Load Windows Management Instrumentation Tester (WBEMTEST.EXE).
2. Connect to the root\ccm\cimodels namespace.
3. Click **Query**, and then enter the below query:

    ```
    select * from ccm_handlersynclet
    ```
4. The results should appear similar to the below list:

    &lt;*Technology*&gt;*Detect\_Synclet.ActionType="Detect",AppDeliveryTypeId="ScopeId\* ...

    &lt;*Technology*&gt;*Install\_Synclet.ActionType="Install" ,AppDeliveryTypeId="ScopeId\* ...

    &lt;*Technology*&gt;*Uninstall\_Synclet.ActionType="Uninstall" ,AppDeliveryTypeId="ScopeId* ...

#### Ensure that each action performs as expected on the client

1. Verify that the deployment action performs correctly.

Note

The deployment settings will impact validation of each action on the client.

- **Available**- If the application is deployed to a user, the user sees the published application in the Application Catalog and can request it on demand. If the application is deployed to a device, the user will see it in the Software Center and can install it on demand.
    - **Required** - The application is deployed automatically, according to the configured schedule. However, a user can track the application deployment status and install the application before the deadline by using the Software Center.