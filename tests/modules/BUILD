package(default_visibility = ["//visibility:public"])

config_setting(
    name = "use_pre_cxx11_abi",
    values = {
        "define": "abi=pre_cxx11_abi",
    },
)

filegroup(
    name = "jit_models",
    srcs = glob(["**/*.jit.pt"]),
)

test_suite(
    name = "module_tests",
    tests = [
        ":test_compiled_modules",
        ":test_modules_as_engines",
        ":test_multiple_registered_engines",
        ":test_serialization",
    ],
)

test_suite(
    name = "aarch64_module_tests",
    tests = [
        ":test_compiled_modules",
        ":test_modules_as_engines",
        ":test_multiple_registered_engines",
        ":test_serialization",
    ],
)

cc_test(
    name = "test_serialization",
    srcs = ["test_serialization.cpp"],
    data = [
        ":jit_models",
    ],
    deps = [
        ":module_test",
    ],
)

cc_test(
    name = "test_multi_gpu_serdes",
    srcs = ["test_multi_gpu_serdes.cpp"],
    data = [
        ":jit_models",
    ],
    deps = [
        ":module_test",
    ],
)

cc_test(
    name = "test_multiple_registered_engines",
    srcs = ["test_multiple_registered_engines.cpp"],
    data = [
        ":jit_models",
    ],
    deps = [
        ":module_test",
    ],
)

cc_test(
    name = "test_modules_as_engines",
    srcs = ["test_modules_as_engines.cpp"],
    data = [
        ":jit_models",
    ],
    deps = [
        ":module_test",
    ],
)

cc_test(
    name = "test_compiled_modules",
    srcs = ["test_compiled_modules.cpp"],
    data = [
        ":jit_models",
    ],
    deps = [
        ":module_test",
    ],
)

cc_library(
    name = "module_test",
    hdrs = ["module_test.h"],
    deps = [
        "//cpp/api:trtorch",
        "//tests/util",
        "@googletest//:gtest_main",
    ] + select({
        ":use_pre_cxx11_abi": ["@libtorch_pre_cxx11_abi//:libtorch"],
        "//conditions:default": ["@libtorch//:libtorch"],
    }),
)
