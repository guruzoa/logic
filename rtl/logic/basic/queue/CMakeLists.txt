# Copyright 2018 Tymoteusz Blazejczyk
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

set(vendor_depends "")

if (QUARTUS_FOUND)
    list(APPEND vendor_depends altera_mf)
endif()

if (STD_OVL_FOUND)
    list(APPEND vendor_depends ovl_no_transition)
endif()

add_hdl_source(logic_basic_queue.sv
    SOURCES
        logic_basic_queue_generic_capacity.sv
        logic_basic_queue_generic_memory.sv
        logic_basic_queue_generic_read.sv
        logic_basic_queue_generic_write.sv
        logic_basic_queue_generic.sv
        logic_basic_queue_intel.sv
        logic_basic_queue_main.sv
    DEPENDS
        logic_pkg
        logic_axi4_stream_if
        logic_reset_synchronizer
        ${vendor_depends}
    ANALYSIS
        TRUE
)
