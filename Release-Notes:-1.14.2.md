What's New in Release 1.14.2
-------------------------
* [**Open File in external Applications**](https://github.com/brackets-cont/brackets/pull/15088) by [niteskum](https://github.com/niteskum) : Brackets now offers support to open file of any arbitary type with external applications. In User Preferences settings, you can associate a file extension to open with the default associated application or open with a specific application.

Usage: For example, Preferences settings for associating svg files to open with Google Chrome and "psd" to open with its default associated application:

"externalApplications": { "svg": "google chrome", "psd": "default" }

The application's name in this settings is OS dependant, for example if you would like to open a file with Chrome you have to use "google chrome" on macOS and "chrome" on Windows in your settings. We use the open npm utility under the hood , and settings that works with this utility will work here.

You may also pass in the app's full path. For example on Windows, this can be "C:\\Program Files (x86)\\Google Chrome\\Application\\chrome.exe" for the Windows installation of Chrome.

* [**Automatically associate Graphics file types to its OS default application**](https://github.com/brackets-cont/brackets/pull/15092) by [niteskum](https://github.com/niteskum) :  If an opened project folder has any graphics file of type: ["xd", "jpg", "jpeg", "svg", "ai", "png", "psd"], then with user’s consent Brackets will associate these graphics file types with its OS default associated application and record this under user preference settings under the category “externalApplications”.

_Full change logs:_ [brackets](https://github.com/brackets-cont/brackets/compare/release-1.14.1...release-1.14.2#commits_bucket) and [brackets-shell](https://github.com/brackets-cont/brackets-shell/compare/release-1.14.1...release-1.14.2#commits_bucket)

Community contributions to Brackets
-----------------------------------


* [Adding value "legacy" to justify-items and removing "unset" from justify-items and justify-self as per w3 org recommendations.](https://github.com/brackets-cont/brackets/pull/14555) by [narayani28](https://github.com/narayani28)
* [Add css scroll-snap-type](https://github.com/brackets-cont/brackets/pull/14555) by [abaracedo](https://github.com/abaracedo)
* [Add autocompletion for justify-items and justify-self](https://github.com/brackets-cont/brackets/pull/14558) by [abaracedo](https://github.com/abaracedo)
* [Fixing update notification locale issue, update notification was shown in English for all locales](https://github.com/brackets-cont/brackets/pull/14995) by [jha-g](https://github.com/jha-g)
* [Fix filters for In App Notifications ](https://github.com/brackets-cont/brackets/pull/14797) by [shubhsnov](https://github.com/shubhsnov)
* [Public methods for closing Search Results and References bottom panel](https://github.com/brackets-cont/brackets/pull/15016) by [SietseB](https://github.com/SietseB)
* [Fix for: `Reload With(out) Extensions` not working](https://github.com/brackets-cont/brackets/pull/15017) by [SietseB](https://github.com/SietseB)

#### Pulling source code from Git

* A new brackets-shell build is _required_ for this sprint. Be sure to rerun `grunt setup` before building.
* Recommended: rebuild or reinstall an updated brackets-shell (no critical updates, but there are bugfixes).
* Some submodules were updated this sprint. Run `git submodule update` to ensure your source tree is fully up to date.