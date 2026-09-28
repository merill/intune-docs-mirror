---
layout: Conceptual
title: App Protection Policies for Extensions - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/app-management/protection/policy-extensions
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: nicholasswhite
ms.author: nwhite
ms.collection:
- M365-identity-device-management
ms.subservice: apps
description: This topic describes the app protection policy (APP) for extensions.
ms.date: 2025-01-06T00:00:00.0000000Z
ms.topic: article
ms.reviewer: demerson
locale: en-us
document_id: db194e9e-9ba8-ac76-ac34-0db6456b206e
document_version_independent_id: db194e9e-9ba8-ac76-ac34-0db6456b206e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/app-management/protection/policy-extensions.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: app-management/protection/policy-extensions
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/app-management/protection/policy-extensions.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/3e34b70d-bca0-4369-a01b-71d1edfd427b
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/aec7dc3e-0dad-4b82-accf-63218d8767d5
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/8ca32b3f-fa14-46df-b09a-9c4a591d6396
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f260444a-7ec6-4768-8e41-ad2438092724
platformId: 8c495372-2635-b583-5b0f-810bc80e5413
---

# App Protection Policies for Extensions - Microsoft Intune | Microsoft Learn

This article describes app protection policies for extensions in Microsoft Intune.

## Add-ins for Outlook app

Outlook add-ins let you integrate popular apps with the email client. Add-ins for Outlook are available on the web, Windows, Mac, and Outlook for Android and iOS/iPadOS. The Intune APP SDK and Intune app protection policies do not include support for managing add-ins for Outlook, but there are other ways to limit their use. Since add-ins are managed via Microsoft Exchange, users will be able to share data and messages across Outlook and unmanaged add-in applications unless add-ins are turned off for the user by their Exchange.

If you want to stop your end users from accessing and installing Outlook add-ins (this affects all Outlook clients), make sure you have the following changes to roles in the Exchange admin center:

- To prevent users from installing Office Store add-ins, remove the My Marketplace role from them.
- To prevent users from side loading add-ins, remove the My Custom Apps role from them.
- To prevent users from installing all add-ins, remove both, My Custom Apps and My Marketplace roles from them.

These instructions apply to Microsoft 365, Exchange 2016, Exchange 2013 across Outlook on the web, Windows, Mac, and mobile.

- Learn more about [add-ins for Outlook](/en-us/exchange/clients-and-mobile-in-exchange-online/add-ins-for-outlook/add-ins-for-outlook).
- Learn more about [how to specify the administrators and users who can install and manage add-ins for Outlook app](/en-us/exchange/clients-and-mobile-in-exchange-online/add-ins-for-outlook/specify-who-can-install-and-manage-add-ins).

## LinkedIn account connections for Microsoft apps

LinkedIn account connections allow users to see public LinkedIn profile information within certain Microsoft apps. By default, your users can choose to connect their LinkedIn and Microsoft work or school accounts to see additional LinkedIn profile information.

Note

LinkedIn integration is currently unavailable for United States Government customers and for organizations with Exchange Online mailboxes hosted in Australia, Canada, China, France, Germany, India, South Korea, United Kingdom, Japan, and South Africa.

The Intune SDK and Intune app protection policies don't include support for managing LinkedIn account connections, but there are other ways to manage them. You can disable LinkedIn account connections for your entire organization, or you can enable LinkedIn account connections for selected user groups in your organization. These settings affect LinkedIn connections across Microsoft 365 apps on all platforms (web, mobile, and desktop). You can:

- Enable or disable LinkedIn account connections for your tenant in the portal.
- Enable or disable LinkedIn account connections for your organization's Office 2016 apps using Group Policy.

If LinkedIn integration is enabled for your tenant, when users in your organization connect their LinkedIn and Microsoft work or school accounts, they have two options:

- They can give permission to share data between both accounts. This means that they give permission for their LinkedIn account to share data with their Microsoft work or school account, as well as their Microsoft work or school account to share data with their LinkedIn account. Data that is shared with LinkedIn leaves the online services.
- They can give permission to share data only from their LinkedIn account to their Microsoft work and school account

If a user consents to sharing data between accounts, as with Office add-ins, LinkedIn integration uses existing Microsoft Graph APIs. LinkedIn integration uses only a subset of the APIs available to Office add-ins and supports various exclusions.

| Microsoft Graph permissions | Description |
| --- | --- |
| Read permissions for [People](/en-us/graph/permissions-reference#people-permissions) | Allows the app to read a scored list of people relevant to the signed-in user. The list can include local contacts, contacts from social networking or your organization's directory, and people from recent communications (such as email and Skype). |
| Read permissions for [Calendars](/en-us/graph/permissions-reference#calendars-permissions) | Allows the app to read events in user calendars. Includes the meetings in signed-in user calendars, their times, locations, and attendees. |
| Read permissions for [User Profile](/en-us/graph/permissions-reference#user-permissions) | Allows users to sign in to the app, and allows the app to read the profile of signed-in users. It also allows the app to read basic company information for signed-in users. |
| Subscriptions | This scope isn't available and not yet in use. It includes subscriptions provided by the user's organization to Microsoft apps and services, such as Microsoft 365. |
| Insights | This scope isn't available and not yet in use. It includes the interests associated with the signed-in user's account based on their use of Microsoft services. |

### Learn more

- Learn about [LinkedIn information and features in your Microsoft apps](https://go.microsoft.com/fwlink/?linkid=850740).
- Learn about LinkedIn account connections release on the [Microsoft 365 Roadmap page](https://products.office.com/en-US/business/office-365-roadmap?filters=%26freeformsearch=linkedin#abc).
- Learn about [Configuring LinkedIn account connections](/en-us/azure/active-directory/linkedin-integration).
- For more information about data that is shared between users' LinkedIn and Microsoft work or school accounts, see [LinkedIn in Microsoft applications at your work or school](https://www.linkedin.com/help/linkedin/answer/84077).