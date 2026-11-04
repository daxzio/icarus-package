# icarus-package

Prebuilt [Icarus Verilog](https://github.com/steveicarus/iverilog) binaries. This repo does not contain the simulator.

The build workflow checks out an upstream tag, compiles Icarus on `ubuntu-24.04`, and attaches `icarus-ubuntu-24.04.tar.gz` to a release of the same name. The archive is a prefix install (`bin/`, `lib/ivl/`, and the headers). [`daxzio/setup-icarus`](https://github.com/daxzio/setup-icarus) downloads that asset and adds `bin` to `PATH`. A workflow that uses the action does not compile Icarus.

`iverilog` locates `lib/ivl` from its own path, so the extracted tree can live anywhere as long as `bin` and `lib` stay side by side.

The binary is licensed the same way as [steveicarus/iverilog](https://github.com/steveicarus/iverilog) (GPL-2.0).

## Publish a version

Actions → Build → Run workflow. Set `tag` to an upstream tag such as `v13_0`.

The asset URL is:

```text
https://github.com/daxzio/icarus-package/releases/download/<tag>/icarus-ubuntu-24.04.tar.gz
```
