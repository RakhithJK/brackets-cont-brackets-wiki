In Brackets we have an HTML utility API ``getTagInfo(editor, cursorPosition)`` to provide the context of an HTML tag and is already used by tag hinting and attribute hinting. However, we do not have a similar CSS utility API to provide CSS rule information. So this document specifies the new CSS utility API in order to achieve the following goals.
* To avoid duplicate effort in detecting CSS context by individual extension provider.
* To avoid inconsistent or incomplete implementation of CSS context detection.
* To provide a maintainable, scalable implementation of CSS context API that has a complete coverage of all possible CSS context.

## getRuleInfo ##
The new API will be defined as ``getRuleInfo(editor, cursorPos)``. It takes two arguments -- editor object and cursor position, and returns a rule information object.
**Open question** - should we call it *getCssInfo* since some of the context do not apply to a css rule (eg. @charset "u|tf-8" where `|` denotes the cursor location)? [Jason: What about ``getOffsetInfo()``? I'm reminded here of APIs we design in Flash Builder for querying our code model: http://livedocs.adobe.com/flex/3/extensibility/CodeModel/com/adobe/flexbuilder/codemodel/tree/ASOffsetInformation.html] 
<br />
The rule information object is defined as follows...
```
{ 
  selector:                              // Used when tokenType == SELECTOR
      { index: currentIndexInValues,
        values: [selector1, selector2, ...] },
  prop:                                  // Used when tokenType == PROP_NAME || tokenType == PROP_VALUE
      { name: propName,
        index: currentIndexInValues,
        values: [propValue1, propValue2, ...] },
  position:
      { tokenType: tokenType,
        offset: offsetInCurrentToken } 
}
```

[Randy] Each item in the array of selector.values (e.g. selector1, selector2, ...), is also a list of simple selectors (e.g. #nav div li > a:hover). Should these also be parsed into an array? Another idea would be to only initially parse into a string (not the array shown above), then have a separate getSelectorInfo() function to parse the selector list deeper only when needed.

`tokenType` is either an empty string or one of the following values that represents the different context in a CSS document.
 * **PROP_NAME** 
   - will implement in sprint 18 for CSS hinting and font hinting
 * **PROP_VALUE** 
   - will implement in sprint 18 for CSS hinting and font hinting 
 * **SELECTOR** 
   - not plan to implement it in sprint 18, but possibly in sprint 19
 * **MEDIA** 
   - may support in the future with some modification to the rule info structure
 * **CHARSET** 
   - may support in the future with some modification to the rule info structure

The value of ``tokenType`` is an empty string for the following context.
 * Current cursor position is in a non-css/non-less document 
 * Current cursor position is within a not-yet-supported or unsupported context - ([examples](#notsupported))
 * Current cursor position is inside an invalid context - ([examples](#invalid))

###Default values of rule information###
If the cursor is in a non-css /non-less document, or inside the unsupported context of a css/less document, a rule info with the following default values is returned.

[Jason: These empty selector and prop properties seem unnecessary to me. Earlier you mention that selector and prop will only be set if the matching tokenType is specified. Would it make more sense to return only a position property with tokenType=UNKNOWN]
```
{ 
  selector:
      { index: -1,
        values: [] },
  prop:
      { name: "",
        index: -1,
        values: [] },
  position:
      { tokenType: "",
        offset: 0 } 
}
```
<a name="notsupported"> </a>
###Examples of Not-Yet Supported CSS Context###
>@char|set "UTF-8";
>
>@import ur|l("booya.css") print,screen;
>
>@import "whatup.css" sc|reen;
>
>@import "|wicked.css";

>@namespace "|http://www.w3.org/1999/xhtml";
>
>@namespace s|vg "http://www.w3.org/2000/svg";
>
>@media sc|reen { ... }

<br />

<a name="invalid"> </a>
###Examples of Invalid CSS Context###
>div { clear |: both; }   /* cursor before the colon and after a valid property name */
>
>div { clear b|oth; }      /* missing colon after "clear" property name */
>
>div { font-family: Arial |, Helvetica; }   /* cursor before the comma separator */

<br />

###Examples of Property Name context###
> 1. div {|
>
> 2. div {
><br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|
>
> 3. div {
><br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|clip:
>
> 4. div {
><br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;clip|:
>
> 5. div {
><br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;c|lip:
>

<br />

All the above example will return a rule info object with "position.tokenType" assigned to PROP_NAME. "prop.index" and "prop.values" are not used for PROP_NAME token type so they will have default values.

For example 1 and 2  "prop.name" will be an empty string since the cursor is not in any property name. Example 3 to 5 will have "clip" assigned to "prop.name". "position.offset" is the cursor offset in the current token "clip" and it is zero for example 3, 4 for example 4 and 1 for example 5.

<br />

###Examples of Property Value context###
> 1. div { font-family:| "Helvetica Neue", Helvetica, Arial, sans-serif; }
>
> 2. div { font-family: "Helvetica Neue"|, Helvetica, Arial, sans-serif; }
>
> 3. div { font-family:| "Helvetica Neue", |Helvetica, Arial, sans-serif; }
>
> 4. div { font-family:| "Helvetica Neue", Helvetica, Arial,| sans-serif; }
>
> 5. div { font-family:| "Helvetica Neue", Helvetica, Arial, sans-serif |; }

<br />
All the examples above will have PROP_VALUE in "position.tokenType" and "prop.name" will be "font-family". Also all of them will have the same array in "prop.values" ``[""Helvetica Neue", ", "Helvetica, ", "Arial, ", "sans-serif"]`` Please note that each item in the values array except the last one has a comma and the trailing white spaces. We intentionally append the comma and the trailing spaces so that the caller can reconstruct the actual string or can calculate the start or end position of a specific value.

Although they all have the same "prop.values" array regardless of the cursor positions, they will have different "prop.index" and "position.offset". Example 1 will have -1 index and zero offset since the cursor is before the very first property value. Index for example 2 is zero and offset will be 16. Index for example 5 is 4 since the cursor is after the last existing property value.