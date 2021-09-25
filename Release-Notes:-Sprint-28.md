What's New in Sprint 28
-----------------------
* **Extensions**
    * [Extension Registry](https://trello.com/card/2-extension-registry-support-in-extension-manager/4f90a6d98f77505d7940ce88/911): Search for and install extensions directly within Brackets! Extension authors, [upload your extensions](https://brackets-registry.aboutweb.com/) to the new registry. More details below.
* **File Management**
    * [New Untitled documents](https://trello.com/card/3-create-save-untitled-file-file-new/4f90a6d98f77505d7940ce88/291): File > New now instantly creates an untitled document. You are not prompted for a name/location until save.
* **Drag & Drop**
    * [Drag _file_ onto window to open](https://trello.com/card/2-native-drag-n-drop-open-file/4f90a6d98f77505d7940ce88/281): Dragging a file onto the Brackets window works the same as File > Open. (This functionality was previously working on Windows only).
    * [Drag _folder_ onto window to switch projects](https://trello.com/card/2-native-drag-n-drop-open-folder/4f90a6d98f77505d7940ce88/873): Dragging a folder onto the Brackets window works the same as File > Open Folder.
* **Stability**
    * The [crash](https://github.com/brackets-cont/brackets/issues/4400) (blank UI) seen by several people while editing JS code should no longer occur. It was caused by a V8 bug that we have temporarily worked around; the actual V8 fix will get merged in the future ([once we can update CEF safely](https://trello.com/c/gIwbocii/938-3-cef-crash-issues)).
* **Overall UI**
    * [Animation cues on open/close inline editor & hover preview (Quick View)](https://trello.com/card/1-ux-animate-inline-editor-and-quick-view/4f90a6d98f77505d7940ce88/809)
* **Research**
    * [Investigate Windows titlebar restyling](https://trello.com/c/d77Fd4F9/874-5-into-darkness-shell-windows): Early investigation for changing to a compact, dark titlebar design on Windows.

_Full change logs:_ [brackets](https://github.com/brackets-cont/brackets/compare/sprint-27...sprint-28#commits_bucket) and [brackets-shell](https://github.com/brackets-cont/brackets-shell/compare/sprint-27...sprint-28#commits_bucket)


UI Changes
----------
**Extension Manager** - The "Available" tab now lists all Brackets extensions, pulled from an online registry. You can browse or search the listing, and install any extension with one click. [Read more...](https://github.com/brackets-cont/brackets/wiki/Brackets-Extensions#installing-and-removing-extensions)

**New File** - File > New now creates an untitled document (name and location aren't specified until the first time you save). The folder tree context menu's New File command continues to work as before (location is determined by what you right-clicked, name is given immediately). Both commands no longer default to a .js file extension.

**New Folder** - Has been removed from the File menu. Use the context menu in the folder tree to access New Folder.

**Live Highlighting** - This toggle has been moved from the File menu to the View menu.

API Changes
-----------
**Extension registry** - To appear in the new Extension Manager listing, your extension must be uploaded to [our new online extension registry](https://brackets-registry.aboutweb.com/). Be sure your extension includes a package.json file [with the required fields](https://github.com/brackets-cont/brackets/wiki/Extension-package-format) (the upload site will validate this for you automatically).

**Toolbar icons** - Icons for the right-side toolbar should be exactly 24x24 pixels. See [Extension Icon Guidelines](https://github.com/brackets-cont/brackets/wiki/Extension-Icon-Guidelines#dimension) for details.

**Untitled Documents** - You may encounter a new subclass of `FileEntry`, `InaccessibleFileEntry`, in two places: the value of `Document.file`, or as an entry in the working set. The `fullPath` can still be used as a key to retrieve the untitled Document (via `getDocumentForPath()`/`getOpenDocumentForPath()`), but it will not point to a real location on disk and any attempts at direct file I/O will fail (though the regular `FILE_SAVE` command works). Use `Document.isUntitled()` to check if a Document is untitled.

**Working set events** - `"workingSetSort"` is now fired in all cases where the existing list items are reordered. There is no longer any need to listen for `"workingSetDisableAutoSorting"`.

New/Improved Extensibility APIs
-------------------------------
**Inline editors** - Quick Edit and Quick Docs providers may now specify a priority to override other providers, including the default providers in Brackets core. See new arguments to `EditorManager.registerInlineEditProvider()` and `registerInlineDocsProvider()`.


Known Issues
------------
* This build _does not support Mac OS 10.6 (Snow Leopard)_. We are hoping to restore 10.6 support very soon (see [#4394](https://github.com/brackets-cont/brackets/issues/4394)).
* Mountain Lion (OS X 10.8) by default will not allow Brackets to run since it's not digitally signed yet. To work around this, right click the Brackets app and choose Open. You only need to do that once -- afterward, launching Brackets the normal way will work also.
* [#2272](https://github.com/brackets-cont/brackets/issues/2272): Windows Vista may not allow the Brackets installer to run (you may not see _any_ error message). To work around this, right-click the installer file, choose Properties, and click the Unblock button.
* [#3207](https://github.com/brackets-cont/brackets/issues/3207): If you use a Sprint 21 or earlier build after using this build at least once, a few preferences such as Recent Projects may get reset. (You can back up your [[cache folder]] if you're concerned about this).
* [#4362](https://github.com/brackets-cont/brackets/issues/4362): Slow startup of Brackets and Live Preview on Windows due to Chrome proxy settings. See workaround https://support.google.com/chrome/answer/106010?hl=en.
* _Debug > Run Tests_ is disabled in the installer/DMG distributions of Brackets, because the unit test code is not included. To run unit tests, [pull Brackets from GitHub](https://github.com/brackets-cont/brackets/wiki/How-to-Hack-on-Brackets#wiki-getcode) instead.

#### Pulling source code from Git
* If you use Brackets from the GitHub source, you should run `git submodule sync` before running `git submodule update`. This ensures you have the correct versions of all submodules.
* A new brackets-shell build _is_ required for this sprint. Be sure to rerun `grunt setup` before building.


Community contributions to Brackets
-----------------------------------
* [Exclude obvious binary file types from Quick Open, Find in Files, etc.](https://github.com/brackets-cont/brackets/pull/4442) by [Mikhail Shevchuk](https://github.com/shevchuk)
* [Enable toggle line/block comment in Groovy](https://github.com/brackets-cont/brackets/pull/4346) by [Arturo Elias](https://github.com/arturoeanton)
* [Enable basic syntax coloring for .NET files .aspx, .cshtml, .asax, .ashx, .config](https://github.com/brackets-cont/brackets/pull/4449) by [Ricky Abell](https://github.com/RickyAbell)
* [Enable syntax coloring for Python .wsgi files](https://github.com/brackets-cont/brackets/pull/4431/files) by [Globex Designs](https://github.com/globexdesigns)
* [Fix #4332: Locale-aware filename sorting in file tree](https://github.com/brackets-cont/brackets/pull/4463) by [Tomás Malbrán](https://github.com/TomMalbran)
* [Fix #4409: Sort order of "Untitled-NN" filenames should match OS](https://github.com/brackets-cont/brackets/pull/4524) by [Tomás Malbrán](https://github.com/TomMalbran)
* [Fix #4333: Paths containing "#" are mishandled](https://github.com/brackets-cont/brackets/pull/4379) by [Arzhan "kai" Kinzhalin (Intel Corporation)](https://github.com/busykai)
* [Fix #2076: Simplify events fired when working set is reordered](https://github.com/brackets-cont/brackets/pull/4450) by [Tomás Malbrán](https://github.com/TomMalbran)
* [Fix #4390: Change dialog box message container from \<p> to \<div>](https://github.com/brackets-cont/brackets/pull/4416) by [Hoshi Chigurh](https://github.com/Chigurh)
* [Fix #3985: Error messages related to New Folder say "file" instead of "folder"](https://github.com/brackets-cont/brackets/pull/4244) by [Daniel Seymour](https://github.com/DaBungalow)
* [Fix #4453: "{0}" appears in filename error dialog](https://github.com/brackets-cont/brackets/pull/4491) by [Tomás Malbrán](https://github.com/TomMalbran)
* [Remove File > New Folder menu item to avoid confusion](https://github.com/brackets-cont/brackets/pull/4488) (remains in context menu) by [Daniel Seymour](https://github.com/DaBungalow)
* [Move File > Live Highlight to View menu to avoid confusion](https://github.com/brackets-cont/brackets/pull/4395) by [Hoshi Chigurh](https://github.com/Chigurh)
* [Cleanup: Refactor inline JS out of index.html](https://github.com/brackets-cont/brackets/pull/4374) by [Maksim Lin](https://github.com/maks)
* [Cleanup: Move JSLint into a submodule](https://github.com/brackets-cont/brackets/pull/4467) by [Tomás Malbrán](https://github.com/TomMalbran)
* [Readme improvements](https://github.com/brackets-cont/brackets/pull/4375) by [Tom Byrer](https://github.com/tomByrer)
* [Linux setup changes for building brackets-shell](https://github.com/brackets-cont/brackets-shell/pull/275) by [Tim Burgess](https://github.com/timburgess)
* [Czech translation update](https://github.com/brackets-cont/brackets/pull/4278) by [kvarel](https://github.com/kvarel)
* [Brazilian Portuguese translation tweaks](https://github.com/brackets-cont/brackets/pull/4396) by [Michael Lancaster](https://github.com/weblancaster)
* [Fix Turkish translation typo](https://github.com/brackets-cont/brackets/pull/4356) by [Mahmut Bulut](https://github.com/vertexclique)

Contributions _from_ the Brackets community
-------------------------------------------

Bugs fixed in Sprint 28
-----------------------
For details on the bugs addressed, please refer to [closed sprint 28 bugs](https://github.com/brackets-cont/brackets/issues?labels=&milestone=15&state=closed). A few of the fixed bugs might not be caught by this search query, however.