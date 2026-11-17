# icarus-package

Prebuilt [Icarus Verilog](https://github.com/steveicarus/iverilog) binaries. This repo does not contain the simulator.

The build workflow compiles Icarus on **ubuntu-24.04** and **ubuntu-26.04** and attaches both tarballs to one release:

- `icarus-ubuntu-26.04.tar.gz` — `ubuntu-26.04` / `ubuntu-latest` (while latest is 26.04)
- `icarus-ubuntu-24.04.tar.gz` — `ubuntu-24.04`

[`daxzio/setup-icarus`](https://github.com/daxzio/setup-icarus) picks the matching asset automatically.

`iverilog` locates `lib/ivl` from its own path, so the extracted tree can live anywhere as long as `bin` and `lib` stay side by side.

The binary is licensed the same way as [steveicarus/iverilog](https://github.com/steveicarus/iverilog) (GPL-2.0).

## Publish a version

Actions → Build → Run workflow.

- `tag` is the release name. For an upstream release use the tag, such as `v13_0`.
- `ref` is the upstream commit to compile. Leave it empty to build `tag`. A dated snapshot sets `tag` to the date and `ref` to the `master` commit that was the tip of the tree at the end of that day.
- `version_tag` is written into `iverilog -V` as `VERSION_TAG`. Leave it empty to keep `git describe`. A snapshot uses `2026.11.04-dirty`.
- `latest` marks that release as the one `setup-icarus` installs when `version` is omitted.
- `targets` — build both images (`all`), or only `24.04` or `26.04`.

Asset URLs:

```text
https://github.com/daxzio/icarus-package/releases/download/<tag>/icarus-ubuntu-26.04.tar.gz
https://github.com/daxzio/icarus-package/releases/download/<tag>/icarus-ubuntu-24.04.tar.gz
```