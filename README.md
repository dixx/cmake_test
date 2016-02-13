# Setup

Make sure you have installed and available:
- `gcc --version` (should be 4.7.2 or higher)
- `g++ --version` (should be 4.7.2 or higher)
- `make --version` (should be 3.81 or higher)
- `cmake --version` (should be 2.8 or higher)

In your project folder, switch to folder `cmake` (create it if it doesn't exist). Here will be all the temporary build stuff.
Depending on your OS, execute
- *Linux/OSX*: `cmake ..`
- *Windows*: `cmake -G "MinGW Makefiles" ..` if you have MinGW installed

This will create you a perfect Makefile.
Now you can execute `make` to build your project, and `make install` to install it into your system.
