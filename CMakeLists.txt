cmake_minimum_required(VERSION 3.10)
project(SimpleCIDemo LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

include(FetchContent)
FetchContent_Declare(
  googletest
  GIT_REPOSITORY https://github.com/google/googletest.git
  # Pick a stable release tag to avoid breakage; change if you prefer 'main'
  GIT_TAG release-1.14.0
)
FetchContent_MakeAvailable(googletest)

enable_testing()

add_executable(runTests
  calculator.cpp
  test_calculator.cpp
)

# Link against the official imported target provided by googletest
target_link_libraries(runTests PRIVATE GTest::gtest_main)

include(GoogleTest)
gtest_discover_tests(runTests)
