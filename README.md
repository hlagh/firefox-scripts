# userChromeJS

#### Tested on Firefox Developer Edition 77.0b8, Windows 10

## Instructions

1. Download [this zip file](https://raw.githubusercontent.com/xiaoxiaoflood/firefox-scripts/master/fx-folder.zip) and extract its content to Firefox installation folder (usually **C:\Program Files\Mozilla Firefox**).

2. Click Firefox menu button (☰) -> *Help* -> *Troubleshooting information* or simply open the address "*about:support*", then click *Open folder*. This is the folder of your Firefox profile. In there, create a new folder called **chrome**.

3. Download one of the files below and extract its content in **chrome** folder.

 - [utils → I'm only interested in scripts](https://raw.githubusercontent.com/xiaoxiaoflood/firefox-scripts/master/utils_scripts_only.zip)

 - [utils → I'm only interested in extensions](https://raw.githubusercontent.com/xiaoxiaoflood/firefox-scripts/master/utils_extensions_only.zip)
 
 - [utils → I'm interested in both scripts and extensions](https://raw.githubusercontent.com/xiaoxiaoflood/firefox-scripts/master/utils.zip)

*Now, if you're only interested in extensions, you can skip to step 6.*

4. Save the desired [userChromeJS scripts](https://github.com/xiaoxiaoflood/firefox-scripts/tree/master/chrome) into **chrome**. Read below the description of some of them.

5. If you want a button to manage your scripts, including the ability to disable/enable scripts without needing to restart Firefox¹, save [rebuild_userChrome.uc.js](https://raw.githubusercontent.com/xiaoxiaoflood/firefox-scripts/master/chrome/rebuild_userChrome.uc.js) into **chrome**.

6. Restart Firefox.

**Important**

In some cases, it may seem that nothing has changed in Firefox. If that happens, it's because Firefox didn't update startup cache, so userChromeJS didn't run. To fix this, reopen your profile folder (see step 2 above), exit Firefox and delete `startupCache` folder. It will be recreated the next time you open Firefox, detecting the scripts that have been added.

¹: Not all scripts are restartless. These have `@shutdown` at the beginning of the code. Almost all scripts on this page were written by me to be restartless, but almost all scripts you get from other sources are not.

## userChromeJS scripts

(click to expand)
<details>
  <summary>Enter Selects</summary>
  Preselects the first suggestion from address bar. For instance, if this page is the first suggestion when you type "xiaoxiaoflood", you don't need to press down arrow key before Enter. This is a workaround for the bad Firefox design choice of autofill domains only.
  
  This script replaces autofill, so `browser.urlbar.autoFill` is disabled on install. If you are typing part of a domain from the start and the first suggestion is from that domain (for instance, *git* from *github.com*), Tab key will autocomplete the domain even if the first suggestion is not the root.
  
  I suggest to set `browser.urlbar.suggest.searches = false` or `browser.urlbar.matchBuckets = general:5` (general:5 means 5 normal suggestions before search suggestions, adjust the value as you wish).

  [Download link](https://raw.githubusercontent.com/xiaoxiaoflood/firefox-scripts/master/chrome/enterSelects.uc.js). 
</details>
<details>
  <summary>Extension Options Menu</summary>
  A single toolbar button to manage all your extensions. It opens a menu listing each extension. Left-click to open Options from the hovered addon, right-click to enable/disable, Ctrl + right-click to uninstall. Hover anywhere on the menu to see more.

  Screenshot:
  
  ![](https://i.imgur.com/FWs3pYl.png)

  [Download link](https://raw.githubusercontent.com/xiaoxiaoflood/firefox-scripts/master/chrome/extensionOptionsMenu.uc.js).
</details>
<details>
  <summary>Master Password+</summary>
  Locks Firefox with password. This will prompt the password on browser startup or anytime when you lock it with Ctrl+Alt+Shift+W.
  
  You need to set a master password in <i>Firefox Options > Privacy & Security > [×] Use a master password</i>.

  [Download link](https://raw.githubusercontent.com/xiaoxiaoflood/firefox-scripts/master/chrome/masterPasswordPlus.uc.js).  

  Locked:
  ![](https://i.imgur.com/cE3sUGT.png)

  Unlocked:
  ![](https://i.imgur.com/KOkEJq5.png)
</details>
<details>
  <summary>multifoxContainer</summary>
  When Firefox introduced containers, I created this script to get some features that I missed from Multifox, the legacy addon that implemented "containers" years before Firefox having this feature by default.
  Since then, Firefox has added some things this script had, so I removed them. But I still use it for two things:
  
  - New tabs (Ctrl+T or New Tab button) inherits the container of current tab (except for Private Tabs).
  
  - The label in urlbar serves as menubutton to reopen current tab in other container. With left click, current tab is replaced. With middleclick, a new tab is opened without closing the other one.
  
  ![](https://i.imgur.com/BE7oPcu.png)

  [Download link](https://raw.githubusercontent.com/xiaoxiaoflood/firefox-scripts/master/chrome/multifoxContainer.uc.js).
</details>
<details>
  <summary>Open in Unloaded Tab</summary>
  Creates an item in contextmenu to open links/bookmarks/history in unloaded tabs, i.e., the tab is created, but it will only load when selected. Just like unloaded tabs when you restore previous session.
 So you can, for example, open multiple related YouTube videos and load them one by one. Or open an entire bookmark folder in tabs without freezing the browser, since tab content will load on demand.

  [Download link](https://raw.githubusercontent.com/xiaoxiaoflood/firefox-scripts/master/chrome/openInUnloadedTab.uc.js).
</details>
<details>
  <summary>PrivateTab</summary>
  Fx 77 blocked the ability to open private tabs in non-private windows, previously possible with Private Tab addon. So I decided to write this script as a replacement. You can change some minor settings at the beginning of the code.

  [Download link](https://raw.githubusercontent.com/xiaoxiaoflood/firefox-scripts/master/chrome/privateTab.uc.js).
</details>
<details>
  <summary>Status Bar</summary>
  Brings back the good old status bar (also known as Addon Bar) at the bottom, with status text plus any buttons you want.

  Screenshots:
  
  ![](https://i.imgur.com/2EBQyjE.png)
  
  ![](https://i.imgur.com/zoX79TT.png)

  [Download link](https://raw.githubusercontent.com/xiaoxiaoflood/firefox-scripts/master/chrome/status-bar.uc.js).
</details>
<details>
  <summary>StyloaiX</summary>
  Basic UserStyle manager with the same power of userChrome.css and userContent.css (can restyle both Firefox windows and websites). It loads <i><u>.css</u></i> files from <i><u>\chrome\UserStyles</u></i>. It supports instant enable/disable per style or global. It also can reload updated styles and load new ones. More features may be added in the future. To reskin websites, <a href="https://addons.mozilla.org/firefox/addon/styl-us/">Stylus</a> is a better option, with more features including autoupdate for styles available on the web. But Stylus can't touch the Firefox interface, only websites.
  
  <b>Note</b>: just like Stylish, UserStyles are loaded by default as AUTHOR_SHEET. If you need AGENT_SHEET or USER_SHEET (for instance, userContent.css is USER_SHEET), save the file as ".as.css" or ".us.css".

  Screenshot (yes, I'm using the old Stylish icon):
  
  ![](https://i.imgur.com/m0EonHK.png)

  [Download link](https://raw.githubusercontent.com/xiaoxiaoflood/firefox-scripts/master/chrome/styloaix.uc.js).
</details>

Bonus: I don't like the new password manager and the old one was removed in Fx 77. I'm still using it. If you want it too, save [these files](https://github.com/xiaoxiaoflood/firefox-scripts/tree/master/chrome/utils/passwordmgr), so that you can access the old password manager using chrome://userchromejs/content/passwordmgr/passwordManager.xhtml (bookmark this URL).

## Screenshots

<img src="https://raw.githubusercontent.com/xiaoxiaoflood/firefox-scripts/master/screenshots/folder.png">

###### userChromeJS Manager (the blue ones are restartless)
<img src="https://raw.githubusercontent.com/xiaoxiaoflood/firefox-scripts/master/screenshots/rebuild_userChrome.png" height="600">

###### Status Bar, Extension Options Menu, MinMaxClose Button, newDownloadPlus.uc.js and legacy extensions:
<img  src="https://raw.githubusercontent.com/xiaoxiaoflood/firefox-scripts/master/screenshots/window.png">
