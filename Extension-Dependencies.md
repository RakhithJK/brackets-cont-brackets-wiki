# Extension Dependencies Research #

(This may eventually become documentation on how extension dependencies are handled.)

There are two different kinds of dependencies that extensions can have:

1. Brackets version
2. other extensions that provide necessary code/features for a given extension

For our initial take on extension management, it is imperative that we address the first concern, Brackets version compatibility. We *can* opt to handle dependency relationships between extensions later on.

What happens if we defer dependency relationships between extensions? The ability of extensions to relate to one another will affect the shape of the ecosystem. As an example of this, npm has taken package dependencies very seriously. As a result, npm has many small packages that "do one thing well" and rely on one another. If managing those dependencies was more difficult or fragile, the ecosystem of node modules would look quite different.

It is early enough for Brackets that we can defer this, but ultimately we'll want extensions to be able to provide capabilities that other extensions can take advantage of. In this document, we'll talk about extension dependencies and considerations of their management.

## Brackets Version Compatibility ##

Extensions work fine with the version of Brackets for which they were created. However, as Brackets continues to evolve, extensions will break if they are not maintained. Here are a few approaches for ensuring that a given extension is compatible with a user's version of Brackets:

1. extension developer keeps minimum and maximum version numbers up to date
2. [semantic versioning](http://semver.org/) is used to make extension API compatibility clear
3. "smart deprecation" and crowdsourcing marks keeps compatibility info up-to-date

I'm going to suggest that the third option is the best, but only after explaining the first two options for clarity as those first two options are the paths more often traveled.

### Min/Max Version Numbers in Metadata ###

Until Firefox 4, Firefox had "big bang" releases every 18 months or so. It was reasonable for Firefox add-on developers to update their metadata after one of these big bang releases after they did the work to ensure that their add-on was working fine with the new release. Firefox 4 spent 8 months in beta, giving developers ample opportunity to update their add-ons before the release, so that there wasn't a big problem of popular add-ons not being compatible with the new release.

Three months after Firefox 4's release, Mozilla changed to a 6 week "rapid release" cycle. API changes between these releases were possible and did happen. The requirement for add-on developers to check their add-ons for each release remained. Some add-on developers, however, did not want to do this every 6 weeks. An increasing number of add-ons started appearing to be incompatible, though many were still just fine because there weren't *that* many API changes in a given six week period.

Addons on addons.mozilla.org started having their metadata automatically updated to reflect compatibility with newer versions of Firefox. However, many add-ons were not installed from addons.mozilla.org. After a few releases of users complaining about "add-ons not being compatible", Firefox switched to having [add-ons be compatible by default](https://wiki.mozilla.org/Features/Add-ons/Add-ons_Default_to_Compatible).

The [Add-on Compatibility Reporter](https://addons.mozilla.org/en-US/firefox/addon/add-on-compatibility-reporter/) allows users to report add-ons that are having trouble with newer versions of Firefox.

With its short release cycles, having Brackets extensions specify their min/max versions will result in users being penalized for keeping their Brackets up to date – many of their extensions will likely stop working when new updates come out. This is especially true given that Brackets has no beta test period at this time.

### Semantic Versioning ###

[Semantic Versioning](http://semver.org/) is a convention for version numbers that provides real meaning behind them. semver is a standard among npm users.

To separate the marketing needs for version numbers from the extensions' needs for version numbers, we can talk about the "API version". If the Brackets API used semver, an extension made for Brackets API 1.x is *guaranteed* to work until Brackets API 2.0.0 is released. (It would be considered a bug if an extension *did* break during the 1.x cycle.)

This is an improvement over the min/max version scheme because it gives the Brackets team the ability to consciously choose when we make breaking changes and to ensure that there's enough warning for developers to deal with it.

The drawback to this scheme, though, is that it's very coarse-grained. If we felt the need to make even *one* backwards-incompatible change, semver dictates that we move to API 2.0. The number itself is not meaningful, but the fact that we've just broken all of the extensions *is*.

### Smart Deprecation + Crowdsourcing ###

In the Python standard library, a function deprecated in version 2.5 will start displaying warnings when used. When 2.6 comes out, that function will be gone. This policy gave Python a chance to move forward, while giving people a reasonable amount of time to heed the warnings and build to the new API.

With a central extensions repository, we can take this a step farther. Extension developers would not specify which version of Brackets their extensions are compatible with. The repository would keep track of the information for everyone.

Here's an example to show the idea:

* I publish an extension called WriteMyCodeForMe. Brackets 0.20 is the current version at the time.
* The repository marks the extension as having no upperbound version of Brackets. (It may default to a minimum version of the current version when the extension is first published.)
* Brackets 0.22 comes out and starts warning (via developer tools console, possibly via other UI) that WriteMyCodeForMe is using a now-deprecated API. The warning states that the API will go away in 0.24.
* When a user:
  * runs Brackets 0.22
  * that includes WriteMyCodeForMe that was installed from the repository
  * and that copy of WriteMyCodeForMe has not been marked as max API version 0.23
  * a message is sent to the repository warning of the impending problem
* during the next update check, everyone else's copy of WriteMyCodeForMe would get the new max API version message
* we could even send the author an email message
* when Brackets 0.24 is released, if WriteMyCodeForMe has *not* been updated, everyone's copies will be disabled

What if no one had WriteMyCodeForMe installed, and then someone installed it on top of Brackets 0.24? There would be a button in the extension manager that a user can click to say "This extension isn't working properly with my version of Brackets."

The combination of these features would mean:

1. users see fewer extensions get disabled because of being "incompatible" (though probably not really incompatible)
2. developers need to do less busywork keeping their extensions up-to-date


## Dependencies for Extensions ##

Next, we get into the idea of how extensions can depend on other extensions. The main purpose in allowing an extension to say that it depends on another is:

1. that extension plugs in to features provided by the one it depends on
2. if the user wants to install that extension, they automatically get the depended-on extension as well, to ensure that their newly installed extension works properly

Another use case that *could* be mentioned is an extension that relies on another extension to merely act as a *library*, providing useful functions and data structures. That does not seem quite a Brackets-specific a problem. In fact, that is a problem that is well-handled by npm, which tries to combine the best aspects of static and dynamic linking. My focus here is not on extension dependencies for purposes of code sharing, but rather for the purposes of *extending Brackets in ways not directly supported by Brackets core*. See "What npm Does" below.

In the [list of extensions today](https://github.com/adobe/brackets/wiki/Brackets-Extensions), we don't actually see a need for this. This is doubtless in part because Brackets extensions currently don't have a way to share code or make their objects and events available to one another. When we do our extension API research, we will doubtless improve the ways in which extensions can share and increase the likelihood that extensions will rely upon each other. A need for extensions to provide facilities for other extensions would be more obvious today if Brackets itself was built on a foundation of extensions.

Let's start with a hypothetical scenario. As part of the [JavaScript code hinting work](https://trello.com/card/2-code-hinting-javascript/4f90a6d98f77505d7940ce88/775), we're adding a JS parser (esprima) to the package. esprima parses on a worker thread, to ensure that the UI stays responsive. Even so, you'd ideally only do the parsing *once* and provide the data to as many consumers as needed. Perhaps one extension would like to use the AST that's built. Another may want to subscribe to events as the AST changes. (These are hypothetical, please ignore whether we can actually get these things from our current parser setup.)

These JS parsing features are going to be built-in to Brackets, so they're still not a good example of an extension requiring another. Imagine, though, an extension that wants similar access to TypeScript parsing from the [TypeScript extension](https://github.com/tomsdev/brackets-typescript-code-intel). Someone else comes along and they want to build a TypeScript beautification extension that takes advantage of an AST already built by the TypeScript extension.

### What npm Does ###

npm uses semantic versioning and fancy module loader tricks to make code happy when it brings in library code. Let's say an application uses libraries to connect to Twitter and Google. The Twitter package depends on some "oauth" library version 1.x and the Google package relies on version 2.x of the same library.

When the Twitter library says `require("oauth")`, it gets version 1.2.3. The Google library says `require("oauth")` and it gets version 2.1.2. Both libraries are happy.

npm also has a feature called ["peer dependencies"](http://blog.nodejs.org/2013/02/07/undefined/) that is specifically for plugins.

### But, That's Not The Problem We Have ###

In my TypeScript example, the problem we're solving is that we're not trying to access code in a library. We're trying to access a *service*. We want a current AST, or a stream of events.

Another way to think of our problem: some Brackets extensions will add UI elements. If we handled these like npm does, the UI bits would get hooked up *twice*, once for each version.

What if extension authors can use exactly the same mechanism that's suggested for Brackets up above? Smart deprecation + crowdsourcing.

The TypeScript extension will provide its services (through means that will be discussed during the extension API research). If it changes how these work, it will deprecate the old ways, marking the version planned to remove the deprecated APIs. Extensions that specify (in the metadata) that they rely on the TypeScript extension will be marked incompatible following the deprecation scheme. Users will also be able to use the same button to report that "an extension has become incompatible" to let people know that the extension no longer works as it used to (whether that's because of Brackets changing or TypeScript changing).

# Smart Deprecation + Crowdsourcing + API Versions #

In conclusion, my suggestion is that we use "smart deprecation + crowdsourcing" (if you haven't been reading the whole way through, see the section with that title above for more detail), with one further addition.

If we made some *huge* breaking change to how extensions work in Brackets, we'd be able to change the extension loader code in one way or another to recognize new vs. old extensions (something I did recently with my prototype that could load 3 different styles of extensions all in the same Brackets instance).

Extensions that offer capabilities for other extensions do not have this ability. If the TypeScript extension needed to make a big change, it should still be able to do so. The author could register a "TypeScript2" extension, but that wouldn't be so good because then users could have both "TypeScript" and "TypeScript2" installed and the behavior may not be desirable.

As a solution to this, my suggestion is that the Brackets API and extensions like the hypothetical TypeScript extension would have an "API version", which would be a whole number for simplicity's sake. This will almost always just be "1" (and can, in fact, default to that). When an extension makes a change to its API that is too large for the deprecation mechanism to work well, the "API version" is incremented and any extensions that used the old API version will no longer be compatible.