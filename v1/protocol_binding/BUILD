load("@rules_cc//cc:defs.bzl", "cc_library", "cc_test")

cc_library(
    name = "binder_lib",
    hdrs = [
        "binder.h",
    ],
    visibility = ["//visibility:public"],
    deps = [
        "//proto:cloud_event_cc_proto",
        "//third_party/statusor:statusor_lib",
        "//v1/util:binder_util_lib",
        "//v1/util:cloud_events_util_lib",
        "//v1/util:formatter_util_lib",

    ],
)

cc_library(
    name = "pubsub_binder_lib",
    srcs = [
        "pubsub_binder.cc"
    ],
    hdrs = [
        "pubsub_binder.h",
    ],
    visibility = ["//visibility:public"],
    deps = [
        "//proto:cloud_event_cc_proto",
        "//proto:pubsub_cc_proto",
        "//third_party/statusor:statusor_lib",
        "//v1/util:binder_util_lib",
        "//v1/util:cloud_events_util_lib",
        ":binder_lib",
    ],
)

cc_test(
   name = "pubsub_binder_test",
   srcs = ["pubsub_binder_test.cc"],
   deps = [
       ":pubsub_binder_lib",
       "@gtest//:gtest",
       "@gtest//:gtest_main"
   ],
)

cc_library(
    name = "http_binder_lib",
    srcs = [
        "http_binder.cc"
    ],
    hdrs = [
        "http_binder.h",
    ],
    visibility = ["//visibility:public"],
    deps = [
        "@boost//:beast",
        "//proto:cloud_event_cc_proto",
        "//third_party/statusor:statusor_lib",
        "//v1/util:binder_util_lib",
        "//v1/util:cloud_events_util_lib",
        ":binder_lib",
    ],
)

cc_test(
   name = "http_binder_test",
   srcs = ["http_binder_test.cc"],
   deps = [
       ":http_binder_lib",
       "@gtest//:gtest",
       "@gtest//:gtest_main"
   ],
)

cc_test(
   name = "integration_test",
   srcs = ["integration_test.cc"],
   deps = [
       ":http_binder_lib",
       ":pubsub_binder_lib",
       "@gtest//:gtest",
       "@gtest//:gtest_main"
   ],
)
