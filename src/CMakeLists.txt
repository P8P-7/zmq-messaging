set(SOURCES
        zmq_io.cpp
        zmq_publisher.cpp
        zmq_subscriber.cpp
        )

add_library(${PROJECT_NAME} ${SOURCES})

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
