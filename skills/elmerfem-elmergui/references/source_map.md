# elmerfem source map: Elmergui

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
- `elmergui`
- `in2d`
- `samples`
- `step`

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
- `ElmerGUI/PythonQt/src/PythonQtImportFileInterface.h` | score: 5 | matched tokens: elmergui
- `ElmerGUI/Application/src/solverparameters.h` | score: 5 | matched tokens: elmergui
- `ElmerGUI/Application/src/solverparameters.cpp` | score: 5 | matched tokens: elmergui
- `ElmerGUI/Application/src/solverlogwindow.h` | score: 5 | matched tokens: elmergui
- `ElmerGUI/Application/src/solverlogwindow.cpp` | score: 5 | matched tokens: elmergui
- `ElmerGUI/Application/src/materiallibrary.h` | score: 5 | matched tokens: elmergui
- `ElmerGUI/Application/src/materiallibrary.cpp` | score: 5 | matched tokens: elmergui
- `ElmerGUI/Application/src/mainwindow.h` | score: 5 | matched tokens: elmergui
- `ElmerGUI/Application/src/mainwindow.cpp` | score: 5 | matched tokens: elmergui
- `ElmerGUI/Application/src/main.cpp` | score: 5 | matched tokens: elmergui
- `ElmerGUI/Application/src/boundarypropertyeditor.h` | score: 5 | matched tokens: elmergui
- `ElmerGUI/Application/src/boundarypropertyeditor.cpp` | score: 5 | matched tokens: elmergui
- `ElmerGUI/Application/src/boundarydivision.h` | score: 5 | matched tokens: elmergui
- `ElmerGUI/Application/src/boundarydivision.cpp` | score: 5 | matched tokens: elmergui
- `ElmerGUI/PythonQt/src/PythonQtWrapper.h` | score: 5 | matched tokens: elmergui
- `ElmerGUI/PythonQt/src/PythonQtWrapper.cpp` | score: 5 | matched tokens: elmergui
- `ElmerGUI/PythonQt/src/PythonQtVariantWrapper.h` | score: 5 | matched tokens: elmergui
- `ElmerGUI/PythonQt/src/PythonQtVariantWrapper.cpp` | score: 5 | matched tokens: elmergui
- `ElmerGUI/PythonQt/src/PythonQtVariants.h` | score: 5 | matched tokens: elmergui
- `ElmerGUI/PythonQt/src/PythonQtVariants.cpp` | score: 5 | matched tokens: elmergui
- `ElmerGUI/PythonQt/src/PythonQtSystem.h` | score: 5 | matched tokens: elmergui
- `ElmerGUI/PythonQt/src/PythonQtStdOut.h` | score: 5 | matched tokens: elmergui
- `ElmerGUI/PythonQt/src/PythonQtStdOut.cpp` | score: 5 | matched tokens: elmergui
- `ElmerGUI/PythonQt/src/PythonQtStdDecorators.h` | score: 5 | matched tokens: elmergui
- `ElmerGUI/PythonQt/src/PythonQtStdDecorators.cpp` | score: 5 | matched tokens: elmergui
- `ElmerGUI/PythonQt/src/PythonQtSlot.h` | score: 5 | matched tokens: elmergui
- `ElmerGUI/PythonQt/src/PythonQtSlot.cpp` | score: 5 | matched tokens: elmergui
- `ElmerGUI/PythonQt/src/PythonQtSignalReceiver.h` | score: 5 | matched tokens: elmergui
- `ElmerGUI/PythonQt/src/PythonQtSignalReceiver.cpp` | score: 5 | matched tokens: elmergui
- `ElmerGUI/PythonQt/src/PythonQtObjectPtr.h` | score: 5 | matched tokens: elmergui
