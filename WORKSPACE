workspace(
    name = "angular_cli",
    managed_directories = {"@npm": ["node_modules"]},
)

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

http_archive(
    name = "bazel_skylib",
    sha256 = "cd55a062e763b9349921f0f5db8c3933288dc8ba4f76dd9416aac68acee3cb94",
    urls = [
        "https://mirror.bazel.build/github.com/bazelbuild/bazel-skylib/releases/download/1.5.0/bazel-skylib-1.5.0.tar.gz",
        "https://github.com/bazelbuild/bazel-skylib/releases/download/1.5.0/bazel-skylib-1.5.0.tar.gz",
    ],
)

http_archive(
    name = "io_bazel_rules_webtesting",
    sha256 = "e9abb7658b6a129740c0b3ef6f5a2370864e102a5ba5ffca2cea565829ed825a",
    urls = ["https://github.com/bazelbuild/rules_webtesting/releases/download/0.3.5/rules_webtesting.tar.gz"],
)

http_archive(
    name = "build_bazel_rules_nodejs",
    sha256 = "5dd1e5dea1322174c57d3ca7b899da381d516220793d0adef3ba03b9d23baa8e",
    urls = ["https://github.com/bazelbuild/rules_nodejs/releases/download/5.8.3/rules_nodejs-5.8.3.tar.gz"],
)

load("@build_bazel_rules_nodejs//:repositories.bzl", "build_bazel_rules_nodejs_dependencies")

build_bazel_rules_nodejs_dependencies()

http_archive(
    name = "rules_pkg",
    sha256 = "8c20f74bca25d2d442b327ae26768c02cf3c99e93fad0381f32be9aab1967675",
    urls = ["https://github.com/bazelbuild/rules_pkg/releases/download/0.8.1/rules_pkg-0.8.1.tar.gz"],
)

load("@bazel_tools//tools/sh:sh_configure.bzl", "sh_configure")

sh_configure()

load("@bazel_skylib//:workspace.bzl", "bazel_skylib_workspace")

bazel_skylib_workspace()

load("@rules_pkg//:deps.bzl", "rules_pkg_dependencies")

rules_pkg_dependencies()

# Setup the Node.js toolchain
load("@rules_nodejs//nodejs:repositories.bzl", "nodejs_register_toolchains")

NODE_18_REPO = {
    "18.19.1-darwin_arm64": ("node-v18.19.1-darwin-arm64.tar.gz", "node-v18.19.1-darwin-arm64", "0c7249318868877032ed21cc0ed450015ee44b31b9b281955521cd3fc39fbfa3"),
    "18.19.1-darwin_amd64": ("node-v18.19.1-darwin-x64.tar.gz", "node-v18.19.1-darwin-x64", "ab67c52c0d215d6890197c951e1bd479b6140ab630212b96867395e21d813016"),
    "18.19.1-linux_arm64": ("node-v18.19.1-linux-arm64.tar.xz", "node-v18.19.1-linux-arm64", "228ad1eee660fba3f9fd2cccf02f05b8ebccc294d27f22c155d20b233a9d76b3"),
    "18.19.1-linux_ppc64le": ("node-v18.19.1-linux-ppc64le.tar.xz", "node-v18.19.1-linux-ppc64le", "2e5812b8fc00548e2e8ab9daa88ace13974c16b6ba5595a7a50c35f848f7d432"),
    "18.19.1-linux_s390x": ("node-v18.19.1-linux-s390x.tar.xz", "node-v18.19.1-linux-s390x", "15106acf4c9e3aca02416dd89fb5c71af77097042455a73f9caa064c1988ead5"),
    "18.19.1-linux_amd64": ("node-v18.19.1-linux-x64.tar.xz", "node-v18.19.1-linux-x64", "f35f24edd4415cd609a2ebc03be03ed2cfe211d7333d55c752d831754fb849f0"),
    "18.19.1-windows_amd64": ("node-v18.19.1-win-x64.zip", "node-v18.19.1-win-x64", "ff08f8fe253fba9274992d7052e9d9a70141342d7b36ddbd6e84cbe823e312c6"),
}

nodejs_register_toolchains(
    name = "node18",
    # The below can be removed once @rules_nodejs/nodejs is updated to latest which contains https://github.com/bazelbuild/rules_nodejs/pull/3701
    node_repositories = NODE_18_REPO,
    node_version = "18.19.1",
)

