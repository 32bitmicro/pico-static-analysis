RP2040-LCD-1.28

1. Basic information:

Waveshare RP2040-LCD-1.28 board:

MCU - RP2040
Gyroscope - QMI8658C IMU includes a 3-axis gyroscope and a 3-axis accelerometer
LCD - 1.28inch 240×240 pixels 65K colorful IPS LCD display
Battery Header - MX1.25 header, for 3.7V Lithium battery
ETA6096 - Lithium battery recharge manager
W25Q16JVUXIQ - 2MB NOR-Flash

2. Pin connection:


I2C_SDA     ->      6
I2C_SDA     ->      7
DC          ->      8
CS          ->      9
SCK         ->      10
DIN         ->      11
RST         ->      12  
BL          ->      25
BAT_ADC     ->      29

3. Basic use:

    Copy the compiled uf2 file to pico

4. Directory structure :


lib/Config: This directory is a hardware interface layer file. You can see many definitions in DEV_Config.c(.h), including:
   type of data;
    GPIO;
    Read and write GPIO;
    Delay: Note: This delay function does not use an oscilloscope to measure specific values.
    Module Init and exit processing:
        void DEV_Module_Init(void);
        void DEV_Module_Exit(void);
             
lib/GUI: This directory is some basic image processing functions, in GUI_Paint.c(.h):
    Common image processing: creating graphics, flipping graphics, mirroring graphics, setting pixels, clearing screens, etc.
    Common drawing processing: drawing points, lines, boxes, circles, Chinese characters, English characters, numbers, etc.;
    Common time display: Provide a common display time function;
    Commonly used display pictures: provide a function to display bitmaps;
    
lib/Fonts: for some commonly used fonts:
    Ascii:
        Font8: 5*8
        Font12: 7*12
        Font16: 11*16
        Font20: 14*20
        Font24: 17*24
    Chinese:
        font12CN: 16*21
        font24CN: 32*41
        
lib/LCD: This directory is the LCD driver function;

examples: This directory is the test program of LCD, you can see the specific usage method in it;