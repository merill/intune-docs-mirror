---
layout: Conceptual
title: What is the administration service - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/adminservice/overview
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
description: Use the Configuration Manager administration service REST API to interact with the site over an HTTPS OData connection.
ms.date: 2021-12-21T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: overview
ms.collection: tier3
locale: en-us
document_id: 188a4f14-6272-ebf3-894d-a3481522588e
document_version_independent_id: f3c01e35-8451-f0e6-f20c-ab75ed5b235f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/adminservice/overview.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/adminservice/overview
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/adminservice/overview.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
platformId: e41dfa20-67d8-5194-d165-02a245ab2bf4
---

# What is the administration service - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

The [SMS Provider](../../core/plan-design/hierarchy/plan-for-the-sms-provider) provides API interoperability access over HTTPS, called the **administration service**. The administration service is a representational state transfer (REST) API based on the Open Data (OData) v4 protocol.

The administration service currently has two layers or routes:

- Administration service &gt; WMI &gt; SQL: `https://<SMSProviderFQDN>/AdminService/wmi/<ClassName>`

    The **WMI** route supports both GET and POST commands to over 700 classes.
- Administration service &gt; OData/SQL: `https://<SMSProviderFQDN>/AdminService/v1.0/<ClassName>`

    This versioned route (**v1.0**) supports new Configuration Manager functionality.

The `<ClassName>` value is a valid Configuration Manager class name. The administration service class names are case-sensitive. Make sure to use the proper capitalization. For example, `SMS_Site`.

## Scenarios

Configuration Manager natively uses the administration service for the following features:

- [Email approval of apps](../../apps/deploy-use/app-approval#bkmk_email-approve)
- [View recently connected consoles](../../core/servers/manage/admin-console#bkmk_viewconnected)
- The **Security**[node of the console](set-up#enable-console-usage)
- Microsoft Intune [tenant attach](../../tenant-attach/device-sync-actions)
- [Community hub](../../core/servers/manage/community-hub)
- [Managing console extensions](../../core/servers/manage/admin-console-extensions)

In addition, you can develop custom solutions with the administration service, for example:

- Replace a custom web service to access information from the site.
- In PowerShell scripts that you run directly from the Configuration Manager console. For more information, see [Create and run PowerShell scripts from the Configuration Manager console](../../apps/deploy-use/create-deploy-scripts).
- A PowerShell script in a task sequence. This action lets you access information from the site without requiring a custom web service to interface with the WMI provider. For more information, see [Task sequence steps - Run PowerShell Script](../../osd/understand/task-sequence-steps#BKMK_RunPowerShellScript).
- Access site data from Power BI using the OData connector option.

## Prerequisites

Configure the following prerequisites on the server that hosts the SMS Provider role:

- In version 2006 and earlier, enable the Windows server role **Web Server (IIS)**. Starting in version 2010, this role is no longer required.
- Starting in version 2107, the SMS Provider requires .NET version 4.6.2, and version 4.8 is recommended. In version 2103 and earlier, this role requires .NET 4.5 or later. For more information, [Site and site system prerequisites](../../core/plan-design/configs/site-and-site-system-prerequisites#net-version-requirements).
- You may need to enable secure HTTPS communication with a trusted certificate. For more information, see [Enable secure HTTPS communication](set-up#enable-secure-https-communication).

To access the administration service, your user account needs to be an administrative user in Configuration Manager. If you access the administration service via a cloud management gateway, you need to have an account in Microsoft Entra ID.

For more information on scalability of the SMS Provider and administration service, see [Size and scale numbers](../../core/plan-design/configs/size-and-scale-numbers#sms-provider).

Note

For any machine with the Configuration Manager console, if it's using a proxy server, the console fails to connect to the administration service. For example, when trying to access the **Security** nodes, you may see errors that the administration service isn't enabled or available. The **SmsAdminUI.log** file shows errors such as, `Failed to get a response for OData query.`

To work around this issue, either remove the proxy configuration from the machine, or make the following configuration change:

1. Manually edit the following XML file: `C:\Program Files (x86)\Microsoft Endpoint Manager\AdminConsole\bin\Microsoft.ConfigurationManagement.exe.config`
2. Configure the `<defaultproxy>` behavior with one of the following options:

    1. Set `enabled="false"`
    2. Add the FQDN of the SMS Provider to the `<bypasslist>`.

    For more information, see [`<defaultProxy>` Element (Network Settings)](/en-us/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings).