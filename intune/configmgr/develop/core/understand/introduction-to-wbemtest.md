---
layout: Conceptual
title: Introduction to WBEMTEST - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/introduction-to-wbemtest
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
description: Learn how to use WBEMTEST, a useful tool for working with WMI/WBEM immediately available on most systems.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: c74e0bc9-47ce-6e46-7fd8-2aca3c6b2b4d
document_version_independent_id: 0200dca2-e58c-7d8a-0436-4622b60d3d73
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/introduction-to-wbemtest.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/introduction-to-wbemtest
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/introduction-to-wbemtest.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: afe54d5a-19a3-1a87-aea6-0f6f4a9bf5ef
---

# Introduction to WBEMTEST - Configuration Manager | Microsoft Learn

If you spend much time around Configuration Manager, you become aware that much of it runs through WMI. WMI is "Windows Management Instrumentation" and is Microsoft's implementation of an Internet standard called Web Based Enterprise Management (WBEM).

As you dig further into Configuration Manager - perhaps doing task sequences and wanting to provide intelligent branching, digging into hardware inventory to possibly extend it, or working with the Configuration Manger SDK – you'll need to dig deeper in to WMI/WBEM. One useful tool for working with WMI/WBEM is WBEMTEST. There are many WMI tools out there. However, WBEMTEST is immediately available on most systems, rather than having to be downloaded first. You might think of it like Notepad.exe – there are text editors with richer capabilities available, but Notepad.exe is always there when you need to view or create a text file.

## Opening WBEMTEST

WBEMTEST is available on any Windows system. Go to Start and type "WBEMTEST" into the search or run box.

When you launch WBEMTEST, different operating system will work slightly differently. Some will automatically connect to a WMI namespace, others (like Windows 7) won't. If you aren't connected automatically to a WMI namespace, you can hit the connect button, make sure that "root\cimv2" is selected, then hit connect again. Now you're back in the main user interface with everything available (when not connected, most buttons are grayed out). You can think of a WMI namespace as similar to a directory within WMI. You can navigate to other WMI namespaces, just like you might change directories on the file system. ROOT\CIMV2 is a WMI namespace where much hardware information is kept – a good starting point.

Important

One limitation of WBEMTEST, is that it doesn't browse the WMI namespaces – you need to know where you're going to connect. ROOT\CIMV2 (all Windows systems), ROOT\CCM (Configuration Manager clients) and ROOT\SMS\site\_&lt;site code&gt; (Configuration Manager site server) are some useful starting points.

ROOT\CIMV2 Namespace

![WBEMTEST CIMV2](media/wbemtestcimv2.jpg)

Configuration Manager Primary Client Namespace

![WBEMTEST CCM](media/wbemtest_ccm.jpg)

Configuration Manager Primary Site Server Namespace (Site Code: ABC)

![WBEMTEST Site](media/wbemtest_site.jpg)

Once you're connected to a WMI namespace, there are many options. If you're already a WMI expert and know what you are after, you could hit the query button and type in a WMI query to look for something specific.

When just starting out, one approach is to explore WMI a bit by browsing the classes in the **ROOT\CIMV2** namespace.

1. Open WBEMTEST.
2. Connect to the **ROOT\CIMV2** namespace.
3. Click the **Enum Classes** button.
4. Select **Recursive** and click **OK**.

    You have just done the equivalent of a `DIR` to list all the contents of the namespace. Everything with underscores (\_*) in the front of the name is WMI overhead - this is what helps WMI be WMI. In most cases you'll skip over everything starting with underscores (\*\_) and look at classes that are specific interest to you.

    A more specific example using `Win32_Service`:
5. Open WBEMTEST.
6. Connect to the **ROOT\CIMV2** namespace.
7. Click the **Enum Classes** button.
8. Select **Recursive** and click **OK**.
9. Browse to **Win32\_Service** and select it by double-clicking.

    You have now opened up the Win32\_Service class in WMI - all of the services on your computer are related to this class. (It gets a little complicated here and the directory analogy breaks down at this point – we'll skip the details and move on to some useful next steps).
10. Click the **Instances** button to see a list of the services available on your computer.
11. Pick a service, such as `RemoteRegistry` and select it by double-clicking.
12. Click the **Show MOF** button.

    Looking at the MOF is a convenient way to look at the information about the RemoteRegistry service- here you can see the service state, description, start mode, etc.

    This was just a starting point to introduce WBEMTEST. Once you're familiar with WBEMTEST, it will become an invaluable tool as you dig into WMI.

### More Resources

**Books:** There are numerous books available for WMI. A few example books are listed below.

- [Developing WMI Solutions: A Guide to Windows Management Instrumentation](https://www.amazon.com/gp/product/0201616130/ref=pd_lpo_k2_dp_sr_1?pf_rd_p=1535523722&amp;pf_rd_s=lpo-top-stripe-1&amp;pf_rd_t=201&amp;pf_rd_i=1578702607&amp;pf_rd_m=ATVPDKIKX0DER&amp;pf_rd_r=05X3A23E6YKTXGZ0P9NZ)
- [Windows Management Instrumentation](https://www.amazon.com/Windows-Management-Instrumentation-Matthew-Lavy/dp/1578702607)
- [Microsoft® Windows® Scripting with WMI: Self-Paced Learning Guide](https://www.amazon.com/Microsoft-Windows-Scripting-WMI-Self-Paced/dp/0735622310/ref=sr_1_5?ie=UTF8&amp;qid=1383150816&amp;sr=8-5&amp;keywords=wmi+books)

    **Videos:** There are numerous videos available for WMI. A few example videos are listed below.
- [YouTube: WMI PowerShell Introduction](https://www.youtube.com/watch?v=5qZfs4j73IQ)
- [YouTube: What is WMI and how to enable remote WMI ?](https://www.youtube.com/watch?v=Nlf3IuTY9wA)

    **Other:** Other resources for WMI are listed below.
- [Windows Management Instrumentation (SDK)](/en-us/windows/win32/wmisdk/wmi-start-page)
- [WMI Scripting Primer: Part 1](/en-us/previous-versions/windows/internet-explorer/ie-developer/scripting-articles/ms974579%28v=msdn.10%29)
- [WMI Scripting Primer: Part 2](/en-us/previous-versions/windows/internet-explorer/ie-developer/scripting-articles/ms974592%28v=msdn.10%29)
- [WMI Scripting Primer: Part 3](/en-us/previous-versions/windows/internet-explorer/ie-developer/scripting-articles/ms974547%28v=msdn.10%29)