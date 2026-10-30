# mugo-prebuilt

Linux arm64 builds of open-source tools that the Mugo Studio images pin but whose upstream projects publish
no arm64 Linux binary that runs on our hosts. Each release is one tool at one version, for example
`blender-5.2.2` with `blender-5.2.2-linux-arm64.tar.xz` and its `.sha256`.

Inside each tarball:

- the tool, unpacked to one folder (libraries built alongside it in `lib/`, found through `$ORIGIN`)
- `runtime-packages.txt`: the Ubuntu 26.10 packages, at exact versions, to install next to it
- `BUILD-INFO`: the base image, the build host and every source archive with its sha256

The builds are unmodified upstream sources. Each tool keeps its own licence (Blender: GPL-2.0-or-later,
qpdf: Apache-2.0, OpenImageIO and OpenImageDenoise: Apache-2.0); the source archives are listed in
`BUILD-INFO` with their download URLs. The build recipes live in `tools/prebuilt/` of the Mugo Studio
repository and are published with `make -C tools/prebuilt build publish TOOL=<tool>`.
