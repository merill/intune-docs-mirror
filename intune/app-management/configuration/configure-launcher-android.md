---
layout: Conceptual
title: Configure Microsoft Launcher for Android Enterprise With Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/app-management/configuration/configure-launcher-android
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: nicholasswhite
ms.author: nwhite
ms.collection:
- M365-identity-device-management
- Android
ms.subservice: apps
description: Use Intune configuration policies with Microsoft Launcher.
ms.date: 2025-02-24T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: priyar
locale: en-us
document_id: 929f84b0-49a9-05b3-d311-2cb700664cbb
document_version_independent_id: 929f84b0-49a9-05b3-d311-2cb700664cbb
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/app-management/configuration/configure-launcher-android.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: app-management/configuration/configure-launcher-android
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/app-management/configuration/configure-launcher-android.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/12ed19f9-ebdf-4c8a-8bcd-7a681836774d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3a764584-4f97-452b-8f1d-36f19b12f6ae
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: c0f0fd32-c134-be2a-b9a1-36e572c367c0
---

# Configure Microsoft Launcher for Android Enterprise With Intune - Microsoft Intune | Microsoft Learn

Microsoft Launcher is an Android application that lets users personalize their phone, stay organized on the go, and transfer from working from their phone to their PC.

On Android Enterprise fully managed devices, Launcher allows enterprise IT admins to customize managed device home screens by selecting the wallpaper, apps, and icon positions. This standardizes the look and feel of all managed Android devices across different OEM devices and system versions.

## How to configure the Microsoft Launcher app

Once the Microsoft Launcher application has been [added to Intune](../deployment/), navigate to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) and select **Apps** &gt; **Configuration**. Add a configuration policy for **Managed devices** running **Android** and choose **Microsoft Launcher** as the associated app. Click on **Configuration settings** to configure the different available Microsoft Launcher settings.

## Choosing a Configuration Settings Format

There are two methods that you can use to define configuration settings for Microsoft Launcher:

- **Configuration designer** allows you to configure settings with an easy-to-use UI that lets you toggle features on or off and set values. In this method, there are a few disabled configuration keys with value type BundleArray. These configuration keys can only be configured by entering JSON data.
- **JSON data** allows you to define all possible configuration keys using a JSON script.

If you add properties with **Configuration Designer**, you can automatically convert these properties to JSON by selecting **Enter JSON data** from the **Configuration settings format** dropdown list as shown below.

![Configuration settings format - Use configuration designer](media/configure-launcher-android/configure-microsoft-launcher-01.png)

Note

