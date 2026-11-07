# Contributing

Thanks for helping. Bugs and ideas for this mod go in
[issues](https://github.com/Open-HMG/hmgapi-nemesis-shortcut/issues); code and docs in pull requests.
Problems with HMG-API itself (the app, the installer, the engine, hook points) go to
[HMG-API's issues](https://github.com/Open-HMG/HMG-API/issues/new/choose).

## Before a pull request

- Build and test off the car with the HMG-API mod SDK, as CI does (the SDK
  `hmgapi-sdk.json` pins; until HMG-API 1.0.3, `./build.sh sdk` in HMG-API at that
  commit). Needs a JDK, Python 3 and the Android SDK (`ANDROID_HOME`); no car files or keys.
- Package: `$HMGAPI_SDK/bin/mkmodpkg.sh nemesis-shortcut <key>` (make a key with
  `java -cp $HMGAPI_SDK/lib/hmgapi-engine.jar hmgapi.engine.Signing keygen <key file>`).
- Say which cars (model, region, software version) a change was tested on, or "off-car only".
- Mod scripts: only commands the head unit has (`$HMGAPI_SDK/bin/check-scripts.sh nemesis-shortcut`).
- A new hook point is a HMG-API pull request first (its catalogue entry, mapped on every
  car); this mod uses it once a HMG-API release has it (HMG-API's `docs/mod-repos.md`,
  section 4).
- Don't change `nemesis-shortcut/mod.json`'s `"version"`: it's set when a release is made.
- Who reviews what (`.github/CODEOWNERS`): VysseCodes reviews CI and releases
  (`.github/`); everything else needs one of the Open-HMG maintainers.

## Rules

- Anything that writes to `/system` keeps a stock checksum check, a backup and an
  uninstall that restores the exact stock bytes.
- The repo holds no manufacturer apps or libraries: only hooks, hash-only recipes,
  delta patch sets, checksums and our own code.
- Never collect or publish per-car secrets (VIN, serials, keys, account tokens,
  `/data` contents), in code, reports, logs or issues.
- Vehicle commands go through the car's own services, never our own CAN frames.
- Commit messages describe the change in plain words.

By contributing you agree your work is licensed under AGPL-3.0.
