What's New in Sprint 37
-----------------------
* **Installation**
    * [Code-signed builds (Mac & Win)](https://trello.com/c/g5ZY1lKY/1131-code-signing-on-win-and-mac): Eliminates some warnings on launch and install. Gatekeeper no longer prevents launching Brackets by default on Mac.
* **Find**
    * [Exclude files/folders from find in files](https://trello.com/c/7Svh6B4Z/1085-exclude-files-folders-from-an-individual-find-in-files-operation): Choose file names, paths, or wildcards to exclude from Find in Files searches.
* **Preferences**
    * [New preferences: proxy server, insert code hints on tab, project tree folder sorting, more](https://github.com/brackets-cont/brackets/wiki/How-to-Use-Brackets#preferences): Notably, this means it's now possible to install extensions via Extension Manager if your Internet access is behind a proxy server. See link for full list of preferences.
    * [Revamped preferences APIs ready for extensions to use](https://github.com/brackets-cont/brackets/pull/6715): See [documentation](https://github.com/brackets-cont/brackets/wiki/How-to-write-extensions#wiki-working-with-preferences) for details.
    * [Migrate view state to new preference storage format](https://trello.com/c/IuFGyICH/1155-preferences-view-state-migration): A new `state.json` file stores preferences that are less likely to be shared across machines.
* **Ongoing Research** (not enabled yet)
    * [Multiple cursor/selection support](https://trello.com/c/urTCdTZj/1156-multiple-cursors-initial-implementation-on-branch): Initial implementation on a branch, not exposed in this release of Brackets yet.
    * [Research JS Code Hints Cleanup](https://trello.com/c/heHZlATB/1158-research-js-code-hints-cleanup): Investigate how to simplify the code, improve performance & maintainability, and unify with new preferences system.
* **CSS Editing**
    * [Open inline CSS easing editor on empty timing functions](https://github.com/brackets-cont/brackets/pull/6922): Graphically create CSS transition easing curves/steps without having to remember or write out the full syntax first.
* **Stability Improvements**
    * Live Preview launches and connects to Chrome more reliably
    * Fixed slow performance when Find in Files results panel left open for long periods of time
    * Fixed issue with noticing external file changes during some 'bulk' operations like git checkout
    * Improved accuracy of JavaScript code hints when using `require()` modules
    * Fixed [#6951](https://github.com/brackets-cont/brackets/issues/6951): Unable to install extensions or run Live Preview on Windows XP
    * Ensure Live Preview works on upcoming Chrome 34 release
* **Localization**
    * [Indonesian translation added](https://github.com/brackets-cont/brackets/pull/6812)

_Full change logs:_ [brackets](https://github.com/brackets-cont/brackets/compare/sprint-36...sprint-37#commits_bucket) and [brackets-shell](https://github.com/brackets-cont/brackets-shell/compare/sprint-36...sprint-37#commits_bucket)


UI Changes
----------
**Working Files list** - Options to change sort order have been moved from the context menu into a new settings menu, accessed via the gear icon in the Working Files header.

API Changes
-----------
**Preferences** - Brackets offers new APIs for storing preferences in a user-accessible JSON format, and the old preferences APIs are now _deprecated_. Preferences are now divided into settings and "view state," each stored separately. Setting-type preferences provide change events that you should listen to for updates. See [full Preferences API documentation] for details, including how to migrate existing user preferences from the old system.

**File System** - Paths with unsupported Windows-style separators ("\" instead of "/") are now explicitly rejected immediately; previously they were accepted by FileSystem but behaved brokenly in various ways. Brackets APIs generally all returned "/"-based paths already, though one that previously did not - `FileSystem.showOpenDialog()` in single-select mode - has been changed to match this format.

**jQuery** - Upgraded from 2.0.1 to 2.1.0

**Editor** - The `"optionChange"` event now uses the Brackets names for the options, rather than the CodeMirror names (for example "wordWrap" rather than "lineWrapping"). See Editor.js for [the complete list](https://github.com/brackets-cont/brackets/blob/master/src/editor/Editor.js#L79).

**Code Hints** - `CodeHintManager.setInsertHintOnTab()` has been **removed**. It is replaced with the `insertHintOnTab` user preference.


New/Improved Extensibility APIs
-------------------------------
**Preferences** - See information above on the new APIs and their capabilities.


Known Issues
------------
* Activity Monitor in Mavericks (OS X 10.9) says the Brackets Helper process is "Not Responding" even when it's working normally ([#5794](https://github.com/brackets-cont/brackets/issues/5794)). You can safely ignore this unless Brackets is actually failing to respond when you click or type text.
* On Windows XP, Brackets will not detect external file changes instantly. It behaves similarly to Sprint 35 and earlier releases - changes are detected upon window activation, and the folder tree must be manually refreshed.
* [#2272](https://github.com/brackets-cont/brackets/issues/2272): Windows Vista may not allow the Brackets installer to run (you may not see _any_ error message). To work around this, right-click the installer file, choose Properties, and click the Unblock button.
* [#4362](https://github.com/brackets-cont/brackets/issues/4362): Slow startup of Brackets and Live Preview on Windows due to Chrome proxy settings. [See workaround](https://support.google.com/chrome/answer/106010?hl=en).
* _Debug > Run Tests_ is disabled in the installer/DMG distributions of Brackets, because the unit test code is not included. To run unit tests, [pull Brackets from GitHub](https://github.com/brackets-cont/brackets/wiki/How-to-Hack-on-Brackets#wiki-getcode) instead.


Community contributions to Brackets
-----------------------------------
* [Allow inline cubic-bezier/steps editor on empty timing functions](https://github.com/brackets-cont/brackets/pull/6922) by [Marcel Gerber](https://github.com/SAPlayer)
* [Keep Find in Files results in predictably sorted order](https://github.com/brackets-cont/brackets/pull/6585) ([and](https://github.com/brackets-cont/brackets/pull/7067)) by [Tomás Malbrán](https://github.com/TomMalbran)
* [Move Working Files sort options from context menu to new settings dropdown](https://github.com/brackets-cont/brackets/pull/6107) by [Alessandro Artoni](https://github.com/artoale) ([followup fixes](https://github.com/brackets-cont/brackets/pull/7085) by [Tomás Malbrán](https://github.com/TomMalbran))
* [New preference: Insert code hints with Tab](https://github.com/brackets-cont/brackets/pull/6984) by [Tomás Malbrán](https://github.com/TomMalbran)
* [New preference: Sort directories to top in file tree (vs. intermingled with files)](https://github.com/brackets-cont/brackets/pull/7138) by [Tomás Malbrán](https://github.com/TomMalbran)
* [New preferences: Disable 'smart indent'; disable auto-inserting HTML close tags](https://github.com/brackets-cont/brackets/pull/6888) by [Tomás Malbrán](https://github.com/TomMalbran)
* [If preferences JSON is invalid, show a warning and then run without the setting changes from that file](https://github.com/brackets-cont/brackets/pull/6719) by [Arzhan "kai" Kinzhalin (Intel Corp)](https://github.com/busykai)
* [Replace can use `$&` to insert whole regexp match](https://github.com/brackets-cont/brackets/pull/5929) by [Marcel Gerber](https://github.com/SAPlayer)
* [Allow specifying a port number in Live Preview custom server URL](https://github.com/brackets-cont/brackets/pull/6815) by [andoband](https://github.com/andoband)
* [Add Indonesian translation](https://github.com/brackets-cont/brackets/pull/6812) ([and](https://github.com/brackets-cont/brackets/pull/7116)) by [Nasaruddin](https://github.com/pace-noge) and [Resi Respati](https://github.com/resir014)
* [Disable Close Others context menu items when irrelevant](https://github.com/brackets-cont/brackets/pull/6020) by [Marcel Gerber](https://github.com/SAPlayer)
* [Strip leading/trailing whitespace from extension URL](https://github.com/brackets-cont/brackets/pull/7052) by [Marcel Gerber](https://github.com/SAPlayer)
* [OS-specific labels for "Show in OS" context menu item](https://github.com/brackets-cont/brackets/pull/6982) by [Marcel Gerber](https://github.com/SAPlayer)
* [Make Overwrite cursor mode visually distinct from Insert mode](https://github.com/brackets-cont/brackets/pull/6777) ([and](https://github.com/brackets-cont/brackets/pull/6883)) by [Bernhard Sirlinger](https://github.com/WebsiteDeveloper)
* [Don't hide user-editable source control files like .gitignore](https://github.com/brackets-cont/brackets/pull/6833) by [Tom Van Schoor](https://github.com/TVScoundrel)
* [Find in Files: Expand/collapse all sections via Ctrl/Cmd-click](https://github.com/brackets-cont/brackets/pull/6640) by [Sathyamoorthi](https://github.com/sathyamoorthi)
* [Bezier inline editor: tab between points to move them with keyboard](https://github.com/brackets-cont/brackets/pull/6576) by [Marcel Gerber](https://github.com/SAPlayer)
* [Add CSS value code hints for `flex`, `flex-basis` properties](https://github.com/brackets-cont/brackets/pull/6584) by [Marcel Gerber](https://github.com/SAPlayer)
* [Highlight .ascx files (ASP.NET User Controls) as plain HTML](https://github.com/brackets-cont/brackets/pull/6914) by [Clay Miller](https://github.com/smockle)
* [Highlight .plist (Property List) files as XML](https://github.com/brackets-cont/brackets/pull/6915) by [Clay Miller](https://github.com/smockle)
* [Fix some native memory leaks on Mac](https://github.com/brackets-cont/brackets-shell/pull/414) by [Brandon Jones](https://github.com/btjones)
* [Fix font zoom viewport for new CodeMirror](https://github.com/brackets-cont/brackets/pull/7118) ([and](https://github.com/brackets-cont/brackets/pull/7120)) by [Tomás Malbrán](https://github.com/TomMalbran)
* [Fix #6828: Return Brackets-style paths from extension-installation code](https://github.com/brackets-cont/brackets/pull/6848) by [Arzhan "kai" Kinzhalin (Intel Corp)](https://github.com/busykai)
* [Fix Toggle Line Comment in JSON files](https://github.com/brackets-cont/brackets/pull/6897) by [Marcel Gerber](https://github.com/SAPlayer)
* [Prep work for supporting native menubar on Linux](https://github.com/brackets-cont/brackets-shell/pull/348) (not enabled yet) by [MattSturgeon](https://github.com/MattSturgeon)
* [Fix #6612: Reset scroll position in Find in Files results more reliably](https://github.com/brackets-cont/brackets/pull/6629) by [Tomás Malbrán](https://github.com/TomMalbran)
* [Fix #5923: Don't scroll hidden list tab in Extension Manager](https://github.com/brackets-cont/brackets/pull/6637) by [Marcel Gerber](https://github.com/SAPlayer)
* [Update jQuery to 2.1.0 (from 2.0.1)](https://github.com/brackets-cont/brackets/pull/6724) by [Bernhard Sirlinger](https://github.com/WebsiteDeveloper)
* [Fix failing ProjectManager unit test](https://github.com/brackets-cont/brackets/pull/6857) by [Lance Campbell](https://github.com/lkcampbell)
* [Fix CodeInspection unit tests on non-English locales](https://github.com/brackets-cont/brackets/pull/6731) by [Bernhard Sirlinger](https://github.com/WebsiteDeveloper)
* [Code cleanup: Close Others context menu](https://github.com/brackets-cont/brackets/pull/7038) by [Marcel Gerber](https://github.com/SAPlayer)
* [Code cleanup: Remove unneeeded .livehtml flag](https://github.com/brackets-cont/brackets/pull/6994) by [Marcel Gerber](https://github.com/SAPlayer)
* [Code cleanup: Remove duplicate CSS code hint value](https://github.com/brackets-cont/brackets/pull/6766) by [Bernhard Sirlinger](https://github.com/WebsiteDeveloper)
* [Code cleanup: Avoid `.not.toBe(null)` in unit tests](https://github.com/brackets-cont/brackets/pull/6577) by [Michael Hernandez (Intel Corp)](https://github.com/mjherna1)
* [setup_for_hacking script: Support git repo locations with spaces in path on Windows](https://github.com/brackets-cont/brackets/pull/6841) by [Andrew Dal Cin](https://github.com/adalcin)
* [Fix brackets-shell build script on Mac case-sensitive file systems](https://github.com/brackets-cont/brackets-shell/pull/410) by [Martin Prins](https://github.com/magarcia)
* [Fix #6452: Prevent Debug > Reload Brackets from being run re-entrantly](https://github.com/brackets-cont/brackets/pull/6846) by [Lance Campbell](https://github.com/lkcampbell)
* [Use names from each language's own locale in the Debug > Switch Language UI](https://github.com/brackets-cont/brackets/pull/6725) by [Michael Hernandez (Intel Corp)](https://github.com/mjherna1)
* [Czech translation update](https://github.com/brackets-cont/brackets/pull/7001) by [kvarel](https://github.com/kvarel)
* [German translation update](https://github.com/brackets-cont/brackets/pull/7177) by [Marcel Gerber](https://github.com/SAPlayer)
* [Persian-Farsi translation update](https://github.com/brackets-cont/brackets/pull/6921) by [Mohammad Yaghobi](https://github.com/mohammadyaghobi)
* [Polish translation update](https://github.com/brackets-cont/brackets/pull/6596) by [Olgierd Grzyb](https://github.com/winek)
* [Romanian translation update](https://github.com/brackets-cont/brackets/pull/6820) by [Micleusanu Nicu](https://github.com/micnic)
* [Spanish translation update](https://github.com/brackets-cont/brackets/pull/7187) by [Tomás Malbrán](https://github.com/TomMalbran)
* [Russian translation fix](https://github.com/brackets-cont/brackets/pull/6924) by [wpt](https://github.com/wpt)
* [Russian translation fix](https://github.com/brackets-cont/brackets/pull/7192) by [Arzhan "kai" Kinzhalin (Intel Corp)](https://github.com/busykai)
* [Update localization instructions](https://github.com/brackets-cont/brackets/pull/7009) by [Michael Hernandez (Intel Corp)](https://github.com/mjherna1)


#### Pulling source code from Git
* Recommended: rebuild or reinstall an updated brackets-shell (no critical updates, but there are bugfixes).
* Some submodules were updated this sprint. Run `git submodule update` to ensure your source tree is fully up to date.


Bugs fixed in Sprint 37
-----------------------
For details on the bugs addressed, please refer to [closed sprint 37 bugs](https://github.com/brackets-cont/brackets/issues?labels=&milestone=24&state=closed). Not all fixed bugs will be caught by this search query, however.
