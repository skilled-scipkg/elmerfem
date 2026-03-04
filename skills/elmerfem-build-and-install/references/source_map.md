# elmerfem source map: Build and Install

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
- `adjrobin`
- `build`
- `calving3d`
- `cmake`
- `cmakelists`
- `compilation`
- `compile`
- `costregsolver`
- `coupled`
- `dependencies`
- `elmerice`
- `elmericesolver`
- `elmersolver`
- `fem`
- `fhutiter`
- `forcetostress`
- `hydro`
- `install`
- `installation`
- `instructions`
- `invmeth`
- `limittemperature`
- `make`
- `mprgp1`
- `mshglacier`
- `mshglaciersynthetic`
- `msys2`
- `nix`
- `parallel`

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
- `fem/src/ElmerSolver.F90` | score: 33 | matched tokens: compile, elmersolver, fem, install, parallel
- `fem/src/MainUtils.F90` | score: 31 | matched tokens: compilation, dependencies, install, instructions
- `fem/src/ParallelUtils.F90` | score: 28 | matched tokens: build, compile, parallel
- `elmergrid/src/egparallel.c` | score: 26 | matched tokens: build, compile, elmergrid, parallel
- `elmerice/UserFunctions/CMakeLists.txt` | score: 29 | matched tokens: cmake, cmakelists, elmerice, make, userfunctions
- `elmerice/Solvers/CMakeLists.txt` | score: 29 | matched tokens: cmake, cmakelists, elmerice, make, solvers
- `elmerice/Solvers/ScatteredDataInterpolator/CMakeLists.txt` | score: 29 | matched tokens: cmake, cmakelists, elmerice, make, solvers
- `elmerice/Solvers/MeshAdaptation_2D/CMakeLists.txt` | score: 29 | matched tokens: cmake, cmakelists, elmerice, make, solvers
- `elmerice/Solvers/GridDataReader/CMakeLists.txt` | score: 29 | matched tokens: cmake, cmakelists, elmerice, make, solvers
- `fhutiter/src/CMakeLists.txt` | score: 24 | matched tokens: cmake, cmakelists, fhutiter, make
- `fem/src/CMakeLists.txt` | score: 24 | matched tokens: cmake, cmakelists, fem, make
- `elmerice/Utils/CMakeLists.txt` | score: 24 | matched tokens: cmake, cmakelists, elmerice, make
- `fem/src/viewaxis/CMakeLists.txt` | score: 24 | matched tokens: cmake, cmakelists, fem, make
- `fem/src/view3d/CMakeLists.txt` | score: 24 | matched tokens: cmake, cmakelists, fem, make
- `fem/src/modules/CMakeLists.txt` | score: 24 | matched tokens: cmake, cmakelists, fem, make
- `fem/src/binio/CMakeLists.txt` | score: 24 | matched tokens: cmake, cmakelists, fem, make
- `fem/src/modules/contrib/CMakeLists.txt` | score: 24 | matched tokens: cmake, cmakelists, fem, make
- `elmerice/Solvers/Adjoint/Adjoint_CostRegSolver.F90` | score: 20 | matched tokens: adjoint, costregsolver, elmerice, solvers
- `meshgen2d/src/CMakeLists.txt` | score: 19 | matched tokens: cmake, cmakelists, make
- `mathlibs/src/CMakeLists.txt` | score: 19 | matched tokens: cmake, cmakelists, make
- `matc/src/CMakeLists.txt` | score: 19 | matched tokens: cmake, cmakelists, make
- `elmergrid/src/CMakeLists.txt` | score: 19 | matched tokens: cmake, cmakelists, make
- `mathlibs/src/parpack/CMakeLists.txt` | score: 19 | matched tokens: cmake, cmakelists, make
- `mathlibs/src/arpack/CMakeLists.txt` | score: 19 | matched tokens: cmake, cmakelists, make
- `elmergrid/src/metis-5.1.0/CMakeLists.txt` | score: 19 | matched tokens: cmake, cmakelists, make
- `elmergrid/src/metis-5.1.0/programs/CMakeLists.txt` | score: 19 | matched tokens: cmake, cmakelists, make
- `elmergrid/src/metis-5.1.0/libmetis/CMakeLists.txt` | score: 19 | matched tokens: cmake, cmakelists, make
- `elmergrid/src/metis-5.1.0/include/CMakeLists.txt` | score: 19 | matched tokens: cmake, cmakelists, make
- `elmergrid/src/metis-5.1.0/GKlib/CMakeLists.txt` | score: 19 | matched tokens: cmake, cmakelists, make
- `elmerice/Solvers/AdjointSSA/AdjointSSA_CostRegSolver.F90` | score: 17 | matched tokens: adjoint, costregsolver, elmerice, solvers
- `fem/src/elmerld.in.cmake` | score: 16 | matched tokens: cmake, fem, make
- `fem/src/elmerld.bat.in.cmake` | score: 16 | matched tokens: cmake, fem, make
- `fem/src/elmerf90.in.cmake` | score: 16 | matched tokens: cmake, fem, make
- `fem/src/elmerf90.bat.in.cmake` | score: 16 | matched tokens: cmake, fem, make
