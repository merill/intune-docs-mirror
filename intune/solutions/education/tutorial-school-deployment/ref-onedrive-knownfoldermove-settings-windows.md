---
layout: Conceptual
title: Common Education OneDrive Known Folder Move configuration - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/solutions/education/tutorial-school-deployment/ref-onedrive-knownfoldermove-settings-windows
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: yegor-a
ms.author: egorabr
ms.subservice: education
description: Learn about common OneDrive Known Folder Move configuration used by Education organizations in Intune.
ms.date: 2024-05-02T00:00:00.0000000Z
ms.topic: tutorial
ms.collection:
- graph-interactive
locale: en-us
document_id: bb9fea7d-cb1e-e800-e34e-05f98c05e1eb
document_version_independent_id: bb9fea7d-cb1e-e800-e34e-05f98c05e1eb
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/solutions/education/tutorial-school-deployment/ref-onedrive-knownfoldermove-settings-windows.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
interactive_type: msgraph
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: solutions/education/tutorial-school-deployment/ref-onedrive-knownfoldermove-settings-windows
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/solutions/education/tutorial-school-deployment/ref-onedrive-knownfoldermove-settings-windows.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7428317a-e6c2-4461-ad3e-8a8ad3608734
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/e4f59707-f107-48f2-8d75-0afd91868cd7
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 77e6a0d8-7cf5-846f-5c8c-7f5b9c4ce362
---

# Common Education OneDrive Known Folder Move configuration - Microsoft Intune | Microsoft Learn

Microsoft Intune and Intune for Education can configure the settings to redirect and move Windows known folders to OneDrive. This article summarizes the configurations that are most commonly used for student and teacher devices to enable OneDrive Known Folder Move to redirect the user's Documents, Desktop, and Pictures folders to OneDrive to prevent data loss.

Note

This is an optional policy

To learn more, see:

- [Use the settings catalog to configure settings on Windows, iOS/iPadOS, and macOS devices](../../../device-configuration/settings-catalog/)
- [Redirect and move Windows known folders to OneDrive](/en-us/sharepoint/redirect-known-folders).

Tip

When creating a settings catalog profile in the Microsoft Intune admin center, you can copy a policy name from this article and paste it into the settings picker search field to find the desired policy.

# [Settings](#tab/settings)
### Organization-specific settings catalog policies

