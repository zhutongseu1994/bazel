load("@rules_java//java:defs.bzl", "java_library")
load(":merge_licenses.bzl", "merge_licenses")

########################################################################
# Description:
#   Main Java code for Bazel
#
# IMPORTANT:  NOT A PUBLIC INTERFACE.
#
# DO NOT ADD A DEPENDENCY on any targets or sub-packages outside of
# __subpackages__ without first talking to Bazel maintainers.
#
# Here are two good reasons:
#
# 1.  FRAGILITY. This is not a stable API, it's an internal interface.
#     It changes from time to time, and your client *will* be broken.
#
# 2.  CORRECTNESS.  The BUILD file parser changes rapidly.  If
#     your application depends upon it, your application will start to
#     bit-rot almost immediately.
#
# There are better alternatives.  The 'bazel query' tool has
# stable command-line and programmatic interfaces that will work with any
# version of Bazel.  They are also debugged and documented, so you'll
# avoid many common traps and pitfalls when (e.g.)  computing
# dependencies.
package(
    default_visibility = ["//src:__subpackages__"],
)

# Generate list of all srcs via:
# bazel query 'filter("srcs", kind("filegroup rule", //src/main/java/com/google/devtools/build/lib/...))' | sort | sed -e "s/^/\"/" | sed -e "s/$/\",/" | fgrep -v "build/lib:srcs"
filegroup(
    name = "srcs",
    srcs = glob(["**"]) + [
        "//src/main/java/com/google/devtools/build/docgen:srcs",
        "//src/main/java/com/google/devtools/build/lib/actions:srcs",
        "//src/main/java/com/google/devtools/build/lib/analysis:srcs",
        "//src/main/java/com/google/devtools/build/lib/authandtls:srcs",
        "//src/main/java/com/google/devtools/build/lib/bazel:srcs",
        "//src/main/java/com/google/devtools/build/lib/buildeventservice/client:srcs",
        "//src/main/java/com/google/devtools/build/lib/buildeventservice:srcs",
        "//src/main/java/com/google/devtools/build/lib/buildeventstream/proto:srcs",
        "//src/main/java/com/google/devtools/build/lib/buildeventstream/transports:srcs",
        "//src/main/java/com/google/devtools/build/lib/buildeventstream:srcs",
        "//src/main/java/com/google/devtools/build/lib/causes:srcs",
        "//src/main/java/com/google/devtools/build/lib/clock:srcs",
        "//src/main/java/com/google/devtools/build/lib/cmdline:srcs",
        "//src/main/java/com/google/devtools/build/lib/collect/compacthashmap:srcs",
        "//src/main/java/com/google/devtools/build/lib/collect/compacthashset:srcs",
        "//src/main/java/com/google/devtools/build/lib/collect/nestedset:srcs",
        "//src/main/java/com/google/devtools/build/lib/collect:srcs",
        "//src/main/java/com/google/devtools/build/lib/concurrent:srcs",
        "//src/main/java/com/google/devtools/build/lib/dynamic:srcs",
        "//src/main/java/com/google/devtools/build/lib/events:srcs",
        "//src/main/java/com/google/devtools/build/lib/exec:srcs",
        "//src/main/java/com/google/devtools/build/lib/graph:srcs",
        "//src/main/java/com/google/devtools/build/lib/metrics:srcs",
        "//src/main/java/com/google/devtools/build/lib/network:srcs",
        "//src/main/java/com/google/devtools/build/lib/packages:srcs",
        "//src/main/java/com/google/devtools/build/lib/pkgcache:srcs",
        "//src/main/java/com/google/devtools/build/lib/platform:srcs",
        "//src/main/java/com/google/devtools/build/lib/profiler/callcounts:srcs",
        "//src/main/java/com/google/devtools/build/lib/profiler/memory:srcs",
        "//src/main/java/com/google/devtools/build/lib/profiler:srcs",
        "//src/main/java/com/google/devtools/build/lib/query2/common:srcs",
        "//src/main/java/com/google/devtools/build/lib/query2/compat:srcs",
        "//src/main/java/com/google/devtools/build/lib/query2/engine:srcs",
        "//src/main/java/com/google/devtools/build/lib/query2/query/aspectresolvers:srcs",
        "//src/main/java/com/google/devtools/build/lib/query2/query/output:srcs",
        "//src/main/java/com/google/devtools/build/lib/query2:srcs",
        "//src/main/java/com/google/devtools/build/lib/remote:srcs",
        "//src/main/java/com/google/devtools/build/lib/repository:srcs",
        "//src/main/java/com/google/devtools/build/lib/rules:srcs",
        "//src/main/java/com/google/devtools/build/lib/sandbox:srcs",
        "//src/main/java/com/google/devtools/build/lib/shell:srcs",
        "//src/main/java/com/google/devtools/build/lib/skyframe:srcs",
        "//src/main/java/com/google/devtools/build/lib/skylarkbuildapi:srcs",
        "//src/main/java/com/google/devtools/build/lib/skylarkdebug/module:srcs",
        "//src/main/java/com/google/devtools/build/lib/skylarkdebug/proto:srcs",
        "//src/main/java/com/google/devtools/build/lib/skylarkdebug/server:srcs",
        "//src/main/java/com/google/devtools/build/lib/skylarkinterface/processor:srcs",
        "//src/main/java/com/google/devtools/build/lib/skylarkinterface:srcs",
        "//src/main/java/com/google/devtools/build/lib/ssd:srcs",
        "//src/main/java/com/google/devtools/build/lib/standalone:srcs",
        "//src/main/java/com/google/devtools/build/lib/supplier:srcs",
        "//src/main/java/com/google/devtools/build/lib/syntax:srcs",
        "//src/main/java/com/google/devtools/build/lib/unix:srcs",
        "//src/main/java/com/google/devtools/build/lib/unsafe:srcs",
        "//src/main/java/com/google/devtools/build/lib/util:srcs",
        "//src/main/java/com/google/devtools/build/lib/versioning:srcs",
        "//src/main/java/com/google/devtools/build/lib/vfs/inmemoryfs:srcs",
        "//src/main/java/com/google/devtools/build/lib/vfs:srcs",
        "//src/main/java/com/google/devtools/build/lib/windows/jni:srcs",
        "//src/main/java/com/google/devtools/build/lib/windows:srcs",
        "//src/main/java/com/google/devtools/build/lib/worker:srcs",
        "//src/main/java/com/google/devtools/build/skyframe:srcs",
        "//src/main/java/com/google/devtools/common/options:srcs",
    ],
    visibility = [
        "//src:__pkg__",
        "//src/test/shell/bazel:__pkg__",
    ],
)

