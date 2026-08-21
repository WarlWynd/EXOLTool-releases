# EXOL Tool - Releases

Release assets for EXOL Tool. This repository holds **no source history** - it
exists only to distribute the built application.

## The file you want

`EXOLTool-Setup.exe`, in the root of this repository, always the **current
build**. Run it as an administrator. It installs to
`C:\Program Files\IITS\EXOLTool`, creates desktop and Start Menu shortcuts, and
grants the folder the write access the app needs to update itself without a UAC
prompt afterwards.

The installer downloads the application itself, so it is the only file you need.

## On the release tags

| Asset               | Purpose                                                  |
|---------------------|-----------------------------------------------------------|
| `version.json`      | Manifest: version, date, sha256, size, notes. The in-app updater reads this. |
| `EXOLTool.zip`      | The application folder. What the installer and the updater unpack. |
| `EXOLTool-Setup.exe`| The same installer as in the root.                        |

The updater reads `releases/latest/download/`, which redirects to whichever
release is newest - so the client URL never changes.

## Why the application EXE is not in the root

`EXOLTool.exe` does not run on its own. It loads its forms from files beside it
at startup, so an exe on its own starts and then fails as soon as a tab is
opened. `EXOLTool.zip` on the release tag is the runnable artifact - or just use
the installer, which handles it.

## Note

The installer is not code-signed yet, so Windows SmartScreen will warn about an
unknown publisher on first run.

Releases are cut by `build.ps1 -Publish` in the private source repository.
Nothing is committed here by hand.
