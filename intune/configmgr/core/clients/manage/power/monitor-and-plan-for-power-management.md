---
layout: Conceptual
title: Monitor and plan for power management - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/power/monitor-and-plan-for-power-management
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
description: Learn how to monitor and plan for power management in Configuration Manager.
ms.date: 2016-10-06T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 08fb39ea-6495-92ff-da5d-5ae81da7fd45
document_version_independent_id: ac3ab2c2-4789-8c1b-2345-dd26449a1d5b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/manage/power/monitor-and-plan-for-power-management.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/manage/power/monitor-and-plan-for-power-management
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/manage/power/monitor-and-plan-for-power-management.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: 80a0ff1f-bcbb-2fc8-e308-d754c75e5510
---

# Monitor and plan for power management - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Use the following information to help you monitor and plan for power management in Configuration Manager.

## How to use reports for power management

Power management in Configuration Manager includes several reports to help you analyze power consumption and computer power settings in your organization. The reports can also be used to help you troubleshoot problems.

Before you can use the power management reports, you must configure reporting for your hierarchy. For more information about reporting in Configuration Manager, see [Introduction to reporting](../../../servers/manage/introduction-to-reporting).

Note

Power management information used by daily reports is retained in the Configuration Manager site database for 31 days. Power management information used by monthly reports is retained in the Configuration Manager site database for 13 months.

When you run reports during the monitoring and planning and compliance phases of power management, save or export the results from any reports for which you want to retain the data for later comparison in case they are later removed by Configuration Manager.

## List of power management reports

The following lists details the power management reports that are available in Configuration Manager.

Note

Power management reports display the number of physical computers and the number of virtual computers in a selected collection. However, only power management information from physical computers is displayed in power management reports.

### Computer Activity report

The **Computer Activity** report displays a graph showing the following activity for a specified collection over a specified period:

- **Computer On** – The computer has been turned on.
- **Monitor On** – The monitor has been turned on.
- **User Active** – Activity has been detected from the computer mouse, computer keyboard, or from a Remote Desktop connection to the computer

    This report is used during the monitoring and planning and enforcement stages to help you understand the alignment between computer activity, monitor activity and user activity over a 24 hour period. If you run the report over a number of days then the data is aggregated over this period. This report can help you to determine typical business (peak) and nonbusiness (non-peak) hours for a selected collection to help you decide when to apply configured power management plans.

    The graph shows time periods where a computer might be turned on, but there is no user activity. Consider applying more restrictive power settings during these times to save on the power costs of computers that are turned on, but are not being used. A computer is counted as being active if there has been computer, user or monitor activity for one minute or more for a displayed hour on the graph. If a computer is not reporting power management data, it will not be included in the **Computer Activity** report.

    Use the following parameters to configure this report.

#### Required report parameters

The following parameters must be specified to run this report.

| Parameter Name | Description |
| --- | --- |
| **Start date** | From the drop-down list, select the start date for this report. |
| **End date (Optional)** | From the drop-down list, select an optional end date for this report. |
| **Collection name** | From the drop-down list, select a collection to use for this report. |
| **Device type** | From the drop-down list, select the type of computer for which you want a report. Valid values are **All** (both desktop and portable computers), **Desktop** (desktop computers only), and **Laptop** (portable computers only). |

#### Hidden report parameters

This report has no hidden parameters that you can set.

#### Report links

If a value for **End date (optional)** is not specified, this report contains a link to the following report which provides further information.

| Report Name | Details |
| --- | --- |
| **Computer Activity Details** | Click the **Click for detailed information** link to see a list of active, inactive and non-reporting computers for the specified date. For more information, see Computer Activity Details Report in this topic. |

### Computer Activity by Computer report

The **Computer Activity by Computer** report displays a graph showing the following activity for a specified computer on a specified date:

- **Computer On** – The computer has been turned on.
- **Monitor On** – The monitor has been turned on.
- **User Active** – Activity has been detected from the computer mouse, computer keyboard, or from a Remote Desktop connection to the computer.

    This report can be run independently or called by the **Computer Activity Details** report.

Note

Information about computer activity is collected from client computers during hardware inventory. Depending on the time at which hardware inventory runs, activity during an applied peak or non-peak power plan might be collected.

