Babolat bags Developer's Guide (Dev. Edition)
================
1. treasure bag outlined pea pods
----------

* Babolat bag is a new extension mechanism that can quickly help developers simple, automatic, batch-oriented station access to the contents of each pea pod Windows version.
* For developers, this is a healthy ecosystem, with millions of users pea pod will provide developers with free promotional platform.
* Here, developers do not need to worry about how to find the user, how to optimize SEO, how to brand promotion, Babolat bags open platform will give developers bring web traffic, downloads, number of users, activity, brand reputation.
* If you're a developer, you are welcome to join the group pea pods Developer:250241844 (please indicate the time of application developers who own identity Ha)

2. Expansion System Development Description (developer Read)
----------

   Each expansion station corresponds to a content. 
   Expand the system so that developers have the ability to quickly and show a lot of content to provide for pea pods.

### 2.1 Developer Documentation Project
* MicroData Description: Documents "[MicroData]"
* Manifest.json Description: Documents "[manifest files]"
* Download Description: Documents "[Download Link]"

### 2.2 is currently expanding webkit/css support features (Universal)
* "[Wandoujia Supported Specifications]"
* Starting from version 2.20 pea pods, support [Android Intent API]
* Starting from version 2.20 pea pods, support Web Fonts
* Starting from version 2.20 pea pods, support Alipay
* Starting from version 2.24 pea pods, support extracting zip package, please see [Zipped Data Download Spec]
* Starting from version 2.33 pea pods, supported determine whether a particular app installed on your phone, detailed documentation to participate in "[manifest files]" section in android_apps
* Starting from version 2.33 pea pods, support access to the phone hardware information, detailed documentation to participate in "[manifest files]" section in privacy_permissions

### 2.3 when developing extensions system
Guideline Content Script

* Modified to adapt to the default page width width pea pods: 780px (considering there is a scroll bar, the proposed control within 760px)

* Please use your work email account and then submit registration pea pod extension

* New extension has been allowed to tamper with other developers to develop the online extension

* New extension does not allow cottage or fully extend existing online plagiarism

* The main content of the page can be called pea pod Download API (downloadable resources should follow the format defined in the microdata, or can not download) to download, do not support the part should open an external browser (target = "_default") or be hide

* If it is difficult to hide inbound links, directly open an external browser (target = "_default")

* Manifest in the fields : name, description of user-visible content, you must have a complete copy description

* The principle of respect for the original content page extension station page structure, which includes the original content of this station login, advertising, share, etc., to decide the fate of these elements by the developer in the development process, but if you leave the need to ensure that it can properly work in pea pods

* Manifest.json matching rules prohibit the use http://\*/\*

* Expansion Pack must contain 72 * 72 icons, observe manifest in the "treasure bag expansion icon norms”：[manifest files]

* Expansion pack file format must be UTF-8 encoding(no BOM)

* Task Manager does not allow the task name "Unnamed name" or garbled characters download

* If the extension is related to dynamic data, the data must be real data, not with false data

* If there are special circumstances to jump to a non-content page, you can retreat back

* Surfaced layer within the page, not special treatment

* The main types of content-type of (a special type of format requires a special agreement):

    * Type of APK: application
    * Type of Zip: application/zip
    * Type of image : image
    * Type of video : video
    * Type of Audio : audio
    * Type of book : book
    * Other file types : file

3. Babolat bags Extended Sample
---------

### 3.1 a treasure bag must contain a manifest.json extension file, the following is an example:


    {
        "name": " Application Search"
        "version": "1.0.0.0",
        "description": "pea pod application search.",
        "content_scripts": [
        {
            "matches":["http://*.wandoujia.com/*", "http://*.wandou.in/*"],
            "run_at": "document_end",
            "js": ["jquery-1.7.min.js", "changeDownload.js"],
            "css": ["contentcss.css"],
            "all_frames":false
        }
        ],
        "icons": {
            "12": "icon12.png",
            "72": "icon72.png"
        },
        "app": {
            "launch": {
                "web_url": "http://apps.wandoujia.com/"
            }
            "navigation": [
            {
                "label": " All Applications "
                "web_url": "http://apps.wandoujia.com/category?id=app"
            }
            {
                "label": " All games "
                "web_url": "http://apps.wandoujia.com/category?id=game"
            }
            {
                "label": " installed the necessary "
                "web_url": "http://apps.wandoujia.com/install"
            }
            {
                "label": "list family "
                "web_url": "http://apps.wandoujia.com/top"
            }
            {
                "label": " pea pod design award "
                "web_url": "http://awardtest.wandoujia.com/p/list"
            }
            ]
        }
        "privacy_permissions": ["device", "social"],
        "android_apps": [{
            "package_name": "com.wandoujia.phoinex2",
            "required": false
        } ]
    }

If manifest.json file used other files, such as *.Js, *.Css, also need to create these files in this directory.
These files can use relative and absolute paths.

