---
layout: Conceptual
title: Customize the self-service portal - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/protect/deploy-use/bitlocker/customize-self-service-portal
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
description: Add custom organization-specific information to the BitLocker management self-service portal
ms.date: 2019-11-29T00:00:00.0000000Z
ms.subservice: protect
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: d550baa2-b078-a632-1765-852aeaab3a1e
document_version_independent_id: e4f78533-cc66-34fb-5267-dff4d3887f45
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/protect/deploy-use/bitlocker/customize-self-service-portal.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/protect/deploy-use/bitlocker/customize-self-service-portal
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/protect/deploy-use/bitlocker/customize-self-service-portal.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/43ab1a66-ffe1-45dd-a4cb-6580218ef802
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
- https://authoring-docs-microsoft.poolparty.biz/devrel/bbc4fbf6-70c4-4d12-b47f-9360080c4977
platformId: 75f43f42-0c08-d52b-41a8-54e69e2a2ce9
---

# Customize the self-service portal - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

After you [install the BitLocker self-service portal](setup-websites), you can customize it for your organization. Add a custom notice, your organization name, and other organization-specific information.

## Branding

Brand the self-service portal with your organization's name, help desk URL, and notice text.

1. On the web server that hosts the self-service portal, sign in as an administrator.
2. Start the **Internet Information Services (IIS) Manager** (run **inetmgr.exe**).
3. Expand **Sites**, expand **Default Web Site**, and select the **SelfService** node. In the details pane, **ASP.NET** group, open **Application Settings**.

    [![Example screenshot of SelfService application settings in IIS Manager](media/bitlocker-self-service-iis-app-settings.png)](media/bitlocker-self-service-iis-app-settings.png#lightbox)
4. Select the item that you want to change, and in the **Actions** pane, select **Edit**. Change the **Value** to the new name that you want to use.

Caution

Don't change the **Name** values. For example, don't change `CompanyName`, change `Contoso IT`. If you change the **Name** values, the self-service portal will stop working.

The changes take effect immediately.

### Supported branding values

For the values that you can set, see the following table:

| Name | Description | Default value |
| --- | --- | --- |
| CompanyName | The organization name that the self-service portal displays as a header at the top of every page. | `Contoso IT` |
| DisplayNotice | Display an initial notice that the user has to acknowledge. | `true` |
| HelpdeskText | The string in the right pane below "For all other related issues" | `Contact Helpdesk or IT Department` |
| HelpdeskUrl | The link for the HelpdeskText string. | (empty) |
| NoticeTextPath | The text of the initial notice that the user has to acknowledge. By default, the full file path on the web server is `C:\inetpub\Microsoft BitLocker Management Solution\Self Service Website\Notice.txt`. Edit and save the file in a plain text editor. This path value is relative to the SelfService application. | `Notice.txt` |

For a screenshot of the default self-service portal, see [BitLocker self-service portal](self-service-portal).

Tip

If necessary, you can localize some of these strings to display in different languages. For more information, see Localization.

## Session time-out

To make the user's session expire after a specified period of inactivity, you can change the session time-out setting for the self-service portal.

1. On the web server that hosts the self-service portal, sign in as an administrator.
2. Start the **Internet Information Services (IIS) Manager** (run **inetmgr.exe**).
3. Expand **Sites**, expand **Default Web Site**, and select the **SelfService** node. In the details pane, **ASP.NET** group, open **Session State**.
4. In the **Cookie Settings** group, change the **Time-out (in minutes)** value. It's the number of minutes after which the user's session expires. The default value is `5`. To disable the setting, so that there's no time-out, set the value to `0`.
5. In the **Actions** pane, select **Apply**.

## Localize helpdesk text and URL

You can configure localized versions of the self-service portal `HelpdeskText` statement and `HelpdeskUrl` link. This string informs users how to get additional help when they use the portal. If you configure localized text, the portal displays the localized version for web browsers in that language. If it doesn't find a localized version, it displays the default value in the `HelpdeskText` and `HelpdeskUrl` settings.

1. On the web server that hosts the self-service portal, sign in as an administrator.
2. Start the **Internet Information Services (IIS) Manager** (run **inetmgr.exe**).
3. Expand **Sites**, expand **Default Web Site**, and select the **SelfService** node. In the details pane, **ASP.NET** group, open **Application Settings**.
4. In the **Actions** pane, select **Add**.
5. In the **Add Application Setting** window, configure the following values:

    - **Name**: enter `HelpdeskText_<language>`, where `<language>` is the language code for the text.

        For example, to create a localized `HelpdeskText` statement in Spanish (Spain), the name is `HelpdeskText_es-es`.
    - **Value**: the localized string to display in the right pane of the self-service portal below "For all other related issues"
6. Select **OK** to save the new setting.
7. Repeat this process to add a new application setting for `HelpdeskUrl_<language>` that matches the associated `HelpdeskText_<language>` setting.

Repeat this process to add a pair of settings for all languages that you support in your organization.

## Localize the notice file

You can configure localized versions of the initial notice that the user has to acknowledge in the self-service portal. By default, the full file path on the web server is `C:\inetpub\Microsoft BitLocker Management Solution\Self Service Website\Notice.txt`.

To display localized notice text, create a localized notice.txt file. Then save it under a specific language folder. For example: `Self Service Website\es-es\Notice.txt` for Spanish (Spain).

The self-service portal displays the notice text based on the following rules:

- If the default notice file is missing, the portal displays a message that the default file is missing.
- If you create a localized notice file in the appropriate language folder, it displays the localized notice text.
- If the web server doesn't find a localized version of the notice file, it displays the default notice.
- If the user sets their browser to a language that doesn't have a localized notice, the portal displays the default notice.

### Create a localized notice file

1. On the web server that hosts the self-service portal, sign in as an administrator.
2. Create a `<language>` folder for each supported language in the `Self Service Website` application path. For example, `es-es` for Spanish (Spain). By default, the full path is `C:\inetpub\Microsoft BitLocker Management Solution\Self Service Website\es-es`.

    For a list of the valid language codes you can use, see [National Language Support (NLS) API Reference](/en-us/windows/win32/intl/locale-identifiers#predefined-locale-identifiers).

    Tip

    The name of the language folder can also be the language neutral name. For example, **es** for Spanish, instead of **es-es** for Spanish (Spain) and **es-ar** for Spanish (Argentina). If the user sets their browser to **es-es**, and that language folder doesn't exist, the web server recursively checks the parent locale folder (**es**). (The parent locales are defined in .NET.) For example,`Self Service Website\es\Notice.txt`. This recursive fallback mimics the .NET resource loading rules.
3. Create a copy of your default notice file with the localized text. Save it in the folder for the language code. For example, for Spanish (Spain), by default the full path is `C:\inetpub\Microsoft BitLocker Management Solution\Self Service Website\es-es\Notice.txt`.

    Repeat this process to a localized notice file for all languages that you support in your organization.