########################################################################
#
# The "foundation" library (concurrent, events, util, vfs, inmemoryfs, options)
# Filesystem abstraction, event reporting, options parsing, I/O routines.
#

# These packages apparently depend on :foundation. I have no idea why, but to
# avoid breaking them, I allow them to depend on it.
java_library(
    name = "foundation",
    exports = [
        "//src/main/java/com/google/devtools/build/lib/concurrent",
        "//src/main/java/com/google/devtools/build/lib/events",
        "//src/main/java/com/google/devtools/build/lib/util",
        "//src/main/java/com/google/devtools/build/lib/vfs",
        "//src/main/java/com/google/devtools/common/options",
    ],
)

# Starlark language for configuration files.
#
# IMPORTANT:  NOT A PUBLIC INTERFACE. TARGETS SHOULDN'T DEPEND ON THIS.
#
java_library(
    name = "skylark-lang",
    visibility = ["//visibility:public"],
    exports = [
        "//src/main/java/com/google/devtools/build/lib/events",
        "//src/main/java/com/google/devtools/build/lib/syntax:evaluator",
        "//src/main/java/com/google/devtools/build/lib/syntax:frontend",
        "//src/main/java/com/google/devtools/build/lib/vfs",
        "//src/main/java/com/google/devtools/build/lib/vfs:pathfragment",
        "//src/main/java/com/google/devtools/build/lib/vfs/inmemoryfs",
    ],
)

