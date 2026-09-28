---
layout: Conceptual
title: Common Education Start menu configuration - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/solutions/education/tutorial-school-deployment/ref-start-menu-settings-windows
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: yegor-a
ms.author: egorabr
ms.subservice: education
description: Learn about common Start menu configuration used by Education organizations in Intune.
ms.date: 2024-05-02T00:00:00.0000000Z
ms.topic: tutorial
ms.collection:
- graph-interactive
locale: en-us
document_id: 7fbdb5c2-28e3-90f1-ae0a-5edbbcb1cacc
document_version_independent_id: 7fbdb5c2-28e3-90f1-ae0a-5edbbcb1cacc
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/solutions/education/tutorial-school-deployment/ref-start-menu-settings-windows.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
interactive_type: msgraph
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: solutions/education/tutorial-school-deployment/ref-start-menu-settings-windows
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/solutions/education/tutorial-school-deployment/ref-start-menu-settings-windows.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 15eb53b4-6da0-5739-94a4-5391deffdd08
---

# Common Education Start menu configuration - Microsoft Intune | Microsoft Learn

Microsoft Intune and Intune for Education can configure settings for a customized Start menu for Windows. This article summarizes the configurations that are most commonly used for student and teacher devices.

Students can benefit from a Start menu that is customized to provide access to educational tools and resources while restricting distractions. By configuring policy settings, educational institutions can create a focused and conducive learning environment.

Note

This policy is optional.

**To learn more**, see:

- [Use the settings catalog to configure settings on Windows, iOS/iPadOS, and macOS devices](../../../device-configuration/settings-catalog/)
- [Customize the Start menu and taskbar layout on Windows devices](/en-us/windows/configuration/start/windows-10-start-layout-options-and-policies)
- [Customize and export the Start layout](/en-us/windows/configuration/start/customize-and-export-start-layout)
- [Configure Windows Taskbar](/en-us/windows/configuration/taskbar/?pivots=windows-11)

Tip

When creating a settings catalog profile in the Microsoft Intune admin center, you can copy a policy name from this article and paste it into the settings picker search field to find the desired policy.

# [Settings](#tab/settings)
| **Category** | **Name** | **Value** | **Notes** | **CSP** |
| --- | --- | --- | --- | --- |
| Start | **Start Layout** | A custom XML string | Create and deploy a custom Start menu and taskbar layout. Refer to articles in the previous section in this article. | [StartLayout](/en-us/windows/client-management/mdm/policy-csp-start#startlayout) |
| Start | **Hide App List** | None |  | [Start/HideAppList](/en-us/windows/client-management/mdm/policy-csp-start#hideapplist) |
| Start | **Hide Change Account Settings** | Disabled |  | [Start/HideChangeAccountSettings](/en-us/windows/client-management/mdm/policy-csp-start#hidechangeaccountsettings) |
| Start | **Hide Frequently Used Apps** | Enabled |  | [Start/HideFrequentlyUsedApps](/en-us/windows/client-management/mdm/policy-csp-start#hidefrequentlyusedapps) |
| Start | **Hide Power Button** | Disabled |  | [Start/HidePowerButton](/en-us/windows/client-management/mdm/policy-csp-start#hidepowerbutton) |
| Start | **Hide Recent Jumplists** | Enabled |  | [Start/HideRecentJumplists](/en-us/windows/client-management/mdm/policy-csp-start#hiderecentjumplists) |
| Start | **Hide Recently Added Apps** | Enabled |  | [Start/HideRecentlyAddedApps](/en-us/windows/client-management/mdm/policy-csp-start#hiderecentlyaddedapps) |
| Start | **Hide User Tile** | Disabled |  | [Start/HideUserTile](/en-us/windows/client-management/mdm/policy-csp-start#hideusertile) |
| Start | **Hide Lock** | Disabled |  | [Start/HideLock](/en-us/windows/client-management/mdm/policy-csp-start#hidelock) |
| Start | **Hide Sign Out** | Disabled |  | [Start/HideSignOut](/en-us/windows/client-management/mdm/policy-csp-start#hidesignout) |

# [Create policy using Graph Explorer](#tab/graph)
Use Graph to create the settings catalog policy in your tenant without assignments or scope tags.

This creates a policy in your tenant with the name **\_MSLearn\_Example\_CommonEDU - Windows - Start menu**.

```msgraph
POST https://graph.microsoft.com/beta/deviceManagement/configurationPolicies
Content-Type: application/json

{"name":"_MSLearn_Example_CommonEDU - Windows - Start menu","description":"https://aka.ms/ManageEduDevices","platforms":"windows10","technologies":"mdm","roleScopeTagIds":["0"],"settings":[{"@odata.type":"#microsoft.graph.deviceManagementConfigurationSetting","settingInstance":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingInstance","settingDefinitionId":"device_vendor_msft_policy_config_start_hideapplist","choiceSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingValue","value":"device_vendor_msft_policy_config_start_hideapplist_0","children":[]}}},{"@odata.type":"#microsoft.graph.deviceManagementConfigurationSetting","settingInstance":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingInstance","settingDefinitionId":"device_vendor_msft_policy_config_start_hidechangeaccountsettings","choiceSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingValue","value":"device_vendor_msft_policy_config_start_hidechangeaccountsettings_0","children":[]}}},{"@odata.type":"#microsoft.graph.deviceManagementConfigurationSetting","settingInstance":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingInstance","settingDefinitionId":"device_vendor_msft_policy_config_start_hidefrequentlyusedapps","choiceSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingValue","value":"device_vendor_msft_policy_config_start_hidefrequentlyusedapps_1","children":[]}}},{"@odata.type":"#microsoft.graph.deviceManagementConfigurationSetting","settingInstance":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingInstance","settingDefinitionId":"device_vendor_msft_policy_config_start_hidepowerbutton","choiceSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingValue","value":"device_vendor_msft_policy_config_start_hidepowerbutton_0","children":[]}}},{"@odata.type":"#microsoft.graph.deviceManagementConfigurationSetting","settingInstance":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingInstance","settingDefinitionId":"device_vendor_msft_policy_config_start_hiderecentjumplists","choiceSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingValue","value":"device_vendor_msft_policy_config_start_hiderecentjumplists_1","children":[]}}},{"@odata.type":"#microsoft.graph.deviceManagementConfigurationSetting","settingInstance":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingInstance","settingDefinitionId":"device_vendor_msft_policy_config_start_hiderecentlyaddedapps","choiceSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingValue","value":"device_vendor_msft_policy_config_start_hiderecentlyaddedapps_1","children":[]}}},{"@odata.type":"#microsoft.graph.deviceManagementConfigurationSetting","settingInstance":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingInstance","settingDefinitionId":"device_vendor_msft_policy_config_start_hideusertile","choiceSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingValue","value":"device_vendor_msft_policy_config_start_hideusertile_0","children":[{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingInstance","settingDefinitionId":"device_vendor_msft_policy_config_start_hidelock","choiceSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingValue","value":"device_vendor_msft_policy_config_start_hidelock_0","children":[]}},{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingInstance","settingDefinitionId":"device_vendor_msft_policy_config_start_hidesignout","choiceSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingValue","value":"device_vendor_msft_policy_config_start_hidesignout_0","children":[]}}]}}},{"@odata.type":"#microsoft.graph.deviceManagementConfigurationSetting","settingInstance":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationSimpleSettingInstance","settingDefinitionId":"device_vendor_msft_policy_config_start_startlayout","simpleSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationStringSettingValue","value":""}}}]}
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