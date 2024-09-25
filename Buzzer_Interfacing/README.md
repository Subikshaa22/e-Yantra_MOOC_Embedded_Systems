AIM
In this experiment, you will interface a Buzzer with the ATmega2560 microcontroller. Buzzer is already interfaced and present on Firebird V robot. You are provided with a skeleton code of Buzzer interfacing program.

The program is ideally expected to configure the Buzzer as output device and turn it ON and OFF at an interval of 1 second. This should repeat itself indefinitely.

The program is provided in a project folder. But, the program contains few errors which you have to find and debug. Once you resolve the errors, you have to build the project as instructed below.

CONNECTIONS
Buzzer : PC3
MACROS TO USE
In the Masking tutorial, you have seen that to configure the Buzzer Port Pin (PC3) as Output, you have to use: DDRC |= (1 << 3).

But, in the skeleton code Experiment-1.c, we have included a header file named, firebird_simulation.h which consists of the declaration of a constant for DDRC register as:

#define buzzer_ddr_reg DDRC

Similarly, other constants are defined:

#define buzzer_port_reg PORTC

#define buzzer_pin 3 // PC3

You have to use these constants declared in firebird_simulation.h and the Masking Operators to complete the Experiment-1. Hence the DDRC |= (1 << 3) will be written as:

buzzer_ddr_reg |= (1 << buzzer_pin)

PROCEDURE
For Windows User (Atmel Studio 7)
Step-1: Download Experiment-1 zip folder. Right-click on the hyperlink and select Save Link As... option to download. Extract the zip file.

Step-2: Open the project Experiment-1.atsln present in the Experiment-1 folder. Start Atmel Studio 7, click on File > Open > Project / Solution and browse for Experiment-1.atsln file to open the project.

Step-3: You will notice some pre-written function stubs in Experiment-1.c included for your assistance. Debug the program and resolve the errors present in it.

Step-4: Once you are done with resolving the errors, build the project using the shortcut key Ctrl+Alt+F7 or from the Menu bar: Build > Rebuild solution.

Note: Make sure you select Change Device option in Project settings and choose ATmega328P instead of ATmega2560, follow the steps in the gif below for the same.

device_change_microchip_studio
If there are no errors present in your program, the project will get compiled correctly and you will get the message in the Output window as below. Also, Debug folder will be generated in project directory that will contain Experiment-1.hex file along with other build files.


**======== Rebuild All: 1 succeeded, 0 failed, 0 skipped ========**

EXPECTED OUTPUT
Load the hex file on the Firebird V robot or simulator circuit once your program gets build successfully. Ensure that code performs as expected.

NOTE: Getting Build succeeded output doesn't mean that your program will give the expected output, there can be logical errors.
