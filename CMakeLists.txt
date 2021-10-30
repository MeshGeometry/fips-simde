if (NOT FIPS_IMPORT)
    cmake_minimum_required(VERSION 2.8)
    get_filename_component(FIPS_ROOT_DIR "../fips" ABSOLUTE)
    include("${FIPS_ROOT_DIR}/cmake/fips.cmake")
    
    set(FIPS_EXCEPTIONS ON CACHE BOOL "Enable C++ exceptions" FORCE)
    set(FIPS_RTTI  ON CACHE BOOL "Enable C++ RTTI" FORCE)

    fips_setup()
    fips_project(fips-simde)
endif()

# target_include_directories(simde::simde INTERFACE "${simde_SOURCE_DIR}")

# Enables native aliases. Not ideal but makes it easier to convert old code.
# target_compile_definitions(simde::simde INTERFACE SIMDE_ENABLE_NATIVE_ALIASES)

fips_add_subdirectory(simde)

if (NOT FIPS_IMPORT)
    fips_finish()
endif()