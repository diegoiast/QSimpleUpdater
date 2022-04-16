cmake_minimum_required(VERSION 3.20)

project(QSimpleUpdater)

set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)
set(CMAKE_AUTOUIC ON)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

find_package(Qt5 COMPONENTS Core Gui Network Widgets REQUIRED)

add_library(QSimpleUpdater
    etc/resources/qsimpleupdater.qrc
    src/Downloader.ui
    src/Downloader.cpp
    src/Downloader.h
    src/Updater.cpp
    src/Updater.h
    src/QSimpleUpdater.cpp
    include/QSimpleUpdater.h
)
target_link_libraries(QSimpleUpdater PRIVATE Qt5::Widgets Qt5::Network)
target_include_directories(QSimpleUpdater PUBLIC include/)
target_include_directories(QSimpleUpdater PRIVATE src/)
target_compile_definitions(QSimpleUpdater PRIVATE -DQSU_INCLUDE_MOC)

# I am unsure if I should define these? Leaving it out seems to work
#target_compile_definitions(QSimpleUpdater PUBLIC -DQSU_IMPORT)
#target_compile_definitions(QSimpleUpdater PRIVATE -DQSU_IMPORT)
