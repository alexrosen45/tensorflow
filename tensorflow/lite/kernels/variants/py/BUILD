load("//tensorflow:strict.default.bzl", "py_strict_test")
load("//tensorflow:tensorflow.default.bzl", "pybind_extension")

pybind_extension(
    name = "register_list_ops",
    srcs = ["register_list_ops.cc"],
    visibility = ["//visibility:public"],
    deps = [
        "//tensorflow/lite:mutable_op_resolver",
        "//tensorflow/lite/kernels/variants:list_ops_lib",
        "@pybind11",
    ],
)

py_strict_test(
    name = "end_to_end_test",
    srcs = ["end_to_end_test.py"],
    tags = ["nochromiumos_arm"],
    deps = [
        ":register_list_ops",
        "//tensorflow:tensorflow_py",
        "//tensorflow/lite/python:interpreter",
        "//tensorflow/python/ops:list_ops",
        "//tensorflow/python/platform:test",
        "//tensorflow/python/types:core",
        "//testing/pybase",
        "//third_party/py/numpy",
        "@absl_py//absl/testing:parameterized",
    ],
)
