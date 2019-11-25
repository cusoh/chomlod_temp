cmake_minimum_required(VERSION 3.4.1)


include_directories(
        ${CMAKE_CURRENT_SOURCE_DIR}/include/CHOLMOD/Core/
        ${CMAKE_CURRENT_SOURCE_DIR}/include/CHOLMOD/Include/
        ${CMAKE_CURRENT_SOURCE_DIR}/include/SuiteSparse_config/
)

## Lets build only the core for now

add_library(
        cholmod-lib

        SHARED

        include/CHOLMOD/Core/cholmod_aat.c
        include/CHOLMOD/Core/cholmod_add.c
        include/CHOLMOD/Core/cholmod_band.c
        include/CHOLMOD/Core/cholmod_change_factor.c
        include/CHOLMOD/Core/cholmod_common.c
        include/CHOLMOD/Core/cholmod_complex.c
        include/CHOLMOD/Core/cholmod_copy.c
        include/CHOLMOD/Core/cholmod_dense.c
        include/CHOLMOD/Core/cholmod_error.c
        include/CHOLMOD/Core/cholmod_factor.c
        include/CHOLMOD/Core/cholmod_memory.c
        include/CHOLMOD/Core/cholmod_sparse.c
        include/CHOLMOD/Core/cholmod_transpose.c
        include/CHOLMOD/Core/cholmod_triplet.c
        include/CHOLMOD/Core/cholmod_version.c
        include/CHOLMOD/Core/lesser.txt
        include/CHOLMOD/Core/t_cholmod_change_factor.c
        include/CHOLMOD/Core/t_cholmod_dense.c
        include/CHOLMOD/Core/t_cholmod_transpose.c
        include/CHOLMOD/Core/t_cholmod_triplet.c

        )


add_library( # Sets the name of the library.
        native-lib

        # Sets the library as a shared library.
        SHARED

        # Provides a relative path to your source file(s).
        native-lib.cpp)


find_library( # Sets the name of the path variable.
        log-lib
        log)

target_link_libraries( # Specifies the target library.
        native-lib

        ${log-lib}
        cholmod-lib
        )