# Copyright 2016 Alexander Lamaison. All rights reserved.
# Copyright 2025 ???
#
# This file is a part of the Windows Template Library.
# The use and distribution terms for this software are covered by the
# Common Public License 1.0 (http://opensource.org/licenses/cpl.php)
# which can be found in the file CPL.TXT at the root of this distribution.
# By using this software in any fashion, you are agreeing to be bound by
# the terms of this license. You must not remove this notice, or
# any other, from this software.


cmake_minimum_required(VERSION 3.20)
project(WTL VERSION 10.0)

add_subdirectory(wtl)

# Install

## During package installation, install WTLConfig.cmake
install(EXPORT WTLConfig NAMESPACE WTL:: DESTINATION lib/cmake/WTL)

## Directly from build tree
# create WTLConfig.cmake
export(TARGETS WTL NAMESPACE WTL:: FILE WTLConfig.cmake)
export(PACKAGE WTL) # register it

## Versioning

include(CMakePackageConfigHelpers)
write_basic_package_version_file(
        ${CMAKE_CURRENT_BINARY_DIR}/WTLConfigVersion.cmake
        VERSION "${PROJECT_VERSION_MAJOR}.${PROJECT_VERSION_MINOR}.${PROJECT_VERSION_PATCH}"
        COMPATIBILITY SameMajorVersion)
install(
        FILES ${CMAKE_CURRENT_BINARY_DIR}/WTLConfigVersion.cmake
        DESTINATION lib/cmake/WTL)