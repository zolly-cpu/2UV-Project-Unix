cmake_minimum_required(VERSION 3.12)


set(CMAKE_INCLUDE_CURRENT_DIR ON)
set(CMAKE_AUTOMOC ON)
set(Qt5_DIR /usr/lib/x86_64-linux-gnu/cmake/Qt5)


if(DEFINED Qt5_DIR)
	message("Ajust CMAKE_PREFIX_PATH")
	set(CMAKE_PREFIX_PATH ${Qt5_DIR};${CMAKE_PREFIX_PATH})
endif()

find_package(Qt5 REQUIRED COMPONENTS Core Widgets Gui Xml Svg Charts Network)


project(TopLevel)
add_subdirectory(AppStartup)
add_subdirectory(CycleBuilder)
add_subdirectory(ObjectViewer)
add_subdirectory(ServerTest)
add_subdirectory(Server)
add_subdirectory(GraphClient)
add_subdirectory(SocketBox)
add_subdirectory(LogServer)
add_subdirectory(DatabaseEditor)
