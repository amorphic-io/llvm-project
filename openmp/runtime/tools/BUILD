load("@rules_python//python:py_binary.bzl", "py_binary")

py_binary(
  name = "message_converter",
  main = "message-converter.py",
  srcs = [
      "message-converter.py",
      "libomputils.py",
  ],
  imports = ["."],
  visibility = ["//openmp:__subpackages__"]
)
