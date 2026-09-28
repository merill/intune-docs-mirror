---
layout: Conceptual
title: How to analyze and convert packages - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/apps/pcm/how-to-analyze-and-convert
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
description: Learn how to analyze and convert packages with Package Conversion Manager in Configuration Manager.
ms.date: 2018-08-24T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 85896fca-1384-9ffb-265a-3d24492e53be
document_version_independent_id: 1afddd03-33a5-4e12-1a82-760b1882fb47
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/apps/pcm/how-to-analyze-and-convert.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/apps/pcm/how-to-analyze-and-convert
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/apps/pcm/how-to-analyze-and-convert.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 61e78395-5d44-4e9c-f4bc-03af7ecae825
---

# How to analyze and convert packages - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Before you can convert a package, first analyze it. Depending on the results of the analysis, you can then do one of the following tasks:

- **Convert** the package to an application. On the **Package** list in the console, the readiness state displays **Automatic**.
- **Fix and Convert** the package, attach collections, and create global conditions. On the **Package** list in the console, the readiness state displays **Automatic**.
- **Fix and Convert** the package. On the **Package** list in the console, the readiness state displays **Manual**.
- Leave the package unconverted. On the **Package** list in the console, the readiness state displays **Not Applicable**.

## How to analyze packages

1. In the Configuration Manager console, go to the **Software Library** workspace. Expand **Application Management**, and select the **Packages** node.
2. Select the package to convert. On the **Home** tab of the ribbon, in the **Package Conversion** group, select **Analyze Package**. Package Conversion Manager analyzes the package.
3. To see the readiness state of the package, add the **Readiness** column to the list of packages. The readiness state of the package determines your next action:

    - **Automatic**: How to convert packages

        To also attach collections and create global conditions with an **Automatic** readiness state, see How to fix and convert packages.
    - **Manual**: How to fix and convert packages
    - **Not Applicable**: This package is missing required content or a program. Add any missing content or programs and retry analysis. Or leave it in an unconverted state and continue to deploy it as a package.
    - **Unknown**: First run the **Analyze** task, or wait for the next scheduled analysis. If the state doesn't change, then see [Troubleshoot Package Conversion Manager](troubleshoot-pcm).

Tip

Optionally, you can use the following PowerShell cmdlet to analyze a package: [Invoke-CMAnalyzePackage](/en-us/powershell/module/configurationmanager/invoke-cmanalyzepackage).

## How to convert packages

1. In the Configuration Manager console, go to the **Software Library** workspace. Expand **Application Management**, and select the **Packages** node.
2. Select the package to convert with a readiness state of **Automatic**. On the **Home** tab of the ribbon, in the **Package Conversion** group, select **Convert Package**. The Convert Package to Application wizard opens.
3. In the Convert Package to Application wizard, review the list of selected packages. Remove any packages that you don't want to convert, and select **OK**. Package Conversion Manager converts the package. The Conversion Complete window lists the Conversion Status of the new applications.

    Note

    When you convert a package, the site records the date and time of the conversion as the UTC time.
4. Follow the instructions in the window. Select either **View applications** or **Close**.

Tip

Optionally, you can use the following PowerShell cmdlet to convert a package: [Invoke-CMConvertPackage](/en-us/powershell/module/configurationmanager/invoke-cmconvertpackage).

## How to fix and convert packages

1. In the Configuration Manager console, go to the **Software Library** workspace. Expand **Application Management**, and select the **Packages** node.
2. Select a package with a readiness state of **Manual** or **Automatic**. On the **Home** tab of the ribbon, in the **Package Conversion** group, select **Fix and Convert**.
3. In the Package Conversion Wizard, review the information on the **Package Selection** page, noting the **Items to Fix**. Then select **Next**.
4. On the **Dependency Review** page, review if the package is dependent on other listed packages, and then select **Next**.

    Note

    If you haven't converted any of the listed dependent packages, first convert those packages. Then restart the package conversion process.

    If a dependency isn't required, delete it, or ignore it and continue the conversion process.
5. On the **Deployment Type** page, review the deployment types for the new application. Change their priorities, or delete the deployment types.
6. If any of the new deployment types don't have an associated detection method, the **Detection Method** column displays a warning icon. Complete the following actions:

    1. Select **Edit Detection Method**.
    2. Select **Add**.
    3. In the Detection Rule dialog box, specify a **Setting Type**.
    4. For the specified setting type, enter the additional information required for the detection rule.
    5. Select **OK**. If necessary, repeat this process to add multiple detection methods to each deployment type.
    6. Select **OK**. Verify the **Detection Method** column displays an icon to confirm a correctly specified detection method.
7. Select **Next**.
8. On the **Requirements Selection** page, review the deployment types of the new application. Select a deployment type, and review the requirements for that deployment type.

    Note

    The wizard only displays the requirements that Package Conversion Manager converts. It doesn't convert all WQL queries in device collections to requirements.
9. Add requirements for a selected deployment type, if necessary.
10. Select **Next**.
11. Complete the wizard to create the application.

    Note

    When you convert a package, the site records the date and time of the conversion as the UTC time.

## Monitor

Go to the **Monitoring** workspace of the Configuration Manager console, and select **Package Conversion Status**. This dashboard shows the overall analysis and conversion state of packages in the site. A new background task automatically summarizes the analysis data.

Tip

Package Conversion Manager integrated with Configuration Manager doesn't require you to schedule analysis of packages. This action is handled by the integrated summarization task. Scheduled package analysis runs every seven days by default.

![Screenshot of example Package Conversion Status dashboard](media/1357861-pcm-dashboard.png)