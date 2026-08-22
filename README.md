# EXOL Tool - Releases

Release assets for EXOL Tool. This repository holds **no source history** - it
exists only to distribute the built application.

## The two files

Both sit in the root of this repository and are always the **current build**.
Older versions stay on their release tags; they are not kept here.

| File                 | What it is                                            |
|----------------------|-------------------------------------------------------|
| `EXOLTool-Setup.exe` | Installer. Run as administrator. Installs to `C:\Program Files\IITS\EXOLTool`, makes desktop and Start Menu shortcuts, and grants the folder the write access the app needs to update itself without a UAC prompt. |
| `EXOLTool.exe`       | The application. **Not standalone** - see below.       |

### Use the installer

`EXOLTool.exe` does not run on its own. It loads its forms from files beside it
at startup, so on its own it opens and then fails as soon as a tab is used. It
needs the rest of the application folder, which is what the installer sets up
and what `EXOLTool.zip` on the release tag contains.

If you already have EXOL Tool installed and only want to swap the binary, this
is the file. For anything else, run the installer.

## On the release tags

| Asset                | Purpose                                                 |
|----------------------|----------------------------------------------------------|
| `version.json`       | Manifest: version, date, sha256, size, notes. The in-app updater reads this. |
| `EXOLTool.zip`       | The full application folder - exe, form scripts, shared modules. |
| `EXOLTool-Setup.exe` | The same installer as in the root.                       |

The updater reads `releases/latest/download/`, which redirects to whichever
release is newest - so the client URL never changes.

## Note

The EXEs are not code-signed yet, so Windows SmartScreen will warn about an
unknown publisher on first run.

Releases are cut by `build.ps1 -Publish` in the private source repository.
Nothing is committed here by hand.
