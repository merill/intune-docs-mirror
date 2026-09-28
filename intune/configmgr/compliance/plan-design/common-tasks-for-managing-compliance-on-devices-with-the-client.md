---
layout: Conceptual
title: Common compliance management tasks - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/compliance/plan-design/common-tasks-for-managing-compliance-on-devices-with-the-client
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
description: Learn about Configuration Manager compliance settings by working through some common scenarios.
ms.date: 2021-10-05T00:00:00.0000000Z
ms.subservice: compliance
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: b9ae0c82-0030-8836-82f9-5ed0e111477c
document_version_independent_id: e88d7c1b-f98f-6806-bad9-4ada6819de00
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/compliance/plan-design/common-tasks-for-managing-compliance-on-devices-with-the-client.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/compliance/plan-design/common-tasks-for-managing-compliance-on-devices-with-the-client
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/compliance/plan-design/common-tasks-for-managing-compliance-on-devices-with-the-client.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/e0ffb20c-01c6-407b-a9bd-29111652a1dc
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/3904bce4-d817-48cf-85fd-b6146fca83b7
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 9984309a-0cdc-ca99-a9c0-27f31b6e88b2
---

# Common compliance management tasks - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

This article gives you an introduction to using Configuration Manager compliance settings by guiding you through some common scenarios that you might come across.

If you're already familiar with compliance settings, you can find detailed information about all the features you use in [Configuration items for devices managed with the Configuration Manager client](../deploy-use/create-configuration-items).

Before you start, read [Get started with compliance settings](../get-started/get-started-with-compliance-settings) to learn some basics about compliance settings. Read [Plan for and configure compliance settings](plan-for-and-configure-compliance-settings) for information about necessary prerequisites.

## General information for each scenario

In each scenario, you'll create a configuration item that performs a specific task. To open the Create Configuration Item Wizard and get started, take these steps:

1. In the Configuration Manager console, select **Assets and Compliance** &gt; **Compliance Settings** &gt; **Configuration Items**.
2. On the **Home** tab, in the **Create** group, select **Create Configuration Item**.
3. On the **General** page of the Create Configuration Item Wizard, shown in the following screenshot, specify a name and description for the configuration item. Then choose the appropriate configuration item type for each scenario in this article.

    ![General page of the Create Configuration Item Wizard](../../mdm/deploy-use/media/compliance-settings-wizard---1.png)

## Scenario: Disable Bluetooth on Windows 10 or later devices

In this scenario, your security department has determined that the Bluetooth capability on devices could be used to transmit sensitive corporate information outside the company. You decide to disable Bluetooth on these devices.

1. On the **General** page of the Create Configuration Item Wizard, select the **Windows 10 or later** configuration item type, and then select **Next**.
2. On the **Supported Platforms** page of the wizard, select all Windows 10 or later platforms.
3. On the **Device Settings** page, select **Device**, and then select **Next**.
4. On the **Device** page, select **Prohibited** as the value for **Bluetooth**.
5. Select **Remediate noncompliant settings** to ensure the change is applied to all Windows 10 or later devices.
6. Complete the wizard to create the configuration item.

You can now use the information in the [Common tasks for creating and deploying configuration baselines with Configuration Manager](common-tasks-for-creating-and-deploying-configuration-baselines) article to help you deploy the configuration you've created to devices.

## Scenario: Remediate an incorrect registry value on Windows desktop computers

Note

On Mac computers running the Configuration Manager client, you have two options for assessing compliance:

- Evaluate a macOS X preferences (plist) file.
- Use a custom script and evaluate the results returned by the script.

For more information, see [How to create configuration items for macOS X devices managed with the Configuration Manager client](../deploy-use/create-configuration-items-for-mac-os-x-devices-managed-with-the-client).

In this scenario, you discover that an important line-of-business app doesn't run correctly on some Windows 8.1 computers that you manage. You determine that this is because a registry key named **HKEY\_LOCAL\_MACHINE\SOFTWARE\Woodgrove\LOB App\Configuration\Configuration1** is set to a value of **0** on some computers. For the line-of-business app to run successfully, this value needs to be set to **1**.

In this procedure, you'll create a configuration item that monitors for and automatically remediates any incorrect registry key values that are found.

1. On the **General** page of the Create Configuration Item Wizard, select the **Windows Desktops and Servers (custom)** configuration item type, and then select **Next**.
2. On the **Supported Platforms** page of the wizard, select **Windows 8.1** (to ensure the configuration item applies only to affected computers).
3. On the **Settings** page, select **New** to create a new setting.
4. On the **General** tab of the **Create Setting** dialog box, configure these settings:

    - **Name** &gt; **Example setting**
    - **Setting type** &gt; **Registry value**
    - **Data type** &gt; **Integer** (because the value contains a number only)
    - **Hive** &gt; **HKEY\_LOCAL\_MACHINE**
    - **Key** &gt; **SOFTWARE\Woodgrove\LOB App\Configuration\Configuration1**
    - **Value** &gt; **1** (the required value)
5. On the **Compliance Rules** tab of the **Create Setting** dialog box, select **New**. In the **Create Rule** dialog box, configure these settings:

    - **Name** &gt; **Example Rule**
    - **Selected setting** &gt; Verify that the selected setting is **Example setting**.
    - **Rule type** &gt; **Value**
    - **The setting must comply with the following rule** &gt; Verify that the setting name is correct and configure the option to specify that the setting value must equal **1**.
    - **Remediate noncompliant rules when supported** &gt; Select this check box to ensure that Configuration Manager will reset the registry key value to the correct value if it's incorrect.
6. Complete the wizard to create the configuration item.

You can now use the information in the [Common tasks for creating and deploying configuration baselines](common-tasks-for-creating-and-deploying-configuration-baselines) article to help you deploy the configuration you've created to devices.