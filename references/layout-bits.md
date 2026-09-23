# Layout bit flags

Bits in a `<Layout>` element's own `<Options>` integer. It is 36 bits wide, the widest value
in the format, so it needs 64-bit arithmetic to read.

`sense` is `=` when setting the property sets the bit, `!` when setting it clears the bit.

| bit | mask | group | key | sense |
|---:|---:|---|---|:-:|
| 0 | 1 | layout | `delineateCurrentRecordOnly` | = |
| 1 | 2 | viewStyles.enabled | `form` | ! |
| 2 | 4 | viewStyles.enabled | `list` | ! |
| 3 | 8 | viewStyles.enabled | `table` | ! |
| 4 | 16 | layout | `saveRecordChangesAutomatically` | ! |
| 5 | 32 | layout | `showFieldFramesWhenActive` | = |
| 7 | 128 | printing | `facingPages` | = |
| 11 | 2048 | layout | `verticalPartLabels` | = |
| 12 | 4096 | layout | `textRuler` | = |
| 13 | 8192 | layout | `showFieldAlerts` | = |
| 15 | 32768 | layout | `quickFind` | ! |
| 16 | 65536 | tableView | `horizontalGrid` | = |
| 17 | 131072 | tableView | `verticalGrid` | = |
| 18 | 262144 | tableView | `includeHeader` | = |
| 19 | 524288 | tableView | `includeFooter` | = |
| 20 | 1048576 | tableView | `columnHeaders` | = |
| 21 | 2097152 | tableView | `resizableColumns` | = |
| 22 | 4194304 | tableView | `reorderableColumns` | = |
| 23 | 8388608 | tableView | `sortOnSelect` | = |
| 26 | 67108864 | tableView | `customColumnOrder` | = |
| 28 | 268435456 | layout | `showCurrentRecordIndicator` | ! |
| 29 | 536870912 | tableView | `includeTopNav` | = |
| 30 | 1073741824 | tableView | `includeBottomNav` | = |
| 32 | 4294967296 | tableView | `systemAppearance` | = |
| 33 | 8589934592 | tableView | `comfortableFormatting` | = |
| 34 | 17179869184 | tableView | `alternatingRowColors` | = |
| 35 | 34359738368 | tableView | `rowNumbers` | = |

## The default value

A newly created layout carries `64440436737`, which is bits 0, 11, 16, 17, 20, 21, 22, 23, 32,
33, 34 and 35. Every one of those is in the table above:

| bit | what it is |
|---:|---|
| 0 | `layout.delineateCurrentRecordOnly` |
| 11 | `layout.verticalPartLabels` |
| 16 | `tableView.horizontalGrid` |
| 17 | `tableView.verticalGrid` |
| 20 | `tableView.columnHeaders` |
| 21 | `tableView.resizableColumns` |
| 22 | `tableView.reorderableColumns` |
| 23 | `tableView.sortOnSelect` |
| 32 | `tableView.systemAppearance` |
| 33 | `tableView.comfortableFormatting` |
| 34 | `tableView.alternatingRowColors` |
| 35 | `tableView.rowNumbers` |
