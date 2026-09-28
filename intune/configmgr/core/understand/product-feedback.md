---
layout: Conceptual
title: Product feedback - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/understand/product-feedback
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
description: Share feedback with the Configuration Manager product team.
ms.date: 2022-04-08T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: dbb04136-cd29-0194-9f10-bd3994f6daea
document_version_independent_id: 24f105a5-c70a-584d-c82e-9c24f9c5db21
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/understand/product-feedback.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/understand/product-feedback
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/understand/product-feedback.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/63959238-cb90-4871-a33d-4a5519097e47
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/78d87f42-5582-4a6b-90be-7db2f12b34e6
platformId: 7b1d85d2-966c-3ef0-7e97-3b57aa560379
---

# Product feedback - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

From the Configuration Manager console, you can share feedback directly to the Microsoft product group. In the upper right corner of the console, select the feedback icon. There are three types of feedback:

![Screenshot of the submit feedback icon in Configuration Manager.](media/console-share-feedback.png)

- **Send a smile** (**ALT** + **SHIFT** + **7**): Send feedback on what you liked.
- **Send a frown** (**ALT** + **SHIFT** + **8**): Send feedback on what you didn't like, and how Microsoft can improve it.
- **Send a suggestion** (**ALT** + **SHIFT** + **9**): Open the Configuration Manager product feedback website to share your idea. For more information, see Send a suggestion.
- **Contact support** (**ALT** + **SHIFT** + **0**): Opens the [Microsoft support for business portal](https://aka.ms/cmcbsupport).

When using the feedback wizard from the console, the following items are displayed where needed:

- A description of the feedback is required
- Select from a list of issue categories for the console workspace
- It includes tips for how to write useful feedback
- You can attach additional files
- A summary page displays your feedback ID, and includes any error messages with suggestions to resolve them.

Note

This wizard is in the Configuration Manager console. Support Center has a similar feedback experience.

## Recent changes to feedback

Starting in version 2203, you have the ability to connect feedback you send to Microsoft through the Configuration Manager console to an authenticated Microsoft Entra user account or Microsoft Account (MSA). User authentication will help Microsoft ensure the privacy of your feedback and diagnostic data. Currently, Microsoft Entra authentication for government clouds isn't available. After selecting either **Send a smile** or **Send a frown**: 

1. Select **Sign in**and sign in with either your Microsoft Entra user account or your Microsoft account.
    - Selecting **Continue without signing in** will allow you to send feedback, but we won't be able to contact you with questions or updates unless you provide an e-mail address.
2. Once you're signed in, select **Next** then provide your feedback. If you need to use a different account, you can select **Sign out** to start again.

Starting in version 2203, the feedback button is displayed in additional console locations. You can also use the keyboard shortcuts for **Send a smile** and **Send a frown** from more locations in the console. 

Starting in Configuration Manager 2111, when you **Report error to Microsoft** the error information included with the feedback can't be altered or removed. Wizards and some property pages also include an icon to provide feedback allowing you to quickly send feedback right from your current activity.

Starting in version 2107, error messages include a link to **Report error to Microsoft**. This action opens the standard send a frown window to provide feedback. It automatically includes details about the user interface and the error to better help Microsoft engineers diagnose the error. Aside from making it easier to send a frown, it also includes the full context of the error message when you share a screenshot. 

## Prerequisites

Update the Configuration Manager console to the latest version.

On the computer where you run the console, allow it to access the following internet endpoints to send diagnostic data to Microsoft:

- `petrol.office.microsoft.com`
- `ceuswatcab01.blob.core.windows.net`
- `ceuswatcab02.blob.core.windows.net`
- `eaus2watcab01.blob.core.windows.net`
- `eaus2watcab02.blob.core.windows.net`
- `weus2watcab01.blob.core.windows.net`
- `weus2watcab02.blob.core.windows.net`
- `umwatsonc.events.data.microsoft.com`
- `*-umwatsonc.events.data.microsoft.com`

## Send a smile

To send feedback on something that you like about Configuration Manager:

1. In the upper-right corner of the Configuration Manager console, select the feedback icon. Choose **Send a smile**.
2. On the first page of the **Provide feedback** wizard:

    - **Tell us what you liked**: Enter a detailed description of why you're filing this feedback.
    - **You can contact me about this feedback**: To allow Microsoft to contact you about this feedback if necessary, select this option and specify a valid email address.
    - **Include screenshot**: Select this option to add a screenshot. By default it uses the full screen, select **Refresh** to capture the latest image. Select **Browse** to select a different image file.

    [![Screenshot of Provide feedback wizard to send a smile.](media/3180826-send-a-smile-2010.png)](media/3180826-send-a-smile-2010.png#lightbox)
3. Select **Next** to send the feedback. You may see a progress bar as it packages the content to send.
4. When the progress is complete, select **Details** to see the transaction ID or any errors that occurred.

    [![Screenshot of Provide feedback wizard completion page.](media/provide feedback-complete.png)](media/provide%20feedback-complete.png#lightbox)

## Send a frown

Before you file a frown, prepare your information:

- If you have multiple issues, send a separate report for each issue. Don't include multiple issues in a single report.
- Provide clear details on the issue. Share any research that you've gathered so far. More detailed information is better to help Microsoft investigate and diagnose the issue.
- Do you need immediate assistance? If so, contact Microsoft support for urgent issues. For more information, see [Support options and community resources](find-help#support-options-and-community-resources).
- Is this feedback a suggestion to improve the product? If so, share a new idea instead. For more information, see Send a suggestion.
- Is the issue with the product documentation? You can file feedback directly on the documentation. For more information, see [Doc feedback](../../../fundamentals/use-docs#about-feedback).

To send feedback on something that you didn't like about the Configuration Manager product:

1. In the upper-right corner of the Configuration Manager console, select the feedback icon. Choose **Send a frown**.
2. On the first page of the **Provide feedback** wizard:

    - **Issue category**: Select a category that's most appropriate for your issue.
    - Describe your issue with as much detail as possible.
    - **You can contact me about this feedback**: To allow Microsoft to contact you about this feedback if necessary, select this option and specify a valid email address.

    [![Screenshot of Provide feedback wizard to send a frown.](media/3180826-describe-issue-2010.png)](media/3180826-describe-issue-2010.png#lightbox)
3. On the **Add more details** page of the wizard:

    - **Include screenshot**: Select this option to add a screenshot. By default it uses the full screen, select **Refresh** to capture the latest image. Select **Browse** to select a different image file.
    - **Include additional files**: Select **Attach** and add log files, which can help Microsoft better understand the issue. To remove all attached files from your feedback, select **Clear all**. To remove individual files, select the delete icon to the right of the file name.

    [![Screenshot of Add more details page in Provide feedback wizard.](media/3180826-add-more-details.png)](media/3180826-add-more-details.png#lightbox)
4. Select **Next** to send the feedback. You may see a progress bar as it packages the content to send.
5. When the progress is complete, select **Details** to see the transaction ID or any errors that occurred.

If you don't have internet connectivity:

- The **Provide feedback** wizard still packages your feedback and files.
- The final summary page shows an error that it couldn't send the feedback.
- Select the option to **Save a copy of feedback and attachments**. For more information on how to send it to Microsoft, see Send feedback that you saved for later submission.

If the **Provide feedback** wizard successfully submits your feedback, but fails to send the attached files, use the same instructions for no internet connectivity.

## Send a suggestion

When you **Send a suggestion**, it opens the [Feedback for Configuration Manager](https://feedbackportal.microsoft.com/feedback/forum/4669adfc-ee1b-ec11-b6e7-0022481f8472) site.

For more information, including the different status values, see [How Microsoft uses feedback](/en-us/microsoft-365/admin/misc/feedback-provide-microsoft#how-microsoft-uses-feedback).

## Status messages

When you **Send a smile** or **Send a frown**, it creates a status message when you submit the feedback. This message provides a record of:

- When you submitted the feedback
- Who submitted it
- The feedback ID
- The message ID identifies if the feedback submission was successful:
    - **53900**: Success
    - **53901**: Failed

![Status message for successfully submitting feedback.](media/5891852-send-smile-status-message.png)

You can use the built-in status message query, **Feedback sent to Microsoft** to easily display these status messages. You can also display status messages in the **Monitoring** workspace, under **System Status** in the **Status Message Queries** node. Start with the **All Status Messages** query and select your time frame. When the messages load, select **Filter messages**, and filter for message ID 53900 or 53901. If you create feedback that you save for later submission, the site doesn't create a status message.

## Information sent with feedback

When you **Send a smile** or **Send a frown**, the feedback includes the following information:

- OS build information
- Configuration Manager support ID, also known as the hierarchy ID
- Product build information
- Language information
- Device identifier: `HKLM\SOFTWARE\Microsoft\SQMClient:MachineId`

## Send feedback that you saved for later submission

You can save your feedback locally and submit it later. Use this process if the current computer doesn't have internet-access.

1. At the bottom of the **Provide feedback** window, select **Save a copy of feedback and attachments**.
2. Save the .zip file. If the local machine doesn't have internet access, copy the file to an internet-connected machine.
3. If needed, copy the **UploadOfflineFeedback** folder from the site server located at `cd.latest\SMSSETUP\Tools\UploadOfflineFeedback\`.

    Note

    For more information about the cd.latest folder, see [the CD.Latest folder](../servers/manage/the-cd.latest-folder).
4. On an internet-connected machine, open a command prompt.
5. Run the following command: `UploadOfflineFeedback.exe -f c:\folder\location_of.zip`

### UploadOfflineFeedback tool usage

The UploadOfflineFeedback tool supports the following command-line parameters:

- `-f`, `--file` (**Required**): The path to the saved feedback file to send.
- `-t`, `--timeout`: Timeout in seconds for sending the data. `0` is unlimited. Default is `30`.
- `-s`, `--silent`: Don't log any output to the command prompt. You can't combine this parameter with `--verbose`.
- `-v`, `--verbose`: Log verbose output to the command prompt. You can't combine this parameter with `--silent`.
- `--help`: Display this usage information.
- `--version`: Display the tool version.

The UploadOfflineFeedback utility supports the use of a proxy server. You can specify the following parameters:

- `-x`, `--proxy`: Specify the proxy server address.
- `-o`, `--port`: Specify the port for the proxy server.
- `-u`, `--user`: Specify the user name to authenticate to the proxy server.
- `-w`, `--password`: Specify the password for the specified user name. If you use an asterisk (`*`), the tool prompts for the password. The password isn't displayed in the prompt. This value is recommended. Including the password in plain text on the command line is less secure.
- `-i`, `--SkipConnectionCheck`: Skips the network connection check, and just starts to upload the feedback with the specified settings.

## Confirmation of console feedback

When you send feedback, it shows a confirmation message. This message includes a **Feedback ID**, which you can give to Microsoft as a tracking identifier.

- In the Provide feedback window from the console, it displays the feedback ID on the final page. To copy it, select the copy icon next to the ID, or use the **CTRL** + **C** key shortcut. This ID isn't stored on your computer, so make sure to copy it before you close the window.
- The status message includes the feedback ID.
- The **UploadOfflineFeedback** command tool writes the **FeedbackID** to the console unless you use `--silent`.

    ![Feedback confirmation from UploadOfflineFeedback.exe in Configuration Manager.](media/1902-offline-feedback-id-example.png)

## Feedback for Support Center

If you have feedback on [Support Center](../support/support-center), use the following instructions:

1. In the upper right corner of the application, select the smiley face.
2. In the drop-down menu, select **Send a smile** or **Send a frown**.

    - If you select **Send a suggestion**, you will be taken to the feedback portal. For more information, see Send a suggestion.
3. Use the text box to explain what you liked or what you didn't like.
4. Choose if you would like to share your e-mail address and a screenshot.
5. Select **Submit Feedback**.

[![Screenshot of the feedback form in Support Center.](media/feedback-support-center.png)](media/feedback-support-center.png#lightbox)

## Feedback for PowerShell

If you have feedback on the [Configuration Manager PowerShell cmdlets](/en-us/powershell/module/configurationmanager), use the same options in the Configuration Manager console to send feedback.

When you send a frown, include the following additional information specific to PowerShell:

- The exact script or command syntax that you used so that Microsoft can try to reproduce the issue.
- What behavior you expected compared to the actual behavior.
- The full output when you run it with the [Verbose](/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters#verbose) common parameter.
- The version and path of the **ConfigurationManager** module. For example, include the output of the following commands:

    ```powershell
    (Get-Module -Name ConfigurationManager).Version
    (Get-Module -Name ConfigurationManager).Path
    ```
- If a cmdlet returns an error, use the following command to get exception details:

    ```powershell
    $Error[0].Exception | Format-List * -Force
    ```