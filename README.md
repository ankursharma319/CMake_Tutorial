# CMake Tutorial Guide

https://cmake.org/cmake/help/latest/guide/tutorial/index.html

## Typical worfklow

```bash
cmake --help

mkdir _build
cd _build
cmake ../
cmake --build .

make help
make


cmake --install
cmake --install . --prefix "/home/myuser/installdir"
```

OR 

```bash
mkdir _build
cmake -S ./ -B ./_build/
cmake --build _build/
```

Normally need to run the configure step rarely (`cmake -S ./ -B ./_build/`) and run the build step regularly (`cmake --build _build/` OR `make -C _build/`)

Install basically copies binaries, headers and libraries into appropriate place on the local computer.

## Private vs. Public vs. Interface

Relevant when adding `target_include_directories()`

- PRIVATE = private include

- PUBLIC = api

- INTERFACE = api but not internally included

A real-world example of INTERFACE. `target_include_directories(libname INTERFACE include PRIVATE include/libname)`. This means that within your library you can include files directly, but as a user of the library you have to insert libname/ first.

https://stackoverflow.com/questions/26243169/cmake-target-include-directories-meaning-of-scope

## add_* variants vs. target_* variants

- `add_compile_options` - adds compile options to all compilation happening in and under current directory.

- `target_compile_options` - adds compile options for a specific target

similar for `target_include_directories` vs. `include_directories`