Use the following parameters to configure this report.

#### Required report parameters

The following parameters must be specified to run this report.

| Parameter Name | Description |
| --- | --- |
| **Report date** | From the drop-down list, select a date for this report. |
| **Computer name** | Enter a computer name for which you want a report. |

#### Hidden report parameters

This report has no hidden parameters that you can set.

#### Report links

This report contains links to the following report which provides further information about the selected item.

| Report Name | Details |
| --- | --- |
| **Computer Details** | Click the **Click for detailed information** link to see the power capabilities, power settings, and applied power plans for the selected computer. |

### Computer Activity Details report

The **Computer Activity Details** report displays a list of active or inactive computers with their sleep and wake capabilities. This report is called by the Computer Activity Report and is not designed to be run directly by the site administrator.

Use the following parameters to configure this report.

#### Required report parameters

The following parameters must be specified to run this report.

| Parameter Name | Description |
| --- | --- |
| **Collection name** | From the drop-down list, select a collection to use for this report. |
| **Report date** | From the drop-down list, select a date to use for this report. |
| **Report hour** | From the drop-down list, select an hour from the specified date for which to run this report. Valid values are between **12am** and **11pm**. |
| **Computer state** | From the drop-down list, select the computer state for which to run this report. Valid values are **All** (computers that were turned on or off), **On** (computers that were turned on), and **Off** (computers that were turned off, in sleep, or in hibernate). These values are only returned for the chosen reporting period. |
| **Device type** | From the drop-down list, select the type of computer for which you want a report. Valid values are **All** (both desktop and portable computers), **Desktop** (desktop computers only), and **Laptop** (portable computers only). These values are only returned for the chosen reporting period. |
| **Sleep capable** | From the drop-down list, select if you want to display computers capable of sleep in the report. Valid values are **All** (both computers capable and incapable of sleep), **No** (computers that are incapable of sleep), and **Yes** (computers that are capable of sleep). |
| **Wake from sleep capable** | From the drop-down list, select if you want to display computers capable of wake from sleep in the report. Valid values are **All** (both computers capable and incapable of wake from sleep), **No** (computers that are incapable of wake from sleep), and **Yes** (computers that are capable of wake from sleep). |
| **Power plan** | From the drop-down list, select the power plan types you want to display in the report. Valid values are **All** (computers that do not have any power management plans applied; computers that have a power management plan applied; computers excluded from power management), **Not specified** (computers that do not have a power management plan applied), **Defined** (computers that have a power management plan applied), and **Excluded** (computers that have been excluded from power management). |
| **Operating system** | From the drop-down list, select the computer operating systems that you want to display in the report or select **All** to display all operating systems. |

#### Hidden report parameters

This report has no hidden parameters that you can set.

#### Report links

This report contains links to the following report which provides further information about the selected item.

