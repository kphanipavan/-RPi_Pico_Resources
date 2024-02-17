## Programming Setup

### Dev Envitonment

Nobara 39 on a hand-me-down dual core dell laptop. An RPi Pico, programming over usb cable. Some wires, buttons, LEDs and resistors I <b>Borrowed</b> from lab.

### Code Editor
Instead of using Arduino IDE, I use Visual Studio Code for programming. I use it because I (seem to) write code more efficiently and because I have it customized it to my liking.

Extensions I use:
- C/C++ Extension Pack from ms-vscode
- CMake and CMake tools
- Vim
- My custom dark theme

### Project Generation

A C Pico project requires additional files to handle compilation: CMakeList.txt and pico_sdk_import.cmake, templates of both available in the installed pico sdk. To automate this, I use [Pico Project Generator](https://github.com/raspberrypi/pico-project-generator). 

<img src="https://git.pvnweb.dedyn.io/phanipavank/RPi_Pico_Resources/raw/branch/master/assets/picoProjGen.png" width="300">
