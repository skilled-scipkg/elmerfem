---
name: elmerfem-releasenotes
description: This skill should be used when users ask about releasenotes in elmerfem; it prioritizes documentation references and then source inspection only for unresolved details.
---

# elmerfem: Releasenotes

## High-Signal Playbook
### Route Conditions
- Use this skill for version-to-version behavior changes, feature introductions, and migration risk assessment.
- Route to `elmerfem-build-and-install` if differences are build/configuration regressions.
- Route to the affected domain skill after identifying the changed subsystem.

### Canonical Workflow
1. Identify target versions and collect relevant notes from `ReleaseNotes/` and `elmerice/ReleaseNotes/`.
2. Map each release-note item to impacted tests/examples.
3. Re-run a minimal baseline case before and after the relevant change set.
4. Confirm whether behavior delta is expected, fixed, or regression.
5. Use `references/source_map.md` only when release notes are insufficient to localize impact.

### Minimal Working Example
```bash
rg -n \"(SSA|MUMPS|NetCDF|XIOS|adjoint|shell)\" ReleaseNotes elmerice/ReleaseNotes
ctest -L quick -j2
```

### Validation Checkpoints
- Claimed release-note changes are reproducible in matching test areas.
- No silent regression in unaffected baseline tests.
- Migration advice references exact release-note files and impacted cases.

## Scope
- Handle questions about documentation grouped under the 'releasenotes' theme.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `ReleaseNotes/release_5.4.txt`
- `ReleaseNotes/release_26.1.md`
- `ReleaseNotes/release_5.3.txt`
- `ReleaseNotes/release_ElmerGUI.txt`
- `ReleaseNotes/release_5.0.txt`

## Workflow
- Start with the primary references above.
- If details are missing, inspect `references/doc_map.md` for the complete topic document list.
- Use tutorials/examples as executable usage patterns when available.
- Use tests as behavior or regression references when available.
- If ambiguity remains after docs, inspect `references/source_map.md` and start with the ranked source entry points.
- Cite exact documentation file paths in responses.

## Tutorials and examples
- `ElmerGUI/samples`
- `elmerice/examples`
- `fem/examples`
- `fhutiter/examples`

## Test references
- `elmergrid/tests`
- `elmerice/Tests`
- `fem/tests`
- `ElmerWorkflows/FreeCADBatchFEMTools/tests`
- `fem/src/binio/test`

## Optional deeper inspection
- `ElmerGUIlogger/src`
- `ElmerGUItester/src`
- `ElmerWorkflows/FreeCADBatchFEMTools`
- `elmergrid/src`
- `elmerice/Solvers`
- `elmerice/UserFunctions`
- `elmerice/Utils`
- `fem/src`
- `fhutiter/src`
- `matc/src`
- `mathlibs/src`
- `meshgen2d/src`
- `ElmerGUI/Application/src`
- `ElmerGUI/PythonQt/src`

## Source entry points for unresolved issues
- `fem/src/ElmerSolver.F90`
- `fem/src/modules/ShellSolver.F90`
- `elmerice/Solvers/SSASolver.F90`
- `elmerice/Solvers/GridDataReader/GridDataReader.F90`
- `elmerice/Solvers/OutPutSolvers/XIOSOutputSolver.F90`
- `elmergrid/src/egparallel.c`
- `ElmerGUI/Application/src/solverparameters.cpp`
- `ElmerGUI/Application/src/mainwindow.cpp`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" ElmerGUIlogger/src ElmerGUItester/src ElmerWorkflows/FreeCADBatchFEMTools elmergrid/src elmerice/Solvers elmerice/UserFunctions elmerice/Utils fem/src fhutiter/src matc/src mathlibs/src meshgen2d/src ElmerGUI/Application/src ElmerGUI/PythonQt/src`).
