AIM
In this experiment, you will increase and decrease the speed of motors using Phase Correct PWM Mode. The aim of this experiment is to get you familiar with one of the PWM mode available on the ATmega2560.

In this experiment, you will interface the L293D motor driver already connected on Firebird V robot and the Timer connected to the ATmega2560.

The program is provided in a project folder. But, the program contains few incomplete functions which you would have to complete as per the instructions present in the comments. The functions necessary for initialization of the Motors and PWM Mode in the Timer are already defined and called in the main() function.

CONNECTIONS
Motors are connected to the Microcontroller through L293D Motor Driver IC.
Motors Pin	Firebird V Interfacing	SimulIDE Interfacing
RB	PA3	PC3
RF	PA2	PC2
LF	PA1	PC1
LB	PA0	PC0
PWM Pins of the Microcontroller are connected to the L293D Motor Driver IC.
PWM Pin	Firebird V Interfacing	SimulIDE Interfacing
Left Motor	PL3	PD5
Right Motor	PL4	PD6
MACROS TO USE
In the skeleton code Experiment-2.c, firebird_simulation.h which consists of the declaration of the following constants:


#if defined(__AVR_ATmega2560__)

// Motor direction registers and pins
#define		motors_dir_ddr_reg		DDRA
#define		motors_dir_port_reg		PORTA
#define 	motors_RB_pin			PA3		// 3
#define 	motors_RF_pin			PA2		// 2
#define 	motors_LF_pin			PA1		// 1
#define 	motors_LB_pin			PA0		// 0

// Motor enable registers and pins
#define		motors_pwm_ddr_reg		DDRL
#define		motors_pwm_port_reg		PORTL
#define		motors_pwm_R_pin		PL4		// 4
#define		motors_pwm_L_pin		PL3		// 3

// Timer / Counter registers
#define		TCNT5H_reg				TCNT5H	// Timer / Counter 5 High Byte register
#define		TCNT5L_reg				TCNT5L	// Timer / Counter 5 Low Byte register
#define		OCR5AL_reg				OCR5AL	// Output Compare Register 5A Low Byte
#define		OCR5AH_reg				OCR5AH	// Output Compare Register 5A High Byte
#define		OCR5BL_reg				OCR5BL	// Output Compare Register 5B Low Byte
#define		OCR5BH_reg				OCR5BH	// Output Compare Register 5B High Byte
#define		TCCR5A_reg				TCCR5A	// Timer / Counter Control Register 5A
#define		TCCR5B_reg				TCCR5B	// Timer / Counter Control Register 5B

// Bits of compare output mode in the TCCRnA register ( Timer / Counter 'n' Control Register A, where n = 0, 1, 2, 3, 4, 5 )
#define		COMA1_bit			COM5A1	// 7 (Compare Output Mode bit 1 for Channel A)
#define		COMA0_bit			COM5A0	// 6 (Compare Output Mode bit 0 for Channel A)
#define		COMB1_bit			COM5B1	// 5 (Compare Output Mode bit 1 for Channel B)
#define		COMB0_bit			COM5B0	// 4 (Compare Output Mode bit 0 for Channel B)

// Bits of waveform generation mode in the TCCRnA and TCCRnB register ( Timer / Counter 'n' Control Register A/B, where n = 0, 1, 2, 3, 4, 5 )	
#define		WGM0_bit				WGM50	// 0 (Waveform Generation Mode bit 0)
#define		WGM1_bit				WGM51	// 1 (Waveform Generation Mode bit 1)
#define		WGM2_bit				WGM52	// 2 (Waveform Generation Mode bit 2)
#define		WGM3_bit				WGM53	// 3 (Waveform Generation Mode bit 3)

// Bits of clock select mode in the TCCRnB register ( Timer / Counter 'n' Control Register B, where n = 0, 1, 2, 3, 4, 5 )
#define		CS0_bit					CS50	// 0 (Clock Select bit 0)
#define		CS1_bit					CS51	// 1 (Clock Select bit 1)
#define		CS2_bit					CS52	// 2 (Clock Select bit 2)


