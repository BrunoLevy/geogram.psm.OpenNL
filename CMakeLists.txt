cmake_minimum_required(VERSION 3.11 FATAL_ERROR)
project (OpenNL_psm
    LANGUAGES C CXX
)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

if (NOT TARGET OpenMP::OpenMP_CXX)
    find_package(OpenMP)
endif()

add_library(OpenNL_psm OpenNL_psm/OpenNL_psm.c OpenNL_psm/OpenNL_psm.h)

target_include_directories(OpenNL_psm
  PUBLIC
  ${CMAKE_CURRENT_SOURCE_DIR}
)

if(OpenMP_CXX_FOUND)
    target_link_libraries(OpenNL_psm OpenMP::OpenMP_CXX)
endif()

if (${BUILD_SHARED_LIBS})
    target_compile_definitions(OpenNL_psm PRIVATE geogram_EXPORTS) 
    message("Building OpenNL_psm as shared library." )
else()
    target_compile_definitions(OpenNL_psm PUBLIC GEO_STATIC_LIBS) 
    message("Building OpenNL_psm as static library." )
endif()

target_link_libraries(OpenNL_psm ${CMAKE_DL_LIBS})
if (UNIX)
    target_link_libraries(OpenNL_psm m)
endif ()


option(OPENNL_MAKE_EXAMPLE "" OFF)
if (${OPENNL_MAKE_EXAMPLE})
    add_executable(OpenNL_example OpenNL_example.c)
    target_include_directories(OpenNL_example PUBLIC "OpenNL_psm")
    target_link_libraries(OpenNL_example PRIVATE OpenNL_psm)
endif()