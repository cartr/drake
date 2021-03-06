# -*- python -*-
# This file contains rules for Bazel; see drake/doc/bazel.rst.

load("//tools:cpplint.bzl", "cpplint")
load(
    "//tools:drake.bzl",
    "drake_cc_binary",
    "drake_cc_library",
)

package(
    default_visibility = ["//drake/examples/kuka_iiwa_arm/dev/monolithic_pick_and_place:__subpackages__"],
)

drake_cc_library(
    name = "iiwa_state_feedback_plan",
    srcs = [
        "iiwa_state_feedback_plan.cc",
    ],
    hdrs = [
        "iiwa_state_feedback_plan.h",
    ],
    deps = [
        "//drake/examples/kuka_iiwa_arm:iiwa_lcm",
        "//drake/lcmtypes:iiwa",
        "//drake/multibody:rigid_body_tree",
        "//drake/multibody/parsers",
        "//drake/util:lcm_util",
        "@robotlocomotion_lcmtypes//:lib",
    ],
)

drake_cc_library(
    name = "kuka_pick_and_place_monolithic",
    srcs = [],
    hdrs = [
        "demo_diagram_builder.h",
        "pick_and_place_common.h",
    ],
    deps = [
        "//drake/examples/kuka_iiwa_arm/iiwa_world:world_sim_tree_builder",
        "//drake/multibody:rigid_body_tree",
        "//drake/multibody/parsers",
    ],
)

drake_cc_binary(
    name = "trajectory_generator_test",
    srcs = ["trajectory_generator_test.cc"],
    deps = [
        ":iiwa_state_feedback_plan",
        ":kuka_pick_and_place_monolithic",
        "//drake/examples/kuka_iiwa_arm:iiwa_common",
        "//drake/examples/kuka_iiwa_arm:iiwa_lcm",
        "//drake/examples/kuka_iiwa_arm/iiwa_world:iiwa_wsg_diagram_factory",
        "//drake/examples/schunk_wsg:schunk_wsg_lcm",
        "//drake/lcm",
        "//drake/systems/analysis",
        "//drake/systems/framework",
        "@gflags//:gflags",
    ],
)

cpplint()
