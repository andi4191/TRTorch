package(default_visibility = ["//visibility:public"])

cc_binary(
    name = "libtrtorch_plugins.so",
    srcs = [],
    deps = [
        "//core/plugins:trtorch_plugins"
    ],
    linkstatic = True,
    linkshared = True
)

cc_binary(
    name = "libtrtorchrt.so",
    srcs = [],
    linkshared = True,
    linkstatic = True,
    deps = [
        "//core/runtime:runtime",
        "//core/plugins:trtorch_plugins"
    ],
)

cc_binary(
    name = "libtrtorch.so",
    srcs = [],
    linkshared = True,
    linkstatic = True,
    deps = [
        "//cpp/api:trtorch",
    ],
)

cc_binary(
    name = "trtorch.dll",
    srcs = [],
    linkshared = True,
    linkstatic = True,
    deps = [
        "//cpp/api:trtorch",
    ],
)
