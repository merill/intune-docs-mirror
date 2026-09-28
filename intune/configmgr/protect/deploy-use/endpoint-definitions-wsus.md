---
layout: Conceptual
title: Endpoint Protection malware definitions from WSUS - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/protect/deploy-use/endpoint-definitions-wsus
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
ms.date: 2022-02-10T00:00:00.0000000Z
ms.subservice: protect
ms.topic: how-to
description: Learn how to configure Windows Server Updates Services to auto-approve definition updates.
ms.collection: tier3
locale: en-us
document_id: 4ed29a03-7065-24d2-b616-4b503e37eeb1
document_version_independent_id: ce56bac9-9ef8-8de0-b3bd-15d265c3f18a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/protect/deploy-use/endpoint-definitions-wsus.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/protect/deploy-use/endpoint-definitions-wsus
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/protect/deploy-use/endpoint-definitions-wsus.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 0d874323-d8b7-f415-3194-4d4e1b46dfb8
---

# Endpoint Protection malware definitions from WSUS - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

If you use WSUS to keep your antimalware definitions up to date, you can configure it to auto-approve definition updates. Although using Configuration Manager software updates is the recommended method to keep definitions up to date, you can also configure WSUS as a method to allow users to manually update definitions. Use the following procedures to configure WSUS as a definition update source.

## Synchronize definition updates for Configuration Manager

1. In the Configuration Manager console, go to the **Administration** workspace, expand **Site Configuration**, and then select **Sites**.
2. Select the site that contains your software update point. In the **Settings** group of the ribbon, select **Configure Site Components**, and then select **Software Update Point**.
3. In the **Software Update Point Component Properties** window, switch to the **Classifications** tab. Select **Definition Updates**.
4. To specify the **Products** updated with WSUS, switch to the **Products** tab.

    - For Windows 10 and later: Under Microsoft &gt; Windows, select **Microsoft Defender Antivirus**.
    - For Windows 8.1 and earlier: Under Microsoft &gt; Forefront, select **System Center Endpoint Protection**.
5. Select **OK** to close the **Software Update Point Component Properties** window.

## Approve definition updates

Endpoint Protection definition updates must be approved and downloaded to the WSUS server before they're offered to clients that request the list of available updates. Clients connect to the WSUS server to check for applicable updates and then request the latest approved definition updates.

### Approve definitions and updates in WSUS

1. In the WSUS administration console, select **Updates**. Then select **All Updates** or the classification of updates that you want to approve.
2. In the list of updates, right-click the update or updates you want to approve for installation, and then select **Approve**.
3. In the **Approve Updates** window, select the computer group for which you want to approve the updates, and then select **Approved for Install**.

### Configure an automatic approval rule

You can also set an automatic approval rule for definition updates and Endpoint Protection updates. This action configures WSUS to automatically approve Endpoint Protection definition updates downloaded by WSUS.

1. In the WSUS administration console, select **Options**, and then select **Automatic Approvals**.
2. On the **Update Rules** tab, select **New Rule**.
3. In the **Add Rule** window, under **Step 1: Select properties**, select the option: **When an update is in a specific classification**.

    1. Under **Step 2: Edit the properties**, select **any classification**.
    2. Clear all options except **Definition Updates**, and then select **OK**.
4. In the **Add Rule** window, under **Step 1: Select properties**, select the option: **When an update is in a specific product**.

    1. Under **Step 2: Edit the properties**, select **any product**.
    2. Clear all options except **System Center Endpoint Protection** for Windows 8.1 and earlier or **Windows Defender** for Windows 10 and later. Then select **OK**.
5. Under **Step 3: Specify a name**, enter a name for the rule, and then select **OK**.
6. In the **Automatic Approvals** dialog box, select the newly created rule, and then select **Run rule**.

Note

To maximize performance on your WSUS server and client computers, decline old definition updates. To accomplish this task, you can configure automatic approval for revisions and automatic declining of expired updates. For more information, see [Microsoft Support article 938947](https://support.microsoft.com/kb/938947).