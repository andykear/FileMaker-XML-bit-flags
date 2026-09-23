# Layout object option bits

A `<LayoutObject>` carries up to seven packed integers at different depths. Each section below
is one of them, named by its path within the object.

`sense` is `=` when setting the property sets the bit, and `!` when setting it clears the bit.

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
| 3 | 8 | `allowEditingOfValueList` | field | = |
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

## `LayoutObject/Portal`

| bit | mask | key | object type | sense |
|---:|---:|---|---|:-:|
| 0 | 1 | `allowVerticalScrolling` | portal | = |
| 2 | 4 | `allowDelete` | portal | = |
| 4 | 16 | `resetScrollBarOnExit` | portal | ! |

## `LayoutObject/External`

| bit | mask | key | object type | sense |
|---:|---:|---|---|:-:|
| 0 | 1 | `allowInteraction` | webViewer | = |
| 1 | 2 | `displayInFindMode` | webViewer | = |
| 2 | 4 | `showProgressBar` | webViewer | = |
| 3 | 8 | `showStatusMessages` | webViewer | = |
| 5 | 32 | `encodeUrl` | webViewer | ! |
| 6 | 64 | `allowJavaScriptToPerformScripts` | webViewer | = |

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
