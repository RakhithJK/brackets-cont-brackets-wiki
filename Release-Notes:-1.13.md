What's New in Release 1.13
-------------------------
* [AutoUpdate Framework](https://github.com/brackets-cont/brackets/pull/14177) by [mbhavi](https://github.com/mbhavi) : You can now automatically update Brackets, without leaving the code editor.
* [Add drag and drop to move items in FileTreeView](https://github.com/brackets-cont/brackets/pull/13546) by [boopeshmahendran](https://github.com/boopeshmahendran) : You can now manipulate folder structure from within Brackets. Move a file/folder from one folder to another with a simple drag and drop.
* [Enable opening of remote(http|https) files in Brackets](https://github.com/brackets-cont/brackets/pull/14153) by [swmitra](https://github.com/swmitra) : You can now open a remotely hosted web-page from within Brackets. Use Ctrl/Cmd-Shift-O shortcut and supply a URL to quickly open the file and review the code within Brackets.


_Full change logs:_ [brackets](https://github.com/brackets-cont/brackets/compare/release-1.12...release-1.13#commits_bucket) and [brackets-shell](https://github.com/brackets-cont/brackets-shell/compare/release-1.12...release-1.13#commits_bucket)

Community contributions to Brackets
-----------------------------------

* [Fix for 13839: Crash on opening file with error "sharing violation".](https://github.com/brackets-cont/brackets-shell/pull/635) by [nethip](https://github.com/nethip)
* [Fix #13099: Disallow user to create files/folder using relative path](https://github.com/brackets-cont/brackets/pull/13256) by [sdalmeida](https://github.com/sdalmeida)
* [Issue #11261: keep the search bar open](https://github.com/brackets-cont/brackets/pull/14141) by [petetnt](https://github.com/petetnt)
* [Linux native menus checked entries](https://github.com/brackets-cont/brackets-shell/pull/633) by [pelatx](https://github.com/pelatx)
* [Bringing in ImmutableJS 3.8.2 ](https://github.com/brackets-cont/brackets/pull/14168) by [vickramdhawal](https://github.com/vickramdhawal)
* [Add 'onHighlight' optional event callback mechanisfor better extensibility features in hint providers](https://github.com/brackets-cont/brackets/pull/14140) by [swmitra](https://github.com/swmitra)
* [Fix layout issue in submenu](https://github.com/brackets-cont/brackets/pull/14073) by [boopeshmahendran](https://github.com/boopeshmahendran)
* [Fix to avoid window location change confirmation dialog while running tests - onbeforeunload conditional registration](https://github.com/brackets-cont/brackets/pull/14169) by [swmitra](https://github.com/swmitra)
* [Fix full screen window issue in multiple montiors](https://github.com/brackets-cont/brackets-shell/pull/638) by [sobisht](https://github.com/sobisht)
* [Linux native menus lost shortcuts](https://github.com/brackets-cont/brackets-shell/pull/637) by [pelatx](https://github.com/pelatx)
* [AutoUpdate Feature Health Data Logging Changes](https://github.com/brackets-cont/brackets-shell/pull/639) by [niteskum](https://github.com/niteskum)
* [Adding Analytics logging for JSRefactor, Live Preview, Quick Edit and more features](https://github.com/brackets-cont/brackets/pull/14253) by [sobisht](https://github.com/sobisht)
* [Disable GPU for Ubuntu18.04](https://github.com/brackets-cont/brackets-shell/pull/648) by [gautam0217](https://github.com/gautam0217)
* [Build fixes for Ubuntu18.04](https://github.com/brackets-cont/brackets-shell/pull/649) by [gautam0217](https://github.com/gautam0217)
* [Fixing issue 14163, F&R replaces all content of file when replacing new line](https://github.com/brackets-cont/brackets/pull/14175) by [navch](https://github.com/navch)
* [Fix Issue 14149 - Fixes Dns rebinding attack in CEF](https://github.com/brackets-cont/brackets-shell/pull/651) by [sabanaya](https://github.com/sabanaya)
* [Linux: Add a check for file exist when "Show in OS" is clicked](https://github.com/brackets-cont/brackets-shell/pull/650) by [sobisht](https://github.com/sobisht)


#### Pulling source code from Git
_TODO: any brackets-shell updates? which of the below messages are applicable?_

* A new brackets-shell build is _required_ for this sprint. Be sure to rerun `grunt setup` before building.
* Recommended: rebuild or reinstall an updated brackets-shell (no critical updates, but there are bugfixes).
* Rebuilding/updating brackets-shell is _optional_ for this release.
* Rebuilding/updating brackets-shell is _not_ required for this release.
* brackets-shell's Node dependencies have changed. Run `npm install` before rebuilding brackets-shell.
* Some submodules were updated this sprint. Run `git submodule update` to ensure your source tree is fully up to date.
* A submodule _URL_ was changed this sprint. Run `git submodule sync` and _then_ `git submodule update --init --recursive` to ensure your local source tree reflects the update.


Bugs fixed in Release 1.13
-------------------------
For details on the bugs addressed, please refer to [closed Release 1.13 bugs](https://github.com/brackets-cont/brackets/issues?q=is%3Aclosed+milestone%3A%22Release+1.13%22). Not all fixed bugs will be caught by this search query, however.