cmake_minimum_required(VERSION 3.0.0)
project(Gauntlet VERSION 0.1.0)


enable_testing()
add_subdirectory(JoyController/JoyLib)
add_subdirectory(ICM20948/rpi_ICM20948)
add_subdirectory(rpi_ads1115-main)

add_executable(Gauntlet main.cpp)
target_link_libraries(Gauntlet icm20948 ads1115rpi_static JoyLib)

target_include_directories(${PROJECT_NAME} PUBLIC JoyController/JoyLib)
target_include_directories(${PROJECT_NAME} PRIVATE rpi_ads1115-main)
target_include_directories(${PROJECT_NAME} PUBLIC ICM20948/rpi_ICM20948)
target_include_directories(${PROJECT_NAME} PUBLIC Gaunlet_class)

set(CPACK_PROJECT_NAME ${PROJECT_NAME})
set(CPACK_PROJECT_VERSION ${PROJECT_VERSION})
include(CPack)