Once properties are configured via the Configuration Designer, the JSON data will also be updated to only reflect these properties. To add additional configuration keys into the JSON Data, use the [JSON script example](configure-launcher-android#microsoft-launcher-configuration-example) to copy the necessary lines for each configuration key.

When editing previously created app configuration policies, if complex properties have been configured, the edit process will display the JSON Data editor. All previously configured settings will be preserved and you can switch to use the configuration designer to modify supported settings.

## Using Configuration Designer

Configuration designer allows you to select pre-populated settings and their associated values.

![Configuration settings format - Enter JSON data](media/configure-launcher-android/configure-microsoft-launcher-02.png)

The following table lists the Microsoft Launcher available configuration keys, value types, default values, and descriptions. The description provides the expected device behavior based on the selected values. Configuration keys that are disabled in Configuration Designer aren't listed in the table.

| Configuration Key | Value type | Default value | Description |
| --- | --- | --- | --- |
| Enrollment Type | String | Default | Allows you to set the enrollment type this policy should apply to. Currently, the value **Default** refers to **CorporateOwnedBusinessOnly**. There are no other supported enrollment types at present. JSON key name: management\_mode\_key |
| Home Screen App Order User Change Allowed | Boolean | True | Allows you to specify if the **Home Screen App Order** setting can be changed by the end user.<br>- If set to **True**, the app order defined in the policy will only be enforced for the initial deployment. Subsequently, the policy won't be enforced to respect any changes the user may have made.<br>- If set to **False**, the app order will be enforced on every sync.<br><br>**Note:** The Home Screen App order can only be configured via the JSON editor.JSON key name:`com.microsoft.launcher.HomeScreen.AppOrder.UserChangeAllowed` |
| Set Grid Size | String | Auto | Allows you to set the grid size for apps to be positioned on the home screen. You can set the number of app rows and columns to define grid size in the following format: `columns;rows`. If you define the grid size, the maximum number of apps that will be shown in a row on the home screen would be the number of rows you set and the maximum number of apps that will be shown in a column in the home screen would be the number of columns you set. JSON key name:`com.microsoft.launcher.HomeScreen.GridSize` |
| Set Device Wallpaper | String | Null | Allows you to set a wallpaper of your choice by entering the URL of the image that you want to set as a wallpaper.JSON key name:`com.microsoft.launcher.Wallpaper.URL` |
| Set Device Wallpaper User Change Allowed | Boolean | True | Allows you to specify if the Set Device Wallpaper setting can be changed by the end user.<br>- If set to **True**, the wallpaper in the policy will only be enforced for the initial deployment. Later, the policy won't be enforced to respect any changes the user may have made.<br>- If set to **False**, the wallpaper will be enforced on every sync.<br><br>JSON key name:`com.microsoft.launcher.Wallpaper.URL.UserChangeAllowed` |
| Feed Enable | Boolean | True | Allows you to enable the launcher feed on the device when the user swipes to the right on the home screen.<br>- If set to **True**, the feed will be enabled.<br>- If set to **False**, the feed will be disabled.<br><br>JSON key name:`com.microsoft.launcher.Feed.Enabled` |
| Feed Enable User Change Allowed | Boolean | True | Allows you to specify if the **Feed Enable** setting can be changed by the end user.<br>- If set to **True**, the feed will only be enforced for the initial deployment. Later, the policy won't be enforced to respect any changes the user may have made.<br>- If set to **False**, the feed will be enforced on every sync.<br><br>JSON key name:`com.microsoft.launcher.Feed.Enabled.UserChangeAllowed` |
| Search Bar Placement | String | Bottom | Allows you to specify the **placement of search bar** on the home screen. <br>- If set to **Bottom**, the search bar will be located on the bottom of the home screen.<br>- If set to **Top**, the search bar will be located on the top of the home screen.<br>- If set to **Hidden**, the search bar will be removed from the home screen.<br><br>JSON key name:`com.microsoft.launcher.Search.SearchBar.Placement` |
| Search Bar Placement User Change Allowed | Boolean | True | Allows you to specify if the **Search Bar Placement** setting can be changed by the end user. <br>- If set to **True**, the search bar placement will only be enforced for the initial deployment. Later, the policy won't be enforced to respect any changes the user may have made.<br>- If set to **False**, the placement of search bar will be enforced on every sync.<br><br>JSON key name:`com.microsoft.launcher.Search.SearchBar.Placement.UserChangeAllowed`<br>**NOTE:** For Microsoft Launcher v 6.2 and later, this setting will no longer be enforced. Therefore, setting this value to `True` will have no effect. Your end users won't be able to customize the location of the search bar placement on their device. |
| Dock Mode | String | Show | Allows you to enable the dock on the device when the user swipes up from the bottom on the home screen.<br>- If set to **Show**, the dock will be enabled.<br>- If set to **Hidden**, the dock will hide from the home screen, but the user can display it when it's needed.<br>- If set to **Disabled**, the dock will be disabled.<br><br>JSON key name:`com.microsoft.launcher.Dock.Mode` |
| Dock Mode User Change Allowed | String | True | Allows you to specify if the Dock Mode setting can be changed by the end user.<br>- If set to **True**, the dock mode setting will only be enforced for the initial deployment. Later, the policy won't be enforced to respect any changes the user may have made.<br>- If set to **False**, the dock mode setting will be enforced on every sync.<br><br>JSON key name:`com.microsoft.launcher.Dock.Mode.UserChangeAllowed` |

## Enter JSON Data

Enter JSON data to configure all available settings for Microsoft Launcher, and the settings disabled in **Configuration Designer**, as shown below.

![Configuration Designer - JSON data](media/configure-launcher-android/configure-microsoft-launcher-03.png)

In addition to the list of configurable settings listed in the Configuration Designer table (above), the following table provides the configuration keys you can only configure via JSON data.

| Configuration Key | Value type | Default value | Description |
| --- | --- | --- | --- |
| Set Allow-Listed ApplicationsJSON key:`com.microsoft.launcher.HomeScreen.Applications` | BundleArray | See: [Set allow-listed applications](configure-launcher-android#set-allow-listed-applications) | Allows you to define the set of apps visible on the home screen from amongst the apps installed on the device. You can define the apps by entering the app package name of the apps that you would like to make visible, for example, `com.android.settings` would make settings accessible on the home screen. The apps that you allow-list in this section should already be installed on the device in order to be visible on the home screen.<br>Properties:<br><br>- **Package:** The application package name<br>- **Class:** The application activity, which is specific to a certain app page. It would use the default app page if this value is empty. |
| Home Screen App OrderJSON key: `com.microsoft.launcher.HomeScreen.AppOrder` | BundleArray | See: [Home screen app order](configure-launcher-android#home-screen-app-order) | Allows you to specify the app order on the home screen.<br>Properties:<br><br>- **Type:** If you want to specify positions of apps, the only type supported is `application`. If you want to specify positions of web links, the type is `weblink`.<br>- **Position:** This specifies application icon slot on home screen. This starts from position 1 on the top left, and goes left to right, top to bottom.<br>- **Package:** This is application package name used for specifying app order.<br>- **Class:** The is an application activity, which is specific to a certain app page. The default app page will be used if this value is empty. This property is used for app.<br>- **Label:** The is an application activity, which is specific to a certain app page. The default app page will be used if this value is empty. This property is used for app.<br>- **Link:** The url to be launched after end user clicks the web link icon. This property is used for web link. |
| Set Pinned Web LinksJSON key: `com.microsoft.launcher.HomeScreen.WebLinks` | BundleArray | N/A | This key allows you to pin website to the home screen as quick launch icon. That way you can make sure that end user can have quick and easy access to essential websites. You can modify location of each web link icon in 'Home Screen App Order' configuration.<br>Properties:<br><br>- **Label:** The weblink title displayed on MS Launcher home screen.<br>- **Link:** The url to be launched after end user clicks the web link icon. |
| Set Folder Icon Shape, Open Format, and Scroll DirectionJSON key: `com.microsoft.launcher.Folder.Style` | BundleArray | N/A | Allows you to define appearance of folder icon and way of opening a folder on the Microsoft Launcher home screen and dock.<br>Properties:<br><br>- **folderShape:** This key can be set as one of the five values: `Rounded_square`, `Square`, `Squircle`, `Round`, and `Teardrop`.<br>- **openFullScreen:** This key can be set as one of the values: `True` or `False`. If it set to `True`, the folder will be opened in the full screen. If it set to `False`, the folder won't be opened in the full screen.<br>- **folderScroll:** This key can be set as one of the values: `vertical` or `horizontal`. The default value is set as `vertical`. |
| Set Folder Icon Shape, Open Format, and Scroll Direction User Change AllowedJSON key: `com.microsoft.launcher.Folder.Style.UserChangeAllowed` | Boolean | True | Allows you to specify if the Folder Style setting can be changed by the end user.<br>- If set to `True`, the shape of folder, the way the folder opens, and the way the folder scrolls as defined in the policy will only be enforced for the initial deployment. Later, the policy won't be enforced to respect any changes the user may have made later.<br>- If set to `False`, the shape of folder, the way the folder opens, and the way the folder scrolls will be enforced on every sync. |

### Set allow-listed applications

```JSON
{
    "key": "com.microsoft.launcher.HomeScreen.Applications",
    "valueBundleArray":
    [
        {
            "managedProperty": [
                {
                    "key": "package",
                    "valueString": "com.android.settings"
                },
                {
                    "key": "class",
                    "valueString": ""
                }
            ]
        }
    ]
}
```

### Home screen app order

```JSON
{
    "key": "com.microsoft.launcher.HomeScreen.AppOrder",
    "valueBundleArray":
    [
        {
            "managedProperty": [
                {
                    "key": "type",
                    "valueString": "application"
                },
                {
                    "key": "position",
                    "valueInteger": 1
                },
                {
                    "key": "package",
                    "valueString": "com.android.settings"
                },
                {
                    "key": "class",
                    "valueString": ""
                }
            ]
        }
    ]
}
```

### Set Pinned Web link

```JSON
{
    "key": "com.microsoft.launcher.HomeScreen.WebLinks",
    "valueBundleArray": [
        {
            "managedProperty": [
                {
                    "key": "label",
                    "valueString": "weblink"
                },
                {
                    "key": "link",
                    "valueString": "https://www.microsoft.com"
                }
            ]
        }
    ]
},
{
    "key": "com.microsoft.launcher.HomeScreen.AppOrder",
    "valueBundleArray": [
        {
            "managedProperty": [
                {
                    "key": "type",
                    "valueString": "weblink"
                },
                {
                    "key": "position",
                    "valueInteger": 2
                },
                {
                    "key": "label",
                    "valueString": "Microsoft"
                },
                {
                    "key": "link",
                    "valueString": "https://www.microsoft.com"
                }
            ]
        }
    ]
}
```

### Microsoft Launcher configuration example

The following is an example JSON script with all the available configuration keys included:

```JSON
{
    "kind": "androidenterprise#managedConfiguration",
    "productId": "app:com.microsoft.launcher",
    "managedProperty": [
        {
            "key": "management_mode_key",
            "valueString": "Default"
        },
        {
            "key": "com.microsoft.launcher.Feed.Enable.UserChangeAllowed",
            "valueBool": false
        },
        {
            "key": "com.microsoft.launcher.Feed.Enable",
            "valueBool": true
        },
        {
            "key": "com.microsoft.launcher.Wallpaper.Url.UserChangeAllowed",
            "valueBool": false
        },
        {
            "key": "com.microsoft.launcher.Wallpaper.Url",
            "valueString": "http://www.contoso.com/wallpaper.png"
        },
        {
            "key": "com.microsoft.launcher.HomeScreen.GridSize",
            "valueString": "5;5"
        },
        {
            "key": "com.microsoft.launcher.HomeScreen.Applications",
            "valueBundleArray": [
                {
                    "managedProperty": [
                        {
                            "key": "package",
                            "valueString": "com.ups.mobile.android"
                        },
                        {
                            "key": "class",
                            "valueString": ""
                        }
                    ]
                },
                {
                    "managedProperty": [
                        {
                            "key": "package",
                            "valueString": "com.microsoft.teams"
                        },
                        {
                            "key": "class",
                            "valueString": ""
                        }
                    ]
                },
                {
                    "managedProperty": [
                        {
                            "key": "package",
                            "valueString": "com.microsoft.bing"
                        },
                        {
                            "key": "class",
                            "valueString": ""
                        }
                    ]
                }
            ]
        },
        {
            "key": "com.microsoft.launcher.HomeScreen.WebLinks",
            "valueBundleArray": [
                {
                    "managedProperty": [
                        {
                            "key": "label",
                            "valueString": "News"
                        },
                        {
                            "key": "link",
                            "valueString": "https://www.contoso.com"
                        }
                    ]
                }
            ]
        },
        {
            "key": "com.microsoft.launcher.HomeScreen.AppOrder.UserChangeAllowed",
            "valueBool": false
        },
        {
            "key": "com.microsoft.launcher.HomeScreen.AppOrder",
            "valueBundleArray": [
                {
                    "managedProperty": [
                        {
                            "key": "type",
                            "valueString": "application"
                        },
                        {
                            "key": "position",
                            "valueInteger": 17
                        },
                        {
                            "key": "package",
                            "valueString": "com.ups.mobile.android"
                        },
                        {
                            "key": "class",
                            "valueString": ""
                        }
                    ]
                },
                {
                    "managedProperty": [
                        {
                            "key": "type",
                            "valueString": "application"
                        },
                        {
                            "key": "position",
                            "valueInteger": 18
                        },
                        {
                            "key": "package",
                            "valueString": "com.microsoft.teams"
                        },
                        {
                            "key": "class",
                            "valueString": ""
                        }
                    ]
                },
                {
                    "managedProperty": [
                        {
                            "key": "type",
                            "valueString": "application"
                        },
                        {
                            "key": "position",
                            "valueInteger": 19
                        },
                        {
                            "key": "package",
                            "valueString": "com.microsoft.bing"
                        },
                        {
                            "key": "class",
                            "valueString": ""
                        }
                    ]
                },
                {
                    "managedProperty": [
                        {
                            "key": "type",
                            "valueString": "weblink"
                        },
                        {
                            "key": "position",
                            "valueInteger": 20
                        },
                        {
                            "key": "label",
                            "valueString": "News"
                        },
                        {
                            "key": "link",
                            "valueString": "https://www.contoso.com"
                        }
                    ]
                }
            ]
        }
    ]
}

```