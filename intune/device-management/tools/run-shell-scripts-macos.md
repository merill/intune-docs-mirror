---
layout: Conceptual
title: Use Shell Scripts on macOS Devices in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-management/tools/run-shell-scripts-macos
author: arnabbiswas
ms.author: arnab
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
ms.collection:
- M365-identity-device-management
- macOS
ms.subservice: apps
description: Deploy shell scripts to macOS devices with Microsoft Intune. Configure run frequency, retries, and user context, then monitor results.
ms.date: 2026-11-02T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 663c3193-e2f8-a905-5acd-340538e37f51
document_version_independent_id: 663c3193-e2f8-a905-5acd-340538e37f51
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-management/tools/run-shell-scripts-macos.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-management/tools/run-shell-scripts-macos
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-management/tools/run-shell-scripts-macos.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 5e1d7d7b-c811-593f-1208-a7bbcfbb9153
---

# Use Shell Scripts on macOS Devices in Microsoft Intune - Microsoft Intune | Microsoft Learn

Use shell scripts to extend device management capabilities in Intune, beyond what the macOS operating system supports.

Note

Rosetta 2 is required to run x64 (Intel) version of apps on Apple Silicon Macs. To install Rosetta 2 on Apple Silicon Macs automatically, deploy a shell script in Intune. To view a sample script, see [Rosetta 2 Installation Script](https://github.com/microsoft/shell-intune-samples/tree/master/macOS/Config/Rosetta2).

## Prerequisites

Ensure that the following prerequisites are met when composing shell scripts and assigning them to macOS devices.

- Devices run macOS 12.0 or later.
- Intune manages the devices.
- Devices connect directly to the Internet. Intune doesn't support connection through a proxy.
- Shell scripts begin with `#!` and are in a valid location such as `#!/bin/sh` or `#!/usr/bin/env zsh`.
- Command-line interpreters for the applicable shells are installed.

## Important considerations before using shell scripts

- Shell scripts require that the Microsoft Intune management agent is successfully installed on the macOS device. For more information, see [Microsoft Intune management agent for macOS](../../app-management/deployment/management-agent-macos).
- Shell scripts run in parallel on devices as separate processes.
- Shell scripts that run as the signed-in user run for all currently signed-in user accounts on the device at the time of the run.
- An end user must sign in to the device to execute scripts running as a signed-in user.
- Root user privileges are required if the script needs to make changes that a standard user account can't make.
- Shell scripts attempt to run more frequently than the chosen script frequency for certain conditions, such as if the disk is full, if the storage location is tampered with, if the local cache is deleted, or if the Mac device restarts.
- Shell scripts that run for longer than 60 minutes are stopped and reported as *failed*.

## Create and assign a shell script policy

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** &gt; **By platform** &gt; **macOS** &gt; **Manage devices** &gt; **Scripts** &gt; **Add**.
3. In **Basics**, enter the following properties, and select **Next**:

    - **Name**: Enter a name for the shell script.
    - **Description**: Enter a description for the shell script. We recommend this optional setting.
4. In **Script settings**, enter the following properties, and select **Next**:

    - **Upload script**: Browse to the shell script. The script file must be less than 1 MB in size.
    - **Run script as signed-in user**: Select **Yes** to run the script with the user's credentials on the device. Choose **No** (default) to run the script as the root user.
    - **Hide script notifications on devices:** By default, script notifications are shown for each script that runs. End users see a *IT is configuring your computer* notification from Intune on macOS devices.
    - **Script frequency:** Select how often the script runs. Choose **Not configured** (default) to run a script only once. Scripts with a frequency set also run after a device restart.
    - **Max number of times to retry if script fails:** Select how many times the script should run if it returns a non-zero exit code (zero means success). Choose **Not configured** (default) to not retry when a script fails.
5. In **Scope tags**, optionally add scope tags for the script, and select **Next**. Use scope tags to determine who can see scripts in Intune. For more information, see [Use role-based access control and scope tags for distributed IT](../../fundamentals/role-based-access-control/scope-tags).
6. Select **Assignments** &gt; **Select groups to include**. An existing list of Microsoft Entra groups is shown. Select one or more user or device groups to receive the script. Choose **Select**. The groups you choose are shown in the list. They receive your script policy.

    Note

    Shell scripts assigned to user groups apply to any user signing in to the Mac. Updating assignments for shell scripts also updates assignments for [Microsoft Intune MDM Agent for macOS](../../app-management/deployment/add-dmg-macos).
7. In **Review + add**, a summary is shown of the settings you configured. Select **Add** to save the script. When you select **Add**, the script policy is deployed to the groups you chose.

The script you created now appears in the list of scripts. If needed, you can view the contents of macOS shell scripts after you upload them to Intune.

## Monitor a shell script policy

You can monitor the run status of all assigned scripts for users and devices by choosing one of the following reports:

- **Scripts** &gt; **select the script to monitor** &gt; **Device status**
- **Scripts** &gt; **select the script to monitor** &gt; **User status**

Important

Regardless of the selected **Script frequency**, the script run status is reported only when the status changes from the last report. For example, if a script reports *Success* in one run and *Failure* in the next, Intune updates both the status and last updated timestamp with the current run information. If the script status doesn't change across syncs, Intune updates the last updated timestamp every seven days from the initial run.

When a script runs, it returns one of the following statuses:

- A script run status of **Failed** indicates that the script returned a non-zero exit code or the script is malformed.
- A script run status of **Success** indicates that the script returned zero as the exit code.

## Troubleshoot macOS shell script policies using log collection

You can collect device logs to help troubleshoot script issues on macOS devices.

### Requirements for log collection

To collect logs on a macOS device, you need to provide the following information:

- The full absolute log file path.
- File paths separated by only a semicolon (;).
- A maximum log collection size of 60 MB (compressed) or 25 files, whichever comes first.
- Allowed file types for log collection include the following extensions: *.log, .zip, .gz, .tar, .txt, .xml, .crash, .rtf*.

#### Collect device logs

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Go to **Devices** &gt; **Manage devices** &gt; **Scripts and remediations** &gt; **Platform scripts** and select a macOS shell script.
3. In **Device status** or **User status** report, select a device.
4. Select **Collect logs** and enter folder paths of log files separated by only a semicolon (;) without spaces or newlines between paths.

    For example, write multiple paths as `/Path/to/logfile1.zip;/Path/to/logfile2.log`.

    Important

    Using commas, periods, newlines, or quotation marks with or without spaces to separate multiple log file paths causes a log collection error. Don't use spaces as separators between paths.
5. Select **OK**. The Intune management agent on the device collects logs the next time it checks in with Intune. This check-in usually happens every 8 hours.

    Note

    - The device encrypts collected logs, transmits them, and stores them in Microsoft Azure storage for 30 days. The Microsoft Intune admin center decrypts and downloads stored logs on demand.
    - In addition to the admin-specified logs, the Intune management agent also collects logs from these folders: `/Library/Logs/Microsoft/Intune` and `~/Library/Logs/Microsoft/Intune`. The agent log file names are `IntuneMDMDaemon date--time.log` and `IntuneMDMAgent date--time.log`.
    - If any admin-specified file is missing or has the wrong file extension, find these file names listed in `LogCollectionInfo.txt`.

### Log collection errors

Log collection might be unsuccessful due to any of the following reasons. To resolve these errors, follow the remediation steps.

| Error code (hex) | Error code (dec) | Error message | Remediation steps |
| --- | --- | --- | --- |
| 0X87D300D1 | 2016214834 | Log file size can't exceed 60 MB. | Ensure that compressed logs are less than 60 MB in size. |
| 0X87D300D1 | 2016214831 | The provided log file path must exist. The system user folder is an invalid location for log files. | Ensure that the provided file path is valid and accessible. |
| 0X87D300D2 | 2016214830 | Log collection file upload failed due to expiration of upload URL. | Retry the **Collect logs** action. |
| 0X87D300D3, 0X87D300D5, 0X87D300D7 | 2016214829, 2016214827, 2016214825 | Log collection file upload failed due to encryption failure. Retry log upload. | Retry the **Collect logs** action. |
|  | 2016214828 | The number of log files exceeded the allowed limit of 25 files. | You can collect only up to 25 log files at a time. |
| 0X87D300D6 | 2016214826 | Log collection file upload failed due to zip error. Retry log upload. | Retry the **Collect logs** action. |
|  | 2016214740 | The logs couldn't be encrypted as compressed logs weren't found. | Retry the **Collect logs** action. |
|  | 2016214739 | The logs were collected but couldn't be stored. | Retry the **Collect logs** action. |

## Custom attributes for macOS

You can create custom attribute profiles that enable you to collect custom properties from managed macOS devices by using shell scripts.

### Create and assign a custom attribute for macOS devices

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** &gt; **By platform** &gt; **macOS** &gt; **Organize devices** &gt; **Custom attributes for macOS** &gt; **Add**.
3. In **Basics**, enter the following properties, and select **Next**:

    - **Name**: Enter a name for the script.
    - **Description**: Enter a description for the script. This setting is optional, but recommended.
4. In **Attribute settings**, enter the following properties, and select **Next**:

    - **Data type of attribute**: Select the data type of the result that the script returns. Available values are **String**, **Integer**, and **Date**.
    - **Script**: Select a script file.

    Additional details:

    - The shell script must echo the attribute to report, and the data type of the output must match the data type of the attribute in the custom attribute profile.
    - The result returned by the shell script must be 20 KB or less.

    Note

    When using `Date` type attributes, ensure that the shell script returns dates in ISO-8601 format. See the following examples.

    **To print an ISO-8601-compliant date with time-zone:**

    ```Shell
    #!/bin/sh
    var=$(date +"%Y-%m-%dT%H:%M:%S%z")
    echo $var # Prints an ISO-8601 compliant date with time-zone
    ```

    **To print an ISO-8601-compliant date in UTC time:**

    ```Shell
    #!/bin/sh
    var=$(date -u +"%Y-%m-%dT%H:%M:%SZ")
    echo $var # Prints an ISO-8601 compliant date in UTC time
    ```
5. In **Assignments**, select **Select groups to include**. When you choose **Select groups to include**, an existing list of Microsoft Entra groups is shown. Select one or more user or device groups to receive the script. Choose **Select**. The groups you choose are shown in the list. They receive your script policy.

    Alternatively, you can choose to select **All users**, **All devices**, or **All users and all devices** by selecting one of these options in the dropdown box next to **Assign to**.

    Note

    Scripts assigned to user groups apply to any user signing in to the Mac.
6. In **Review + add**, a summary is shown of the settings you configured. Select **Add** to save the script. When you select **Add**, the script policy is deployed to the groups you chose.

The script you created now appears in the list of custom attributes. View the contents of custom attributes after you upload them to Intune.

## Monitor a custom attribute policy

You can monitor the run status of all assigned custom attribute profiles for users and devices by choosing one of the following reports:

- **Custom attributes** &gt; *select the custom attribute profile to monitor* &gt; **Device status**
- **Custom attributes** &gt; *select the custom attribute profile to monitor* &gt; **User status**

Important

Shell scripts provided in custom attribute profiles run every 8 hours on managed Macs and report their status.

When a custom attribute profile runs, it returns one of the following statuses:

- A status of **Failed** indicates that the script returned a non-zero exit code or the script is malformed. The error is reported in the **Result** column.
- A status of **Success** indicates that the script returned zero as the exit code. The output echoed by the script is reported in the **Result** column.

## Frequently asked questions

### Why are assigned shell scripts not running on the device?

Several reasons could cause this problem:

- The agent might need to check in to receive new or updated scripts. This check-in process occurs every 8 hours and is different from the MDM check-in. Ensure that the device is awake and connected to a network for a successful agent check-in and wait for the agent to check in. You can also request the end user to open Company Portal on the Mac, select the device, and select **Check settings**.
- The agent might not be installed. Check that the agent is installed at `/Library/Intune/Microsoft Intune Agent.app` on the macOS device.
- The agent might not be in a healthy state. The agent attempts to recover for 24 hours, remove itself, and reinstall if shell scripts are still assigned.

### How frequently is script run status reported?

Script run status is reported to Microsoft Intune admin center as soon as script run is complete. If a script is scheduled to run periodically at a set frequency, it only reports status the first time it runs.

### When are shell scripts run again?

When a script returns a non-zero exit code, Intune retries it according to the **Max number of times to retry if script fails** setting. If that setting is **Not configured**, Intune doesn't retry the failed run and reports its status as **failed**. Scripts with a configured frequency can also run again on schedule or after a device restart.

### What Intune role permissions are required for shell scripts?

Your assigned Intune role needs **Device configurations** permissions to delete, assign, create, update, or read shell scripts.

## Known issues

- **No script run status:** If the device receives a script but goes offline before it reports the run status, the device doesn't report the run status for the script in the admin center.

## Additional information

When you deploy shell scripts or custom attributes for macOS devices from Microsoft Intune, you deploy the new universal version of the Intune management agent app that runs natively on Apple Silicon Mac machines. The same deployment installs the x64 version of the app on Intel Mac machines.

You need Rosetta 2 to run the x64 (Intel) version of apps on Apple Silicon Macs. To automatically install Rosetta 2 on Apple Silicon Macs, you can deploy a shell script in Intune. To view a sample script, see [Rosetta 2 Installation Script](https://github.com/microsoft/shell-intune-samples/tree/master/macOS/Config/Rosetta2).