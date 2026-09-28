---
layout: Conceptual
title: Applicability rules - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/sum/tools/updates-publisher-applicability-rules
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
description: Manage applicability rules for System Center Updates Publisher
ms.date: 2017-04-29T00:00:00.0000000Z
ms.subservice: software-updates
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 0975b543-e730-cab1-bcc1-b0fbea952c40
document_version_independent_id: 9d1d5830-2f46-94be-62d1-fc88168e39ec
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/sum/tools/updates-publisher-applicability-rules.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/sum/tools/updates-publisher-applicability-rules
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/sum/tools/updates-publisher-applicability-rules.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/aa9d0281-4c35-44bb-8c75-a0920bde2014
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/c7449412-70b0-48ea-831f-3b132eafb97e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
platformId: 729663fc-0239-086e-4e19-9eda41c09c7a
---

# Applicability rules - Configuration Manager | Microsoft Learn

*Applies to: System Center Updates Publisher*

With Updates Publisher, applicability rules define requirements that must be met before a device can install an update. The rules are also used to determine if the computer has an update installed. An applicability rule that is complex with multiple parts is referred to as a rule set.

Update bundles do not use applicability rules.

## Overview of applicability rules

You manage applicability rules from the **Rules Workspace**. When you create a rule, you are specifying one or more conditions. When multiple conditions are specified, you can configure relationships between the conditions so they are evaluated sequentially or combined into logical **And** or **Or** statements.

For example, the following is a rule set that contains three rules. The first rule verifies that the *MyFile* file exists, and the second and third rules verify that the language of the Windows operating system is either English or Japanese.

```Example
And
  File '\[PROGRAM\_FILES\] \\Microsoft\\MyFile' exists
  Or
    Windows Language is English
    Windows Language is Japanese
```

All updates require at least one applicability rule. Updates you import already have applicability rules applied, and when you create your own updates, you must add one or more rules to them. You can modify and expand on the rules for any update in Updates Publisher.

To view rules you have created, in the **Rules Workspace**, select a rule from the **My saved rules** list. The individual conditions and logical operations for that rule display in the **Applicability Rules** pane of the console. Rules for updates that you import can only be viewed and modified when you edit that update.

You can create rules in two locations in Updates Publisher:

- In the **Rules Workspace,** you create and **save** rule sets that you can then use later. When editing or creating an update you can select **Saved rule** as the **Rule type**, and then select from a list of your pre-created rule sets.
- You can also create new rules at the time that you create or edit an update. Rules you create in this way are not saved for future use.

## Create applicability rule

The following information is similar to how you create rules from within the [Create Update wizard](create-updates-with-updates-publisher#use-the-create-update-wizard). But unlike the wizard, you have the option to save your rule sets for future use.

1. In the **Rules Workspace**, choose **Create** to open the **Create Rule** wizard.
2. Specify a name for the rule, and then click ![New Rule](media/newrule.png). This opens the **Applicability Rule** page where you can configure rules.
3. For **Rule type,** select one of the following. The options you must configure vary for each type:

    - **File** – Use this rule to require that a device have a file with properties that meet one or more criteria you specify before this update can be applied.
    - **Registry –** Use this type to specify registry details that must be present before a device qualifies to install this update.
    - **System –** This rule uses system details to determine applicability. You can choose between defining a Windows version, a Windows language, processor architecture, or specify a WMI query to identify the devices operating system.
    - **Windows Installer –** Use this rule type to determine applicability based on an installed .MSI or Windows Installer patch (.MSP). You can also determine if specific components or features are installed as part of the requirement.

        Important

        On managed deices, the Windows Update Agent cannot detect Windows Install packages that are installed per-user. When you use this rule type, configure additional applicability rules, like file versions or registry key values, so that the Windows Installer package can be properly detected regardless of a per-user or per-system basis.
    - **Saved rule –** This option lets you find and use rules that you previously configured and saved.
4. Continue to add and configure additional rules as desired.
5. Use the logical operation buttons to order and group different rules to create more complex prerequisite checks.
6. When the rule set is complete, click **OK** to save it. The rule set now appears in the **My saved rules** list.

## Edit applicability rule sets

To edit an applicability rule, in the **Rules Workspace** select any rule that is saved in the **My saved rules** list, and then choose **Edit** from the ribbon. This opens the **Edit Rule** wizard.

The **Edit Rule** wizard displays the current rules for the rule set. You edit rules in the same way as you use the **Create Rule** wizard to create new rules. You can use this wizard to rename the rule set, delete rules, re-order rules and relationships, or add new rules.

After you make changes, choose **OK** to save the changes and close the wizard.

For more details about using the rule wizard, see **Step 7**, the applicability page, of the [Create Update wizard](create-updates-with-updates-publisher#use-the-create-update-wizard).

## Delete applicability rules

To delete a saved applicability rule, in the **Rules Workspace** select the rule or rule set from the **My saved rules** list, and then choose **Delete** from the ribbon. This removes the saved rule or rule set from Updates Publisher.

To delete a rule from a specific update, you must [edit the update](manage-updates-with-updates-publisher#edit-updates-and-bundles).