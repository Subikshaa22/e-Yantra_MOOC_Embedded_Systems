We will consider an example code for blinking the LED on Arduino Uno board as our basis to understand and work with the software installed:

Atmel Studio 7 ( OR ) Visual Studio Code
SimulIDE v0.4.15-final

Step-1: Download blink_led_simulation zip folder. Right-click on the hyperlink and select Save Link As... option to download. Extract the zip file.

Step-2: Open the project blink_led_simulation.atsln present in the blink_led_simulation folder. Start Atmel Studio 7, click on File > Open > Project / Solution and browse for blink_led_simulation.atsln file to open the project.

Step-3: You will notice some pre-written function stubs in blink_led_simulation.c included for your assistance. Debug the program and resolve the errors present in it.

Step-4: Once you are done with resolving the errors, build the project using the shortcut key Ctrl+Alt+F7 or from the Menu bar: Build > Rebuild solution.

If there are no errors present in your program, the project will get compiled correctly and you will get the message in the Output window as below.


**======== Rebuild All: 1 succeeded, 0 failed, 0 skipped ========**
Also, Debug folder will be generated in project directory that will contain blink_led_simulation.hex file along with other build files.

Simulation in SimulIDE
Download blink_led_simulation.simu circuit. Right-click on the hyperlink and select Save Link As... option to download.

Open circuit in SimulIDE.

Load the blink_led_simulation.hex file into the Arduino Uno board and Power the circuit to see the working of your code.
