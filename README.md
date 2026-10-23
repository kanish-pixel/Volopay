# Revenue Intelligence Inbox — VS Code starter

## What this project does
A no-build, browser-based dashboard for the Revenue Intelligence Inbox assignment. It supports JSON imports, unique record identity, revision-aware updates, persistent manual route overrides, source inspection, filters, a manager brief, and JSON/CSV export.

## Important: add the two source JSON files
The documents supplied with this project explain the assignment but do **not** include the actual delivery files. Put the real files here:
- `data/01_initial.json`
- `data/02_update.json`

Do not invent these records. The assignment expects 44 unique source records and 17 usable supplied texts after initial import; after the update it should remain 44 records with 18 usable texts.

## Run in VS Code
1. Extract this ZIP.
2. Open the folder in VS Code.
3. Add the two JSON delivery files to `data/`.
4. Open `index.html` in a browser, or use the VS Code Live Server extension and choose **Open with Live Server**.
5. Go to **Imports & exports**.
6. Choose `data/01_initial.json`, click **Import initial**.
7. Choose `data/02_update.json`, click **Import update**.
8. Go to **Conversation inbox**, search for `M07`, inspect it and manually change its route.
9. Return to **Imports & exports** and click **Repeat initial import**. M07's revision 2 and manual route should remain.
10. Refresh the page and confirm the route still persists.

## Replay test
- Reset local state.
- Import initial: unique count should be 44, usable text count should be 17.
- Repeat initial: unique count remains 44.
- Manually change M07 route.
- Import update: unique count remains 44, usable text count should become 18.
- Import initial again: revision 1 must not overwrite revision 2.
- Refresh: manual route override persists.

## Features and implementation notes
- Identity: `(source_type, source_id)`.
- Higher revisions replace the source payload and transcript payload; same/older revisions are ignored.
- Manual route choices are stored separately and persist in browser `localStorage`.
- Routing suggestions are transparent deterministic keyword rules, not a live AI model. Review them before acting.
- On changed source text, analysis should be reviewed; the app surfaces review state.
- Dashboard metrics are calculated from the selected records. Person grouping uses call rep name for calls and meeting organiser email for meetings.
- Transcript coverage = records with a nonblank call transcript or at least one nonblank meeting turn / selected unique source records.
- This dataset is a selected exercise sample, not a team-performance benchmark. Do not infer deal values or outcomes that the source does not establish.

## Export
Use **Export current state** or the export buttons on Imports & exports. The JSON export bundle includes a manifest and output objects. Manifest paths are relative paths within the export bundle and identify generated output records. You can also download `manifest.csv`.

## Files
- `index.html` — complete application.
- `data/README.md` — instructions for the required input files.
- `exports/` — place exported files here if you choose to save them locally.
