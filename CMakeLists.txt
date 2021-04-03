cmake_minimum_required(VERSION 3.0)
project(libopenaptx
        LANGUAGES C
        VERSION 0.2.0)

set(CMAKE_C_STANDARD 99)

if("${INSTALL_LIBDIR}" STREQUAL "")
    set(INSTALL_LIBDIR ${CMAKE_INSTALL_PREFIX}/lib)
endif()

if("${INSTALL_INCLUDEDIR}" STREQUAL "")
    set(INSTALL_INCLUDEDIR ${CMAKE_INSTALL_PREFIX}/include)
endif()

if("${INSTALL_PKGCONFIGDIR}" STREQUAL "")
    set(INSTALL_PKGCONFIGDIR ${INSTALL_LIBDIR}/pkgconfig)
endif()

add_subdirectory(pkgconfig)

include_directories(.)

# Library
add_library(openaptx SHARED
        openaptx.c
           )

# Utilities
add_executable (openaptxdec openaptxdec.c)
target_link_libraries(openaptxdec PUBLIC openaptx)

add_executable (openaptxenc openaptxenc.c)
target_link_libraries(openaptxenc PUBLIC openaptx)

# Installation
install(TARGETS
                openaptx
                openaptxdec
                openaptxenc
        LIBRARY
                DESTINATION ${INSTALL_LIBDIR}
        PUBLIC_HEADER
                DESTINATION ${INSTALL_INCLUDEDIR}
        )

