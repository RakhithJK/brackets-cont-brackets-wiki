_This is a draft!_
--------------------
_This document will not be finalized until the end of Sprint 25 -- approximately May 21._

What's New in Sprint 25
-----------------------
* **Live Preview**
    * [Improved connection reliability](https://trello.com/card/2-live-development-improve-launching-chrome-on-win/4f90a6d98f77505d7940ce88/835) on Windows: no longer need to restart Chrome.
* **Extensions**
    * [Extension managemer](https://trello.com/card/2-extension-listing-remove-manage/4f90a6d98f77505d7940ce88/815): Listing of your currently installed extensions. Easier to uninstall extensions.
* **Code Editing**
    * [Improved typing performance](https://trello.com/card/3-research-rendering-typing-performance/4f90a6d98f77505d7940ce88/860): _MAYBE_


_Full change logs:_ [brackets](https://github.com/adobe/brackets/compare/sprint-24...sprint-25#commits_bucket) and [brackets-shell](https://github.com/adobe/brackets-shell/compare/sprint-24...sprint-25#commits_bucket)


UI Changes
----------
No major changes to existing features.


API Changes
-----------

New/Improved Extensibility APIs
-------------------------------

Known Issues
------------
* [#3458](https://github.com/adobe/brackets/issues/3458): Quick View does not yet support the latest CSS gradient syntax (using `to` keyword, unprefixed `radial-gradient`, `repeating-linear-gradient` or `repeating-radial-gradient`).
* [#3207](https://github.com/adobe/brackets/issues/3207): If you use a Sprint 21 or earlier build after using this build at least once, a few preferences such as Recent Projects may get reset. (You can back up your [[cache folder]] if you're concerned about this).
* Mountain Lion (OS X 10.8) by default will not allow Brackets to run since it's not digitally signed yet.  To work around this, right click the Brackets app and choose Open.  You only need to do that once -- afterward, launching Brackets the normal way will work also.
* [#2272](https://github.com/adobe/brackets/issues/2272): Windows Vista may not allow the Brackets installer to run (you may not see _any_ error message). To work around this, right-click the installer file, choose Properties, and click the Unblock button.
* _Debug > Run Tests_ is disabled in the installer/DMG distributions of Brackets, because the unit test code is not included. To run unit tests, [pull Brackets from GitHub](https://github.com/adobe/brackets/wiki/How-to-Hack-on-Brackets#wiki-getcode) instead.
* [#3570](https://github.com/adobe/brackets/issues/3570): Mac only - Quick View popover may not appear after resizing window or going fullscreen. Move the mouse to the top of the screen to fix.

Community contributions to Brackets
-----------------------------------

Contributions _from_ the Brackets community
-------------------------------------------
**Contributions to [CodeMirror](https://github.com/marijnh/CodeMirror):**
* ...

Bugs fixed in Sprint 25
-----------------------
For details on the bugs addressed, please refer to [closed sprint 25 bugs](https://github.com/adobe/brackets/issues?labels=&milestone=12&state=closed). A few of the fixed bugs might not be caught by this search query, however.