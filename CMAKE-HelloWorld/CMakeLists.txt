cmake_minimum_required(VERSION 3.20)

set(VAR 1 2 3)

message("foreach loop:")

foreach(MYVAR IN LISTS VAR)
	if(NOT MYVAR EQUAL 3 AND MYVAR GREATER 1)
		message("\t ${MYVAR}")
	elseif(MYVAR EQUAL 3)
		message("\t last Index, ${MYVAR}")
	endif()
endforeach(MYVAR)

set(INDEX 0)

set(SIZE 0)
list(LENGTH VAR SIZE)

message("list length:${SIZE}")
message("while loop:")

while(INDEX LESS SIZE) #so useless, cant even get value by index in list
	list(GET VAR 0 1 2 VAL)
	message("\t ${VAL}")
	math(EXPR INDEX "${INDEX}+1")
endwhile()

function(MyFunc ARGS1 ARGS2)
	message("Inside Function: ${CMAKE_CURRENT_FUNCTION}")
	message("Inside Function: ARGS1 ${ARGS1} ARGS2 ${ARGS2}")
	set(ARGS1 -1)
	message("Inside Function: ARGS1 ${ARGS1}")
endfunction()

set(ARG1 0)
set(ARG2 1)

message("Outside function: ARG1 ${ARG1}")

MyFunc(${ARG1} ${ARG2})

message("Outside Function: ARG1 ${ARG1}")
