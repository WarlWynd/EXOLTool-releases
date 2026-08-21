# EXOL Tool - Releases

Release assets for EXOL Tool. This repository holds **no source history** - it
exists only so the in-app updater has a public endpoint to fetch from.

Each release carries two assets:

| Asset          | Purpose                                                       |
|----------------|---------------------------------------------------------------|
| `version.json` | Manifest: version, date, sha256, size, release notes          |
| `EXOLTool.zip` | The application folder                                        |

The updater reads them through `releases/latest/download/`, which redirects to
whichever release is newest - so the client URL never changes.

Releases are cut by `build.ps1 -Publish` in the private source repository.
Nothing is committed here by hand.
