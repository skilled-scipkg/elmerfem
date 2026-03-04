# elmerfem source map: Troubleshooting

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
- `debug`
- `elmerice`
- `error`
- `failure`
- `faq`
- `iscal`
- `issue`
- `known`
- `problem`
- `solvers`
- `troubleshoot`
- `troubleshooting`

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
- `elmerice/Solvers/Covarianceutils/BackgroundErrorCostSolver.F90` | score: 12 | matched tokens: elmerice, error, solvers
- `elmerice/Solvers/Covarianceutils/GaussianSimulationSolver.F90` | score: 10 | matched tokens: elmerice, solvers
- `elmerice/Solvers/ThicknessSolver.F90` | score: 10 | matched tokens: elmerice, solvers
- `elmerice/Solvers/SurfaceBoundaryEnthalpy.F90` | score: 10 | matched tokens: elmerice, solvers
- `elmerice/Solvers/SSASolver.F90` | score: 10 | matched tokens: elmerice, solvers
- `elmerice/Solvers/SIASolver.F90` | score: 10 | matched tokens: elmerice, solvers
- `elmerice/Solvers/PlumeSolver.F90` | score: 10 | matched tokens: elmerice, solvers
- `elmerice/Solvers/MMG3DSolver.F90` | score: 10 | matched tokens: elmerice, solvers
- `elmerice/Solvers/IDSSolver.F90` | score: 10 | matched tokens: elmerice, solvers
- `elmerice/Solvers/IcyMaskSolver.F90` | score: 10 | matched tokens: elmerice, solvers
- `elmerice/Solvers/GroundedSolver.F90` | score: 10 | matched tokens: elmerice, solvers
- `elmerice/Solvers/GlaDSCoupledSolver.F90` | score: 10 | matched tokens: elmerice, solvers
- `elmerice/Solvers/GlaDSchannelSolver.F90` | score: 10 | matched tokens: elmerice, solvers
- `elmerice/Solvers/EPLSolver.F90` | score: 10 | matched tokens: elmerice, solvers
- `elmerice/Solvers/EnthalpySolver.F90` | score: 10 | matched tokens: elmerice, solvers
- `elmerice/Solvers/CostSolver_Robin.F90` | score: 10 | matched tokens: elmerice, solvers
- `elmerice/Solvers/CostSolver_Adjoint.F90` | score: 10 | matched tokens: elmerice, solvers
- `elmerice/Solvers/CalvingGeometry.F90` | score: 10 | matched tokens: elmerice, solvers
- `elmerice/Solvers/CaffeSolver.F90` | score: 10 | matched tokens: elmerice, solvers
- `elmerice/Solvers/AdjointSolver.F90` | score: 10 | matched tokens: elmerice, solvers
- `elmerice/Solvers/ScatteredDataInterpolator/Scattered2D_FInterface.F90` | score: 10 | matched tokens: elmerice, solvers
- `elmerice/Solvers/Permafrost/PermafrostMaterials.F90` | score: 10 | matched tokens: elmerice, solvers
- `elmerice/Solvers/OutPutSolvers/XIOSOutputSolver.F90` | score: 10 | matched tokens: elmerice, solvers
- `elmerice/Solvers/MeshAdaptation_2D/MMG2DSolver.F90` | score: 10 | matched tokens: elmerice, solvers
- `elmerice/Solvers/Covarianceutils/CovarianceVectorMultiplySolver.F90` | score: 10 | matched tokens: elmerice, solvers
- `elmerice/Solvers/AdjointThickness/AdjointThickness_ThicknessSolver.F90` | score: 10 | matched tokens: elmerice, solvers
- `elmerice/Solvers/AdjointThickness/AdjointThickness_GradientSolver.F90` | score: 10 | matched tokens: elmerice, solvers
- `elmerice/Solvers/AdjointStokes/AdjointStokes_GradientBetaSolver.F90` | score: 10 | matched tokens: elmerice, solvers
- `elmerice/Solvers/AdjointSSA/AdjointSSA_SSASolver.F90` | score: 10 | matched tokens: elmerice, solvers
- `elmerice/Solvers/AdjointSSA/AdjointSSA_GradientSolver.F90` | score: 10 | matched tokens: elmerice, solvers
