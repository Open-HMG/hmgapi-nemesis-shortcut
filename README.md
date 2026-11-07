# hmgapi-nemesis-shortcut

**NEMESIS in the app menu**, a mod for [HMG-API](https://github.com/Open-HMG/HMG-API)
on Hyundai, Kia and Genesis Gen5W head units: adds NEMESIS Manager to the all-apps
menu, and offers "Open NEMESIS" as a ★ key action.

The whole mod is its `mod.json`: a `"launcher"` entry and a `"star_key"` entry that
HMG-API's launcher and ★ key hooks show. No code, no files changed. It needs
[NEMESIS](https://github.com/xwtk/hmg_nemesis) Manager (`com.nemesis.manager`) on the
head unit.

## Cars

Every car HMG-API supports (no `"system"` limit), with HMG-API 0.1.0 or newer. HMG-API's
[Supported cars](https://github.com/Open-HMG/HMG-API/wiki/Supported-cars) lists them.

## Installing

From the HMG-API app (USB stick, `HMGAPI/updates/`), NEMESIS or adb: see
[Installing and removing mods](https://github.com/Open-HMG/HMG-API/wiki/Installing-and-removing-mods).
Until this repo's first release (after HMG-API 1.0.3), the package is the one on
[HMG-API v1.0.2](https://github.com/Open-HMG/HMG-API/releases/tag/v1.0.2):
`nemesis-shortcut-1.1.0.zip`, or `nemesis-shortcut-1.1.0-nemesis.zip` for NEMESIS.

## Building

```
nemesis-shortcut/  the mod (mod.json)
hmgapi-sdk.json    the HMG-API mod SDK it builds with (a HMG-API commit until 1.0.3)
.github/workflows  ci.yml (HMG-API's mod workflow), release.yml
```

With the SDK unpacked in `$HMGAPI_SDK`:

```
$HMGAPI_SDK/bin/mkmodpkg.sh nemesis-shortcut <key>
```

How mods build outside HMG-API: HMG-API's `docs/mod-reference.md`, "Building a mod
outside this repo". What `"launcher"` and `"star_key"` can do: HMG-API's
`docs/mod-reference.md`. A change that needs a new hook point starts as a HMG-API pull
request (`docs/mod-repos.md`, section 4).

## Releases

A tag `v<version>`, the same as `nemesis-shortcut/mod.json`'s `"version"`, runs
`release.yml`: it builds the mod, signs it with the author key (the `release`
environment's `MOD_KEY`, the key installed cars have) and makes a **draft** release with
the package and its NEMESIS package. A maintainer publishes it, then adds it to
HMG-API's catalogue by pull request with the `tools/catalog.py add` command the run
prints.

No releases until HMG-API 1.0.3.

## Licence

AGPL-3.0 ([LICENSE](LICENSE)).
