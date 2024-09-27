cmake_minimum_required(VERSION 3.10)
project(JenkinsTest)

add_executable(${PROJECT_NAME} main.cpp)

add_custom_target(App
  COMMAND ${PROJECT_NAME}
  WORKING_DIRECTORY ${CMAKE_BINARY_DIR}
  COMMENT "Running ${PROJECT} executable")

add_custom_command(TARGET ${PROJECT_NAME}
  POST_BUILD
  COMMAND ${CMAKE_COMMAND} --build ${CMAKE_BINARY_DIR} --target App)