java_library(
    name = "syntax",
    srcs = [],
    visibility = ["//visibility:public"],
    exports = [
        "//src/main/java/com/google/devtools/build/lib/syntax:evaluator",
        "//src/main/java/com/google/devtools/build/lib/syntax:frontend",
    ],
)

# Deprecated: This target has been moved. Depend on the actual target instead.
java_library(
    name = "transitive-info-provider",
    exports = ["//src/main/java/com/google/devtools/build/lib/analysis:transitive_info_provider"],
)

# Deprecated: This target has been moved. Depend on the actual target instead.
java_library(
    name = "config-matching-provider",
    exports = ["//src/main/java/com/google/devtools/build/lib/analysis:config/config_matching_provider"],
)

# Deprecated: This target has been moved. Depend on the actual target instead.
java_library(
    name = "provider-collection",
    exports = [
        "//src/main/java/com/google/devtools/build/lib/analysis:provider_collection",
    ],
)

# Deprecated: This target has been moved. Depend on the actual target instead.
java_library(
    name = "build-configuration-option-details",
    visibility = [
        "//src/main/java/com/google/devtools/build/lib/rules/config:__pkg__",
    ],
    exports = [
        "//src/main/java/com/google/devtools/build/lib/analysis:config/build_configuration_option_details",
    ],
)

# Deprecated: This target has been split. Depend on the sub-targets instead.
java_library(
    name = "build-base",
    exports = [
        ":runtime/blaze_server_startup_options",
        ":runtime/build_event_streamer_utils",
        "//src/main/java/com/google/devtools/build/lib/analysis:legacy_exports",
        "//src/main/java/com/google/devtools/build/lib/analysis/stringtemplate",
        "//src/main/java/com/google/devtools/build/lib/exec:legacy_exports",
        "//src/main/java/com/google/devtools/build/lib/repository:legacy_exports",
        "//src/main/java/com/google/devtools/build/lib/rules:legacy_exports",
        "//src/main/java/com/google/devtools/build/lib/skyframe:legacy_exports",
    ],
)

# Rules
# Deprecated: This target has been moved. Depend on the actual target instead.
java_library(
    name = "nativedeps-rules",
    exports = [
        "//src/main/java/com/google/devtools/build/lib/rules:nativedeps",
    ],
)

# Deprecated: This target has been moved. Depend on the actual target instead.
java_library(
    name = "core-rules",
    exports = [
        "//src/main/java/com/google/devtools/build/lib/rules:core_rules",
    ],
)

# Deprecated: This target has been moved. Depend on the actual target instead.
java_library(
    name = "core-workspace-rules",
    exports = [
        "//src/main/java/com/google/devtools/build/lib/rules:core_workspace_rules",
    ],
)

# Deprecated: This target has been moved. Depend on the actual target instead.
java_library(
    name = "testing-support-rules",
    exports = [
        "//src/main/java/com/google/devtools/build/lib/rules:test_rules",
    ],
)

java_library(
    name = "shared-base-rules",
    exports = [
        ":nativedeps-rules",
        "//src/main/java/com/google/devtools/build/lib/rules/android",
        "//src/main/java/com/google/devtools/build/lib/rules/java:java-compilation",
        "//src/main/java/com/google/devtools/build/lib/rules/java:java-rules",
        "//src/main/java/com/google/devtools/build/lib/rules/proto",
        "//src/main/java/com/google/devtools/build/lib/rules/python",
    ],
)

java_library(
    name = "build-request-options",
    srcs = ["buildtool/BuildRequestOptions.java"],
    deps = [
        "//src/main/java/com/google/devtools/build/lib/actions:localhost_capacity",
        "//src/main/java/com/google/devtools/build/lib/util",
        "//src/main/java/com/google/devtools/build/lib/util:resource_converter",
        "//src/main/java/com/google/devtools/build/lib/vfs:pathfragment",
        "//src/main/java/com/google/devtools/common/options",
        "//third_party:flogger",
        "//third_party:guava",
        "//third_party:jsr305",
    ],
)

