This page discusses lower level parsing utilities in Brackets used by utilities
such as `CSSUtils`, `HTMLUtils`, and `JSUtils`.

## Usage

The 2 main usages are:

1. Parsing Block of Code
2. Determining State of Current Position

### Parsing Block of Text

Parsing a block of text (usually an entire file) is necessary
to enumerate certain elements such as:

* CSS selectors
* JS functions
* `<style>` blocks
* `<script>` blocks

The block of text being parsed can be large, so this code needs to be performant.

#### Examples in Brackets code base

* CSSUtils
    - `findMatchingRules()`
    - `extractAllSelectors()`
* JSUtils
    - `findAllMatchingFunctionsInText()`
* HTMLUtils
    - `findBlocks()`
    - `findStyleBlocks()`


### Determining State

To determine the token, type, state, etc. of current position in document,
text before and after current position is parsed.

#### Examples

* EditorCommandHandlers
    - `blockComment()`
    - `lineComment()`
* CSSCodeHints
    - `insertHint()`
* CSSUtils
    - `getInfoAtPos()`
    - `findSelectorAtDocumentPos()`
* HTMLUtils
    - `getTagAttributes()`
    - `getTagInfo()`


## Methods

Following are the common ways of parsing in Brackets:

* `TokenUtils`: `getInitialContext()`, `moveNextToken()`, `movePrevToken()`
* Using `mode.token()` with `CodeMirror.StringStream`


### TokenUtils

Written using [CodeMirror mode, state, and token API](http://codemirror.net/doc/manual.html#api_mode). Tokens and states are generated by CodeMirror modes defined in [src/thirdparty/CodeMirror2/mode](https://github.com/adobe/CodeMirror2/tree/master/mode) folder.

#### Examples

* EditorCommandHandlers
    - `blockComment()`
    - `lineComment()`
* CSSCodeHints
    - `insertHint()`
* CSSUtils
    - `getInfoAtPos()`
    - `findSelectorAtDocumentPos()`
* HTMLUtils
    - `getTagAttributes()`
    - `getTagInfo()`
    - `findBlocks()`
    - `findStyleBlocks()`


### StringStream

Uses [CodeMirror Mode API](http://codemirror.net/doc/manual.html#modeapi).

#### Examples

* CSSUtils
    - `findMatchingRules()`
    - `extractAllSelectors()`
* JSUtils
    - `findAllMatchingFunctionsInText()`

## Misc.

Implementation details in [CSS Context API implementation spec](https://github.com/brackets-cont/brackets/wiki/CSS-Context-API-implementation-spec).

CodeMirror modes, states, and tokens change over time due to more granular states being added.
These change can break parsing code, so beware when upgrading CodeMirror.

The SVG Code Hints extension may be merged into core soon, so a new `XMLUtils` utility may be introduced.
