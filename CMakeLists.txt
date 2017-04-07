cmake_minimum_required(VERSION 3.6)
project(core-mqtt-sn-gateway)

set(CMAKE_CXX_STANDARD 11)

file(GLOB GLOBAL_SOURCES *)

include_directories(src)
include_directories(src/Implementation)

set(IMPLEMENTATIONL_FILES
        src/Implementation/MqttBrokerImplementation.cpp src/Implementation/MqttBrokerImplementation.h
        src/Implementation/SocketImplementation.cpp
        src/Implementation/SocketImplementation.h
        src/Implementation/SystemImplementation.cpp
        src/Implementation/SystemImplementation.h
        src/Implementation/LoggerImplementation.cpp
        src/Implementation/LoggerImplementation.h
        src/Implementation/PersistentImplementation.cpp
        src/Implementation/PersistentImplementation.h
        src/main/main.cpp)

set(CORE_FILES
        src/core_defines.h
        src/CoreImpl.cpp
        src/CoreImpl.h
        src/CoreInterface.h
        src/Gateway.cpp
        src/Gateway.h
        src/global_defines.h
        src/LoggerInterface.h
        src/MqttMessageHandlerInterface.cpp
        src/MqttMessageHandlerInterface.h
        src/mqttsn_messages.h
        src/MqttSnMessageHandler.cpp
        src/MqttSnMessageHandler.h
        src/PersistentInterface.cpp
        src/PersistentInterface.h
        src/SocketInterface.cpp
        src/SocketInterface.h
        )


set(SOURCE_FILES ${CORE_FILES} )
add_library(core-mqtt-sn-gateway ${SOURCE_FILES})
add_executable(example-mqtt-sn-gateway ${IMPLEMENTATIONL_FILES})
target_link_libraries(example-mqtt-sn-gateway core-mqtt-sn-gateway)
