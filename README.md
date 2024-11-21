![pcesk-wide](https://github.com/user-attachments/assets/c4f9c7d0-4d11-43f4-812a-da7fa4e0f0ca)

# Personal Chrome Extension Starter Kit

This is a collection of essential files for rolling out your own custom Chrome browser extension. These files are super basic intentionally, only meant as a bare bones setup to get you started with adding HTML and CSS to any site you want in your browser. These are perfect for personal use in your browser where you can easily tweak styles on any site you choose, helping alleviate your personal annoyances when visiting those sites where something is just a little off. 

## Getting Started
Download the files or fork and clone this repo locally to get started. 

## File Customization

### manifest.json
The manifest file defines important settings that Chrome uses to run the extension. The key settings include:

- The extension name ("Custom Injector")
- Version number (1.4)
- Description of what it does
- Which files to inject (content.js and style.css)
- When and where to inject these files (at document start, on all web pages)

It works even in frames embedded within pages (enabled by `"all_frames": true`).

The `"content_scripts"` section is particularly important as it defines what gets injected into web pages and under what conditions. You can add more CSS/JS files that only run on speicic sites by updating your manifest file to follow allong with the example shown here:

```json
"content_scripts": [
  {
    "run_at": "document_end",
    "matches": [
      "https://*.stackexchange.com/*"
    ],
    "js": [
      "my_functions_file_1.js",
      "my_functions_file_2.js"
    ],
    "css": ["style-1.css"]
  },
  {
    "run_at": "document_start",
    "matches": [
      "https://*.stackoverflow.com/*"
    ],
    "js": [
      "my_functions_file_3.js",
      "my_functions_file_4.js"
    ],
    "css": ["style-2.css"]
  }
],
```

### style.css
This is where you can easily add any styles you want to use on pages you visit in your browser. There is a sample that will turn some of the site's text red, this should be removed and replaced with your own custom styles. Remember if you are using one stylesheet across many sites, you may need to add greater specificity to your selectors to prevent any unwanted side effects of code that is meant for only one site or another.



### content.js
Here you can add any JS that you want to execute or add to a page. There is a sample in the file to log a message to the browser console by default, this should be removed so you can add whatever you want to run. 


## Import Extension Into Chrome
1. Open Chrome: Go to chrome://extensions
2. Enable Developer Mode: Toggle the switch in the top right corner
3. Load Unpacked: Click the "Load unpacked" button near the logo in the top left and select the folder for this project

## Update Extension
Once your extension has already been loaded into Chrome, anytime you make local file changes to the folder that Chrome is pointing at, it will show a small update button in the lower right of your extension. 
1. Open Chrome: Go to chrome://extensions
2. Find your extension, will look similar to the image below
3. Press the refresh button in the lower right corner

![image](https://github.com/user-attachments/assets/6d73f78c-e18f-44fd-8c77-5a543f022407)



