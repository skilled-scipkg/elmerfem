---
name: elmerfem-build-and-install
description: This skill should be used when users ask about build and install in elmerfem; it prioritizes documentation references and then source inspection only for unresolved details.
---

# elmerfem: Build and Install

## High-Signal Playbook
### Route Conditions
- Use this skill for configure/build/install/dependency selection requests.
- Route to `elmerfem-parallel-hpc` for scheduler/job-launch tuning after build succeeds.
- Route to `elmerfem-simulation-workflows` once binaries are available and the user needs run/restart flow.
- Route to `elmerfem-troubleshooting` for persistent link/config/runtime failures after following the canonical build path.

### Triage Questions
- Which platform/toolchain is in scope (`Ubuntu`, `macOS`, `Windows MSYS2`, `Nix`)?
- Which optional features are required now: `MPI`, `OpenMP`, `ElmerIce`, `ElmerGUI`, `NetCDF`, `XIOS`, `MUMPS`?
- Is the build prefix user-local or system-wide (`CMAKE_INSTALL_PREFIX`)?
- Are you using clean out-of-source build directories?
- Should we validate with `ctest` labels (`quick`, `elmerice-fast`) before finishing?
- Do you need reproducible/containerized builds (`nix`, `docker/elmer.dockerfile`)?

### Canonical Workflow
1. Choose the platform recipe: `compilation_instructions/Ubuntu.md`, `compilation_instructions/macOS.md`, `compilation_instructions/Windows-msys2.md`, `compilation_instructions/nix.md`.
2. Create a clean build directory and set only required CMake toggles from `CMakeLists.txt` (`WITH_MPI`, `WITH_OpenMP`, `WITH_ElmerIce`, `WITH_ELMERGUI`, `WITH_NETCDF`, `WITH_XIOS`, `WITH_Mumps`).
3. Configure with explicit install prefix and dependency hints when needed (MSYS2 `pkg-config` flow in `compilation_instructions/Windows-msys2.md`).
4. Build/install with CMake build/install commands.
5. Run smoke tests via `ctest -L quick` and `ctest -L elmerice-fast` (`fem/tests/ElmerSolver_cmake_test-how-to.txt`, `elmerice/Tests/ElmerIceSolver_cmake_test_how-to.txt`).
6. Run one small solver case manually before handing off.
7. If behavior is still unclear, jump to `references/source_map.md` and inspect CMake wiring plus launch/runtime routines (`fem/src/ElmerSolver.F90`, `fem/src/MainUtils.F90`) in that order.

### Minimal Working Example
```bash
mkdir -p build && cd build
cmake .. \
  -DCMAKE_INSTALL_PREFIX="$PWD/../install" \
  -DWITH_OpenMP=ON \
  -DWITH_MPI=ON \
  -DWITH_ElmerIce=ON \
  -DWITH_Mumps=ON
cmake --build . -j"$(nproc)"
cmake --install .
ctest -L quick -j2
ctest -L elmerice-fast -j2
```

```bash
cd ../elmerice/Tests/SSA_Weertman
ElmerGrid 1 2 rectangle.grd
ElmerSolver ismip_SSA_2D_Weertman.sif
```

### Pitfalls/Fixes
- `WITH_ElmerIce=ON` with `WITH_MPI=OFF` is invalid: configure fails (`CMakeLists.txt`).
- `WITH_XIOS=ON` requires NetCDF discovery (`WITH_NETCDF=ON` and `NETCDF_FOUND`) (`CMakeLists.txt`).
- NetCDF/HDF5 not found only disables related functionality; confirm expected behavior from configure log (`CMakeLists.txt`).
- MSYS2 build requires upgraded package DB and (for MPI) `MSMPI_BIN` export (`compilation_instructions/Windows-msys2.md`).
- macOS configure can fail with package-manager autodetection unless Homebrew/MacPorts is available (`CMakeLists.txt`, `compilation_instructions/macOS.md`).
- Old docs may not match current distro package names exactly; prefer compiling with the minimal flag set first (`compilation_instructions/Ubuntu.md` note).

### Convergence/Validation Checks
- Configure summary shows expected libraries/components (MPI/BLAS/LAPACK/MUMPS/NetCDF as requested).
- `ElmerSolver`, `ElmerGrid`, and optionally `ElmerSolver_mpi` exist in install/bin.
- `ctest -L quick` passes on the build tree.
- If ElmerIce is enabled, `ctest -L elmerice-fast` passes.
- At least one manual test case runs and writes expected output files (`.result`/`.vtu`).

## Scope
- Handle questions about build, installation, compilation, and environment setup.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `README.adoc`
- `CMakeLists.txt`
- `compilation_instructions/Ubuntu.md`
- `compilation_instructions/macOS.md`
- `elmerice/examples/Test_MshGlacierSynthetic/README.txt`
- `elmerice/examples/Adjoint_CostRegSolver/Readme.md`
- `elmerice/examples/Test_MshGlacier/README.txt`
- `elmerice/Tests/SIA/README.txt`
- `elmerice/Tests/Hydro_SedOnly/Readme.txt`
- `elmerice/Tests/Hydro_Coupled/Readme.txt`
- `ReleaseNotes/release_8.3.txt`
- `compilation_instructions/nix.md`
- `compilation_instructions/Windows-msys2.md`
- `docker/elmer.dockerfile`
- `ci/LUMI/Elmer-linux-gcc11.cmake`
- `fem/tests/ElmerSolver_cmake_test-how-to.txt`
- `elmerice/Tests/ElmerIceSolver_cmake_test_how-to.txt`
- `elmerice/Tests/CMakeLists.txt`

## Workflow
- Start with the primary references above.
- If details are missing, inspect `references/doc_map.md` for the complete topic document list.
- Use tutorials/examples as executable usage patterns when available.
- Use tests as behavior or regression references when available.
- If ambiguity remains after docs, inspect `references/source_map.md` and start with the ranked source entry points.
- Cite exact documentation file paths in responses.

## Tutorials and examples
- `ElmerGUI/samples`
- `elmerice/examples`
- `fem/examples`
- `fhutiter/examples`

## Test references
- `elmergrid/tests`
- `elmerice/Tests`
- `fem/tests`
- `ElmerWorkflows/FreeCADBatchFEMTools/tests`
- `fem/src/binio/test`

## Optional deeper inspection
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

## Source entry points for unresolved issues
- `fem/src/ElmerSolver.F90`
- `fem/src/MainUtils.F90`
- `fem/src/ParallelUtils.F90`
- `elmergrid/src/egparallel.c`
- `elmerice/UserFunctions/CMakeLists.txt`
- `elmerice/Solvers/CMakeLists.txt`
- `elmerice/Solvers/ScatteredDataInterpolator/CMakeLists.txt`
- `elmerice/Solvers/MeshAdaptation_2D/CMakeLists.txt`
- `elmerice/Solvers/GridDataReader/CMakeLists.txt`
- `fhutiter/src/CMakeLists.txt`
- `fem/src/CMakeLists.txt`
- `elmerice/Utils/CMakeLists.txt`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" ElmerGUIlogger/src ElmerGUItester/src ElmerWorkflows/FreeCADBatchFEMTools elmergrid/src elmerice/Solvers elmerice/UserFunctions elmerice/Utils fem/src fhutiter/src matc/src mathlibs/src meshgen2d/src ElmerGUI/Application/src ElmerGUI/PythonQt/src`).
