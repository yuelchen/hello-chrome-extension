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

