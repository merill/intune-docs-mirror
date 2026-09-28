---
layout: Conceptual
title: Common Education iPads with no user affinity configuration - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/solutions/education/tutorial-school-deployment/ref-shared-device-settings-ipados
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: yegor-a
ms.author: egorabr
ms.subservice: education
description: Learn about common iPads with no user affinity configuration used by Education organizations in Intune.
ms.date: 2024-10-16T00:00:00.0000000Z
ms.topic: tutorial
ms.collection:
- graph-interactive
locale: en-us
document_id: 7348a40a-44e5-4eb9-7bcd-d764c8f5c27d
document_version_independent_id: 7348a40a-44e5-4eb9-7bcd-d764c8f5c27d
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/solutions/education/tutorial-school-deployment/ref-shared-device-settings-ipados.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
interactive_type: msgraph
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: solutions/education/tutorial-school-deployment/ref-shared-device-settings-ipados
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/solutions/education/tutorial-school-deployment/ref-shared-device-settings-ipados.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/aebdc4a3-c54b-4eea-94e3-663d5e166f57
- https://authoring-docs-microsoft.poolparty.biz/devrel/2624a017-7337-44fa-9494-a407bb0e59fa
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/1baec8e6-ab38-4b56-bb59-f6282d94f311
- https://authoring-docs-microsoft.poolparty.biz/devrel/a438284e-c3c3-4c36-ab0b-aa7c244b912c
platformId: f0392319-ee78-e93a-76c3-13dcd395228b
---

# Common Education iPads with no user affinity configuration - Microsoft Intune | Microsoft Learn

iPads used in earlier grades are commonly enrolled with no user affinity to simplify the user experience for younger students and to allow sharing of devices. For more information, please refer to [Enroll devices with Automated Device Enrollment](enroll-ios-ade).

These iPads generally have additional restrictions that are not suitable for 1:1 devices.

To learn more, see:

- [Use the settings catalog to configure settings on Windows, iOS/iPadOS and macOS devices](../../../device-configuration/settings-catalog/)
- [Restrictions payload](https://developer.apple.com/documentation/devicemanagement/restrictions)

Tip

When creating a settings catalog profile in the Microsoft Intune admin center, you can copy a policy name from this article and paste it into the settings picker search field to find the desired policy.

# [Settings](#tab/settings)
| **Category** | **Property** | **Value** | **Notes** | **Payload property** |
| --- | --- | --- | --- | --- |
| Restrictions | **Allow Account Modification** | False | Disables modification of accounts such as Apple IDs and Internet-based accounts such as Mail, Contacts, and Calendar. | [allowAccountModification](https://developer.apple.com/documentation/devicemanagement/restrictions) |
| Restrictions | **Allow Bookstore** | False | Removes the Book Store tab from the Books app. | [allowBookstore](https://developer.apple.com/documentation/devicemanagement/restrictions) |
| Restrictions | **Allow Enterprise Book Backup** | False | Disables backup of Enterprise books. | [allowEnterpriseBookBackup](https://developer.apple.com/documentation/devicemanagement/restrictions) |
| Restrictions | **Allow Enterprise Book Metadata Sync** | False | Disables sync of Enterprise books, notes, and highlights. | [allowEnterpriseBookMetadataSync](https://developer.apple.com/documentation/devicemanagement/restrictions) |
| Restrictions | **Allow Fingerprint For Unlock** | False | Prevents Touch ID or Face ID from unlocking a device. | [allowFingerprintForUnlock](https://developer.apple.com/documentation/devicemanagement/restrictions) |
| Restrictions | **Allow Fingerprint Modification** | False | Prevents the user from modifying Touch ID or Face ID. | [allowFingerprintModification](https://developer.apple.com/documentation/devicemanagement/restrictions) |
| Restrictions | **Allow Passcode Modification** | False | Prevents adding, changing, or removing the passcode. | [allowPasscodeModification](https://developer.apple.com/documentation/devicemanagement/restrictions) |
| Restrictions | **Allow Password Auto Fill** | False |  | [allowPasswordAutoFill](https://developer.apple.com/documentation/devicemanagement/restrictions) |
| Restrictions | **Safari Allow Autofill** | False | Disables Safari AutoFill for passwords, contact info, and credit cards and also prevents using the Keychain for AutoFill. | [safariAllowAutoFill](https://developer.apple.com/documentation/devicemanagement/restrictions) |

# [Create policy using Graph Explorer](#tab/graph)
Use Graph to create the settings catalog policy in your tenant without assignments or scope tags.

This will create a policy in your tenant with the name **\_MSLearn\_Example\_CommonEDU - iPads - No user affinity**.

```msgraph
POST https://graph.microsoft.com/beta/deviceManagement/configurationPolicies
Content-Type: application/json

{"name":"_MSLearn_Example_CommonEDU - iPads - No user affinity","description":"","platforms":"iOS","technologies":"mdm,appleRemoteManagement","roleScopeTagIds":["0"],"settings":[{"@odata.type":"#microsoft.graph.deviceManagementConfigurationSetting","settingInstance":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationGroupSettingCollectionInstance","settingDefinitionId":"com.apple.applicationaccess_com.apple.applicationaccess","groupSettingCollectionValue":[{"children":[{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingInstance","settingDefinitionId":"com.apple.applicationaccess_allowaccountmodification","choiceSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingValue","value":"com.apple.applicationaccess_allowaccountmodification_false","children":[]}},{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingInstance","settingDefinitionId":"com.apple.applicationaccess_allowbookstore","choiceSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingValue","value":"com.apple.applicationaccess_allowbookstore_false","children":[]}},{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingInstance","settingDefinitionId":"com.apple.applicationaccess_allowenterprisebookbackup","choiceSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingValue","value":"com.apple.applicationaccess_allowenterprisebookbackup_false","children":[]}},{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingInstance","settingDefinitionId":"com.apple.applicationaccess_allowenterprisebookmetadatasync","choiceSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingValue","value":"com.apple.applicationaccess_allowenterprisebookmetadatasync_false","children":[]}},{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingInstance","settingDefinitionId":"com.apple.applicationaccess_allowfingerprintforunlock","choiceSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingValue","value":"com.apple.applicationaccess_allowfingerprintforunlock_false","children":[]}},{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingInstance","settingDefinitionId":"com.apple.applicationaccess_allowfingerprintmodification","choiceSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingValue","value":"com.apple.applicationaccess_allowfingerprintmodification_false","children":[]}},{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingInstance","settingDefinitionId":"com.apple.applicationaccess_allowpasscodemodification","choiceSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingValue","value":"com.apple.applicationaccess_allowpasscodemodification_false","children":[]}},{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingInstance","settingDefinitionId":"com.apple.applicationaccess_allowpasswordautofill","choiceSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingValue","value":"com.apple.applicationaccess_allowpasswordautofill_false","children":[]}},{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingInstance","settingDefinitionId":"com.apple.applicationaccess_safariallowautofill","choiceSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingValue","value":"com.apple.applicationaccess_safariallowautofill_false","children":[]}}]}]}}]}
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