# ESL_HW2
// make a directory to put all the binary files and generated Makefile<br>
mkdir build<br>
<br>
// CMake takes the current directory as build directory.<br>
cd build<br>
<br>
//Generating Makefiles, the given path must contain CMakeLists.txt<br>
cmake ..<br>
<br>
//Compile the SystemC source code.<br>
make<br>
<br>
// Run the program<br>
make run<br>
