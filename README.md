# FileMaker XML bit flags

What the `<Options>` integers in a FileMaker Save as XML export mean.

FileMaker stores many settings as packed decimal numbers. An export gives you
`<Options>64440436737</Options>` and nothing else. This is the map.

## Contents

| File | Rows | Covers |
|---|---:|---|
| `data/step-flags.json` | 161 | Script step `<Options>`, 99 step types |
| `data/layout-flags.json` | 27 | A layout's own `<Options>`, 36 bits wide |
| `data/layout-object-flags.json` | 41 | `<LayoutObject>`, its six nested integers, and a popover's own attribute |
| `data/part-flags.json` | 4 | The `Options` attribute on a part's `<Definition>` |
| `references/*.md` | | The same, as tables |
| `SKILL.md` | | Rules for decoding correctly |

233 flags in total.

## Five facts

**A layout object holds seven packed integers, not one.** Its own, plus separate ones inside
`Field`, `Portal`, `External`, `SlideControl`, `TabControl` and
`ExtendedAttributes/Formatting/Graphic`. Reading only the outermost finds 11 of 41 properties.
`quickFind` is in the one inside `Field`. A popover panel carries an eighth value as an
`Options=` attribute on its own tag rather than as an element.

**Forty-seven flags are stored inverted.** The bit is the negative of the property name.
`withDialog` is bit 7, which is FileMaker's `NoInteract`: bit set means the dialog is
suppressed.

**A bit means different things on different steps.** Bit 9 is `forceCommit` on Commit
Records/Requests and `createFolders` on Export Records. Look up by `stepID`.

**A layout's own integer is 36 bits wide**, the widest value in the format. `64440436737` is
the value every new layout carries, and all twelve of its set bits are accounted for: the
table view grid, headers, column behaviour and row formatting, plus vertical part labels and
delineate-current-record-only.

**`805306368` on a layout object is `anchors.left` plus `anchors.top`** and nothing else. An
object with no anchors carries `0`.

## Scope

Mapped: script step options, a layout's own options, the seven integers and one attribute on
a layout object, and the pagination bits on a layout part.

Not in any of these integers: seven booleans on Show Custom Dialog, and a part's
`rowState.useAlternate` and `rowState.useActive`. Those are stored elsewhere and are listed
where they belong rather than omitted.

Not mapped: the accounts catalog.

Unexplained: bit 14 on Save Records as PDF, bit 1 on Insert from URL, and bit 0 of a popover
panel's Options attribute.

## Not for clipboard XML

Clipboard XML (`<fmxmlsnippet>`) has no packed integer. Each flag is a named element whose
`state` carries the raw bit rather than the meaning, so `withDialog` on serialises as
`<NoInteract state="False"/>`. Generating paste XML needs element names, not these bits.

## Verified, not guessed

✓ **round-trip tested.** Every row was produced by setting the property, reading the integer
back, and recording which bit moved.

◎ **observed in native exports.** 121 of the step rows are independently confirmed by
FileMaker's own output. Every export writes `<Boolean type="With dialog" id="128">` inside a
step's `ParameterValues`, where `id` is the mask and `type` is FileMaker's wording. Across 171
unrelated exports, every mask stated that way is a single power of two, and all 120 that
overlap the probed rows agree with them.

The bits listed above as unexplained are neither observed nor inferred — they are simply not
accounted for, and are listed rather than omitted.

Exports carrying `Source="26.0.2"`.

## Related

The other specifications in this collection cover the **clipboard** format
(`fmxmlsnippet`): script steps, layout objects, and field and table definitions. This one
covers the **export** format (`FMSaveAsXML`), which is a different serialisation of the same
settings and does not share their vocabulary.

## Licence

CC BY 4.0. Andrew Kear, Clockwork Creative Technology.
