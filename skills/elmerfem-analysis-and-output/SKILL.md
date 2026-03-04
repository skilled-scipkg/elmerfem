---
name: elmerfem-analysis-and-output
description: This skill should be used when users ask about analysis and output in elmerfem; it prioritizes documentation references and then source inspection only for unresolved details.
---

# elmerfem: Analysis and Output

## High-Signal Playbook
### Route Conditions
- Use this skill for result extraction, output format checks, and post-run validation metrics.
- Route to `elmerfem-simulation-workflows` if the run itself is not completing yet.
- Route to `elmerfem-parallel-hpc` for MPI/XIOS runtime launch issues.

### Canonical Workflow
1. Select an output-focused reference case (`elmerice/examples/SaveGridDataNetCDF/README.txt`, `elmerice/Tests/Xios/README.txt`).
2. Run the case unchanged once and archive outputs.
3. Apply one output-format or post-processing change at a time.
4. Compare against reference using documented tolerance checks.
5. Escalate to `references/source_map.md` when field naming/connectivity behavior is unclear.

### Minimal Working Example
```bash
ElmerGrid 2 2 elmerice/examples/SaveGridDataNetCDF/Syn1Mesh -partition 4 1 1
mpirun -np 4 ElmerSolver_mpi elmerice/examples/SaveGridDataNetCDF/SaveGridDataNetCDFTest.sif
ncdiff -O elmerice/examples/SaveGridDataNetCDF/NetCDFTest_ref.nc Syn1Mesh/NetCDFTest.nc -o diff.nc
```

### Validation Checkpoints
- Output artifact exists in expected format (`.result`, NetCDF, or VTK family).
- Numeric difference check stays within documented tolerance.
- Connectivity/field names remain compatible with downstream readers.

## Scope
- Handle questions about output formats, analysis, and post-processing.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `elmerice/Tests/Xios/README.txt`
- `elmerice/Tests/UGridDataReader/README.txt`
- `fem/tests/Shell_with_Solid_Eigenanalysis/Readme.txt`
- `fem/tests/Shell_Eigenanalysis_Spherical/Readme.txt`
- `fem/tests/Shell_Eigenanalysis_L-shaped/Readme.txt`
- `fem/tests/Shell_Eigenanalysis_Cylinder/Readme.txt`
- `elmerice/Solvers/Documentation/OutputStrainHeating.md`

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
- `elmerice/Solvers/OutputStrainHeating.F90`
- `elmerice/Solvers/UGridDataReader.F90`
- `elmerice/Solvers/Scalar_OUTPUT_Glacier.F90`
- `elmerice/Solvers/Permafrost/Permafrost_solid.F90`
- `elmerice/Solvers/OutPutSolvers/XIOSOutputSolver.F90`
- `elmerice/Solvers/Covarianceutils/GaussianSimulationSolver.F90`
- `elmerice/Solvers/ThicknessSolver.F90`
- `elmerice/Solvers/SurfaceBoundaryEnthalpy.F90`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" ElmerGUIlogger/src ElmerGUItester/src ElmerWorkflows/FreeCADBatchFEMTools elmergrid/src elmerice/Solvers elmerice/UserFunctions elmerice/Utils fem/src fhutiter/src matc/src mathlibs/src meshgen2d/src ElmerGUI/Application/src ElmerGUI/PythonQt/src`).
