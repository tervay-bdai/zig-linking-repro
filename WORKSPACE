load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

RULES_PYTHON = {
    "version": "0.23.1",
    "sha": "84aec9e21cc56fbc7f1335035a71c850d1b9b5cc6ff497306f84cced9a769841",
}
RULES_ROS2 = {
    "version": "e5ca0b2f86a3e9f1b97ff8d6b2a8e3e03185ad81",
    "sha": "56e78c7910c6684a051c0754cc58739484800b11a64e542194a25c34dc8bc488",
}
HERMETIC_CC_TOOLCHAIN = {
    "version": "2.0.0",
    "sha": "57f03a6c29793e8add7bd64186fc8066d23b5ffd06fe9cc6b0b8c499914d3a65",
}

http_archive(
    name = "rules_python",
    sha256 = RULES_PYTHON["sha"],
    strip_prefix = "rules_python-{}".format(RULES_PYTHON["version"]),
    url = "https://github.com/bazelbuild/rules_python/releases/download/{0}/rules_python-{0}.tar.gz".format(RULES_PYTHON["version"]),
)

http_archive(
    name = "com_github_mvukov_rules_ros2",
    sha256 = RULES_ROS2["sha"],
    strip_prefix = "rules_ros2-{}".format(RULES_ROS2["version"]),
    url = "https://github.com/mvukov/rules_ros2/archive/{}.tar.gz".format(RULES_ROS2["version"]),
)

http_archive(
    name = "hermetic_cc_toolchain",
    sha256 = HERMETIC_CC_TOOLCHAIN["sha"],
    url = "https://github.com/uber/hermetic_cc_toolchain/releases/download/v{0}/hermetic_cc_toolchain-v{0}.tar.gz".format(HERMETIC_CC_TOOLCHAIN["version"]),
)


load("@rules_python//python:repositories.bzl", "py_repositories")

py_repositories()

load("@com_github_mvukov_rules_ros2//repositories:repositories.bzl", "ros2_repositories")

ros2_repositories()

load("@com_github_mvukov_rules_ros2//repositories:deps.bzl", "PIP_ANNOTATIONS", "ros2_deps")

ros2_deps()

load("@rules_python//python:repositories.bzl", "python_register_toolchains")
load("@hermetic_cc_toolchain//toolchain:defs.bzl", zig_toolchains = "toolchains")

python_register_toolchains(
    name = "python",
    python_version = "3.10.6",
)

python_register_toolchains(
    name = "rules_ros2_python",
    python_version = "3.10.6",
)

zig_toolchains()
register_toolchains(
    "@zig_sdk//toolchain:linux_amd64_gnu.2.34",
    "@zig_sdk//toolchain:linux_arm64_gnu.2.34",
)

load("@rules_python//python:pip.bzl", "pip_parse")
load("@rules_ros2_python//:defs.bzl", rules_ros2_interpreter = "interpreter")
load("@com_github_mvukov_rules_ros2//repositories:deps.bzl", "PIP_ANNOTATIONS")

pip_parse(
    name = "rules_ros2_pip_deps",
    annotations = PIP_ANNOTATIONS,
    python_interpreter_target = rules_ros2_interpreter,
    requirements_lock = "@com_github_mvukov_rules_ros2//:requirements_lock.txt",
)

load("@rules_ros2_pip_deps//:requirements.bzl", install_rules_ros2_pip_deps = "install_deps")

install_rules_ros2_pip_deps()
