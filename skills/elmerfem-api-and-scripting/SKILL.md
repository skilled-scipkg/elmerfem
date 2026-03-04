---
name: elmerfem-api-and-scripting
description: This skill should be used when users ask about api and scripting in elmerfem; it prioritizes documentation references and then source inspection only for unresolved details.
---

# elmerfem: API and Scripting

## High-Signal Playbook
### Route Conditions
- Use this skill for Elmer/Ice solver/user-function interface wiring, extension points, and scripting hooks.
- Route to `elmerfem-elmerice` when the user only needs to run existing tests/examples without API changes.
- Route to `elmerfem-build-and-install` if compile/link of user code or optional components is failing.
- Route to `elmerfem-simulation-workflows` for multi-stage run orchestration after API pieces are wired.

### Triage Questions
- Are you using an existing USF/solver or authoring a new one?
- Where is the hook point: `Body Force`, `Boundary Condition`, `Material`, or `Solver` block?
- Which variables are required as inputs/outputs, and what are their exact SIF names?
- Should this run in serial only or MPI too?
- Do you need on-the-fly shared-object compilation (`elmerf90`) or full tree rebuild?
- What validation test will prove the interface wiring is correct?

### Canonical Workflow
1. Start from documentation templates and an existing nearest function (`elmerice/UserFunctions/Documentation/*.md`, `elmerice/Solvers/Documentation/*.md`).
2. Copy the documented SIF fragment verbatim first (procedure names, variable names, required keywords).
3. Implement/modify Fortran in `elmerice/UserFunctions` or `elmerice/Solvers` and keep symbol names aligned with SIF.
4. Compile either as external module (`elmerf90 ...`) or via CMake-integrated build path.
5. Run the smallest matching test (`Proj_South`, `ShapeFactor`, `LateralFriction`, etc.) before integrating into larger models.
6. Add `SaveScalars`/output probes and compare against documented expectations.
7. If behavior differs from docs, inspect the listed source entry files directly (`elmerice/UserFunctions/USF_*`, `elmerice/Solvers/Calving3D*.F90`, `elmerice/Solvers/ScatteredDataInterpolator/Scattered2DDataInterpolator.F90`).

### Minimal Working Example
```text
Body Force 1
  Internal Melt = Logical True
  Surface Melt = Logical True
  Hydraulic Potential Volume Source = Variable temp
    Real Procedure "ElmerIceUSFs" "SourceCalc"
  Internal Melt Variable Name = String "temp residual"
  Surface Melt Variable Name = String "runoff"
End
```

```bash
ElmerGrid 1 2 rectangle.grd
ElmerSolver Case.sif   # elmerice/Tests/Proj_South
```

### Pitfalls/Fixes
- Procedure/library names must match exactly between SIF and compiled symbols; small naming drift causes runtime lookup failures.
- `getFrictionLoads` and legacy `getFrictionHeat` differ in units (W vs W/m2); copy the correct BC/body-force pattern from docs.
- Friction-load restart workflows still need the Stokes solver block present (`Exec Solver = Never` is acceptable), per documentation.
- `SourceCalc` assumes hydraulic-potential variable naming conventions from its documentation; renaming can silently break coupling.
- Missing normals/loads export in SIF can make friction-related USFs appear "working" but return unusable outputs.

### Convergence/Validation Checks
- The minimal associated test (`Proj_South`, `ShapeFactor`, `LateralFriction`) runs without unresolved symbol/procedure errors.
- Expected output variables are present and non-trivial in result files.
- Scalar/reference checks in the test case remain within tolerance after API edits.
- Restart-aware API hooks (if used) produce identical behavior between fresh and restart paths.
- Source and doc signatures remain aligned (argument/keyword names unchanged unless all call sites updated).

## Scope
- Handle questions about language bindings, APIs, and programmatic interfaces.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `README.adoc`
- `elmerice/Tests/Proj_South/README.txt`
- `elmerice/Tests/ShapeFactor/README.txt`
- `elmerice/Tests/LateralFriction/README.txt`
- `fem/tests/SD_Classical2DShell/README.txt`
- `fem/tests/Classical2DShell/README.txt`
- `ReleaseNotes/release_8.1.txt`
- `ReleaseNotes/release_8.0.txt`
- `elmerice/UserFunctions/Documentation/SourceCalcCalving.md`
- `elmerice/UserFunctions/Documentation/Template.md`
- `elmerice/UserFunctions/Documentation/FrictionLoads.md`
- `elmerice/Solvers/Documentation/Template.md`
- `elmerice/Solvers/Documentation/Scattered2DDataInterpolator.md`

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
- `elmerice/UserFunctions/USF_SourceCalcCalving.F90`
- `elmerice/UserFunctions/USF_ShapeFactor.F90`
- `elmerice/UserFunctions/USF_proj.F90`
- `elmerice/UserFunctions/USF_LateralFriction.F90`
- `elmerice/UserFunctions/USF_IceProperties.F90`
- `elmerice/UserFunctions/USF_Damage.F90`
- `elmerice/Solvers/CalvingGlacierAdvance3D.F90`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" ElmerGUIlogger/src ElmerGUItester/src ElmerWorkflows/FreeCADBatchFEMTools elmergrid/src elmerice/Solvers elmerice/UserFunctions elmerice/Utils fem/src fhutiter/src matc/src mathlibs/src meshgen2d/src ElmerGUI/Application/src ElmerGUI/PythonQt/src`).
