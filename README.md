# Temporary Godot engine artifacts

This repository contains only the Godot source pin, its temporary patch queue,
license notices and downloadable engine archives. It contains no Aeons game
or platform source. Remove this unit when a qualified official Godot 4.8 build
replaces the complete patch queue.

The engine identity is `4.7.2.stable.aeons_patch1.ed1daf0bf`.
The base is Godot 4.7.2-stable at
`ed1daf0bf001b61586d9930840f2f1394092c079`.
[`build.json`](build.json) pins every patch and desktop dependency by SHA-256.
[`archives.json`](archives.json) pins each archive and lists its contents.

Apply these patches, in order, to an empty checkout of the exact upstream pin:

1. `cache-waits.patch`: release registered allowance locks at the loader waits.
2. `upstream-122064.patch`: preserve exact upstream commit
   `53ec17a1d2ae9a742ca5a2f65906f52604dfae6e`.
3. `upstream-121958.patch`: preserve exact upstream commit
   `5a4e2e8f186072ebf811f03baf2e0bbc22bb990a`.

The upstream patch files retain their original source and author markers.
Build Linux and Windows editors and release templates on Linux with the
pinned dependencies. Linux uses the Godot Buildroot SDK. Windows uses
LLVM-MinGW with WinRT, AccessKit, D3D12 and ANGLE enabled. Builds set
`BUILD_NAME=aeons_patch1`, `dev_build=no`, `debug_symbols=no`, `optimize=speed`,
`lto=none`, `arch=x86_64`. Windows also sets `use_mingw=yes`, `use_llvm=yes`,
`agility_sdk_multiarch=no` and `import_env_vars=TMPDIR`.

Linux runtime controls pass. Windows qualification uses Wine/Proton on Linux,
with Vulkan as the required renderer and translated D3D12 as a report.
No native Windows driver has run. Qualification is still in progress.
Do not infer production activation from the existence of an archive.
macOS remains on the official Godot build.

Godot and this engine patch queue use the MIT license in
[`LICENSE.txt`](LICENSE.txt). Third-party components retain their own licenses;
the MIT license does not replace them. Keep
[`COPYRIGHT.txt`](COPYRIGHT.txt) and [`notices/`](notices/) with redistribution.
The Microsoft Direct3D runtime DLLs retain Microsoft's accompanying terms.
