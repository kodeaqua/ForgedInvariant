# ForgedInvariant

Lilu plugin (macOS kext, x86_64) that synchronises the TSC across CPU threads on Intel and AMD.
Licensed under the Thou Shalt Not Profit License 1.5 — see `LICENSE`.

## Layout

- `ForgedInvariant/Plugin.cpp` — Lilu `PluginConfiguration` and boot args (`-FIOff`, `-FIDebug`, `-FIBeta`).
- `ForgedInvariant/TSCSyncer.{hpp,cpp}` — `TSCForger` singleton: CPU capability detection, `mp_rendezvous_no_intrs` sync, kernel routes (`_xcpm_urgency`, `IOPMrootDomain::tracePoint`, `clock_get_calendar_microtime`), periodic timer.
- `Lilu/`, `MacKernelSDK/` — git submodules; run `git submodule update --init --recursive` first.

## Build

```sh
xcodebuild -configuration Debug -arch x86_64 build
xcodebuild -configuration Research\ Release -arch x86_64 build
xcodebuild -configuration Release -arch x86_64 build
```

CI (`.github/workflows/main.yml`) builds all three configurations and runs `xcodebuild analyze`; the analyzer must produce zero HTML reports. Releases are cut from `v*` tags and require a matching `## vX.Y.Z` section in `CHANGELOG.md`.

## Conventions

- Style is enforced by `.clang-format` / `.clang-tidy`; keep the existing brace and comment style.
- Kernel context: no exceptions/RTTI, no blocking allocations in rendezvous callbacks, use the `SYSLOG`/`DBGLOG` macros.
- `threadCount` must equal the number of CPUs entering the rendezvous, otherwise the spin barriers hang the machine.
- Boot arg `-FIPeriodic` forces periodic sync (every 5 s); it is automatic when neither TSC_ADJUST nor AMD LockTscToCurrentP0 is available.
- Commit messages: English, conventional prefix (`feat:`, `fix:`, `chore:`, `docs:`).
- Kext cannot be loaded/tested without real hardware; the project cannot be built without the submodules checked out.
