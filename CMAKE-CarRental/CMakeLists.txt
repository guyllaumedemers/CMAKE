cmake_minimum_required(VERSION 3.20)

project(
	CAR_RENTAL_TUTORIAL
	VERSION 0.0.0.0
	DESCRIPTION "template for car rental service"
	LANGUAGES CXX
	)

set(PROJECT_STATIC_SRC_DIR "CMAKE-CarRental")

include("${PROJECT_STATIC_SRC_DIR}/Car.cmake")

add_executable(
	${PROJECT_NAME}
	Main.cpp
	${CAR_RENTAL}
	)