java_library(
    name = "runtime/blaze_server_startup_options",
    srcs = ["runtime/BlazeServerStartupOptions.java"],
    deps = [
        "//src/main/java/com/google/devtools/build/lib/util",
        "//src/main/java/com/google/devtools/build/lib/vfs",
        "//src/main/java/com/google/devtools/build/lib/vfs:pathfragment",
        "//src/main/java/com/google/devtools/common/options",
        "//third_party:guava",
    ],
)

java_library(
    name = "keep-going-option",
    srcs = ["runtime/KeepGoingOption.java"],
    deps = ["//src/main/java/com/google/devtools/common/options"],
)

java_library(
    name = "loading-phase-threads-option",
    srcs = ["runtime/LoadingPhaseThreadsOption.java"],
    deps = [
        "//src/main/java/com/google/devtools/build/lib/actions:localhost_capacity",
        "//src/main/java/com/google/devtools/build/lib/util:resource_converter",
        "//src/main/java/com/google/devtools/common/options",
        "//third_party:flogger",
    ],
)

java_library(
    name = "server",
    srcs = [
        "server/CommandManager.java",
        "server/GrpcServerImpl.java",
        "server/IdleServerTasks.java",
        "server/ServerWatcherRunnable.java",
    ],
    deps = [
        ":bug-report",
        ":runtime",
        "//src/main/java/com/google/devtools/build/lib/clock",
        "//src/main/java/com/google/devtools/build/lib/profiler",
        "//src/main/java/com/google/devtools/build/lib/profiler:google-auto-profiler-utils",
        "//src/main/java/com/google/devtools/build/lib/unix",
        "//src/main/java/com/google/devtools/build/lib/util",
        "//src/main/java/com/google/devtools/build/lib/util:exit_code",
        "//src/main/java/com/google/devtools/build/lib/util:os",
        "//src/main/java/com/google/devtools/build/lib/util:string",
        "//src/main/java/com/google/devtools/build/lib/util/io:out-err",
        "//src/main/java/com/google/devtools/build/lib/vfs",
        "//src/main/java/com/google/devtools/common/options",
        "//src/main/java/com/google/devtools/common/options:invocation_policy",
        "//src/main/protobuf:command_server_java_grpc",
        "//src/main/protobuf:command_server_java_proto",
        "//src/main/protobuf:failure_details_java_proto",
        "//src/main/protobuf:invocation_policy_java_proto",
        "//third_party:flogger",
        "//third_party:guava",
        "//third_party:jsr305",
        "//third_party/grpc:grpc-jar",
        "//third_party/protobuf:protobuf_java",
    ],
)

java_library(
    name = "bug-report",
    srcs = glob(["bugreport/*.java"]),
    deps = [
        "//src/main/java/com/google/devtools/build/lib/analysis:blaze_version_info",
        "//src/main/java/com/google/devtools/build/lib/util:crash_failure_details",
        "//src/main/java/com/google/devtools/build/lib/util:custom_exit_code_publisher",
        "//src/main/java/com/google/devtools/build/lib/util:custom_failure_detail_publisher",
        "//src/main/java/com/google/devtools/build/lib/util:detailed_exit_code",
        "//src/main/java/com/google/devtools/build/lib/util:exit_code",
        "//src/main/java/com/google/devtools/build/lib/util:logging",
        "//src/main/java/com/google/devtools/build/lib/util/io:out-err",
        "//third_party:flogger",
        "//third_party:guava",
        "//third_party:jsr305",
    ],
)

java_library(
    name = "runtime/build_event_streamer_utils",
    srcs = ["runtime/BuildEventStreamerUtils.java"],
    deps = [
        "//src/main/java/com/google/devtools/build/lib/buildeventstream/proto:build_event_stream_java_proto",
        "//src/main/protobuf:test_status_java_proto",
    ],
)

