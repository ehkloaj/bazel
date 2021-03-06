load("@rules_java//java:defs.bzl", "java_library", "java_test")

package(default_visibility = ["//visibility:public"])

licenses(["notice"])  # Apache 2.0

java_test(
    name = "BranchCoverageTest",
    srcs = ["BranchCoverageTest.java"],
    deps = [
        "//third_party:guava",
        "//third_party:junit4",
        "//third_party:truth",
        "//tools/test/CoverageOutputGenerator/java/com/google/devtools/coverageoutputgenerator:BranchCoverage",
    ],
)

java_test(
    name = "LineCoverageTest",
    srcs = ["LineCoverageTest.java"],
    deps = [
        "//third_party:guava",
        "//third_party:junit4",
        "//third_party:truth",
        "//tools/test/CoverageOutputGenerator/java/com/google/devtools/coverageoutputgenerator:LineCoverage",
    ],
)

java_test(
    name = "SourceFileCoverageTest",
    srcs = ["SourceFileCoverageTest.java"],
    deps = [
        ":LcovMergerTestUtils",
        ":LineCoverageTest",
        "//third_party:guava",
        "//third_party:junit4",
        "//third_party:truth",
        "//tools/test/CoverageOutputGenerator/java/com/google/devtools/coverageoutputgenerator:LineCoverage",
        "//tools/test/CoverageOutputGenerator/java/com/google/devtools/coverageoutputgenerator:SourceFileCoverage",
    ],
)

java_test(
    name = "LcovPrinterTest",
    srcs = ["LcovPrinterTest.java"],
    tags = [
        # TODO(laszlocsomor): fix on Windows or describe why it cannot pass.
        "no_windows",
    ],
    deps = [
        ":LcovMergerTestUtils",
        "//third_party:guava",
        "//third_party:junit4",
        "//third_party:truth",
        "//tools/test/CoverageOutputGenerator/java/com/google/devtools/coverageoutputgenerator:Constants",
        "//tools/test/CoverageOutputGenerator/java/com/google/devtools/coverageoutputgenerator:Coverage",
        "//tools/test/CoverageOutputGenerator/java/com/google/devtools/coverageoutputgenerator:LcovPrinter",
        "//tools/test/CoverageOutputGenerator/java/com/google/devtools/coverageoutputgenerator:SourceFileCoverage",
    ],
)

java_test(
    name = "LcovParserTest",
    srcs = ["LcovParserTest.java"],
    deps = [
        ":LcovMergerTestUtils",
        "//third_party:guava",
        "//third_party:junit4",
        "//third_party:truth",
        "//tools/test/CoverageOutputGenerator/java/com/google/devtools/coverageoutputgenerator:Constants",
        "//tools/test/CoverageOutputGenerator/java/com/google/devtools/coverageoutputgenerator:Coverage",
        "//tools/test/CoverageOutputGenerator/java/com/google/devtools/coverageoutputgenerator:LcovParser",
        "//tools/test/CoverageOutputGenerator/java/com/google/devtools/coverageoutputgenerator:LineCoverage",
        "//tools/test/CoverageOutputGenerator/java/com/google/devtools/coverageoutputgenerator:SourceFileCoverage",
    ],
)

java_test(
    name = "GcovParserTest",
    srcs = ["GcovParserTest.java"],
    deps = [
        ":LcovMergerTestUtils",
        "//third_party:guava",
        "//third_party:junit4",
        "//third_party:truth",
        "//tools/test/CoverageOutputGenerator/java/com/google/devtools/coverageoutputgenerator:BranchCoverage",
        "//tools/test/CoverageOutputGenerator/java/com/google/devtools/coverageoutputgenerator:Constants",
        "//tools/test/CoverageOutputGenerator/java/com/google/devtools/coverageoutputgenerator:Coverage",
        "//tools/test/CoverageOutputGenerator/java/com/google/devtools/coverageoutputgenerator:GcovParser",
        "//tools/test/CoverageOutputGenerator/java/com/google/devtools/coverageoutputgenerator:LineCoverage",
        "//tools/test/CoverageOutputGenerator/java/com/google/devtools/coverageoutputgenerator:SourceFileCoverage",
    ],
)

java_test(
    name = "CoverageTest",
    srcs = ["CoverageTest.java"],
    deps = [
        ":LcovMergerTestUtils",
        "//third_party:guava",
        "//third_party:junit4",
        "//third_party:truth",
        "//tools/test/CoverageOutputGenerator/java/com/google/devtools/coverageoutputgenerator:Coverage",
        "//tools/test/CoverageOutputGenerator/java/com/google/devtools/coverageoutputgenerator:SourceFileCoverage",
    ],
)

java_test(
    name = "LcovMergerFlagsTest",
    srcs = ["LcovMergerFlagsTest.java"],
    deps = [
        "//third_party:junit4",
        "//third_party:truth",
        "//tools/test/CoverageOutputGenerator/java/com/google/devtools/coverageoutputgenerator:LcovMergerFlags",
    ],
)

java_test(
    name = "MainTest",
    srcs = ["MainTest.java"],
    deps = [
        ":LcovMergerTestUtils",
        "//third_party:junit4",
        "//third_party:truth",
        "//tools/test/CoverageOutputGenerator/java/com/google/devtools/coverageoutputgenerator:Constants",
        "//tools/test/CoverageOutputGenerator/java/com/google/devtools/coverageoutputgenerator:Coverage",
        "//tools/test/CoverageOutputGenerator/java/com/google/devtools/coverageoutputgenerator:LcovParser",
        "//tools/test/CoverageOutputGenerator/java/com/google/devtools/coverageoutputgenerator:LcovPrinter",
        "//tools/test/CoverageOutputGenerator/java/com/google/devtools/coverageoutputgenerator:MainLibrary",
    ],
)

java_library(
    name = "LcovMergerTestUtils",
    testonly = 1,
    srcs = ["LcovMergerTestUtils.java"],
    deps = [
        "//third_party:guava",
        "//third_party:truth",
        "//tools/test/CoverageOutputGenerator/java/com/google/devtools/coverageoutputgenerator:LineCoverage",
        "//tools/test/CoverageOutputGenerator/java/com/google/devtools/coverageoutputgenerator:SourceFileCoverage",
    ],
)

filegroup(
    name = "srcs",
    srcs = glob(["**"]),
    visibility = ["//visibility:public"],
)

test_suite(
    name = "windows_tests",
    tags = [
        "-no_windows",
        "-slow",
    ],
    visibility = ["//visibility:private"],
)

test_suite(
    name = "all_windows_tests",
    tests = [":windows_tests"],
    visibility = ["//tools/test:__pkg__"],
)
