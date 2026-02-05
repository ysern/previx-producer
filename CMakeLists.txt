add_library(previx-producer SHARED
  src/producer.cpp
)

add_library(previx::producer
  ALIAS
    previx-producer
)

target_link_libraries(previx-producer
  PUBLIC previx::server
)

target_include_directories(previx-producer
  PUBLIC
    $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
    $<INSTALL_INTERFACE:include>
)

target_compile_definitions(previx-producer
  PRIVATE PREVIX_PRODUCER_BUILD
)

install(TARGETS previx-producer
  RUNTIME DESTINATION bin
  LIBRARY DESTINATION lib
  ARCHIVE DESTINATION lib
)

install(
  DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/include/
  DESTINATION include
)
