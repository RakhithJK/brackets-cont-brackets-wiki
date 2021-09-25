What's New in Sprint 38
-----------------------
* **Multiple Cursors**
    * **[Multiple cursor / multiple selection support](https://trello.com/c/g58aNzCz/1187-finish-multiple-selection-multiple-cursor-support)**, including...
    * Ctrl/Cmd-click or drag to create multiple cursors/selections
    * Alt-drag to create a rectangular selection (add Ctrl/Cmd to select multiple rectangles)
    * Ctrl/Cmd-U to undo selection/cursor changes (add Shift to navigate forward in cursor history)
    * Ctrl/Cmd-B to add a new selection at the next occurrence of a word or selected text. Shift-Ctrl/Cmd-B to skip an occurrence and add a selection on the next one. Alt-F3 or Cmd-Ctrl-G to add _all_ occurrences as selections at once.
    * [Read the full documentation for details](https://github.com/brackets-cont/brackets/wiki/Working-with-Multiple-Selections).
* **Linting**
    * [Support asynchronous linting](https://github.com/brackets-cont/brackets/pull/6530): Linters that require reading extra files from disk or talking to network services can now integrate with the standard Brackets linting UI.
* **Search**
    * [Improved usability of file/folder exclusions](https://github.com/brackets-cont/brackets/pull/7400): Filter editor displays how many files are left after filtering. Search shows warning if filter excludes all files in subtree. Filters disabled when searching only a single file.
    * [Improved performance on Windows](https://github.com/brackets-cont/brackets/pull/7290) if large binary files exist in the project
* **Files and Folders**
    * [File tree expand/collapse shortcuts](https://github.com/brackets-cont/brackets/pull/7026/files): Ctrl/Cmd-click to expand/collapse all siblings; Ctrl/Cmd-Alt-click to collapse subtree.
* **Image Preview**
    * [View .ico files](https://github.com/brackets-cont/brackets/pull/7201), e.g. often used as website "favicon"
* **Overall UI**
    * [Visual polish, subtle animations added](https://github.com/brackets-cont/brackets/pull/5921)
* **Localization**
    * [UK English locale added](https://github.com/brackets-cont/brackets/pull/7333)
    * Process change: translation pull requests should include which SHA (commit) the update is based on.  [See localization README for details](https://github.com/brackets-cont/brackets/blob/master/src/nls/README.md).
* **Ongoing Research** (not implemented yet)
    * [Research: JS Code Hints Cleanup](https://trello.com/c/heHZlATB/1158-research-js-code-hints-cleanup): Investigate how to simplify the code, improve performance & maintainability, and unify with new preferences system.
    * [Research: Improved LESS support](https://trello.com/c/qv5gTqXp/1163-s-research-early-less-support): Investigate support for Live Preview, Quick Edit, and Quick Find Definition with LESS code.

_Full change logs:_ [brackets](https://github.com/brackets-cont/brackets/compare/sprint-37...sprint-38#commits_bucket) and [brackets-shell](https://github.com/brackets-cont/brackets-shell/compare/sprint-37...sprint-38#commits_bucket)


UI Changes
----------
**Find in Files** - If you've set a [file/folder exclusion filter](https://github.com/brackets-cont/brackets/wiki/Using-File-Filters) and then you use 'Find In...' on a single file, filtering is temporarily disabled to ensure the file is always searched.


API Changes
-----------
**CodeMirror v4 & multiple cursors/selections** - See the **[[Brackets CodeMirror v4 Migration Guide]]**. Notably, referencing `CodeMirror` as a global identifier is now deprecated; use Require instead, as with other modules.

**PHP files** - `Editor.getLanguageForSelection()` will now return the correct `"php"` language (instead of the generic `"clike"`).

New/Improved Extensibility APIs
-------------------------------
**Inline Editors** - When a provider has nothing to show for the current cursor position, it can return an explanation string instead of just `null`. If no providers respond, the explanation is shown in a popup. This can help make inline editing functionality more discoverable to users.

**LanguageManager** - If a file extension already has a default Language mapping in Brackets, an extension can unregister the mapping in order to use it with a new Language. (For example, changing ".twig" from generic HTML highlighting to a new Twig-specific highlighting mode). Use `Language.removeFileExtension()` and `removeFileName()`.

In addition, all the add/remove file name/extension APIs can now optionally be passed an array of items instead of a single item.

**Editor** - All `get*` and `set*` methods for Editor settings now take an optional path parameter to get setting for a particular file. If omitted, then the current document is used. The `set*` methods also now return a boolean value which indicates whether value is valid.

**Jump to Definition** - use `EditorManager.registerJumpToDefProvider()` to register a provider for the _Navigate > Jump to Definition_ command.


Known Issues
------------
* "Brackets Code Folding" extension causes extremely slow typing in HTML files with this release. [Track this extension bug for updates](https://github.com/thehogfather/brackets-code-folding/issues/55).
* Brackets may crash or freeze on projects using the **Ionic** framework. [Exclude](https://github.com/brackets-cont/brackets/wiki/JavaScript-Code-Hints#configuration) the framework JS files to avoid this (they will be automatically excluded in Sprint 39).
* Activity Monitor in Mavericks (OS X 10.9) says the Brackets Helper process is "Not Responding" even when it's working normally ([#5794](https://github.com/brackets-cont/brackets/issues/5794)). You can safely ignore this unless Brackets is actually failing to respond when you click or type text.
* On Windows XP, Brackets will not detect external file changes instantly. It behaves similarly to Sprint 35 and earlier releases - changes are detected upon window activation, and the folder tree must be manually refreshed.
* [#2272](https://github.com/brackets-cont/brackets/issues/2272): Windows Vista may not allow the Brackets installer to run (you may not see _any_ error message). To work around this, right-click the installer file, choose Properties, and click the Unblock button.
* [#4362](https://github.com/brackets-cont/brackets/issues/4362): Slow startup of Brackets and Live Preview on Windows due to Chrome proxy settings. [See workaround](https://support.google.com/chrome/answer/106010?hl=en).
* _Debug > Run Tests_ is disabled in the installer/DMG distributions of Brackets, because the unit test code is not included. To run unit tests, [pull Brackets from GitHub](https://github.com/brackets-cont/brackets/wiki/How-to-Hack-on-Brackets#wiki-getcode) instead.
* [#7127](https://github.com/brackets-cont/brackets/issues/7127): With Chrome 34, using Live Preview will show a console error: "'CSS.getAllStyleSheets' wasn't found". This is harmless and shouldn't affect Live Preview.


Community contributions to Brackets
-----------------------------------
* [Support asynchronous linting / code inspection providers](https://github.com/brackets-cont/brackets/pull/6530) by [Arzhan "kai" Kinzhalin (Intel Corp)](https://github.com/busykai)
* [New preference: allow scrolling past the end of file](https://github.com/brackets-cont/brackets/pull/7142) by [Tomás Malbrán](https://github.com/TomMalbran)
* [Added 'Collapse File Tree' feature](https://github.com/brackets-cont/brackets/pull/7026) by [Martin Zagora](https://github.com/zaggino)
* [Select only filename (not extension) when renaming](https://github.com/brackets-cont/brackets/pull/7209) by [Robo210](https://github.com/Robo210)
* [Refinement: select only filename even with multi-part extensions](https://github.com/brackets-cont/brackets/pull/7242) by [Martin Zagora](https://github.com/zaggino)
* [Preview .ico files in Brackets](https://github.com/brackets-cont/brackets/pull/7201) by [Marcel Gerber](https://github.com/SAPlayer)
* [New Brackets-logo spinner icon](https://github.com/brackets-cont/brackets/pull/7304) by [Marcel Gerber](https://github.com/SAPlayer)
* [Fix: JSLint didn't respect tab size setting when Tab char enabled](https://github.com/brackets-cont/brackets/pull/7243) by [Martin Zagora](https://github.com/zaggino)
* [Fix: Inline bezier editor error didn't reappear after editing during fadeout](https://github.com/brackets-cont/brackets/pull/7235) ([and](https://github.com/brackets-cont/brackets/pull/7248)) by [Marcel Gerber](https://github.com/SAPlayer)
* [Accept string id in `PreferencesManager.convertPreferences()`, not just module object](https://github.com/brackets-cont/brackets/pull/7415) by [Marcel Gerber](https://github.com/SAPlayer)
* [Allow extensions to load LESS files that use `@import` _(Win only for now)_](https://github.com/brackets-cont/brackets/pull/7230) by [Martin Zagora](https://github.com/zaggino)
* [Fix shift in document scroll position when reloading Brackets with non-default font size](https://github.com/brackets-cont/brackets/pull/7185) by [Tomás Malbrán](https://github.com/TomMalbran)
* [Fix: No `"fontSizeChange"` event from Restore Font Size command](https://github.com/brackets-cont/brackets/pull/7443) by [Lance Campbell](https://github.com/lkcampbell)
* [Fix: Async.PromiseQueue halts if any promise rejects](https://github.com/brackets-cont/brackets/pull/7407) by [jayther](https://github.com/jayther)
* [Fix: Restore the correct selections after Toggle Line Comment](https://github.com/brackets-cont/brackets/pull/7301) by [Marcel Gerber](https://github.com/SAPlayer)
* [Fix issues with Close Others context menu preferences](https://github.com/brackets-cont/brackets/pull/7088) by [Tomás Malbrán](https://github.com/TomMalbran)
* [Green Update buttons in Extension Manager - easier to spot](https://github.com/brackets-cont/brackets/pull/6315) by [Matt Stow](https://github.com/stowball)
* [Fix: Clicking update icon in Extension Manager tab doesn't select tab](https://github.com/brackets-cont/brackets/pull/7287) by [Olgierd Grzyb](https://github.com/winek)
* [Fix console warning spam for external changes inside .git folder](https://github.com/brackets-cont/brackets/pull/7332) by [Martin Zagora](https://github.com/zaggino)
* [Highlight Streamlinejs files (._js, ._coffee) as plain JS/CoffeScript](https://github.com/brackets-cont/brackets/pull/7050) by [Drew Fyock](https://github.com/fyockm)
* [Recognize .xsl files as XML](https://github.com/brackets-cont/brackets/pull/7210) by [Gideon Goldberg](https://github.com/gidsg)
* [Recognize .jshintrc & .bowerrc as JSON, and Guardfile as Ruby](https://github.com/brackets-cont/brackets/pull/7249) by [Diego Leme](https://github.com/diegoleme)
* [Fix Grunt build error in case-sensitive file systems](https://github.com/brackets-cont/brackets/pull/7253) by [Alain Kalker](https://github.com/ackalker)
* [Add English (UK) language distinct from English (US)](https://github.com/brackets-cont/brackets/pull/7333) (no specific localizations yet though) by [Martin Zagora](https://github.com/zaggino)
* [Simplified Chinese translation update](https://github.com/brackets-cont/brackets/pull/7259) by [peterfyj](https://github.com/peterfyj)
* [Czech translation update](https://github.com/brackets-cont/brackets/pull/7260) by [kvarel](https://github.com/kvarel)
* [Italian translation update](https://github.com/brackets-cont/brackets/pull/7429) by [Francesco Borzì](https://github.com/ShinDarth)
* [Italian translation update](https://github.com/brackets-cont/brackets/pull/7468) by [Denisov21](https://github.com/Denisov21)
* [German translation update](https://github.com/brackets-cont/brackets/pull/7468) by [Marcel Gerber](https://github.com/SAPlayer)
* [Spanish translation update](https://github.com/brackets-cont/brackets/pull/7479) by [Tomás Malbrán](https://github.com/TomMalbran)
* [Swedish translation update](https://github.com/brackets-cont/brackets/pull/7487) by [Mikael Jorhult](https://github.com/mikaeljorhult)
* [Nicer apostrophes in French & Italian translations](https://github.com/brackets-cont/brackets/pull/7369) by [Fez Vrasta](https://github.com/FezVrasta)
* [Update Commands.js docs for preferences toggle handlers](https://github.com/brackets-cont/brackets/pull/7323) by [Lance Campbell](https://github.com/lkcampbell)

#### Pulling source code from Git
* A new brackets-shell build is _not_ needed for this sprint.
* Git submodules were updated this sprint. Run `git submodule update` to ensure your source tree is fully up to date.

Bugs fixed in Sprint 38
-----------------------
For details on the bugs addressed, please refer to [closed sprint 38 bugs](https://github.com/brackets-cont/brackets/issues?labels=&milestone=25&state=closed). Not all fixed bugs will be caught by this search query, however.