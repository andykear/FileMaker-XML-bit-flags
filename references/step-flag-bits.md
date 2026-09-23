# Script step bit flags

Bit positions in a `<Step>` element's `<Options>` integer in a Save as XML export.

`label` is FileMaker's own wording, from the `<Boolean type=...>` element exports write.
`sense` is `=` when setting the property sets the bit, `!` when setting it clears the bit.
`default` is the value a newly created step carries.
`files` is how many of 171 independent exports state this mask.

| Step | id | bit | mask | key | label | sense | default | files |
|---|---:|---:|---:|---|---|:-:|---|---:|
| Append PDF | 244 | 9 | 512 | `createFolders` | Create folders | = | off | 1 |
| Change Password | 83 | 7 | 128 | `withDialog` | With dialog | ! | on | 3 |
| Check Selection | 18 | 12 | 4096 | `select` | Select | = | on | 6 |
| Clear | 49 | 12 | 4096 | `select` | Select | = | on | 8 |
| Close PDF | 245 | 9 | 512 | `createFolders` | Create folders | = | off | 2 |
| Close PDF | 245 | 29 | 536870912 | `openAutomatically` | — | = | off | — |
| Close PDF | 245 | 30 | 1073741824 | `createEmail` | — | = | off | — |
| Close Window | 121 | 31 | 2147483648 | `currentFileOnly` | — | = | on | — |
| Commit Records/Requests | 75 | 7 | 128 | `withDialog` | With dialog | ! | off | 36 |
| Commit Records/Requests | 75 | 8 | 256 | `skipDataEntryValidation` | Skip data entry validation | = | off | 36 |
| Commit Records/Requests | 75 | 9 | 512 | `forceCommit` | Force Commit | = | off | 36 |
| Configure AI Account | 212 | 28 | 268435456 | `verifySslCertificates` | Verify SSL Certificates | = | off | 4 |
| Configure Persistent Data | 238 | 8 | 256 | `delete` | — | = | off | — |
| Configure RAG Account  | 227 | 28 | 268435456 | `verifySslCertificates` | Verify SSL Certificates | = | off | 1 |
| Configure Regression Model | 222 | 12 | 4096 | `skipEmptyOrInvalidRecords` | Skip empty or invalid records | = | off | 1 |
| Constrain Found Set | 126 | 8 | 256 | `findWithoutIndexes` | Find without indexes | = | off | 32 |
| Constrain Found Set | 126 | 25 | 33554432 | `restore` | — | = | off | — |
| Convert File | 139 | 7 | 128 | `withDialog` | With dialog | ! | on | 2 |
| Convert File | 139 | 8 | 256 | `openFile` | Open File | ! | on | 2 |
| Convert File | 139 | 9 | 512 | `skipIndexes` | Skip Indexes | = | off | 2 |
| Convert File | 139 | 28 | 268435456 | `verifySslCertificates` | Verify SSL Certificates | = | off | 2 |
| Copy | 47 | 12 | 4096 | `select` | Select | = | on | 19 |
| Create Data File | 190 | 9 | 512 | `createFolders` | Create folders | = | on | 6 |
| Create PDF | 243 | 25 | 33554432 | `restore` | — | = | off | — |
| Cut | 46 | 12 | 4096 | `select` | Select | = | on | 1 |
| Delete All Records | 10 | 7 | 128 | `withDialog` | With dialog | ! | on | 30 |
| Delete Portal Row | 104 | 7 | 128 | `withDialog` | With dialog | ! | on | 28 |
| Delete Record/Request | 9 | 7 | 128 | `withDialog` | With dialog | ! | on | 35 |
| Dial Phone | 65 | 7 | 128 | `withDialog` | With dialog | ! | off | 1 |
| Else | 69 | 25 | 33554432 | `collapsed` | Collapsed | = | off | 35 |
| Else If | 125 | 25 | 33554432 | `collapsed` | Collapsed | = | off | 34 |
| Enter Browse Mode | 55 | 24 | 16777216 | `pause` | Pause | = | off | 29 |
| Enter Find Mode | 22 | 24 | 16777216 | `pause` | Pause | = | on | 36 |
| Enter Find Mode | 22 | 25 | 33554432 | `restore` | — | = | off | — |
| Enter Preview Mode | 41 | 24 | 16777216 | `pause` | Pause | = | off | 13 |
| Execute FileMaker Data API | 203 | 12 | 4096 | `select` | Select | = | on | 7 |
| Execute SQL | 117 | 7 | 128 | `withDialog` | With dialog | ! | off | 1 |
| Execute SQL | 117 | 9 | 512 | `createFolders` | Create folders | = | off | 1 |
| Execute URL | 224 | 28 | 268435456 | `verifySslCertificates` | — | = | off | — |
| Export Field Contents | 132 | 9 | 512 | `createFolders` | Create folders | = | on | 30 |
| Export Field Contents | 132 | 29 | 536870912 | `openAutomatically` | — | = | off | — |
| Export Field Contents | 132 | 30 | 1073741824 | `createEmail` | — | = | off | — |
| Export Records | 36 | 7 | 128 | `withDialog` | With dialog | ! | off | 24 |
| Export Records | 36 | 9 | 512 | `createFolders` | Create folders | = | on | 24 |
| Export Records | 36 | 25 | 33554432 | `restore` | — | = | off | — |
| Export Records | 36 | 29 | 536870912 | `openAutomatically` | — | = | off | — |
| Export Records | 36 | 30 | 1073741824 | `createEmail` | — | = | off | — |
| Extend Found Set | 127 | 25 | 33554432 | `restore` | — | = | off | — |
| Generate Response from Model | 220 | 15 | 32768 | `stream` | Stream | = | off | 4 |
| Generate Response from Model | 220 | 17 | 131072 | `agenticMode` | Agentic mode | = | on | 4 |
| Get Folder Path | 181 | 8 | 256 | `allowFolderCreation` | Allow Folder Creation | = | off | 12 |
| Go to Field | 17 | 12 | 4096 | `selectPerform` | Select/perform | = | off | 29 |
| Go to Portal Row | 99 | 7 | 128 | `withDialog` | — | ! | on | — |
| Go to Portal Row | 99 | 12 | 4096 | `select` | Select | = | off | 23 |
| Go to Portal Row | 99 | 13 | 8192 | `exitAfterLast` | — | = | off | — |
| Go to Record/Request/Page | 16 | 7 | 128 | `withDialog` | — | ! | off | — |
| Go to Record/Request/Page | 16 | 13 | 8192 | `exitAfterLast` | — | = | off | — |
| Go to Related Record | 74 | 9 | 512 | `matchAllRecordsInFoundSet` | — | = | off | — |
| Go to Related Record | 74 | 25 | 33554432 | `showOnlyRelatedRecords` | — | = | off | — |
| If | 68 | 25 | 33554432 | `collapsed` | Collapsed | = | off | 35 |
| Import Records | 35 | 7 | 128 | `withDialog` | With dialog | ! | off | 23 |
| Import Records | 35 | 25 | 33554432 | `restore` | — | = | off | — |
| Import Records | 35 | 28 | 268435456 | `verifySslCertificates` | Verify SSL Certificates | = | off | 23 |
| Insert Audio/Video | 159 | 11 | 2048 | `storeOnlyReference` | Store only a reference | = | off | 1 |
| Insert Calculated Result | 77 | 12 | 4096 | `select` | Select | = | on | 5 |
| Insert Current Date | 13 | 12 | 4096 | `select` | Select | = | on | 1 |
| Insert Current Time | 14 | 12 | 4096 | `select` | Select | = | on | 1 |
| Insert Current User Name | 60 | 12 | 4096 | `select` | Select | = | on | 1 |
| Insert Embedding in Found Set | 216 | 10 | 1024 | `replaceTargetContents` | Replace target contents | = | off | 1 |
| Insert Embedding in Found Set | 216 | 12 | 4096 | `continueOnError` | Continue on error | = | off | 1 |
| Insert Embedding in Found Set | 216 | 13 | 8192 | `showSummary` | Show summary | = | off | 1 |
| Insert File | 131 | 9 | 512 | `dialogOptions` | — | = | off | — |
| Insert File | 131 | 11 | 2048 | `storeAsReference` | — | = | off | — |
| Insert Image Captions in Found Set | 240 | 10 | 1024 | `replaceTargetContents` | Replace target contents | = | off | 1 |
| Insert Image Captions in Found Set | 240 | 12 | 4096 | `continueOnError` | Continue on error | = | off | 1 |
| Insert PDF | 158 | 11 | 2048 | `storeOnlyReference` | Store only a reference | = | off | 1 |
| Insert Picture | 56 | 11 | 2048 | `storeOnlyReference` | Store only a reference | = | off | 1 |
| Insert Text | 61 | 12 | 4096 | `select` | Select | = | on | 7 |
| Insert from Index | 11 | 12 | 4096 | `select` | Select | = | on | 1 |
| Insert from Last Visited | 12 | 12 | 4096 | `select` | Select | = | on | 1 |
| Insert from URL | 160 | 7 | 128 | `withDialog` | With dialog | ! | off | 24 |
| Insert from URL | 160 | 8 | 256 | `curlOptionsSpecified` | — | = | off | — |
| Insert from URL | 160 | 12 | 4096 | `select` | Select | = | on | 24 |
| Insert from URL | 160 | 28 | 268435456 | `verifySslCertificates` | Verify SSL Certificates | = | off | 24 |
| Install Menu Set | 142 | 9 | 512 | `useAsFileDefault` | Use as file default | = | off | 26 |
| Loop | 71 | 25 | 33554432 | `collapsed` | Collapsed | = | off | 40 |
| Omit Multiple Records | 26 | 7 | 128 | `withDialog` | With dialog | ! | off | 7 |
| Open File | 33 | 8 | 256 | `openHidden` | Open hidden | = | off | 19 |
| Open PDF | 246 | 9 | 512 | `createFolders` | Create folders | = | off | 1 |
| Open Transaction | 205 | 8 | 256 | `skipDataEntryValidation` | Skip data entry validation | = | off | 7 |
| Open Transaction | 205 | 9 | 512 | `overrideEssLockingConflicts` | Override ESS locking conflicts | = | off | 7 |
| Open Transaction | 205 | 12 | 4096 | `skipAutoEnterOptions` | Skip auto-enter options | = | off | 7 |
| Open Transaction | 205 | 25 | 33554432 | `collapsed` | Collapsed | = | off | 7 |
| Open URL | 111 | 7 | 128 | `withDialog` | With dialog | ! | off | 15 |
| Open URL | 111 | 8 | 256 | `inExternalBrowser` | In external browser | = | off | 15 |
| Page Setup | 42 | 7 | 128 | `withDialog` | With dialog | ! | off | 28 |
| Page Setup | 42 | 25 | 33554432 | `specifyPageSetup` | — | = | off | — |
| Paste | 48 | 9 | 512 | `noStyle` | No style | = | on | 8 |
| Paste | 48 | 12 | 4096 | `select` | Select | = | on | 8 |
| Perform Find | 28 | 25 | 33554432 | `restore` | — | = | off | — |
| Perform Find/Replace | 128 | 7 | 128 | `withDialog` | With dialog | ! | on | 7 |
| Perform RAG Action | 219 | 12 | 4096 | `stream` | — | = | off | — |
| Perform RAG Action | 219 | 15 | 32768 | `detectVerticalText` | — | = | off | — |
| Perform SQL Query by Natural Language | 214 | 12 | 4096 | `stream` | Stream | = | off | 1 |
| Perform Script on Server | 164 | 8 | 256 | `waitForCompletion` | Wait for completion | ! | on | 34 |
| Perform Semantic Find | 218 | 8 | 256 | `returnCount` | Return count | = | off | 1 |
| Print | 43 | 7 | 128 | `withDialog` | With dialog | ! | off | 24 |
| Print | 43 | 25 | 33554432 | `specifyPrintOptions` | — | = | off | — |
| Print PDF | 242 | 7 | 128 | `withDialog` | With dialog | ! | off | 2 |
| Print PDF | 242 | 8 | 256 | `password` | Password | = | off | 2 |
| Print PDF | 242 | 9 | 512 | `usePrintOptionsFrom` | Use print options from | = | off | 2 |
| Print PDF | 242 | 10 | 1024 | `savePrintOptionsTo` | Save print options to | = | off | 2 |
| Print PDF | 242 | 25 | 33554432 | `restore` | — | = | off | — |
| Re-Login | 138 | 7 | 128 | `withDialog` | With dialog | ! | off | 27 |
| Recover File | 95 | 7 | 128 | `withDialog` | With dialog | ! | off | 1 |
| Refresh Window | 80 | 8 | 256 | `flushCachedJoinResults` | Flush cached join results | = | off | 33 |
| Refresh Window | 80 | 9 | 512 | `flushCachedExternalData` | Flush cached external data | = | off | 33 |
| Relookup Field Contents | 40 | 7 | 128 | `withDialog` | With dialog | ! | off | 15 |
| Replace Field Contents | 91 | 7 | 128 | `withDialog` | With dialog | ! | off | 24 |
| Revert Record/Request | 51 | 7 | 128 | `withDialog` | With dialog | ! | off | 16 |
| Revert Transaction | 207 | 8 | 256 | `hasCondition` | Condition | = | off | 1 |
| Revert Transaction | 207 | 9 | 512 | `hasErrorCode` | Error Code | = | off | 1 |
| Save Records as Excel | 143 | 7 | 128 | `withDialog` | With dialog | ! | off | 28 |
| Save Records as Excel | 143 | 9 | 512 | `createFolders` | Create folders | = | on | 28 |
| Save Records as Excel | 143 | 25 | 33554432 | `restore` | — | = | off | — |
| Save Records as JSONL | 225 | 9 | 512 | `createFolders` | Create folders | = | off | 1 |
| Save Records as JSONL | 225 | 12 | 4096 | `formatForFineTuning` | Format for fine-tuning | = | off | 1 |
| Save Records as PDF | 144 | 7 | 128 | `withDialog` | With dialog | ! | off | 29 |
| Save Records as PDF | 144 | 8 | 256 | `appendToExistingPdf` | Append to existing PDF | = | off | 29 |
| Save Records as PDF | 144 | 9 | 512 | `createFolders` | Create folders | = | on | 29 |
| Save Records as PDF | 144 | 25 | 33554432 | `restore` | — | = | off | — |
| Save Records as PDF | 144 | 29 | 536870912 | `openAutomatically` | — | = | off | — |
| Save Records as PDF | 144 | 30 | 1073741824 | `createEmail` | — | = | off | — |
| Save Records as Snapshot Link | 152 | 9 | 512 | `createFolders` | Create folders | = | on | 2 |
| Save a Copy as | 37 | 9 | 512 | `createFolders` | Create folders | = | on | 1 |
| Save a Copy as | 37 | 29 | 536870912 | `openAutomatically` | — | = | off | — |
| Save a Copy as | 37 | 30 | 1073741824 | `createEmail` | — | = | off | — |
| Save a Copy as Add-on Package | 96 | 18 | 262144 | `replaceUuids` | Replace UUIDs | = | off | 1 |
| Save a Copy as XML | 3 | 8 | 256 | `includeDetailsForAnalysisTools` | Include details for analysis tools | = | off | 3 |
| Save a Copy as XML | 3 | 9 | 512 | `saveEachLayoutObjectsBinaryDataUnderItsNode` | Save each layout object's binary data under its node | = | off | 2 |
| Save a Copy as XML | 3 | 15 | 32768 | — | Specify options as JSON | — | — | 2 |
| Select Window | 123 | 31 | 2147483648 | `currentFileOnly` | — | = | on | — |
| Send Mail | 63 | 7 | 128 | `withDialog` | — | ! | off | — |
| Set AI Call Logging | 217 | 9 | 512 | `verbose` | Verbose | = | off | 1 |
| Set AI Call Logging | 217 | 10 | 1024 | `truncateMessages` | Truncate Messages | = | off | 1 |
| Set AI Call Logging | 217 | 17 | 131072 | `enabled` | enabled | = | off | 1 |
| Set Error Logging | 200 | 8 | 256 | `enabled` | enabled | = | off | 5 |
| Set Field by Name | 147 | 27 | 134217728 | `specifyTargetField` | Specify target field | = | off | 25 |
| Set Window Title | 124 | 31 | 2147483648 | `currentFileOnly` | — | = | on | — |
| Set Zoom Level | 97 | 19 | 524288 | `lock` | Lock | = | off | 24 |
| Show/Hide Menubar | 166 | 19 | 524288 | `lock` | Lock | = | off | 29 |
| Show/Hide Toolbars | 29 | 8 | 256 | `includeEditRecordToolbar` | Include Edit Record Toolbar | = | on | 30 |
| Show/Hide Toolbars | 29 | 19 | 524288 | `lock` | Lock | = | off | 30 |
| Sort Records | 39 | 7 | 128 | `withDialog` | With dialog | ! | off | 36 |
| Sort Records | 39 | 25 | 33554432 | `restore` | — | = | off | — |
| Trigger Claris Connect Flow | 211 | 7 | 128 | `withDialog` | With dialog | ! | off | 1 |
| Trigger Claris Connect Flow | 211 | 12 | 4096 | `select` | Select | = | on | 1 |
| Trigger Claris Connect Flow | 211 | 28 | 268435456 | `verifySslCertificates` | Verify SSL Certificates | = | off | 1 |
| Truncate Table | 182 | 7 | 128 | `withDialog` | With dialog | ! | on | 25 |
| Undo/Redo | 45 | 25 | 33554432 | `collapsed` | Collapsed | = | off | 6 |
| Write to Data File | 192 | 9 | 512 | `appendLineFeed` | Append line feed | = | on | 6 |

## Not in this integer

Seven booleans on Show Custom Dialog (`input1Password`, `input2Password`, `input3Password`,
`button1Commit`, `button2Commit`, `button3Commit`, `autoClose`) are stored as discrete
`<Boolean>` elements inside `ParameterValues`, not as bits.

## Unexplained

Bit 14 on Save Records as PDF (144) is set by default and is not accounted for.
