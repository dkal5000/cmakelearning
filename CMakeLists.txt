cmake_minimum_required(VERSION 3.2)
project(ProjectName)
add_executable(MyExecutable hello.c hello2.c)

add_custom_command(
  OUTPUT ${CMAKE_CURRENT_SOURCE_DIR}/hello2.c
  COMMAND ${CMAKE_COMMAND} -E touch ${CMAKE_CURRENT_SOURCE_DIR}/hello2.c
  DEPENDS ${CMAKE_CURRENT_SOURCE_DIR}/hello.depend
  COMMENT "Supercalifragelisticexpialidocious ${CMAKE_CURRENT_SOURCE_DIR}/hello2.c"
  VERBATIM
)

add_custom_target(generate_hello2_c DEPENDS ${CMAKE_CURRENT_SOURCE_DIR}/hello2.c)

add_dependencies(MyExecutable generate_hello2_c)