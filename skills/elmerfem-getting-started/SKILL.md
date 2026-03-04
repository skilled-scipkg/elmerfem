---
name: elmerfem-getting-started
description: This skill should be used when users ask about getting started in elmerfem; it prioritizes documentation references and then source inspection only for unresolved details.
---

# elmerfem: Getting Started

## High-Signal Playbook
### Route Conditions
- Use this skill for first successful run setup, solver sanity checks, and basic tool orientation.
- Route to `elmerfem-build-and-install` if binaries (`ElmerSolver`, `ElmerGrid`) are missing.
- Route to `elmerfem-simulation-workflows` once a baseline case runs and multi-stage workflows are needed.

### Canonical Workflow
1. Confirm binaries are visible in `PATH` (`ElmerSolver`, `ElmerGrid`, and optionally `ElmerSolver_mpi`).
2. Run one known-good starter case unchanged (`elmerice/Tests/SSA_Weertman/README.txt`).
3. Validate expected artifacts (`.result` file, non-empty solver log).
4. Only after baseline success, begin edits in a copied case directory.
5. Escalate unresolved behavior to `references/source_map.md`.

### Minimal Working Example
```bash
cd elmerice/Tests/SSA_Weertman
ElmerGrid 1 2 rectangle.grd
ElmerSolver ismip_SSA_2D_Weertman.sif
```

### Validation Checkpoints
- `ElmerSolver` exits normally and writes a result file.
- Solver log does not end in convergence abort for the starter test.
- Re-running without edits is reproducible.

## Scope
- Handle questions about initial setup, quickstarts, and core concepts.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `elmerice/Solvers/Documentation/Introduction.md`
- `elmerice/Solvers/Documentation/Adjoint_LinearSolver.md`
- `elmerice/Solvers/Documentation/AdjointSSA_SSASolver.md`
- `elmerice/Solvers/Documentation/Adjoint_CostRegSolver.md`
- `elmerice/Solvers/Documentation/Adjoint_CostContSolver.md`
- `elmerice/ReleaseNotes/release_elmerice_9.0.md`
- `elmerice/Solvers/Documentation/Adjoint_GradientValidation.md`
- `elmerice/Solvers/Documentation/AdjointSSA_CostTaubSolver.md`
- `elmerice/Solvers/Documentation/Optimize_m1qn3.md`
- `elmerice/Solvers/Documentation/Adjoint_CostDiscSolver.md`
- `elmerice/Solvers/Documentation/AdjointThickness_ThicknessSolver.md`
- `elmerice/Solvers/Documentation/AdjointSSA_GradientSolver.md`

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
- `elmerice/Solvers/Scalar_OUTPUT_Glacier.F90`
- `elmerice/Solvers/AdjointThickness/AdjointThickness_ThicknessSolver.F90`
- `elmerice/Solvers/AdjointThickness/AdjointThickness_GradientSolver.F90`
- `elmerice/Solvers/AdjointStokes/AdjointStokes_GradientBetaSolver.F90`
- `elmerice/Solvers/AdjointSSA/AdjointSSA_SSASolver.F90`
- `elmerice/Solvers/AdjointSSA/AdjointSSA_GradientSolver.F90`
- `elmerice/Solvers/AdjointSSA/AdjointSSA_CostTaubSolver.F90`
- `elmerice/Solvers/AdjointSSA/AdjointSSA_CostRegSolver.F90`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" ElmerGUIlogger/src ElmerGUItester/src ElmerWorkflows/FreeCADBatchFEMTools elmergrid/src elmerice/Solvers elmerice/UserFunctions elmerice/Utils fem/src fhutiter/src matc/src mathlibs/src meshgen2d/src ElmerGUI/Application/src ElmerGUI/PythonQt/src`).
