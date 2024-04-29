cmake_minimum_required (VERSION 3.10)
project ({{cookiecutter.pkg_name}} VERSION 1.0 LANGUAGES CXX)

set(CMAKE_CXX_STANDARD_11)
set(CMAKE_CXX_STANDARD_REQUIRED True)

set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)
set(CMAKE_AUTOUIC ON)


configure_file({{cookiecutter.pkg_name}}Config.h.in {{cookiecutter.pkg_name}}Config.h)

find_package(Qt5 COMPONENTS Widgets REQUIRED)
find_package(OpenCV REQUIRED )

add_executable(${CMAKE_PROJECT_NAME}
        main.cpp
        mainwindow.cpp
        MyGraphicsView.cpp
)

target_include_directories(${CMAKE_PROJECT_NAME} PUBLIC
                           "${PROJECT_BINARY_DIR}"
                           "${OpenCV_INCLUDE_DIRS}")


target_link_libraries(${CMAKE_PROJECT_NAME} Qt5::Widgets "${OpenCV_LIBS}")
