# ArmorPaint Windows Installer Plan

## Goal
Create a Windows installer artifact for ArmorPaint so users can download and install a ready-to-run build without manually invoking the build system.

## Current repo signals
- Windows target exists in `base/project.js`.
- Windows startup and file location logic already exist in `base/sources/backends/windows_system.c` and `base/sources/iron.h`.
- The README currently instructs Windows users to run `..\base\make` and open the generated Visual Studio solution.

## Proposed packaging approach
Use **Inno Setup** for the installer because it is straightforward for Windows desktop apps and can package:
- the ArmorPaint executable
- shipped assets
- required runtime DLLs
- shortcuts/uninstaller metadata

## Implementation outline
1. Add a GitHub Actions workflow that builds the Windows target.
2. Collect the build output and runtime assets into a staging directory.
3. Generate an Inno Setup script that points at the staging directory.
4. Publish the installer as a workflow artifact.

## Likely installer contents
- `ArmorPaint.exe`
- `data/` assets
- any required runtime DLLs from the build output
- license/readme files

## Follow-up work
After this scaffold lands, the next commit should add the actual workflow + installer script.
