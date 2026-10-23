# openwrt_build_cache

Per-package SDK build cache for openwrt_builder.

Layout: `<target>/<package-dir>/<package-dir>_<version>_cache.tar.xz`

Each tarball contains the files the OpenWrt SDK needs to treat a package as
already built (build_dir with its stamps, staged headers/libs, install stamp,
install metadata and the built binary package). It is unpacked into the SDK
directory before compiling, so dependency packages do not have to be rebuilt.

The cache is only an accelerator: when the SDK configuration or a dependency
changes, the stamps no longer match and OpenWrt rebuilds the package.
