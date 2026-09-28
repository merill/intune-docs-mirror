---
layout: Conceptual
title: View BitLocker reports - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/protect/deploy-use/bitlocker/view-reports
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
description: Learn about the BitLocker management reports in Configuration Manager
ms.date: 2021-11-23T00:00:00.0000000Z
ms.subservice: protect
ms.topic: reference
ms.collection: tier3
ms.custom: sfi-image-nochange
locale: en-us
document_id: ec4c8398-a7f9-abd8-e76e-b472c647958f
document_version_independent_id: c9667799-90fd-295b-18d7-f114474a1da8
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/protect/deploy-use/bitlocker/view-reports.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/protect/deploy-use/bitlocker/view-reports
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/protect/deploy-use/bitlocker/view-reports.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7cbaac1e-1137-4825-819f-cd751d73c036
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/eda7d4a5-11e2-4d6f-b379-0d496f2a17a5
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: 6fa11397-3c0f-970f-d288-ade955e66f16
---

# View BitLocker reports - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

After you [install the reports](setup-websites) on the reporting services point, you can view the reports. The reports show BitLocker compliance for the enterprise and for individual devices. They provide tabular information and charts, and have filters that let you view data from different perspectives.

In the Configuration Manager console, go to the **Monitoring** workspace, expand **Reporting**, and select the **Reports** node. The following reports are in the **BitLocker Management** category:

- BitLocker Computer Compliance
- BitLocker Enterprise Compliance Dashboard
- BitLocker Enterprise Compliance Details
- BitLocker Enterprise Compliance Summary
- Recovery Audit Report

You can access all of these reports directly from the reporting services point website.

Note

For these reports to display complete data:

- Create and deploy a BitLocker management policy to a device collection
- Clients in the target collection need to send hardware inventory

## BitLocker computer compliance

Use this report to collect information that's specific to a computer. It provides detailed encryption information about the OS drive and any fixed data drives. To view the details of each drive, expand the Computer Name entry. It also indicates the policy that's applied to each drive type on the computer.

