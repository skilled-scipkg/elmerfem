# elmerfem source map: Fem

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
- `axials`
- `beam`
- `benchmarkcase1`
- `benchmarkcase2`
- `blending`
- `disc`
- `elasticity`
- `faraday`
- `fem`
- `gauge`
- `high`
- `isotropic`
- `linear`
- `mgdyn`
- `nodal`
- `normalsolver`
- `openhemisphere`
- `order`
- `pinchedcylinder`
- `platecase`
- `quad`
- `sections`
- `shell`
- `solid`
- `solvers`
- `springs`
- `stvenant`
- `third`
- `transient`

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
- `elmerice/Solvers/MeshAdaptation_2D/Compute2DNodalGradient.F90` | score: 12 | matched tokens: 2d, nodal, solvers
- `fem/src/modules/NormalSolver.F90` | score: 10 | matched tokens: fem, normalsolver
- `elmerice/Solvers/MeshAdaptation_2D/MMG2DSolver.F90` | score: 10 | matched tokens: 2d, solvers
- `fem/src/view3d/2d_4node.c` | score: 10 | matched tokens: 2d, fem
- `fem/src/view3d/16node_quad.c` | score: 10 | matched tokens: fem, quad
- `elmerice/Solvers/Permafrost/Permafrost_solid.F90` | score: 10 | matched tokens: solid, solvers
- `elmerice/Solvers/MeshAdaptation_2D/MMG2D_MetricIntersect.F90` | score: 10 | matched tokens: 2d, solvers
- `elmerice/Solvers/MeshAdaptation_2D/MMG2D_MetricAniso.F90` | score: 10 | matched tokens: 2d, solvers
- `elmerice/Solvers/MeshAdaptation_2D/GetConnectedAreas.F90` | score: 10 | matched tokens: 2d, solvers
- `elmerice/Solvers/MeshAdaptation_2D/GetActiveMesh.F90` | score: 10 | matched tokens: 2d, solvers
- `elmerice/Solvers/MeshAdaptation_2D/CMakeLists.txt` | score: 10 | matched tokens: 2d, solvers
- `fem/src/modules/ShellSolver.F90` | score: 7 | matched tokens: fem, shell
- `fem/src/modules/BeamSolver3D.F90` | score: 7 | matched tokens: beam, fem
- `elmerice/Solvers/ScatteredDataInterpolator/Scattered2D_FInterface.F90` | score: 7 | matched tokens: 2d, solvers
- `elmerice/Solvers/AdjointSSA/AdjointSSA_CostDiscSolver.F90` | score: 7 | matched tokens: disc, solvers
- `elmerice/Solvers/Adjoint/Adjoint_LinearSolver.F90` | score: 7 | matched tokens: linear, solvers
- `elmerice/Solvers/Adjoint/Adjoint_CostDiscSolver.F90` | score: 7 | matched tokens: disc, solvers
- `fem/src/modules/contrib/ShellMultiSolver/ShellMultiSolver.F90` | score: 7 | matched tokens: fem, shell
- `fem/src/SolidMechanicsUtils.F90` | score: 7 | matched tokens: fem, solid
- `fem/src/LinearForms.F90` | score: 7 | matched tokens: fem, linear
- `fem/src/LinearAlgebra.F90` | score: 7 | matched tokens: fem, linear
- `fem/src/DiffuseConvectiveGeneralAnisotropic.F90` | score: 7 | matched tokens: fem, isotropic
- `fem/src/DiffuseConvectiveAnisotropic.F90` | score: 7 | matched tokens: fem, isotropic
- `elmerice/Solvers/TwoMeshes.F90` | score: 7 | matched tokens: solvers, two
- `elmerice/Solvers/Grid2DInterpolator.F90` | score: 7 | matched tokens: 2d, solvers
- `fem/src/view3d/LinearSolveJacob.c` | score: 7 | matched tokens: fem, linear
- `fem/src/view3d/LinearSolveGaussSeidel.c` | score: 7 | matched tokens: fem, linear
- `fem/src/view3d/LinearSolveConjGrad.c` | score: 7 | matched tokens: fem, linear
- `fem/src/view3d/LinearSolve.c` | score: 7 | matched tokens: fem, linear
- `fem/src/view3d/BiQuadraticUtil.c` | score: 7 | matched tokens: fem, quad
