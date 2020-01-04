---
description: Creating Asp.NET webpages.
---

# Asp.NET

## RegisterClientScript vs. RegisterStartupScript

**Source**: [http://stackoverflow.com/questions/666519/](http://stackoverflow.com/questions/666519/difference-between-registerstartupscript-and-registerclientscriptblock)

When you use RegisterStartupScript, it will render your script after all the elements in the page \(right before the form's end tag\). This enables the script to call or reference page elements without the possibility of it not finding them in the Page's DOM.

When you use RegisterClientScriptBlock, the script is rendered right after the Viewstate tag, but before any of the page elements. Since this is a direct script \(not a function that can be called, it will immediately be executed by the browser. But the browser does not find the label in the Page's DOM at this stage and hence you should receive an "Object not found" error.

## 