# Set the default nodejs toolchain to the latest supported major version
nodejs_register_toolchains(
    name = "nodejs",
    # The below can be removed once @rules_nodejs/nodejs is updated to latest which contains https://github.com/bazelbuild/rules_nodejs/pull/3701
    node_repositories = NODE_18_REPO,
    node_version = "18.19.1",
)

nodejs_register_toolchains(
    name = "node20",
    # The below can be removed once @rules_nodejs/nodejs is updated to latest which contains https://github.com/bazelbuild/rules_nodejs/pull/3701
    node_repositories = {
        "20.11.1-darwin_arm64": ("node-v20.11.1-darwin-arm64.tar.gz", "node-v20.11.1-darwin-arm64", "e0065c61f340e85106a99c4b54746c5cee09d59b08c5712f67f99e92aa44995d"),
        "20.11.1-darwin_amd64": ("node-v20.11.1-darwin-x64.tar.gz", "node-v20.11.1-darwin-x64", "c52e7fb0709dbe63a4cbe08ac8af3479188692937a7bd8e776e0eedfa33bb848"),
        "20.11.1-linux_arm64": ("node-v20.11.1-linux-arm64.tar.xz", "node-v20.11.1-linux-arm64", "c957f29eb4e341903520caf362534f0acd1db7be79c502ae8e283994eed07fe1"),
        "20.11.1-linux_ppc64le": ("node-v20.11.1-linux-ppc64le.tar.xz", "node-v20.11.1-linux-ppc64le", "51343cacf5cdf5c4b5e93e919d19dd373d6ef43d5f2c666eae299f26e31d08b5"),
        "20.11.1-linux_s390x": ("node-v20.11.1-linux-s390x.tar.xz", "node-v20.11.1-linux-s390x", "b32616b705cd0ddbb230b95c693e3d7a37becc2ced9bcadea8dc824cceed6be0"),
        "20.11.1-linux_amd64": ("node-v20.11.1-linux-x64.tar.xz", "node-v20.11.1-linux-x64", "d8dab549b09672b03356aa2257699f3de3b58c96e74eb26a8b495fbdc9cf6fbe"),
        "20.11.1-windows_amd64": ("node-v20.11.1-win-x64.zip", "node-v20.11.1-win-x64", "bc032628d77d206ffa7f133518a6225a9c5d6d9210ead30d67e294ff37044bda"),
    },
    node_version = "20.11.1",
)

load("@build_bazel_rules_nodejs//:index.bzl", "yarn_install")

yarn_install(
    name = "npm",
    data = [
        "//:.yarn/releases/yarn-1.22.17.cjs",
        "//:.yarnrc",
        "//:tools/postinstall/patches/@angular+bazel+17.0.0-next.1.patch",
        "//:tools/postinstall/patches/@bazel+concatjs+5.8.1.patch",
    ],
    # Currently disabled due to:
    #  1. Missing Windows support currently.
    #  2. Incompatibilites with the `ts_library` rule.
    exports_directories_only = False,
    package_json = "//:package.json",
    # We prefer to symlink the `node_modules` to only maintain a single install.
    # See https://github.com/angular/dev-infra/pull/446#issuecomment-1059820287 for details.
    symlink_node_modules = True,
    yarn = "//:.yarn/releases/yarn-1.22.17.cjs",
    yarn_lock = "//:yarn.lock",
)

http_archive(
    name = "aspect_bazel_lib",
    sha256 = "ac6392cbe5e1cc7701bbd81caf94016bae6f248780e12af4485d4a7127b4cb2b",
    strip_prefix = "bazel-lib-2.6.1",
    url = "https://github.com/aspect-build/bazel-lib/releases/download/v2.6.1/bazel-lib-v2.6.1.tar.gz",
)

load("@aspect_bazel_lib//lib:repositories.bzl", "aspect_bazel_lib_dependencies", "aspect_bazel_lib_register_toolchains")

aspect_bazel_lib_dependencies()

aspect_bazel_lib_register_toolchains()

register_toolchains(
    "@npm//@angular/build-tooling/bazel/git-toolchain:git_linux_toolchain",
    "@npm//@angular/build-tooling/bazel/git-toolchain:git_macos_x86_toolchain",
    "@npm//@angular/build-tooling/bazel/git-toolchain:git_macos_arm64_toolchain",
    "@npm//@angular/build-tooling/bazel/git-toolchain:git_windows_toolchain",
)

load("@npm//@angular/build-tooling/bazel/browsers:browser_repositories.bzl", "browser_repositories")

browser_repositories()
