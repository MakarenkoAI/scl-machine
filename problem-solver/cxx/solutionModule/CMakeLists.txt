file(GLOB_RECURSE SOURCES "*.cpp" "*.hpp")

list(FILTER SOURCES EXCLUDE REGEX ".*/test/.*")

add_library(solutionModule SHARED ${SOURCES})
target_link_libraries(solutionModule
    LINK_PRIVATE sc-memory
    LINK_PRIVATE sc-agents-common)
target_include_directories(solutionModule
    PUBLIC ${CMAKE_CURRENT_LIST_DIR}
    PRIVATE ${SC_MEMORY_SRC})

if (${SC_BUILD_TESTS})
    include(${CMAKE_CURRENT_LIST_DIR}/test/tests.cmake)
endif ()
