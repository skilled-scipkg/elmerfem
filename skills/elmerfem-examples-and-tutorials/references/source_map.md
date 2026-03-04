# elmerfem source map: Examples and Tutorials

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
- `b010`
- `c010`
- `cookbook`
- `d010`
- `data`
- `directvalidation`
- `elmerice`
- `elmericesolver`
- `f000`
- `gradientvalidation`
- `hom`
- `howto`
- `inverse`
- `inversemethods`
- `ismip`
- `macayeal`
- `massconservation`
- `methods`
- `mshglacierdem`
- `old`
- `optimisation`
- `partitioned`
- `ronnefilchner`
- `scripts`
- `serial`
- `src`
- `ssa`
- `stokes`
- `walkthrough`

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
- `elmerice/UserFunctions/USF_CouplingGlaDS_SSA.F90` | score: 10 | matched tokens: elmerice, ssa
- `fem/src/modules/Stokes.F90` | score: 10 | matched tokens: src, stokes
- `elmerice/Solvers/Adjoint/Adjoint_GradientValidation.F90` | score: 10 | matched tokens: elmerice, gradientvalidation
- `elmerice/Utils/SSAMaterialModels.F90` | score: 7 | matched tokens: elmerice, ssa
- `fem/src/modules/DataToFieldSolver.F90` | score: 7 | matched tokens: data, src
- `elmerice/Solvers/SSASolver.F90` | score: 7 | matched tokens: elmerice, ssa
- `fem/src/modules/ReynoldsSolver.F90` | score: 7 | matched tokens: old, src
- `elmerice/Solvers/ScatteredDataInterpolator/Scattered2D_FInterface.F90` | score: 7 | matched tokens: data, elmerice
- `elmerice/Solvers/AdjointStokes/AdjointStokes_GradientBetaSolver.F90` | score: 7 | matched tokens: elmerice, stokes
- `elmerice/Solvers/AdjointSSA/AdjointSSA_SSASolver.F90` | score: 7 | matched tokens: elmerice, ssa
- `elmerice/Solvers/AdjointSSA/AdjointSSA_GradientSolver.F90` | score: 7 | matched tokens: elmerice, ssa
- `elmerice/Solvers/AdjointSSA/AdjointSSA_CostTaubSolver.F90` | score: 7 | matched tokens: elmerice, ssa
- `elmerice/Solvers/AdjointSSA/AdjointSSA_CostRegSolver.F90` | score: 7 | matched tokens: elmerice, ssa
- `elmerice/Solvers/AdjointSSA/AdjointSSA_CostFluxDivSolver.F90` | score: 7 | matched tokens: elmerice, ssa
- `elmerice/Solvers/AdjointSSA/AdjointSSA_CostDiscSolver.F90` | score: 7 | matched tokens: elmerice, ssa
- `elmerice/Solvers/AdjointSSA/AdjointSSA_CostContSolver.F90` | score: 7 | matched tokens: elmerice, ssa
- `elmerice/Solvers/AdjointSSA/AdjointSSA_AdjointSolver.F90` | score: 7 | matched tokens: elmerice, ssa
- `fem/src/modules/SaveData/SaveMaterials.F90` | score: 7 | matched tokens: data, src
- `fem/src/modules/SaveData/SaveBoundaryValues.F90` | score: 7 | matched tokens: data, src
- `fem/src/NavierStokesGeneral.F90` | score: 7 | matched tokens: src, stokes
- `fem/src/NavierStokesCylindrical.F90` | score: 7 | matched tokens: src, stokes
- `fem/src/NavierStokes.F90` | score: 7 | matched tokens: src, stokes
- `fem/src/Messages.F90` | score: 7 | matched tokens: src, ssa
- `fem/src/IterativeMethods.F90` | score: 7 | matched tokens: methods, src
- `fem/src/ClusteringMethods.F90` | score: 7 | matched tokens: methods, src
- `elmerice/Solvers/UGridDataReader.F90` | score: 7 | matched tokens: data, elmerice
- `elmerice/Solvers/SSAmask.F90` | score: 7 | matched tokens: elmerice, ssa
- `mathlibs/src/parpack/pssaupd.f` | score: 7 | matched tokens: src, ssa
- `mathlibs/src/parpack/pssaup2.f` | score: 7 | matched tokens: src, ssa
- `mathlibs/src/parpack/pssapps.f` | score: 7 | matched tokens: src, ssa
