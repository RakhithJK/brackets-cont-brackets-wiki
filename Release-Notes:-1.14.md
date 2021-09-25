What's New in Release 1.14
-------------------------
* [**Support for Language Server Protocol**](https://github.com/brackets-cont/brackets/pull/14606) by [subhashjha333](https://github.com/subhashjha333) and [shubhsnov](https://github.com/shubhsnov) : Brackets now supports Language Server Protocol. The inbuilt language client can be used and customized to facilitate integration of language servers (such as PHP, Python, and more) to provide features like code hinting, parameter hinting, jump to definition etc.
* [**PHP Support**](https://github.com/brackets-cont/brackets/pull/14671) by [niteskum](https://github.com/niteskum) : Brackets now supports PHP via integration of a PHP language server. When writing PHP code, you can take advantage of code hinting, function parameter hinting, jump to definition, document and project wide symbols, find references and linting.

_Full change logs:_ [brackets](https://github.com/brackets-cont/brackets/compare/release-1.13...release#commits_bucket) and [brackets-shell](https://github.com/brackets-cont/brackets-shell/compare/release-1.13...release#commits_bucket)

Community contributions to Brackets
-----------------------------------


* [Forcefully disabling renderer accesibility](https://github.com/brackets-cont/brackets-shell/pull/660) by nethip
* [Executing default update process handler, in case auto-update fails.](https://github.com/brackets-cont/brackets/pull/14605) by nethip
* [AutoUpdate Mac Installer Script Administrator privileges changes](https://github.com/brackets-cont/brackets-shell/pull/656) by [niteskum](https://github.com/niteskum)
* [Linux window size and position ](https://github.com/brackets-cont/brackets-shell/pull/636) by [pelatx](https://github.com/pelatx)
* [Upgrading node to v6.14.0](https://github.com/brackets-cont/brackets-shell/pull/653) by [subhashjha333](https://github.com/subhashjha333)
* [Auto Update Error Handlng Fix](https://github.com/brackets-cont/brackets/pull/14412) by [niteskum](https://github.com/niteskum)
* [JSRefactoring Bugs Fix](https://github.com/brackets-cont/brackets/pull/14455) by [niteskum](https://github.com/niteskum)
* [Fixed ExtractToVariable Menu Close Issue due to scrolling](https://github.com/brackets-cont/brackets/pull/14492) by [niteskum](https://github.com/niteskum)
* [Fixed Getter Setter Redo Issue](https://github.com/brackets-cont/brackets/pull/14508) by [niteskum](https://github.com/niteskum)
* [jsRefactor Rename Relative Path issue fixed](https://github.com/brackets-cont/brackets/pull/14520) by [niteskum](https://github.com/niteskum)
* [Fixing the mac debug build](https://github.com/brackets-cont/brackets-shell/pull/657) by [vickramdhawal](https://github.com/vickramdhawal)
* [Update CSSProperties.json for text-align and text-justify](https://github.com/brackets-cont/brackets/pull/14563) by [narayani28](https://github.com/narayani28)
* [Update notification - based on current platform](https://github.com/brackets-cont/brackets/pull/14655) by [swmitra](https://github.com/swmitra)
* [switching from anonymous to pseudonymous to align with the definition…](https://github.com/brackets-cont/brackets/pull/14687) by [niteskum](https://github.com/niteskum)
* [Removing the old Brackets CLA check](https://github.com/brackets-cont/brackets/pull/14684) by [shubhsnov](https://github.com/shubhsnov)
* [Fixed LSP Linting Synchronization Issues](https://github.com/brackets-cont/brackets/pull/14685) by [niteskum](https://github.com/niteskum)
* [Php Tooling Strings changes](https://github.com/brackets-cont/brackets/pull/14688) by [niteskum](https://github.com/niteskum)
* [Fix for "GetItNow" action behaviour](https://github.com/brackets-cont/brackets/pull/14691) by [swmitra](https://github.com/swmitra)
* [Sending Analytics Data for file Operation and LSP features](https://github.com/brackets-cont/brackets/pull/14683) by [niteskum](https://github.com/niteskum)
* [Fix for PHPCodeHints invocation failure scenarios](https://github.com/brackets-cont/brackets/pull/14692) by [shubhsnov](https://github.com/shubhsnov)
* [PHPCodeHints : Select initial element in the hint list](https://github.com/brackets-cont/brackets/pull/14694) by [shubhsnov](https://github.com/shubhsnov)
* [Fix : Error occurs when dismissing QuickOpen dialog when no document is open](https://github.com/brackets-cont/brackets/pull/14698) by [shubhsnov](https://github.com/shubhsnov)
* [Changes to send data only once per 24 hours](https://github.com/brackets-cont/brackets/pull/14695) by [SnchitGrover](https://github.com/SnchitGrover)
* [Adding Code Hints Description Box for handling additional hint information in LSP](https://github.com/brackets-cont/brackets/pull/14696) by [shubhsnov](https://github.com/shubhsnov)
* [Capability to Support Document & Project Symbols provided by a Language Server](https://github.com/brackets-cont/brackets/pull/14697) by [shubhsnov](https://github.com/shubhsnov)
* [LSP Find References Feature](https://github.com/brackets-cont/brackets/pull/14693) by [niteskum](https://github.com/niteskum)
* [In App Notifications in Brackets](https://github.com/brackets-cont/brackets/pull/14715) by [swmitra](https://github.com/swmitra)


#### Pulling source code from Git

* A new brackets-shell build is _required_ for this sprint. Be sure to rerun `grunt setup` before building.
* Recommended: rebuild or reinstall an updated brackets-shell (no critical updates, but there are bugfixes).
* Rebuilding/updating brackets-shell is _optional_ for this release.
* Rebuilding/updating brackets-shell is _not_ required for this release.
* brackets-shell's Node dependencies have changed. Run `npm install` before rebuilding brackets-shell.
* Some submodules were updated this sprint. Run `git submodule update` to ensure your source tree is fully up to date.
* A submodule _URL_ was changed this sprint. Run `git submodule sync` and _then_ `git submodule update --init --recursive` to ensure your local source tree reflects the update.


Bugs fixed in Release 1.14
-------------------------
For details on the bugs addressed, please refer to [closed Release 1.14 bugs](https://github.com/brackets-cont/brackets/issues?q=is%3Aclosed+milestone%3A%22Release+1.14%22). Not all fixed bugs will be caught by this search query, however.