---
layout: Conceptual
title: Common Education Windows Update configuration - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/solutions/education/tutorial-school-deployment/ref-update-settings-windows
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: yegor-a
ms.author: egorabr
ms.subservice: education
description: Learn about common Windows Update configuration used by Education organizations in Intune.
ms.date: 2024-05-02T00:00:00.0000000Z
ms.topic: tutorial
ms.collection:
- graph-interactive
locale: en-us
document_id: 867debe5-198e-d527-894f-cad8b693df6a
document_version_independent_id: 867debe5-198e-d527-894f-cad8b693df6a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/solutions/education/tutorial-school-deployment/ref-update-settings-windows.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
interactive_type: msgraph
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: solutions/education/tutorial-school-deployment/ref-update-settings-windows
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/solutions/education/tutorial-school-deployment/ref-update-settings-windows.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: ae1af62b-8d62-29d2-99f9-c0da4d413919
---

# Common Education Windows Update configuration - Microsoft Intune | Microsoft Learn

Microsoft Intune and Intune for Education can configure many Windows Update configuration settings. This article summarizes the configurations that are most commonly used for student and teacher devices.

Use Microsoft Intune or Intune for Education to manage the install of Windows software updates from Windows Update client policies. You can configure update settings on devices and configure deferral of update installation. You can also prevent devices from installing features from new Windows versions to help keep them stable, while allowing those devices to continue installing updates for quality and security.

## Update rings for Windows

Update ring policies are a collection of settings that configure when devices that run Windows updates get installed.

To learn more, see:

