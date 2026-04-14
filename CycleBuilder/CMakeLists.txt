cmake_minimum_required(VERSION 3.12)

set(CMAKE_INCLUDE_CURRENT_DIR ON)
set(CMAKE_AUTOMOC ON)


project(CycleBuilder)

set(SOURCES
    ${SOURCES}
    ${CMAKE_CURRENT_SOURCE_DIR}/clMain.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/clMainWindow.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/clIceClientLogging.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/clIceClientServer.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/ICE_LogApplication.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/ICE_ServerApplication.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/clCycleBuilderView.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/clClassObjectTreeItem.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/clDatabaseColumn.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/clDatabaseAction.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/clEditObjectUI.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/clNewObjectUI.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/clListWidgetExtendForObject.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/clWidgetExtendForObject.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/clListWidgetSelectObject.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/clListWidgetExtendForString.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/clChangePropertieTextArray.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/clExtendGraphicsView.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/clComboBoxExtend.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/clNode.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/clEdge.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/clParentChild.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/clDatabaseRow.cpp
)
set(MOC_HEADERS
    ${CMAKE_CURRENT_SOURCE_DIR}/clMainWindow.h
    ${CMAKE_CURRENT_SOURCE_DIR}/clCycleBuilderView.h
    ${CMAKE_CURRENT_SOURCE_DIR}/clClassObjectTreeItem.h
    ${CMAKE_CURRENT_SOURCE_DIR}/clEditObjectUI.h
    ${CMAKE_CURRENT_SOURCE_DIR}/clNewObjectUI.h
    ${CMAKE_CURRENT_SOURCE_DIR}/clListWidgetExtendForObject.h
    ${CMAKE_CURRENT_SOURCE_DIR}/clWidgetExtendForObject.h
    ${CMAKE_CURRENT_SOURCE_DIR}/clListWidgetSelectObject.h
    ${CMAKE_CURRENT_SOURCE_DIR}/clListWidgetExtendForString.h
    ${CMAKE_CURRENT_SOURCE_DIR}/clChangePropertieTextArray.h
    ${CMAKE_CURRENT_SOURCE_DIR}/clExtendGraphicsView.h
    ${CMAKE_CURRENT_SOURCE_DIR}/clNode.h
    ${CMAKE_CURRENT_SOURCE_DIR}/clParentChild.h
)

SET (UIS
    ${CMAKE_CURRENT_SOURCE_DIR}/wdChangePropertieText.ui
    ${CMAKE_CURRENT_SOURCE_DIR}/wdCycleBuilderView.ui    
)
find_package(Qt5 REQUIRED COMPONENTS Core Widgets Gui Xml Svg Charts Network)

QT5_WRAP_UI(UI_HEADERS ${UIS})
QT5_WRAP_CPP(MOC_SRCS ${MOC_HEADERS})

FIND_LIBRARY(ICE_LIB Ice IceUtil)
FIND_PATH(ICE_PATH Ice)

find_package(Python COMPONENTS Development)
find_package(PostgreSQL)
find_package(Ice COMPONENTS Ice IceDiscovery IceLocatorDiscovery IceSSL)




add_executable(CycleBuilder ${SOURCES} ${MOC_SRCS} ${UI_HEADERS})

target_link_libraries(CycleBuilder Python::Python Qt5::Core Qt5::Widgets Qt5::Gui Qt5::Svg Qt5::Xml Qt5::Charts Qt5::Network PostgreSQL::PostgreSQL Ice::Ice Ice::IceDiscovery Ice::IceLocatorDiscovery Ice::IceSSL)



