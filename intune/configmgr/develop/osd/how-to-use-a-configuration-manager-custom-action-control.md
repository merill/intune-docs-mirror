---
layout: Conceptual
title: Use a Custom Action Control - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-use-a-configuration-manager-custom-action-control
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
description: The custom action control is used to configure a custom action that you have defined. The custom action then becomes a step in the task sequence you are editing.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: bc03f2c7-b6bc-749f-b5ab-66343d56060d
document_version_independent_id: e8fe001b-ec43-e2e9-871a-f4857c175f7b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/osd/how-to-use-a-configuration-manager-custom-action-control.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/osd/how-to-use-a-configuration-manager-custom-action-control
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/osd/how-to-use-a-configuration-manager-custom-action-control.md
cmProducts: []
platformId: f4bd46d2-522b-ab31-7347-4fbdafacca89
---

# Use a Custom Action Control - Configuration Manager | Microsoft Learn

In Configuration Manager, you use a custom action control by selecting it in the Configuration Manager console Task Sequence Editor. The custom action control is used to configure a custom action that you have defined. The custom action becomes a step in the task sequence you are editing. The following procedure assumes that you have completed the tasks in the following topics:

[How to Create a Configuration Manager Custom Action Control](how-to-create-a-configuration-manager-custom-action-control)

[How to Create a MOF File for a Configuration Manager Custom Action](how-to-create-a-mof-file-for-a-configuration-manager-custom-action)

The following procedure demonstrates the custom action control saving its properties and reloading them the next time that the action is edited.

To use the custom action as part of the sequence that contains it, you will need to advertise it using a Configuration Manager task sequence package. For more information, see [About Configuration Manager Custom Action Client Applications](about-configuration-manager-custom-action-client-applications)

Note

Step 1 and step 2 are only necessary if the action control Managed Object Format (MOF) file or assembly has been changed.

### How to use a custom action control in the task sequence editor

1. If the Configuration Manager console is open, close it.
2. Open the Configuration Manager console.
3. In the Configuration Manager console, navigate to **Software Library** / **Operating Systems**.
4. Right-click **Task Sequences**, and select **Create Task Sequence**. The New Task Sequence Wizard is displayed.
5. Select **Create a new custom task sequence**, and click **Next**.
6. In **Task sequence name**, enter `My custom task sequence`.
7. Click **Next**, confirm the summary information, and click **Next** again to create the task sequence.
8. Click **Close** to close the wizard.
9. In the results pane, right-click the task sequence that you just created and select **Edit** to display the Task Sequence Editor.
10. In the Task Sequence Editor, select **Add**, and the categories list is displayed.
11. Select **CustomActionCategory**, and your custom action appears as one of the possible choices.
12. Select your custom action (**ConfigMgrTSActionControl**), and the control is displayed.
13. Add some text to the edit box, and then click **OK**. The Task Sequence Editor should be closed.
14. Edit the task sequence again and select your custom action.
15. Note that the text you entered has been retained.