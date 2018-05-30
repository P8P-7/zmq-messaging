set(RELATIVE_INCLUDES
        zmq-messaging.h
        zmq-messaging/zmq_io.h
        zmq-messaging/zmq_publisher.h
        zmq-messaging/zmq_subscriber.h
        )

prepend(ABSOLUTE_INCLUDES ${CMAKE_CURRENT_SOURCE_DIR} ${RELATIVE_INCLUDES})

set(INCLUDES
        ${ABSOLUTE_INCLUDES}
        PARENT_SCOPE
        )