In this example the following list of documents :

    manifest.json
    jquery-1.7.min.js
    changeDownload.js
    contentcss.css
    icon16.png
    icon72.png

Download sample package : [sample package]

4 Babolat bags development tools introduced
-----------

### 4.1 prerequisite
Prerequisite for entering the developer version of the account must be registered peas and pea pods in a Windows client login :
![Login pea pods Windows client][register]

### To enter developer mode 4.2
![Enter developer mode ][settings_1]
![Enter developer mode ][settings_2]

### 4.3 Management Extensions
![Enter Management Extensions page][manage]

### 4.4 Load local expansion
![Load local extension ][load_extensions_1]
![Load local extension ][load_extensions_2]
![Load local extension ][load_extensions_3]

### 4.5 Debugging
![Page Debug][debug_1]
![Page Debug][debug_2]

### 4.6 Refresh extension
Click the "Update extensions" to reload the local expansion.
It should be noted that there may need to manually refresh the page.

![Refresh extension][reload_extension]

### 4.7 expansion pack
Click on "Pack Extension", you can immediately generate packaged \*. Wdx file, and it will open the file location .

![Expansion pack][package_extension]

### 4.7 extensions on-line
* Developer extension development is completed, you can submit to the pea pod Addons: http://developer.wandoujia.com/
* Expansion of on-line process is as follows:

![Expansion pack][extension_online]

* Note :

 - After the first expansion pack to submit audit time pea pods are 1 to 3 days , will be on the line day after approval.
 - Expansion pack due to failure (revision, service instability, offline , for legal reasons) or breach of the provisions of pea pods off the assembly line, and then be back to normal expansion pack should be observed for 24 hours, the developer
   Basis having to re-apply on-line process on line.
 - After the developers will expand the package upgrade, you need to re-take the review process.

* Audit and extended downline principles:
 - Expansion of content including pornography, obscenity, walking a fine line, such as adult content
 - Expansion of content or innuendo involving politically sensitive information and content
 - Extension containing the virus
 - Extended Content misleading to deceive the user's behavior or arbitrary deductions, deductions dark
 - Extended serious bug, can not properly use
 - Extended Content Script does not comply with the Guideline pea pod specification
 - Expansion Station revision because of its content, developers offline, legal restrictions as a result of failure
  
  [manifest files]: https://github.com/wandoulabs/developer-documents/blob/master/Doraemon/Manifest%20Files.md
  [Download Link]: https://github.com/wandoulabs/developer-documents/blob/master/Doraemon/Download%20Link.md
  [MicroData]: https://github.com/wandoulabs/developer-documents/blob/master/Microdata/App%20Microdata.md
  [Wandoujia Supported Specifications]: https://github.com/wandoulabs/developer-documents/blob/master/Doraemon/Wandoujia%20Supported%20Specifications.md
  [Android Intent API]: https://github.com/wandoulabs/developer-documents/blob/master/Doraemon/Android%20Intent.md
  [register]: https://github.com/wandoulabs/developer-documents/blob/master/Doraemon/pictures/register.jpg?raw=true
  [settings_1]: https://github.com/wandoulabs/developer-documents/blob/master/Doraemon/pictures/settings_1.jpg?raw=true
  [settings_2]: https://github.com/wandoulabs/developer-documents/blob/master/Doraemon/pictures/settings_2.jpg?raw=true
  [manage]: https://github.com/wandoulabs/developer-documents/blob/master/Doraemon/pictures/manage.jpg?raw=true
  [load_extensions_1]: https://github.com/wandoulabs/developer-documents/blob/master/Doraemon/pictures/load_extensions_1.jpg?raw=true
  [load_extensions_2]: https://github.com/wandoulabs/developer-documents/blob/master/Doraemon/pictures/load_extensions_2.jpg?raw=true
  [load_extensions_3]: https://github.com/wandoulabs/developer-documents/blob/master/Doraemon/pictures/load_extensions_3.jpg?raw=true
  [debug_1]: https://github.com/wandoulabs/developer-documents/blob/master/Doraemon/pictures/debug_1.jpg?raw=true
  [debug_2]: https://github.com/wandoulabs/developer-documents/blob/master/Doraemon/pictures/debug_2.jpg?raw=true
  [reload_extension]: https://github.com/wandoulabs/developer-documents/blob/master/Doraemon/pictures/reload_extension.jpg?raw=true
  [package_extension]: https://github.com/wandoulabs/developer-documents/blob/master/Doraemon/pictures/package_extension.jpg?raw=true
  [extension_online]: https://github.com/wandoulabs/developer-documents/blob/master/Doraemon/pictures/extension_online.jpg?raw=true
  [sample package]: https://github.com/wandoulabs/developer-documents/blob/master/Doraemon/files/search.zip?raw=true
  [Zipped Data Download Spec]:  https://github.com/wandoulabs/developer-documents/blob/master/Doraemon/Zipped%20Data%20Download%20Spec.md