java_library(
    name = "runtime",
    srcs = glob(
        [
            "runtime/*.java",
            "runtime/commands/*.java",
            "runtime/mobileinstall/*.java",
            "buildtool/*.java",
            "buildtool/buildevent/*.java",
        ],
        exclude = [
            "buildtool/BuildRequestOptions.java",
            "runtime/KeepGoingOption.java",
            "runtime/LoadingPhaseThreadsOption.java",
        ],
    ) + [
        "server/RPCServer.java",
        "server/signal/InterruptSignalHandler.java",
    ],
    resources = glob([
        "runtime/commands/*.txt",
        "runtime/mobileinstall/*.txt",
    ]),
    deps = [
        ":bug-report",
        ":build-base",
        ":build-request-options",
        ":keep-going-option",
        ":loading-phase-threads-option",
        ":shared-base-rules",
        "//src/main/java/com/google/devtools/build/lib/actions",
        "//src/main/java/com/google/devtools/build/lib/actions:localhost_capacity",
        "//src/main/java/com/google/devtools/build/lib/bazel/repository/downloader",
        "//src/main/java/com/google/devtools/build/lib/buildeventstream",
        "//src/main/java/com/google/devtools/build/lib/buildeventstream/proto:build_event_stream_java_proto",
        "//src/main/java/com/google/devtools/build/lib/buildeventstream/transports",
        "//src/main/java/com/google/devtools/build/lib/clock",
        "//src/main/java/com/google/devtools/build/lib/cmdline",
        "//src/main/java/com/google/devtools/build/lib/collect",
        "//src/main/java/com/google/devtools/build/lib/collect/nestedset",
        "//src/main/java/com/google/devtools/build/lib/concurrent",
        "//src/main/java/com/google/devtools/build/lib/events",
        "//src/main/java/com/google/devtools/build/lib/exec/local:options",
        "//src/main/java/com/google/devtools/build/lib/metrics:event",
        "//src/main/java/com/google/devtools/build/lib/packages",
        "//src/main/java/com/google/devtools/build/lib/packages:build_type",
        "//src/main/java/com/google/devtools/build/lib/packages:starlark_semantics_options",
        "//src/main/java/com/google/devtools/build/lib/packages:type",
        "//src/main/java/com/google/devtools/build/lib/pkgcache",
        "//src/main/java/com/google/devtools/build/lib/platform:suspend_counter",
        "//src/main/java/com/google/devtools/build/lib/profiler",
        "//src/main/java/com/google/devtools/build/lib/profiler:google-auto-profiler-utils",
        "//src/main/java/com/google/devtools/build/lib/profiler:profiler-output",
        "//src/main/java/com/google/devtools/build/lib/profiler/memory:allocationtracker",
        "//src/main/java/com/google/devtools/build/lib/query2",
        "//src/main/java/com/google/devtools/build/lib/query2/common:abstract-blaze-query-env",
        "//src/main/java/com/google/devtools/build/lib/query2/engine",
        "//src/main/java/com/google/devtools/build/lib/query2/query/output",
        "//src/main/java/com/google/devtools/build/lib/shell",
        "//src/main/java/com/google/devtools/build/lib/syntax:evaluator",
        "//src/main/java/com/google/devtools/build/lib/syntax:frontend",
        "//src/main/java/com/google/devtools/build/lib/unix",
        "//src/main/java/com/google/devtools/build/lib/util",
        "//src/main/java/com/google/devtools/build/lib/util:abrupt_exit_exception",
        "//src/main/java/com/google/devtools/build/lib/util:command",
        "//src/main/java/com/google/devtools/build/lib/util:crash_failure_details",
        "//src/main/java/com/google/devtools/build/lib/util:custom_exit_code_publisher",
        "//src/main/java/com/google/devtools/build/lib/util:custom_failure_detail_publisher",
        "//src/main/java/com/google/devtools/build/lib/util:debug-logger-configurator",
        "//src/main/java/com/google/devtools/build/lib/util:detailed_exit_code",
        "//src/main/java/com/google/devtools/build/lib/util:exit_code",
        "//src/main/java/com/google/devtools/build/lib/util:filetype",
        "//src/main/java/com/google/devtools/build/lib/util:os",
        "//src/main/java/com/google/devtools/build/lib/util:process",
        "//src/main/java/com/google/devtools/build/lib/util:shell_escaper",
        "//src/main/java/com/google/devtools/build/lib/util:string",
        "//src/main/java/com/google/devtools/build/lib/util/io",
        "//src/main/java/com/google/devtools/build/lib/util/io:out-err",
        "//src/main/java/com/google/devtools/build/lib/vfs",
        "//src/main/java/com/google/devtools/build/lib/vfs:output_service",
        "//src/main/java/com/google/devtools/build/lib/vfs:pathfragment",
        "//src/main/java/com/google/devtools/build/lib/windows",
        "//src/main/java/com/google/devtools/build/skyframe",
        "//src/main/java/com/google/devtools/build/skyframe:skyframe-objects",
        "//src/main/java/com/google/devtools/common/options",
        "//src/main/java/com/google/devtools/common/options:invocation_policy",
        "//src/main/protobuf:action_cache_java_proto",
        "//src/main/protobuf:analysis_java_proto",
        "//src/main/protobuf:bazel_flags_java_proto",
        "//src/main/protobuf:build_java_proto",
        "//src/main/protobuf:command_line_java_proto",
        "//src/main/protobuf:command_server_java_proto",
        "//src/main/protobuf:extra_actions_base_java_proto",
        "//src/main/protobuf:failure_details_java_proto",
        "//src/main/protobuf:invocation_policy_java_proto",
        "//src/main/protobuf:option_filters_java_proto",
        "//src/main/protobuf:test_status_java_proto",
        "//third_party:auto_value",
        "//third_party:flogger",
        "//third_party:gson",
        "//third_party:guava",
        "//third_party:jsr305",
        "//third_party/protobuf:protobuf_java",
    ],
)

