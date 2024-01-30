cmake_minimum_required(VERSION 3.27)
project(libsecale VERSION 0.0.1)

# Use libc++ instead of libstdc++ (Clang only)
if (${CMAKE_CXX_COMPILER_ID} STREQUAL Clang)
    option(USE_LIBCPP "Use libc++ as C++ standard library" OFF)
    if (USE_LIBCPP)
        add_compile_options(-stdlib=libc++)
    endif ()
endif ()

# Place all output binaries into the root of the build directory
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY  ${CMAKE_CURRENT_BINARY_DIR})
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_CURRENT_BINARY_DIR})

set(BOOST_REQUIRED_VERSION 1.83)

include(GNUInstallDirs)
include(GenerateExportHeader)
include(CheckIPOSupported)
# check for LTO support in the compiler
check_ipo_supported(RESULT LTO_SUPPORTED)

add_library(
        secale
        SHARED
        src/dummy.cpp
)

enable_testing()
