# llm-management-x64-dist

Public download mirror for the Windows x64 build of the Anro LLM Management
core (`anro-llm-core.exe`).

- Source code and build tooling live in `Anro-Lab/llm-management-x64`
  (private). This repository holds no source code.
- Every release here is a copy of the release with the same tag in the source
  repository. Both are created by `scripts/release-exe/publish-release.ps1`.
- AnroMark reads the latest release here (`/releases/latest`) to update its
  local AI core. Drafts and pre-releases are ignored.

## Release assets

| File | Content |
| ---- | ------- |
| `anro-llm-core-<version>-win-x64.zip` | the `anro-llm-core/` folder; the executable is `anro-llm-core/anro-llm-core.exe` |
| `anro-llm-core-<version>-win-x64.zip.sha256` | SHA-256 of the zip |
| `anro-llm-core-<version>-win-x64.manifest.json` | `version`, `tag`, `asset`, `assetSha256`, `assetBytes`, `exeInZip`, `fileCount`, `coreApi`, source `gitCommit` |

Tags are `v<version>`. `<version>` is a number; a larger number is newer.
`coreApi` is the interface level AnroMark checks before it uses a build.
Releases whose manifest has no `coreApi` field are level 1.

## Verify a download

```powershell
(Get-FileHash .\anro-llm-core-261027-win-x64.zip -Algorithm SHA256).Hash
```

The result must equal the `.sha256` file and `assetSha256` in the manifest.

## Rules

- Do not push source code here.
- Do not create or edit releases here by hand. Run `publish-release.ps1` from
  the source repository so both repositories get the same tag and assets.
