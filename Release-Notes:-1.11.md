What's New in Release 1.11
-------------------------

*  **[Support for ECMAScript 2015](https://github.com/brackets-cont/brackets/pull/13635)** by [swmitra](https://github.com/swmitra) :
Brackets now supports ECMAScript 2015. Quick-type listing now shows classes, methods, arrow functions, generator functions and much more. Brackets also supports linting of ECMAScript 2015 code, with ESLint defaulting as Javascript linter, as well.
 
*  **[Brackets on Linux](https://github.com/brackets-cont/brackets-shell/pull/619)** by [nethip](https://github.com/nethip) :
Brackets now offers full support for the Linux platform. With an update to the shell with a new version of CEF, Brackets is now fully functional on Linux.
 

_Full change logs:_ [brackets](https://github.com/brackets-cont/brackets/compare/release-1.10...release#commits_bucket) and [brackets-shell](https://github.com/brackets-cont/brackets-shell/compare/release-1.10...release#commits_bucket)



Community contributions to Brackets
-----------------------------------
* [Fix lgtm alerts](https://github.com/brackets-cont/brackets/pull/13483) by [xiemaisi](https://github.com/xiemaisi)
* [Fix extension registry link in README.md](https://github.com/brackets-cont/brackets/pull/13583) by [PikadudeNo1](https://github.com/PikadudeNo1)
* [Fix CTRL+Space handling while the CodeHintList is open](https://github.com/brackets-cont/brackets/pull/13560) by [petetnt](https://github.com/petetnt)
* [Update strings.js [Croatian]](https://github.com/brackets-cont/brackets/pull/13571) by [diomed](https://github.com/diomed)
* [On Windows force a 32 bit build until nodejs 64 bit is supported](https://github.com/brackets-cont/brackets/pull/13384) by [ficristo](https://github.com/ficristo)
* [Fixes wrong function call in ProjectManager.js](https://github.com/brackets-cont/brackets/pull/13611) by [hkirat](https://github.com/hkirat)
* [Fix typos [Croatian]](https://github.com/brackets-cont/brackets/pull/13628) by [dbaric](https://github.com/dbaric)
* ["Getting Started" page in ukrainian language](https://github.com/brackets-cont/brackets/pull/13397) by [yarik-vv](https://github.com/yarik-vv)
* [- add: doubleclick on search result header closes search results window](https://github.com/brackets-cont/brackets/pull/13624) by [lukaszsobek](https://github.com/lukaszsobek)
* [Add mapping for stylus mode in LanguageManager](https://github.com/brackets-cont/brackets/pull/13380) by [opl-](https://github.com/opl-)
* [Now reverse inspect can be disabled by setting the 'livedev.enableReverseInspect' pref to false](https://github.com/brackets-cont/brackets/pull/13659) by [saurabh95](https://github.com/saurabh95)
* [Upgrade brackets-eslint to 3.2.0](https://github.com/brackets-cont/brackets/pull/13717) by [ficristo](https://github.com/ficristo)


#### Pulling source code from Git
_TODO: any brackets-shell updates? which of the below messages are applicable?_

* A new brackets-shell build is _required_ for this sprint. Be sure to rerun `grunt setup` before building.
* Recommended: rebuild or reinstall an updated brackets-shell (no critical updates, but there are bugfixes).
* Rebuilding/updating brackets-shell is _optional_ for this release.
* Rebuilding/updating brackets-shell is _not_ required for this release.
* brackets-shell's Node dependencies have changed. Run `npm install` before rebuilding brackets-shell.
* Some submodules were updated this sprint. Run `git submodule update` to ensure your source tree is fully up to date.
* A submodule _URL_ was changed this sprint. Run `git submodule sync` and _then_ `git submodule update --init --recursive` to ensure your local source tree reflects the update.


Bugs fixed in Release 1.11
-------------------------
For details on the bugs addressed, please refer to [closed Release 1.11 bugs](https://github.com/brackets-cont/brackets/issues?q=is%3Aclosed+milestone%3A%22Release+1.11%22). Not all fixed bugs will be caught by this search query, however.