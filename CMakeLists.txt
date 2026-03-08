cmake_minimum_required(VERSION 3.15)
project(WebAgent VERSION 1.0 LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Зависимости (нужно установить через vcpkg, conan или apt/brew)
find_package(CPR REQUIRED)
find_package(nlohmann_json REQUIRED)
find_package(spdlog REQUIRED)
find_package(GTest REQUIRED) # Для тестов

add_executable(web_agent
    src/main.cpp
    src/config.cpp
    src/logger.cpp
    src/network.cpp
    src/agent.cpp
    src/task.cpp
)

target_include_directories(web_agent PRIVATE include)
target_link_libraries(web_agent PRIVATE
    CPR::cpr
    nlohmann_json::nlohmann_json
    spdlog::spdlog
)

# Тесты
add_subdirectory(tests)
