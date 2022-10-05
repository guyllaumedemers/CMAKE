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

message("\nMyMacro")

macro(MyMacro ARG1) #access global value which is why it can set value inside macro
	message("\t Inside MyMacro: ${ARG1}")
	set(ARG1 -1)
	message("\t Inside MyMacro: ${ARG1}")
endmacro()

message("Outside MyMacro: ${ARG1}")
set(ARG1 100)
MyMacro("${ARG1}")
message("Outside MyMacro: ${ARG1}")

message("\nMyMacro2")

macro(MyMacro2 ARGS1) #avoid macro... cannot set Args values inside macro and print the modified value. can ONLY update Args value if VERBOSE is EQUAL to the Args passed AND that this Args passed is global.
	message("\t Inside MyMacro2: ${ARGS1}")
	set("${ARGS1}" -10)
	message("\t Inside MyMacro2: ${ARGS1}")
endmacro()

message("Outisde MyMacro2: ${ARG1}")
MyMacro2("${ARG1}")
message("Outside MyMacro2: ${ARG1}")
