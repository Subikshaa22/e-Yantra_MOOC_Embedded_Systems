AIM
In this experiment, you will interface ADC with the micro-controller. The aim of this experiment is to get you familiar with ADC present on Firebird V robot.

ATmega2560 features a 10-bit successive approximation ADC. This built-in ADC is connected to an 16 channel Analog Multiplexer which allows 16 single ended voltage inputs constructed from the pins of Port K and Port F of ATmega2560.

In this experiment, you will interface the White Line and IR Proximity sensors already connected on Firebird V robot. The aim of this experiment is to get you familiar with the configuring and interfacing of these sensors and using the built-in ADC of ATmega2560.

Your task is to get the 8-bit ADC result from the three white line sensors and 3rd, 4th and 5th IR proximity sensors in Single Conversion Mode and display the ADC converted digital values on LCD and send the ADC data of Center White Line sensor on UART Serial Terminal.

The program is provided in a project folder. But, the program contains few incomplete functions related to ADC only which you would have to complete as per the instructions present in the comments. The functions necessary for initialization of LCD and UART are already defined and called in the main() function.

CONNECTIONS
Sensor	Firebird V Interfacing	SimulIDE Interfacing
Left White Line Sensor	PF3 [ ADC Channel 3 ]	PC1 [ ADC Channel 1 ]
Center White Line Sensor	PF2 [ ADC Channel 2 ]	PC0 [ ADC Channel 0 ]
Right White Line Sensor	PF1 [ ADC Channel 1 ]	PC2 [ ADC Channel 2 ]
3rd IR Proximity Sensor	PF6 [ ADC Channel 6 ]	PC3 [ ADC Channel 3 ]
4th IR Proximity Sensor	PF7 [ ADC Channel 7 ]	PC4 [ ADC Channel 4 ]
5th IR Proximity Sensor	PK0 [ ADC Channel 8 ]	PC5 [ ADC Channel 5 ]
MACROS TO USE
In the skeleton code Experiment-1.c, we have included a header file named, firebird_simulation.h which consists of the declaration of the following constants:
#if defined(__AVR_ATmega2560__)

For 3 White Line Sensors:

#define wl_sensors_ddr_reg DDRF

#define wl_sensors_port_reg PORTF

#define left_wl_sensor_pin 3 // PF3

#define left_wl_sensor_channel 3 // ADC3 - ADC Channel 3

#define center_wl_sensor_pin 2 // PF2

#define center_wl_sensor_channel 2 // ADC2 - ADC Channel 2

#define right_wl_sensor_pin 1 // PF1

#define right_wl_sensor_channel 1 // ADC1 - ADC Channel 1

For 3rd and 4th IR proximity Sensors:

#define ir_prox_3_4_sensors_ddr_reg DDRF

#define ir_prox_3_4_sensors_port_reg PORTF

#define ir_prox_3_sensor_pin 6 // PF6

#define ir_prox_3_sensor_channel 6 // ADC6 - ADC Channel 6

#define ir_prox_4_sensor_pin 7 // PF7

#define ir_prox_4_sensor_channel 7 // ADC7 - ADC Channel 7

For 5th IR proximity Sensor:

#define ir_prox_5_sensor_ddr_reg DDRK

#define ir_prox_5_sensor_port_reg PORTK

#define ir_prox_5_sensor_pin 0 // PK0

#define ir_prox_5_sensor_channel 8 // ADC8 - ADC Channel 8


#if defined(__AVR_ATmega328P__)

For 3 White Line Sensors:

#define wl_sensors_ddr_reg DDRC

#define wl_sensors_port_reg PORTC

#define left_wl_sensor_pin 1 // PC3

#define left_wl_sensor_channel 1 // ADC1 - ADC Channel 1

#define center_wl_sensor_pin 0 // PC0

#define center_wl_sensor_channel 0 // ADC0 - ADC Channel 0

#define right_wl_sensor_pin 2 // PC2

#define right_wl_sensor_channel 2 // ADC2 - ADC Channel 2

For 3rd and 4th IR proximity Sensors:

#define ir_prox_3_4_sensors_ddr_reg DDRC

