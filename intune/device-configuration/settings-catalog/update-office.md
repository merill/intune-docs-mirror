---
layout: Conceptual
title: Update Microsoft 365 Apps With the Settings Catalog in Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/settings-catalog/update-office
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.collection:
- M365-identity-device-management
ms.subservice: configuration
description: Use settings catalog in Microsoft Intune to update Microsoft 365 apps to the latest version, and choose how frequently Office checks for updates. See the device registry keys that are updated when an Intune policy to Office update is applied.
ms.date: 2026-04-30T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: mayurjadhav
locale: en-us
document_id: 971bfd63-fe19-cd67-0b9c-6f9da4753075
document_version_independent_id: 971bfd63-fe19-cd67-0b9c-6f9da4753075
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/settings-catalog/update-office.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/settings-catalog/update-office
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/settings-catalog/update-office.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/e2c9f30c-00ec-44c0-846c-b20dbfb3283f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/1dd701e0-441f-4b0a-9806-aa47decc4e35
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/702271fe-87d7-4493-828b-2d6fde3de8ab
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/0a2fc935-5977-4aa6-9f55-0be03bd2acb8
platformId: 82c9a55a-785d-3758-ceae-ea19429609cc
---

# Update Microsoft 365 Apps With the Settings Catalog in Intune - Microsoft Intune | Microsoft Learn

Admins must keep Microsoft 365 Apps up-to-date so users have access to the latest security updates and performance improvements. In Intune, use the [settings catalog](./) to update Microsoft 365 apps on your Windows devices, including setting the update channel.

This article shows you how to use the settings catalog to manage Microsoft 365 app updates. It also provides guidance on confirming your policies apply successfully, which can help when troubleshooting.

In this scenario, you create a settings catalog policy in Intune that updates Microsoft 365 on your devices. For more information on settings catalog, see [Use the Intune settings catalog to configure settings](./).

This feature applies to:

- Windows
- Microsoft 365

## Prerequisites

![](../../media/icons/16/licensing.svg)**Licensing requirements**

> 
> Requires Microsoft Intune and a Microsoft 365 subscription. For more information on Intune licensing, see [Microsoft Intune licensing](../../fundamentals/licensing).

![](../../media/icons/16/rbac.svg)**Roles requirements**

> 
> To configure the settings catalog policy, at a minimum, sign in to the Intune admin center with the **Policy and Profile Manager** role. For more information about the built-in roles in Intune, see [Role-based access control (RBAC) with Microsoft Intune](../../fundamentals/role-based-access-control/overview).

![](../../media/icons/16/configuration.svg)**Device configuration requirements**

