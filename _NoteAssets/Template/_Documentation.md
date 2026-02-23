---
tags:
  - Official-Documentation
author:
  - jacgit18
Status: Done
Started: 
EditDate: 
Relates: "[[]]"
URL: https://forums.daybreakgames.com/dcuo/index.php?threads/last-anime-gif-wins.263481/page-23
---
```dataviewjs
// Access the URL value from the current note's YAML frontmatter
const { URL } = dv.current();

// Check if the URL exists
if (!URL) {
    dv.span("No URL found in the YAML frontmatter.");
} else {
    // Create an iframe element dynamically
    const iframe = document.createElement("iframe");

    // Set iframe attributes
    iframe.src = URL;
    iframe.style.width = "100%";
    iframe.style.height = "100vh";
    iframe.style.border = "none";

    // Style the document body to fit the iframe
    document.body.style.margin = "0";
    document.body.style.overflow = "hidden";

    // Append the iframe to the document body
    document.body.appendChild(iframe);
}
```





<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Iframe Example</title>
  <style>
    body {
      margin: 0;
      overflow: hidden;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
    }
    iframe {
      width: 1080px;
      height: 1920px;
      border: none;
    }
  </style>
</head>
<body>
  <!-- Embed the iframe with fixed dimensions -->
  <iframe src="https://forums.daybreakgames.com/dcuo/index.php?threads/last-anime-gif-wins.263481/page-23"></iframe>
</body>
</html>

