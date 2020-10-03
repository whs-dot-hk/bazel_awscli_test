load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

http_archive(
    name = "io_bazel_rules_docker",
    sha256 = "4521794f0fba2e20f3bf15846ab5e01d5332e587e9ce81629c7f96c793bb7036",
    strip_prefix = "rules_docker-0.14.4",
    urls = ["https://github.com/bazelbuild/rules_docker/releases/download/v0.14.4/rules_docker-v0.14.4.tar.gz"],
)

load(
    "@io_bazel_rules_docker//repositories:repositories.bzl",
    container_repositories = "repositories",
)
container_repositories()

load("@io_bazel_rules_docker//repositories:deps.bzl", container_deps = "deps")

container_deps()

load("@io_bazel_rules_docker//repositories:pip_repositories.bzl", "pip_deps")

pip_deps()

load(
    "@io_bazel_rules_docker//container:container.bzl",
    "container_pull",
)

container_pull(
    name = "python3_base",
    digest = "sha256:6263f412090b815afc2eb5aca0fbb4b391aa7faa81394186b8dadffd13b1e6a3",  # 3.7.9-stretch
    registry = "docker.io",
    repository = "python",
)

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

all_content = """filegroup(name = "all", srcs = glob(["**"]), visibility = ["//visibility:public"])"""

http_archive(
    name = "awscli_v1",
    build_file_content = all_content,
    strip_prefix = "awscli-bundle",
    urls = ["https://s3.amazonaws.com/aws-cli/awscli-bundle.zip"],
)

http_archive(
    name = "awscli_v2",
    build_file_content = all_content,
    urls = ["https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip"],
)
