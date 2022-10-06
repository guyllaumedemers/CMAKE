add_library(
	cars OBJECT
	Car.cpp
	CarMaintenance.cpp
	)

target_include_directories(
	cars
	PUBLIC
	.
	)
