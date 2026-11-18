# Layout object option bits

A `<LayoutObject>` carries up to eight packed integers at different depths. Each section below
is one of them, named by its path within the object.

`sense` is `=` when setting the property sets the bit, and `!` when setting it clears the bit.

`[26.1+]` marks an option FileMaker 26.1 added (`"since": "26.1"` in the JSON). A file only
carries it if FileMaker 26.1 or later set it.

## `LayoutObject`

| bit | mask | key | object type | sense |
|---:|---:|---|---|:-:|
| 1 | 2 | `locked` | field | = |
| 4 | 16 | `slideUp` | field | = |
| 5 | 32 | `slideLeft` | field | = |
| 6 | 64 | `resizeEnclosingPart` | field | = |
| 8 | 256 | `applyInFindMode` | field | = |
| 9 | 512 | `hideWhenPrinting` | field | = |
| 16 | 65536 | `showHandCursor` | button | = |
| 28 | 268435456 | `anchors.left` | field | = |
| 29 | 536870912 | `anchors.top` | field | = |
| 30 | 1073741824 | `anchors.right` | field | = |
| 31 | 2147483648 | `anchors.bottom` | field | = |

## `LayoutObject/Field`


| bit | mask | key | object type | sense |
|---:|---:|---|---|:-:|
| 0 | 1 | `allowEntryOfOtherValues` | field | = |
| 1 | 2 | `selectContentsOnEntry` | field | = |
| 2 | 4 | `browseEntryViewOnly` | field | = |
| 3 | 8 | `allowEditingOfValueList` | field | = |
| 4 | 16 | `findEntryViewOnly` | field | = |
| 5 | 32 | `exitOnTab` | field | = |
| 6 | 64 | `exitOnReturn` | field | = |
| 7 | 128 | `exitOnEnter` | field | = |
| 8 | 256 | `showVerticalScrollBar` | field | = |
| 10 | 1024 | `includeShowHideIcon` | field | = |
| 11 | 2048 | `autoComplete` | field | = |
| 13 | 8192 | `applyVisualSpellChecking` | field | ! |
| 15 | 32768 | `quickFind` | field | ! |
| 16 | 65536 | `showPlaceholderInFindMode` | field | ! |
| 20 | 1048576 | `overrideDataFormattingWithValueList` | field | ! |
| 22 | 4194304 | `displaySingleCheckboxWithoutValue` `[26.1+]` | field | = |
| 23 | 8388608 | `showIndicatorForClippedContents` `[26.1+]` | field | = |
| 24 | 16777216 | `browseEntrySelectOnly` | field | = |
| 25 | 33554432 | `findEntrySelectOnly` | field | = |

Field entry is two two-bit enums rather than four independent flags. In each mode
the low bit alone is View Only, the high bit alone is Select Only, and both bits
together is Set by Calculation. Browse mode uses bits 2 and 24, Find mode bits 4
and 25. A plain edit box reads 32, not 0, so compare against that baseline.

## `LayoutObject/Portal`


| bit | mask | key | object type | sense |
|---:|---:|---|---|:-:|
| 0 | 1 | `allowVerticalScrolling` | portal | = |
| 2 | 4 | `allowDelete` | portal | = |
| 3 | 8 | `sort` | portal | = |
| 4 | 16 | `resetScrollBarOnExit` | portal | ! |
| 7 | 128 | `filter` | portal | = |
| 10 | 1024 | `placeNewRecordRowAtTop` `[26.1+]` | portal | = |

Bits 3 and 7 are the two checkboxes in the portal setup dialog, not the presence of
the elements they control. FileMaker keeps a portal's sort order and filter formula in
the file after either box is unticked. Across 338 portals in four exports neither bit
was ever set without its element, but 17 of 217 stored sorts and 45 of 157 stored
filters had the bit clear. A tool that reads the element rather than the bit reports a
filter FileMaker is not applying.

## `LayoutObject/External`

