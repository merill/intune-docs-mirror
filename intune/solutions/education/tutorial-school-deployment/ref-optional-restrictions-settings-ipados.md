---
layout: Conceptual
title: Common Education iPads optional configuration - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/solutions/education/tutorial-school-deployment/ref-optional-restrictions-settings-ipados
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: yegor-a
ms.author: egorabr
ms.subservice: education
description: Learn about common iPads optional configuration used by Education organizations in Intune.
ms.date: 2024-10-16T00:00:00.0000000Z
ms.topic: tutorial
ms.collection:
- graph-interactive
locale: en-us
document_id: bcc57ec5-0987-3fd6-d348-34e8ae65f2c7
document_version_independent_id: bcc57ec5-0987-3fd6-d348-34e8ae65f2c7
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/solutions/education/tutorial-school-deployment/ref-optional-restrictions-settings-ipados.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
interactive_type: msgraph
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: solutions/education/tutorial-school-deployment/ref-optional-restrictions-settings-ipados
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/solutions/education/tutorial-school-deployment/ref-optional-restrictions-settings-ipados.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: cc21d0e4-bc89-a4e7-be87-dcfcfb798e00
---

# Common Education iPads optional configuration - Microsoft Intune | Microsoft Learn

Optional policies, while relatively common, are provided for more situational use cases.

To learn more, see:

