# Layout part bit flags

Bits in the `Options` attribute on a layout part's `<Definition>` element.

| bit | mask | key | sense |
|---:|---:|---|:-:|
| 0 | 1 | `pagination.breakBefore` | = |
| 2 | 4 | `pagination.restartPageNumbers` | = |
| 6 | 64 | `pagination.allowBreakAcrossPages` | = |
| 8 | 256 | `pagination.discardRemainder` | = |

## Not in this integer

`rowState.useAlternate` and `rowState.useActive` move no bit. A part written with either true
or false carries `Options="0"`, so both are stored somewhere other than this integer.

## A dependency worth knowing

`discardRemainder` cannot be set unless `allowBreakAcrossPages` is also true. FileMaker Pro
greys the checkbox out until then.
