What's New in Release 1.12
-------------------------

*  **[JavaScript Refactoring](https://github.com/brackets-cont/brackets/pull/13965)** by [navch](https://github.com/navch) :
You can now easily restructure JavaScript code using Refactor capabilities in Brackets. You can now rename, wrap in Try/Catch or Condition, Extract to Variable or Function, and Create Getters/Setters – all at the click of a button (or two!).
 

_Full change logs:_ [brackets](https://github.com/brackets-cont/brackets/compare/release-1.11...release) and [brackets-shell](https://github.com/brackets-cont/brackets-shell/compare/release-1.11...release#commits_bucket)



Community contributions to Brackets
-----------------------------------
* [Upgraded codemirror version to 5.30.0](https://github.com/brackets-cont/brackets/pull/13754) by [saurabh95](https://github.com/saurabh95)
* [Update CSS at-rule hints](https://github.com/brackets-cont/brackets/pull/14013) by [valtlai](https://github.com/valtlai)
* [Update CSS pseudo-selector hints](https://github.com/brackets-cont/brackets/pull/14012) by [valtlai](https://github.com/valtlai)
* [Findbar search string retention](https://github.com/brackets-cont/brackets/pull/13955) by [TrocaTudo95](https://github.com/TrocaTudo95)

#### Pulling source code from Git
_TODO: any brackets-shell updates? which of the below messages are applicable?_

* A new brackets-shell build is _required_ for this sprint. Be sure to rerun `grunt setup` before building.
* Recommended: rebuild or reinstall an updated brackets-shell (no critical updates, but there are bugfixes).
* Rebuilding/updating brackets-shell is _optional_ for this release.
* Rebuilding/updating brackets-shell is _not_ required for this release.
* brackets-shell's Node dependencies have changed. Run `npm install` before rebuilding brackets-shell.
* Some submodules were updated this sprint. Run `git submodule update` to ensure your source tree is fully up to date.
* A submodule _URL_ was changed this sprint. Run `git submodule sync` and _then_ `git submodule update --init --recursive` to ensure your local source tree reflects the update.


Bugs fixed in Release 1.12
-------------------------
For details on the bugs addressed, please refer to [closed Release 1.12 bugs](https://github.com/brackets-cont/brackets/issues?q=is%3Aclosed+milestone%3A%22Release+1.12%22). Not all fixed bugs will be caught by this search query, however.