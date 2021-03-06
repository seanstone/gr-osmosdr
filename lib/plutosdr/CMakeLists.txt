# Copyright 2012 Free Software Foundation, Inc.
#
# This file is part of GNU Radio
#
# GNU Radio is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 3, or (at your option)
# any later version.
#
# GNU Radio is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with GNU Radio; see the file COPYING.  If not, write to
# the Free Software Foundation, Inc., 51 Franklin Street,
# Boston, MA 02110-1301, USA.

########################################################################
# This file included, use CMake directory variables
########################################################################

message(STATUS "IIO_INCLUDE_DIRS ${IIO_INCLUDE_DIRS}")
message(STATUS "GNURADIO_IIO_INCLUDE_DIRS ${GNURADIO_IIO_INCLUDE_DIRS}")

message(STATUS "CMAKE_CURRENT_SOURCE_DIR" ${CMAKE_CURRENT_SOURCE_DIR})

target_include_directories(gnuradio-osmosdr PRIVATE
    ${CMAKE_CURRENT_SOURCE_DIR}
    ${GNURADIO_IIO_INCLUDE_DIRS}
    ${IIO_INCLUDE_DIRS}
    /usr/include/iio
    ${CMAKE_CURRENT_SOURCE_DIR}/..
)

target_link_libraries(gnuradio-osmosdr
#    ${CMAKE_CURRENT_SOURCE_DIR}/iio_sink_c.cc
    ${CMAKE_CURRENT_SOURCE_DIR}/plutosdr_source_c.cc
)

########################################################################
# Append gnuradio-osmosdr library sources
########################################################################
list(APPEND gr_osmosdr_srcs ${iio_srcs})
list(APPEND gr_osmosdr_libs ${GNURADIO_IIO_LIBRARIES} ${IIO_LIBRARIES})