merge_licenses(
    name = "merge_licenses",
    srcs = [
        "//:LICENSE",
        "//third_party:srcs",
    ],
    out = "runtime/commands/LICENSE",
)

java_library(
    name = "all-build-rules",
    exports = [
        "//src/main/java/com/google/devtools/build/lib/actions",
        "//src/main/java/com/google/devtools/build/lib/analysis:legacy_exports",
        "//src/main/java/com/google/devtools/build/lib/concurrent",
        "//src/main/java/com/google/devtools/build/lib/graph",
        "//src/main/java/com/google/devtools/build/lib/rules:legacy_exports",
        "//src/main/java/com/google/devtools/build/lib/rules/objc",
        "//src/main/java/com/google/devtools/build/lib/util",
        "//src/main/java/com/google/devtools/build/lib/vfs",
        "//src/main/java/com/google/devtools/common/options",
        "//third_party:guava",
    ],
)

# Deprecated: This target has been deprecated. Please depend on the correct exported library instead.
java_library(
    name = "build",
    exports = [
        ":all-build-rules",
        ":build-base",
        ":foundation",
        ":query2",
        "//src/main/java/com/google/devtools/build/lib/actions",
        "//src/main/java/com/google/devtools/build/lib/packages",
    ],
)

########################################################################
#
# The Blaze query language, revision 2: query2.
#

java_library(
    name = "query2",
    exports = [
        ":foundation",
        "//src/main/java/com/google/devtools/build/lib/concurrent",
        "//src/main/java/com/google/devtools/build/lib/events",
        "//src/main/java/com/google/devtools/build/lib/graph",
        "//src/main/java/com/google/devtools/build/lib/packages",
        "//src/main/java/com/google/devtools/build/lib/query2",
        "//src/main/java/com/google/devtools/build/lib/util",
        "//src/main/java/com/google/devtools/build/lib/vfs",
        "//src/main/java/com/google/devtools/common/options",
        "//src/main/protobuf:build_java_proto",
        "//third_party:guava",
    ],
)

########################################################################
#
# Documentation generation
#

filegroup(
    name = "generated_docs",
    srcs = [
        "//src/main/java/com/google/devtools/build/lib:gen_buildencyclopedia",
        "//src/main/java/com/google/devtools/build/lib:gen_command-line-reference",
        "//src/main/java/com/google/devtools/build/lib:gen_skylarklibrary",
    ],
    visibility = ["//src/test/shell/bazel:__pkg__"],
)