- [Update rings for Windows policy in Intune](../../../device-updates/windows/manage-update-rings)
- [The Windows Update policies you should set and why](https://techcommunity.microsoft.com/t5/windows-it-pro-blog/the-windows-update-policies-you-should-set-and-why/ba-p/3270914)
- [YouTube: Windows Update for Business Fundamentals](https://www.youtube.com/watch?v=TXwp-jLDcg0&amp;list=PLMuDtq95SdKvpS9zPyFt9fc9HgepQxaw9&amp;index=1)
- [YouTube: Windows Update for Business Fundamentals (Japanese)](https://youtu.be/o6_eGOyv-_g)

# [Settings](#tab/settings)
| **Update settings** | **Value** | **Notes** | **CSP** |
| --- | --- | --- | --- |
| **Microsoft product updates** | Allow | Don't set to Block. In order to revert the configuration, PowerShell commands have to be run on each device. | [AllowMUUpdateService](/en-us/windows/client-management/mdm/policy-csp-update#allowmuupdateservice) |
| **Windows drivers** | Allow |  | [ExcludeWUDriversInQualityUpdate](/en-us/windows/client-management/mdm/policy-csp-update#excludewudriversinqualityupdate) |
| **Quality update deferral period (days)** | 7 |  | [DeferQualityUpdatesPeriodInDays](/en-us/windows/client-management/mdm/policy-csp-update#deferqualityupdatesperiodindays) |
| **Feature update deferral period (days)** | 30 | Select 0 if using a **Feature update policy** otherwise select 30 days. | [DeferFeatureUpdatesPeriodInDays](/en-us/windows/client-management/mdm/policy-csp-update#deferfeatureupdatesperiodindays) |
| **Upgrade Windows 10 devices to Latest Windows 11 release** | No |  | [ProductVersion](/en-us/windows/client-management/mdm/policy-csp-update#productversion) |
| **Set feature update uninstall period** (2 - 60 days) | 14 |  | [ConfigureFeatureUpdateUninstallPeriod](/en-us/windows/client-management/mdm/policy-csp-update#configurefeatureupdateuninstallperiod) |
| **Enable pre-release builds** | Not configured |  | [ManagePreviewBuilds](/en-us/windows/client-management/mdm/policy-csp-update#managepreviewbuilds) |

| **User experience settings** | **Value** | **Notes** | **CSP** |
| --- | --- | --- | --- |
| **Automatic update behavior** | Reset to default | Auto install and restart. Updates are downloaded automatically on non-metered networks and installed during "Automatic Maintenance" when the device isn't in use and isn't running on battery power.**Note:** If Windows Update policy is configured via the settings catalog, the value should be **Auto install and restart**. | [AllowAutoUpdate](/en-us/windows/client-management/mdm/policy-csp-update#allowautoupdate) |
| **Restart checks (EDU Restart)** | Allow | Must not be disabled in existing Windows Update Rings.This setting is no longer available when creating a new Windows Update Ring policy. | [SetEDURestart](/en-us/windows/client-management/mdm/policy-csp-update#setedurestart) |
| **Option to pause Windows updates** | Disable |  | [SetDisablePauseUXAccess](/en-us/windows/client-management/mdm/policy-csp-update#setdisablepauseuxaccess) |
| **Option to check for Windows updates** | Disable |  | [SetDisableUXWUAccess](/en-us/windows/client-management/mdm/policy-csp-update#setdisableuxwuaccess) |
| **Change notification update level** | Turn off all notifications, excluding restart warnings |  | [UpdateNotificationLevel](/en-us/windows/client-management/mdm/policy-csp-update#updatenotificationlevel) |
| **Use deadline settings** | Allow | Only enables the setting configuration. |  |
| **Deadline for feature updates** | 7 |  | [ConfigureDeadlineForFeatureUpdates](/en-us/windows/client-management/mdm/policy-csp-update#configuredeadlineforfeatureupdates) |
| **Deadline for quality updates** | 3 |  | [ConfigureDeadlineForQualityUpdates](/en-us/windows/client-management/mdm/policy-csp-update#configuredeadlineforqualityupdates) |
| **Grace period** | 2 |  | [ConfigureDeadlineGracePeriod](/en-us/windows/client-management/mdm/policy-csp-update#configuredeadlinegraceperiod)[ConfigureDeadlineGracePeriodForFeatureUpdates](/en-us/windows/client-management/mdm/policy-csp-update#configuredeadlinegraceperiodforfeatureupdates) |
| **Auto reboot before deadline** | Yes |  | [ConfigureDeadlineNoAutoReboot](/en-us/windows/client-management/mdm/policy-csp-update#configuredeadlinenoautoreboot) |

# [Create policy using Graph Explorer](#tab/graph)
Use Graph to create the settings catalog policy in your tenant without assignments or scope tags.

This will create a policy in your tenant with the name **\_MSLearn\_Example\_CommonEDU - Windows - Update ring**.

```msgraph
POST https://graph.microsoft.com/beta/deviceManagement/deviceConfigurations
Content-Type: application/json

{"@odata.type":"#microsoft.graph.windowsUpdateForBusinessConfiguration","id":"","displayName":"_MSLearn_Example_CommonEDU - Windows - Update ring","description":"https://aka.ms/ManageEduDevices","roleScopeTagIds":["0"],"microsoftUpdateServiceAllowed":true,"driversExcluded":false,"qualityUpdatesDeferralPeriodInDays":7,"featureUpdatesDeferralPeriodInDays":30,"allowWindows11Upgrade":false,"qualityUpdatesPaused":false,"featureUpdatesPaused":false,"businessReadyUpdatesOnly":"userDefined","skipChecksBeforeRestart":false,"automaticUpdateMode":"windowsDefault","installationSchedule":null,"userPauseAccess":"disabled","userWindowsUpdateScanAccess":"disabled","updateNotificationLevel":"restartWarningsOnly","updateWeeks":null,"featureUpdatesRollbackWindowInDays":14,"deadlineForFeatureUpdatesInDays":7,"deadlineForQualityUpdatesInDays":3,"deadlineGracePeriodInDays":2,"postponeRebootUntilAfterDeadline":false,"engagedRestartDeadlineInDays":null,"engagedRestartSnoozeScheduleInDays":null,"engagedRestartTransitionScheduleInDays":null,"engagedRestartSnoozeScheduleForFeatureUpdatesInDays":null,"engagedRestartTransitionScheduleForFeatureUpdatesInDays":null,"autoRestartNotificationDismissal":"notConfigured","scheduleRestartWarningInHours":null,"scheduleImminentRestartWarningInMinutes":null}
```

1. Click *Try it* to open Graph Explorer.
2. Once Graph Explorer is open, select the ![](../../../media/icons/16/person.svg) user icon in the top right to sign-in and sign in with your Intune administrator organizational account.
3. Click **Run query** to create the policy in your tenant.

    Tip

    If it's the first time using Graph Explorer, you may need to authorize the application to access your tenant or to modify the existing permissions. This graph call requires *DeviceManagementConfiguration.ReadWrite.All* permissions. You can grant the required permissions by selecting **modify permissions** and then selecting **Consent**.
4. The policy is created in your tenant and can be edited to meet your requirements before assigning to groups.

Note

As of July 31 2025, Microsoft Graph replaced use of the *DeviceManagementConfiguration.ReadWrite.All* permission with *DeviceManagementScripts.ReadWrite.All* for the following API calls:

- ~/deviceManagement/deviceShellScripts
- ~/deviceManagement/deviceHealthScripts
- ~/deviceManagement/deviceComplianceScripts
- ~/deviceManagement/deviceCustomAttributeShellScripts
- ~/deviceManagement/deviceManagementScripts

---

## Settings catalog

Settings described in this section aren't available in an Update ring policy and should be configured using a settings catalog type configuration profile.

To learn more, see [Use the settings catalog to configure settings on Windows, iOS/iPadOS, and macOS devices](../../../device-configuration/settings-catalog/).

Tip

When creating a settings catalog profile in the Microsoft Intune admin center, you can copy a policy name from this article and paste it into the settings picker search field to find the desired policy.

# [Settings](#tab/settings)
| **Category** | **Name** | **Value** | **Notes** | **CSP** |
| --- | --- | --- | --- | --- |
| Windows Update For Business | **No update notifications during active hours** | Enabled |  | [NoUpdateNotificationsDuringActiveHours](/en-us/windows/client-management/mdm/policy-csp-update#noupdatenotificationsduringactivehours) |

# [Create policy using Graph Explorer](#tab/graph)
Use Graph to create the settings catalog policy in your tenant without assignments or scope tags.

This will create a policy in your tenant with the name **\_MSLearn\_Example\_CommonEDU - Windows - Updates**.

```msgraph
POST https://graph.microsoft.com/beta/deviceManagement/configurationPolicies
Content-Type: application/json

{"name":"_MSLearn_Example_CommonEDU - Windows - Updates","description":"https://aka.ms/ManageEduDevices","platforms":"windows10","technologies":"mdm","roleScopeTagIds":["0"],"settings":[{"@odata.type":"#microsoft.graph.deviceManagementConfigurationSetting","settingInstance":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingInstance","settingDefinitionId":"device_vendor_msft_policy_config_update_noupdatenotificationsduringactivehours","choiceSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingValue","value":"device_vendor_msft_policy_config_update_noupdatenotificationsduringactivehours_1","children":[]}}}]}
```

1. Click *Try it* to open Graph Explorer.
2. Once Graph Explorer is open, select the ![](../../../media/icons/16/person.svg) user icon in the top right to sign-in and sign in with your Intune administrator organizational account.
3. Click **Run query** to create the policy in your tenant.

    Tip

    If it's the first time using Graph Explorer, you may need to authorize the application to access your tenant or to modify the existing permissions. This graph call requires *DeviceManagementConfiguration.ReadWrite.All* permissions. You can grant the required permissions by selecting **modify permissions** and then selecting **Consent**.
4. The policy is created in your tenant and can be edited to meet your requirements before assigning to groups.

Note

As of July 31 2025, Microsoft Graph replaced use of the *DeviceManagementConfiguration.ReadWrite.All* permission with *DeviceManagementScripts.ReadWrite.All* for the following API calls:

- ~/deviceManagement/deviceShellScripts
- ~/deviceManagement/deviceHealthScripts
- ~/deviceManagement/deviceComplianceScripts
- ~/deviceManagement/deviceCustomAttributeShellScripts
- ~/deviceManagement/deviceManagementScripts

---

## Windows Update Feature Control

Windows feature updates contain new Windows features to improve the user experience. Windows feature versions are supported differently depending on the edition. It's important to ensure that the Windows version installed remains supported so that it can receive the latest security updates and support required applications such as testing apps.

Use the support lifecycle websites for each Windows operating system version and edition:

- [Windows 11 Home, Pro, and Pro Education](/en-us/lifecycle/products/windows-11-home-and-pro)
- [Windows 11 Enterprise and Education](/en-us/lifecycle/products/windows-11-enterprise-and-education)

There are two ways to control how and when Windows feature updates are installed on Windows.

| **Feature update control type** | **Configuration** | **Advantages** | **Disadvantages** |
| --- | --- | --- | --- |
| **Automatically keep up to date (recommended)** | Use only **Update ring policies** and set a feature update deferral to 30 or more days | Devices are always kept up to date and receive access to the latest Windows features | Users may not have had training on new features, and some apps may not be compatible with the new feature version |
| **Control feature version** | Use **feature update policies** to keep devices at a particular version of Windows | Devices are kept at a particular Windows version until the policy is changed | The policy must be reviewed and changed periodically to ensure Windows remains supported |

### Automatically keep Windows up to date

Using the **update ring** you configured earlier, set the **Feature update deferral period (days)** to **30** days. The deferral period can be increased or decreased based on the school needs.

### Control feature version

A [Feature update policy](../../../device-updates/windows/configure-feature-update-policy) can be configured to set devices to a particular version of Windows. Devices running older versions of Windows will update to the specified version. Devices with newer versions of Windows won't perform any feature updates.

To set a feature update policy:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** &gt; **By platform** &gt; **Windows** &gt; **Manage updates** &gt; **Windows 10 and later updates** &gt; **Feature updates** tab &gt; **Create profile**.
3. Under **Deployment settings**:
    - Specify a name, a description (optional), and for **Feature update to deploy**, select the version of Windows with the feature set you want, and then select **Next**.
    - Configure **Rollout options** to **As soon as possible**.
4. Under **Assignments**, choose **+ Select groups to include** and then assign the feature updates deployment to one or more device groups. Select **Next** to continue.
5. Under **Review + create**, review the settings. When ready to save the Feature updates policy, select **Create**.

Warning

If you don't review the feature update version at least every 18 months, your Windows devices may no longer receive security updates. Ensure you review and update the feature version to stay supported.