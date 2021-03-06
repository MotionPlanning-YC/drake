# Source files used to build drakeSystemAnalysis
set(sources
  simulator.cc
)

# Headers that should be installed with Drake so that they
# are available elsewhere via #include.
set(installed_headers
    integrator_base.h
    explicit_euler_integrator.h
    runge_kutta2_integrator.h
    simulator.h
)

# Headers that are needed by code here but should not
# be exposed anywhere else.
set(private_headers)

add_library_with_exports(LIB_NAME drakeSystemAnalysis
  SOURCE_FILES ${sources} ${installed_headers} ${private_headers})
target_link_libraries(drakeSystemAnalysis drakeSystemFramework drakeCommon)

drake_install_headers(${installed_headers})

pods_install_libraries(drakeSystemAnalysis)
drake_install_pkg_config_file(drake-system-analysis
  TARGET drakeSystemAnalysis
  LIBS -ldrakeSystemAnalysis
  REQUIRES
    drake-common
    drake-system-framework)

if(BUILD_TESTING)
  add_subdirectory(test)
endif()
