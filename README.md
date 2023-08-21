Bazel 6.3.2

```sh
$ bazelisk run //src:ex

INFO: Analyzed target //src:ex (0 packages loaded, 0 targets configured).
INFO: Found 1 target...
ERROR: /home/jtervay/.cache/bazel/_bazel_jtervay/2ba880a27a7b10a0e8a3abfc5bd990ba/external/ros2_rclpy/BUILD.bazel:11:16: Linking external/ros2_rclpy/rclpy/rclpy/_rclpy_pybind11.so failed: (Exit 1): c++ failed: error executing command (from target @ros2_rclpy//:rclpy/rclpy/_rclpy_pybind11.so) external/zig_sdk/tools/x86_64-linux-gnu.2.34/c++ -shared -o bazel-out/k8-fastbuild-ST-35841e508e03/bin/external/ros2_rclpy/rclpy/rclpy/_rclpy_pybind11.so ... (remaining 59 arguments skipped)

Use --sandbox_debug to see verbose messages from the sandbox and retain the sandbox build root for debugging
ld.lld: error: unable to find library -latomic
Target //src:ex failed to build
Use --verbose_failures to see the command lines of failed build steps.
INFO: Elapsed time: 0.504s, Critical Path: 0.30s
INFO: 3 processes: 3 internal.
FAILED: Build did NOT complete successfully
ERROR: Build failed. Not running target
```
