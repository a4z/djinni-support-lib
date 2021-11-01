load("@rules_cc//cc:defs.bzl", "cc_library", "objc_library")

cc_library(
    name = "djinni-base",
    srcs = [
        "djinni/cwrapper/wrapper_marshal.cpp",
    ],
    hdrs = [
        "djinni/cwrapper/wrapper_marshal.h",
        "djinni/cwrapper/wrapper_marshal.hpp",
        "djinni/djinni_common.hpp",
        "djinni/proxy_cache_impl.hpp",
        "djinni/proxy_cache_interface.hpp",
    ],
    copts = ["--std=c++17"],
    visibility = ["//visibility:public"],
)

cc_library(
    name = "djinni-jni",
    srcs = [
        "djinni/jni/djinni_jni_main.cpp",
        "djinni/jni/djinni_support.cpp",
    ],
    hdrs = [
        "djinni/jni/Marshal.hpp",
        "djinni/jni/djinni_jni_main.hpp",
        "djinni/jni/djinni_support.hpp",
    ],
    copts = ["--std=c++17"],
    linkstatic = True,
    visibility = ["//visibility:public"],
    deps = [
        ":djinni-base",
        "@bazel_tools//tools/jdk:jni", # TODO , not needed in Android build
    ],
    alwayslink = 1,
)

objc_library(
    name = "djinni-objc",
    srcs = [
        "djinni/objc/DJICppWrapperCache+Private.h",
        "djinni/objc/DJIError.mm",
        "djinni/objc/DJIMarshal+Private.h",
        "djinni/objc/DJIObjcWrapperCache+Private.h",
        "djinni/objc/DJIProxyCaches.mm",
    ],
    hdrs = [
        "djinni/objc/DJIError.h",
    ],
    copts = [
        "-ObjC++",
    ],
    visibility = ["//visibility:public"],
    deps = [":djinni-base"],
)
