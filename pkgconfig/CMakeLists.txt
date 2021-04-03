set(PREFIX ${CMAKE_INSTALL_PREFIX})
set(LIBDIR ${INSTALL_LIBDIR})
set(INCLUDEDIR ${INSTALL_INCLUDEDIR})
set(VERSION ${PROJECT_VERSION})

set(PC_VAR_PREFIX "\${prefix}")
set(PC_VAR_LIBDIR "\${libdir}")
set(PC_VAR_INCLUDEDIR "\${includedir}")

configure_file(
        libopenaptx.pc.in
        libopenaptx.pc
)

install(FILES
        ${CMAKE_CURRENT_BINARY_DIR}/libopenaptx.pc
        DESTINATION
        ${INSTALL_PKGCONFIGDIR})
