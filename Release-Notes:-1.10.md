What's New in Release 1.10
-------------------------

*  **[Multiple encoding support](https://github.com/brackets-cont/brackets/pull/13412)** by [saurabh95](https://github.com/saurabh95) :
Brackets now supports more than 40 different file encodings. You can now Open/Save files with different encodings.
 
*  **[Forward/Backward navigation in edit history](https://github.com/brackets-cont/brackets/pull/13418)** by [swmitra](https://github.com/swmitra) :
Navigate backward/forward using Alt-I, Alt-Shift-I across explicit cursor positions.
 
*  **[Enable/Disable default extensions](https://github.com/brackets-cont/brackets/pull/13136)** by [zaggino](https://github.com/zaggino) 
You can now enable/disable default extensions, that are shipped with Brackets.
 
*  **[Search History](https://github.com/brackets-cont/brackets/pull/13237)** by [saurabh95](https://github.com/saurabh95) :
Access all your most recently searched queries from the search bar. 
 
*  **[Native Menus for Linux](https://github.com/brackets-cont/brackets-shell/pull/602)** by [eyelash](https://github.com/eyelash) and [saurabh95](https://github.com/saurabh95) :
HTML menus are replaced with native menus in Linux.
 
*  **[@rule and pseudo-selector code hints](https://github.com/brackets-cont/brackets/pull/13295)** by [swmitra](https://github.com/swmitra) :
CSS code hints now support @rule and pseudo selector/element code hints. 
 
*  **[Inline CSS code hints](https://github.com/brackets-cont/brackets/pull/13270)** by [swmitra](https://github.com/swmitra) :
Brackets now provides CSS code hints in style attribute value in html.

*  **[Live Preview highlight customization](https://github.com/brackets-cont/brackets/pull/12949)** by [Worie](https://github.com/Worie) :
Live Preview highlight customization (colors of highlight can be customized via user preferences). This shows highlight with clear segregation of different box model layers.


_Full change logs:_ [brackets](https://github.com/brackets-cont/brackets/compare/release-1.9...release-1.10#commits_bucket) and [brackets-shell](https://github.com/brackets-cont/brackets-shell/compare/release-1.9...release-1.10#commits_bucket)



Known Issues
------------
* _Debug > Run Tests_ is disabled in the installer/DMG distributions of Brackets, because the unit test code is not included. To run unit tests, [pull Brackets from GitHub](https://github.com/brackets-cont/brackets/wiki/How-to-Hack-on-Brackets#wiki-getcode) instead.

* Navigate Backward/Forward feature would be available only as Navigate > menu items in OSX. We will enable keyboard shortcuts in next pre-release.

Community contributions to Brackets
-----------------------------------

* [Fix NavigationProvider throwing errors when doc.file is missing](https://github.com/brackets-cont/brackets/pull/13492) by [petetnt](https://github.com/petetnt)
* [zh-cn](https://github.com/brackets-cont/brackets/pull/13473) by [FallingHeart](https://github.com/FallingHeart)
* [Fixes translation error in Simplified Chinese](https://github.com/brackets-cont/brackets/pull/13463) by [mjaseem](https://github.com/mjaseem)
* [Update urls.js](https://github.com/brackets-cont/brackets/pull/13459) by [FallingHeart](https://github.com/FallingHeart)
* [In writeJSON (grunt), use CRLF on Windows](https://github.com/brackets-cont/brackets/pull/13458) by [MarcelGerber](https://github.com/MarcelGerber)
* [Small linting refactor](https://github.com/brackets-cont/brackets/pull/13452) by [horiaradu](https://github.com/horiaradu)
* [Use the correct border color in multifile Replace in Files bar with d…](https://github.com/brackets-cont/brackets/pull/13449) by [MarcelGerber](https://github.com/MarcelGerber)
* [Create index.html](https://github.com/brackets-cont/brackets/pull/13446) by [FallingHeart](https://github.com/FallingHeart)
* [German Translation](https://github.com/brackets-cont/brackets/pull/13436) by [MarcelGerber](https://github.com/MarcelGerber)
* [Fix root strings](https://github.com/brackets-cont/brackets/pull/13435) by [MarcelGerber](https://github.com/MarcelGerber)
* [Problems panel: add an icon per problem to tell which type it is](https://github.com/brackets-cont/brackets/pull/13430) by [ficristo](https://github.com/ficristo)
* [Various additions and changes to Swedish interface strings](https://github.com/brackets-cont/brackets/pull/13404) by [Lominean](https://github.com/Lominean)
* [Polish translation update for brackets 1.10](https://github.com/brackets-cont/brackets/pull/13398) by [karmatys](https://github.com/karmatys)
* [Release](https://github.com/brackets-cont/brackets/pull/13373) by [sharklaser2342345235](https://github.com/sharklaser2342345235)
* [fixing JP translation in comment tags](https://github.com/brackets-cont/brackets/pull/13363) by [ArturOledzki](https://github.com/ArturOledzki)
* [Fix box model regression (transform)](https://github.com/brackets-cont/brackets/pull/13357) by [Worie](https://github.com/Worie)
* [replace parseInt with parseFloat in RemoteFunctions (LP boxmodel fix)](https://github.com/brackets-cont/brackets/pull/13353) by [Worie](https://github.com/Worie)
* [Update CSS Code Hints pseudo-selectors](https://github.com/brackets-cont/brackets/pull/13345) by [valtlai](https://github.com/valtlai)
* [Update CSS Code Hints properties](https://github.com/brackets-cont/brackets/pull/13344) by [valtlai](https://github.com/valtlai)
* [Editor command handlers test](https://github.com/brackets-cont/brackets/pull/13337) by [ficristo](https://github.com/ficristo)
* [add: flow-root as value for display](https://github.com/brackets-cont/brackets/pull/13334) by [praveenpuglia](https://github.com/praveenpuglia)
* [Translated English to Japanese Comments](https://github.com/brackets-cont/brackets/pull/13327) by [Blackweda](https://github.com/Blackweda)
* [Found translations for all the missing Portuguese menu options](https://github.com/brackets-cont/brackets/pull/13323) by [Blackweda](https://github.com/Blackweda)
* [Changed url to access Japanese translated page](https://github.com/brackets-cont/brackets/pull/13321) by [Blackweda](https://github.com/Blackweda)
* [Replaced English comments with Japanese translations](https://github.com/brackets-cont/brackets/pull/13320) by [Blackweda](https://github.com/Blackweda)
* [Addressed performance problems when navigating between large code folded files](https://github.com/brackets-cont/brackets/pull/13310) by [thehogfather](https://github.com/thehogfather)
* [Fix #13274 - make Brackets margin/padding remoteHighlight work like Chrome one](https://github.com/brackets-cont/brackets/pull/13297) by [Worie](https://github.com/Worie)
* [Fix #13274 - make Brackets margin/padding remoteHighlight work like Chrome one](https://github.com/brackets-cont/brackets/pull/13288) by [Worie](https://github.com/Worie)
* [Addresses #13264 where setting `saveFoldStates` preference to false caused folding problems](https://github.com/brackets-cont/brackets/pull/13269) by [thehogfather](https://github.com/thehogfather)
* [Pflynn/in browser file system](https://github.com/brackets-cont/brackets/pull/13265) by [enterstudio](https://github.com/enterstudio)
* [Add new comments preference. Support indent block comments on line co…](https://github.com/brackets-cont/brackets/pull/13254) by [ficristo](https://github.com/ficristo)
* [Add support for TypeScript](https://github.com/brackets-cont/brackets/pull/13250) by [justinrusso](https://github.com/justinrusso)
* [Fix layout on narrow extension manager](https://github.com/brackets-cont/brackets/pull/13245) by [justinrusso](https://github.com/justinrusso)
* [Add JavaScript code hinting in JSX files](https://github.com/brackets-cont/brackets/pull/13243) by [justinrusso](https://github.com/justinrusso)
* [Fixes issue #13227](https://github.com/brackets-cont/brackets/pull/13235) by [parthsharma2](https://github.com/parthsharma2)
* [Add inputStyle preference](https://github.com/brackets-cont/brackets/pull/13216) by [ficristo](https://github.com/ficristo)
* [Update grunt-contrib-watch to 1.0.0 and clean a bit the task](https://github.com/brackets-cont/brackets/pull/13215) by [ficristo](https://github.com/ficristo)
* [Bootstrap](https://github.com/brackets-cont/brackets/pull/13208) by [dmitrymw](https://github.com/dmitrymw)
* [Add no-unsafe-negation rule and upgrade grunt-eslint to 19.0.0](https://github.com/brackets-cont/brackets/pull/13199) by [ficristo](https://github.com/ficristo)
* [Makes the content of script and style tags collapsible](https://github.com/brackets-cont/brackets/pull/13198) by [thehogfather](https://github.com/thehogfather)
* [Create tests for Disabled context menu items for unsaved files / #12806 #13134](https://github.com/brackets-cont/brackets/pull/13178) by [leeyimin](https://github.com/leeyimin)


#### Pulling source code from Git
_TODO: any brackets-shell updates? which of the below messages are applicable?_

* A new brackets-shell build is _required_ for this sprint. Be sure to rerun `grunt setup` before building.
* Recommended: rebuild or reinstall an updated brackets-shell (no critical updates, but there are bugfixes).
* Rebuilding/updating brackets-shell is _optional_ for this release.
* Rebuilding/updating brackets-shell is _not_ required for this release.
* brackets-shell's Node dependencies have changed. Run `npm install` before rebuilding brackets-shell.
* Some submodules were updated this sprint. Run `git submodule update` to ensure your source tree is fully up to date.
* A submodule _URL_ was changed this sprint. Run `git submodule sync` and _then_ `git submodule update --init --recursive` to ensure your local source tree reflects the update.


Bugs fixed in Release 1.10
-------------------------
For details on the bugs addressed, please refer to [closed Release 1.10 bugs](https://github.com/brackets-cont/brackets/issues?q=is%3Aclosed+milestone%3A%22Release+1.10%22). Not all fixed bugs will be caught by this search query, however.