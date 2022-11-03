# Template For C++ Projects

![Build CI Test](https://github.com/tbrandenburg/CppProject/workflows/Ubuntu%20CI%20Test/badge.svg)
[![codecov](https://codecov.io/gh/tbrandenburg/CppProject/branch/master/graph/badge.svg)](https://codecov.io/gh/tbrandenburg/CppProject)

This is a template for C++ projects. What you get:

- Library, executable and test code separated in distinct folders.
- Use of modern CMake for building and compiling.
- External libraries fetched by CMake or cloned by Git.
- External libraries installed and managed by [Conan](https://conan.io/) or [VCPKG](https://github.com/microsoft/vcpkg).
- Unit testing using [Catch2](https://github.com/catchorg/Catch2)
- General purpose libraries: [JSON](https://github.com/nlohmann/json), [spdlog](https://github.com/gabime/spdlog), [cxxopts](https://github.com/jarro2783/cxxopts) and [fmt](https://github.com/fmtlib/fmt).
- Continuous integration testing with Github Actions.
- Code coverage reports, including automatic upload to [Codecov](https://codecov.io).
- Code documentation with [Doxygen](http://www.stack.nl/~dimitri/doxygen/).

## Structure

``` text
├── CMakeLists.txt
├── app
│   ├── CMakesLists.txt
│   └── main.cc
├── cmake
│   └── cmake modules
├── docs
│   ├── Doxyfile
│   └── html/
├── external
│   ├── CMakesLists.txt
│   ├── ...
├── src
│   ├── CMakesLists.txt
│   ├── my_lib.h
│   └── my_lib.cc
└── tests
    ├── CMakeLists.txt
    └── main.cc
```

Library code goes into [src/](src/), main program code in [app/](app) and tests go in [tests/](tests/).

## Software Requirements

- CMake 3.16+
- GNU Makefile
- Doxygen
- Conan or VCPKG
- MSVC 2017 (or higher), G++9 (or higher), Clang++9 (or higher)
- Code Coverage (only on GNU|Clang): lcov, gcovr

## Building

First, clone this repo and do the preliminary work:

```shell
git clone --recursive https://github.com/franneck94/CppProjectTemplate
make prepare
```

- App Executable:
The build type can be Debug/Release/MinSizeRel or RelWithDebInfo

```shell
cd build
cmake -DCMAKE_BUILD_TYPE=Release ..
cmake --build . --config Release --target main
cd bin
./main
```

- Unit testing:
The build type should be Debug for GCC/Clang and Release for MSVC (due to bug).

```shell
cd build
cmake -DCMAKE_BUILD_TYPE=Debug ..
cmake --build . --config Debug --target unit_tests
cd bin
./unit_tests
```

- Documentation

```shell
cd build
cmake -DCMAKE_BUILD_TYPE=Debug ..
cmake --build . --config Debug --target docs
```

- Code Coverage (Unix only):
The build type has to be Coverage.

```shell
cd build
cmake -DCMAKE_BUILD_TYPE=Coverage -DENABLE_CODE_COVERAGE=ON ..
cmake --build . --config Coverage --target coverage
```

For more info about CMake see [here](./CMakeGuide.md).
