workspace(name = "envoy_filter_example")


# http_archive is not a native function since bazel 0.19
load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive", "http_file")

# 1. Determine SHA256 `wget https://github.com/istio/envoy/archive/$COMMIT.tar.gz && sha256sum $COMMIT.tar.gz`
# 2. Update .bazelversion, envoy.bazelrc and .bazelrc if needed.
#
# Note: this is needed by release builder to resolve envoy dep sha to tag.
# Commit date: 2020-11-10
ENVOY_SHA = "cd87e827e33cc92d9c2d849f786822a0d407803f"

ENVOY_SHA256 = "6a3b8815a730bd822ce1746667c4ae5b2bd6af6cc20a65e9ab9c7bfe278e60d8"

ENVOY_ORG = "istio"

ENVOY_REPO = "envoy"

# To override with local envoy, just pass `--override_repository=envoy=/PATH/TO/ENVOY` to Bazel or
# persist the option in `user.bazelrc`.
http_archive(
    name = "envoy",
    sha256 = ENVOY_SHA256,
    strip_prefix = ENVOY_REPO + "-" + ENVOY_SHA,
    url = "https://github.com/" + ENVOY_ORG + "/" + ENVOY_REPO + "/archive/" + ENVOY_SHA + ".tar.gz",
)


load("@envoy//bazel:api_binding.bzl", "envoy_api_binding")

envoy_api_binding()

load("@envoy//bazel:api_repositories.bzl", "envoy_api_dependencies")

envoy_api_dependencies()

load("@envoy//bazel:repositories.bzl", "envoy_dependencies")

envoy_dependencies()

load("@envoy//bazel:repositories_extra.bzl", "envoy_dependencies_extra")

envoy_dependencies_extra()

load("@envoy//bazel:dependency_imports.bzl", "envoy_dependency_imports")

envoy_dependency_imports()