| bit | mask | key | object type | sense |
|---:|---:|---|---|:-:|
| 0 | 1 | `allowInteraction` | webViewer | = |
| 1 | 2 | `displayInFindMode` | webViewer | = |
| 2 | 4 | `showProgressBar` | webViewer | = |
| 3 | 8 | `showStatusMessages` | webViewer | = |
| 5 | 32 | `encodeUrl` | webViewer | ! |
| 6 | 64 | `allowJavaScriptToPerformScripts` | webViewer | = |
| 7 | 128 | *not identified* | webViewer | ? |
| 8 | 256 | `allowJavaScriptToExecuteDataApiRequests` | webViewer | = |
| 15 | 32768 | *not identified* | webViewer | ? |

Bits 7 and 8 were measured in FileMaker 26.1 by setting the options with a tool, and the Web
Viewer Setup dialog was not checked. Setting `allowJavaScriptToExecuteDataApiRequests` set bit
8 alone. Setting `allowJavaScriptToPerformScripts` set bit 7 as well as bit 6. Across 566 web
viewers in exports from FileMaker 21 to 26.0, 87 of them with bit 6, neither bit 7 nor bit 8 is
ever set. In FileMaker 26.1.1 exports bit 7 is set on 168 of the 190 viewers with bit 6, and
never without it. Most of those files were built by tools.

Bit 15 is used in real files and is not identified. Across 321 web viewers in 55 exports it is
set on 189 and clear on 132, and the same combination of the six known bits occurs both with it
and without — so it is independent of them rather than a side effect.

Three explanations have been ruled out. It is not a marker for the version that wrote the file:
twelve of the exports contain web viewers both with and without it. It does not distinguish a
literal address from a calculated one: objects carrying a fixed URL, a quoted calculation and a
field reference all read the same. It is not the Data API option, which is bit 8: three web
viewers created in FileMaker 26.1, one with default settings, one with the Data API option on
and one with perform scripts on, all carry bit 15.

## `LayoutObject/Button`

| bit | mask | key | object type | sense |
|---:|---:|---|---|:-:|
| 2 | 4 | `iconCalculationInEffect` `[26.1+]` | button | = |

Earlier versions write this integer too. Bit 2 is set while a calculated icon is in effect,
and the formula is then in `<IconData type="4">` as `<SVGCalc>` (clipboard XML spells it
`SvgCalc`). Bits 0 and 1 are used in real files and are not identified: in every export from
FileMaker 21 to 26.0 checked, the value is 0, 2 or 3, never 1.

## `LayoutObject/SlideControl`

| bit | mask | key | object type | sense |
|---:|---:|---|---|:-:|
| 0 | 1 | `showNavigationDots` | slideControl | ! |
| 1 | 2 | `enableSwipeGestures` | slideControl | ! |

## `LayoutObject/TabControl`

| bit | mask | key | object type | sense |
|---:|---:|---|---|:-:|
| 8 | 256 | `tabsShareSingleStyle` | tabControl | = |

## `LayoutObject/ExtendedAttributes/Formatting/Graphic`

| bit | mask | key | object type | sense |
|---:|---:|---|---|:-:|
| 2 | 4 | `maintainOriginalProportions` | field | = |
| 9 | 512 | `autoPlay` | field | = |
| 10 | 1024 | `preservePdfTransparency` | field | = |
| 11 | 2048 | `noContextMenu` | field | = |

## The default value

`805306368` is `0x30000000`, which is bit 28 plus bit 29: `anchors.left` and `anchors.top`.
An object with no anchors carries `0`.

## The attribute, not the element

A `PopoverPanel` object carries a second packed value as an `Options=` **attribute on its own
tag**, separate from the `<Options>` element inside it. Across 172 exports only PopoverPanel
objects have it, on 5,885 objects, and only bits 0 and 1 are ever used.

| bit | mask | key | sense |
|---:|---:|---|:-:|
| 1 | 2 | `showTitleBar` | ! |

A popover button is two objects in the file, the button and the panel it opens, and
`showTitleBar` belongs to the panel rather than the button.

Bit 0 of the same attribute is used in real files and is not identified.
