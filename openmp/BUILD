load("@bazel_skylib//rules:expand_template.bzl", "expand_template")

LIBOMP_VERSION_MAJOR = "5"
LIBOMP_VERSION_MINOR = "0"
LIBOMP_VERSION_PATCH = "20140926"

expand_template(
    name = "omp_header_gen",
    out = "runtime/src/include/omp.h",
    substitutions = {
        "@LIBOMP_VERSION_MAJOR@": LIBOMP_VERSION_MAJOR,
        "@LIBOMP_VERSION_MINOR@": LIBOMP_VERSION_MINOR,
        "@LIBOMP_VERSION_PATCH@": LIBOMP_VERSION_PATCH,
    },
    template = "runtime/src/include/omp.h.var",
)

expand_template(
    name = "kmp_config_header_gen",
    out = "runtime/src/kmp_config.h",
    substitutions = {
        "#cmakedefine01 DEBUG_BUILD": "#define DEBUG_BUILD 0",
        "#cmakedefine01 RELWITHDEBINFO_BUILD": "#define RELWITHDEBINFO_BUILD 0",
        "#cmakedefine01 LIBOMP_USE_ITT_NOTIFY": "#define LIBOMP_USE_ITT_NOTIFY 0",
        "#cmakedefine01 LIBOMP_USE_VERSION_SYMBOLS": "#define LIBOMP_USE_VERSION_SYMBOLS 1",
        "#cmakedefine01 LIBOMP_HAVE_WEAK_ATTRIBUTE": "#define LIBOMP_HAVE_WEAK_ATTRIBUTE 1",
        "#cmakedefine01 LIBOMP_HAVE_PSAPI": "#define LIBOMP_HAVE_PSAPI 0",
        "#cmakedefine01 LIBOMP_STATS": "#define LIBOMP_STATS 0",
        "#cmakedefine01 LIBOMP_HAVE_X86INTRIN_H": "#define LIBOMP_HAVE_X86INTRIN_H 0",
        "#cmakedefine01 LIBOMP_HAVE___BUILTIN_READCYCLECOUNTER": "#define LIBOMP_HAVE___BUILTIN_READCYCLECOUNTER 0",
        "#cmakedefine01 LIBOMP_HAVE___RDTSC": "#define LIBOMP_HAVE___RDTSC 0",
        "#cmakedefine01 LIBOMP_USE_DEBUGGER": "#define LIBOMP_USE_DEBUGGER 0",
        "#cmakedefine01 LIBOMP_OMPT_DEBUG": "#define LIBOMP_OMPT_DEBUG 0",
        "#cmakedefine01 LIBOMP_OMPT_SUPPORT": "#define LIBOMP_OMPT_SUPPORT 0",
        "#cmakedefine01 LIBOMP_OMPD_SUPPORT": "#define LIBOMP_OMPD_SUPPORT 0",
        "#cmakedefine01 LIBOMP_OMPX_TASKGRAPH": "#define LIBOMP_OMPX_TASKGRAPH 0",
        "#cmakedefine01 LIBOMP_PROFILING_SUPPORT": "#define LIBOMP_PROFILING_SUPPORT 0",
        "#cmakedefine01 LIBOMP_OMPT_OPTIONAL": "#define LIBOMP_OMPT_OPTIONAL 1",
        "#cmakedefine01 LIBOMP_USE_ADAPTIVE_LOCKS": "#define LIBOMP_USE_ADAPTIVE_LOCKS 0",
        "#cmakedefine01 LIBOMP_USE_INTERNODE_ALIGNMENT": "#define LIBOMP_USE_INTERNODE_ALIGNMENT 0",
        "#cmakedefine01 LIBOMP_ENABLE_ASSERTIONS": "#define LIBOMP_ENABLE_ASSERTIONS 1",
        "#cmakedefine01 LIBOMP_USE_HIER_SCHED": "#define LIBOMP_USE_HIER_SCHED 0",
        "#cmakedefine01 STUBS_LIBRARY": "#define STUBS_LIBRARY 0",
        "#cmakedefine01 LIBOMP_USE_HWLOC": "#define LIBOMP_USE_HWLOC 0",
        "#cmakedefine01 LIBOMP_ENABLE_SHARED": "#define LIBOMP_ENABLE_SHARED 1",
        "#cmakedefine01 MSVC": "#define MSVC 0",
        "#cmakedefine01 LIBOMP_HAVE_WAITPKG_INTRINSICS": "#define LIBOMP_HAVE_WAITPKG_INTRINSICS 1",
        "#cmakedefine01 LIBOMP_HAVE_RTM_INTRINSICS": "#define LIBOMP_HAVE_RTM_INTRINSICS 1",
        "#cmakedefine01 LIBOMP_HAVE_IMMINTRIN_H": "#define LIBOMP_HAVE_IMMINTRIN_H 1",
        "#cmakedefine01 LIBOMP_HAVE_INTRIN_H": "#define LIBOMP_HAVE_INTRIN_H 0",
        "#cmakedefine01 LIBOMP_HAVE_ATTRIBUTE_WAITPKG": "#define LIBOMP_HAVE_ATTRIBUTE_WAITPKG 1",
        "#cmakedefine01 LIBOMP_HAVE_ATTRIBUTE_RTM": "#define LIBOMP_HAVE_ATTRIBUTE_RTM 1",
        "#cmakedefine01 LIBOMP_ARCH_AARCH64_A64FX": "#define LIBOMP_ARCH_AARCH64_A64FX 0",
        "#cmakedefine01 LIBOMP_HAVE_XMMINTRIN_H": "#define LIBOMP_HAVE_XMMINTRIN_H 1",
        "#cmakedefine01 LIBOMP_HAVE__MM_MALLOC": "#define LIBOMP_HAVE__MM_MALLOC 1",
        "#cmakedefine01 LIBOMP_HAVE_ALIGNED_ALLOC": "#define LIBOMP_HAVE_ALIGNED_ALLOC 1",
        "#cmakedefine01 LIBOMP_HAVE_POSIX_MEMALIGN": "#define LIBOMP_HAVE_POSIX_MEMALIGN 1",
        "#cmakedefine01 LIBOMP_HAVE__ALIGNED_MALLOC": "#define LIBOMP_HAVE__ALIGNED_MALLOC 0",
        "#cmakedefine01 OPENMP_ENABLE_LIBOMPTARGET": "#define OPENMP_ENABLE_LIBOMPTARGET 1",
        "@LIBOMP_LEGAL_ARCH@":        "__unknown__",
        "@LIBOMP_LIB_FILE@":          "libomp.so",
        "@LIBOMP_VERSION_MAJOR@":     LIBOMP_VERSION_MAJOR,
        "@LIBOMP_VERSION_MINOR@":     LIBOMP_VERSION_MINOR,
    },
    template = "runtime/src/kmp_config.h.cmake",
)

