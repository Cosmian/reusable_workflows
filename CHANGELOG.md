# Changelog

All notable changes to this project will be documented in this file.

## [0.7] - 2025-05-10

### 🚀 Features

- Split FIPS tests (#29)
- Add workflows (#34)
- Add workflow to push on package.cosmian.com
- Add workflow to push on package.cosmian.com - add destination argument
- Rockylinux (#35)
- Add cargo workspace publish
- Reuse Cosmian rocky linux images

### 🐛 Bug Fixes

- Remove hardcoded registry image name
- Update cargo version for udeps
- Remove udeps, too unstable and too slow
- Darwin build (#23)
- Publish to PyPI with token instead of passwords (#25)
- *(pip)* Freeze pip version to 24.0
- Replace cargo-audit with cargo-deny
- Add toolchain in cargo fmt
- Use stable version of rust-toolchain
- Simplify workspace publish
- *(rockylinux)* Reinstall gcc
- Remove support of MacOS Intel. Build windows on debug too

### ⚙️ Miscellaneous Tasks

- Merge tag 'v0.6' into develop
- Fix(pyo3): build of windows/macos - bad triggering condition (#24)
- Upgrade centos 7 for rhel 8.5
- Bump ubuntu 20.04 to 22.04 for cloudproof_python tests
- Fix permissions on checkout
- Bump artifact@v3 to v4
- Add postgres container on lint.yml
- Add redis & postgres containers for benches (#30)
- Upgrade macos GH runner from 14 to 15
- Reenable cargo fmt check

## [0.6] - 2023-12-08

### Features

- Support of Findex 6.0.0 -> cloudproof_rust 2.4.0

## [0.5] - 2023-06-05

### Bug Fixes

- Individual package publishing

### Miscellaneous Tasks

- Merge tag 'v0.4' into develop

## [0.4] - 2023-06-03

### Bug Fixes

- Add features cloud and compact_live for cloudproof

### Features

- Include findex cloud in java tests

## [0.3] - 2023-06-02

### Features

- Support of cloudproof_rust 2.0.0

## [0.2] - 2023-03-08

### Bug Fixes

- Remove useless project-name
- Python build
- Discard darwin cp37-cp37 python build
- Split cargo nursery
- Remove semver if no publish
- Crates moved to crates folder
- Cbindgen output dir
- Python tests
- Wasm path
- Do not miss all targets tests (including examples)
- Pb size on .a: use only ffi feature for flutter (android, ios and x86)
- Python install requirements order
- Make ios build blocking if failing
- Disable ios build on flutter by default
- Remove target dir from github cargo cache for benches

### Features

- Support of:
  - CoverCrypt 11.0.0 - via cloudproof_rust
  - Findex 3.0.0 - via cloudproof_rust
  - KMS 4.3.3
  - cloudproof_java 5.0.0
  - cloudproof_js 8.0.0
  - cloudproof_flutter 6.0.0
  - cloudproof_python 3.0.0
- Add flutter test on mac
- Write branch name in artifacts

### Refactor

- Rename feature wasm
- Make features param optional in cargo-bench
- Non regression vector

### Testing

- Debug ios build

### Ci

- Make fresh build copy optional
- Adapt to cloudproof_rust, build both findex and cover_crypt
- Revert wasm feature to wasm_bindgen
- Remove publish part from cloudproof
- Install gnuplot for bench build (no run)
- Split cargo doc in a separate workflow
- Add missing cargo doc workflow
- Make flutter-darwin a blocking step
- Simplify tag tasks triggering syntax
- Handle multi branches

## [0.1] - 2023-02-14

### Bug Fixes

- Flutter test
- Update package
- Remove cache for flutter
- Wasm-pack publish
- Call requirements.txt for python
- Branch name for python
- Branch regression test path
- Branch regression test path
- Python install on centos7
- Download native libs via python script
- Generate bindings for flutter
- Generate bindings for flutter
- Delete ndk folder from gh cache
- Force reinstall target lib
- Test python on linux only
- Reuse workflow from local branch
- Source-dir
- Python tests
- Link python tests to packages task
- Pip install on windows
- Python tests on windows
- Pip install on windows
- Python runner version must be 3.8 for async tests
- Flutter test, copy fresh lib AFTER get_native_libraries.py
- Generate bindings for flutter
- Generate bindings for flutter
- Copy .h for flutter tests
- Delete last_build when tags is created
- Test on js, download wasm before
- Run bench on demands
- Run bench on demands
- Benchmark to markdown
- Upload benchmark results on tags only
- Freeze restore-keys
- Use last_build in CI by default
- Publish python
- Cloudproof workflow
- Python whl publish
- Missing pypi credentials
- Run cargo udeps in nightly

### Features

- Support of:
  - CoverCrypt 10.0.0
  - Findex 2.1.0
  - KMS 4.2.0
  - cloudproof_java 4.1.0
  - cloudproof_js 7.1.0
  - cloudproof_flutter 5.1.0
  - cloudproof_python 2.0.1
- Add cloudproof workflows
- Add android build
- Add regression vectors copy for cloudproof python
- Download native libs on demand
- Add python to cloudproof_java environment
- Run tests for pyo3 libs
- Python tests for win, mac and linux
- Add kms container to cloudproof_python tests
- Display cpuinfo before benches
- Autogenerate benchmarks.md

### Miscellaneous Tasks

- Push build on last_build directory of package.cosmian.com
- Push to package.cosmian.com build on tags too
- Update cargo name task
- Install missing deps for bench
- Dump github context for later use
- List files before python tests
- Call cleanup when everything succeed
- Build benches but only run on tags

### Ci

- Handle cache per cargo usage
- Passe github secrets to workflow
- Cannot support semver on findex nor covercrypt
- Run flutter test with non concurrency
- Cleanup flutter wf
- Remove findex references
- Re-enable semver check
- Build android
- Isolate android build
- Enable redis tests for cloudproof_java
- Force benchmarks even on tags
- Push to last_build only on non-tags commit
- Verify cargo useless dependencies

<!-- generated by git-cliff -->
