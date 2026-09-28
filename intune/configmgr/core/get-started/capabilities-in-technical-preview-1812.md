---
layout: Conceptual
title: Technical preview 1812 - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/capabilities-in-technical-preview-1812
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
description: Learn about new features available in the Configuration Manager technical preview branch version 1812.
ms.date: 2018-12-14T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: whats-new
ROBOTS: NOINDEX
ms.collection: tier3
locale: en-us
document_id: d6c7cb20-cacd-40d3-3fbe-ca7af6d1e74a
document_version_independent_id: 216f22f2-4503-b70a-b917-53fae6f34ad4
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/get-started/capabilities-in-technical-preview-1812.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/get-started/capabilities-in-technical-preview-1812
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/get-started/capabilities-in-technical-preview-1812.md
platformId: 249559c6-bfc0-a3cd-f3c1-2dc950590d4e
---

# Technical preview 1812 - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (technical preview branch)*

This article introduces the features that are available in the technical preview for Configuration Manager, version 1812. Install this version to update and add new features to your technical preview site.

Review the [technical preview](technical-preview) article before installing this update. That article familiarizes you with the general requirements and limitations for using a technical preview, how to update between versions, and how to provide feedback.

**The following sections describe the new features to try out in this version:**

## Improvements to Run PowerShell Script task sequence step

Based on customer feedback, the **Run PowerShell Script** task sequence step now includes the following improvements:

- When you choose the **Enter a PowerShell script** option, select **Edit Script**. The new PowerShell script window provides the following actions:

    - Edit the script directly
    - Open an existing script from file
    - Browse to an existing approved script in Configuration Manager
- Save the script output to a custom task sequence variable
- To include the script parameters in the task sequence log, set the task sequence variable **OSDLogPowerShellParameters** to **TRUE**. By default, the parameters aren't in the log.

## Improvements to application approvals via email

This release has improvements to the feature to receive [email notifications](../../apps/deploy-use/app-approval#bkmk_email-approve) for application requests. Users have always had the ability to add a comment to the request from Software Center. This comment shows on the application request in the Configuration Manager console. Now that comment also shows in the email. Including this comment in the email helps the approvers make a better decision to approve or deny the request.

## Configure user device affinity in Software Center

With [Software Center infrastructure improvements](../plan-design/changes/whats-new-in-version-1806#software-center-infrastructure-improvements) starting in version 1806, the application catalog site server roles are no longer required for most scenarios. Some customers still relied upon the application catalog to allow users to set their primary device for user device affinity. For more information, see [Link users and devices with user device affinity](../../apps/deploy-use/link-users-and-devices-with-user-device-affinity).

Now users can set their primary device in Software Center. This action makes them a primary user of the device in Configuration Manager.

### Prerequisite

Enable the following client setting in the **User and device affinity** group: **Allow user to define their primary devices**. For more information, see [About client settings](../clients/deploy/about-client-settings#user-and-device-affinity).

### Try it out!

Try to complete the tasks. Then send [Feedback](../understand/product-feedback) with your thoughts on the feature.

1. On a Configuration Manager client, open **Software Center**.
2. Select the **Options** tab.
3. In the **Work information** section, select the following option: **I regularly use this computer to do my work**.

## Improvements to Configuration Manager console

Based on customer feedback at the Midwest Management Summit (MMS) Desert Edition 2018, this release includes the following improvements to the Configuration Manager console:

#### Maximize the browse registry window

In the **Software Library** workspace, expand **Application Management**, and select the **Applications** node. Select an application that has a deployment type with a detection method. For example, a Windows Installer detection method. In the details pane, switch to the **Deployment Types** tab. Open the properties of a deployment type, and switch to the **Detection Method** tab. Select **Add Clause**. Change the **Setting Type** to **Registry** and select **Browse** to open the **Browse Registry** window. Now you can now maximize this window.

#### Go to the collection from an application deployment

In the **Software Library** workspace, expand **Application Management**, and select the **Applications** node. Select an application. In the details pane, switch to the **Deployments** tab. Select a deployment, and then choose the new **Collection** option in the ribbon on the Deployment tab. (This action is also available from the right-click context menu on the deployment in this view.) This action switches the view to the collection that's the target of the deployment.

#### Edit a task sequence by default

In the **Software Library** workspace, expand **Operating Systems**, and select the **Task Sequences** node. **Edit** is now the default action when opening a task sequence. Previously the default action was **Properties**.

#### Remove content from monitoring status

In the **Monitoring** workspace, expand **Distribution Status**, and select **Content Status**. Select an item in the list, and choose the **View Status** option in the ribbon. In the Asset Details pane, right-click a distribution point, and select the new option **Remove**. This action removes this content from the selected distribution point.

#### Views sort by integer values

Based on your feedback, we made improvements to how various views sort data. If there are any others you find, send [Feedback](../understand/product-feedback).

For example, in the **Deployments** node of the **Monitoring** workspace, the following columns now sort as numbers instead of string values:

- Number Errors
- Number In Progress
- Number Other
- Number Success
- Number Unknown

#### Move the warning for a large number of results

When you select a node in the console that returns more than 1,000 results, Configuration Manager displays the following warning:

> 
> Configuration Manager returned a large number of results. You can narrow your results by using search. Or, click here to view a maximum of 100000 results.

There's now additional blank space in between this warning and the search field. This move helps to prevent inadvertently selecting the warning to display more results.

## Download reports from the Community Hub

This release iterates on the [Community Hub](capabilities-in-technical-preview-1807#bkmk_hub) by adding support for reports. When you download a report from the hub, Configuration Manager installs it to the reporting point. You'll see downloaded reports from the community in a new **Hub** folder under reports.

Note

It can take up to 10 minutes before a downloaded report is available on the reporting point.

### Prerequisite

Enable the SMS Provider to use a certificate. Manually bind a PKI-based certificate to port 443 on the server that hosts the SMS Provider role. Add the certificate to the server, and then use one of the following options:

#### Bind the certificate with IIS

If the server with the SMS Provider role has the IIS Management Console, use the **Edit Bindings** action on the default web site. Add port 443, and specify your certificate from the machine's certificate store.

Note

The SMS Provider role doesn't require IIS. This procedure is using the IIS console to bind the certificate. These certificate bindings are for the machine, not any specific service.

#### Bind the certificate with netsh

Use the netsh command line to bind the certificate: `netsh http add sslcert ipport=0.0.0.0:443 certhash=<thumbprint> appid=<GUID>` Where **thumbprint** is the thumbprint of the installed certificate, and **GUID** is a random GUID.

Tip

Use the Windows PowerShell cmdlet `New-Guid` to generate a random GUID.

For example, `netsh http add sslcert ipport=0.0.0.0:443 certhash=5aef9c1f348d4d1c8675309ca3363c2a5d3b617d appid={00001111-aaaa-2222-bbbb-3333cccc4444}`

### Known issue

If the hub fails to download a report, the console doesn't display an error message. It displays a success message when the site successfully downloads and installs the report.