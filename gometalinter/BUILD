load("@bazel_skylib//:bzl_library.bzl", "bzl_library")

package(
    default_visibility = [
        "//:__pkg__",
        "//:__subpackages__",
    ],
)

exports_files(["runner.bash.template"])

bzl_library(
    name = "gometalinter",
    srcs = [
        "def.bzl",
        "deps.bzl",
    ],
)
