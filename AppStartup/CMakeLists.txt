cmake_minimum_required(VERSION 3.12)


set(CMAKE_INCLUDE_CURRENT_DIR ON)
set(CMAKE_AUTOMOC ON)




project(AppStarter)
add_executable(AppStarter
    ${SOURCE}
    ${CMAKE_CURRENT_SOURCE_DIR}/clMain.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/clAppStarterWidget.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/clAppStarterWidget.h
)
target_link_libraries(AppStarter Qt5::Core Qt5::Widgets Qt5::Gui Qt5::Svg Qt5::Xml)

