# Copyright (c) 2022-2023 Robert Bosch GmbH
#
# This program and the accompanying materials are made available under the
# terms of the Apache License, Version 2.0 which is available at
# https://www.apache.org/licenses/LICENSE-2.0.
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS, WITHOUT
# WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the
# License for the specific language governing permissions and limitations
# under the License.
#
# SPDX-License-Identifier: Apache-2.0

set(TARGET_NAME "app_utests")

add_executable(${TARGET_NAME}
    ${CMAKE_CURRENT_SOURCE_DIR}/../../src/SeatAdjusterApp.cpp
    SeatAdjusterApp_test.cpp
)

include_directories(
    ${CMAKE_CURRENT_SOURCE_DIR}/../../src
)

add_dependencies(${TARGET_NAME}
    vehicle-app-sdk
    app
)

target_link_libraries(${TARGET_NAME}
    vehicle-app-sdk
    gtest_main
)

include(GoogleTest)
gtest_discover_tests(${TARGET_NAME})