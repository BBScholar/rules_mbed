# -*- python -*-

# Copyright 2018-2019 Josh Pieper, jjp@pobox.com.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

package(default_visibility = ["//visibility:public"])

load(":cc_toolchain_config.bzl", "cc_toolchain_config", "cc_toolchain_config_stm32")

cc_toolchain_suite(
    name = "toolchain",
    toolchains = {
        "k8|compiler": "cc_toolchain_linux",
        "stm32g4|compiler": "cc_toolchain_stm32g4",
        "stm32f4|compiler": "cc_toolchain_stm32f4",
        "stm32f0|compiler": "cc_toolchain_stm32f0",
    },
)

filegroup(
    name = "empty",
    srcs = [],
)

filegroup(
    name = "arm_everything",
    srcs = [
        "@com_arm_developer_gcc//:everything",
    ] + glob(["wrapper/arm-none-eabi-*"]),
)

filegroup(
    name = "clang_wrappers",
    srcs = glob(["wrapper/clang-*"]) + [
        "@org_llvm_clang//:binaries",
        "@org_llvm_clang//:clang_libs",
    ],
)

filegroup(
    name = "clang_compiler",
    srcs = [
        ":clang_wrappers",
        "@org_llvm_clang//:includes",
    ],
)

filegroup(
    name = "clang_all",
    srcs = [
        ":clang_wrappers",
        "@org_llvm_clang//:includes",
        "@org_llvm_clang//:runtime_libs",
        "@org_llvm_clang//:static_libs",
    ],
)

cc_toolchain_config(
    name = "clang-k8",
    toolchain_identifier = "clang-k8",
    cpu = "k8",
    target_cpu = "k8",
    target_system_name = "k8",
    builtin_include_directories = [
        "external/org_llvm_clang/include/",
        "external/org_llvm_clang/lib/clang/9.0.0/include/",
        "/usr/include/",
    ],
    host_compiler_prefix = "wrapper",
    host_compiler_path = "wrapper/clang-clang",
)

cc_toolchain(
    name = "cc_toolchain_linux",
    toolchain_identifier = "clang-x86_64",
    all_files = ":clang_all",
    compiler_files = ":clang_compiler",
    dwp_files = ":clang_wrappers",
    linker_files = ":clang_wrappers",
    ar_files = ":clang_wrappers",
    as_files = ":clang_wrappers",
    objcopy_files = ":clang_wrappers",
    strip_files = ":clang_wrappers",
    supports_param_files = True,
    toolchain_config = ":clang-k8",
    dynamic_runtime_lib = "@org_llvm_clang//:runtime_libs",
    static_runtime_lib = "@org_llvm_clang//:static_libs",
)

cc_toolchain_config_stm32(
    name = "gcc-stm32f0",
    cpu = "stm32f0",
    toolchain_identifier = "gcc-stm32f0",
    host_compiler_prefix = "wrapper",
    host_compiler_path = "wrapper/arm-none-eabi-g++",
    builtin_include_directories = [
        "external/com_arm_developer_gcc/arm-none-eabi/include/",
        "external/com_arm_developer_gcc/arm-none-eabi/include/sys/",
    ],
)

cc_toolchain(
    name = "cc_toolchain_stm32f0",
    all_files = ":arm_everything",
    compiler_files = ":arm_everything",
    dwp_files = ":empty",
    linker_files = ":arm_everything",
    ar_files = ":arm_everything",
    as_files = ":arm_everything",
    objcopy_files = ":empty",
    strip_files = ":empty",
    supports_param_files = 0,
    toolchain_identifier = "gcc-stm32f0",
    toolchain_config = ":gcc-stm32f0",
)

cc_toolchain_config_stm32(
    name = "gcc-stm32f4",
    cpu = "stm32f4",
    toolchain_identifier = "gcc-stm32f4",
    host_compiler_prefix = "wrapper",
    host_compiler_path = "wrapper/arm-none-eabi-g++",
    builtin_include_directories = [
        "external/com_arm_developer_gcc/arm-none-eabi/include/",
        "external/com_arm_developer_gcc/arm-none-eabi/include/sys/",
    ],
)

cc_toolchain(
    name = "cc_toolchain_stm32f4",
    all_files = ":arm_everything",
    compiler_files = ":arm_everything",
    dwp_files = ":empty",
    linker_files = ":arm_everything",
    ar_files = ":arm_everything",
    as_files = ":arm_everything",
    objcopy_files = ":empty",
    strip_files = ":empty",
    supports_param_files = 0,
    toolchain_identifier = "gcc-stm32f4",
    toolchain_config = ":gcc-stm32f4",
)

cc_toolchain_config_stm32(
    name = "gcc-stm32g4",
    cpu = "stm32g4",
    toolchain_identifier = "gcc-stm32g4",
    host_compiler_prefix = "wrapper",
    host_compiler_path = "wrapper/arm-none-eabi-g++",
    builtin_include_directories = [
        "external/com_arm_developer_gcc/arm-none-eabi/include/",
        "external/com_arm_developer_gcc/arm-none-eabi/include/sys/",
    ],
)

cc_toolchain(
    name = "cc_toolchain_stm32g4",
    all_files = ":arm_everything",
    compiler_files = ":arm_everything",
    dwp_files = ":empty",
    linker_files = ":arm_everything",
    ar_files = ":arm_everything",
    as_files = ":arm_everything",
    objcopy_files = ":empty",
    strip_files = ":empty",
    supports_param_files = 0,
    toolchain_identifier = "gcc-stm32g4",
    toolchain_config = ":gcc-stm32g4",
)
