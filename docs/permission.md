### Security (permission)
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
