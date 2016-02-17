## Goal
This will be an example how to set up CMake for a more complex project.
I did this to 1) learn how to CMake to 2) be able to cross-compile **dixx/Die_Chroniken_eines_namenlosen_Spiels** more easily.

## Setup
Make sure you have installed and available:
- `gcc --version` (should be 4.7.2 or higher)
- `g++ --version` (should be 4.7.2 or higher)
- `make --version` (should be 3.81 or higher)
- `cmake --version` (should be 2.8 or higher)

In your project folder, switch to folder `_build` (create it if it doesn't exist). Here will be all the temporary build stuff.
Depending on your OS, execute
- *Linux/OSX*: `cmake ..`
- *Windows*: `cmake -G "MinGW Makefiles" ..` if you have MinGW installed

This will create you a perfect Makefile.
Now you can execute `make` to build your project, and `make install` to install it into your system.

## Sources
This example is combined of information mainly from this sources:
- http://irrlicht.sourceforge.net/forum/viewtopic.php?t=37091
- https://cmake.org/cmake-tutorial/
- http://stackoverflow.com/questions/21163188/most-simple-but-complete-cmake-example
- https://tuannguyen68.gitbooks.io/learning-cmake-a-beginner-s-guide/content/chap1/chap1.html