> 
> Add and enable [Microsoft 365 Apps Automatic Updates](/en-us/deployoffice/configure-update-settings-for-office-365-proplus) for your Office apps. You can enable automatic updates using Group Policy, or the Intune Office settings catalog settings:
> 
> [![Screenshot of searching for the Enable Office updates setting in the settings catalog in Microsoft Intune.](media/update-office/settings-catalog-search-enable-automatic-updates.png)](media/update-office/settings-catalog-search-enable-automatic-updates.png#lightbox)
> 
> [![Screenshot of the Enable Office updates setting configured in the settings catalog in Microsoft Intune.](media/update-office/settings-catalog-enable-automatic-updates.png)](media/update-office/settings-catalog-enable-automatic-updates.png#lightbox)

## Set the Microsoft 365 update channel in the Intune settings catalog

Use an Intune policy to set the update channel for Microsoft 365 apps. The update channel determines how frequently Office checks for updates.

1. In your [settings catalog](./#create-the-policy) policy, search for **Update Channel**, and select it. Close the settings picker.

    [![Screenshot of adding the Office Update Channel setting in the Microsoft Intune settings catalog.](media/update-office/settings-catalog-update-channel.png)](media/update-office/settings-catalog-update-channel.png#lightbox)
2. Set the **Update Channel** to **Enabled** and select the channel name. For example, select `Semi-Annual Enterprise Channel`:

    [![Screenshot of enabling the Office Update Channel setting and selecting a channel in the Microsoft Intune settings catalog.](media/update-office/settings-catalog-update-channel-semi-annual.png)](media/update-office/settings-catalog-update-channel-semi-annual.png#lightbox)

    Tip

    - It's recommended to update more frequently. Semi-annually is only used as an example.
    - For information on the different update channels, see [Overview of update channels for Microsoft 365 Apps](/en-us/microsoft-365-apps/updates/overview-update-channels).
3. When the policy is ready, [assign the policy](../assign-device-profile) to your Windows client devices. To test your policy sooner, you can also sync the policy.

    - [Sync the policy in Intune](../../device-management/actions/sync)
    - [Manually sync the policy on the device](../../user-help/device-actions/sync-device-windows#sync-from-settings-app)

## Check the Intune registry keys

After you assign the policy and the device syncs, you can confirm the Intune policy is applied.

1. On the device, open the **Registry Editor** app.
2. Go to the Intune policy path: `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PolicyManager\Providers\<Provider ID>\default\Device\office16v2~Policy~L_MicrosoftOfficemachine~L_Updates`.

    The `<Provider ID>` in the registry key changes. To find the provider ID for your device, open the **Registry Editor** app, and go to `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PolicyManager\AdmxInstalled`. The provider ID is shown.

    When the policy is applied, you see the following registry key:

    - `L_UpdatePath`

    Looking at the following example, you see `L_UpdatePath` has a value similar to `<enabled/><data id="L_UpdatePathID" value="http://officecdn.microsoft.com/pr/7ffbc6bf-bc32-4f92-8982-f9dd17fd3114" />`. This value means the update channel is set similar to the following image:

    [![Screenshot of the L_UpdatePath registry key value in the Registry Editor for Microsoft Office.](media/update-office/settings-catalog-update-path-registry-key.png)](media/update-office/settings-catalog-update-path-registry-key.png#lightbox)

    Tip

    [Manage Microsoft 365 Apps with Configuration Manager](../../configmgr/sum/deploy-use/manage-office-365-proplus-updates#bkmk_channel) lists the values, and what they mean. The registry values are based on the distribution channel selected:

    - Current Channel - value=`http://officecdn.microsoft.com/pr/492350f6-3a01-4f97-b9c0-c7c6ddf67d60`
    - Current Channel (preview) - value=`http://officecdn.microsoft.com/pr/64256afe-f5d9-4f86-8936-8840a6a4f5be`
    - Monthly Enterprise Channel - value=`http://officecdn.microsoft.com/pr/55336b82-a18d-4dd6-b5f6-9e5095c314a6`
    - Semi-Annual Enterprise Channel - value=`http://officecdn.microsoft.com/pr/7ffbc6bf-bc32-4f92-8982-f9dd17fd3114`
    - Semi-Annual Enterprise Channel (preview) - value=`http://officecdn.microsoft.com/pr/b8f9b850-328d-4355-9145-c59439a0c4cf`
    - Beta - value=`http://officecdn.microsoft.com/pr/5440fd1f-7ecb-4221-8110-145efaa6372f`

At this point, the Intune policy is successfully applied to the device.

## Check the Office registry keys

1. On the device, open the **Registry Editor** app.
2. Go to the Office policy path: `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\ClickToRun\Configuration`.

    You see the following registry keys:

    - `UpdateChannel`: A dynamic key that changes, depending on the configured settings.
    - `CDNBaseUrl`: Set when Microsoft 365 installs on the device.
3. Look at the `UpdateChannel` value. The value tells you how frequently Office is updated. [Manage Microsoft 365 Apps with Configuration Manager](../../configmgr/sum/deploy-use/manage-office-365-proplus-updates#bkmk_channel) lists the values, and what they're set to.

    Looking at the following example, you see `UpdateChannel` is set to `http://officecdn.microsoft.com/pr/492350f6-3a01-4f97-b9c0-c7c6ddf67d60`, which is the **Current Channel** (monthly):

    [![Screenshot of the Office UpdateChannel registry key value in the Registry Editor.](media/update-office/update-channel-office-registry-key.png)](media/update-office/update-channel-office-registry-key.png#lightbox)

    This example means the policy isn't applied yet, as the registry setting is still set to **monthly**, instead of **semi-annual**.

This registry key updates when the **Task Scheduler** &gt; **Office Automatic Updates 2.0** runs, or when a user signs into the device. To confirm, open the **Task Scheduler app** &gt; **Microsoft** &gt; **Office** &gt; **Office Automatic Updates 2.0** task &gt; **Triggers**. Depending on your triggers, it can take at least a day and more before the `UpdateChannel` registry key updates.

## Force Office automatic updates to run on the device

To test your policy, force the policy settings on the device. The following steps update the registry. As always, be careful when updating the registry.

1. Clear the registry key:

    1. Go to `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\ClickToRun\Updates`.
    2. Double-select the `UpdateDetectionLastRunTime` key &gt; delete the value data &gt; **OK**.
2. Run the Office Automatic Updates task:

    1. Open the **Task Scheduler** app on the device.
    2. Expand **Task Scheduler Library** &gt; **Microsoft** &gt; **Office**.
    3. Select **Office Automatic Updates 2.0** &gt; **Run**:

        [![Screenshot of running the Office Automatic Updates 2.0 task in Task Scheduler.](media/update-office/task-scheduler-office-automatic-updates.png)](media/update-office/task-scheduler-office-automatic-updates.png#lightbox)

        Wait for the task to finish, which can take several minutes.
3. In the **Registry Editor** app, go to `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\ClickToRun\Configuration`. Check the `UpdateChannel` value.

    It should be updated with the value set in the policy. In our example, the value should be set to `http://officecdn.microsoft.com/pr/7ffbc6bf-bc32-4f92-8982-f9dd17fd3114`.

At this point, the Office update channel is successfully changed on the device. You can open a Microsoft 365 app for a user that receives this update to check status.

## Force the Office synchronization to update account information

If you want to do more, you can force Office to get the latest version update. The following steps should only be done as a confirmation, or if you need the devices to get the latest version update from that channel quickly. Otherwise, let Office do its job, and update automatically.

### Step 1: Force the Office version to update

1. Confirm the Office version supports the update channel you choose. [Update history for Microsoft 365 Apps](/en-us/officeupdates/update-history-office365-proplus-by-date) lists the build numbers that support the different update channels.
2. In your settings catalog policy, search for the **Target Version** setting, and close the settings picker:

    [![Screenshot of searching for the Target Version setting in a Microsoft Intune settings catalog policy.](media/update-office/settings-catalog-search-target-version.png)](media/update-office/settings-catalog-search-target-version.png#lightbox)
3. Enter the version you want. Your **Target version** setting looks similar to the following setting:

    [![Screenshot of the Target Version setting configured in the Microsoft Intune settings catalog.](media/update-office/settings-catalog-enable-target-version-setting.png)](media/update-office/settings-catalog-enable-target-version-setting.png#lightbox)

Important

- Be sure to assign the policy.
- If you change an existing policy, your changes affect all assigned users.
- If you're testing this feature, create a test policy, and assign the policy to a test group of users.

### Step 2: Check the Office version

To test your policy before deploying it to all users, use the following steps:

1. In the **Registry Editor** app, go to `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PolicyManager\Providers\<Provider ID>\default\Device\office16~Policy~L_MicrosoftOfficemachine~L_Updates`.
2. Look at the `L_UpdateTargetVersion` value. When the policy applies, the value is set to the version you entered, such as `<enabled /><data id="L_UpdateTargetVersionID" value="16.0.19127.20082" />`.

    At this point, the Intune policy is successfully applied to the device.
3. Next, force Office to update. Open an Office app, such as Excel. Select to update now (possibly in the **Account** menu).

    The update takes several minutes. You can confirm Office is trying to get the version you enter:

    1. On the device, go to `C:\Program Files (x86)\Microsoft Office\Updates\Detection\Version`.
    2. Open the `VersionDescriptor.xml` file, and go to the `<Version>` section. The available version should be the same version you entered in the Intune policy, such as:

        [![Screenshot of the version section in the VersionDescriptor XML file for Office.](media/update-office/office-version-descriptor-xml-example.png)](media/update-office/office-version-descriptor-xml-example.png#lightbox)
4. After the update is installed, the Office app shows the new version (for example, on the **Account** menu).