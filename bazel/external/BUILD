licenses(["notice"])  # Apache 2

exports_files([
    "boringssl_nonfips.genrule_cmd",  # non-FIPS 빌드 스크립트
    "boringssl_fips.genrule_cmd",     # FIPS 빌드 스크립트도 함께 export
])

# Use a wrapper cc_library with an empty source source file to force
# compilation of other cc_library targets that only list *.a sources.
cc_library(
    name = "all_external",
    srcs = [":empty.cc"],
    tags = ["skip_on_windows"],
    deps = [
        "@com_github_datadog_dd_trace_cpp//:dd_trace_cpp",
        "@com_google_googletest//:gtest",
    ],
)

genrule(
    name = "empty_cc",
    outs = ["empty.cc"],
    cmd = "touch \"$(@D)/empty.cc\"",
    visibility = ["//visibility:public"],
)
