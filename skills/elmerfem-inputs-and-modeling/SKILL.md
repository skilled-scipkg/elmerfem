---
name: elmerfem-inputs-and-modeling
description: This skill should be used when users ask about inputs and modeling in elmerfem; it prioritizes documentation references and then source inspection only for unresolved details.
---

# elmerfem: Inputs and Modeling

## High-Signal Playbook
### Route Conditions
- Use this skill for SIF modeling changes: materials, body forces, boundary conditions, and solver block wiring.
- Route to `elmerfem-simulation-workflows` when orchestration/restart is the main issue.
- Route to `elmerfem-api-and-scripting` when custom user functions are required.

### Canonical Workflow
1. Start from a case with documented commands and known output (`elmerice/Tests/Grid2DInterpolator/README.txt`).
2. Keep one baseline SIF file untouched and clone a second file for edits.
3. Change one model axis at a time (friction law, enthalpy coupling, interpolation settings).
4. Add scalar/output checks for each change before moving on.
5. If a keyword effect is unclear, inspect the matching solver implementation in `references/source_map.md`.

### Minimal Working Example
```bash
ElmerGrid 14 2 elmerice/Tests/Grid2DInterpolator/teterousse1a.msh -autoclean -order 1.0 0.1 0.01
ElmerSolver elmerice/Tests/Grid2DInterpolator/teterousse1a.sif
```

### Validation Checkpoints
- Baseline and edited SIF runs both complete.
- Expected modeled variable exists and changes in the intended direction.
- No unintended drift when reverting edited keywords.

## Scope
- Handle questions about inputs, system setup, models, and physical parameterization.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `elmerice/Solvers/Documentation/README.md`
- `elmerice/examples/Test_SurfaceBoundaryEnth/README.md`
- `ReleaseNotes/release_9.0.md`
- `ReleaseNotes/release_8.4.txt`
- `ReleaseNotes/release_8.4.md`
- `ReleaseNotes/release_7.0.txt`
- `elmerice/Solvers/Documentation/AIFlowSolve.md`
- `elmerice/Solvers/Documentation/PlumeSolver.md`
- `elmerice/Solvers/Documentation/HydrologyGlaDS.md`
- `elmerice/Solvers/Documentation/SurfaceBoundaryEnthalpy.md`
- `elmerice/Solvers/Documentation/Grid2DInterpolator.md`
- `elmerice/Utils/Documentation/SSAMaterialModels.md`

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
- `elmerice/Utils/SSAMaterialModels.F90`
- `elmerice/Solvers/SurfaceBoundaryEnthalpy.F90`
- `elmerice/Utils/PorousMaterialModels.F90`
- `elmerice/Solvers/CalvingGeometry.F90`
- `elmerice/Solvers/PlumeSolver.F90`
- `elmerice/Solvers/Grid2DInterpolator.F90`
- `elmerice/Solvers/AIFlowSolve_nlS2.F90`
- `elmerice/Solvers/AIFlowSolve_nlD2.F90`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" ElmerGUIlogger/src ElmerGUItester/src ElmerWorkflows/FreeCADBatchFEMTools elmergrid/src elmerice/Solvers elmerice/UserFunctions elmerice/Utils fem/src fhutiter/src matc/src mathlibs/src meshgen2d/src ElmerGUI/Application/src ElmerGUI/PythonQt/src`).
