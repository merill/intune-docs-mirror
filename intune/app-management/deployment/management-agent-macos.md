---
layout: Conceptual
title: Understanding Microsoft Intune Management Agent for macOS - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/app-management/deployment/management-agent-macos
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: nicholasswhite
ms.author: nwhite
ms.collection:
- M365-identity-device-management
- macOS
ms.reviewer: arnab
ms.subservice: apps
description: Learn about the Microsoft Intune management agent for macOS.
ms.date: 2024-07-12T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 45077568-779f-a677-700e-17541253e18e
document_version_independent_id: 45077568-779f-a677-700e-17541253e18e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/app-management/deployment/management-agent-macos.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: app-management/deployment/management-agent-macos
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/app-management/deployment/management-agent-macos.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: bb4a0449-c235-5330-22d5-65c92bdaa1b3
---

# Understanding Microsoft Intune Management Agent for macOS - Microsoft Intune | Microsoft Learn

## Why is the agent required?

The Microsoft Intune management agent is necessary to be installed on managed macOS devices in order to enable advanced device management capabilities that aren't supported by the native macOS operating system.

## How is the agent installed?

The agent is automatically and silently installed on Intune-managed macOS devices that you assign at least one shell script to in [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431). The agent is installed at `/Library/Intune/Microsoft Intune Agent.app` when applicable and doesn't appear in **Finder** &gt; **Applications** on macOS devices. The agent appears as `IntuneMdmAgent` in **Activity Monitor** when running on macOS devices.

## What does the agent do?

- The agent silently authenticates with Intune services before checking in to receive assigned shell scripts for the macOS device.
- The agent receives assigned shell scripts and runs the scripts based on the configured schedule, retry attempts, notification settings, and other settings set by the admin.
- The agent checks for new or updated scripts with Intune services usually every 8 hours. This check-in process is independent of the MDM check-in.

## How can I manually initiate an agent check-in from a Mac?

On a managed Mac that has the agent installed, open **Company Portal**, select the local device, select **Check status**. This initiates an MDM check-in as well as an agent check-in.

Alternatively, open **Terminal**, run the `sudo killall IntuneMdmAgent` command to terminate the `IntuneMdmAgent` process. The `IntuneMdmAgent` process restarts immediately, which will initiate a check-in with Intune.

Note

The **Sync** action for devices in Microsoft Intune admin center initiates an MDM check-in and does not force an agent check-in.

## When is the agent removed?

There are several conditions that can cause the agent to be removed from the device such as:

- Shell scripts are no longer assigned to the device.
- The macOS device is no longer managed.
- The agent is in an irrecoverable state for more than 24 hours (device-awake time).

## Why are scripts running even though the Mac is no longer managed?

When a Mac with assigned scripts is no longer managed, the agent isn't removed immediately. The agent detects that the Mac isn't managed at the next agent check-in (usually every 8 hours) and cancels scheduled script-runs. So, any locally stored scripts scheduled to run more frequently than the next scheduled agent check-in will run. When the agent is unable to check in, it retries checking in for up to 24 hours (device-awake time) and then removes itself from the Mac.

## How to turn off usage data sent to Microsoft for shell scripts?

To turn off usage data sent to Microsoft from the Intune management agent, open Company Portal, point to **Menu**, select **Preferences**, and then clear the **allow Microsoft to collect usage data** checkbox. This turns off usage data sent for both the agent and Company Portal.