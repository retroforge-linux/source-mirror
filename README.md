# source-mirror

Copies of [retroforge-linux/os-build](https://github.com/retroforge-linux/os-build)'s build
inputs, so one upstream host going down does not stop a build: source tarballs, the kernel
tarball, the FEX guest RootFS, the Arch Linux Archive files the x86 Mesa builder installs, and
the git sources makepkg clones.

Everything is in the releases, one per kind, under the files' own names:

| release | holds |
|---|---|
| `sources` | the kernel, mesa and PKGBUILD source tarballs (`linux-7.3.5.tar.xz`, `qrtr-1.2.tar.gz`) |
| `prebuilt` | prebuilt downloads (`pygame_ce-...whl`) |
| `fex-rootfs` | the FEX guest image (`ArchLinux-2026-08-11.sqsh`) |
| `git` | git sources as bundles (`gamescope-3.17.0-e6674a98118c.bundle`) |
| `archlinux-<date>-<repo>` | the Arch Linux Archive files the x86 Mesa builder installs from that snapshot |

The list of what belongs here is os-build's `mirror/sources.lock`. os-build's build reads this
mirror first and upstream second, and checks every file against its pinned hash, so a copy here
can only make a build succeed, never change what is built. os-build's CI uploads what the lock names
and the releases lack before every build; this repo's `sync` workflow does the same every day.

How it works and how to refresh the lock: os-build
[tools/source-mirror/README.md](https://github.com/retroforge-linux/os-build/blob/main/tools/source-mirror/README.md).

The files are their upstreams' own releases, under their own licences; this repository only keeps
copies.
