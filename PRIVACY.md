# Lumen and your privacy

**The short version:** Lumen has no accounts, no ads, no analytics, no crash reporting and no telemetry. It doesn't talk to Google unless you go to a Google site, use Google as your search engine, or use the Chrome Web Store. What you do in Lumen stays on your PC, unless you turn on Sync, which encrypts everything with a passphrase only you know before it leaves.

## What stays on your PC

Your tabs, spaces, history, bookmarks, notes, downloads list, saved passwords, data ledger and settings are stored in `%APPDATA%\Lumen`. Saved passwords and the data ledger are encrypted with your Windows account. None of it is uploaded anywhere, except through Sync if you turn it on.

## Who Lumen connects to, and why

Besides the websites you visit, these are the only places Lumen connects to:

| Where | When | Why | What it learns about you |
|---|---|---|---|
| Your search engine (DuckDuckGo unless you pick another) | When you search from the address bar | To search | Your search, as with any browser |
| GitHub (`github.com`, `api.github.com`, `raw.githubusercontent.com`) | A few times a day | Lumen updates, the ad blocker's filter lists (every 3 days), yt-dlp updates (once a day) | That someone downloaded a file: your IP address and Lumen's version, like any download |
| malware-filter (`malware-filter.gitlab.io`, `malware-filter.pages.dev`, `curbengh.github.io`) | Twice a day | Lists of known phishing and malware sites | Nothing about where you browse: the sites you visit are checked against the list **on your PC** |
| Have I Been Pwned (`haveibeenpwned.com`) | Once a day, if Breach alerts are on | The public list of known data breaches | Nothing: the list is matched against your data ledger **on your PC** |
| Microsoft (`login.microsoftonline.com`, `graph.microsoft.com`) | Only if you turn on Sync | Storing your encrypted sync file in your own OneDrive | Your Microsoft account sign-in; the file itself is encrypted before upload and Microsoft can't read it |
| Google: Chrome Web Store (`chromewebstore.google.com`, `clients2.google.com`, `update.googleapis.com`) | Only when you open the Web Store, and to update extensions you installed from it | Installing and updating extensions | Which extensions you have |
| The npm registry (`registry.npmjs.org`) | Only for copies run from the source folder | Checking for a newer engine | That someone checked, like any download |
| Your own network (`wpad`) | When Lumen starts | Windows' standard check for a proxy server on your network | Nothing leaves your network |

If you installed Lumen from the Microsoft Store, the Store installs Lumen's updates instead of GitHub, under Microsoft's own privacy terms for the Store.

## What Lumen never does

- No telemetry, usage statistics, analytics or crash reports.
- No Google Safe Browsing: dangerous-site checks use public lists, checked on your PC.
- No Google sign-in prompts, Google account or any other account.
- No ads, and nothing is sold or shared.
- No hidden Google services. Lumen is built on Chromium through Electron, which leaves out Chrome's Google features (sync, translation, Safe Browsing, usage reporting).

## Blocking

Ad and tracker blocking is built into Lumen, not added as an extension, so Chrome's Manifest V3 limits don't apply. It blocks at the network level and hides leftover ad boxes, using the same filter lists as uBlock Origin and Ghostery. The shield in the address bar shows how much was blocked on a page and lets you turn blocking off for one site.

## How we checked

We recorded Lumen's network traffic (Chromium's network log) on 25 October 2026, with Lumen 0.1.6 (Electron 45, Chromium 156). During startup, browsing a page, typing into a spell-checked text box and 90 seconds of idling, the browser engine made **no requests to Google or anyone else** apart from the page itself and Windows' local proxy check (`wpad`). The connections Lumen makes on its own, listed above, come from its source code.

## Turning things off

Settings → Privacy & security: ad and tracker blocking, dangerous-site warnings, the data ledger and Breach alerts. Settings → Downloads: the download button on videos. Sync is off unless you turn it on.

## Questions

Ask anything about Lumen and your privacy by opening an issue at [github.com/HashTito1/lumen-releases/issues](https://github.com/HashTito1/lumen-releases/issues). If this policy changes, the new version will be on this page with its date.

*Last updated: 25 October 2026*
