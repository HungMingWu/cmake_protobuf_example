find_package(Protobuf REQUIRED)
FILE(GLOB protofiles "${CMAKE_CURRENT_SOURCE_DIR}/*.proto")
PROTOBUF_GENERATE_CPP(PROTOSRCS PROTOHDRS ${protofiles})
add_library(proto STATIC ${PROTOSRCS} ${PROTOHDRS}) 
target_include_directories(proto
	PUBLIC ${CMAKE_CURRENT_BINARY_DIR}
		   ${PROTOBUF_INCLUDE_DIR}
)
target_link_libraries(proto PRIVATE ${PROTOBUF_LIBRARIES})
