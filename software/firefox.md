---
description: Anything related to THE MOST CUSTOMIZABLE browser out there.
---

# Mozilla Firefox

## Useful Add-ons

* Adguard Adblocker
* Greasemonkey
* React Developer Tools
* Reddit Enhancement Suite
* Table of Contents for Github
* Zoom Image

## Live Bookmarks

Live bookmarks can be used to list RSS feeds, or return a query from your bookmarks, from the database in `places.sqlite`. To create custom live bookmarks like the "recent" and "most visited", create a new bookmark and in "Address" add a `places:` and append your query string. Examples below.

Then close and re-open your browser to see the result.

### Documentation

* [Official docs](https://developer.mozilla.org/en-US/docs/Mozilla/Tech/Places/Places_query_URIs)
* [List of examples from MDN forums](http://forums.mozillazine.org/viewtopic.php?p=3260477)
* [API docs for Places](https://developer.mozilla.org/en-US/docs/Mozilla/Tech/Places/Querying)

### Examples

| Uri | Description |
| :--- | :--- |
| `place:queryType=1&tag=Sidebar&sort=8` | Tag search. |
| `place:folder=MOBILE_BOOKMARKS&folder=UNFILED_BOOKMARKS&queryType=1&excludeQueries=1&expandQueries=0&sort=12&maxResults=20` | Reading list. |
| `place:queryType=0&sort=8&maxResults=10` | Default: Most visited |
| `place:folder=BOOKMARKS_MENU&folder=UNFILED_BOOKMARKS&folder=TOOLBAR&queryType=1&sort=12&excludeItemIfParentHasAnnotation=livemark%2FfeedURI&maxResults=10&excludeQueries=1` | Default: Recent |
| `place:type=6&sort=14&maxResults=10` | Sorted by last modified |
| `place:folder=UNFILED_BOOKMARKS&excludeItems=1&expandQueries=0` | Unsorted |
| `place:folder=BOOKMARKS_MENU&folder=UNFILED_BOOKMARKS&folder=TOOLBAR&queryType=1&sort=12&excludeItemIfParentHasAnnotation=livemark%2FfeedURI&maxResults=10&excludeQueries=1` | Recent bookmarks in a folder |
| `place:beginTime=-86400000000&endTime=0&domain=mozillazine.org&terms=firefox&queryType=0` | Query for all history from last day that contains "firefox" and is from mozillazine.org domain |
| `place:folder=4&queryType=1&group=3&terms=top&sort=1&excludeQueries=1&expandQueries=0` | Query for all bookmarks with "top" tag \(broken\) |
| `place:terms=linux&folder=BOOKMARKS_MENU&folder=TOOLBAR&folder=UNFILED_BOOKMARKS&expandQueries=0&queryType=1` | Query for term "linux"\(broken\) |
| `place:queryType=0&sort=8&maxResults=10&onlyBookmarked=true` | Query for most visited bookmarked items |
| `place:folder=4&group=3&queryType=1&applyOptionsToContainers=1&sort=12&maxResults=10` | Query for items with recently used tags |
| `place:type=0&sort=4&maxResults=10` | Default history menu |
| `place:folder=BOOKMARKS_MENU&excludeItems=1&queryType=1` | Default bookmarks menu |
| `place:folder=UNFILED_BOOKMARKS` | Add Unfiled Bookmarks to Bookmarks Menu |
| `queryType=1&type=7&folder=tag_folder_id` | Retreive bookmarks with specific tag \(doesn't use terms, but folder id\) |

## About:Config

| key | default | recommended | Description |
| :--- | :---: | :---: | :--- |
| toolkit.scrollbox.verticalScrollDistance | 3 | 15 | Change arrow keys scroll speed |
| mousewheel.acceleration.start | -1 | -1 | Starts scrolling accelerations after 4 scroll-wheel clicks |
| mousewheel.acceleration.factor | 10 | 10 | Scroll speed after enabling scroll acceleration |
| extensions.pocket.enabled | true | false | Disables the bundled Pocket sharing extension |
| extensions.screenshots.disabled | false | true | Disabled the bundled screenshot extension |
| mousewheel.default.delta\_multiplier\_y | 100 | 300 | Mouse y scrolling |
| browser.ctrlTab.previews | false | true | Tab-preview on ctrl-tab |
| browser.urlbar.clickSelectsAll | true | false | Clicking in url bar selects all text |
| browser.urlbar.doubleClickSelectsAll | false | true | Double click in url bar selects all text |
| findbar.modalHighlight | false | true | Adds an overlay to the page when searching for text, makes it easier to spot your results. |
| findbar.highlightAll | false | true | Can also be enabled in the search bar, this highlights all results on the page when searching |
| browser.tabs.loadBookmarksInTabs | false | true | Open bookmarks in tabs. |
| browser.search.openintab | false | true | Open search in tabs. |
| layout.word\_select.eat\_space\_to\_next\_word | true | false | Double clicking a word sometimes select the space next to it. |
| reader.parse-on-load.enabled | true | ? | Disables the reading mode. Don't know if it will speed up anything. |
| browser.search.context.loadInBackground | false | true | Launches the context menu search in a background tab. |
| browser.backspace\_action | 0 | 2 | Decides what backspace does. 0 goes back in history. 1 does a page up. 2 disables it. Useful to disable to avoid accidentally losing pages when deleting text from a textbox. Not that it really matters, Firefox remembers the page state when you press page-forward. Wish i had this in Edge. |

### Security settings

| key | default | recommended | Description |
| :--- | :---: | :---: | :--- |
| security.mixed\_content.block\_display\_content | false | true | Stops loading http resources on https pages |
| network.IDN\_show\_punycode | false | true | Disable ASCII compatible encoding in url bar. [Source](https://www.wordfence.com/blog/2017/04/chrome-firefox-unicode-phishing/). |
| browser.safebrowsing.downloads.enabled | true | ? | Firefox is sending information to Google. Do you want to? |
| browser.safebrowsing.downloads.remote.enabled | true | ? | Firefox is sending information to Google. Do you want to? |
| browser.safebrowsing.malware.enabled | true | ? | Firefox is sending information to Google. Do you want to? |
| browser.safebrowsing.phishing.enabled | true | ? | Firefox is sending information to Google. Do you want to? |
| browser.fixup.alternate.enabled | true | false | Out of the box, Firefox has a feature designed to help people mis-typing URLs in the browser bar. It’s described in detail here, but briefly, if a URL fails to resolve, Firefox trys a couple of permutations of the URL to try find what you –might have– really intended, appending a .com and/or prefixing a www. to the host name portion of the URL to see if they resolve. [Source](https://cdivilly.wordpress.com/tag/browser-fixup-alternate-enabled/). |

## Export Firefox Quantum passwords

* Python script to export passwords from Firefox:

  [https://github.com/unode/firefox\_decrypt](https://github.com/unode/firefox_decrypt)

* Software to export passwords from Firefox:

  [http://www.nirsoft.net/utils/passwordfox.html](http://www.nirsoft.net/utils/passwordfox.html)