| Report Name | Details |
| --- | --- |
| **Computer Activity by Computer** | Click a computer name to see specific activity for that computer over a chosen reporting period. These activities include **Computer on** (has the computer been turned on?), **Monitor on** (has the monitor been turned on?), and **User Active** (activity has been detected from the computer's mouse, keyboard, or a remote desktop connection). For more information, see Computer Activity by Computer Report in this topic. |

### Computer Details report

The **Computer Details** report displays detailed information about the power capabilities, power settings, and power plans applied to a specified computer. This report is called by the **Computer Activity by Computer** report, the **Computers with Multiple Power Plans** report, the **Power Capabilities** report and the **Power Settings Details** report. It is not designed to be run directly by the site administrator.

#### Required report parameters

The following parameters must be specified to run this report.

| Parameter Name | Description |
| --- | --- |
| **Computer name** | Enter a computer name for which you want a report. |
| **Power mode** | From the drop down list, select the type of power settings you want to display in the report results. Select **Plugged In** to view the power settings configured for when the computer is plugged in and **On Battery** to view the power settings configured for when the computer is running on battery power. |

#### Hidden report parameters

This report has no hidden parameters you can set.

#### Report links

This report does not link to any other power management reports.

### Computer Not Reporting Details report

The **Computer Not Reporting Details** report displays a list of computers in a specified collection that have not reported any power activity on a specified date and time. This report is called by the **Computer Activity Report** and is not designed to be run directly by the site administrator.

Note

Computers report power management information as part of their hardware inventory schedule. Before you consider a computer to not be reporting, ensure it has reported hardware inventory.

Use the following parameters to configure this report.

#### Required report parameters

The following parameters must be specified to run this report.

| Parameter Name | Description |
| --- | --- |
| **Collection name** | From the drop-down list, select a collection to use for this report. |
| **Report date** | From the drop-down list, select a date for this report. |
| **Report hour** | From the drop-down list, select an hour from the specified date for which to run this report. Valid values are between **12am** and **11pm**. |
| **Device type** | From the drop-down list, select the type of computer for which you want a report. Valid values are **All** (both desktop and portable computers), **Desktop** (desktop computers only), and **Laptop** (portable computers only). These values are only returned for the chosen reporting period. |

#### Hidden report parameters

This report has no hidden parameters that you can set.

#### Report links

This report does not link to any other power management reports.

### Computers Excluded

The **Computers Excluded** report displays a list of computers in a specified collection that have been excluded from Configuration Manager power management.

Use the following parameters to configure this report.

#### Required report parameters

The following parameters must be specified to run this report.

| Parameter Name | Description |
| --- | --- |
| **Collection** | From the drop-down list, select a collection for this report. |
| **Reason** | From the drop-down list, select the reason why the computers were excluded from power management. You can display **All** (all excluded computers), **Excluded by administrator** (only computers that were excluded by an administrative user), and **Excluded by user** (only computers that were excluded by a user of Software Center). |

#### Hidden report parameters

This report has no hidden parameters that you can set.

#### Report links

This report contains links to the following report which provides further information about the selected item.

| Report Name | Details |
| --- | --- |
| **Power Computer Details** | Click a computer name to see the power capabilities, power settings, and applied power plans for the selected computer. For more information, see Computer Details Report in this topic. |

### Computers with Multiple Power Plans

The **Computers with Multiple Power Plans** report displays a list of computers that are members of multiple collections, each applying different power plans. For each computer with potentially conflicting power settings, the report displays the computer name and the power plans being applied for each collection that the computer is a member of.

Important

If a computer is a member of multiple collections, where each collection has different power plans, then the least restrictive power plan will be applied.

If a computer is a member of multiple collections, where each collection has different wakeup times, then the time closest to midnight will be used.

Use the following parameters to configure this report.

#### Required report parameters

The following parameters must be specified to run this report.

| Parameter Name | Description |
| --- | --- |
| **Collection name** | From the drop-down list, select a collection for this report. |

#### Hidden report parameters

This report has no hidden parameters that you can set.

#### Report links

This report contains links to the following report which provides further information about the selected item.

| Report Name | Details |
| --- | --- |
| **Power Computer Details** | Click a computer name to see the power capabilities, power settings, and applied power plans for the selected computer. For more information, see Computer Details Report in this topic. |

### Energy Consumption report

The **Energy Consumption** report displays the following information:

- A graph showing the total monthly power consumption of computers in kiloWatt per hour (kWh) in the specified collection for the specified time period.
- A graph showing the average power consumption in kiloWatt per hour (kWh) of each computer in the specified collection for the specified time period.
- A table showing the total monthly power consumption in kiloWatt per hour (kWh) and the average power consumption of computers in the specified collection for the specified time period.

    This information can be used to help you to understand power consumption trends in your environment. After applying a power plan to computers in the selected collection, the power consumption of computers should decrease.

Note

If you add or remove members to the collection after you have applied a power plan, this will affect the results shown by the **Energy Consumption** report and might make it more difficult to compare the results from the monitoring and planning phase and the enforcement phase.

Use the following parameters to configure this report.

#### Required report parameters

The following parameters must be specified to run this report.

| Parameter Name | Description |
| --- | --- |
| **Start date** | From the drop-down list, select a start date for this report. |
| **End date** | From the drop-down list, select an end date for this report. |
| **Collection name** | From the drop-down list, select a collection for this report. |
| **Device type** | From the drop-down list, select the type of computer for which you want a report. Valid values are **All** (both desktop and portable computers), **Desktop** (desktop computers only), and **Laptop** (portable computers only). These values are only returned for the chosen reporting period. |

#### Hidden report parameters

The following hidden parameters can optionally be specified to change the behavior of this report.

| Parameter Name | Description |
| --- | --- |
| **Desktop computer on** | Specify the power consumption of a desktop computer when it is turned on. The default value is **0.07** kW per hour. |
| **Laptop computer on** | Specify the power consumption of a portable computer when it is turned on. The default value is **0.02** kW per hour. |
| **Desktop computer sleep** | Specify the power consumption of a desktop computer that has entered sleep. The default value is **0.003** kW per hour. |
| **Laptop computer sleep** | Specify the power consumption of a portable computer that has entered sleep. The default value is **0.001** kW per hour. |
| **Desktop computer off** | Specify the power consumption of a desktop computer when it is turned off. The default value is **0** kW per hour. |
| **Laptop computer off** | Specify the power consumption of a portable computer when it is turned off. The default value is **0** kW per hour. |
| **Desktop monitor on** | Specify the power consumption of a desktop computer monitor when it is turned on. The default value is **0.028** kW per hour. |
| **Laptop monitor on** | Specify the power consumption of a portable computer monitor when it is turned on. The default value is **0** kW per hour. |

#### Report links

This report does not link to any other power management reports.

### Energy Consumption by Day report

The **Energy Consumption by Day** report displays the following information:

- A graph showing the total daily power consumption of computers in kiloWatt per hour (kWh) in the specified collection for the last 31 days.
- A graph showing the average daily power consumption in kiloWatt per hour (kWh) of each computer in the specified collection for last 31 days.
- A table showing the total daily power consumption in kiloWatt per hour (kWh) and the average daily power consumption of computers in the specified collection for the last 31 days.

    This information can be used to help you to understand power consumption trends in your environment. After applying a power plan to computers in the selected collection, the power consumption of computers should decrease.

Note

If you add or remove members to the collection after you have applied a power plan, this will affect the results shown by the **Energy Consumption** report and might make it more difficult to compare the results from the monitoring and planning phase and the enforcement phase.

Use the following parameters to configure this report.

#### Required report parameters

The following parameters must be specified to run this report.

| Parameter Name | Description |
| --- | --- |
| **Collection** | From the drop-down list, select a collection for this report. |
| **Device Type** | From the drop-down list, select the type of computer for which you want to report. Valid values are **All** (both desktop and portable computers), **Desktop** (desktop computers only), and **Laptop** (portable computers only). These values are only returned for the chosen reporting period. |

#### Hidden report parameters

The following hidden parameters can optionally be specified to change the behavior of this report.

| Parameter Name | Description |
| --- | --- |
| **Desktop computer on** | Specify the power consumption of a desktop computer when it is turned on. The default value is **0.07** kW per hour. |
| **Laptop computer on** | Specify the power consumption of a portable computer when it is turned on. The default value is **0.02** kW per hour. |
| **Desktop computer sleep** | Specify the power consumption of a desktop computer that has entered sleep. The default value is **0.003** kW per hour. |
| **Laptop computer sleep** | Specify the power consumption of a portable computer that has entered sleep. The default value is **0.001** kW per hour. |
| **Desktop computer off** | Specify the power consumption of a desktop computer when it is turned off. The default value is **0** kW per hour. |
| **Laptop computer off** | Specify the power consumption of a portable computer when it is turned off. The default value is **0** kW per hour. |
| **Desktop monitor on** | Specify the power consumption of a desktop computer monitor when it is turned on. The default value is **0.028** kW per hour. |
| **Laptop monitor on** | Specify the power consumption of a portable computer monitor when it is turned on. The default value is **0** kW per hour. |

#### Report links

This report does not link to any other power management reports.

### Energy Cost report

The **Energy Cost** report displays the following information:

- A graph showing the total monthly power cost for computers in the specified collection for specified time period.
- A graph showing the average monthly power cost for each computer in the specified collection for the specified time period.
- A table showing the total monthly power cost and the average monthly power cost for computers in the specified collection for the last 31 days.

    This information can be used to help you to understand power cost trends in your environment. After applying a power plan to computers in the selected collection, the power cost for computers should decrease.

    Use the following parameters to configure this report.

#### Required report parameters

The following parameters must be specified to run this report.

| Parameter Name | Description |
| --- | --- |
| **Start date** | From the drop-down list, select a start date for this report. |
| **End date** | From the drop-down list, select an end date for this report. |
| **Cost of KwH** | Specify the cost per kWh of electricity. The default value is **0.09**. You can modify the unit of currency used by this report in the hidden parameters section. |
| **Collection name** | From the drop-down list, select a collection to use for this report. |
| **Device type** | From the drop-down list, select the type of computer for which you want to report. Valid values are **All** (both desktop and portable computers), **Desktop** (desktop computers only), and **Laptop** (portable computers only). These values are only returned for the chosen reporting period. |

#### Hidden report parameters

The following hidden parameters can optionally be specified to change the behavior of this report.

| Parameter Name | Description |
| --- | --- |
| **Desktop computer on** | Specify the power consumption of a desktop computer when it is turned on. The default value is **0.07** kW per hour. |
| **Laptop computer on** | Specify the power consumption of a portable computer when it is turned on. The default value is **0.02** kW per hour. |
| **Desktop computer sleep** | Specify the power consumption of a desktop computer that has entered sleep. The default value is **0.003** kW per hour. |
| **Laptop computer sleep** | Specify the power consumption of a portable computer that has entered sleep. The default value is **0.001** kW per hour. |
| **Desktop computer off** | Specify the power consumption of a desktop computer when it is turned off. The default value is **0** kW per hour. |
| **Laptop computer off** | Specify the power consumption of a portable computer when it is turned off. The default value is **0** kW per hour. |
| **Desktop monitor on** | Specify the power consumption of a desktop computer monitor when it is turned on. The default value is **0.028** kW per hour. |
| **Laptop monitor on** | Specify the power consumption of a portable computer monitor when it is turned on. The default value is **0** kW per hour. |
| **Currency** | Specify the currency label to use for this report. The default value is **USD ($)**. |

#### Report links

This report does not link to any other power management reports.

### Energy Cost by Day report

The **Energy Cost by Day** report displays the following information:

- A graph showing the total daily power cost for computers in the specified collection for the last 31 days.
- A graph showing the average daily power cost for each computer in the specified collection for the last 31 days.
- A table showing the total daily power cost and the average daily power cost for computers in the specified collection for the last 31 days.

    This information can be used to help you to understand power cost trends in your environment. After applying a power plan to computers in the selected collection, the power cost for computers should decrease.

    Use the following parameters to configure this report.

#### Required report parameters

The following parameters must be specified to run this report.

| Parameter Name | Description |
| --- | --- |
| **Collection name** | From the drop-down list, select a collection to use for this report. |
| **Device type** | From the drop-down list, select the type of computer you want to report about. Valid values are **All** (both desktop and portable computers), **Desktop** (desktop computers only), and **Laptop** (portable computers only). These values are only returned for the chosen reporting period. |
| **Cost of KwH** | Specify the cost per kWh of electricity. The default value is **0.09**. You can modify the unit of currency used by this report in the hidden parameters section. |

#### Hidden report parameters

The following hidden parameters can optionally be specified to change the behavior of this report.

| Parameter Name | Description |
| --- | --- |
| **Desktop computer on** | Specify the power consumption of a desktop computer when it is turned on. The default value is **0.07** kW per hour. |
| **Laptop computer on** | Specify the power consumption of a portable computer when it is turned on. The default value is **0.02** kW per hour. |
| **Desktop computer sleep** | Specify the power consumption of a desktop computer that has entered sleep. The default value is **0.003** kW per hour. |
| **Laptop computer sleep** | Specify the power consumption of a portable computer that has entered sleep. The default value is **0.001** kW per hour. |
| **Desktop computer off** | Specify the power consumption of a desktop computer when it is turned off. The default value is **0** kW per hour. |
| **Laptop computer off** | Specify the power consumption of a portable computer when it is turned off. The default value is **0** kW per hour. |
| **Desktop monitor on** | Specify the power consumption of a desktop computer monitor when it is turned on. The default value is **0.028** kW per hour. |
| **Laptop monitor on** | Specify the power consumption of a portable computer monitor when it is turned on. The default value is **0** kW per hour. |
| **Currency** | Specify the currency label to use for this report. The default value is **USD ($)**. |

#### Report links

This report does not link to any other power management reports.

### Environmental Impact report

The **Environmental Impact** report displays the following information:

- A graph showing the total monthly CO2 generated (in tons) for computers in the specified collection for the specified time period.
- A graph showing the average monthly CO2 generated (in tons) for each computer in the specified collection for the specified time period.
- A table showing the total monthly CO2 generated and the average monthly CO2 generated for computers in the specified collection for specified time period.

    The **Environmental Impact** report calculates the amount of CO2 generated (in tons) by using the time that a computer or monitor was turned on in a 24 hour period.

    Use the following parameters to configure this report.

#### Required report parameters

The following parameters must be specified to run this report.

| Parameter Name | Description |
| --- | --- |
| **Report start date** | From the drop-down list, select a start date for this report. |
| **Report end date** | From the drop-down list, select an end date for this report. |
| **Collection name** | From the drop-down list, select a collection for this report. |
| **Device type** | From the drop-down list, select the type of computer for which you want a report. Valid values are **All** (both desktop and portable computers), **Desktop** (desktop computers only), and **Laptop** (portable computers only). These values are only returned for the chosen reporting period. |

#### Hidden report parameters

The following hidden parameters can optionally be specified to change the behavior of this report.

| Parameter Name | Description |
| --- | --- |
| **Desktop computer on** | Specify the power consumption of a desktop computer when it is turned on. The default value is **0.07** kW per hour. |
| **Laptop computer on** | Specify the power consumption of a portable computer when it is turned on. The default value is **0.02** kW per hour. |
| **Desktop computer sleep** | Specify the power consumption of a desktop computer that has entered sleep. The default value is **0.003** kW per hour. |
| **Laptop computer sleep** | Specify the power consumption of a portable computer that has entered sleep. The default value is **0.001** kW per hour. |
| **Desktop computer off** | Specify the power consumption of a desktop computer when it is turned off. The default value is **0** kW per hour. |
| **Laptop computer off** | Specify the power consumption of a portable computer when it is turned off. The default value is **0** kW per hour. |
| **Desktop monitor on** | Specify the power consumption of a desktop computer monitor when it is turned on. The default value is **0.028** kW per hour. |
| **Laptop monitor on** | Specify the power consumption of a portable computer monitor when it is turned on. The default value is **0** kW per hour. |
| **Carbon Factor (tons/kWh)** (CO2Mix) | Specify the value for carbon factor (in tons/kWh) that you typically can obtain from your power company. The default value is **0.0015** tons per kWh. |

#### Report links

This report does not link to any other power management reports.

### Environmental Impact by Day report

The **Environmental Impact by Day** report displays the following information:

- A graph showing the total daily CO2 generated (in tons) for computers in the specified collection for the last 31 days.
- A graph showing the average daily CO2 generated (in tons) for each computer in the specified collection for the last 31 days.
- A table showing the total daily CO2 generated and the average daily CO2 generated for computers in the specified collection for the last 31 days.

    The **Environmental Impact by Day** report calculates the amount of CO2 generated (in tons) by using the time that a computer or monitor was turned on in a 24 hour period.

#### Required report parameters

The following parameters must be specified to run this report.

| Parameter Name | Description |
| --- | --- |
| **Collection name** | From the drop-down list, select a collection for this report. |
| **Device type** | From the drop-down list, select the type of computer you want to report about. Valid values are **All** (both desktop and portable computers), **Desktop** (desktop computers only), and **Laptop** (portable computers only). These values are only returned for the chosen reporting period. |

#### Hidden report parameters

The following hidden parameters can optionally be specified to change the behavior of this report.

| Parameter Name | Description |
| --- | --- |
| **Desktop computer on** | Specify the power consumption of a desktop computer when it is turned on. The default value is **0.07** kWh. |
| **Laptop computer on** | Specify the power consumption of a portable computer when it is turned on. The default value is **0.02** kWh. |
| **Desktop computer off** | Specify the power consumption of a desktop computer when it is turned off. The default value is **0** kWh. |
| **Laptop computer off** | Specify the power consumption of a portable computer when it is turned off. The default value is **0** kWh. |
| **Desktop computer sleep** | Specify the power consumption of a desktop computer that has entered sleep. The default value is **0.003** kWh. |
| **Laptop computer sleep** | Specify the power consumption of a portable computer has entered sleep. The default value is **0.001** kWh. |
| **Desktop monitor on** | Specify the power consumption of a desktop computer monitor when it is turned on. The default value is **0.028** kWh. |
| **Laptop monitor on** | Specify the power consumption of a portable computer monitor when it is turned on. The default value is **0** kWh. |
| **Carbon Factor (tons/kWh)** (CO2Mix) | Specify a value for the carbon factor (in tons/kWh) that you typically can obtain from your power company. The default value is **0.0015** tons per kWh. |

#### Report links

This report does not link to any other power management reports.

### Insomnia Computer Details report

The **Insomnia Computer Details** report displays a list of computers that did not sleep or hibernate for a specific reason within a specified time period. This report is called by the **Insomnia Report** and is not designed to be run directly by the site administrator.

The **Insomnia Report** displays computers as **Not sleep capable** when they are not capable of sleep and have been turned on during the entire specified report interval. The report displays computers as **Not hibernate capable** when they are not capable of hibernate and have been turned on during the entire specified report interval.

Note

Power management can only collect causes that prevented computers from entering sleep or hibernate from computers running Windows 7 or Windows Server 2008 R2.

Use the following parameters to configure this report.

#### Required report parameters

The following parameters must be specified to run this report.

| Parameter Name | Description |
| --- | --- |
| **Collection name** | From the drop-down list, select a collection to use for this report. |
| **Report interval (days)** | Specify the number of days to report. The default value is **7** days. |
| **Cause of Insomnia** | From the drop-down list, select one of the causes that can prevent computers from entering sleep or hibernate. |

#### Hidden report parameters

This report has no hidden parameters that you can set.

#### Report links

This report contains links to the following report which provides further information about the selected item.

| Report Name | Details |
| --- | --- |
| **Computer Details** | Click the **Click for detailed information** link to see the power capabilities, power settings, and applied power plans for the selected computer. For more information, see Computer Details Report in this topic. |

### Insomnia report

The **Insomnia Report** displays a list of common causes that prevented computers from entering sleep or hibernate and the number of computers affected by each cause for a specified time period. There are a number of causes that might prevent a computer from entering sleep or hibernate such as a process running on the computer, an open Remote Desktop session, or that the computer is incapable of sleep or hibernate. From this report, you can open the **Insomnia Computer Details** report which displays a list of computers affected by each cause of computers not sleeping or hibernating.

The Power Insomnia report displays computers as **Not sleep capable** when they are not capable of sleep and have been turned on during the entire specified report interval. The report displays computers as **Not hibernate capable** when they are not capable of hibernate and have been turned on during the entire specified report interval.

Note

Power management can only collect causes that prevented computers from entering sleep or hibernate from computers running Windows 7 or Windows Server 2008 R2.

Use the following parameters to configure this report.

#### Required report parameters

The following parameters must be specified to run this report.

| Parameter Name | Description |
| --- | --- |
| **Collection name** | From the drop-down list, select a collection to use for this report. |
| **Report interval (days)** | Specify the number of days to report. The default value is **7** days. The maximum value is **365** days. Specify **0** to run the report for today. |

#### Hidden report parameters

This report has no hidden parameters that you can set.

#### Report links

This report contains links to the following report which provides further information about the selected item.

| Report Name | Details |
| --- | --- |
| **Insomnia Computer Details** | Click a number in the **Affected Computers** column to see a list of computers that could not sleep or hibernate because of the selected cause. For more information, see Insomnia Computer Details Report in this topic. |

### Power Capabilities report

The **Power Capabilities** report displays the power management hardware capabilities of computers in the specified collection. This report is typically used in the monitoring phase of power management to determine the power management capabilities of computers in your organization. The information displayed in the report can then be used to create collections of computers to apply power plans to, or to exclude from power management. The power management capabilities displayed by this report are:

- **Sleep Capable** - Indicates whether the computer has the capability to enter sleep if it is configured to do so.
- **Hibernate Capable** – Indicates whether the computer can enter hibernate if it is configured to do so.
- **Wake from Sleep** – Indicates whether the computer can wake from sleep if it is configured to do so.
- **Wake from Hibernate** – Indicates whether the computer can wake from hibernate if it is configured to do so.

    The values reported by the **Power Capabilities** report indicate the sleep and hibernate capabilities of computers as reported by Windows. However, the reported values do not reflect cases where Windows or BIOS settings prevent these functions from working.

    Use the following parameters to configure this report.

#### Required report parameters

The following parameters must be specified to run this report.

| Parameter Name | Description |
| --- | --- |
| **Collection** | From the drop-down list, select a collection for this report. |
| **Display Filter** | From the drop-down list, select **Not Supported** to display only computers in the specified collection that are incapable of sleep, hibernate, wake from sleep, or wake from hibernate. Select **Show All** to display all computers in the specified collection. |

#### Hidden report parameters

This report has no hidden parameters that you can set.

#### Report links

This report contains links to the following report which provides further information about the selected item.

| Report Name | Details |
| --- | --- |
| **Computer Details** | Click a computer name to see the power capabilities, power settings, and applied power plans for the selected computer. For more information, see Computer Details Report in this topic. |

### Power Settings report

The **Power Settings** report displays an aggregated list of power settings used by computers in the specified collection. For each power setting, the possible power modes, values, and units are displayed, together with a count of the number of computers that use those values. This report can be used during the monitoring phase of power management to help the administrator understand the existing power settings used by computers in the site and to help plan optimal power settings to be applied by using a power management plan. The report is also useful when troubleshooting to validate that power settings were correctly applied.

Note

The settings displayed are collected from client computers during hardware inventory. Depending on the time at which hardware inventory runs, settings from applied peak or non-peak power plans might be collected.

Use the following parameters to configure this report.

#### Required report parameters

The following parameters must be specified to run this report.

| Parameter Name | Description |
| --- | --- |
| **Collection name** | From the drop-down list, select a collection for this report. |

#### Hidden report parameters

The following hidden parameters can optionally be specified to change the behavior of this report.

| Parameter Name | Description |
| --- | --- |
| **numberOfLocalizations** | Specify the number of languages in which you want to view power setting names reported by client computers. If you only want to view the most popular language, leave this setting at the default of **1**. To view all languages, set this value to **0**. |

#### Report links

This report contains links to the following report which provides further information about the selected item.

| Report Name | Details |
| --- | --- |
| **Power Settings Details** | Click the number of computers in the **Computers** column to see a list of all computers that use the power settings in that row. For more information, see Power Settings Details Report in this topic. |

### Power Settings Details report

The **Power Settings Details** report displays further information about computers selected in the **Power Settings** report. This report is called by the **Power Settings** report and is not designed to be run directly by the site administrator.

#### Required report parameters

The following parameters must be specified to run this report.

| Parameter Name | Description |
| --- | --- |
| **Collection** | From the drop-down list, select a collection to use for this report. |
| **Power Setting GUID** | From the drop-down list, select the power setting GUID on which you want to report. For a list of all power settings and their uses, see [Available power management plan settings](create-and-apply-power-plans#BKMK_Plans) in the topic [How to create and apply power plans](create-and-apply-power-plans). |
| **Power Mode** | From the drop down list, select the type of power settings you want to display in the report results. Select **Plugged In** to view the power settings configured for when the computer is plugged in and **On Battery** to view the power settings configured for when the computer is running on battery power. |
| **Setting Index** | From the drop-down list, select the value for the selected power setting name on which you want to report. For example, if you want to display all computers with the **turn off hard disk after** setting set to **10** minutes, select **turn off hard disk after** for **Power Setting Name** and **10** for **Setting Index**. |

#### Hidden report parameters

The following hidden parameters can optionally be specified to change the behavior of this report.

| Parameter Name | Description |
| --- | --- |
| **numberOfLocalizations** | Specify the number of languages in which you want to view power setting names reported by client computers. If you only want to view the most popular language, leave this setting at the default of **1**. To view all languages, set this value to **0**. |

#### Report links

This report contains links to the following report which provides further information about the selected item.

| Report Name | Details |
| --- | --- |
| **Computer Details** | Click a computer name to see the power capabilities, power settings, and applied power plans for the selected computer. For more information, see Computer Details Report in this topic. |