filegroup(
    name = "docs_embedded_in_sources",
    srcs = glob(["**/*.java"]) + [
        "//src/main/java/com/google/devtools/build/lib/analysis:srcs",
        "//src/main/java/com/google/devtools/build/lib/exec:srcs",
        "//src/main/java/com/google/devtools/build/lib/repository:srcs",
        "//src/main/java/com/google/devtools/build/lib/rules:srcs",
        "//src/main/java/com/google/devtools/build/lib/bazel/rules:srcs",
    ],
)

genrule(
    name = "gen_buildencyclopedia",
    srcs = [":docs_embedded_in_sources"],
    outs = ["build-encyclopedia.zip"],
    cmd = (
        "mkdir -p $(@D)/be && " +
        "$(location //src/main/java/com/google/devtools/build/docgen:docgen_bin)" +
        " --product_name=bazel" +
        " --provider=com.google.devtools.build.lib.bazel.rules.BazelRuleClassProvider" +
        " --input_dir=$$PWD/src/main/java/com/google/devtools/build/lib" +
        " --output_dir=$(@D)/be &&" +
        "zip -qj $@ $(@D)/be/*"
    ),
    tools = [
        "//src/main/java/com/google/devtools/build/docgen:docgen_bin",
        "//src/main/java/com/google/devtools/build/docgen:docgen_javalib",
    ],
    visibility = ["//site:__pkg__"],
)

genrule(
    name = "gen_command-line-reference",
    srcs = [
        "//site:command-line-reference-prefix.html",
        "//site:command-line-reference-suffix.html",
    ],
    outs = ["command-line-reference.html"],
    cmd = (
        "cat $(location //site:command-line-reference-prefix.html) > $@ && " +
        "TMP=`mktemp -d /tmp/tmp.XXXXXXXXXX` && " +
        # TODO(#11179): Remove when the stub template fix is released.
        "export JARBIN=$(JAVABASE)/bin/jar && " +
        "$(location //src/main/java/com/google/devtools/build/lib/bazel:BazelServer) " +
        "--jvm_flag=-Dio.bazel.EnableJni=0 --batch " +
        "--install_base=$${TMP} --output_base=$${TMP}/output/ --output_user_root=$${TMP} " +
        "--failure_detail_out=$${TMP}/output/failure_detail.rawproto " +
        "help everything-as-html >> $@ 2>/dev/null && " +
        "cat $(location //site:command-line-reference-suffix.html) >> $@"
    ),
    toolchains = ["@bazel_tools//tools/jdk:current_host_java_runtime"],
    tools = [
        "//src/main/java/com/google/devtools/build/lib/bazel:BazelServer",
    ],
    visibility = ["//site:__pkg__"],
)

genrule(
    name = "gen_skylarklibrary",
    outs = ["skylark-library.zip"],
    cmd = "mkdir -p $(@D)/skylark-lib &&" +
          "$(location //src/main/java/com/google/devtools/build/docgen:skydoc_bin) $(@D)/skylark-lib" +
          " && zip -qj $@ $(@D)/skylark-lib/*",
    tools = ["//src/main/java/com/google/devtools/build/docgen:skydoc_bin"],
    visibility = ["//site:__pkg__"],
)

########################################################################
#
# Miscellaneous targets
#

# A library for just the BuildInfo class, so it can be used by the external
# SingleJar implementation.

# Deprecated: This target has been moved. Depend on the actual target instead.
java_library(
    name = "build-info",
    exports = [
        "//src/main/java/com/google/devtools/build/lib/analysis:build_info",
    ],
)

# Deprecated: This target has been moved. Depend on the actual target instead.
java_library(
    name = "blaze-version-info",
    exports = [
        "//src/main/java/com/google/devtools/build/lib/analysis:blaze_version_info",
    ],
)

# Deprecated: This target has been moved. Depend on the actual target instead.
java_library(
    name = "rule-definition-context",
    exports = [
        "//src/main/java/com/google/devtools/build/lib/analysis:rule_definition_context",
    ],
)

# TODO(b/144899336): This belongs in skyframe/BUILD once it exists.
# Deprecated: This target has been moved. Depend on the actual target instead.
java_library(
    name = "sane_analysis_exception",
    exports = [
        "//src/main/java/com/google/devtools/build/lib/skyframe:sane_analysis_exception",
    ],
)