[![Example screenshot of BitLocker computer compliance report](media/bitlocker-computer-compliance.png)](media/bitlocker-computer-compliance.png#lightbox)

You can also use this report to determine the last known BitLocker encryption status of lost or stolen computers. Configuration Manager determines compliance of the device based on the BitLocker policies that you deploy. Before you try to determine the BitLocker encryption state of a device, verify the policies that you've deployed to it.

Note

This report doesn't show the Removable Data Volume encryption status.

### Computer details

| Column name | Description |
| --- | --- |
| Computer name | User-specified DNS computer name. |
| Domain name | Fully qualified domain name for the computer. |
| Computer Type | Type of computer, valid types are **Non-Portable** and **Portable**. |
| Operating system | OS type of the computer. |
| Overall compliance | Overall BitLocker compliance status of the computer. Valid states are **Compliant** and **Non-compliant**. The compliance status per drive may indicate different compliance states. However, this field represents that compliance state from the specified policy. |
| Operating system compliance | Compliance status of the OS on the computer. Valid states are **Compliant** and **Non-compliant**. |
| Fixed data drive compliance | Compliance status of a fixed data drive on the computer. Valid states are **Compliant** and **Non-compliant**. |
| Last update date | Date and time that the computer last contacted the server to report compliance status. |
| Exemption | Indicates whether the user is exempt or non-exempt from the BitLocker policy. |
| Exempted user | The user who's exempt from the BitLocker policy. |
| Exemption date | Date on which the exemption was granted. |
| Compliance status details | Error and status messages about the compliance state of the computer from the specified policy. |
| Policy cipher strength | Cipher strength that you selected in the BitLocker management policy. |
| Policy: Operating system drive | Indicates if encryption is required for the OS drive and the appropriate protector type. |
| Policy: Fixed data drive | Indicates if encryption is required for the fixed data drive. |
| Manufacturer | Computer manufacturer name as it appears in the computer BIOS. |
| Model | Computer manufacturer model name as it appears in the computer BIOS. |
| Device users | Known users on the computer. |

### Computer volume

| Column name | Description |
| --- | --- |
| Drive letter | The drive letter on the computer. |
| Drive type | Type of drive. Valid values are **Operating System Drive** and **Fixed Data Drive**. These entries are physical drives rather than logical volumes. |
| Cipher strength | Cipher strength that you selected during in the BitLocker management policy. |
| Protector types | Type of protector that you selected in the policy to encrypt the drive. The valid protector types for an OS drive are **TPM** or **TPM+PIN**. The valid protector type for a fixed data drive is **Password**. |
| Protector state | Indicates that the computer enabled the protector type specified in the policy. The valid states are **ON** or **OFF**. |
| Encryption state | Encryption state of the drive. Valid states are **Encrypted**, **Not Encrypted**, or **Encrypting**. |

## BitLocker enterprise compliance dashboard

This report provides the following graphs, which show BitLocker compliance status across your organization:

- Compliance status distribution
- Non-compliant - Errors distribution
- Compliance status distribution by drive type

[![Example screenshot of BitLocker enterprise compliance dashboard](media/bitlocker-enterprise-compliance-dashboard.png)](media/bitlocker-enterprise-compliance-dashboard.png#lightbox)

### Compliance status distribution

This pie chart shows compliance status for computers in the organization. It also shows the percentage of computers with that compliance status, compared to the total number of computers in the selected collection. The actual number of computers with each status is also shown.

The pie chart shows the following compliance statuses:

- Compliant
- Non-compliant
- User exempt
- Temporary user exempt
- Policy not enforced

    Note

    This state may be caused by a device that's encrypted and previously escrowed its key, but can't currently escrow its key. Because it can't escrow its key it doesn't enforce policy anymore.
- Unknown. These computers reported a status error, or they're part of the collection but have never reported their compliance status. The lack of a compliance status could occur if the computer is disconnected from the organization.

### Non-compliant - Errors distribution

This pie chart shows the categories of computers in your organization that aren't compliant with the BitLocker Drive Encryption policy. It also shows the number of computers in each category. The report calculates each percentage from the total number of non-compliant computers in the collection.

- User postponed encryption
- Unable to find compatible TPM
- System partition not available or large enough
- TPM visible but not initialized
- Policy conflict
- Waiting for TPM auto provisioning
- An unknown error has occurred
- No information. These computers don't have the BitLocker management agent installed, or it's installed but not activated. For example, the service isn't working.

### Compliance status distribution by drive type

This bar chart shows the current BitLocker compliance status by drive type. The statuses are **Compliant** and **Non-compliant**. Bars are shown for fixed data drives and OS drives. The report includes computers without a fixed data drive, and only shows a value in the **Operating System Drive** bar. The chart doesn't include users who have been granted an exemption from the BitLocker Drive Encryption policy or the No Policy category.

## BitLocker enterprise compliance details

This report shows information about the overall BitLocker compliance across your organization for the collection of computers to which you deployed the BitLocker management policy.

[![Example screenshot of BitLocker enterprise compliance details](media/bitlocker-enterprise-compliance-details.png)](media/bitlocker-enterprise-compliance-details.png#lightbox)

| Column name | Description |
| --- | --- |
| Managed computers | Number of computers to which you deployed a BitLocker management policy. |
| % Compliant | Percentage of compliant computers in the organization. |
| % Non-compliant | Percentage of non-compliant computers in the organization. |
| % Unknown compliance | Percentage of computers with a compliance state that's not known. |
| % Exempt | Percentage of computers exempt from the BitLocker encryption requirement. |
| % Non-exempt | Percentage of computers not exempt from the BitLocker encryption requirement. |
| Compliant | Count of compliant computers in the organization. |
| Non-Compliant | Count of non-compliant computers in the organization. |
| Unknown Compliance | Count of computers with a compliance state that's not known. |
| Exempt | Count of computers that are exempt from the BitLocker encryption requirement. |
| Non-exempt | Count of computers that aren't exempt from the BitLocker encryption requirement. |

### Computer details

| Column name | Description |
| --- | --- |
| Computer name | DNS computer name of the managed device. |
| Domain name | Fully qualified domain name for the computer. |
| Compliance status | Overall compliance status of the computer. Valid states are **Compliant** and **Non-compliant**. |
| Exemption | Indicates whether the user is exempt or non-exempt from the BitLocker policy. |
| Device users | Users of the device. |
| Compliance status details | Error and status messages about the compliance state of the computer from the specified policy. |
| Last contact | Date and time that the computer last contacted the server to report compliance status. |

## BitLocker enterprise compliance summary

Use this report to show the overall BitLocker compliance across your organization. It also shows the compliance for individual computers to which you deployed the BitLocker management policy.

[![Example screenshot of BitLocker enterprise compliance summary](media/bitlocker-enterprise-compliance-summary.png)](media/bitlocker-enterprise-compliance-summary.png#lightbox)

| Column name | Description |
| --- | --- |
| Managed computers | Number of computers that you manage with BitLocker policy. |
| % Compliant | Percentage of compliant computers in your organization. |
| % Non-compliant | Percentage of non-compliant computers in your organization. |
| % Unknown compliance | Percentage of computers with a compliance state that's not known. |
| % Exempt | Percentage of computers exempt from the BitLocker encryption requirement. |
| % Non-exempt | Percentage of computers not exempt from the BitLocker encryption requirement. |
| Compliant | Count of compliant computers in your organization. |
| Non-compliant | Count of non-compliant computers in your organization. |
| Unknown compliance | Count of computers with a compliance state that's not known. |
| Exempt | Count of computers that are exempt from the BitLocker encryption requirement. |
| Non-exempt | Count of computers that aren't exempt from the BitLocker encryption requirement. |

## Recovery audit report

Note

This report is only available from the [BitLocker administration and monitoring website](helpdesk-portal#reports).

Use this report to audit users who have requested access to BitLocker recovery keys. You can filter on the following criteria:

- A specific type of user, for example, a help desk user or an end user
- If the request failed or was successful
- The specific type of key requested: Recovery Key Password, Recovery Key ID, or TPM Password Hash
- A date range during which the retrieval occurred

[![Example screenshot of BitLocker Recovery audit report](media/bitlocker-recovery-audit-report.png)](media/bitlocker-recovery-audit-report.png#lightbox)

| Column name | Description |
| --- | --- |
| Request date and time | Date and time that an end user or help desk user requested a key. |
| Audit request source | The site from where the request came. Valid values are **Self-Service Portal** or **Helpdesk**. |
| Request result | Status of the request. Valid values are **Successful** or **Failed**. |
| Helpdesk user | The administrative user who requested the key. If a helpdesk admin recovers the key without specifying the user name, the **End User** field is blank. A standard helpdesk user must specify the user name, which appears in this field. For recovery via the self-service portal, this field and the **End User** field display the name of the user making the request. |
| End user | Name of the user who requested key retrieval. |
| Computer | Name of the computer that was recovered. |
| Key type | Type of key that the user requested. The three types of keys are:- **Recovery key password**: used to recover a computer in recovery mode- **Recovery key ID**: used to recover a computer in recovery mode for another user- **TPM password hash**: used to recover a computer with a locked TPM |
| Reason description | Why the user requested the specified key type, based upon the option they selected in the form. |