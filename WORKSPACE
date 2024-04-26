load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

http_archive(
    name = "toolchains_llvm",
    canonical_id = "1.0.0",
    sha256 = "e91c4361f99011a54814e1afbe5c436e0d329871146a3cd58c23a2b4afb50737",
    strip_prefix = "toolchains_llvm-1.0.0",
    url = "https://github.com/bazel-contrib/toolchains_llvm/releases/download/1.0.0/toolchains_llvm-1.0.0.tar.gz",
)

load("@toolchains_llvm//toolchain:deps.bzl", "bazel_toolchain_dependencies")

bazel_toolchain_dependencies()

load("@toolchains_llvm//toolchain:rules.bzl", "llvm_toolchain")

llvm_toolchain(
    name = "llvm_toolchain",
    llvm_version = "17.0.6",
)

load("@llvm_toolchain//:toolchains.bzl", "llvm_register_toolchains")

llvm_register_toolchains()

http_archive(
    name = "llvm-raw",
    build_file = "//build/llvm-raw:BUILD.llvm-raw",
    canonical_id = "17.0.6",
    integrity = "sha256-gUlNMubxLqb3PW0lQk29I2RkYBG7j340XKhwdQqifeE=",
    strip_prefix = "llvm-project-llvmorg-17.0.6",
    url = "https://github.com/llvm/llvm-project/archive/refs/tags/llvmorg-17.0.6.tar.gz",
)

http_archive(
    name = "com_github_facebook_zstd",
    build_file = "//build/com_facebook_zstd:BUILD.zstd",
    canonical_id = "1.5.5",
    integrity = "sha256-nEOWzIKc+uMZpuJhUgLoKq1BNyBzSC/OKG+seGRtPuQ=",
    strip_prefix = "zstd-1.5.5",
    url = "https://github.com/facebook/zstd/releases/download/v1.5.5/zstd-1.5.5.tar.gz",
)

http_archive(
    name = "net_zlib_zlib",
    build_file = "//build/net_zlib_zlib:BUILD.zlib",
    canonical_id = "1.2.13",
    integrity = "sha256-s6JN6XqP28g1uYMxaVAQMLiXcDG8tUs7OsE3QPhGqzA=",
    strip_prefix = "zlib-1.2.13",
    url = "https://github.com/madler/zlib/releases/download/v1.2.13/zlib-1.2.13.tar.gz",
)

load("@llvm-raw//utils/bazel:configure.bzl", "llvm_configure")

llvm_configure(
    name = "llvm-project",
    repo_mapping = {
        "@llvm_zlib": "@net_zlib_zlib",
        "@llvm_zstd": "@com_github_facebook_zstd",
    },
)
