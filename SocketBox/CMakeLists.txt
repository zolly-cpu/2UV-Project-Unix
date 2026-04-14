cmake_minimum_required(VERSION 3.12)

set(CMAKE_INCLUDE_CURRENT_DIR ON)
set(CMAKE_AUTOMOC ON)


project(2UVSocketBox)

set(SOURCES
    ${SOURCES}
    ${CMAKE_CURRENT_SOURCE_DIR}/clMain.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/clSocketBox.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/clSocketBoxThread.cpp
)
set(MOC_HEADERS
	${CMAKE_CURRENT_SOURCE_DIR}/clSocketBox.h
	${CMAKE_CURRENT_SOURCE_DIR}/clSocketBoxThread.h
)

find_package(Qt5 REQUIRED COMPONENTS Core Widgets Gui Xml Svg Charts Network 3DCore 3DRender 3DInput 3DExtras)

QT5_WRAP_CPP(MOC_SRCS ${MOC_HEADERS})

FIND_LIBRARY(ICE_LIB Ice IceUtil)
FIND_PATH(ICE_PATH Ice)

find_package(Python COMPONENTS Development)
find_package(PostgreSQL)
find_package(Ice COMPONENTS Ice IceDiscovery IceLocatorDiscovery IceSSL)




add_executable(2UVSocketBox ${SOURCES} ${MOC_SRCS})

target_link_libraries(2UVSocketBox Python::Python Qt5::Core Qt5::3DExtras Qt5::3DRender Qt5::3DCore Qt5::3DInput Qt5::Widgets Qt5::Gui Qt5::Svg Qt5::Xml Qt5::Charts Qt5::Network PostgreSQL::PostgreSQL Ice::Ice Ice::IceDiscovery Ice::IceLocatorDiscovery Ice::IceSSL)



