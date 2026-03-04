# elmerfem source map: API and Scripting

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
- `bindings`
- `calving3d`
- `calvingglacieradvance3d`
- `class`
- `classical2dshell`
- `covarianceutilsmodule`
- `damage`
- `elmerice`
- `fem`
- `frictionheat`
- `frictionloads`
- `function`
- `iceproperties`
- `interface`
- `lateralfriction`
- `library`
- `lset`
- `proj`
- `release`
- `releasenotes`
- `scattered2ddatainterpolator`
- `scripting`
- `shapefactor`
- `solvers`
- `sourcecalccalving`
- `south`
- `template`
- `userfunctions`

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
- `elmerice/Solvers/Calving3D_lset.F90` | score: 20 | matched tokens: calving3d, elmerice, lset, solvers
- `elmerice/UserFunctions/USF_SourceCalcCalving.F90` | score: 17 | matched tokens: elmerice, function, sourcecalccalving, userfunctions
- `elmerice/UserFunctions/USF_ShapeFactor.F90` | score: 17 | matched tokens: elmerice, function, shapefactor, userfunctions
- `elmerice/UserFunctions/USF_proj.F90` | score: 17 | matched tokens: elmerice, function, proj, userfunctions
- `elmerice/UserFunctions/USF_LateralFriction.F90` | score: 17 | matched tokens: elmerice, function, lateralfriction, userfunctions
- `elmerice/UserFunctions/USF_IceProperties.F90` | score: 17 | matched tokens: elmerice, function, iceproperties, userfunctions
- `elmerice/UserFunctions/USF_Damage.F90` | score: 17 | matched tokens: damage, elmerice, function, userfunctions
- `elmerice/Solvers/CalvingGlacierAdvance3D.F90` | score: 15 | matched tokens: calvingglacieradvance3d, elmerice, solvers
- `elmerice/Solvers/Calving3D.F90` | score: 15 | matched tokens: calving3d, elmerice, solvers
- `elmerice/Solvers/ScatteredDataInterpolator/Scattered2DDataInterpolator.F90` | score: 15 | matched tokens: elmerice, scattered2ddatainterpolator, solvers
- `elmerice/UserFunctions/USF_GetFrictionHeating.F90` | score: 14 | matched tokens: elmerice, frictionheat, function, userfunctions
- `elmerice/Solvers/ScatteredDataInterpolator/Scattered2D_FInterface.F90` | score: 12 | matched tokens: elmerice, interface, solvers
- `elmerice/UserFunctions/USF_Zs.F90` | score: 12 | matched tokens: elmerice, function, userfunctions
- `elmerice/UserFunctions/USF_WaterTransfer.F90` | score: 12 | matched tokens: elmerice, function, userfunctions
- `elmerice/UserFunctions/USF_Sliding.F90` | score: 12 | matched tokens: elmerice, function, userfunctions
- `elmerice/UserFunctions/USF_Haf.F90` | score: 12 | matched tokens: elmerice, function, userfunctions
- `elmerice/UserFunctions/USF_GlacierMeshMetric.F90` | score: 12 | matched tokens: elmerice, function, userfunctions
- `elmerice/UserFunctions/USF_CoV.F90` | score: 12 | matched tokens: elmerice, function, userfunctions
- `elmerice/UserFunctions/USF_CouplingGlaDS_SSA.F90` | score: 12 | matched tokens: elmerice, function, userfunctions
- `elmerice/UserFunctions/USF_Contact.F90` | score: 12 | matched tokens: elmerice, function, userfunctions
- `elmerice/UserFunctions/CMakeLists.txt` | score: 12 | matched tokens: elmerice, function, userfunctions
- `elmerice/UserFunctions/CaffeFlow.F90` | score: 12 | matched tokens: elmerice, function, userfunctions
- `elmerice/UserFunctions/Buoyancy.F90` | score: 12 | matched tokens: elmerice, function, userfunctions
- `elmerice/Solvers/ProjectCalving.F90` | score: 12 | matched tokens: elmerice, proj, solvers
- `elmerice/Solvers/Covarianceutils/GaussianSimulationSolver.F90` | score: 10 | matched tokens: elmerice, solvers
- `elmerice/Solvers/ThicknessSolver.F90` | score: 10 | matched tokens: elmerice, solvers
- `elmerice/Solvers/SurfaceBoundaryEnthalpy.F90` | score: 10 | matched tokens: elmerice, solvers
- `elmerice/Solvers/SSASolver.F90` | score: 10 | matched tokens: elmerice, solvers
- `elmerice/Solvers/SIASolver.F90` | score: 10 | matched tokens: elmerice, solvers
- `elmerice/Solvers/PlumeSolver.F90` | score: 10 | matched tokens: elmerice, solvers
