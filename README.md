# PvZ-Advance-CI

Build and release workflows for the PvZ-AdvanceTX decompilation
(`https://github.com/IsraelDXPP/PvZ-AdvanceTX`). The workflows check the
source repository out (`SOURCE_REPO`) and build it.

| Workflow | Builds |
| --- | --- |
| `.github/workflows/build-androidtv.yml` | Windows, macOS, Linux, Android, iOS (unsigned IPA) and the release |
| `.github/workflows/build-lawntv-uwp.yml` | UWP |

## Keep it in sync with the source repository

The source repository carries its own copy of the pipeline in
`.github/workflows/build.yml`. **The two are one pipeline kept in two places:**

- A change to a workflow, or to something a job packs (`ios/`, `android/`,
  `Shaders/*.scbp`, `ios/setup.ios.env`, preset names, the `vcpkg.json`
  baseline, asset copy steps), is made in **both** repositories in the same
  round of work.
- The files are not byte-identical (this repository uses a token to check the
  source out and has the release and UWP jobs): port the change, not the file.
- Validate the YAML in both before pushing.

The rule is written down in the source repository's `CLAUDE.md`,
`AGENTS.md` (rule 14) and `docs/upstream.md`.
