---
name: elmerfem-elmerice
description: This skill should be used when users ask about elmerice in elmerfem; it prioritizes documentation references and then source inspection only for unresolved details.
---

# elmerfem: Elmerice

## High-Signal Playbook
### Route Conditions
- Use this skill for Elmer/Ice solver-family selection and test/example execution.
- Route to `elmerfem-api-and-scripting` when the request is mainly about writing/modifying USFs.
- Route to `elmerfem-simulation-workflows` for multi-stage restart pipelines and broader run orchestration.
- Route to `elmerfem-build-and-install` if required ElmerIce components are not compiled/enabled.

### Triage Questions
- Which ElmerIce mode is needed (SSA/SIA/Stokes, hydrology, interpolation, calving, grounded/contact)?
- Is the case self-contained or does it need external datasets/user programs?
- Serial or MPI execution?
- Which mesh format is available (`.grd`, `.msh`, existing mesh dir)?
- What output variable defines success (velocity, grounded mask, stress, interpolated field)?
- Is this a new case from scratch or adaptation of an existing `elmerice/Tests` directory?

### Canonical Workflow
1. Choose the nearest `elmerice/Tests/*/README.txt` case and run it unchanged once.
2. Build/convert mesh with `ElmerGrid` exactly as documented.
3. Compile helper programs/USFs only if the test requires them (for example `elmerice/Tests/Grounded/PROG/*`).
4. Run `ElmerSolver` (or MPI variant when required).
5. Validate against test-specific checks in README or SIF `Reference Norm`/`SaveScalars` outputs.
6. Then adapt physics knobs (friction law, grounded handling, interpolation settings) one at a time.
7. If docs are insufficient, jump to `references/source_map.md` entry points (`elmerice/Solvers/SSASolver.F90`, `elmerice/Solvers/GroundedSolver.F90`, `elmerice/Solvers/Grid2DInterpolator.F90`, `elmerice/Solvers/GlaDSCoupledSolver.F90`).

### Minimal Working Example
```bash
# SSA friction-law verification
ElmerGrid 1 2 rectangle.grd
ElmerSolver ismip_SSA_2D_Weertman.sif
```

```bash
# Grounded test with helper functions
elmerf90 ./elmerice/Tests/Grounded/PROG/bedrock.f90 ./elmerice/Tests/Grounded/PROG/fbed.f90 -o bedrock
ElmerGrid 1 2 Cube.grd
ElmerSolver grounded.sif
```

### Pitfalls/Fixes
- Some tests depend on compiled helper sources under `elmerice/Tests/Grounded/PROG/`; if skipped, runtime variables are missing.
- `Grid2DInterpolator` runs are sensitive to mesh import/order options; follow README command flags exactly.
- XIOS-related tests require XIOS-enabled build and matching runtime config files.
- Similar SSA cases (Weertman/Coulomb) differ only in friction law; accidental SIF mix-ups are common.
- Hydrology/coupled tests may need stricter consistency in BC and physical parameter sections than generic FEM cases.

### Convergence/Validation Checks
- README command sequence reproduces successfully before any local edits.
- Expected fields are present in output (`SaveScalars`/result variables tied to the test objective).
- Grounded/contact-style tests meet qualitative README checks (for example bed-contact evolution).
- `ctest -L elmerice-fast` passes after local modifications when available.
- For friction-law swaps, compare velocity/stress behavior across Weertman vs Coulomb reference tests.

## Scope
- Handle questions about documentation grouped under the 'elmerice' theme.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `README.adoc`
- `elmerice/Tests/Grid2DInterpolator/README.txt`
- `elmerice/Tests/Xios2/README.txt`
- `elmerice/Tests/Teterousse_DeformHeat/README.txt`
- `elmerice/Tests/Teterousse3a/README.txt`
- `elmerice/Tests/SSA_Weertman/README.txt`
- `elmerice/Tests/SSA_IceSheet/README.txt`
- `elmerice/Tests/SSA_Coulomb/README.txt`
- `elmerice/Tests/IntegratedVelocity/README.txt`
- `elmerice/Tests/IntegrateVertically/README.txt`
- `elmerice/Tests/Grounded/README.txt`
- `elmerice/Tests/Glen_2D/README.txt`
- `elmerice/Tests/GlaDS_SSA/README.txt`
- `elmerice/Solvers/Documentation/SSASolvers_part.md`

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
- `elmerice/Solvers/Grid2DInterpolator.F90`
- `elmerice/Solvers/MeshAdaptation_2D/MMG2DSolver.F90`
- `elmerice/UserFunctions/USF_Contact.F90`
- `elmerice/Solvers/IntegrateVertically.F90`
- `elmerice/Solvers/IntegratedVelocity.F90`
- `elmerice/Solvers/Calving3D_lset.F90`
- `elmerice/Solvers/Calving3D.F90`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" ElmerGUIlogger/src ElmerGUItester/src ElmerWorkflows/FreeCADBatchFEMTools elmergrid/src elmerice/Solvers elmerice/UserFunctions elmerice/Utils fem/src fhutiter/src matc/src mathlibs/src meshgen2d/src ElmerGUI/Application/src ElmerGUI/PythonQt/src`).
