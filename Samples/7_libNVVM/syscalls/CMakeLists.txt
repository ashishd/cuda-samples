# Copyright (c) 2023, NVIDIA CORPORATION. All rights reserved.
#
# Redistribution and use in source and binary forms, with or without
# modification, are permitted provided that the following conditions
# are met:
#  * Redistributions of source code must retain the above copyright
#    notice, this list of conditions and the following disclaimer.
#  * Redistributions in binary form must reproduce the above copyright
#    notice, this list of conditions and the following disclaimer in the
#    documentation and/or other materials provided with the distribution.
#  * Neither the name of NVIDIA CORPORATION nor the names of its
#    contributors may be used to endorse or promote products derived
#    from this software without specific prior written permission.
#
# THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS ``AS IS'' AND ANY
# EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE
# IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR
# PURPOSE ARE DISCLAIMED.  IN NO EVENT SHALL THE COPYRIGHT OWNER OR
# CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL,
# EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO,
# PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR
# PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY
# OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT
# (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE
# OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.


add_test(NAME test-syscalls-malloc-free
	COMMAND "${CMAKE_CURRENT_BINARY_DIR}/../ptxgen/ptxgen" "${CMAKE_CURRENT_SOURCE_DIR}/malloc-free.ll"
  WORKING_DIRECTORY "${CMAKE_CURRENT_BINARY_DIR}")

add_test(NAME test-syscalls-vprintf
	COMMAND "${CMAKE_CURRENT_BINARY_DIR}/../ptxgen/ptxgen" "${CMAKE_CURRENT_SOURCE_DIR}/vprintf.ll"
  WORKING_DIRECTORY "${CMAKE_CURRENT_BINARY_DIR}")

set_tests_properties(test-syscalls-vprintf test-syscalls-malloc-free
                     PROPERTIES FIXTURES_REQUIRED PTXGENTEST)

file(COPY malloc-free.ll DESTINATION "${CMAKE_CURRENT_BINARY_DIR}")
file(COPY vprintf.ll DESTINATION "${CMAKE_CURRENT_BINARY_DIR}")
