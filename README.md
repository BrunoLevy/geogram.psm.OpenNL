# geogram.psm.OpenNL
geogram OpenNL pluggable software module

This is OpenNL Pluggable Software Module, extracted
from GEOGRAM source tree. It contains a standalone .cpp/.h
pair that can be used in any program and that does not have
any dependency. 

# Example program using GCC
It also contain an example program that can be compiled by using:
```sh
$ g++ -O3 -fopenmp -frounding-math -ffp-contract=off --std=c++11 OpenNL_example.c OpenNL_psm/OpenNL_psm.c -o OpenNL_example -ldl -lm
```

# Example program using CMake
OpenNL_psm library can be built with its example using CMake: 
```sh
git clone https://github.com/BrunoLevy/geogram.psm.OpenNL
cd geogram.psm.OpenNL
mkdir build
cmake -DOPENNL_MAKE_EXAMPLE=ON .. 
make -j
./OpenNL_example
```

# Include OpenNL_psm in your CMake project
Add the following code to your CMakeLists.txt to use OpenNL_psm: 
```cmake 
include(FetchContent)
FetchContent_Declare(
  OpenNL_psm
  GIT_REPOSITORY https://github.com/BrunoLevy/geogram.psm.OpenNL
  GIT_TAG        main
)
FetchContent_MakeAvailable(OpenNL_psm)
```
You can now simply link your executable / library with OpenNL_psm:
```cmake
target_link_libraries(... PUBLIC OpenNL_psm)
```
Include & compilation options are automatically handled by CMake. This requires CMake 3.11 and newer. 

# Documentation
- [OpenNL tutorial](https://github.com/BrunoLevy/geogram/wiki/OpenNL)
- [OpenNL reference](https://brunolevy.github.io/geogram/nl_8h.html)





