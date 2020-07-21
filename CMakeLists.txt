cmake_minimum_required(VERSION 3.14)

project(
	Bliss
	VERSION 0.73.0
	LANGUAGES CXX C
	DESCRIPTION "A Tool for Computing Automorphism Groups and Canonical Labelings of Graphs"
	HOMEPAGE_URL "http://www.tcs.hut.fi/Software/bliss/"
)

add_library(
	libbliss
	src/bliss_C.cc
	src/defs.cc
	src/graph.cc
	src/heap.cc
	src/orbit.cc
	src/partition.cc
	src/timer.cc
	src/uintseqhash.cc
	src/utils.cc
)
set_target_properties(libbliss PROPERTIES OUTPUT_NAME bliss)
add_library(Bliss::libbliss ALIAS libbliss)

target_include_directories(
	libbliss
	PUBLIC
		$<INSTALL_INTERFACE:include>
		$<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
	PRIVATE
		${CMAKE_CURRENT_SOURCE_DIR}/src
)

set_target_properties(libbliss PROPERTIES
	# All code ending in a shared library should be made PIC
	POSITION_INDEPENDENT_CODE ON
	# Compiling with hidden visibility
	CXX_VISIBILITY_PRESET hidden
	VISIBILITY_INLINES_HIDDEN ON
)

add_executable(bliss src/bliss.cc)
add_executable(Bliss::bliss ALIAS bliss)
target_link_libraries(bliss PRIVATE libbliss)
