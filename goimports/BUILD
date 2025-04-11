load("@bazel_skylib//:bzl_library.bzl", "bzl_library")

package(
    default_visibility = [
        "//:__pkg__",
        "//:__subpackages__",
    ],
)

exports_files(["runner.bash.template"])

bzl_library(
    name = "goimports",
    srcs = [
        "def.bzl",
        "deps.bzl",
    ],
)
