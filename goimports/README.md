# goimports

Bazel rule for [goimports](https://pkg.go.dev/golang.org/x/tools/cmd/goimports?tab=doc).

## Limitations

This rule does not work with:

- generated Go code
- with Bazel-managed Go dependencies
- with Go modules, unless `go mod vendor` is used

## Setup and usage via Bazel

You can invoke goimports via the Bazel rule.

`WORKSPACE` file:

```bzl
load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")
load("@bazel_tools//tools/build_defs/repo:git.bzl", "git_repository")

# goimports is written in Go and hence needs rules_go and gazelle to be built.
# See https://github.com/bazelbuild/bazel-gazelle for the up to date setup instructions.
http_archive(
    name = "rules_go",
)

http_archive(
    name = "bazel_gazelle",
)

git_repository(
    name = "compat-bazel-tools",
    commit = "<commit>",
    remote = "https://github.com/ash2k/bazel-tools.git",
    shallow_since = "<bla>",
)

load("@compat-bazel-tools//goimports:deps.bzl", "goimports_dependencies")

goimports_dependencies()
```

`BUILD.bazel` typically in the workspace root:

```bzl
load("@compat-bazel-tools//goimports:def.bzl", "goimports")

goimports(
    name = "goimports",
    display_diffs = True,
    write = True,
    prefix = "<your project prefix>",
)
```

Invoke with

```bash
bazel run //:goimports
```