| **Category** | **Name** | **Value** | **Notes** | **CSP** |
| --- | --- | --- | --- | --- |
| OneDrive | **Allow syncing OneDrive accounts for only specific organizations** | Enabled | Only enables the setting configuration. | [AllowTenantList](/en-us/sharepoint/use-group-policy#allow-syncing-onedrive-accounts-for-only-specific-organizations) |
| OneDrive | **Allow syncing OneDrive accounts for only specific organizations &gt; Tenant ID: (Device)** | *tenant ID* | **Important!** This is a tenant-specific value. [How to find your Microsoft Entra tenant ID](/en-us/entra/fundamentals/how-to-find-tenant) | [AllowTenantList](/en-us/sharepoint/use-group-policy#allow-syncing-onedrive-accounts-for-only-specific-organizations) |

### General restrictions

| **Category** | **Name** | **Value** | **Notes** | **CSP** |
| --- | --- | --- | --- | --- |
| OneDrive | **Block file downloads when users are low on disk space** | Enabled |  | [MinDiskSpaceLimitInMB](/en-us/sharepoint/use-group-policy#block-file-downloads-when-users-are-low-on-disk-space) |
| OneDrive | **Block file downloads when users are low on disk space &gt; Minimum available disk space: (Device)** | 1024 | Only enables the setting configuration. | [MinDiskSpaceLimitInMB](/en-us/sharepoint/use-group-policy#block-file-downloads-when-users-are-low-on-disk-space) |
| OneDrive | **Convert synced team site files to online-only files** | Enabled | Files in currently syncing team sites are changed to online-only files, by default. Files later added or updated in the team site are also downloaded as online-only files. | [DehydrateSyncedTeamSites](/en-us/sharepoint/use-group-policy#convert-synced-team-site-files-to-online-only-files) |
| OneDrive | **Disable the tutorial that appears at the end of OneDrive Setup (User)** | Enabled |  | [DisableTutorial](/en-us/sharepoint/use-group-policy#disable-the-tutorial-that-appears-at-the-end-of-onedrive-setup) |
| OneDrive | **Prevent users from redirecting their Windows known folders to their PC** | Enabled |  | [KFMBlockOptOut](/en-us/sharepoint/use-group-policy#prevent-users-from-redirecting-their-windows-known-folders-to-their-pc) |
| OneDrive | **Prevent users from syncing libraries and folders shared from other organizations** | Enabled |  | [BlockExternalSync](/en-us/sharepoint/use-group-policy#prevent-users-from-syncing-libraries-and-folders-shared-from-other-organizations) |
| OneDrive | **Prevent users from syncing personal OneDrive accounts (User)** | Enabled |  | [DisablePersonalSync](/en-us/sharepoint/use-group-policy#prevent-users-from-syncing-personal-onedrive-accounts) |
| OneDrive | **Set the sync app update ring** | Enabled | Only enables the setting configuration. | [GPOSetUpdateRing](/en-us/sharepoint/use-group-policy#set-the-sync-app-update-ring) |
| OneDrive | **Set the sync app update ring &gt; Update ring: (Device)** | Production | Users get the latest features as they become available. | [GPOSetUpdateRing](/en-us/sharepoint/use-group-policy#set-the-sync-app-update-ring) |
| OneDrive | **Silently move Windows known folders to OneDrive** | Enabled | **!Important**: Make sure to pick the setting with 5 sub-settings listed below. Redirect and move your users' Documents, Pictures, and/or Desktop folders to OneDrive without any user interaction. | [KFMSilentOptIn](/en-us/sharepoint/use-group-policy#silently-move-windows-known-folders-to-onedrive) |
| OneDrive | **Silently move Windows known folders to OneDrive &gt; Desktop (Device)** | True |  | [KFMSilentOptIn](/en-us/sharepoint/use-group-policy#silently-move-windows-known-folders-to-onedrive) |
| OneDrive | **Silently move Windows known folders to OneDrive &gt; Documents (Device)** | True |  | [KFMSilentOptIn](/en-us/sharepoint/use-group-policy#silently-move-windows-known-folders-to-onedrive) |
| OneDrive | **Silently move Windows known folders to OneDrive &gt; Pictures (Device)** | True |  | [KFMSilentOptIn](/en-us/sharepoint/use-group-policy#silently-move-windows-known-folders-to-onedrive) |
| OneDrive | **Silently move Windows known folders to OneDrive &gt; Show notification to users after folders have been redirected: (Device)** | No |  | [KFMSilentOptIn](/en-us/sharepoint/use-group-policy#silently-move-windows-known-folders-to-onedrive) |
| OneDrive | **Silently move Windows known folders to OneDrive &gt; Tenant ID: (Device)** | *{tenant ID}* |  | [KFMSilentOptIn](/en-us/sharepoint/use-group-policy#silently-move-windows-known-folders-to-onedrive) |
| OneDrive | **Silently sign in users to the OneDrive sync app with their Windows credentials** | Enabled | Users who are signed in on a PC that's joined to Microsoft Entra ID can set up the sync app without entering their account credentials. | [SilentAccountConfig](/en-us/sharepoint/use-group-policy#silently-sign-in-users-to-the-onedrive-sync-app-with-their-windows-credentials) |
| OneDrive | **Use OneDrive Files On-Demand** | Enabled | New users who set up the sync app see online-only files in File Explorer, by default. | [FilesOnDemandEnabled](/en-us/sharepoint/use-group-policy#use-onedrive-files-on-demand) |
| OneDrive | **Warn users who are low on disk space** | Enabled | Only enables the setting configuration. | [WarningMinDiskSpaceLimitInMB](/en-us/sharepoint/use-group-policy#warn-users-who-are-low-on-disk-space) |
| OneDrive | **Warn users who are low on disk space &gt; Minimum available disk space: (Device)** | 2048 | Specify a minimum amount of available disk space in MB, and warn users when the OneDrive sync app (OneDrive.exe) downloads a file that causes them to have less than this amount. | [WarningMinDiskSpaceLimitInMB](/en-us/sharepoint/use-group-policy#warn-users-who-are-low-on-disk-space) |

# [Create policy using Graph Explorer](#tab/graph)
Use Graph to create the settings catalog policy in your tenant without assignments or scope tags.

This will create a policy in your tenant with the name **\_MSLearn\_Example\_CommonEDU - Windows - OneDrive Known Folder Move**.

```msgraph
POST https://graph.microsoft.com/beta/deviceManagement/configurationPolicies
Content-Type: application/json

{"name":"_MSLearn_Example_CommonEDU - Windows - OneDrive Known Folder Move","description":"https://aka.ms/ManageEduDevices","platforms":"windows10","technologies":"mdm","roleScopeTagIds":["0"],"settings":[{"@odata.type":"#microsoft.graph.deviceManagementConfigurationSetting","settingInstance":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingInstance","settingDefinitionId":"device_vendor_msft_policy_config_onedrivengscv2~policy~onedrivengsc_allowtenantlist","choiceSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingValue","value":"device_vendor_msft_policy_config_onedrivengscv2~policy~onedrivengsc_allowtenantlist_1","children":[{"@odata.type":"#microsoft.graph.deviceManagementConfigurationSimpleSettingCollectionInstance","settingDefinitionId":"device_vendor_msft_policy_config_onedrivengscv2~policy~onedrivengsc_allowtenantlist_allowtenantlistbox","simpleSettingCollectionValue":[{"value":" tenantId","@odata.type":"#microsoft.graph.deviceManagementConfigurationStringSettingValue"}]}]}}},{"@odata.type":"#microsoft.graph.deviceManagementConfigurationSetting","settingInstance":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingInstance","settingDefinitionId":"device_vendor_msft_policy_config_onedrivengscv3~policy~onedrivengsc_mindiskspacelimitinmb","choiceSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingValue","value":"device_vendor_msft_policy_config_onedrivengscv3~policy~onedrivengsc_mindiskspacelimitinmb_1","children":[{"@odata.type":"#microsoft.graph.deviceManagementConfigurationSimpleSettingInstance","settingDefinitionId":"device_vendor_msft_policy_config_onedrivengscv3~policy~onedrivengsc_mindiskspacelimitinmb_mindiskspacemb","simpleSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationIntegerSettingValue","value":1024}}]}}},{"@odata.type":"#microsoft.graph.deviceManagementConfigurationSetting","settingInstance":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingInstance","settingDefinitionId":"device_vendor_msft_policy_config_onedrivengscv2~policy~onedrivengsc_dehydratesyncedteamsites","choiceSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingValue","value":"device_vendor_msft_policy_config_onedrivengscv2~policy~onedrivengsc_dehydratesyncedteamsites_1","children":[]}}},{"@odata.type":"#microsoft.graph.deviceManagementConfigurationSetting","settingInstance":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingInstance","settingDefinitionId":"user_vendor_msft_policy_config_onedrivengscv6~policy~onedrivengsc_disablefreanimation","choiceSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingValue","value":"user_vendor_msft_policy_config_onedrivengscv6~policy~onedrivengsc_disablefreanimation_1","children":[]}}},{"@odata.type":"#microsoft.graph.deviceManagementConfigurationSetting","settingInstance":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingInstance","settingDefinitionId":"device_vendor_msft_policy_config_onedrivengscv2~policy~onedrivengsc_blockexternalsync","choiceSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingValue","value":"device_vendor_msft_policy_config_onedrivengscv2~policy~onedrivengsc_blockexternalsync_1","children":[]}}},{"@odata.type":"#microsoft.graph.deviceManagementConfigurationSetting","settingInstance":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingInstance","settingDefinitionId":"user_vendor_msft_policy_config_onedrivengscv2~policy~onedrivengsc_disablepersonalsync","choiceSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingValue","value":"user_vendor_msft_policy_config_onedrivengscv2~policy~onedrivengsc_disablepersonalsync_1","children":[]}}},{"@odata.type":"#microsoft.graph.deviceManagementConfigurationSetting","settingInstance":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingInstance","settingDefinitionId":"device_vendor_msft_policy_config_onedrivengscv2~policy~onedrivengsc_gposetupdatering","choiceSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingValue","value":"device_vendor_msft_policy_config_onedrivengscv2~policy~onedrivengsc_gposetupdatering_1","children":[{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingInstance","settingDefinitionId":"device_vendor_msft_policy_config_onedrivengscv2~policy~onedrivengsc_gposetupdatering_gposetupdatering_dropdown","choiceSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingValue","value":"device_vendor_msft_policy_config_onedrivengscv2~policy~onedrivengsc_gposetupdatering_gposetupdatering_dropdown_5","children":[]}}]}}},{"@odata.type":"#microsoft.graph.deviceManagementConfigurationSetting","settingInstance":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingInstance","settingDefinitionId":"device_vendor_msft_policy_config_onedrivengscv2.updates~policy~onedrivengsc_kfmoptinnowizard","choiceSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingValue","value":"device_vendor_msft_policy_config_onedrivengscv2.updates~policy~onedrivengsc_kfmoptinnowizard_1","children":[{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingInstance","settingDefinitionId":"device_vendor_msft_policy_config_onedrivengscv2.updates~policy~onedrivengsc_kfmoptinnowizard_kfmoptinnowizard_desktop_checkbox","choiceSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingValue","value":"device_vendor_msft_policy_config_onedrivengscv2.updates~policy~onedrivengsc_kfmoptinnowizard_kfmoptinnowizard_desktop_checkbox_1","children":[]}},{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingInstance","settingDefinitionId":"device_vendor_msft_policy_config_onedrivengscv2.updates~policy~onedrivengsc_kfmoptinnowizard_kfmoptinnowizard_documents_checkbox","choiceSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingValue","value":"device_vendor_msft_policy_config_onedrivengscv2.updates~policy~onedrivengsc_kfmoptinnowizard_kfmoptinnowizard_documents_checkbox_1","children":[]}},{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingInstance","settingDefinitionId":"device_vendor_msft_policy_config_onedrivengscv2.updates~policy~onedrivengsc_kfmoptinnowizard_kfmoptinnowizard_pictures_checkbox","choiceSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingValue","value":"device_vendor_msft_policy_config_onedrivengscv2.updates~policy~onedrivengsc_kfmoptinnowizard_kfmoptinnowizard_pictures_checkbox_1","children":[]}},{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingInstance","settingDefinitionId":"device_vendor_msft_policy_config_onedrivengscv2.updates~policy~onedrivengsc_kfmoptinnowizard_kfmoptinnowizard_dropdown","choiceSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingValue","value":"device_vendor_msft_policy_config_onedrivengscv2.updates~policy~onedrivengsc_kfmoptinnowizard_kfmoptinnowizard_dropdown_0","children":[]}},{"@odata.type":"#microsoft.graph.deviceManagementConfigurationSimpleSettingInstance","settingDefinitionId":"device_vendor_msft_policy_config_onedrivengscv2.updates~policy~onedrivengsc_kfmoptinnowizard_kfmoptinnowizard_textbox","simpleSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationStringSettingValue","value":"tenantId"}}]}}},{"@odata.type":"#microsoft.graph.deviceManagementConfigurationSetting","settingInstance":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingInstance","settingDefinitionId":"device_vendor_msft_policy_config_onedrivengscv2~policy~onedrivengsc_silentaccountconfig","choiceSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingValue","value":"device_vendor_msft_policy_config_onedrivengscv2~policy~onedrivengsc_silentaccountconfig_1","children":[]}}},{"@odata.type":"#microsoft.graph.deviceManagementConfigurationSetting","settingInstance":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingInstance","settingDefinitionId":"device_vendor_msft_policy_config_onedrivengscv2~policy~onedrivengsc_filesondemandenabled","choiceSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingValue","value":"device_vendor_msft_policy_config_onedrivengscv2~policy~onedrivengsc_filesondemandenabled_1","children":[]}}},{"@odata.type":"#microsoft.graph.deviceManagementConfigurationSetting","settingInstance":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingInstance","settingDefinitionId":"device_vendor_msft_policy_config_onedrivengscv3~policy~onedrivengsc_warningmindiskspacelimitinmb","choiceSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingValue","value":"device_vendor_msft_policy_config_onedrivengscv3~policy~onedrivengsc_warningmindiskspacelimitinmb_1","children":[{"@odata.type":"#microsoft.graph.deviceManagementConfigurationSimpleSettingInstance","settingDefinitionId":"device_vendor_msft_policy_config_onedrivengscv3~policy~onedrivengsc_warningmindiskspacelimitinmb_warningmindiskspacemb","simpleSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationIntegerSettingValue","value":2048}}]}}}]}
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