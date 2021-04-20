### Chrome API's
Dont forget to define the Chrome API in permissions. 

#### Chrome Storage API ([chrome.storage](https://developer.chrome.com/docs/extensions/reference/storage/))
- Used to store, retrieve and track changes to user data.  
- To store data, you can either use storage.sync or storage.local. 
  - The storage.sync option will store the data and if sync is enabled, will update across any Chrome browser that the user is logged into (i.e. iphone application, chrome browser). 
  - The storage.local only stores the data locally.  
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
