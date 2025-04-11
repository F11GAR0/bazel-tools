# file_hash

Bazel rule for hashing. Supports MD5, SHA1, SHA256, SHA512.

## Setup and usage via Bazel

`WORKSPACE` file:

```bzl
load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")
load("@bazel_tools//tools/build_defs/repo:git.bzl", "git_repository")

# file_hash is written in Go and hence needs rules_go to be built.
# See https://github.com/bazelbuild/rules_go for the up to date setup instructions.
http_archive(
    name = "rules_go",
)

git_repository(
    name = "compat-bazel-tools",
    commit = "<commit>",
    remote = "https://github.com/ash2k/bazel-tools.git",
    shallow_since = "<bla>",
)
```

`BUILD.bazel` file:

```bzl
load("@compat-bazel-tools//file_hash:def.bzl", "file_hash")

file_hash(
    name = "something_sha256",
    algorithm = "sha256",
    hex = True,
    files = [
        "file1",
        "file2",
    ],
)
```
