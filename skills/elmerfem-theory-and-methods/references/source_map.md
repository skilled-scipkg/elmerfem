# elmerfem source map: Theory and Methods

Generated from source roots:
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

Use this map only after exhausting the topic docs in `doc_map.md`.

## Topic query tokens
- `algorithm`
- `benchmarkcase1`
- `benchmarkcase2`
- `calving3d`
- `derivation`
- `elementaldirector`
- `elmerice`
- `equation`
- `fem`
- `formalism`
- `lset`
- `method`
- `methods`
- `parmmg`
- `quad`
- `release`
- `releasenotes`
- `shell`
- `theory`
- `tria`

## Fast source navigation
- `rg -n "<symbol_or_keyword>" ElmerGUIlogger/src ElmerGUItester/src ElmerWorkflows/FreeCADBatchFEMTools elmergrid/src elmerice/Solvers elmerice/UserFunctions elmerice/Utils fem/src fhutiter/src matc/src mathlibs/src meshgen2d/src ElmerGUI/Application/src ElmerGUI/PythonQt/src`
- `rg -n "class|def|struct|namespace" ElmerGUIlogger/src ElmerGUItester/src ElmerWorkflows/FreeCADBatchFEMTools elmergrid/src elmerice/Solvers elmerice/UserFunctions elmerice/Utils fem/src fhutiter/src matc/src mathlibs/src meshgen2d/src ElmerGUI/Application/src ElmerGUI/PythonQt/src`
- If a doc mentions a function/class, search that exact symbol first, then inspect nearby implementation files.

## Function-level behavior checks
- Extract routines from one candidate file before editing:
  - For Fortran: `rg -n "^[[:space:]]*(subroutine|function)[[:space:]]+" <path/to/file.F90>`
  - For C/C++: `rg -n "^[[:space:]]*[A-Za-z_][A-Za-z0-9_:* ]+[[:space:]]+[A-Za-z_][A-Za-z0-9_]*\(" <path/to/file.{c,cpp,h}>`
- Trace call sites from that routine into solver wiring:
  - `rg -n "<RoutineName>" elmerice/Solvers elmerice/UserFunctions fem/src elmergrid/src ElmerGUI/Application/src`
- Confirm behavior using the closest runnable case listed in `doc_map.md` before proposing code edits.

## Suggested source entry points
- `elmerice/Solvers/Calving3D_lset.F90` | score: 15 | matched tokens: calving3d, elmerice, lset
- `elmerice/Solvers/Calving3D.F90` | score: 10 | matched tokens: calving3d, elmerice
- `fem/src/view3d/16node_quad.c` | score: 10 | matched tokens: fem, quad
- `fem/src/IterativeMethods.F90` | score: 9 | matched tokens: fem, method, methods
- `fem/src/ClusteringMethods.F90` | score: 9 | matched tokens: fem, method, methods
- `fem/src/modules/ShellSolver.F90` | score: 7 | matched tokens: fem, shell
- `fem/src/modules/LevelSet/LevelSetSolver.F90` | score: 7 | matched tokens: fem, lset
- `fem/src/modules/contrib/ShellMultiSolver/ShellMultiSolver.F90` | score: 7 | matched tokens: fem, shell
- `elmerice/Solvers/CalvingRemeshparMMG.F90` | score: 7 | matched tokens: elmerice, parmmg
- `fem/src/view3d/TriangleUtil.c` | score: 7 | matched tokens: fem, tria
- `fem/src/view3d/BiQuadraticUtil.c` | score: 7 | matched tokens: fem, quad
- `fem/src/modules/TransportEquation.F90` | score: 7 | matched tokens: equation, fem
- `fem/src/modules/FacetShellSolve.F90` | score: 7 | matched tokens: fem, shell
- `fem/src/modules/EnergyRelease.F90` | score: 7 | matched tokens: fem, release
- `fem/src/modules/LevelSet/LevelSetTimestep.F90` | score: 7 | matched tokens: fem, lset
- `fem/src/modules/LevelSet/LevelSetIntegrate.F90` | score: 7 | matched tokens: fem, lset
- `fem/src/modules/LevelSet/LevelSetDistance.F90` | score: 7 | matched tokens: fem, lset
- `fem/src/modules/LevelSet/LevelSetCurvature.F90` | score: 7 | matched tokens: fem, lset
- `fem/src/MaterialModels.F90` | score: 5 | matched tokens: fem
- `elmerice/Utils/SSAMaterialModels.F90` | score: 5 | matched tokens: elmerice
- `elmerice/Utils/PorousMaterialModels.F90` | score: 5 | matched tokens: elmerice
- `fem/src/modules/ScannedFieldSolver.F90` | score: 5 | matched tokens: fem
- `fem/src/modules/DataToFieldSolver.F90` | score: 5 | matched tokens: fem
- `elmerice/Solvers/Covarianceutils/GaussianSimulationSolver.F90` | score: 5 | matched tokens: elmerice
- `fem/src/SParIterSolver.F90` | score: 5 | matched tokens: fem
- `fem/src/SolverUtils.F90` | score: 5 | matched tokens: fem
- `fem/src/SolverActivate_x.F90` | score: 5 | matched tokens: fem
- `fem/src/Solver.F90` | score: 5 | matched tokens: fem
- `fem/src/ModelDescription.F90` | score: 5 | matched tokens: fem
- `fem/src/MainUtils.F90` | score: 5 | matched tokens: fem
