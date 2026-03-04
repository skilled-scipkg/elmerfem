---
name: elmerfem-parallel-hpc
description: This skill should be used when users ask about parallel and hpc in elmerfem; it prioritizes documentation references and then source inspection only for unresolved details.
---

# elmerfem: Parallel and HPC

## High-Signal Playbook
### Route Conditions
- Use this skill for partitioning, MPI launcher choices, and cluster execution stability/performance.
- Route to `elmerfem-build-and-install` if MPI-enabled binaries were not built.
- Route to `elmerfem-simulation-workflows` for non-HPC run orchestration questions.

### Canonical Workflow
1. Pick a documented MPI case (`elmerice/Tests/GlaDS_3dMesh/README.txt`).
2. Partition mesh first, then run auxiliary redistribution scripts if required (`makemoulin.py` in GlaDS).
3. Match `mpirun -np N` with `partitioning.N`.
4. For partitioned direct solves, switch SIF linear solver settings as recommended (for example UMFPACK -> MUMPS in GlaDS docs).
5. Validate outputs and compare against serial/baseline behavior.

### Minimal Working Example
```bash
ElmerGrid 2 2 elmerice/Tests/GlaDS_3dMesh/mesh_B5_3d -partition 2 1 1
python elmerice/Tests/GlaDS_3dMesh/makemoulin.py --meshdir elmerice/Tests/GlaDS_3dMesh/mesh_B5_3d --moulin elmerice/Tests/GlaDS_3dMesh/B5_M.xy --partition 2
mpirun -np 2 ElmerSolver_mpi elmerice/Tests/GlaDS_3dMesh/glads_3dmesh.sif
```

### Validation Checkpoints
- Partition directory exists and matches MPI rank count.
- MPI run reaches completion without immediate divergence.
- Core outputs match expected structure (`.result`, `.vtu`, or NetCDF artifacts depending on case).

## Scope
- Handle questions about MPI/OpenMP/GPU execution, scaling, and batch systems.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `elmerice/Solvers/Documentation/GridDataReader.md`
- `compilation_instructions/macOS.md`
- `compilation_instructions/Ubuntu.md`

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
- `elmerice/Solvers/GridDataReader/GridDataReader.F90`
- `elmerice/Solvers/GridDataReader/CMakeLists.txt`
- `elmerice/Solvers/UGridDataReader.F90`
- `elmerice/Solvers/Optimize_m1qn3Parallel.F90`
- `elmerice/Solvers/Covarianceutils/GaussianSimulationSolver.F90`
- `elmerice/Solvers/ThicknessSolver.F90`
- `elmerice/Solvers/SurfaceBoundaryEnthalpy.F90`
- `elmerice/Solvers/SSASolver.F90`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" ElmerGUIlogger/src ElmerGUItester/src ElmerWorkflows/FreeCADBatchFEMTools elmergrid/src elmerice/Solvers elmerice/UserFunctions elmerice/Utils fem/src fhutiter/src matc/src mathlibs/src meshgen2d/src ElmerGUI/Application/src ElmerGUI/PythonQt/src`).
