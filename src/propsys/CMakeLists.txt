cmake_minimum_required(VERSION 3.5)
project(propsys2 LANGUAGES C)

set(CMAKE_INCLUDE_CURRENT_DIR ON)

add_custom_target(${PROJECT_NAME} ALL
    armv7-w64-mingw32-dlltool -m arm -k --as=armv7-w64-mingw32-as --output-lib "\"${PROJECT_BINARY_DIR}/libpropsys2.a\"" --input-def "\"${PROJECT_SOURCE_DIR}/propsys.def\""
)

install(PROGRAMS ${PROJECT_BINARY_DIR}/libpropsys2.a DESTINATION lib)