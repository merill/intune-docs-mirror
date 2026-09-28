---
layout: Conceptual
title: Migrate your imported group policy to a policy in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/migrate-group-policy
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
description: After you import your Windows group policy objects in Microsoft Intune, use the migrate feature to transfer your GPOs to a Settings Catalog policy. This policy uses your imported GPOs, and can be assigned to users and devices managed by your organizations.
ms.date: 2025-02-20T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: aanavath
locale: en-us
document_id: 6bb78152-ef35-dd05-a41a-02d1115ae1d8
document_version_independent_id: 6bb78152-ef35-dd05-a41a-02d1115ae1d8
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/migrate-group-policy.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/migrate-group-policy
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/migrate-group-policy.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 5331dda8-e86f-70ac-4341-d59df2228f7f
---

# Migrate your imported group policy to a policy in Microsoft Intune - Microsoft Intune | Microsoft Learn

You can import your on-premises Group Policy Objects (GPOs), and create an Intune policy using these imported settings. This policy can be deployed to users and devices managed by your organization.

With Group Policy Analytics, you import your on-premises GPOs. It analyzes your imported GPOs, and shows the settings that are also available in Microsoft Intune. For the settings that are available, you can create a [Settings Catalog policy](settings-catalog/), and then deploy the policy to your managed devices.

This feature applies to:

- Windows

This article shows you how to create the policy from your imported GPOs. For more information and an overview on Group Policy Analytics, go to [Analyze your on-premises group policy objects (GPO) using Group Policy analytics in Microsoft Intune](import-group-policy-analytics).

## Before you begin

