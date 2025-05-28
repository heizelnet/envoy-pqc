licenses(["notice"])  # Apache 2

cc_library(
    name = "crypto",
    srcs = [
        "crypto/libcrypto.so",
    ],
    hdrs = glob(["/include/openssl/*.h"]),
    defines = ["BORINGSSL_FIPS"],
    includes = ["include"],
    visibility = ["//visibility:public"],
)

cc_library(
    name = "ssl",
    srcs = [
        "ssl/libssl.so",
    ],
    hdrs = glob(["/include/openssl/*.h"]),
    includes = ["include"],
    visibility = ["//visibility:public"],
    deps = [":crypto"],
)

genrule(
    name = "build",
    srcs = glob(["**"]),
    outs = [
        "crypto/libcrypto.so",
        "ssl/libssl.so",
    ],
    cmd = "$(location {}) $(location crypto/libcrypto.so) $(location ssl/libssl.so)".format("@envoy//bazel/external:boringssl_fips.genrule_cmd"),
    tools = ["@envoy//bazel/external:boringssl_fips.genrule_cmd"],
)
