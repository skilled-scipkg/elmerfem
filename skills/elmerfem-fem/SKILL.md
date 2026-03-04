---
name: elmerfem-fem
description: This skill should be used when users ask about fem in elmerfem; it prioritizes documentation references and then source inspection only for unresolved details.
---

# elmerfem: Fem

## High-Signal Playbook
### Route Conditions
- Use this skill for core `fem/tests` finite-element verification and solver-module behavior.
- Route to `elmerfem-elmerice` for cryosphere-specific solver/user-function workflows.
- Route to `elmerfem-build-and-install` if the issue is compile/link/setup rather than model behavior.
- Route to `elmerfem-simulation-workflows` when the user asks for full run orchestration over multiple stages.

### Triage Questions
- Which family is in scope: shell/solid mechanics, UMAT/material modeling, EM/waveguide, or magnetodynamics?
- Is this about element formulation/order (`p`-FEM, Nedelec, shell basis) or solver settings?
- Do you need single-solver verification or coupled/multi-solver assembly (e.g., shell+solid)?
- Is the target serial correctness first, then parallel?
- Which error metric is the acceptance criterion (reference norm, relative energy error trend, field agreement)?
- Are custom modules/user subroutines involved?

### Canonical Workflow
1. Pick the nearest regression test in `fem/tests` and copy it unchanged.
2. Build mesh with `ElmerGrid` if required by the case run script or README (for example `fem/tests/p-FEM_with_varying_p/runtest.cmake`).
3. Run using `ELMERSOLVER_STARTINFO` and capture baseline outputs/logs.
4. Check the `Reference Norm` / tolerance encoded in SIF for pass criteria.
5. Modify one parameter family at a time (element order, quadrature, coupling choices).
6. Re-check error trends and norm targets against README expectations.
7. Escalate to `references/source_map.md` (for example `fem/src/modules/ShellSolver.F90`, `fem/src/modules/NormalSolver.F90`, `fem/src/SolidMechanicsUtils.F90`) when docs are insufficient.

### Minimal Working Example
```bash
# Variable-order p-FEM shell verification
ElmerGrid 1 2 eighth
ElmerSolver cylindrical_shell.sif
```

```bash
# UMAT-based isotropic 2D elasticity check
ElmerGrid 1 2 beam
ElmerSolver elasticity.sif
```

### Pitfalls/Fixes
- Variable-order `p`-basis with hanging DOFs is explicitly marked as still evolving in the test README; prefer conservative setups when debugging.
- If multiple solvers use different basis/order definitions, align bodywise `Element = "p:..."` rules carefully (`p-FEM_two_solvers` context).
- UMAT small-strain scanning cases should converge quickly; delayed convergence usually indicates material block mismatch.
- Shell/solid coupled benchmarks are sensitive to body IDs and boundary assignment; verify target boundaries before solver tuning.
- EM waveguide checks depend on element family/order; wrong family can destroy expected convergence-rate behavior.

### Convergence/Validation Checks
- `Reference Norm` targets in SIF are met within tolerance.
- Relative energy error trend in p-FEM README is monotonic with increased order (up to expected plateau).
- For waveguide cases, measured refinement rates match the documented order trends.
- `ctest -R <testname>` passes after each material/element change.
- Coupled shell-solid case agrees with pure-shell benchmark expectations.

## Scope
- Handle questions about documentation grouped under the 'fem' theme.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `README.adoc`
- `fem/tests/p-FEM_with_varying_p/README.txt`
- `fem/tests/p-FEM_two_solvers/README.txt`
- `fem/tests/mgdyn_faraday_wheel/Readme.txt`
- `fem/tests/mgdyn_faraday_disc_transient/Readme.txt`
- `fem/tests/mgdyn_faraday_disc/Readme.txt`
- `fem/tests/mgdyn_bh_gauge/Readme.txt`
- `fem/tests/elasticity_with_springs/Readme.txt`
- `fem/tests/VectorHelmholtzWaveguide_TM/Readme.md`
- `fem/tests/UMAT_linear_isotropic_2D/Readme.txt`
- `fem/tests/UMAT_StVenant_axials/Readme.txt`
- `fem/tests/UMAT_StVenant_2D/Readme.txt`
- `fem/tests/Shell_with_Solid_BenchmarkCase2/Readme.txt`
- `fem/tests/ElmerSolver_cmake_test-how-to.txt`

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
- `elmerice/Solvers/MeshAdaptation_2D/Compute2DNodalGradient.F90`
- `fem/src/modules/NormalSolver.F90`
- `elmerice/Solvers/MeshAdaptation_2D/MMG2DSolver.F90`
- `fem/src/view3d/2d_4node.c`
- `fem/src/view3d/16node_quad.c`
- `elmerice/Solvers/Permafrost/Permafrost_solid.F90`
- `elmerice/Solvers/MeshAdaptation_2D/MMG2D_MetricIntersect.F90`
- `elmerice/Solvers/MeshAdaptation_2D/MMG2D_MetricAniso.F90`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" ElmerGUIlogger/src ElmerGUItester/src ElmerWorkflows/FreeCADBatchFEMTools elmergrid/src elmerice/Solvers elmerice/UserFunctions elmerice/Utils fem/src fhutiter/src matc/src mathlibs/src meshgen2d/src ElmerGUI/Application/src ElmerGUI/PythonQt/src`).
