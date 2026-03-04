# elmerfem source map: Elmerice

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
- `calving3d`
- `contact`
- `coulomb`
- `dating`
- `deformheat`
- `density`
- `elmerice`
- `friction`
- `glads`
- `glen`
- `grid2dinterpolator`
- `grounded`
- `icesheet`
- `integratedvelocity`
- `integratevertically`
- `mismip`
- `ssa`
- `teterousse`
- `teterousse3a`
- `weertman`
- `xios2`

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
- `elmerice/UserFunctions/USF_CouplingGlaDS_SSA.F90` | score: 12 | matched tokens: elmerice, glads, ssa
- `elmerice/Solvers/Grid2DInterpolator.F90` | score: 12 | matched tokens: 2d, elmerice, grid2dinterpolator
- `elmerice/Solvers/MeshAdaptation_2D/MMG2DSolver.F90` | score: 10 | matched tokens: 2d, elmerice
- `elmerice/UserFunctions/USF_Contact.F90` | score: 10 | matched tokens: contact, elmerice
- `elmerice/Solvers/IntegrateVertically.F90` | score: 10 | matched tokens: elmerice, integratevertically
- `elmerice/Solvers/IntegratedVelocity.F90` | score: 10 | matched tokens: elmerice, integratedvelocity
- `elmerice/Solvers/Calving3D_lset.F90` | score: 10 | matched tokens: calving3d, elmerice
- `elmerice/Solvers/Calving3D.F90` | score: 10 | matched tokens: calving3d, elmerice
- `elmerice/Solvers/MeshAdaptation_2D/MMG2D_MetricIntersect.F90` | score: 10 | matched tokens: 2d, elmerice
- `elmerice/Solvers/MeshAdaptation_2D/MMG2D_MetricAniso.F90` | score: 10 | matched tokens: 2d, elmerice
- `elmerice/Solvers/MeshAdaptation_2D/GetConnectedAreas.F90` | score: 10 | matched tokens: 2d, elmerice
- `elmerice/Solvers/MeshAdaptation_2D/GetActiveMesh.F90` | score: 10 | matched tokens: 2d, elmerice
- `elmerice/Solvers/MeshAdaptation_2D/Compute2DNodalGradient.F90` | score: 10 | matched tokens: 2d, elmerice
- `elmerice/Solvers/MeshAdaptation_2D/CMakeLists.txt` | score: 10 | matched tokens: 2d, elmerice
- `elmerice/Solvers/Weertman2Coulomb.F90` | score: 9 | matched tokens: coulomb, elmerice, weertman
- `elmerice/Utils/SSAMaterialModels.F90` | score: 7 | matched tokens: elmerice, ssa
- `elmerice/Solvers/SSASolver.F90` | score: 7 | matched tokens: elmerice, ssa
- `elmerice/Solvers/GroundedSolver.F90` | score: 7 | matched tokens: elmerice, grounded
- `elmerice/Solvers/GlaDSCoupledSolver.F90` | score: 7 | matched tokens: elmerice, glads
- `elmerice/Solvers/GlaDSchannelSolver.F90` | score: 7 | matched tokens: elmerice, glads
- `elmerice/Solvers/ScatteredDataInterpolator/Scattered2D_FInterface.F90` | score: 7 | matched tokens: 2d, elmerice
- `elmerice/Solvers/AdjointSSA/AdjointSSA_SSASolver.F90` | score: 7 | matched tokens: elmerice, ssa
- `elmerice/Solvers/AdjointSSA/AdjointSSA_GradientSolver.F90` | score: 7 | matched tokens: elmerice, ssa
- `elmerice/Solvers/AdjointSSA/AdjointSSA_CostTaubSolver.F90` | score: 7 | matched tokens: elmerice, ssa
- `elmerice/Solvers/AdjointSSA/AdjointSSA_CostRegSolver.F90` | score: 7 | matched tokens: elmerice, ssa
- `elmerice/Solvers/AdjointSSA/AdjointSSA_CostFluxDivSolver.F90` | score: 7 | matched tokens: elmerice, ssa
- `elmerice/Solvers/AdjointSSA/AdjointSSA_CostDiscSolver.F90` | score: 7 | matched tokens: elmerice, ssa
- `elmerice/Solvers/AdjointSSA/AdjointSSA_CostContSolver.F90` | score: 7 | matched tokens: elmerice, ssa
- `elmerice/Solvers/AdjointSSA/AdjointSSA_AdjointSolver.F90` | score: 7 | matched tokens: elmerice, ssa
- `elmerice/UserFunctions/USF_LateralFriction.F90` | score: 7 | matched tokens: elmerice, friction
