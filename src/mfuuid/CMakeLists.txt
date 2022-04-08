cmake_minimum_required(VERSION 3.5)
project(mfuuid2 LANGUAGES C)

set(CMAKE_INCLUDE_CURRENT_DIR ON)

add_library(${PROJECT_NAME} STATIC)
target_sources(${PROJECT_NAME} PUBLIC
    libmfuuid.c
    include/propsys2.h
    include/mfapi2.h
    include/mfcaptureengine.h
    include/mfd3d12.h
    include/mfidl2.h
    include/mfmediacapture.h
    include/mfreadwrite2.h
)
target_include_directories(${PROJECT_NAME} PUBLIC
    ${CMAKE_CURRENT_SOURCE_DIR}/include
)

set(INSTALL_HEADERS
    include/propsys2.h
    include/mfapi2.h
    include/mfcaptureengine.h
    include/mfd3d12.h
    include/mfidl2.h
    include/mfmediacapture.h
    include/mfreadwrite2.h
)
set_target_properties(${PROJECT_NAME} PROPERTIES PUBLIC_HEADER "${install_headers}")

install(TARGETS ${PROJECT_NAME})
INSTALL (
    DIRECTORY include/
    DESTINATION include
    FILES_MATCHING PATTERN "*.h*"
)