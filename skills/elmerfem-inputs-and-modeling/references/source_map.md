# elmerfem source map: Inputs and Modeling

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
- `aiflowsolve`
- `basis`
- `boundary`
- `elmerice`
- `field`
- `force`
- `forcefield`
- `geometry`
- `grid2dinterpolator`
- `hydrologyglads`
- `input`
- `inputs`
- `material`
- `model`
- `modeling`
- `plumesolver`
- `release`
- `releasenotes`
- `solvers`
- `ssamaterialmodels`
- `structure`
- `surfaceboundaryenth`
- `surfaceboundaryenthalpy`
- `utils`

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
- `elmerice/Utils/SSAMaterialModels.F90` | score: 21 | matched tokens: elmerice, material, model, ssamaterialmodels, utils
- `elmerice/Solvers/SurfaceBoundaryEnthalpy.F90` | score: 21 | matched tokens: boundary, elmerice, solvers, surfaceboundaryenth, surfaceboundaryenthalpy
- `elmerice/Utils/PorousMaterialModels.F90` | score: 16 | matched tokens: elmerice, material, model, utils
- `elmerice/Solvers/CalvingGeometry.F90` | score: 16 | matched tokens: elmerice, geometry, solvers
- `elmerice/Solvers/PlumeSolver.F90` | score: 15 | matched tokens: elmerice, plumesolver, solvers
- `elmerice/Solvers/Grid2DInterpolator.F90` | score: 15 | matched tokens: elmerice, grid2dinterpolator, solvers
- `elmerice/Solvers/AIFlowSolve_nlS2.F90` | score: 15 | matched tokens: aiflowsolve, elmerice, solvers
- `elmerice/Solvers/AIFlowSolve_nlD2.F90` | score: 15 | matched tokens: aiflowsolve, elmerice, solvers
- `elmerice/Solvers/Permafrost/Permafrost_Utils.F90` | score: 15 | matched tokens: elmerice, solvers, utils
- `elmerice/Solvers/Permafrost/PermafrostMaterials.F90` | score: 14 | matched tokens: elmerice, material, solvers
- `elmerice/Solvers/Covarianceutils/GaussianSimulationSolver.F90` | score: 12 | matched tokens: elmerice, solvers, utils
- `elmerice/Solvers/Covarianceutils/CovarianceVectorMultiplySolver.F90` | score: 12 | matched tokens: elmerice, solvers, utils
- `elmerice/Solvers/Covarianceutils/BackgroundErrorCostSolver.F90` | score: 12 | matched tokens: elmerice, solvers, utils
- `elmerice/Solvers/ForceToStress.F90` | score: 12 | matched tokens: elmerice, force, solvers
- `elmerice/Solvers/ElmerIceUtils.F90` | score: 12 | matched tokens: elmerice, solvers, utils
- `elmerice/Solvers/Covarianceutils/CovarianceUtils.F90` | score: 12 | matched tokens: elmerice, solvers, utils
- `elmerice/Solvers/ThicknessSolver.F90` | score: 10 | matched tokens: elmerice, solvers
- `elmerice/Solvers/SSASolver.F90` | score: 10 | matched tokens: elmerice, solvers
- `elmerice/Solvers/SIASolver.F90` | score: 10 | matched tokens: elmerice, solvers
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
- `elmerice/Solvers/CaffeSolver.F90` | score: 10 | matched tokens: elmerice, solvers
