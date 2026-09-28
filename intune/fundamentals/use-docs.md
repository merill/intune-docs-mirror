---
layout: Conceptual
title: How to use Microsoft Intune documentation - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/fundamentals/use-docs
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.collection:
- M365-identity-device-management
ms.subservice: fundamentals
description: Learn how to search, provide feedback about, and contribute to Microsoft Intune product family documentation. This documentation also covers Configuration Manager, Intune, Endpoint analytics, and Windows Autopilot.
ms.date: 2025-04-10T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: bf5143cd-62b8-fd00-23d9-b0dead6231d0
document_version_independent_id: bf5143cd-62b8-fd00-23d9-b0dead6231d0
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/fundamentals/use-docs.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../configmgr/core/toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: fundamentals/use-docs
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/fundamentals/use-docs.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/12ed19f9-ebdf-4c8a-8bcd-7a681836774d
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3a764584-4f97-452b-8f1d-36f19b12f6ae
platformId: ba90fc99-143f-eb0a-c782-5258e536f6d5
---

# How to use Microsoft Intune documentation - Microsoft Intune | Microsoft Learn

This article provides resources and tips for using the Microsoft Intune product family documentation library. It applies to Configuration Manager, Microsoft Intune, Endpoint analytics, and Windows Autopilot, and covers the following areas:

- How to search
- Submitting doc bugs, enhancements, questions, and new ideas
- How to get notified of changes
- How to contribute to documentation on Microsoft Learn

For general help and support, see:

- [Find help for Configuration Manager](../configmgr/core/understand/find-help)
- [Get support in Microsoft Intune](it-pro-support/get-support-admin-center)

Tip

