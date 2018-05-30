cmake_minimum_required(VERSION 3.5 FATAL_ERROR)

project(goliath-zmq-messaging-module LANGUAGES CXX)

set(CMAKE_MODULE_PATH ${CMAKE_CURRENT_SOURCE_DIR}/cmake/modules)

set(BOOST_MIN_VERSION "1.62.0")
set(CPPZMQ_MIN_VERSION "4.2.3")
set(PROTOBUF_MIN_VERSOIN "3.5.1")

find_package(cppzmq ${CPPZMQ_MIN_VERSION} REQUIRED)
find_package(Protobuf ${PROTOBUF_MIN_VERSION} REQUIRED)
find_package(Boost ${BOOST_MIN_VERSION}
        COMPONENTS
            log
        REQUIRED
        )
        
include(protobuf)
include(prepend)

add_subdirectory(third_party)
add_subdirectory(include/goliath)
add_subdirectory(src)

add_library(${PROJECT_NAME} ${SOURCES} ${INCLUDES})

add_definitions(-DBOOST_LOG_DYN_LINK)

include_directories(${Boost_INCLUDE_DIRS})

target_link_libraries(${PROJECT_NAME}
        PUBLIC
            goliath-proto
            goliath-foundation-module
        PRIVATE
            cppzmq
            ${cppzmq_LIBRARY}
            ${Protobuf_LIBRARY}
            ${CMAKE_THREAD_LIBS_INIT}
            ${Boost_LIBRARIES}
        )

target_include_directories(${PROJECT_NAME}
        PUBLIC
            ${CMAKE_CURRENT_SOURCE_DIR}/include
        PRIVATE
            ${ZeroMQ_INCLUDE_DIR}
            ${cppzmq_INCLUDE_DIR}
        )
