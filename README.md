# Personal Chrome Extension Starter Kit

This is a collection of files for rolling out your own custom Chrome browswer extension. These files are super basic intentionally, only meant as a basic setup to get you started with adding HTML and CSS to any site you want in your browser. These are perfect for personal use in your browswer where you can easily tweak styles on any site you choose, helping you alleviate your personal annoyances when visiting those sites where something is just a little off. 

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
This is where you can easily add any styles you want to use on pages you visit in your browser. There is a sample that will turn some of the site's text red, this should be removed and replaced with your own custom styles. Remember if you are using one stylesheet across many sites, you may need to add greater specificity to your selectors to prevent any unwanted side effects of code that is meant for only one site or another. Styles and selectors may be updated any time by the site owners, causing you to need to update your code.



### content.js
Here you can add any JS that you want to execute or add to a page. There is a sample in the file to log a message to the browser console by default, this should be removed so you can add whatever you want to run. 