Also visit the **Documentation** node in the **Community** workspace of the Configuration Manager console. This node includes up-to-date information about Configuration Manager documentation and support articles. For more information, see [Using the Configuration Manager console](../configmgr/core/servers/manage/admin-console#bkmk_doc-dashboard).

Information in this article also applies to the [Configuration Manager PowerShell documentation](/en-us/powershell/sccm/overview) in the [sccm-docs-powershell-ref repository](https://github.com/MicrosoftDocs/sccm-docs-powershell-ref).

## Search

Use the following search tips to help you find the information that you need:

- When using your preferred search engine to locate content, include a keyword along with your search keywords. For example, `ConfigMgr` for Configuration Manager and `Intune` for Intune.

    - Look for results from `learn.microsoft.com/mem`. Results from `learn.microsoft.com/previous-versions`, `technet.microsoft.com`, or `msdn.microsoft.com` are for older product versions.
    - To further focus the search results to the current content library, include `site:learn.microsoft.com` in your query to scope the search engine.
- Use search terms that match terminology in the user interface and online documentation. Avoid unofficial terms or abbreviations that you might see in community content. For example, search for:

    - "management point" rather than "MP"
    - "deployment type" rather than "DT"
    - "Intune management extension" rather than "IME"
- To search within the current article, use your browser's **Find** feature. With most modern web browsers, press **Ctrl**+**F** and then enter your search terms.
- Each article on `learn.microsoft.com` includes the following fields to assist with searching the content:

    - **Search** in the upper right corner. To search all articles, enter terms in this field. Articles in this content library automatically include one of the following search scopes: `ConfigMgr`, `Intune`, or `Autopilot`.

        ![Docs search field in header.](media/use-docs/docs-search-field.png)
    - **Filter by title** above the left table of contents. To search the current table of contents, enter terms in this field. This field only matches terms that appear in the article titles for the current node. For example, **Configuration Manager Core Infrastructure** (`learn.microsoft.com/mem/configmgr/core`) or **Intune Apps** (`https://learn.microsoft.com/mem/intune/apps/`). The last item in the search results gives you the option to search for the terms in the entire content library.

        ![Animation of using the table of contents filter.](media/use-docs/docs-filter-toc.gif)

Having problems finding something? File feedback! When you file an issue about search results, provide the search engine you're using, the keywords you tried, and the target article. This feedback helps Microsoft optimize the content for better search.

### Add a custom search engine

With many modern web browsers, you can create a custom search engine. Use this feature to quickly and easily search `learn.microsoft.com`. For example, with Microsoft Edge, version 77 and later, use the following process:

1. In Microsoft Edge, version 77 and later, open **Settings**.
2. In the left menu, select **Privacy, search, and services**.
3. Scroll to the bottom of the **Services** group and select **Address bar and search**.
4. Select **Manage search engines**.
5. Select **Add** and specify the following information:

    - **Search engine**: Enter a friendly name to identify it in the list of search engines. For example, `Microsoft Learn`.
    - **Keyword**: Specify a short term to use in the address bar to activate this search engine. For example, `memdocs`.
    - **URL with `%s` in place of query**: For example,

        ```https
        https://learn.microsoft.com/search/index?search=%s&scope=ConfigMgr
        ```

        Note

        This example is specific to the `ConfigMgr` scope. You can remove the scope variable to search all `learn.microsoft.com` or use a different scope.

        The Microsoft technical documentation search engine requires a locale in the address. For example, `en-us`. You can change your entry to use a different locale.

    ![Add to Microsoft Edge a custom search engine for Microsoft technical documentation.](media/use-docs/docs-search-engine.png)

After you add this search engine, type your keyword in the browser address bar, press `Tab`, then type your search terms, and press `Enter`. It will automatically search Microsoft technical documentation for your specified terms using the defined scope.

## About feedback

Select the **Feedback** link in the upper right of any article or go to the Feedback section at the bottom.

![Screenshot of the feedback section of a Microsoft Learn article.](media/use-docs/docs-feedback.png)

### Types of feedback

- Product feedback for [Configuration Manager](../configmgr/core/understand/product-feedback) or [Intune](https://feedbackportal.microsoft.com/feedback/forum/ef1d6d38-fd1b-ec11-b6e7-0022481f8472)
- [Product questions](/en-us/answers/products/enterprise-mobility-security)
- Support requests for [Configuration Manager](https://aka.ms/cmcbsupport) or [Microsoft Intune](it-pro-support/get-support-admin-center)

## Notifications

To receive notifications when content changes in the documentation library, use the following steps:

1. Use the [docs search](/en-us/search/) to find an article or set of articles.

    - Search for a single article by title, such as [What's new in Microsoft Intune](/en-us/search/?scope=Intune&amp;terms=%22What%27s%20new%20in%20microsoft%20intune%22%2B%22learn%20what%27s%20new).

        Tip

        To refine the search to a single article, use the full title that displays in the Microsoft technical documentation search results. You can also use a string from the first paragraph, as shown in this example.

        This example results in the following RSS link:

        ```https
        https://learn.microsoft.com/api/search/rss?search=%22What%27s+new+in+microsoft+intune%22%2B%22learn+what%27s+new%22&locale=en-us&facet=&%24filter=scopes%2Fany%28t%3A+t+eq+%27Intune%27%29
        ```

        Note

        The above RSS feed URL example includes the `&locale=en-us` variable. The `locale` variable is required, but you can change it to another supported locale. For example, `&locale=ja-jp`.
    - Search for any Configuration Manager article about [BitLocker](/en-us/search/?search=BitLocker&amp;scope=ConfigMgr)

    Note

    Use other keywords or the Microsoft Learn search filters to further refine your search query.
2. At the bottom of the list of results, select the **RSS** link.

    ![Screenshot of search results and RSS link.](media/use-docs/docs-search-rss.png)
3. Use this feed in an RSS application to receive notifications when there's a change to any of the search results. Refer to the RSS application's documentation on how to configure and tune it.

Tip

You can also **Watch** the [MEMDocs repository](https://github.com/MicrosoftDocs/memdocs) on GitHub. This method can generate *many* notifications. It also doesn't include changes from the private repository that Microsoft uses.

## Contribute

The Microsoft Intune product family documentation library, like most Microsoft technical documentation, is open-sourced on GitHub. This library accepts and encourages community contributions. For more information on how to get started, see our [contributor guide](/en-us/contribute/). The only prerequisite is to create a [GitHub account](https://github.com/join).

### Basic steps to contribute

1. From the target article, select **Edit** in the upper right corner. This action opens the source file in GitHub.
2. To edit the source file, select the pencil icon.

    ![Screenshot of GitHub source file header.](media/use-docs/docs-github-edit.png)
3. Make changes in the markdown source. For more information, see [How to use Markdown in Microsoft Learn articles](/en-us/contribute/markdown-reference).
4. In the Propose file change section, enter the public commit comment describing *what* you changed. Then select **Propose file change**.
5. Scroll down and verify the changes you made. Select **Create pull request** to open the form. Describe *why* you made this change. Select **Create pull request**.

The writing team receives your pull request, and assigns it to the appropriate writer. The author reviews the text, and does a quick edit pass on it. They'll either approve and merge the changes, or contact you for more information about the update.

### What to contribute

If you want to contribute, but don't know where to start, see the following suggestions:

- Review an article for accuracy. Then update the **ms.date** metadata using `mm/dd/yyyy` format. This contribution helps keep the content fresh.
- Add clarifications, examples, or guidance based on your experience. This contribution uses the power of the community to share knowledge.

Note

Large contributions require signing a Contribution License Agreement (CLA) if you aren't a Microsoft employee. GitHub automatically requires you to sign this agreement when a contribution meets the threshold. You only need to sign this agreement once.

### Contribution tips

Follow these general guidelines when you contribute:

- Don't surprise us with large pull requests. Instead, file an issue and start a discussion. Then we can agree on a direction before you invest a large amount of time.
- Read the [Microsoft style guide](/en-us/style-guide/welcome/). Know the [Top 10 tips for Microsoft style and voice](/en-us/style-guide/top-10-tips-style-voice).
- Follow the [GitHub Flow workflow](https://guides.github.com/introduction/flow/).
- Blog and tweet (or whatever) about your contributions, frequently!

(This list was borrowed from the [.NET contributing guide](/en-us/contribute/content/dotnet/dotnet-contribute).)