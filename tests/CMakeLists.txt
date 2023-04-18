project(SPLIB_tests)

set(SOURCE_FILES
      ${CMAKE_CURRENT_SOURCE_DIR}/SPLIB_test.cpp
)

find_package(SofaPython3Testing REQUIRED)
find_package(SofaGTestMain REQUIRED)
find_package(Sofa.Helper REQUIRED)

set(TEST_FILES
    python3/splib/numerics/matrix_test.py
    python3/splib/numerics/quat_test.py
    python3/splib/numerics/vec3_test.py
    )

enable_testing()
add_executable(${PROJECT_NAME} ${SOURCE_FILES} ${TEST_FILES})
target_link_libraries(${PROJECT_NAME} SofaGTestMain Sofa.Helper SofaPython3Testing)

add_test(NAME ${PROJECT_NAME} COMMAND ${PROJECT_NAME})

file(COPY python3/ DESTINATION ${CMAKE_BINARY_DIR}/bin/splib-tests)
