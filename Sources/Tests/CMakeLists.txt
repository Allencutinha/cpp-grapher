add_subdirectory(Runner)
add_subdirectory(Integration)
add_subdirectory(Performance)
add_subdirectory(System)
add_subdirectory(Unit)

set(TEST_SOURCE_FILES
        ${UNIT_TEST_SOURCE_FILES}
        ${INTEGRATION_TEST_SOURCE_FILES}
        ${PERFORMANCE_SOURCE_FILES}
        ${SYSTEM_TEST_SOURCE_FILES}
        ${TEST_RUNNER_SOURCE_FILES})

add_executable(Tests ${TEST_SOURCE_FILES})

target_include_directories(Tests PUBLIC
        ${CMAKE_CURRENT_SOURCE_DIR}/3rdParty/Catch/include/
        /usr/local/include/ImageMagick-7/)

target_compile_definitions(Tests PRIVATE TEST_HELPER_ACCESS_PRIVATES MAGICKCORE_QUANTUM_DEPTH=8 MAGICKCORE_HDRI_ENABLE)
target_link_libraries (Tests PUBLIC Runner CppGrapher RangedGraph)
