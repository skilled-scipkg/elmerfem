---
name: elmerfem-troubleshooting
description: This skill should be used when users ask about troubleshooting in elmerfem; it prioritizes documentation references and then source inspection only for unresolved details.
---

# elmerfem: Troubleshooting

## High-Signal Playbook
### Route Conditions
- Use this skill for build/runtime failures, solver divergence, missing outputs, or regression drift.
- Route to `elmerfem-build-and-install` if the issue is unresolved dependency/configuration setup.
- Route to `elmerfem-inputs-and-modeling` if the error is clearly due to wrong physical model wiring.

### Canonical Workflow
1. Reproduce with the smallest available case and unedited inputs.
2. Capture exact failing command, terminal output, and final 100 lines of solver log.
3. Classify failure: configure/link, input parse, solver convergence, or post-processing mismatch.
4. Run nearest regression (`ctest -R <case>` or documented test command) before changing physics knobs.
5. If behavior is still unexplained, inspect solver entry points in `references/source_map.md`.

### Minimal Working Example
```bash
cd elmerice/Tests/SSA_Weertman
ElmerGrid 1 2 rectangle.grd
ElmerSolver ismip_SSA_2D_Weertman.sif
```

### Validation Checkpoints
- Failure reproduces consistently from a clean run.
- At least one neighboring baseline case passes.
- Root cause category is identified before applying fixes.

## Scope
- Handle questions about known issues, diagnostics, and debugging patterns.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `elmerice/Solvers/Documentation/ISCAL.md`

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
- `elmerice/Solvers/Covarianceutils/BackgroundErrorCostSolver.F90`
- `elmerice/Solvers/Covarianceutils/GaussianSimulationSolver.F90`
- `elmerice/Solvers/ThicknessSolver.F90`
- `elmerice/Solvers/SurfaceBoundaryEnthalpy.F90`
- `elmerice/Solvers/SSASolver.F90`
- `elmerice/Solvers/SIASolver.F90`
- `elmerice/Solvers/PlumeSolver.F90`
- `elmerice/Solvers/MMG3DSolver.F90`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" ElmerGUIlogger/src ElmerGUItester/src ElmerWorkflows/FreeCADBatchFEMTools elmergrid/src elmerice/Solvers elmerice/UserFunctions elmerice/Utils fem/src fhutiter/src matc/src mathlibs/src meshgen2d/src ElmerGUI/Application/src ElmerGUI/PythonQt/src`).
