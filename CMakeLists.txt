cmake_minimum_required(VERSION 3.5)
project(SPLIB VERSION 3.0)

include(cmake/environment.cmake)

find_package(SofaFramework REQUIRED)
find_package(SofaPython3 REQUIRED)

if(SofaPython3_FOUND)
    message("-- Found SofaPython3")
    SP3_add_python_package(
        SOURCE_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/src/python3/splib
        TARGET_DIRECTORY splib
    )
    set(SofaPythonAny_FOUND TRUE)
endif()

set(HEADER_FILES src/cpp/splib/initPlugin.h)
set(SOURCE_FILES src/cpp/splib/initPlugin.cpp)

file(GLOB_RECURSE RESOURCE_FILES  "*.md" "*.psl" "*.py" "*.pyscn" "*.scn" "*.rst")

add_library(${PROJECT_NAME} SHARED ${HEADER_FILES} ${SOURCE_FILES} ${RESOURCE_FILES})
set_target_properties(${PROJECT_NAME} PROPERTIES COMPILE_FLAGS "-DSOFA_BUILD_SPLIB")
set_target_properties(${PROJECT_NAME} PROPERTIES DEBUG_POSTFIX "_d")
target_link_libraries(${PROJECT_NAME} SofaCore)

## Install rules for the library and headers; CMake package configurations files
sofa_create_package_with_targets(
    PACKAGE_NAME SPLIB
    PACKAGE_VERSION ${PROJECT_VERSION}
    TARGETS ${PROJECT_NAME} AUTO_SET_TARGET_PROPERTIES
    INCLUDE_INSTALL_DIR SPLIB
    INCLUDE_SOURCE_DIR "src"
    RELOCATABLE "plugins"
    )

install(DIRECTORY docs DESTINATION share/sofa/${PROJECT_NAME})
install(FILES "README.md" "LICENSE" DESTINATION .)

include(cmake/packaging.cmake)