#if defined(__AVR_ATmega328P__)

// Motor direction registers and pins
#define		motors_dir_ddr_reg		DDRC
#define		motors_dir_port_reg		PORTC
#define 	motors_RB_pin			PC3		// 3
#define 	motors_RF_pin			PC2		// 2
#define 	motors_LF_pin			PC1		// 1
#define 	motors_LB_pin			PC0		// 0

// Motor enable registers and pins
#define		motors_pwm_ddr_reg		DDRD
#define		motors_pwm_port_reg		PORTD
#define		motors_pwm_R_pin		PD6		// 6
#define		motors_pwm_L_pin		PD5		// 5

// Timer / Counter registers
#define		TCNT5H_reg				TCNT0H	// Timer / Counter 5 High Byte register
#define		TCNT5L_reg				TCNT0L	// Timer / Counter 5 Low Byte register
#define		OCR5AL_reg				OCR0AL	// Output Compare Register 5A Low Byte
#define		OCR5AH_reg				OCR0AH	// Output Compare Register 5A High Byte
#define		OCR5BL_reg				OCR0BL	// Output Compare Register 5B Low Byte
#define		OCR5BH_reg				OCR0BH	// Output Compare Register 5B High Byte
#define		TCCR5A_reg				TCCR0A	// Timer / Counter Control Register 5A
#define		TCCR5B_reg				TCCR0B	// Timer / Counter Control Register 5B

// Bits of compare output mode in the TCCRnA register ( Timer / Counter 'n' Control Register A, where n = 0, 1, 2, 3, 4, 5 )
#define		COMA1_bit			COM0A1	// 7 (Compare Output Mode bit 1 for Channel A)
#define		COMA0_bit			COM0A0	// 6 (Compare Output Mode bit 0 for Channel A)
#define		COMB1_bit			COM0B1	// 5 (Compare Output Mode bit 1 for Channel B)
#define		COMB0_bit			COM0B0	// 4 (Compare Output Mode bit 0 for Channel B)

// Bits of waveform generation mode in the TCCRnA and TCCRnB register ( Timer / Counter 'n' Control Register A/B, where n = 0, 1, 2, 3, 4, 5 )	
#define		WGM0_bit				WGM00	// 0 (Waveform Generation Mode bit 0)
#define		WGM1_bit				WGM01	// 1 (Waveform Generation Mode bit 1)
#define		WGM2_bit				WGM02	// 2 (Waveform Generation Mode bit 2)
#define		WGM3_bit				WGM03	// 3 (Waveform Generation Mode bit 3)

// Bits of clock select mode in the TCCRnB register ( Timer / Counter 'n' Control Register B, where n = 0, 1, 2, 3, 4, 5 )
#define		CS0_bit					CS00	// 0 (Clock Select bit 0)
#define		CS1_bit					CS01	// 1 (Clock Select bit 1)
#define		CS2_bit					CS02	// 2 (Clock Select bit 2)

You have to use these constants declared in firebird_simulation.h and the Masking Operators to complete the function stubs in Experiment-2.

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

A variable of type unsigned char named duty_cycle is initialized and assigned to 0;
The function call to pwm_pin_config initializes the GPIO registers for the pins on which the PWM signal will be present.
The function call to timer_pwm_init initializes the OCR5A, OCR5B, TCCR5A and TCCR5B registers of the Timer.
The function call to motors_pin_config initializes the GPIO registers for the pins on which the Motor Driver is connected.
The function call to motors_move_forward sets the appropriate pins connected to the Motor Driver in the configuration to go forward.
In the while loop, the duty cycle is set as the in complement of each other for the left and right motors, it is incremented by one every ten milliseconds.

EXPECTED OUTPUT
Load the hex file on the Firebird V robot or simulator circuit once your program gets build successfully. Ensure that code performs as expected.
NOTE: Getting Build succeeded output doesn't mean that your program will give the expected output, there can be logical errors.
