# Description

This repository contains a patched version of ASCO optimizer for usage with Qucs-S. See https://asco.sourceforge.net/ for more info

The difference from the default ASCO version:

* Added `-simulator-path` CLI option to specify exact simulator executable location and not rely on `$PATH`
* Added `ASCO_SIM_PATH` environment variable. Set this variable to specify the path to simulator executable used by ASCO

The use case of these features may be to handle multiple simulator installations and rename simulator executable. 

# Installation

Use CMake to build this version of ASCO. It doesn't require an extra dependencies except GCC compiler and GLIBC libraries.
Define `CMAKE_INSTALL_PREFIX` for the installation directory and `CMAKE_BUILD_TYPE` for Debug/Release build type. 

