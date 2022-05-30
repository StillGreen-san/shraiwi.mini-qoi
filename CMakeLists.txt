cmake_minimum_required( VERSION 3.20 )

project( shraiwi_miniqoi C CXX )

option( ENABLE_EXAMPLES "build examples" OFF )

add_library( shraiwi_miniqoi_c src/mini_qoi.c )
add_library( shraiwi::miniqoi::c ALIAS shraiwi_miniqoi_c )
target_include_directories( shraiwi_miniqoi_c PUBLIC src )

add_library( shraiwi_miniqoi_cpp src/MiniQOI.cpp )
add_library( shraiwi::miniqoi::cpp ALIAS shraiwi_miniqoi_cpp )
target_link_libraries( shraiwi_miniqoi_cpp PRIVATE shraiwi_miniqoi_c )

if( ENABLE_EXAMPLES )
	add_executable( shraiwi_miniqoi_cmdline_decoder examples/cmdline_decoder/mqoi_decoder.c )
	target_link_libraries( shraiwi_miniqoi_cmdline_decoder PRIVATE shraiwi_miniqoi_c )
endif()
