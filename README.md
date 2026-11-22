# source-mirror

Copies of [retroforge-linux/os-build](https://github.com/retroforge-linux/os-build)'s build
inputs, so one upstream host going down does not stop a build: source tarballs, the kernel
tarball, the FEX guest RootFS, the Arch Linux Archive files the x86 Mesa builder installs, and
the git sources makepkg clones.

Everything is in the releases, content-addressed:

- a file is the asset `<sha256>`, a git source the asset `<commit>.bundle`;
- each lives in release `shard-<first hex digit>` (`shard-0` .. `shard-f`).

The list of what belongs here is os-build's `mirror/sources.lock`. os-build's build reads this
mirror first and upstream second, and checks every file against its pinned hash, so a copy here
can only make a build succeed, never change what is built. The `sync` workflow uploads what the
lock names and the releases lack, every day and on demand.

How it works and how to refresh the lock: os-build
[tools/source-mirror/README.md](https://github.com/retroforge-linux/os-build/blob/main/tools/source-mirror/README.md).

The files are their upstreams' own releases, under their own licences; this repository only keeps
copies.
