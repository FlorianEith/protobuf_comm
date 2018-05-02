cmake_minimum_required(VERSION 2.8.3)
project(protobuf_comm)

add_definitions("-DHAVE_LIBCRYPTO")
add_compile_options(-std=c++11)

find_package(Boost 1.46.1 REQUIRED thread system)
find_package(OpenSSL REQUIRED)

catkin_package(
   INCLUDE_DIRS include
   LIBRARIES protobuf_comm
)

include_directories(
  include
  ${Boost_INCLUDE_DIRS}
  ${OPENSSL_INCLUDE_DIR}
  ${CFH_LIBS_DIR}
)

add_library(${PROJECT_NAME}
  src/client.cpp
  src/server.cpp
  src/crypto.cpp
  src/message_register.cpp
  src/peer.cpp
)

target_link_libraries(${PROJECT_NAME} ${Boost_LIBRARIES} ${OPENSSL_LIBRARIES} )
