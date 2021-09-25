What's New in Sprint 24
-----------------------
* **Visual Editing**
    * [Quick View for colors, gradients, images](https://trello.com/card/2-hover-preview/4f90a6d98f77505d7940ce88/848): Hover over code to see a popup preview
    * [Quick Docs for CSS](https://trello.com/card/3-quick-docs-css/4f90a6d98f77505d7940ce88/839): Press Ctrl+K/&#x2318;K on a CSS property to see inline documentation from [WebPlatform.org](http://docs.webplatform.org/).
* **Code Editing**
    * [Supercharged JavaScript code hints](https://trello.com/card/2-pull-request-tern-based-code-hinting/4f90a6d98f77505d7940ce88/849): Greatly improved code hints based on [Tern](http://ternjs.net/) type inferencing. Increased code hinting accuracy, camelCase support and built-in intelligence for RequireJS and jQuery. Code hints even for items declared in other files!
    * [Jump to Definition](https://trello.com/card/2-pull-request-tern-based-code-hinting/4f90a6d98f77505d7940ce88/849): Locate a function or property definition anywhere in your project, instantly.
    * [Function argument / signature hints](https://trello.com/card/2-pull-request-tern-based-code-hinting/4f90a6d98f77505d7940ce88/849): Press Ctrl+Space inside a function call's `()`s to see information on its arguments and their types.
    * [Insert line above / below current line](https://github.com/brackets-cont/brackets/pull/2729): Press Ctrl+Enter/&#x2318;+Enter or Ctrl+Shift+Enter/&#x2318;+Shift+Enter to insert a blank line below or above the current line, respectively.
* **Overall UI**
    * [New project panel visual design](https://trello.com/card/2-ux-implement-project-panel/4f90a6d98f77505d7940ce88/807)


_Full change logs:_ [brackets](https://github.com/brackets-cont/brackets/compare/sprint-23...sprint-24#commits_bucket) and [brackets-shell](https://github.com/brackets-cont/brackets-shell/compare/sprint-23...sprint-24#commits_bucket)


UI Changes
----------
**Go to Definition** renamed to **Quick Find Definition** - This helps to distinguish it more clearly from the new "Jump to Definition" command:
* Jump to Definition - searches across all files based on the identifier at the cursor position.
* Quick Find Definition - searches within the current file for the identifier you type in the quick search bar.

**Project panel / folder tree** - In addition to the aesthetic changes, "Project Settings..." has been removed from the recent projects dropdown menu. It remains accessible via the File menu. For more on the design direction Brackets is headed in, [take look at this mockup](http://www.behance.net/gallery/Brackets/6499177).

**Install Extension shortcuts** - New toolbar icon provides quicker access to the Install Extension command, and the Install Extension dialog box contains a link to the [extensions listing page](https://github.com/brackets-cont/brackets/wiki/Brackets-Extensions).


API Changes
-----------
No known breaking changes to existing APIs.

New/Improved Extensibility APIs
-------------------------------
**Quick Docs** - To register an additional inline docs provider, use `EditorManager.registerInlineDocsProvider()`. Similar to inline editors (Quick Edit), Quick Docs providers are "winner take all": if two providers are both willing to respond for a given cursor position, the first one registered is shown and the other is completely ignored. To be a good citizen, your provider should be as narrowly tailored as is reasonably possible.

Known Issues
------------
* [#3709](https://github.com/brackets-cont/brackets/issues/3709): Using JavaScript code hints inside inline editors can lead to code getting inserted twice in the document.
* [#3458](https://github.com/brackets-cont/brackets/issues/3458): Quick View does not yet support the latest CSS gradient syntax (using `to` keyword, unprefixed `radial-gradient`, `repeating-linear-gradient` or `repeating-radial-gradient`).
* [#3207](https://github.com/brackets-cont/brackets/issues/3207): If you use a Sprint 21 or earlier build after using this build at least once, a few preferences such as Recent Projects may get reset. (You can back up your [[cache folder]] if you're concerned about this).
* Mountain Lion (OS X 10.8) by default will not allow Brackets to run since it's not digitally signed yet.  To work around this, right click the Brackets app and choose Open.  You only need to do that once -- afterward, launching Brackets the normal way will work also.
* [#2272](https://github.com/brackets-cont/brackets/issues/2272): Windows Vista may not allow the Brackets installer to run (you may not see _any_ error message). To work around this, right-click the installer file, choose Properties, and click the Unblock button.
* _Debug > Run Tests_ is disabled in the installer/DMG distributions of Brackets, because the unit test code is not included. To run unit tests, [pull Brackets from GitHub](https://github.com/brackets-cont/brackets/wiki/How-to-Hack-on-Brackets#wiki-getcode) instead.
* [#3570](https://github.com/brackets-cont/brackets/issues/3570): Mac only - Quick View popover may not appear after resizing window or going fullscreen. Move the mouse to the top of the screen to fix.

Community contributions to Brackets
-----------------------------------
* [Insert line above/below shortcuts](https://github.com/brackets-cont/brackets/pull/2729) by [Alessandro Di Martino](https://github.com/zeis)
* [Inline color editor: support percentage RGB colors](https://github.com/brackets-cont/brackets/pull/2212) by [Dennis Kehrig](https://github.com/DennisKehrig)
* [Highlight .tpl/.twig files (as plain HTML)](https://github.com/brackets-cont/brackets/pull/3362) by [niu tech](https://github.com/niutech)
* [Fix #3130: Move line up/down has incorrect behavior in edge cases in inline editor](https://github.com/brackets-cont/brackets/pull/3233) by [Tom Malbrán](https://github.com/TomMalbran)
* [Fix #3466: Brackets hangs if floating-point value entered for Tab/Spaces size](https://github.com/brackets-cont/brackets/pull/3487) by [Tom Malbrán](https://github.com/TomMalbran)
* [Fix #3440: Working set does not re-sort when automatic sort is turned on](https://github.com/brackets-cont/brackets/pull/3450) by [Tom Malbrán](https://github.com/TomMalbran)
* [Fix #1570: Quick Edit should work on closing tag](https://github.com/brackets-cont/brackets/pull/3419) by [Bernhard Sirlinger](https://github.com/WebsiteDeveloper)
* [Fix #3323: Reopening same folder closes all files](https://github.com/brackets-cont/brackets/pull/3329) by [Bernhard Sirlinger](https://github.com/WebsiteDeveloper)
* [Fix #2641: Input field goes blank if F2 pressed a second time](https://github.com/brackets-cont/brackets/pull/3299) by [Tom Malbrán](https://github.com/TomMalbran)
* [Fix #3041: Shortcuts using "-" are shown as "+" on Windows](https://github.com/brackets-cont/brackets/pull/3331) by [Bernhard Sirlinger](https://github.com/WebsiteDeveloper)
* [Add CollectionUtils.some() to allow breaking out of iteration](https://github.com/brackets-cont/brackets/pull/3117) by [Tom Malbrán](https://github.com/TomMalbran)
* [German translation update](https://github.com/brackets-cont/brackets/pull/2937) ([and](https://github.com/brackets-cont/brackets/pull/3500)) by [mynetx](https://github.com/mynetx)
* [Spanish translation update](https://github.com/brackets-cont/brackets/pull/3536) by [Chema Balsas](https://github.com/jbalsas)
* [Add YouTube link to README](https://github.com/brackets-cont/brackets/pull/3276) by [drdamour](https://github.com/drdamour)


Bugs fixed in Sprint 24
-----------------------
For details on the bugs addressed, please refer to [closed sprint 24 bugs](https://github.com/brackets-cont/brackets/issues?labels=&milestone=11&state=closed). A few of the fixed bugs might not be caught by this search query, however.