- In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), sign in as:

    - The **Intune administrator**

        **OR**
    - A role that has the **Security baselines** permission and the **Device configurations/Create** permission

    For more information about the permissions included with the built-in Intune roles, go to [built-in admin roles](../fundamentals/role-based-access-control/overview#built-in-roles). For information on custom roles, go to [assign permissions to custom roles](../fundamentals/role-based-access-control/create-custom-role#custom-role-permissions).
- Import your on-premises GPOs, and review the results.

    For the specific steps, go to [Import and analyze your on-premises GPOs using Group Policy analytics in Intune](import-group-policy-analytics#import-gpos-and-run-analytics).
- Only admins scoped to the GPO can create a settings catalog policy from that imported GPO. Scope tags are first applied during import of the GPO and can be edited. If a scope tag isn't or wasn't selected during the GPO import, then the **Default** scope tag is automatically used.

## Review and migrate your GPOs to a Settings Catalog policy

After you [import your GPOs](import-group-policy-analytics#import-gpos-and-run-analytics), review the settings that can be migrated. Remember, some settings don't make sense on cloud native endpoints, like Windows devices. After you review them, you can migrate the settings to a Settings Catalog policy.

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Devices** &gt; **Manage devices** &gt; **Group Policy analytics**.
2. In the list, your imported GPOs are shown. Next to the GPO you want in your Settings Catalog profile, select the **Migrate** checkbox. You can select one GPO or many GPOs:

    [![Screenshot that shows how to select the Migrate checkbox next to your imported GPO in Microsoft Intune.](media/migrate-group-policy/select-migrate-checkbox-imported-gpo.png)](media/migrate-group-policy/select-migrate-checkbox-imported-gpo.png#lightbox)
3. To see all the settings in your imported GPO, select **Migrate**:

    [![Screenshot that shows how to select the Migrate button to see all the settings in your imported GPO in Microsoft Intune.](media/migrate-group-policy/select-migrate-see-all-settings.png)](media/migrate-group-policy/select-migrate-see-all-settings.png#lightbox)
4. In the **Settings to migrate** tab, select the **Migrate** column for the settings you want to include in your Settings Catalog profile:

    ![Screenshot that shows the settings to migrate, and how to select the Migrate checkbox in Microsoft Intune.](media/migrate-group-policy/settings-to-migrate-tab.png)

    To help you pick the settings, you can use the built-in features:

    - **Select all on this page**: Select this option if you want all settings on the existing page to be included in your Settings Catalog profile.

        [![Screenshot that shows how to use the select all on this page button to include all page settings in the Group Policy Analytics migrate feature in Microsoft Intune.](media/migrate-group-policy/select-all-on-this-page.png)](media/migrate-group-policy/select-all-on-this-page.png#lightbox)
    - **Search by setting name**: Enter the setting name to find the settings you want:

        [![Screenshot that shows how to search for the setting name in the Group Policy Analytics migrate feature in Microsoft Intune.](media/migrate-group-policy/search-by-setting-name.png)](media/migrate-group-policy/search-by-setting-name.png#lightbox)
    - **Sort**: Sort your settings using the column names:

        [![Screenshot that shows how to sort the settings using the Migrate, Setting name, Group policy setting category, MDM support, value, scope, min OS version, and CSP name Group Policy Analytics migrate features in Microsoft Intune.](media/migrate-group-policy/sort-using-column-names.png)](media/migrate-group-policy/sort-using-column-names.png#lightbox)

    Tip

    If you haven't already, review your Group Policy settings. It's possible some settings don't apply to cloud-based policy management or don't apply to cloud native endpoints, like Windows devices. It's not recommended to include all your Group Policy settings without reviewing them.

    Select **Next**.
5. In **Configuration**, your settings and their values are shown. The values are the same values in the on-premises Group Policy. Review these settings and their values.

    After you create the Settings Catalog policy, you can change any values.

    Select **Next**.
6. In **Profile info**, enter the following settings:

    - **Name**: Enter a descriptive name for the Setting Catalog profile. Name your profiles so you can easily identify them later. For example, a good profile name is **Windows: Imported Microsoft Edge GPOs**.
    - **Description**: Enter a description for the profile. This setting is optional, but recommended.

    Select **Next**.
7. In **Scope tags**, optionally assign a tag to filter the profile to specific IT groups, such as US-NC IT Team or JohnGlenn\_ITDepartment. For more information about scope tags, go to [Use role-based access control (RBAC) roles and scope tags for distributed IT](../fundamentals/role-based-access-control/scope-tags).
8. In **Assignments**, select the user or groups that will receive your profile. For more information on assigning profiles, including advice and guidance, go to [Assign user and device profiles in Intune](assign-device-profile).

    Select **Next**.
9. In **Review + deploy**, review your settings.

    When you select **Create**, your changes are saved, and the profile is assigned. The policy is shown in the **Devices** &gt; **Manage devices** &gt; **Configuration** list.

The next time any device within your assigned groups checks for configuration updates, the settings you configured are applied.

## Conflicting settings are detected early

It's possible you have multiple GPOs that include the same setting, and that the setting is set to different values. When you're creating a policy, and selecting your settings in the **Settings to migrate** tab, any conflicting settings show the following error:

`Conflicts are detected for the following settings: <setting name>. Select only one version with the value you prefer in order to continue.`

[![Screenshot that shows conflicts are detected error message with the Group Policy Analytics migrate feature in Microsoft Intune.](media/migrate-group-policy/conflicting-settings.png)](media/migrate-group-policy/conflicting-settings.png#lightbox)

To resolve the conflict, uncheck a conflicting setting, and continue the migration.

## What you need to know

The **Migrate** feature takes the parsed data from the imported Group Policy object (GPO) and translates it to a relevant setting in the Settings Catalog, if the setting exists.

**Migrate** is best effort.

When you create the Settings Catalog profile, any settings that can be included in the profile are included. There can be some differences with the imported settings and the settings in Settings Catalog.

- **Some settings have a better configuration experience in Endpoint Security**

    If you import AppLocker settings or Firewall rule settings, then the **Migrate** option is disabled and grayed out. Instead, configure these settings using the Endpoint Security workload in the Intune admin center.

    For more information, go to:

    - [Firewall policy in Endpoint Security](endpoint-security/firewall)
    - [Application control policy in Endpoint Security](endpoint-security/attack-surface-reduction).

    If you have GPOs that focus on endpoint security, then you should look at the features available in [Endpoint Security](../device-security/endpoint-security-policies), including security baselines and mobile threat defense.
- **Some settings don't migrate exactly, and may use a different setting**

    In some scenarios, some GPO settings don't migrate to the exact same setting in the Settings Catalog. Intune shows an alternate setting that has a similar effect.

    You can see this behavior if you import GPOs that include older Office Administrative Template settings or older Google Chrome settings. In the following image, an older Office setting isn't supported. So, Intune suggests migrating to a supported version:

    ![Screenshot that shows older Office setting that isn't supported and suggests migrating to a supported version in Microsoft Intune.](media/migrate-group-policy/setting-not-supported-migrate.png)
- **Some settings fail to migrate**

    It's possible some errors can happen when the settings are migrating. When the profile is being created, settings that return an error are shown in **Notifications**:

    ![Screenshot that shows notifications with additional information when the policy is being created in Microsoft Intune.](media/migrate-group-policy/notifications.png)

    Some common reasons a setting might show an error include:

    - The setting value is in an unexpected format.
    - A child setting is missing from the imported GPO and is required to configure the parent setting.