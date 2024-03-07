### Decorative Text

Decorative Text extension is a unique and artistic text transformation extension for Chrome that's designed to elevate your digital expressions. This extension is your go-to tool for converting plain text into an array of decorative ASCII characters, adding a touch of elegance and creativity to your messages, social media posts, or any digital content. With a diverse selection of 10 different styles, Decorative Text offers endless possibilities to personalize and stylize your text, ensuring that your digital presence stands out. Whether you're looking to add sophistication to your documents or flair to your online interactions, this extension empowers you to make a statement that resonates with your unique style.

![decorative text](https://github.com/sourceduty/Extensions/assets/123030236/4bba5187-86f2-44f6-8d8f-5abb32ccb18d)


Copyright (C) 2024, Sourceduty - All Rights Reserved.

***

### Chrome Exit Saver

![Chrome](https://github.com/sourceduty/Extensions/assets/123030236/78b0e140-ce76-417b-840f-c103061fae5a)

This Chrome extension is designed to prevent the accidental closure of the browser when only a single tab is open by prompting the user with a confirmation dialog. The primary goal is to safeguard users from inadvertently losing their work or the context of their current task due to a misclick or habitual closing of the browser. When the user attempts to close the last remaining tab in Chrome, the extension detects this action and displays a standard browser confirmation popup, asking the user to confirm their intention to close the tab. This added step serves as a safety net, ensuring that users have a moment to reconsider their action and potentially avoid the unintended closure of important tabs.

#

manifest.json

```
{
  "manifest_version": 3,
  "name": "Tab Close Confirmation",
  "version": "1.0",
  "description": "Ask for confirmation before closing the last tab in Chrome.",
  "background": {
    "service_worker": "background.js"
  },
  "permissions": [
    "tabs"
  ]
}
```

#

background.js

```
chrome.tabs.onRemoved.addListener(checkLastTab);

async function checkLastTab() {
  let queryOptions = { currentWindow: true };
  let tabs = await chrome.tabs.query(queryOptions);

  if (tabs.length === 1) {
    let confirmClose = confirm("Are you sure you want to close the last tab?");
    if (!confirmClose) {
      // Prevent tab closure (Note: This might not be fully effective due to browser security restrictions)
      chrome.tabs.create({}); // Create a new tab to prevent the window from closing
    }
  }
}
```

***

Integrating this feature directly into Chrome would enhance the user experience by offering a built-in layer of protection against accidental tab closure, especially when working with crucial information or during intensive research sessions. This would eliminate the need for external extensions, ensuring a seamless and more secure browsing experience for all users. By providing users with a native option to enable or disable this confirmation prompt based on their preferences, Chrome could cater to a wider audience, accommodating those who value this safeguard while maintaining efficiency for users who prefer uninterrupted browsing. Such a feature would reflect Chrome's commitment to user-centric design, prioritizing not just speed and efficiency but also the prevention of potential disruptions in the user's workflow.

Remove the "X" from the single tab?

#

🛈 This software is free and open-source; anyone can redistribute it and/or modify it.

***