- [Use the settings catalog to configure settings on Windows, iOS/iPadOS and macOS devices](../../../device-configuration/settings-catalog/)
- [Restrictions payload](https://developer.apple.com/documentation/devicemanagement/restrictions)

Tip

When creating a settings catalog profile in the Microsoft Intune admin center, you can copy a policy name from this article and paste it into the settings picker search field to find the desired policy.

# [Settings](#tab/settings)
| **Category** | **Property** | **Value** | **Notes** | **Payload property** |
| --- | --- | --- | --- | --- |
| Managed Settings &gt; Bluetooth | **Enabled** | True | Enable the Bluetooth setting. | [Enabled](https://developer.apple.com/documentation/devicemanagement/settingscommand/command/settings/bluetooth) |
| Restrictions | **Force Automatic Date And Time** | True | Enables the Set Automatically feature in Date & Time and the user can't disable it.**Note:**<br>- Location services must be enabled during Setup Assistant.<br>- Manual Time Zone policy will return an error if this policy is set to True. | [forceAutomaticDateAndTime](https://developer.apple.com/documentation/devicemanagement/restrictions) |
| Managed Settings &gt; Time Zone | **Time Zone** | **Example**:America/Los\_AngelesAsia/TokyoAustralia/BrisbaneSee complete list in [IANA time zone database](https://data.iana.org/time-zones/tzdb/zone.tab). | If the **forceAutomaticDateAndTime** restriction is set in Restrictions, this setting fails with an error. Otherwise, setting this value disables automatic time zone logic. The user is still able to change the time zone; for example, by turning automatic date and time back on. The intention is to allow setting the time zone when automatic determination isn't available, such as when Location Services are off. | [TimeZone](https://developer.apple.com/documentation/devicemanagement/settingscommand/command/settings/timezone) |
| Restrictions | **Allow Bluetooth Modification** | False | Prevents modification of Bluetooth settings. | [allowBluetoothModification](https://developer.apple.com/documentation/devicemanagement/restrictions) |
| Restrictions | **Allow USB Restricted Mode** | True | Allows iOS devices to always connect to USB accessories while locked. If the system has Lockdown mode enabled, it ignores this value. | [allowUSBRestrictedMode](https://developer.apple.com/documentation/devicemanagement/restrictions) |
| Restrictions | **Blocked App Bundle IDs** | **Example:**com.apple.facetimecom.apple.findmycom.apple.Homecom.apple.MobileStorecom.apple.MobileSMScom.apple.Musiccom.apple.podcastscom.apple.stockscom.apple.tvcom.apple.store.Jollycom.apple.supportapp | Prevents showing or launching apps with bundle IDs in the array. | [blockedAppBundleIDs](https://developer.apple.com/documentation/devicemanagement/restrictions) |
| Restrictions | **Enforced Software Update Delay** | 30 | How many days to delay a software update on the device. | [enforcedSoftwareUpdateDelay](https://developer.apple.com/documentation/devicemanagement/restrictions) |
| Restrictions | **Force Classroom Automatically Join Classes** | True | Automatically gives permission to the teacher's requests without prompting the student. | [forceClassroomAutomaticallyJoinClasses](https://developer.apple.com/documentation/devicemanagement/restrictions) |
| Restrictions | **Force Classroom Request Permission To Leave Classes** | True | A student enrolled in an unmanaged course through Classroom needs to request permission from the teacher to leave the course. | [forceClassroomRequestPermissionToLeaveClasses](https://developer.apple.com/documentation/devicemanagement/restrictions) |
| Restrictions | **Force Classroom Unprompted App And Device Lock** | True | Allows the teacher to lock apps or the device without prompting the student. | [forceClassroomUnpromptedAppAndDeviceLock](https://developer.apple.com/documentation/devicemanagement/restrictions) |
| Restrictions | **Force Classroom Unprompted Screen Observation** | True | If true and ScreenObservationPermissionModificationAllowed is also true in the [Education](https://developer.apple.com/documentation/devicemanagement/educationconfiguration) payload, a student enrolled in a managed course through the Classroom app automatically gives permission to that course teacher's requests to observe the student's screen without prompting the student. | [forceClassroomUnpromptedScreenObservation](https://developer.apple.com/documentation/devicemanagement/restrictions) |
| Restrictions | **Force Preserve ESIM On Erase** | True | Preserves eSIM when it erases the device due to too many failed password attempts or the Erase All Content and Settings option.**Note:** Doesn't preserve eSIM if Find My initiates erasing the device. | [forcePreserveESIMOnErase](https://developer.apple.com/documentation/devicemanagement/restrictions) |
| System Configuration &gt; Lock Screen Message | **Asset Tag Information** | {{devicename}} | Displayed in the login window and Lock screen. | [AssetTagInformation](https://developer.apple.com/documentation/devicemanagement/lockscreenmessage) |
| System Configuration &gt; Lock Screen Message | **Lock Screen Footnote** | **Example**: School of Fine Art | The footnote displayed in the login window and Lock screen. | [LockScreenFootnote](https://developer.apple.com/documentation/devicemanagement/lockscreenmessage) |

# [Create policy using Graph Explorer](#tab/graph)
Use Graph to create the settings catalog policy in your tenant without assignments or scope tags.

This will create a policy in your tenant with the name **\_MSLearn\_Example\_CommonEDU - iPads - Optional**.

```msgraph
POST https://graph.microsoft.com/beta/deviceManagement/configurationPolicies
Content-Type: application/json

{"name":"_MSLearn_Example_CommonEDU - iPads - Optional","description":"","platforms":"iOS","technologies":"mdm,appleRemoteManagement","roleScopeTagIds":["0"],"settings":[{"@odata.type":"#microsoft.graph.deviceManagementConfigurationSetting","settingInstance":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationGroupSettingCollectionInstance","settingDefinitionId":"settings_item_bluetooth","groupSettingCollectionValue":[{"children":[{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingInstance","settingDefinitionId":"settings_item_bluetooth_enabled","choiceSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingValue","value":"settings_item_bluetooth_enabled_true","children":[]}}]}]}},{"@odata.type":"#microsoft.graph.deviceManagementConfigurationSetting","settingInstance":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationGroupSettingCollectionInstance","settingDefinitionId":"settings_item_timezone","groupSettingCollectionValue":[{"children":[{"@odata.type":"#microsoft.graph.deviceManagementConfigurationSimpleSettingInstance","settingDefinitionId":"settings_item_timezone_timezone","simpleSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationStringSettingValue","value":"America/Los_Angeles"}}]}]}},{"@odata.type":"#microsoft.graph.deviceManagementConfigurationSetting","settingInstance":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationGroupSettingCollectionInstance","settingDefinitionId":"com.apple.applicationaccess_com.apple.applicationaccess","groupSettingCollectionValue":[{"children":[{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingInstance","settingDefinitionId":"com.apple.applicationaccess_allowbluetoothmodification","choiceSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingValue","value":"com.apple.applicationaccess_allowbluetoothmodification_false","children":[]}},{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingInstance","settingDefinitionId":"com.apple.applicationaccess_allowusbrestrictedmode","choiceSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingValue","value":"com.apple.applicationaccess_allowusbrestrictedmode_true","children":[]}},{"@odata.type":"#microsoft.graph.deviceManagementConfigurationSimpleSettingCollectionInstance","settingDefinitionId":"com.apple.applicationaccess_blockedappbundleids","simpleSettingCollectionValue":[{"value":"com.apple.facetime","@odata.type":"#microsoft.graph.deviceManagementConfigurationStringSettingValue"},{"value":"com.apple.findmy","@odata.type":"#microsoft.graph.deviceManagementConfigurationStringSettingValue"},{"value":"com.apple.Home","@odata.type":"#microsoft.graph.deviceManagementConfigurationStringSettingValue"},{"value":"com.apple.MobileStore","@odata.type":"#microsoft.graph.deviceManagementConfigurationStringSettingValue"},{"value":"com.apple.MobileSMS","@odata.type":"#microsoft.graph.deviceManagementConfigurationStringSettingValue"},{"value":"com.apple.Music","@odata.type":"#microsoft.graph.deviceManagementConfigurationStringSettingValue"},{"value":"com.apple.podcasts","@odata.type":"#microsoft.graph.deviceManagementConfigurationStringSettingValue"},{"value":"com.apple.stocks","@odata.type":"#microsoft.graph.deviceManagementConfigurationStringSettingValue"},{"value":"com.apple.tv","@odata.type":"#microsoft.graph.deviceManagementConfigurationStringSettingValue"},{"value":"com.apple.store.Jolly","@odata.type":"#microsoft.graph.deviceManagementConfigurationStringSettingValue"},{"value":"com.apple.supportapp","@odata.type":"#microsoft.graph.deviceManagementConfigurationStringSettingValue"}]},{"@odata.type":"#microsoft.graph.deviceManagementConfigurationSimpleSettingInstance","settingDefinitionId":"com.apple.applicationaccess_enforcedsoftwareupdatedelay","simpleSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationIntegerSettingValue","value":30}},{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingInstance","settingDefinitionId":"com.apple.applicationaccess_forceautomaticdateandtime","choiceSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingValue","value":"com.apple.applicationaccess_forceautomaticdateandtime_true","children":[]}},{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingInstance","settingDefinitionId":"com.apple.applicationaccess_forceclassroomautomaticallyjoinclasses","choiceSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingValue","value":"com.apple.applicationaccess_forceclassroomautomaticallyjoinclasses_true","children":[]}},{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingInstance","settingDefinitionId":"com.apple.applicationaccess_forceclassroomrequestpermissiontoleaveclasses","choiceSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingValue","value":"com.apple.applicationaccess_forceclassroomrequestpermissiontoleaveclasses_true","children":[]}},{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingInstance","settingDefinitionId":"com.apple.applicationaccess_forceclassroomunpromptedappanddevicelock","choiceSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingValue","value":"com.apple.applicationaccess_forceclassroomunpromptedappanddevicelock_true","children":[]}},{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingInstance","settingDefinitionId":"com.apple.applicationaccess_forceclassroomunpromptedscreenobservation","choiceSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingValue","value":"com.apple.applicationaccess_forceclassroomunpromptedscreenobservation_true","children":[]}},{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingInstance","settingDefinitionId":"com.apple.applicationaccess_forcepreserveesimonerase","choiceSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingValue","value":"com.apple.applicationaccess_forcepreserveesimonerase_true","children":[]}}]}]}},{"@odata.type":"#microsoft.graph.deviceManagementConfigurationSetting","settingInstance":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationGroupSettingCollectionInstance","settingDefinitionId":"com.apple.shareddeviceconfiguration_com.apple.shareddeviceconfiguration","groupSettingCollectionValue":[{"children":[{"@odata.type":"#microsoft.graph.deviceManagementConfigurationSimpleSettingInstance","settingDefinitionId":"com.apple.shareddeviceconfiguration_assettaginformation","simpleSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationStringSettingValue","value":"{{devicename}}"}},{"@odata.type":"#microsoft.graph.deviceManagementConfigurationSimpleSettingInstance","settingDefinitionId":"com.apple.shareddeviceconfiguration_lockscreenfootnote","simpleSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationStringSettingValue","value":"MSLearn_Example_CommonEDU"}}]}]}}]}
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