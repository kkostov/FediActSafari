# FediAct (v0.9.8)
A Chrome/Firefox extension that simplifies follow and post interactions on Mastodon servers other than your own.

**Features**:
- Supports Mastodon v3 + v4 (some features v4 only)
- Follow, boost, bookmark, reply, fav, vote polls and mute/block on external servers while only being logged in to your home server
- Show following state and toot state (boosted, faved, bookmarked, voted) on external servers
- Single click to execute action only, double click to redirect to content on home server
- Reply button on external servers always redirects to home server and enters reply-mode
- Hide muted content on external servers if enabled
- Needs nothing more than your home server domain to work

## Navigation
- [Installation](#installation)
- [Setup](#setup)
- [FAQ](#faq)
- [Screenshots / GIFs](#screenshots--gifs)
- [Manual installation](#manual-installation)
  - [Install in Firefox for Android](#install-in-firefox-for-android)
- [Additional notes](#additional-notes)
- [Todos / Planned features](#todos--planned-features)
- [Contributing](#contributing)

## Installation

[link-chrome]: https://chrome.google.com/webstore/detail/fediact/lmpcajpkjcclkjbliapfjfolocffednm 'Version published on Chrome Web Store'
[link-firefox]: https://addons.mozilla.org/en-US/firefox/addon/fediact/ 'Version published on Mozilla Add-ons'

[<img src="https://raw.githubusercontent.com/alrra/browser-logos/90fdf03c/src/chrome/chrome.svg" width="48" alt="Chrome" valign="middle">][link-chrome] [<img valign="middle" src="https://img.shields.io/chrome-web-store/v/lmpcajpkjcclkjbliapfjfolocffednm.svg?label=%20">&nbsp;&nbsp;Chrome Webstore][link-chrome]  
All up-to-date Chromium browsers, including Kiwi and Yandex browsers on Android

[<img src="https://raw.githubusercontent.com/alrra/browser-logos/90fdf03c/src/firefox/firefox.svg" width="48" alt="Firefox" valign="middle">][link-firefox] [<img valign="middle" src="https://img.shields.io/amo/v/fediact.svg?label=%20%20">&nbsp;&nbsp;Mozilla Addon Store][link-firefox]  
Up-to-date Firefox (v107+), including Firefox Nightly on Android

**Please note:**  
- If webstore release is outdated, use the [manual installation method](#manual-installation) to install the latest version  
- Special installation steps for [Firefox on Android](#install-in-firefox-for-android)  
- Chrome store updates take 1-2 days longer  
- If you like this addon, please consider donating: [paypal.me/lartsch](https://paypal.me/lartsch)

## Setup

1. Make sure you are logged in to your home server
2. Click the extension icon or open its settings page
3. Set your home server domain (required)
4. Check out the other settings (optional)
5. Click the "Save" button to save

If you have set your home server correctly, you can now interact on other Mastodon servers.

**Please note:**   
- If FediAct is running, a small icon will be displayed in the bottom right corner  
- Also, it is indicated while content is resolving or when it could not be resolved  
- Performance depends on your home server and the external server you are browsing (read more [below](#additional-notes))  
- Some toots can't be resolved to your home (e.g. when searching the post manually wouldn't work either)  
- It's NOT recommended to disable the API delay (servers use rate limiting and might block your IP)

## FAQ
**Why does it need permission for all websites?**

> The addon needs to determine whether or not the site you are currently browsing is a Mastodon server. For that to work, it requires access to all sites. Otherwise, each existing Mastodon server would have to be explicitly added.

**Can I use this on Android?**

> Yes! There are three options that I am aware of: Kiwi Browser, Yandex Browser and Firefox Nightly (see [below](#install-in-firefox-for-android))

**Can I use this on iOS?**

> Currently not in a reliable way, but:  
> - It's possible that Orion Browser can soon be used (see issue [#16](https://github.com/Lartsch/FediAct/issues/16))  
> - There are plans for Safari support (see issue [#17](https://github.com/Lartsch/FediAct/issues/17))

**Can you add feature XY?**

> Feel free to create an issue here on GitHub and I will look into it.

**Is this safe to use?**

> This project is open source. Anyone with some programming knowledge can check out the source code, either here on GitHub or by extracting the addon file from the addon stores. You can also make improvements. 
> Considering the implementation, I am not aware of any risks. Efforts were made to prevent servers from abusing this addon to perform actions on the user's behalf. It does not require your username or password. All data is stored in your browser locally, with the API token being the only sensitive data. This token is **only** sent to your home server. No other data ever leaves your device. All requests are made from the background script, out-of-scope for websites you visit.

## Screenshots / GIFs
v0.9.8
<details>
  <summary>Extension popup / settings</summary>
  <img src="https://github.com/lartsch/FediAct/blob/main/img/settings.png?raw=true">
</details>
<details>
  <summary>Showcase</summary>
  <img src="https://github.com/lartsch/FediAct/blob/main/img/showcase.gif?raw=true">
</details>

## Manual installation
1. Download the [latest GitHub release](https://github.com/Lartsch/FediAct/releases/latest) for your browser (Chrome or Firefox)
### Chrome
2. Unzip the downloaded file somewhere
3. Go to your Chrome extension page (URL: chrome://extensions) and enable developer mode
4. Click the "Load unpacked" button and then select the unzipped folder

Note: Some Chromium browsers allow you to directly load a .zip file - you can use it if available

### Firefox
2. Open the debugging page (URL: about:debugging)
3. Select "This Firefox"
4. Click the "Load Temporary Add-on" button and then select the downloaded Firefox ZIP file

### Install in Firefox for Android
For a while now, Firefox on Android has only allowed installing from a [curated list](https://addons.mozilla.org/en-US/android/search/?promoted=recommended&sort=random&type=extension) of addons, preventing installation of anything else. The following instructions will guide you through installing it from the webstore anyway.

**Requirements:**  
- Firefox [**Nightly**](https://play.google.com/store/apps/details?id=org.mozilla.fenix) for Android  
  
**Steps:**  
1. In Firefox, go to Settings > About Firefox Nightly
2. Click the Firefox logo 5 times to enable Developer options
3. Go back to Settings > Custom Add-on Collection
4. Enter the following data:
    - ID: 17665294
    - Name: FediAct
5. Click OK, Firefox will close - reopen it
6. FediAct will now be available in the Add-ons menu of Firefox Nightly

To update the addon instantly, simply remove and re-install it. I don't know if or when auto-update triggers in Firefox.
  
I included all of the default add-ons in the custom collection, so you will not miss out on any of those. Of course, you can create [your own collection](https://support.mozilla.org/en-US/kb/how-use-collections-addonsmozillaorg) as well.

## Additional notes
1. Support for other Fedi software is planned
2. There are several reasons why resolving/interacting might not work including:
    - Not being logged in to your home server
    - Element identifiers have changed / the server uses an unsupported flavour
    - The external server you are browsing or the originating server of a toot is not Mastodon
    - Your home server has strong rate limiting and limited your IP
    - Your home server / the external server / the original server of a toot have defederated / are moderated
    - The toot has not yet federated to your home instace (follow the account and toots should start federating)
    - The server you are browsing does not use 302 redirects for external toots
    - The network conditions of your home server or the external server are bad (slow speed)
    - That a toot is set to unlisted on its original server may play a role
3. There can be delays because API calls have to be made and it is tries to avoid error 429 (too many requests). Especially if a page has many toots or you are scrolling through a feed really fast.
4. If the extension fails to resolve content, the affected buttons will behave as if the extension weren't active (popup modal) and a notice ("Unresolved") is added to the toot
5. If "Collect errors" is enabled (Chrome), there can be uncatched errors being displayed for FediAct. This is not relevant to functionality.

## Todos / Planned features 
Check out the [GitHub project](https://github.com/users/Lartsch/projects/2) to see planned features and todos. They are sorted from most important to least important.

## Contributing
Feel free to create [issues](https://github.com/Lartsch/FediAct/issues) for bugs and feature suggestions. Even better: Create pull requests for whatever improvements you can make! :)

## Thanks to...
- @raikasdev because I stole his fix for cross-browser storage API support  
- @rosemarydotworld because I customized and use his awesome jQuery.DOMNodeAppear where MutationObservers and delegation failed
- All the direct [contributors](https://github.com/Lartsch/FediAct/graphs/contributors) to this repository!
