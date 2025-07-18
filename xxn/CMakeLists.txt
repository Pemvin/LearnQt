############################################################################
# QSkinny - Copyright (C) The authors
#           SPDX-License-Identifier: BSD-3-Clause
############################################################################
cmake_minimum_required(VERSION 3.27)
set(ENV{LC_ALL} "C.UTF-8")
set(ENV{LANG} "C.UTF-8")

project(XxnApp
    VERSION 1.0.0
    LANGUAGES CXX)
find_package(Qt6 REQUIRED COMPONENTS Core Quick Qml OpenGL QuickControls2 ShaderTools )#ShaderToolsTools)
find_package(QSkinny REQUIRED)

qt_standard_project_setup(REQUIRES 6.8)
qt_policy(SET QTP0001 NEW)
qt_policy(SET QTP0002 NEW)
qt_policy(SET QTP0003 NEW) # Qt 6.7
qt_policy(SET QTP0004 NEW) # Qt 6.8
 
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
 
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)
set(CMAKE_AUTOUIC OFF)

 # 自动收集src目录下的所有源文件
file(GLOB_RECURSE PROJECT_SOURCES 
    "${CMAKE_CURRENT_SOURCE_DIR}/src/*.cpp"
)
 
add_executable(${PROJECT_NAME} WIN32
    ${PROJECT_SOURCES}
    qml/qml.qrc)

target_link_libraries(${PROJECT_NAME} PRIVATE
    Qt6::Core
    Qt6::Gui
    Qt6::Qml
    Qt6::Quick
    Qsk::QSkinny
    Qsk::QmlExport)

qt_add_shaders(${PROJECT_NAME} "shaders"
    BATCHABLE 
    PRECOMPILE
#    OPTIMIZED
#    GLSL "310es,440"
#    PREFIX
#        "/qt/qml/xxn"
    FILES
        "qml/shaders/background.vert"
        "qml/shaders/background.frag"
)

