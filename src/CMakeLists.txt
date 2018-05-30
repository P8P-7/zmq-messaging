set(RELATIVE_SOURCES
        zmq_io.cpp
        zmq_publisher.cpp
        zmq_subscriber.cpp
        )

prepend(ABSOLUTE_SOURCES ${CMAKE_CURRENT_SOURCE_DIR} ${RELATIVE_SOURCES})

set(SOURCES
        ${ABSOLUTE_SOURCES}
        PARENT_SCOPE
        )
