---
layout: Conceptual
title: Endpoint Protection client settings - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/protect/deploy-use/endpoint-protection-configure-client
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
description: Learn how to configure custom client settings for Endpoint Protection.
ms.date: 2018-07-30T00:00:00.0000000Z
ms.subservice: protect
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 884b3e56-812d-64fc-a84a-bceb90ebbac6
document_version_independent_id: e6fd0a65-4061-49c0-b1de-0094b59c6740
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/protect/deploy-use/endpoint-protection-configure-client.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/protect/deploy-use/endpoint-protection-configure-client
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/protect/deploy-use/endpoint-protection-configure-client.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/e0ffb20c-01c6-407b-a9bd-29111652a1dc
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/3904bce4-d817-48cf-85fd-b6146fca83b7
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 1816da93-9ee8-24db-e3df-5dcf564e731d
---

# Endpoint Protection client settings - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

This procedure configures custom client settings for Endpoint Protection, which you can deploy to collections of devices in your hierarchy.

Important

Only configure the default Endpoint Protection client settings if you're sure that you want them applied to all computers in your hierarchy.

## To enable Endpoint Protection and configure custom client settings

1. In the Configuration Manager console, click **Administration**.
2. In the **Administration** workspace, click **Client Settings**.
3. On the **Home** tab, in the **Create** group, click **Create Custom Client Device Settings**.
4. In the **Create Custom Client Device Settings** dialog box, provide a name and a description for the group of settings, and then select **Endpoint Protection**.
5. Configure the Endpoint Protection client settings that you require. For a full list of Endpoint Protection client settings that you can configure, see the Endpoint Protection section in [About client settings](../../core/clients/deploy/about-client-settings#endpoint-protection).

    Important

    Install the Endpoint Protection site system role before you configure client settings for Endpoint Protection.
6. Click **OK** to close the **Create Custom Client Device Settings** dialog box. The new client settings are displayed in the **Client Settings** node of the **Administration** workspace.
7. Next, deploy the custom client settings to a collection. Select the custom client settings you want to deploy. In the **Home** tab, in the **Client Settings** group, click **Deploy**.
8. In the **Select Collection** dialog box, choose the collection to which you want to deploy the client settings and then click **OK**. The new deployment is shown in the **Deployments** tab of the details pane.

Clients are configured with these settings when they next download client policy. For more information, see [Initiate policy retrieval for a Configuration Manager client](../../core/clients/manage/manage-clients#start-policy-retrieval).

## How to provision the Endpoint Protection client in a disk image

Install the Endpoint Protection client on a computer that you intend to use as a disk image source for Configuration Manager OS deployment. This computer is typically called the reference computer. After you create the OS image, then use Configuration Manager OS deployment to deploy the image.

Important

Starting in Windows 10 and Windows Server 2016, Windows Defender is installed by default. You don't need this procedure on those versions or later versions of Windows.

Use the following procedures to help you install and configure the Endpoint Protection client on a reference computer.

### Prerequisites

The following list contains the required prerequisites for installing the Endpoint Protection client software on a reference computer.

- You must have access to the Endpoint Protection client installation package, **scepinstall.exe**. Find this package in the **Client** folder of the Configuration Manager installation folder on the site server.
- To deploy the Endpoint Protection client with your organization's required configuration, create and export an antimalware policy. Then specify this policy when you manually install the Endpoint Protection client. For more information, see [How to create and deploy antimalware policies](endpoint-antimalware-policies).

    Note

    You can't export the **Default Client Antimalware Policy**.
- If you want to install the Endpoint Protection client with the latest definitions, download them from [Windows Defender Security Intelligence](https://www.microsoft.com/wdsi).

### How to install the Endpoint Protection client on the reference computer

Install the Endpoint Protection client locally on the reference computer from a command prompt. First get the installation file **scepinstall.exe**. For more information, see Install the Endpoint Protection client from a command prompt.

If necessary, also include a preconfigured antimalware policy or with an antimalware policy that you previously exported.

## To install the Endpoint Protection client from a command prompt

1. Copy **scepinstall.exe** from the **Client** folder of the Configuration Manager installation folder to the computer on which you want to install the Endpoint Protection client software.
2. Open a command prompt as an administrator. Change directory to the folder with the installer. Then run `scepinstall.exe`, adding any additional command-line properties that you require:

    | Property | Description |
    | --- | --- |
    | `/s` | Run the installer silently |
    | `/q` | Extract the setup files silently |
    | `/i` | Run the installer normally |
    | `/policy` | Specify an antimalware policy file to configure the client during installation |
    | `/sqmoptin` | Opt-in to the Microsoft Customer Experience Improvement Program (CEIP) |
3. Follow the on-screen instructions to complete the client installation.
4. If you downloaded the latest update definition package, copy the package to the client computer, and then double-click the definition package to install it.

    Note

    After the Endpoint Protection client install completes, the client automatically performs a definition update check. If this update check succeeds, you don't have to manually install the latest definition update package.

#### Example: install the client with an antimalware policy

`scepinstall.exe /policy <full path>\<policy file>`

## Verify the Endpoint Protection client installation

After you install the Endpoint Protection client on your reference computer, verify that the client is working correctly.

1. On the reference computer, open **System Center Endpoint Protection** from the Windows notification area.
2. On the **Home** tab of the **System Center Endpoint Protection** dialog box, verify that **Real-time protection** is set to **On**.
3. Verify that **Up-to-date** is displayed for **Virus and spyware definitions**.
4. To make sure that your reference computer is ready for imaging, under **Scan options**, select **Full**, and then click **Scan now**.

## Prepare the Endpoint Protection client for imaging

Perform the following steps to prepare the Endpoint Protection client for imaging:

1. On the reference computer, sign in as an administrator.
2. Download and install **PsExec** from [Windows SysInternals](/en-us/sysinternals/downloads/psexec).
3. Run a command prompt as an administrator, change directory to the folder where you installed PsTools, and then type the following command:

    `psexec.exe -s -i regedit.exe`

    Important

    Use caution when you run the Registry Editor in this manner. PsExec.exe runs it in the LocalSystem context.
4. In the Registry Editor, delete the following registry keys:

    Important

    Delete these registry keys as the last step before imaging the reference computer. The Endpoint Protection client recreates these keys when it starts. If you restart the reference computer, delete the registry keys again.

    - `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft Antimalware\InstallTime`
    - `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft Antimalware\Scan\LastScanRun`
    - `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft Antimalware\Scan\LastScanType`
    - `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft Antimalware\Scan\LastQuickScanID`
    - `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft Antimalware\Scan\LastFullScanID`
    - `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\RemovalTools\MRT\GUID`

You're now ready to prepare the reference computer for imaging.

When you deploy an OS image that contains the Endpoint Protection client, it automatically reports information to the device's assigned Configuration Manager site. The client downloads and applies any targeted antimalware policy.