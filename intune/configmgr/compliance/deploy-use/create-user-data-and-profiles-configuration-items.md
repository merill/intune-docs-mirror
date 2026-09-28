---
layout: Conceptual
title: Create user data and profiles configuration items - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/compliance/deploy-use/create-user-data-and-profiles-configuration-items
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
description: Use data and profiles configuration items in Configuration Manager to manage folder redirection, offline files, and roaming profiles.
ms.date: 2021-10-05T00:00:00.0000000Z
ms.subservice: compliance
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 52722235-3d25-8284-9812-bbe3072d8bf5
document_version_independent_id: e3bd7feb-9614-6b86-e847-33711e2fa854
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/compliance/deploy-use/create-user-data-and-profiles-configuration-items.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/compliance/deploy-use/create-user-data-and-profiles-configuration-items
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/compliance/deploy-use/create-user-data-and-profiles-configuration-items.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: e86b74aa-5d17-6404-c294-7a2c45a4f97e
---

# Create user data and profiles configuration items - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

User data and profiles configuration items in Configuration Manager contain settings that can manage folder redirection, offline files, and roaming profiles on computers that run Windows 8 and later for users in your hierarchy. For example, you can:

- Redirect a user's Documents folder to a network share.
- Ensure that specified files stored on the network are available on a user's computer when the network connection is unavailable.
- Configure which files in a user's roaming profile are synchronized with a network share when the user logs on and off.

Unlike other configuration items in Configuration Manager, you don't add user data and profile configuration items to a configuration baseline, which you then deploy. Instead, you deploy the configuration item directly by using the **Deploy User Data and Profiles Configuration Item** dialog box.

You can only deploy user data and profiles configuration items to user collections.

Important

If you deploy this policy, it restricts folder redirection group policy on the same devices. For more information, see [Folder Redirection group policy is not applied in Windows 8, Windows 8.1, or Windows 10 and later](/en-us/troubleshoot/windows-server/group-policy/folder-redirection-group-policy-not-applied).

## Enable user data and profiles for compliance settings

Use the following procedure to configure the default client setting for user data and profiles compliance settings, which will apply to all computers in your hierarchy. If you want this setting to apply to only some computers, create a custom device client setting and assign it to a collection that contains the computers for which you want to use user data and profiles compliance settings. For more information about how to create custom device settings, see [How to configure client settings](../../core/clients/deploy/configure-client-settings).

1. In the Configuration Manager console, go to **Administration** &gt; **Client Settings** &gt; **Default Settings**.
2. On the **Home** tab of the ribbon, in the **Properties** group, select **Properties**.
3. In the **Default Settings** dialog box, select **Compliance Settings**.
4. From the **Enable User Data and Profiles** drop-down list, select **Yes**.
5. Select **OK** to close the **Default Settings** dialog box.

## Create a user data and profiles configuration item

1. In the Configuration Manager console, go to **Assets and Compliance** &gt; **Compliance Settings** &gt; **User Data and Profiles**.
2. On the **Home** tab, in the **Create** group, select **Create User Data and Profiles Configuration Item**.
3. On the **General** page of the **Create User Data and Profiles Configuration Item Wizard**, specify the following information:

    - **Name:** Enter a unique name for the configuration item. You can use a maximum of 256 characters.
    - **Description:** Provide a description that gives an overview of the configuration item and other relevant information that helps to identify it in the Configuration Manager console. You can use a maximum of 256 characters.
    - **Folder redirection:** Configure settings for folder redirection for this configuration item.
    - **Offline files:** Configure settings for offline files for this configuration item.
    - **Roaming user profiles:** Configure settings for roaming user profiles for this configuration item.
4. On the **Folder Redirection** page of the **Create User Data and Profiles Configuration Item Wizard**, specify how you want the client computers of users that receive this configuration item to manage folder redirection. You can configure settings for any device the user signs into or for only the user's primary devices.

    Note

    This page only appears if you checked **Folder redirection** on the **General** page of the wizard.
5. On the **Offline Files** page of the **Create User Data and Profiles Configuration Item Wizard**, you can enable or disable the use of offline files for users that receive this configuration item and configure settings for the behavior of the offline files. You can also specify offline files that will always be available on any computer that the user signs into.

    Note

    This page only appears if you checked the box **Offline files** on the **General** page of the wizard.
6. On the **Roaming Profiles** page of the **Create User Data and Profiles Configuration Item Wizard**, you can configure whether roaming profiles are available on computers that the user signs into and also configure further information about how these profiles behave.

    Note

    This page only appears if you checked the box **Roaming user profiles** on the **General** page of the wizard.
7. Complete the wizard.

The new configuration item is shown in the **User Data and Profiles** node of the **Assets and Compliance** workspace.

## Deploy a user data and profiles configuration item

1. In the Configuration Manager console, go to **Assets and Compliance** &gt; **Compliance Settings** &gt; **User Data and Profiles**.
2. Select the user data and profiles configuration item you want to deploy and then, in the **Home** tab, in the **Deployment** group, select **Deploy**.
3. In the **Deploy User Data and Profiles Configuration Item** dialog box, specify the following information:

    - **Collection**: Select **Browse** to select the user collection where you want to deploy the configuration item.

        Important

        You can only deploy user data and profiles configuration items to user collections.
    - **Remediate noncompliant rules when supported**: Enable this option to automatically remediate any rules that are evaluated as noncompliant on client computers.
    - **Allow remediation outside the maintenance window**: If you configured a maintenance window for the collection to which you're deploying the configuration item, enable this option. It lets compliance settings remediate the value outside of the maintenance window. For more information about maintenance windows, see [How to use maintenance windows](../../core/clients/manage/collections/use-maintenance-windows).
    - **Generate an alert**: Enable this option to configure an alert that the site generates if the configuration item compliance is less than a specified percentage by a specified date and time. You can also specify whether you want an alert to be sent to System Center Operations Manager.
    - **Specify the compliance evaluation schedule for this configuration item**: Specify the schedule by which clients evaluate the deployed configuration item. This schedule can be either a simple or a custom schedule.
4. Select **OK** to close the **Deploy User Data and Profiles Configuration Item** dialog box and to create the deployment.