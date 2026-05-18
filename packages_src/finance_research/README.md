# Finance Research – staging XMLs

This directory holds loose TotalAgility XML exports for the Finance Research connector before they are bundled into a release `.zip` for import.

## Files

- `CustomService_Finance.xml` – `you.com finance research` Custom Service definition.
- `WebServices_Finance.xml` – `youcom finance research` Web Service reference (`https://api.you.com/v1/finance_research`).
- `Process_Finance_V1.xml` – process map wiring the Custom Service to its inputs/outputs (`INPUT`, `RESEARCH_EFFORT`, `FINANCE_RESPONSE_DATA`, `STATUS_CODE`).

## Why this is here, not under `packages/`

The repo's documented import flow (see top-level `README.MD`) is to import a single `.zip` from `packages/` via **TotalAgility Designer → Settings → Import / Export → Import Package**. Dropping loose XML files into `packages/` breaks that flow and confuses operators following the README.

These files are kept here as *source* artefacts. To ship them:

1. Open the existing `packages/You.com TA connector package.zip` (or a fresh export) in TotalAgility Designer.
2. Add these three definitions via the Designer UI, or merge them into a new package export.
3. Replace / version `packages/You.com TA connector package.zip` with the resulting zip.

The three GUIDs in these files are real (32-char uppercase hex). The `CustomService_Finance.xml` `<Id>`, the `Process_Finance_V1.xml` `<mapid>`, and `parentprocessmapid` all share the same GUID so the Process references resolve to the Custom Service on import.
