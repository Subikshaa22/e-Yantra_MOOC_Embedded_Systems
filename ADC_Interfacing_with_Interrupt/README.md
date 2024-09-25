AIM
In this experiment, you will interface ADC with the micro-controller. The aim of this experiment is to get you familiar with ADC present on Firebird V robot.

ATmega2560 features a 10-bit successive approximation ADC. This built-in ADC is connected to an 16 channel Analog Multiplexer which allows 16 single ended voltage inputs constructed from the pins of Port K and Port F of ATmega2560.

In this experiment, you will interface the White Line and IR Proximity sensors already connected on Firebird V robot. The aim of this experiment is to get you familiar with the configuring and interfacing of these sensors and using the built-in ADC of ATmega2560.

Your task is to get the 10-bit ADC result from the 2nd Sharp sensor in Single Conversion Mode using the ADC Conversion Interrupt. Display the ADC data on LCD and send the same to UART Serial Terminal.

The program is provided in a project folder. But, the program contains few incomplete functions which you would have to complete as per the instructions present in the comments. The functions necessary for initialization of LCD and UART are already defined and called in the main() function.

CONNECTIONS
Sensor	Firebird V Interfacing	SimulIDE Interfacing
2nd Sharp Sensor	PK2 [ ADC Channel 10 ]	PC0 [ ADC Channel 0 ]
NOTE: This sensor is not present on Firebird V robot but its header is present. Kindly refer to the section Firebird V: EXPECTED OUTPUT below to know the connections.

MACROS TO USE
In the skeleton code Experiment-2.c, we have included a header file named, firebird_simulation.h which consists of the declaration of the following constants:

For 2nd Sharp Sensor:

#if defined(__AVR_ATmega2560__)

#define sharp_sensor_ddr_reg DDRK

#define sharp_sensor_port_reg PORTK

#define sharp_sensor_pin 2 // PK2

#define sharp_sensor_channel 10 // ADC10 - ADC Channel 10

#if defined(__AVR_ATmega328P__)

#define sharp_sensor_ddr_reg DDRC

#define sharp_sensor_port_reg PORTC

#define sharp_sensor_pin 0 // PK0

#define sharp_sensor_channel 0 // ADC0 - ADC Channel 0

You have to use these constants declared in firebird_simulation.h and the Masking Operators to complete the Experiment-2.

There are other constants defined for each of the registers and bits associated with ADC in the firebird_simulation.h, you will have to use them for completing the pre-written function stubs while using Masking Operators.

Kindly go through the names of these constants and use them accordingly wherever required.

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
Complete the program as per the instructions present as comments in the C file.

Complete the pre-written functions to achieve the following as per the main function:

Configure only 2nd Sharp sensor pin as Input and deactivate pull-up resistors only for this pin.
Initialize the ADC.
Select the appropriate channel number for this sensor and get the ADC converted data from it into the defined variable, sharp_sensor_data.
Display the ADC converted data from this sensor on LCD.
Send the ADC converted data from this sensor on UART Serial Terminal.
More Detailed:
Configure the sensor pin as Input and deactivate the pull-up resistors for this pin.
Initialize the ADCSRA, ADCSRB, ADMUX and ACSR registers related to ADC.
To enable the Interrupt of ADC conversion, make sure to first clear the Global Interrupt Enable bit (I) in SREG register using the cli() function. Then, set the ADIE bit in ADCSRA register to enable the interrupt. Lastly, set the I-bit in SREG register using the sei() function.
Before starting the ADC conversion for a sensor, set / reset the appropriate Channel Selection bits: MUX[5:0] to select corresponding ADC channel.
Start ADC conversion by setting the ADSC bit in ADCSRA register.
Since the interrupt is enabled, the ISR for ADC_vect will be called each time ADC has completed its conversion for the selected channel.
Read the 10-bit converted data from ADC data registers, ADCL and ADCH, depending on whether the ADLAR bit is set or reset in ADCSRA register while initialization (inside the ISR). The ADIF bit will get cleared by itself once the ISR is executed.
Reset the MUX5 bit and MUX[4:0] bits in registers ADCSRA, ADCSRB and ADMUX registers respectively to their default values as configured during the initialization of ADC. This will set the bits of these registers for proper selection of ADC channel for the next conversion (inside the ISR). Note: Make sure that the ISR is as short as possible and there are no delay statements inside ISR.
Repeat the steps from 3, for ADC conversion of next channel.

EXPECTED OUTPUT
Load the hex file on the Firebird V robot or simulator circuit once your program gets build successfully. Ensure that code performs as expected.
NOTE: Getting Build succeeded output doesn't mean that your program will give the expected output, there can be logical errors.
