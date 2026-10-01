---
name: filemaker-xml-bit-flags
description: Decode the packed <Options> integers in a FileMaker Save as XML export — script step flags and layout object flags, with bit positions, polarity and defaults. Use when reading or analysing a .xml export, not when generating clipboard XML.
---

# Decoding FileMaker's packed option integers

A Save as XML export stores many settings as packed decimal numbers. Use the four files in
`data/` to turn them into names: step flags, a layout's own flags, layout object flags, and
layout part flags.

## Rules that must not be skipped

1. **A bit means different things on different steps.** Bit 9 is `forceCommit` on Commit
   Records/Requests and `createFolders` on Export Records. Always look up by `stepID`, never by
   step name and never globally. The name is not stable either: id 42 is `Page Setup` in the
   palette and `Print Setup` in an export, and 147 is `Set Field by Name` against `Set Field By
   Name`. Matching on the name silently produces two rows for one bit.

2. **Check `inverted` before reporting.** When it is true the stored bit is the negative of the
   key's name. `withDialog` on bit 7 is FileMaker's `NoInteract`: bit set means the dialog is
   suppressed. Forty-seven flags across the four files are stored this way.

3. **A layout object has seven integers.** Read all of them, at these paths:
   `LayoutObject`, `LayoutObject/Field`, `LayoutObject/Portal`, `LayoutObject/External`,
   `LayoutObject/SlideControl`, `LayoutObject/TabControl`,
   `LayoutObject/ExtendedAttributes/Formatting/Graphic`.

4. **Use 64-bit arithmetic.** A layout's own `<Options>` is 36 bits wide. JavaScript's `^`,
   `>>` and `>>> 0` coerce to int32, so they drop everything above bit 31 and, because a shift
   count is taken modulo 32, invent a bit 32 that is not there. Use `BigInt`.

5. **A bit is the checkbox, not the thing the checkbox controls.** A portal's bit 3 and
   bit 7 are the Sort and Filter tickboxes. FileMaker keeps the sort order and the filter
   formula in the file after either box is unticked, so the element outlives the bit: across
   338 portals in four files neither bit was ever set without its element, but 45 of 157
   stored filters and 17 of 217 stored sorts had the bit clear. Decide from the bit. A tool
   that reads the `<Calculation>` child instead reports a filter FileMaker is not applying.

6. **A bit that looks general may not be.** Bit 14 reads like "this step carries a
   calculation" — clear on a name-only Set Variable, set once it has a value. Over 60,987
   step instances that reading holds for 60,370 and fails for 617, concentrated in steps
   whose parameter is a field reference rather than a calculation. Do not generalise a
   meaning across steps because it fits the two you checked. Rule 1 applies to meanings as
   well as names.

7. **Report unexplained bits as unexplained.** A tidy table implies completeness it has not
   earned. Bit 14 on Save Records as PDF and bit 1 on Insert from URL are not accounted for.

## Do not use this for clipboard XML

Clipboard XML has no packed integer. Each flag is a named element and its `state` is the raw
bit, not the meaning: `withDialog` on serialises as `<NoInteract state="False"/>`. Generating
paste XML needs element names, which are not in this repo.
