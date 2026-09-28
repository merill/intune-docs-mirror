---
layout: Conceptual
title: Deployment Monitoring Tool - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/support/deployment-monitoring-tool
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
description: Use the Deployment Monitoring Tool to troubleshoot software deployments on a Configuration Manager client.
ms.date: 2019-09-24T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: install-set-up-deploy
ms.collection: tier3
locale: en-us
document_id: f36eefd5-d27d-c1c8-5fdb-f402ce14a6aa
document_version_independent_id: 047e9023-35df-c855-24cf-bb5c42bc5635
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/support/deployment-monitoring-tool.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/support/deployment-monitoring-tool
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/support/deployment-monitoring-tool.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: c103a1ab-5ebf-00bd-60c1-5d7d14100b68
---

# Deployment Monitoring Tool - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

The Deployment Monitoring Tool is one of the [Configuration Manager tools](tools). It's a graphical user interface designed to assist in troubleshooting application, software update, and configuration baseline deployments on a Configuration Manager client. The tool is read-only as it doesn't change any state on the client. You can safely use it to diagnose common deployment scenarios.

## Features

- Run it as an administrator to troubleshoot deployments on a local client.
- Troubleshoot deployments on a remote client. Launch the tool and connect to a remote machine as an administrator.
- Export to XML all the data collected in the tool. Share the XML file with others, and use it as a common platform for talking about troubleshooting deployments.
- Import previously exported data to a different machine, and use it to run the tool in offline mode.

## Usage

The Deployment Monitoring Tool supports graphical user interface only. To launch the tool, run **DeploymentMonitoringTool.exe** as an administrator. There are three views:

- **Client Properties**: A list of useful attributes about the device and the Configuration Manager client. This view is the default.
- **Deployments**: View all of the currently targeted deployments. Select a deployment in the results pane to view more information in the details pane.
- **All Updates**: View all of the software updates and their status.

To copy data in any view, select a cell, and press **CTRL** + **C**.

### Actions menu

The following actions are available in the **Actions** menu:

- **Connect to remote machine**: Select a computer to connect to. When you don't specify a user name and password, it uses the current credentials. Click **Save** to connect to remote computer.
- **Export Data**: Select the file to write the data into, and click **Save**. Use the exported XML file for remote troubleshooting on a different computer.
- **Import Data**: Select a file to import into the tool.
- **View Log**: Opens an associated log file, depending upon the view:

    - Client Properties: `\\<hostname>\c$\Windows\CCM\Logs\PolicyAgent.log`
    - Deployments: `\\<hostname>\c$\Windows\CCM\Logs\PolicyAgent.log`
    - All Updates: `C:\Windows\WindowsUpdate.log`