include_directories(.)
include("${wxWidgets_USE_FILE}")

# add resources on windows
if (WIN32)
  set(sources "${sources}; App.rc")
endif()

file(GLOB sources *.cpp)

add_executable(wxcalc ${sources}) 

target_link_libraries(wxcalc ${wxWidgets_LIBRARIES})

install(TARGETS wxcalc RUNTIME DESTINATION bin)

if (DEFINED TESTS AND NOT TESTS EQUAL 0)
  add_subdirectory(test)
endif()
