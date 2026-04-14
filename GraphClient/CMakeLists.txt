cmake_minimum_required(VERSION 3.12)

set(CMAKE_INCLUDE_CURRENT_DIR ON)
set(CMAKE_AUTOMOC ON)


project(2UVGraphClient)

set(SOURCES
    ${SOURCES}
    ${CMAKE_CURRENT_SOURCE_DIR}/clMain.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/clMainWindow.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/clIceClientServer.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/clIceClientLogging.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/clGraphView.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/clGraphLine.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/clQuery.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/ICE_LogApplication.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/ICE_ServerApplication.cpp
)
set(MOC_HEADERS
	${CMAKE_CURRENT_SOURCE_DIR}/clMainWindow.h
	${CMAKE_CURRENT_SOURCE_DIR}/clGraphView.h
)

find_package(Qt5 REQUIRED COMPONENTS Core Widgets Gui Xml Svg Charts Network 3DCore 3DRender 3DInput 3DExtras)


QT5_WRAP_CPP(MOC_SRCS ${MOC_HEADERS})

FIND_LIBRARY(ICE_LIB Ice IceUtil)
FIND_PATH(ICE_PATH Ice)

find_package(Python COMPONENTS Development)
find_package(PostgreSQL)
find_package(Ice COMPONENTS Ice IceDiscovery IceLocatorDiscovery IceSSL)




add_executable(2UVGraphClient ${SOURCES} ${MOC_SRCS})

target_link_libraries(2UVGraphClient Python::Python Qt5::Core Qt5::3DExtras Qt5::3DRender Qt5::3DCore Qt5::3DInput Qt5::Widgets Qt5::Gui Qt5::Svg Qt5::Xml Qt5::Charts Qt5::Network PostgreSQL::PostgreSQL Ice::Ice Ice::IceDiscovery Ice::IceLocatorDiscovery Ice::IceSSL)



