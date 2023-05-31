---
title: "How to build your first ever chrome extension"
datePublished: Wed May 31 2023 20:22:28 GMT+0000 (Coordinated Universal Time)
cuid: clic5m1rc000f09ld8x5087oh
slug: how-to-build-your-first-ever-chrome-extension
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1685564506168/07a620c6-fa99-4a47-baa9-897245b528a6.jpeg
tags: technology, chrome-extension, social-media

---

In today's blog, I will be showing you guys how to build your first-ever Chrome extension which you can use in your daily life activities. Here we will be building a simple Chrome extension which helps you to **download whatsapp status from WhatsApp web** in just one click.

### First lets learn the basics

To build something you should have a pre-defined folder structure which manages your code and it should be readable so others can also contribute to it. In my case, I kept it as simple as possible.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685561688503/64704391-b8c3-43d9-8add-4372b630deb1.png align="center")

Here you can see I have a `manifest.json` file which is the main entry point for the Chrome extension. All the details regarding your extension like version, name, permissions, and action files everything is defined here.

then we have `background.js` file which runs in the background in a Chrome extension. It can be used to perform tasks that need to be done continuously or at regular intervals. In `manifest.json` file, you declare this file as this

```json
"background": {
    "service_worker": "background.js"
 },
```

Then we have `popup.html` file which is the normal HTML file that is shown when you click the extension button. You can use CSS to make it looks good and add a helper javascript file for more functionalities.

### Build a whatsapp status downloader extension

Now I hope you have a basic understanding of how to build a basic extension. So let's make our hands dirty with some real-life applications. We will be building a Chrome extension which downloads status from WhatsApp web.

For it let's first define the basic configuration in `manifest.json` file.

```json
{
  "manifest_version": 3,
  "name": "whatsapp web status saver",
  "version": "1.01",
  "permissions": [
    "activeTab",
    "scripting"
  ],
  "background": {
    "service_worker": "background.js"
  },
  "action": {
    "default_popup": "popup.html",
    "default_icon": {
      "16": "icons/icon@16.png",
      "48": "icons/icon@48.png",
      "128": "icons/icon@128.png"
    }
  }
}
```

Here I mentioned what will be my extension name, the version of the extension, the permission required to run it, `background.js` file path and the icons path which will be used to display it.

Now let's define the `popup.html` file which will contain the HTML code for the popup which appears when you click the extension button.

```xml
<!DOCTYPE html>
<html>
  <head>
    <title>WhatsApp Status Downloader</title>
    <script src="popup.js"></script>
  </head>
  <body>
    wait for status to load then click on download button!!
    <button id="download-btn">Download Status</button>
  </body>
</html>
```

Next, let's define the `popup.js` file. There we will add a listener to our download button. Whenever that button is clicked it will send a message to Chrome runtime with the <mark>download_status</mark> message for the current tab id.

```javascript

document.addEventListener("DOMContentLoaded", function() {
    const downloadBtn = document.getElementById("download-btn");
    downloadBtn.addEventListener("click", function() {
      chrome.tabs.query({ active: true, currentWindow: true }, function(tabs) {
        chrome.runtime.sendMessage({ message: "download_status", tabId: tabs[0].id });
      });
    });
  });
```

Now let's add a listener for this <mark>download_status</mark> event. We will execute a script whenever we receive this message.

```javascript
chrome.runtime.onMessage.addListener(function(request, sender, sendResponse) {
  if (request.message === "download_status") {
    chrome.scripting.executeScript({
      target: { tabId: request.tabId },
      func: downloadStatus
    });
  }
});
```

As you can see I have added a listener and whenever it captures a request, it checks if `request.message` is the same as "download\_status" or not. If yes, it invokes `downloadStatus` function. So let's define the function also.

```javascript

function downloadStatus() {
const mediaList = document.querySelectorAll("img[src^='blob:'], video[src^='blob:']");
// Check if any media was found
if (mediaList.length === 0) {
  alert("No status media found or please wait until the status is loaded!!");
}
for (let i = 0; i < mediaList.length; i++) {
  const mediaUrl = mediaList[i].src;
  fetch(mediaUrl)
    .then(response => response.blob())
    .then(blob => {
      const url = URL.createObjectURL(blob);
      const link = document.createElement("a");
      link.href = url;
      link.download = `status_${i}.${blob.type.split("/")[1]}`;
      document.body.appendChild(link);
      link.click();
      document.body.removeChild(link);
    })
    .catch(error => console.error(error));
}
}
```

It simply first select all the video and image element present in the current tab. Then first convert it to blob and make it downloadable. If no media file found, it shows an alert. That's it.

Now to test this all you have to do is go to `chrome://extensions/` and enable developer mode. Then upload this folder by clicking the load unpacked button.

Now you should be able to use it. Just open WhatsApp on the web, then go to someone's status and click the extension. You can easily download their status and it will save those files in your local.

If you like to contribute in the code you can do it here on [GitHub](https://github.com/rijusougata13/wa-web-status-downloader). Also if you want to directly try my extension, you can do that also by visiting [here](https://chrome.google.com/webstore/detail/whatsapp-web-status-saver/ndmjmomjcjfencljofkclokaphggfkin?hl=en&authuser=0).

### Conclusion

I hope you have now a pretty much good idea about how to build your own Chrome extension and distribute it to millions of people. I will try to come up with new ideas in the next blog also. If you enjoyed this article you can support me by [**buying me a coffee**](https://www.buymeacoffee.com/rijusougata13) and following me on [**twitter**](https://twitter.com/rijusougata13).