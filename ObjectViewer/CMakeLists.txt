cmake_minimum_required(VERSION 3.12)

set(CMAKE_INCLUDE_CURRENT_DIR ON)
set(CMAKE_AUTOMOC ON)


project(ObjectViewer)

set(SOURCES
    ${SOURCES}
    ${CMAKE_CURRENT_SOURCE_DIR}/clChangePropertieTextArray.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/clChangePropertieText.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/clClassInfo.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/clClassLoader.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/clObject.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/clObjectListItem.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/clObjectLocator.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/clObjectViewer.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/clProductPlanner.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/clSchedulePlanner.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/clTimeLine.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/clGraphicsItem.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/clGraphicsScene.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/clGraphicsView.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/Indicator.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/Track.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/clMain.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/clMainWindow.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/clIceClientLogging.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/clIceClientServer.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/ICE_LogApplication.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/ICE_ServerApplication.cpp
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
    ${CMAKE_CURRENT_SOURCE_DIR}/clChangePropertieText.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/clComboBoxExtend.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/clObjectCall.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/clMethodCall.cpp
    
)
set(MOC_HEADERS
    ${CMAKE_CURRENT_SOURCE_DIR}/clMainWindow.h
    ${CMAKE_CURRENT_SOURCE_DIR}/clObjectViewer.h
    ${CMAKE_CURRENT_SOURCE_DIR}/clProductPlanner.h
    ${CMAKE_CURRENT_SOURCE_DIR}/clSchedulePlanner.h
    ${CMAKE_CURRENT_SOURCE_DIR}/clClassInfo.h
    ${CMAKE_CURRENT_SOURCE_DIR}/clClassLoader.h
    ${CMAKE_CURRENT_SOURCE_DIR}/clClassObjectTreeItem.h
    ${CMAKE_CURRENT_SOURCE_DIR}/clEditObjectUI.h
    ${CMAKE_CURRENT_SOURCE_DIR}/clNewObjectUI.h
    ${CMAKE_CURRENT_SOURCE_DIR}/clListWidgetExtendForObject.h
    ${CMAKE_CURRENT_SOURCE_DIR}/clWidgetExtendForObject.h
    ${CMAKE_CURRENT_SOURCE_DIR}/clListWidgetSelectObject.h
    ${CMAKE_CURRENT_SOURCE_DIR}/clListWidgetExtendForString.h
    ${CMAKE_CURRENT_SOURCE_DIR}/clChangePropertieTextArray.h
    ${CMAKE_CURRENT_SOURCE_DIR}/clChangePropertieText.h
    ${CMAKE_CURRENT_SOURCE_DIR}/clObjectListItem.h
    ${CMAKE_CURRENT_SOURCE_DIR}/clComboBoxExtend.h
    ${CMAKE_CURRENT_SOURCE_DIR}/clObjectLocator.h
    ${CMAKE_CURRENT_SOURCE_DIR}/clGraphicsScene.h
    ${CMAKE_CURRENT_SOURCE_DIR}/clGraphicsView.h
    ${CMAKE_CURRENT_SOURCE_DIR}/clTimeLine.h
)

SET (UIS
    ${CMAKE_CURRENT_SOURCE_DIR}/wdChangePropertieText.ui
    ${CMAKE_CURRENT_SOURCE_DIR}/wdObjectLocator.ui 
    ${CMAKE_CURRENT_SOURCE_DIR}/wdSchedulePlanner.ui
    ${CMAKE_CURRENT_SOURCE_DIR}/wdProductPlanner.ui
    ${CMAKE_CURRENT_SOURCE_DIR}/wdObjectView.ui
)
find_package(Qt5 REQUIRED COMPONENTS Core Widgets Gui Xml Svg Charts Network 3DCore 3DRender 3DInput 3DExtras)

QT5_WRAP_UI(UI_HEADERS ${UIS})
QT5_WRAP_CPP(MOC_SRCS ${MOC_HEADERS})

FIND_LIBRARY(ICE_LIB Ice IceUtil)
FIND_PATH(ICE_PATH Ice)

find_package(Python COMPONENTS Development)
find_package(PostgreSQL)
find_package(Ice COMPONENTS Ice IceDiscovery IceLocatorDiscovery IceSSL)




add_executable(ObjectViewer ${SOURCES} ${MOC_SRCS} ${UI_HEADERS})

target_link_libraries(ObjectViewer Python::Python Qt5::Core Qt5::3DExtras Qt5::3DRender Qt5::3DCore Qt5::3DInput Qt5::Widgets Qt5::Gui Qt5::Svg Qt5::Xml Qt5::Charts Qt5::Network PostgreSQL::PostgreSQL Ice::Ice Ice::IceDiscovery Ice::IceLocatorDiscovery Ice::IceSSL)



