---
name: elmerfem-examples-and-tutorials
description: This skill should be used when users ask about examples and tutorials in elmerfem; it prioritizes documentation references and then source inspection only for unresolved details.
---

# elmerfem: Examples and Tutorials

## High-Signal Playbook
### Route Conditions
- Use this skill to pick/adapt a runnable example quickly.
- Route to `elmerfem-build-and-install` when required tools/libraries are missing.
- Route to `elmerfem-simulation-workflows` after example selection if the main question is run/restart orchestration.
- Route to `elmerfem-inputs-and-modeling` for deep SIF physics edits beyond template adaptation.

### Triage Questions
- Which physics family is the user targeting (SSA, Stokes, hydrology, mesh preprocessing, FEM verification)?
- Is a synthetic/self-contained case acceptable, or are external observation datasets required?
- Does the user need serial reproducibility first or direct MPI/partitioned execution?
- Is custom user-function compilation acceptable (`elmerf90-nosh`/`elmerf90`)?
- Is the goal demonstration, regression baseline, or parameter study template?
- What is the expected validation signal (cost decrease, norm target, NetCDF diff, visual field sanity)?

### Canonical Workflow
1. Map the request to the closest curated family:
   - inverse optimization: `elmerice/examples/Inverse_Methods/*/README.md`
   - mesh generation/deformation: `elmerice/examples/Test_MshGlacier*`
   - NetCDF output validation: `elmerice/examples/SaveGridDataNetCDF/README.txt`
2. Run the example exactly as documented once, without edits.
3. Capture baseline artifacts (`.result`, `.vtu`, generated meshes, scalar outputs).
4. Change one axis at a time (mesh resolution, regularization, solver tolerances, forcing data).
5. Keep the original case runnable as a control for regressions.
6. If behavior differs from docs, consult the topic `references/source_map.md` and inspect the listed solver/USF entry files.

### Minimal Working Example
```bash
# Inverse-method starter (Stokes Weertman)
ElmerGrid 1 2 rectangle
ElmerSolver Direct_nl.sif
ElmerSolver OPTIM_TWIND_nl.sif
```

```bash
# Mesh preprocessing starter (DEM serial path)
gmsh teterousse.geo -1 -2
ElmerGrid 14 2 teterousse.msh -autoclean
ExtrudeMesh teterousse WithOutCavity 14 1 1 0 0 0 0
./MshGlacierDEM
```

### Pitfalls/Fixes
- Several inverse-method cases need external datasets from `elmerice/examples/Inverse_Methods/DATA/`; verify dataset prep before running.
- `MacAyeal_*` and related scripts may expect pre-generated noisy observations; generate/prepare those first.
- In `StokesWeertman`, discrete twin experiments may not converge to zero cost with mismatched synthetic data generation path (documented caveat).
- DEM examples require platform-specific shared library extension (`.so` vs `.dylib`) for helper binaries.
- Partitioned DEM workflows require matching `-metis` partition count and extrusion/distribution settings.
- Legacy `InverseMethods_OLD` exists; prefer `Inverse_Methods` unless reproducing old papers.

### Convergence/Validation Checks
- Baseline run reproduces documented command sequence end-to-end without local edits.
- Optimization examples show monotonic/expected cost decrease over iterations.
- Mesh-generating examples produce expected mesh directories and post-processable outputs.
- Validation-style examples (for example NetCDF case) meet documented tolerance checks.
- Adapted case still matches baseline behavior when knobs are reset.

## Scope
- Handle questions about worked examples, tutorials, and cookbook usage.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `README.adoc`
- `elmerice/examples/Test_MshGlacierDEM/Serial/README.txt`
- `elmerice/examples/Test_MshGlacierDEM/Partitioned/README.txt`
- `elmerice/examples/Inverse_Methods/DATA/README.md`
- `elmerice/examples/Inverse_Methods/README.md`
- `elmerice/examples/Inverse_Methods/MassConservation/README.md`
- `elmerice/examples/InverseMethods_OLD/README.md`
- `elmerice/examples/Inverse_Methods/RonneFilchner_SSA/README.md`
- `elmerice/examples/Inverse_Methods/MacAyeal_Stokes/README.md`
- `elmerice/examples/Inverse_Methods/MacAyeal_SSA/README.md`
- `elmerice/examples/Inverse_Methods/MassConservation/src/README.md`
- `elmerice/examples/Inverse_Methods/MassConservation/Optimisation/README.md`
- `elmerice/examples/Inverse_Methods/MassConservation/GradientValidation/README.md`
- `elmerice/examples/Inverse_Methods/StokesWeertman/README.md`

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
- `elmerice/UserFunctions/USF_CouplingGlaDS_SSA.F90`
- `fem/src/modules/Stokes.F90`
- `elmerice/Solvers/Adjoint/Adjoint_GradientValidation.F90`
- `elmerice/Utils/SSAMaterialModels.F90`
- `fem/src/modules/DataToFieldSolver.F90`
- `elmerice/Solvers/SSASolver.F90`
- `fem/src/modules/ReynoldsSolver.F90`
- `elmerice/Solvers/ScatteredDataInterpolator/Scattered2D_FInterface.F90`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" ElmerGUIlogger/src ElmerGUItester/src ElmerWorkflows/FreeCADBatchFEMTools elmergrid/src elmerice/Solvers elmerice/UserFunctions elmerice/Utils fem/src fhutiter/src matc/src mathlibs/src meshgen2d/src ElmerGUI/Application/src ElmerGUI/PythonQt/src`).
