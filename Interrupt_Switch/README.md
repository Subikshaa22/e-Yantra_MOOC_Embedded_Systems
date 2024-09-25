AIM
In this experiment, you will turn ON the Buzzer present on the Firebird-V when Interrupt Switch is pressed using the Interrupt Switch. The aim of this experiment is to get you familiar with interrupts on the ATmega2560.

The program is provided in a project folder. But, the program contains few incomplete functions which you would have to complete as per the instructions present in the comments. The functions necessary for initialization of Buzzer, Interrupt Switch and External Interrupt are already called in the main() function.

CONNECTIONS
Device	Firebird V Interfacing	SimulIDE Interfacing
Buzzer	PC3	PD6
Interrupt Switch	PE7	PD2
NOTE: There are two switches present on Firebird-V. One is Reset Switch and the other is Interrupt Switch. In this experiment, we will be using the Interrupt Switch which is connected to an External Interrupt Pin (PE7 / INT7) and hence the name.

MACROS TO USE
In the skeleton code Experiment-1.c, we have included a header file named, firebird_simulation.h which consists of the declaration of the following constants:


#if defined(__AVR_ATmega2560__) 

#define buzzer_ddr_reg						DDRC
#define buzzer_port_reg						PORTC
#define buzzer_pin							3			// PC3

#define interrupt_sw_ddr_reg				DDRE
#define interrupt_sw_port_reg				PORTE
#define interrupt_sw_pin_reg				PINE
#define interrupt_sw_pin					PE7			// PE7

#define interrupt_isr_vect					INT7_vect
#define interrupt_switch_pin				INT7
#define EIMSK_reg							EIMSK
#define EICRB_reg							EICRB
#define interrupt_ISC_switch_bit1			ISC71
#define interrupt_ISC_switch_bit0			ISC70

#define interrupt_switch_pin				INT7
#define EMISK_reg							EIMSK
#define EICRB_reg							EICRB
#define interrupt_ISC_switch_bit1			ISC71
#define interrupt_ISC_switch_bit0			ISC70

#if defined(__AVR_ATmega328P__)

#define buzzer_ddr_reg						DDRD
#define buzzer_port_reg						PORTD
#define buzzer_pin							6			// PD6	( IO6 )

#define interrupt_sw_ddr_reg				DDRD
#define interrupt_sw_port_reg				PORTD
#define interrupt_sw_pin_reg				PIND
#define interrupt_sw_pin					2			// PD2	( IO2 )

#define interrupt_isr_vect					INT0_vect
#define interrupt_switch_pin				INT0
#define EIMSK_reg							EIMSK
#define EICRB_reg							EICRA
#define interrupt_ISC_switch_bit1			ISC01
#define interrupt_ISC_switch_bit0			ISC00

You have to use these constants declared in firebird_simulation.h and the Masking Operators to complete the function stubs in Experiment-1.

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

The function call to buzzer_pin_config initializes the GPIO registers for the pin on which the buzzer is connected.
The function call to interrupt_sw_pin_config initializes the GPIO registers for the pin on which the Interrupt Switch is connected.
The function call to interrupt_sw_config initializes the EIMSK and EICRB registers to configure external interrupt on the Interrupt Switch.
The function call to buzzer_on and buzzer_off turns buzzer pin high and low respectively.

EXPECTED OUTPUT
Load the hex file on the Firebird V robot or simulator circuit once your program gets build successfully. Ensure that code performs as expected.
NOTE: Getting Build succeeded output doesn't mean that your program will give the expected output, there can be logical errors.