genrule(
    name = "kmp_i18n_id_inc_gen",
    srcs = [
        "runtime/src/i18n/en_US.txt",
    ],
    outs = ["runtime/src/kmp_i18n_id.inc"],
    cmd = "$(location //openmp/runtime/tools:message_converter) " +
        "--enum=$@ $(SRCS)",
    tools = ["//openmp/runtime/tools:message_converter"],
)

genrule(
    name = "kmp_i18n_default_inc_gen",
    srcs = [
        "runtime/src/i18n/en_US.txt",
    ],
    outs = ["runtime/src/kmp_i18n_default.inc"],
    cmd = "$(location //openmp/runtime/tools:message_converter) " +
        "--default=$@ $(SRCS)",
    tools = ["//openmp/runtime/tools:message_converter"],
)

filegroup(
    name = "omp_version_script",
    srcs = ["runtime/src/exports_so.txt"],
)

cc_library(
    name = "openmp",
    srcs = [
        "runtime/src/kmp_alloc.cpp",
        "runtime/src/kmp_atomic.cpp",
        "runtime/src/kmp_csupport.cpp",
        "runtime/src/kmp_debug.cpp",
        "runtime/src/kmp_itt.cpp",
        "runtime/src/kmp_environment.cpp",
        "runtime/src/kmp_error.cpp",
        "runtime/src/kmp_global.cpp",
        "runtime/src/kmp_i18n.cpp",
        "runtime/src/kmp_io.cpp",
        "runtime/src/kmp_runtime.cpp",
        "runtime/src/kmp_settings.cpp",
        "runtime/src/kmp_str.cpp",
        "runtime/src/kmp_tasking.cpp",
        "runtime/src/kmp_threadprivate.cpp",
        "runtime/src/kmp_utility.cpp",
        "runtime/src/kmp_barrier.cpp",
        "runtime/src/kmp_wait_release.cpp",
        "runtime/src/kmp_affinity.cpp",
        "runtime/src/kmp_dispatch.cpp",
        "runtime/src/kmp_lock.cpp",
        "runtime/src/kmp_sched.cpp",
        "runtime/src/kmp_collapse.cpp",
        "runtime/src/z_Linux_util.cpp",
        "runtime/src/kmp_gsupport.cpp",
        "runtime/src/z_Linux_asm.S",
        "runtime/src/kmp_taskdeps.cpp",
        "runtime/src/kmp_cancel.cpp",
        "runtime/src/kmp_ftn_cdecl.cpp",
        "runtime/src/kmp_ftn_extra.cpp",
        "runtime/src/kmp_version.cpp",
    ] + [
        "runtime/src/kmp_dispatch_hier.h",
        "runtime/src/kmp_settings.h",
        "runtime/src/kmp_wrapper_malloc.h",
        "runtime/src/kmp_omp.h",
        "runtime/src/kmp_stats.h",
        "runtime/src/kmp_dispatch.h",
        "runtime/src/kmp_platform.h",
        "runtime/src/kmp_collapse.h",
        "runtime/src/kmp_affinity.h",
        "runtime/src/kmp_safe_c_api.h",
        "runtime/src/kmp_stats_timing.h",
        "runtime/src/kmp_environment.h",
        "runtime/src/kmp_io.h",
        "runtime/src/kmp_wrapper_getpid.h",
        "runtime/src/kmp_wait_release.h",
        "runtime/src/kmp_atomic.h",
        "runtime/src/kmp.h",
        "runtime/src/kmp_debugger.h",
        "runtime/src/kmp_taskdeps.h",
        "runtime/src/kmp_lock.h",
        "runtime/src/kmp_utils.h",
        "runtime/src/kmp_i18n.h",
        "runtime/src/kmp_itt.h",
        "runtime/src/kmp_debug.h",
        "runtime/src/kmp_str.h",
        "runtime/src/kmp_error.h",
        "runtime/src/kmp_os.h",
        "runtime/src/kmp_ftn_os.h",
        "runtime/src/kmp_barrier.h",
        "runtime/src/kmp_version.h",
        "runtime/src/ompt-specific.h",
        "runtime/src/kmp_ftn_entry.h",
        # Generated
        "runtime/src/kmp_config.h",
        "runtime/src/kmp_i18n_default.inc",
        "runtime/src/kmp_i18n_id.inc",
    ],
    additional_linker_inputs = [
        ":omp_version_script",
    ],
    linkopts = [
        # Tell the linker to apply the same version script CMake did:
        "-Wl,--version-script=$(location :omp_version_script)",
    ],
    hdrs = [
      "runtime/src/include/omp.h",
    ],
    includes = [
        "runtime/src/include",
        "runtime/src",
    ],
    visibility = ["//visibility:public"],
)
