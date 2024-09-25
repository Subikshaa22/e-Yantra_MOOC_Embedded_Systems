AIM
In this experiment, you will interface the Bar-graph LEDs and the Interrupt Switch already present on Firebird V robot. The aim of this experiment is to get you familiar with the configuring and interfacing of Input and Output devices.

Your task is to toggle the status of 2 Bar-graph LEDs depending on whether the Interrupt Switch is pressed or released.

The program is provided in a project folder. But, the program contains few incomplete functions which you would have to complete as per the instructions present in the comments.

CONNECTIONS
Interrupt Switch : PE7

NOTE: There are two switches present on Firebird-V. One is Reset Switch and the other is Interrupt Switch. In this experiment we will be using the Interrupt Switch which is connected to an External Interrupt Pin (PE7 / INT7) and hence the name.

Bar-graph LED:


   	  LED 1   -->   PJ0

   	  LED 2   -->   PJ1

   	  LED 3   -->   PJ2

   	  LED 4   -->   PJ3

   	  LED 5   -->   PJ4

   	  LED 6   -->   PJ5

   	  LED 7   -->   PJ6

   	  LED 8   -->   PJ7
NOTE: In order to connect PORTJ of ATmega2560 to the Bar-graph LED on the Firebird-V, make sure that Jumper J3 is present as shown in the figure below.

j3_jumper_interrupt_switch

MACROS TO USE
In the skeleton code Experiment-2.c, we have included a header file named, firebird_simulation.h which consists of the declaration of the following constants:

For Interrupt Switch:

#define interrupt_sw_ddr_reg DDRE

#define interrupt_sw_port_reg PORTE

#define interrupt_sw_pin 7 // PE7

For Bar-graph LED:

#define bar_graph_led_ddr_reg DDRJ

#define bar_graph_led_port_reg PORTJ

#define bar_graph_led_2_pin 1 // PJ1

#define bar_graph_led_8_pin 7 // PJ7

#define bar_graph_led_6_pin 5 // PJ5

You have to use these constants declared in firebird_simulation.h and the Masking Operators to complete the Experiment-2.

PROCEDURE
For Windows User (Atmel Studio 7)
Step-1: Download Experiment-2 zip folder. Right-click on the hyperlink and select Save Link As... option to download. Extract the zip file.

Step-2: Open the project Experiment-2.atsln present in the Experiment-2 folder. Start Atmel Studio 7, click on File > Open > Project / Solution and browse for Experiment-2.atsln file to open the project.

Step-3: You will notice some pre-written function stubs in Experiment-2.c included for your assistance. Complete the program as per the instructions present as comments in the C file, Experiment-2.c.

Step-4: After completing the source file i.e. Experiment-2.c, build the project using the shortcut key Ctrl+Alt+F7 or from the Menu bar: Build > Rebuild solution.

Note: Make sure you select Change Device option in Project settings and choose ATmega328P instead of ATmega2560, follow the steps in the gif below for the same.

device_change_microchip_studio
If there are no errors present in your program, the project will get compiled correctly and you will get the message in the Output window as below. Also, Debug folder will be generated in project directory that will contain Experiment-2.hex file along with other build files.


**======== Rebuild All: 1 succeeded, 0 failed, 0 skipped ========**


ALGORITHM
Complete the program as per the instructions present as comments in the C file. Complete the pre-written functions to achieve the following as per the main function:

Only the 2nd, 6th and 8th Bar-graph LED pins are configured as Output and only the 2nd LED is turned ON.
The Interrupt Switch is configured as Input and the pull-up resistor for it is activated.
The 6th LED on the Bar-graph is turned ON.
Check whether the Interrupt Switch is pressed or not.
If the Interrupt Switch is pressed, only the 2nd LED will turn OFF and the 8th LED will turn ON.
If the Interrupt Switch is not pressed, the 2nd LED will remain ON and only 8th LED will turn OFF.

EXPECTED OUTPUT
Load the hex file on the Firebird V robot or simulator circuit once your program gets build successfully. Ensure that code performs as expected.
NOTE: Getting Build succeeded output doesn't mean that your program will give the expected output, there can be logical errors.
