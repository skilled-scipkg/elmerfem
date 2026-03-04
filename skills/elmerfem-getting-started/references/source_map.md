# elmerfem source map: Getting Started

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
- `adjoint`
- `adjointssa`
- `adjointstokes`
- `adjointthickness`
- `basics`
- `costcontsolver`
- `costdiscsolver`
- `costfluxdivsolver`
- `costregsolver`
- `costtaubsolver`
- `covariance`
- `elmerice`
- `getting`
- `glacier`
- `gradientbetasolver`
- `gradientsolver`
- `gradientvalidation`
- `icymasksolver`
- `intro`
- `introduction`
- `linearsolver`
- `m1qn3`
- `optimize`
- `output`
- `overview`
- `quickstart`
- `release`
- `releasenotes`
- `scalar`
- `solvers`

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
- `elmerice/Solvers/Scalar_OUTPUT_Glacier.F90` | score: 25 | matched tokens: elmerice, glacier, output, scalar, solvers
- `elmerice/Solvers/AdjointThickness/AdjointThickness_ThicknessSolver.F90` | score: 22 | matched tokens: adjoint, adjointthickness, elmerice, solvers, thicknesssolver
- `elmerice/Solvers/AdjointThickness/AdjointThickness_GradientSolver.F90` | score: 22 | matched tokens: adjoint, adjointthickness, elmerice, gradientsolver, solvers
- `elmerice/Solvers/AdjointStokes/AdjointStokes_GradientBetaSolver.F90` | score: 22 | matched tokens: adjoint, adjointstokes, elmerice, gradientbetasolver, solvers
- `elmerice/Solvers/AdjointSSA/AdjointSSA_SSASolver.F90` | score: 22 | matched tokens: adjoint, adjointssa, elmerice, solvers, ssasolver
- `elmerice/Solvers/AdjointSSA/AdjointSSA_GradientSolver.F90` | score: 22 | matched tokens: adjoint, adjointssa, elmerice, gradientsolver, solvers
- `elmerice/Solvers/AdjointSSA/AdjointSSA_CostTaubSolver.F90` | score: 22 | matched tokens: adjoint, adjointssa, costtaubsolver, elmerice, solvers
- `elmerice/Solvers/AdjointSSA/AdjointSSA_CostRegSolver.F90` | score: 22 | matched tokens: adjoint, adjointssa, costregsolver, elmerice, solvers
- `elmerice/Solvers/AdjointSSA/AdjointSSA_CostFluxDivSolver.F90` | score: 22 | matched tokens: adjoint, adjointssa, costfluxdivsolver, elmerice, solvers
- `elmerice/Solvers/AdjointSSA/AdjointSSA_CostDiscSolver.F90` | score: 22 | matched tokens: adjoint, adjointssa, costdiscsolver, elmerice, solvers
- `elmerice/Solvers/AdjointSSA/AdjointSSA_CostContSolver.F90` | score: 22 | matched tokens: adjoint, adjointssa, costcontsolver, elmerice, solvers
- `elmerice/Solvers/Adjoint/Adjoint_LinearSolver.F90` | score: 20 | matched tokens: adjoint, elmerice, linearsolver, solvers
- `elmerice/Solvers/Adjoint/Adjoint_CostRegSolver.F90` | score: 20 | matched tokens: adjoint, costregsolver, elmerice, solvers
- `elmerice/Solvers/Adjoint/Adjoint_CostDiscSolver.F90` | score: 20 | matched tokens: adjoint, costdiscsolver, elmerice, solvers
- `elmerice/Solvers/Adjoint/Adjoint_CostContSolver.F90` | score: 20 | matched tokens: adjoint, costcontsolver, elmerice, solvers
- `elmerice/Solvers/Adjoint/Adjoint_GradientValidation.F90` | score: 20 | matched tokens: adjoint, elmerice, gradientvalidation, solvers
- `elmerice/Solvers/AdjointSSA/AdjointSSA_AdjointSolver.F90` | score: 17 | matched tokens: adjoint, adjointssa, elmerice, solvers
- `elmerice/Solvers/Optimize_m1qn3Parallel.F90` | score: 17 | matched tokens: elmerice, m1qn3, optimize, solvers
- `elmerice/Solvers/AdjointStokes/AdjointStokes_GradientMu.F90` | score: 17 | matched tokens: adjoint, adjointstokes, elmerice, solvers
- `elmerice/Solvers/ThicknessSolver.F90` | score: 15 | matched tokens: elmerice, solvers, thicknesssolver
- `elmerice/Solvers/SSASolver.F90` | score: 15 | matched tokens: elmerice, solvers, ssasolver
- `elmerice/Solvers/IcyMaskSolver.F90` | score: 15 | matched tokens: elmerice, icymasksolver, solvers
- `elmerice/Solvers/CostSolver_Adjoint.F90` | score: 15 | matched tokens: adjoint, elmerice, solvers
- `elmerice/Solvers/m1qn3.F` | score: 15 | matched tokens: elmerice, m1qn3, solvers
- `elmerice/Solvers/DJDmu_Adjoint.F90` | score: 15 | matched tokens: adjoint, elmerice, solvers
- `elmerice/Solvers/DJDBeta_Adjoint.F90` | score: 15 | matched tokens: adjoint, elmerice, solvers
- `elmerice/Solvers/Covarianceutils/GaussianSimulationSolver.F90` | score: 12 | matched tokens: covariance, elmerice, solvers
- `elmerice/Solvers/AdjointSolver.F90` | score: 12 | matched tokens: adjoint, elmerice, solvers
- `elmerice/Solvers/OutPutSolvers/XIOSOutputSolver.F90` | score: 12 | matched tokens: elmerice, output, solvers
- `elmerice/Solvers/Covarianceutils/CovarianceVectorMultiplySolver.F90` | score: 12 | matched tokens: covariance, elmerice, solvers
