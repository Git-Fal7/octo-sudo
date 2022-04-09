cmake_minimum_required(VERSION 3.23)
project(octo-sudo)
find_package(Qt5 REQUIRED COMPONENTS Core Gui Widgets)
find_package(Threads REQUIRED)
find_library(UTIL_LIBRARY NAMES util)

set(CMAKE_AUTOMOC ON)

set(src main.cpp passworddialog.cpp sudo.cpp)

set(header passworddialog.h sudo.h)

set(ui passworddialog.ui)

qt5_wrap_ui(src ${ui})

add_executable(octo-sudo ${src} ${header} ${qmFiles})
target_compile_definitions(octo-sudo PRIVATE QT_DEPRECATED_WARNINGS QT_USE_QSTRINGBUILDER QT_NO_CAST_FROM_ASCII QT_NO_CAST_TO_ASCII QT_NO_URL_CAST_FROM_STRING QT_NO_CAST_FROM_BYTEARRAY)
target_include_directories(octo-sudo PRIVATE ${CMAKE_CURRENT_BINARY_DIR} ${Qt5Core_INCLUDE_DIRS} ${Qt5Gui_INCLUDE_DIRS} ${Qt5Widgets_INCLUDE_DIRS})
target_link_libraries(octo-sudo PRIVATE Threads::Threads Qt5::Core Qt5::Gui Qt5::Widgets ${UTIL_LIBRARY})
install(TARGETS octo-sudo RUNTIME DESTINATION lib/octo-sudo LIBRARY DESTINATION lib PUBLIC_HEADER DESTINATION include)
