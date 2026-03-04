---
name: elmerfem-elmergui
description: This skill should be used when users ask about elmergui in elmerfem; it prioritizes documentation references and then source inspection only for unresolved details.
---

# elmerfem: Elmergui

## High-Signal Playbook
### Route Conditions
- Use this skill for GUI-driven setup, parameter editing, and solver launch/log inspection.
- Route to `elmerfem-build-and-install` if GUI binaries or Qt dependencies are missing.
- Route to `elmerfem-simulation-workflows` when the question becomes full run orchestration.

### Canonical Workflow
1. Start from a known sample geometry/input (`ElmerGUI/samples/step` or `ElmerGUI/samples/in2d`).
2. Confirm GUI can open and keep project metadata consistent with solver input files.
3. Launch solver from GUI once and compare generated command/input with CLI run.
4. If GUI behavior differs from CLI results, inspect parameter serialization and solver-log handlers in `references/source_map.md`.

### Minimal Working Example
```bash
ElmerGUI
# then load one of:
#   ElmerGUI/samples/step/axle.step
#   ElmerGUI/samples/in2d/square.in2d
```

### Validation Checkpoints
- Project opens without import/parser errors.
- Generated solver input is runnable from CLI.
- GUI solver log window shows completion and expected outputs.

## Scope
- Handle questions about documentation grouped under the 'elmergui' theme.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `ElmerGUI/samples/step/README.txt`
- `ElmerGUI/samples/in2d/README.txt`

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
- `ElmerGUI/PythonQt/src/PythonQtImportFileInterface.h`
- `ElmerGUI/Application/src/solverparameters.h`
- `ElmerGUI/Application/src/solverparameters.cpp`
- `ElmerGUI/Application/src/solverlogwindow.h`
- `ElmerGUI/Application/src/solverlogwindow.cpp`
- `ElmerGUI/Application/src/materiallibrary.h`
- `ElmerGUI/Application/src/materiallibrary.cpp`
- `ElmerGUI/Application/src/mainwindow.h`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" ElmerGUIlogger/src ElmerGUItester/src ElmerWorkflows/FreeCADBatchFEMTools elmergrid/src elmerice/Solvers elmerice/UserFunctions elmerice/Utils fem/src fhutiter/src matc/src mathlibs/src meshgen2d/src ElmerGUI/Application/src ElmerGUI/PythonQt/src`).
