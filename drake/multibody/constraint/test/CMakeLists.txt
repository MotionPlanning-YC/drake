add_executable(testConstraintConstructor testConstraintConstructor.cpp)
target_link_libraries(testConstraintConstructor drakeRBM drakeRigidBodyConstraint)
drake_add_test(NAME testConstraintConstructor WORKING_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}" COMMAND testConstraintConstructor)
