cmake_minimum_required(VERSION 3.5)
project(majordomo)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")

set(SOURCE_FILES_BROKER src/mdp_broker.c src/mdp_msg.c )
add_library(mdp_broker STATIC ${SOURCE_FILES_BROKER})

set(SOURCE_FILES_WORKER src/mdp_worker.c src/mdp_worker_msg.c )
add_library(mdp_worker STATIC ${SOURCE_FILES_WORKER})

set(SOURCE_FILES_CLIENT src/mdp_client.c src/mdp_client_msg.c )
add_library(mdp_client STATIC ${SOURCE_FILES_CLIENT})

set(SOURCE_FILES_TEST src/mdp_test.c)
add_executable(mdp_test ${SOURCE_FILES_TEST})
target_link_libraries(mdp_test czmq zmq mdp_broker mdp_worker mdp_client)