#define ir_prox_3_4_sensors_port_reg PORTC

#define ir_prox_3_sensor_pin 3 // PC3

#define ir_prox_3_sensor_channel 3 // ADC3 - ADC Channel 3

#define ir_prox_4_sensor_pin 4 // PC4

#define ir_prox_4_sensor_channel 4 // ADC4 - ADC Channel 4

For 5th IR proximity Sensor:

#define ir_prox_5_sensor_ddr_reg DDRC

#define ir_prox_5_sensor_port_reg PORTC

#define ir_prox_5_sensor_pin 5 // PC5

#define ir_prox_5_sensor_channel 5 // ADC5 - ADC Channel 5

You have to use these constants declared in firebird_simulation.h and the Masking Operators to complete the Experiment-1.
There are other constants defined for each of the registers and bits associated with ADC in the firebird_simulation.h, you will have to use them for completing the pre-written function stubs while using Masking Operators.
Kindly go through the names of these constants and use them accordingly wherever required.
PROCEDURE
For Windows User (Atmel Studio 7)
Step-1: Download Experiment-1 zip folder. Right-click on the hyperlink and select Save Link As... option to download. Extract the zip file.

Step-2: Open the project Experiment-1.atsln present in the Experiment-1 folder. Start Atmel Studio 7, click on File > Open > Project / Solution and browse for Experiment-1.atsln file to open the project.

Step-3: You will notice some pre-written function stubs in Experiment-1.c included for your assistance. Complete the program as per the instructions present as comments in the C file, Experiment-1.c.

Step-4: After completing the source file i.e. Experiment-1.c, build the project using the shortcut key Ctrl+Alt+F7 or from the Menu bar: Build > Rebuild solution.

Note: Make sure you select Change Device option in Project settings and choose ATmega328P instead of ATmega2560, follow the steps in the gif below for the same.

device_change_microchip_studio
If there are no errors present in your program, the project will get compiled correctly and you will get the message in the Output window as below. Also, Debug folder will be generated in project directory that will contain Experiment-1.hex file along with other build files.


**======== Rebuild All: 1 succeeded, 0 failed, 0 skipped ========**


ALGORITHM
Complete the program as per the instructions present as comments in the C file.

Complete the pre-written functions to achieve the following as per the main function:

Configure only three (Left, Center and Right) white line sensor's and three (3rd, 4th and 5th) IR proximity sensor's pins as Input and deactivate pull-up resistors only for these pins.
Initialize the ADC.
Select the appropriate channel number of each sensor and get the ADC converted data from these sensors into their respective defined variables.
Display the ADC converted data from these sensors on LCD.
Send the ADC data of the Center White Line sensor on UART Serial Terminal.
More Detailed:
Configure the sensor pins as Input and deactivate the pull-up resistors for these pins.

Initialize the ADCSRA, ADCSRB, ADMUX and ACSR registers related to ADC.

Before starting the ADC conversion for a sensor, set / reset the appropriate Channel Selection bits: MUX[5:0] to select corresponding ADC channel.

Start ADC conversion by setting the ADSC bit in ADCSRA register.

Use polling method to check:

ADC Interrupt Flag bit (ADIF) - it updates from 0 to 1 once ADC conversion completes

-- OR --

ADC Start Conversion bit (ADSC) - it updates from 1 to 0 once ADC conversion completes

Read the 8-bit converted data from ADC data registers, ADCL and / or ADCH, depending on whether the ADLAR bit is set or reset in ADCSRA register while initialization.

Reset the ADIF bit, MUX5 bit and MUX[4:0] bits in registers ADCSRA, ADCSRB and ADMUX registers respectively to their default values as configured during the initialization of ADC. This will set the bits of these registers for proper selection of ADC channel for the next conversion. Note: To clear ADIF bit, one must write logical one to the bit.

Repeat the steps from 3, for ADC conversion of next channel.


EXPECTED OUTPUT
Load the hex file on the Firebird V robot or simulator circuit once your program gets build successfully. Ensure that code performs as expected.
NOTE: Getting Build succeeded output doesn't mean that your program will give the expected output, there can be logical errors.
