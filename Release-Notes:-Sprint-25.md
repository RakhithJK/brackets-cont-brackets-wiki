What's New in Sprint 25
-----------------------
* **Live Preview**
    * [Improved connection reliability](https://trello.com/card/2-live-development-improve-launching-chrome-on-win/4f90a6d98f77505d7940ce88/835): No longer need to restart Chrome on Windows. If the Live Preview connection is lost, Brackets gives the reason why.
* **Extensions**
    * [Extension manager](https://trello.com/card/2-extension-listing-remove-manage/4f90a6d98f77505d7940ce88/815): Listing of your currently installed extensions. Easier to uninstall extensions.
* **File Management**
    * [Refresh file tree](https://github.com/brackets-cont/brackets/pull/3370): Right-click on the file tree and choose Refresh to update the file list from disk &ndash; no need to restart Brackets. (This is a stopgap along the way to [fully automatic refresh](https://trello.com/card/8-file-directory-watching/4f90a6d98f77505d7940ce88/292), which will come further down the road).
    * [Delete file/folder](https://github.com/brackets-cont/brackets/pull/3879): Right-click in the file tree an choose Delete to move a file or entire folder to the trash.
    * [Show file/folder in OS](https://github.com/brackets-cont/brackets/pull/2128): Right-click in the file tree or working files list and choose Show in OS to show a file or folder in Windows Explorer or Mac Finder.
* **Search**
    * [Faster, more accurate Quick Edit for JavaScript](https://github.com/brackets-cont/brackets/pull/3847): Now using the [Tern code intelligence engine](http://ternjs.net/) that powers code hints and Jump to Definition.
* **Code Editing**
    * Many bug fixes in JavaScript code hinting
    * [Improved typing performance](https://trello.com/card/3-research-rendering-typing-performance/4f90a6d98f77505d7940ce88/860): Brackets responds to keypresses 21% faster in JavaScript code and 13% faster in general (fixed [unneeded repaints](https://github.com/marijnh/CodeMirror/issues/1514) and optimized code hint popup creation).


_Full change logs:_ [brackets](https://github.com/brackets-cont/brackets/compare/sprint-24...sprint-25#commits_bucket) and [brackets-shell](https://github.com/brackets-cont/brackets-shell/compare/sprint-24...sprint-25#commits_bucket)


UI Changes
----------
New visual design for Quick Open / Quick Find Definition, JSLint panel, and Find in Files results panel.


API Changes
-----------
**Extension package format** - _All extensions should now include a **package.json file**_ with descriptive metadata. See [[Extension package format]] for details. Extensions that omit package.json will still work, but won't look very nice in the new Extension Manager dialog. (Down the road, package.json will become required though).

**Adding panels** -
* To add a resizable panel below the editor, use `PanelManager.createBottomPanel()`. The previous approach (insert DOM node manually, then call `Resizer.makeResizable()`) still works, but is deprecated.
* To show/hide a panel, use Resizer's APIs or the Panel object returned by PanelManager. Again, the old approach (call jQuery `show()`/`hide()`, then call `EditorManager.resizeEditor()`) still works for now, but is deprecated.

**ProjectManager** - Previously, `ProjectManager.getSelectedItem()` returned null when the selection highlight was in the working set instead of the file tree. Now it returns whatever file/folder is selected _anywhere_ in the sidebar (working set _or_ file tree). (Note that is may still return null in some cases when a current document is open - for example if a Find in Files result was clicked and the opened file is not visible anywhere in the sidebar, the sidebar will have no selection).

**QuickOpen** - The search heuristic no longer automatically applies special weighting when items look like a path. Quick Open providers can switch back to the path-oriented behavior by supplying `matcherOptions: { segmentedSearch: true }` in the settings passed to `addQuickOpenPlugin()`.

**Sidebar show/hide** - `SidebarView.toggleSidebar()` was renamed to `toggle()`. Added new `show()`, `hide()`, and `isVisible()` methods.

New/Improved Extensibility APIs
-------------------------------
**QuickOpen / StringMatch** - In addition to the `segmentedSearch` option described above, Quick Open providers can also specify `matcherOptions: { preferPrefixMatches: true }` to give additional weighting when the search text is an exact prefix of some results. The same options can be passed to the raw StringMatch API as a constructor argument. (Prefix weighting is useful for sorting code hint matches, for example &ndash; which would typically use a raw StringMatcher for sorting).

**Font size event** - `ViewCommandHandlers` dispatches a `"fontSizeChange"` event whenever the editor font size is changed by the user.

**showOSFolder()** - The existing `brackets.app.showOSFolder()` API can now be passed a file instead of a folder. It will open the containing folder with that file pre-selected.


Known Issues
------------
* Mountain Lion (OS X 10.8) by default will not allow Brackets to run since it's not digitally signed yet. To work around this, right click the Brackets app and choose Open. You only need to do that once -- afterward, launching Brackets the normal way will work also.
* [#2272](https://github.com/brackets-cont/brackets/issues/2272): Windows Vista may not allow the Brackets installer to run (you may not see _any_ error message). To work around this, right-click the installer file, choose Properties, and click the Unblock button.
* [#3458](https://github.com/brackets-cont/brackets/issues/3458): Quick View does not yet support the latest CSS gradient syntax (using `to` keyword, unprefixed `radial-gradient`, `repeating-linear-gradient` or `repeating-radial-gradient`).
* [#3570](https://github.com/brackets-cont/brackets/issues/3570): Mac only - Quick View popover may not appear after resizing window or going fullscreen. Move the mouse to the top of the screen to fix.
* [#3207](https://github.com/brackets-cont/brackets/issues/3207): If you use a Sprint 21 or earlier build after using this build at least once, a few preferences such as Recent Projects may get reset. (You can back up your [[cache folder]] if you're concerned about this).
* _Debug > Run Tests_ is disabled in the installer/DMG distributions of Brackets, because the unit test code is not included. To run unit tests, [pull Brackets from GitHub](https://github.com/brackets-cont/brackets/wiki/How-to-Hack-on-Brackets#wiki-getcode) instead.


Community contributions to Brackets
-----------------------------------
* [Make JSLint error messages selectable in JSLint panel](https://github.com/brackets-cont/brackets/pull/3688) by [Jeffrey Fisher](https://github.com/jeffslofish)
* [Color-code Handlebars .hbs files as HTML](https://github.com/brackets-cont/brackets/pull/3699) by [Thomas Carlsen](https://github.com/tcarlsen)
* [Color-code Kit .kit files as HTML](https://github.com/brackets-cont/brackets/pull/3809) by [Tucker Whitehouse](https://github.com/TuckerWhitehouse)
* [Color-code Embedded JS .ejs & Java .jsp files as HTML](https://github.com/brackets-cont/brackets/pull/3809) by [Tucker Whitehouse](https://github.com/TuckerWhitehouse)
* [Fix #3723: Allow replacing non-multi-line selection with Tab character](https://github.com/brackets-cont/brackets/pull/3759) by [Jeffrey Fisher](https://github.com/jeffslofish)
* [Fix #3679: File extension isn't color-coded if created via File > New](https://github.com/brackets-cont/brackets/pull/3690) by [Rajesh Segu](https://github.com/rajeshsegu)
* [Restore useful error messages when addMenuItem() is passed bad arguments](https://github.com/brackets-cont/brackets/pull/3611) by [Tomás Malbrán](https://github.com/TomMalbran)
* [Fix #3637: Incorrect selection indicator after loading Brackets with sidebar hidden](https://github.com/brackets-cont/brackets/pull/3719) by [Jeffrey Fisher](https://github.com/jeffslofish)
* [Partial fix for #3478: 1px top border sometimes appears on search result highlight](https://github.com/brackets-cont/brackets/pull/3568) by [Tomás Malbrán](https://github.com/TomMalbran)
* [Fix #3773: Only show '"The maximum number of files have been indexed' error once per project (per session)](https://github.com/brackets-cont/brackets/pull/3783) by [dschaffe](https://github.com/dschaffe)
* [Fix incorrect plural in statusbar for 1-line files](https://github.com/brackets-cont/brackets/pull/3584) by [Tomás Malbrán](https://github.com/TomMalbran)
* [Speed improvement to CollectionUtils.hasOwnProperty()](https://github.com/brackets-cont/brackets/pull/3687) by [Rajesh Segu](https://github.com/rajeshsegu)
* [Add ViewCommandHandlers "fontSizeChange" event](https://github.com/brackets-cont/brackets/pull/3787) by [Lance Campbell](https://github.com/lkcampbell)
* [Add cleaner APIs for sidebar panel: isVisibile(), show(), hide()](https://github.com/brackets-cont/brackets/pull/3297) ([and](https://github.com/brackets-cont/brackets/pull/3876)) by [Lance Campbell](https://github.com/lkcampbell)
* [Cleanup: Use Mustache templates for some of the Debug commands' UI](https://github.com/brackets-cont/brackets/pull/3336) by [Tomás Malbrán](https://github.com/TomMalbran)
* [Cleanup: Upgrade Mustache version](https://github.com/brackets-cont/brackets/pull/3693) by [Bernhard Sirlinger](https://github.com/WebsiteDeveloper)
* [Cleanup: Use submodules for RequireJS text & i18n plugins](https://github.com/brackets-cont/brackets/pull/3680) by [Tucker Whitehouse](https://github.com/TuckerWhitehouse)
* [Cleanup: Stop using jQuery.toggleClass() due to argument type bug-proneness](https://github.com/brackets-cont/brackets/pull/3689) by [Bernhard Sirlinger](https://github.com/WebsiteDeveloper)
* [Cleanup: Stop using deprecated Promise.isResolved()/isRejected()](https://github.com/brackets-cont/brackets/pull/3665) by [Tucker Whitehouse](https://github.com/TuckerWhitehouse)
* [Cleanup: Stop using deprecated CodeMirror token.className](https://github.com/brackets-cont/brackets/pull/3697) by [Jeffrey Fisher](https://github.com/jeffslofish)
* [Cleanup: Group strings used by default extensions](https://github.com/brackets-cont/brackets/pull/3575) by [Tomás Malbrán](https://github.com/TomMalbran)
* [Cleanup: Remove unused string](https://github.com/brackets-cont/brackets/pull/3586) by [Tomás Malbrán](https://github.com/TomMalbran)
* [Unit tests for HTML entity code hints](https://github.com/brackets-cont/brackets/pull/3524) ([and](https://github.com/brackets-cont/brackets/pull/3710)) by [Bernhard Sirlinger](https://github.com/WebsiteDeveloper)
* [Localize language names in Debug > Switch Language dropdown](https://github.com/brackets-cont/brackets/pull/3704) by [Tammo Pape](https://github.com/tammo)
* [Fix unlocalized string "pixels" in Quick View popup](https://github.com/brackets-cont/brackets/pull/3811) by [Kieran Gorman](https://github.com/kjgorman)
* [German translation update](https://github.com/brackets-cont/brackets/pull/3641) by [mynetx](https://github.com/mynetx)
* [Spanish translation update](https://github.com/brackets-cont/brackets/pull/3929) by [Chema Balsas](https://github.com/jbalsas)


Contributions _from_ the Brackets community
-------------------------------------------
**Contributions to [CodeMirror](https://github.com/marijnh/CodeMirror):**
* [CSS mode: record better info for @import directives](https://github.com/marijnh/CodeMirror/pull/1487) (enables Brackets URL hinting when typing an `@import`)
* [Don't continue line numbers next to horizontal scrollbar](https://github.com/marijnh/CodeMirror/pull/1493)
* [vim mode: Fix dialog box used for ':' commands](https://github.com/marijnh/CodeMirror/pull/1509)

**Contributions to [Tern](https://github.com/marijnh/tern):**
* [Fix capitalization error in jQuery API hint](https://github.com/marijnh/tern/pull/127)

Bugs fixed in Sprint 25
-----------------------
For details on the bugs addressed, please refer to [closed sprint 25 bugs](https://github.com/brackets-cont/brackets/issues?labels=&milestone=12&state=closed). A few of the fixed bugs might not be caught by this search query, however.