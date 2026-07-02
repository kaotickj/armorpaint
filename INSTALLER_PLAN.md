name: Windows Installer Build

This branch adds a Windows installer packaging path for ArmorPaint so the app can be distributed as a bundled installer instead of requiring users to run the build system locally.

## What changed

- Adds a Windows packaging workflow based on Inno Setup.
- Bundles the built ArmorPaint executable with the runtime assets required for launch.
- Documents the build-and-package steps for Windows contributors.

## Files to add next

- `.github/workflows/windows-installer.yml` — GitHub Actions build + installer packaging
- `installer/armorpaint.iss` — Inno Setup script
- `installer/README.md` — local packaging notes
- `base/tools/package_windows.js` or similar — asset collection helper, if needed

## Notes

The repository already has a Windows target in `base/project.js` and a Windows launch path in `base/sources/backends/windows_system.c`, so the remaining work is packaging and installer generation.
