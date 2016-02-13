# Setup

Make sure you have installed and available:
- `gcc`
- `make`
- `cmake`

In your project folder, switch to folder `cmake`. Here will be all the temporary build stuff.
Depending on your OS, execute
- *Linux/OSX*: `cmake ..`
- *Windows*: `cmake -G "MinGW Makefiles" ..` if you have MinGW installed

This will create you a perfect Makefile.
Now you can execute `make` to build your project, and `make install` to install it into your system.
