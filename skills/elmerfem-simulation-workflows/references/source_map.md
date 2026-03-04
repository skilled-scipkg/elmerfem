# elmerfem source map: Simulation Workflows

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
- `2d`
- `3dint`
- `3dmesh`
- `buoyancy`
- `computedevstress`
- `coulomb`
- `damage`
- `dgsolver`
- `dynamics`
- `eigenvalues`
- `elmerice`
- `enthalpy`
- `exportvertically`
- `forcetostress`
- `friction`
- `frictionheat`
- `glads`
- `griddatareader`
- `integrator`
- `inverse`
- `methods`
- `pipeline`
- `ronnefilchner2`
- `run`
- `savegriddatanetcdf`
- `simulation`
- `ssa`
- `step`
- `stokesweertman`
- `strainrate`

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
- `elmerice/Solvers/Weertman2Coulomb.F90` | score: 13 | matched tokens: coulomb, elmerice, weertman, weertman2
- `elmerice/Solvers/MeshAdaptation_2D/MMG2DSolver.F90` | score: 12 | matched tokens: 2d, elmerice
- `elmerice/UserFunctions/USF_CouplingGlaDS_SSA.F90` | score: 12 | matched tokens: elmerice, glads, ssa
- `elmerice/Solvers/ForceToStress.F90` | score: 12 | matched tokens: elmerice, forcetostress
- `elmerice/Solvers/ExportVertically.F90` | score: 12 | matched tokens: elmerice, exportvertically
- `elmerice/Solvers/ComputeDevStress.F90` | score: 12 | matched tokens: computedevstress, elmerice
- `elmerice/Solvers/MeshAdaptation_2D/MMG2D_MetricIntersect.F90` | score: 12 | matched tokens: 2d, elmerice
- `elmerice/Solvers/MeshAdaptation_2D/MMG2D_MetricAniso.F90` | score: 12 | matched tokens: 2d, elmerice
- `elmerice/Solvers/MeshAdaptation_2D/GetConnectedAreas.F90` | score: 12 | matched tokens: 2d, elmerice
- `elmerice/Solvers/MeshAdaptation_2D/GetActiveMesh.F90` | score: 12 | matched tokens: 2d, elmerice
- `elmerice/Solvers/MeshAdaptation_2D/Compute2DNodalGradient.F90` | score: 12 | matched tokens: 2d, elmerice
- `elmerice/Solvers/MeshAdaptation_2D/CMakeLists.txt` | score: 12 | matched tokens: 2d, elmerice
- `elmerice/Solvers/GridDataReader/GridDataReader.F90` | score: 12 | matched tokens: elmerice, griddatareader
- `elmerice/Solvers/GridDataReader/CMakeLists.txt` | score: 12 | matched tokens: elmerice, griddatareader
- `elmerice/Solvers/Covarianceutils/GaussianSimulationSolver.F90` | score: 11 | matched tokens: elmerice, simulation
- `elmerice/UserFunctions/USF_Damage.F90` | score: 10 | matched tokens: damage, elmerice
- `elmerice/UserFunctions/Buoyancy.F90` | score: 10 | matched tokens: buoyancy, elmerice
- `elmerice/Solvers/SurfaceBoundaryEnthalpy.F90` | score: 9 | matched tokens: elmerice, enthalpy
- `elmerice/Solvers/SSASolver.F90` | score: 9 | matched tokens: elmerice, ssa
- `elmerice/Solvers/GlaDSCoupledSolver.F90` | score: 9 | matched tokens: elmerice, glads
- `elmerice/Solvers/GlaDSchannelSolver.F90` | score: 9 | matched tokens: elmerice, glads
- `elmerice/Solvers/EnthalpySolver.F90` | score: 9 | matched tokens: elmerice, enthalpy
- `elmerice/Solvers/ScatteredDataInterpolator/Scattered2D_FInterface.F90` | score: 9 | matched tokens: 2d, elmerice
- `elmerice/Solvers/AdjointSSA/AdjointSSA_SSASolver.F90` | score: 9 | matched tokens: elmerice, ssa
- `elmerice/Solvers/AdjointSSA/AdjointSSA_GradientSolver.F90` | score: 9 | matched tokens: elmerice, ssa
- `elmerice/Solvers/AdjointSSA/AdjointSSA_CostTaubSolver.F90` | score: 9 | matched tokens: elmerice, ssa
- `elmerice/Solvers/AdjointSSA/AdjointSSA_CostRegSolver.F90` | score: 9 | matched tokens: elmerice, ssa
- `elmerice/Solvers/AdjointSSA/AdjointSSA_CostFluxDivSolver.F90` | score: 9 | matched tokens: elmerice, ssa
- `elmerice/Solvers/AdjointSSA/AdjointSSA_CostDiscSolver.F90` | score: 9 | matched tokens: elmerice, ssa
- `elmerice/Solvers/AdjointSSA/AdjointSSA_CostContSolver.F90` | score: 9 | matched tokens: elmerice, ssa
