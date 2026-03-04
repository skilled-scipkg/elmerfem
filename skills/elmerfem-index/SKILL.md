---
name: elmerfem-index
description: This skill should be used when users ask how to use elmerfem and the correct generated documentation skill must be selected before going deeper into source code.
---

# elmerfem Skills Index

## Route the request
- Classify the request into one of the generated topic skills listed below.
- Prefer abstract, workflow-level guidance for large scientific packages; do not attempt full function-by-function coverage unless explicitly requested.

## Generated topic skills
- `elmerfem-build-and-install`: Build and Install (build, installation, compilation, and environment setup)
- `elmerfem-examples-and-tutorials`: Examples and Tutorials (worked examples, tutorials, and cookbook usage)
- `elmerfem-api-and-scripting`: API and Scripting (language bindings, APIs, and programmatic interfaces)
- `elmerfem-simulation-workflows`: Simulation Workflows (simulation setup, execution flow, and runtime controls)
- `elmerfem-getting-started`: Getting Started (initial setup, quickstarts, and core concepts)
- `elmerfem-inputs-and-modeling`: Inputs and Modeling (inputs, system setup, models, and physical parameterization)
- `elmerfem-theory-and-methods`: Theory and Methods (theoretical background and algorithmic methods)
- `elmerfem-analysis-and-output`: Analysis and Output (output formats, analysis, and post-processing)
- `elmerfem-parallel-hpc`: Parallel and HPC (MPI/OpenMP/GPU execution, scaling, and batch systems)
- `elmerfem-troubleshooting`: Troubleshooting (known issues, diagnostics, and debugging patterns)
- `elmerfem-fem`: Fem (documentation grouped under the 'fem' theme)
- `elmerfem-elmerice`: Elmerice (documentation grouped under the 'elmerice' theme)
- `elmerfem-releasenotes`: Releasenotes (documentation grouped under the 'releasenotes' theme)
- `elmerfem-elmergui`: Elmergui (documentation grouped under the 'elmergui' theme)

## Documentation-first inputs
- `ReleaseNotes`
- `compilation_instructions`
- `elmerice/ReleaseNotes`
- `fhutiter/doc`
- `matc/doc`
- `elmerice/Solvers/Documentation`
- `elmerice/UserFunctions/Documentation`
- `elmerice/Utils/Documentation`

## Tutorials and examples roots
- `ElmerGUI/samples`
- `elmerice/examples`
- `fem/examples`
- `fhutiter/examples`

## Test roots for behavior checks
- `elmergrid/tests`
- `elmerice/Tests`
- `fem/tests`
- `ElmerWorkflows/FreeCADBatchFEMTools/tests`
- `fem/src/binio/test`

## Escalate only when needed
- Start from topic skill primary references.
- If those references are insufficient, open the selected topic skill doc map (for example `skills/elmerfem-simulation-workflows/references/doc_map.md`).
- If documentation still leaves ambiguity, open the selected topic skill source map (for example `skills/elmerfem-simulation-workflows/references/source_map.md`) and inspect the suggested source entry points.
- Use targeted symbol search while inspecting source (e.g., `rg -n "<symbol_or_keyword>" ElmerGUIlogger/src ElmerGUItester/src ElmerWorkflows/FreeCADBatchFEMTools elmergrid/src elmerice/Solvers elmerice/UserFunctions elmerice/Utils fem/src fhutiter/src matc/src mathlibs/src meshgen2d/src ElmerGUI/Application/src ElmerGUI/PythonQt/src`).

## Default simulation start order
1. `elmerfem-build-and-install`: verify binaries/libraries and run smoke tests.
2. `elmerfem-examples-and-tutorials` or `elmerfem-elmerice`: run an unmodified reference case.
3. `elmerfem-simulation-workflows`: orchestrate mesh/partition/restart/output checks.
4. `elmerfem-inputs-and-modeling`: modify physics in SIF files once baseline run is stable.

## Source directories for deeper inspection
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
