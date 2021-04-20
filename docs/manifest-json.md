# About manifest.json
This document is to go over the purpose of a manifest.json file. 

### JSON Definition Covered:
```json:
{
  "name" STRING,
  "description" STRING,
  "version" : STRING,
  "manifest_version" : INTEGER,
  "background" : JSONObject,
  "permission" : JSONArray,
  "action" : JSONObject, 
  "icons" : JSONObject,
  "options_page" : STRING
}
```

### The Bare Minimum
There are four fields that are required in a manifest file for installing an extension:
1. Name of the extension. 
2. Description of the extension.
3. The version of the extension. 
4. The manifest version used to define the extension. 

```json:
{
  "name" : "Bee Productive",
  "description" : "A free Chrome extension.",
  "version" : "1.0",
  "manifest_version" : 3
}
```

To install the extension afterwards, follow the below steps:
1. Open Chrome. 
2. Select the extension button (puzzle icon near the top right corner). 
3. Select manage extensions. 
4. Enable developer mode if not already enabled (toggle button near the top right corner). 
5. Select the 'load unpacked' button (button near the top left corner).
6. Open the root folder of your manifest.json file. 

### Security and Defining Chrome API's (permission)
To use Chrome API's in your extension, we need to declare them using the permission field in the manifest file. 
Extensions can request three categories of permission in the manifest file, and they are specified as a list of known Strings. 
1. permission - contains items from a list of known strings (i.e. storage, geolocation). 
2. optional_permission - like regular permission but granted by the user at runtime. 
3. host_permission - contains one or more match patterns to one or more hosts. 

```json:
  "permission" : [ 
    "storage", 
    "activeTab", 
    "scripting" 
  ],
  "optional_permission" : [
    "unlimitedStorage"
  ],
  "host_permission" : [
    "http://google.com/",
    "http://*.google.com/"
  ]
```

The importance of permission cannot be stressed enought as it's what protects your end-users. 
If by some chance your extension becomes compromised, permissions limit the damage that can done as your extension access is limited. 
It is also recommeded to use optional_permissions whenever feasible, as this option provides end-users with informed control over access to data and resource which your extension will access. 

See [Extensions Platform Vision](https://developer.chrome.com/docs/extensions/mv3/intro/platform-vision/#improved-user-visibility-and-control) for more information. 

### Adding Functionality (background)
To add functionality to our extension, we need to use the background field to define the location of our code which will need to run. 
When we define the background task, we are basically informing Chrome how a file should behave, the location and name of the file. 

The below defines a background service worker as a file named background.js:
```json:
  "background" : {
    "service_worker" : "background.js"
  }
```

### Using Chrome API's
Dont forget to define the Chrome API in permissions. 

#### Chrome Storage API ([chrome.storage](https://developer.chrome.com/docs/extensions/reference/storage/))
- Used to store, retrieve and track changes to user data.  
- To store data, you can either use storage.sync or storage.local. The storage.sync option will store the data and if sync is enabled, will update across any Chrome browser that the user is logged into (i.e. iphone application, chrome browser). The storage.local only stores the data locally.  
- Never store confidential (users personal data) using storage API. 

```json:
  "permission" : [ "storage" ]
```

#### Chrome Action API ([chrome.action](https://developer.chrome.com/docs/extensions/reference/action/))
- Used to control extension icon in the Google Chrome toolbar.  
- UI covered by Action API:  
  - Icon 
  - Tooltip (title)  
  - Badge  
  - Popup  
  - Per-tab State  
  - Enabled State  

```json:
  "action": {
    "default_popup": "popup.html",
    "default_icon": {
      "16": "/images/get_started16.png",
      "32": "/images/get_started32.png",
      "48": "/images/get_started48.png",
      "128": "/images/get_started128.png"
    }
  },
  "icons": {
    "16": "/images/get_started16.png",
    "32": "/images/get_started32.png",
    "48": "/images/get_started48.png",
    "128": "/images/get_started128.png"
  }
```
