---
name: elmerfem-theory-and-methods
description: This skill should be used when users ask about theory and methods in elmerfem; it prioritizes documentation references and then source inspection only for unresolved details.
---

# elmerfem: Theory and Methods

## High-Signal Playbook
### Route Conditions
- Use this skill for method/formulation questions (shell theory, level set methods, calving numerics, iterative schemes).
- Route to `elmerfem-fem` for implementation-focused FEM module debugging.
- Route to `elmerfem-elmerice` for domain-specific cryosphere workflows.

### Canonical Workflow
1. Start from a benchmark case with documented expected behavior (`fem/tests/Shell_BenchmarkCase1_Quad/Readme.txt` or related shell cases).
2. Run baseline without edits and record primary quantities of interest.
3. Map theoretical claim -> solver block -> implementation file.
4. Change one method parameter at a time and compare trend against benchmark expectations.
5. Use `references/source_map.md` for direct routine-level inspection when documentation is not enough.

### Minimal Working Example
```bash
cd fem/tests/Shell_BenchmarkCase1_Quad
ElmerSolver shell_case1.sif
```

### Validation Checkpoints
- Baseline reproduces expected benchmark trend or magnitude window.
- Method parameter changes produce directionally consistent output changes.
- Numerical behavior is explainable from the mapped implementation routine(s).

## Scope
- Handle questions about theoretical background and algorithmic methods.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `fem/tests/Shell_BenchmarkCase2_Quad/Readme.txt`
- `fem/tests/Shell_BenchmarkCase1_Tria/Readme.txt`
- `fem/tests/Shell_BenchmarkCase1_Quad/Readme.txt`
- `fem/tests/Shell_BenchmarkCase1_ElementalDirector/Readme.txt`
- `fem/tests/Shell_BenchmarkCase2_Tria/Readme.txt`
- `elmerice/Tests/Calving3D_lset_parMMG/README.txt`
- `elmerice/Tests/Calving3D_lset/README.txt`
- `ReleaseNotes/release_5.2.txt`

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
- `elmerice/Solvers/Calving3D_lset.F90`
- `elmerice/Solvers/Calving3D.F90`
- `fem/src/view3d/16node_quad.c`
- `fem/src/IterativeMethods.F90`
- `fem/src/ClusteringMethods.F90`
- `fem/src/modules/ShellSolver.F90`
- `fem/src/modules/LevelSet/LevelSetSolver.F90`
- `fem/src/modules/contrib/ShellMultiSolver/ShellMultiSolver.F90`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" ElmerGUIlogger/src ElmerGUItester/src ElmerWorkflows/FreeCADBatchFEMTools elmergrid/src elmerice/Solvers elmerice/UserFunctions elmerice/Utils fem/src fhutiter/src matc/src mathlibs/src meshgen2d/src ElmerGUI/Application/src ElmerGUI/PythonQt/src`).
