cmake_minimum_required(VERSION 3.10)

project(i-playground VERSION 1.0 LANGUAGES C)

set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

if (NOT DEFINED BUNYAN_I_GENERATED_C)
    message(FATAL_ERROR "i-playground must be built through bunyan.py in mode='i'")
endif()
if (NOT DEFINED BUNYAN_I_COMPILER_DIR OR NOT DEFINED BUNYAN_I_STD_DIR)
    message(FATAL_ERROR "Bunyan could not resolve I.exe on PATH")
endif()

add_executable(${PROJECT_NAME}
    ${BUNYAN_I_GENERATED_C}
    ${BUNYAN_I_GENERATED_H}
)

set_source_files_properties(${BUNYAN_I_GENERATED_C} PROPERTIES
    OBJECT_DEPENDS "${BUNYAN_I_ENTRY};${BUNYAN_I_GENERATED_H}"
)

target_include_directories(${PROJECT_NAME} PRIVATE
    ${BUNYAN_I_GEN_DIR}
    ${BUNYAN_I_COMPILER_DIR}
    ${BUNYAN_I_STD_DIR}
)
