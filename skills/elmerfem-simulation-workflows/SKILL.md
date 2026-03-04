---
name: elmerfem-simulation-workflows
description: This skill should be used when users ask about simulation workflows in elmerfem; it prioritizes documentation references and then source inspection only for unresolved details.
---

# elmerfem: Simulation Workflows

## High-Signal Playbook
### Route Conditions
- Use this skill for end-to-end run execution (mesh -> solver -> restart -> output checks).
- Route to `elmerfem-build-and-install` if binaries/dependencies are not ready.
- Route to `elmerfem-inputs-and-modeling` when the blocker is SIF physics wiring, not run orchestration.
- Route to `elmerfem-parallel-hpc` for scheduler/NUMA/MPI launcher tuning on clusters.

### Triage Questions
- Is this a serial run, MPI run, or both?
- What is the mesh origin (`.grd`, `.msh`, prebuilt Elmer mesh directory)?
- Are partitions required, and does partition count match `mpirun -np`?
- Is this a fresh run or a restart from a `.result` file (`Restart File`, `Restart Before Initial Conditions`)?
- Are NetCDF/XIOS-dependent paths required (for `elmerice/Solvers/GridDataReader/GridDataReader.F90` / SaveGridData)?
- What output artifact is the acceptance criterion (`.result`, `.vtu`, NetCDF diff, scalar checks)?

### Canonical Workflow
1. Start from an existing test/example README with explicit run commands (`elmerice/Tests/GlaDS_3dMesh/README.txt`, `elmerice/examples/Inverse_Methods/StokesWeertman/README.md`).
2. Generate/convert mesh with `ElmerGrid`; if partitioned, partition first and run any distribution helper scripts (`makemoulin.py`) before solving.
3. Validate the SIF linear solver path for MPI (for several GlaDS cases, replace UMFPACK with MUMPS in multi-partition runs).
4. Run base simulation (`ElmerSolver` or `mpirun ... ElmerSolver_mpi`).
5. For restart/optimization stages, run the direct/initial stage first, then point follow-up stage to the produced `.result` file.
6. Check primary outputs (`.result`, `.vtu`, NetCDF) plus README-specific checks (for example NCO `ncdiff` threshold in `elmerice/examples/SaveGridDataNetCDF/README.txt`).
7. If docs are insufficient, escalate to `references/source_map.md` entry points (`elmerice/Solvers/GridDataReader/GridDataReader.F90`, `elmerice/UserFunctions/USF_CouplingGlaDS_SSA.F90`, `elmerice/Solvers/SSASolver.F90`).

### Minimal Working Example
```bash
# Parallel GlaDS workflow
ElmerGrid 2 2 mesh_B5_3d -partition 2 1 1
python makemoulin.py --meshdir mesh_B5_3d --moulin B5_M.xy --partition 2
mpirun -np 2 ElmerSolver_mpi glads_3dmesh.sif
```

```bash
# Two-stage restart workflow (direct -> optimization)
ElmerGrid 1 2 rectangle
ElmerSolver Direct_nl.sif
ElmerSolver OPTIM_TWIND_nl.sif
```

### Pitfalls/Fixes
- MPI run with partitioned mesh but UMFPACK left enabled in SIF can fail or stall; switch to MUMPS as noted in GlaDS READMEs.
- Partitioned hydrology examples require moulin redistribution (`makemoulin.py`) after partitioning.
- Regenerating benchmark meshes with newer `gmsh` may alter results; GlaDS READMEs note mesh reproducibility constraints.
- Restart stage fails if the direct stage output file name/path does not match `Restart File` in follow-up SIF.
- NetCDF validation workflows require NetCDF-enabled build and NCO tools (`ncdiff`, `ncap2`) for comparison.
- `mpirun -np` must match available mesh partitioning directory (`partitioning.N`).

### Convergence/Validation Checks
- Solver log reaches completion without `Abort Not Converged` paths for critical solvers.
- Expected output files exist (`*.result`, `*.vtu`, or NetCDF file in mesh directory).
- For `SaveGridDataNetCDF`, max diff is within README threshold (`<= 10e-6`).
- For ForceToStress tests, `Stress` and `StressAna` agree on the prescribed boundary.
- Restart stage reproduces/continues expected fields rather than reinitializing from zero.

## Scope
- Handle questions about simulation setup, execution flow, and runtime controls.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `README.adoc`
- `elmerice/Tests/GlaDS_3dMesh/README.txt`
- `elmerice/Tests/GlaDS_3dInt/README.txt`
- `elmerice/Tests/GlaDS_2d/README.txt`
- `elmerice/examples/Inverse_Methods/StokesWeertman/README.md`
- `elmerice/examples/Inverse_Methods/RonneFilchner2_SSA/README.md`
- `elmerice/Tests/GridDataReader/README.txt`
- `elmerice/Tests/FrictionHeat/README.txt`
- `elmerice/Tests/ExportVertically/README.txt`
- `elmerice/Tests/Enthalpy/README.txt`
- `elmerice/Tests/EigenValues/README.txt`
- `elmerice/Tests/DGsolver/README.txt`
- `elmerice/examples/SaveGridDataNetCDF/README.txt`
- `elmerice/Tests/ForceToStress/README.txt`
- `elmerice/Tests/ForceToStress_parallel/README.txt`

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
- `elmerice/Solvers/Weertman2Coulomb.F90`
- `elmerice/Solvers/MeshAdaptation_2D/MMG2DSolver.F90`
- `elmerice/UserFunctions/USF_CouplingGlaDS_SSA.F90`
- `elmerice/Solvers/ForceToStress.F90`
- `elmerice/Solvers/ExportVertically.F90`
- `elmerice/Solvers/ComputeDevStress.F90`
- `elmerice/Solvers/MeshAdaptation_2D/MMG2D_MetricIntersect.F90`
- `elmerice/Solvers/MeshAdaptation_2D/MMG2D_MetricAniso.F90`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" ElmerGUIlogger/src ElmerGUItester/src ElmerWorkflows/FreeCADBatchFEMTools elmergrid/src elmerice/Solvers elmerice/UserFunctions elmerice/Utils fem/src fhutiter/src matc/src mathlibs/src meshgen2d/src ElmerGUI/Application/src ElmerGUI/PythonQt/src`).
