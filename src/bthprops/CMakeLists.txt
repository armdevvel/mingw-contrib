cmake_minimum_required(VERSION 3.5)
project(bthprops LANGUAGES C)

set(CMAKE_INCLUDE_CURRENT_DIR ON)

add_custom_target(${PROJECT_NAME} ALL
    armv7-w64-mingw32-dlltool -m arm -k --as=armv7-w64-mingw32-as --output-lib "\"${PROJECT_BINARY_DIR}/libbthprops.a\"" --input-def "\"${PROJECT_SOURCE_DIR}/bthprops.def\""
)

install(PROGRAMS ${PROJECT_BINARY_DIR}/libbthprops.a DESTINATION lib)