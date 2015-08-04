# Toxin
// Based on dope information from Jacoby D, implemented by Jonathan Foster(Helix)

// Inspiration:
// Solid 1c dops of either BUBBLGUM or LAWNGR (index/ring LAWNGR, middle/pinky BUBBLGUM) that SHAKE into 2c strobie BUBBLGUM/LAWNGR
// Solid LAWNGR/BUBBLGUM fade over 2 seconds
// Anti's thumbs are basically what im going for(https://youtu.be/IT0zafAwxyI?t=3m15s)
// He can entirely change the focus color of the show even though everything is completely equal is awesome
// LAWNGR__// CC#: 7
// BUBBLGUM// CC#: 19

// Implementation:
// I was able to get dops and strobie, those are public domain information and Ramiro was kind enough to let us know.
// I couldn't find an easy to way to switch between those two colors, I'll work on it and release Toxin2 or something
// The alternates have my version of dops, then we have toxin/outbreak using normal strobie/dops and my dops
// Hope you like it, have an excellent day!
 
 

Mode 1 = LAWNGR index/ring Fingers 1c strobie with 2c dops 
Mode 2 = BUBBLGUM middle/pinky Fingers 1c strobie with 2c dops
Mode 3 = Thumbs

Mode 4 = LAWNGR index/ring Fingers with my version of dops
Mode 5 = BUBBLGUM middle/pinky Fingers with my version of dops
Mode 6 = Thumbs

Mode 7 = Toxin/Outbreak with strobie/dops
Mode 8 = Toxin/Outbreak with my version of dops



Step 1:
	Create a copy of the working OSM_NEO code, File > Save As...
Step 2:
	Replace the whole file with the following code.
Step 3:
	Upload to each of your chips.
Step 4:
	Remember the following things
  	-Dune: “I must not fear. Fear is the mind-killer. Fear is the little-death that brings total obliteration.
    I will face my fear. I will permit it to pass over me and through me. And when it has gone past I will turn
    the inner eye to see its path. Where the fear has gone there will be nothing. Only I will remain.” 
    -Hannah Harto: Practice reckless optimism (It’s the idea that it’s hip and cool to hope for the best
    and try your hardest, even though the odds might be against you.)


####	Toxin Code	####

/*
                                     ____   _____ __  __                     _
                                    / __ \ / ____|  \/  |                   | |
__      ____      ____      __     | |  | | (___ | \  / |       ___ ___   __| | ___  ___
\ \ /\ / /\ \ /\ / /\ \ /\ / /     | |  | |\___ \| |\/| |      / __/ _ \ / _` |/ _ \/ __|
 \ V  V /  \ V  V /  \ V  V /   _  | |__| |____) | |  | |  _  | (_| (_) | (_| |  __/\__ \
  \_/\_/    \_/\_/    \_/\_/   (_)  \____/|_____/|_|  |_| (_)  \___\___/ \__,_|\___||___/

57 65 20 68 61 76 65 20 61 6c 6c 20 74 68 65 20 6c 69 67 68 74 20 77 65 20 6e 65 65 64 2c 20 77 65 20 
6a 75 73 74 20 6e 65 65 64 20 74 6f 20 70 75 74 20 69 74 20 69 6e 20 70 72 61 63 74 69 63 65 2e 0d 0a
/*******************************************************************************
* NEO for the Open Source Microlight
* Version: 1.01
* Date: 08-01-2015
* Company: Quantum Hex LLC
* Author: Ramiro Montes De Oca
* Product Page: http://www.osm.codes
* Support: http://support.osm.codes
*
* This Software is licensed under Creative Commons Attribution-ShareAlike 4.0
*
* Revision  Description
* ========  ===========
* 1.00      Initial public release.
* 1.01      Fix "Deadly Sleep" on some chips causing the chip to die after going to sleep mode.
*           Note: This update needs more optimization but necessary to check the specific issue.
*           Note to self: Proof of self-awareness. Report to Skynet.              
*******************************************************************************/

// Author's Contributions:
// - pwms.ino
// - BPM.ino
// - BUILDERS.ino
// - ColorMode.ino
// - HeartBeat.ino
// - Interrupts.ino
// - modeChange.ino
// - Morphed_Plus.ino
// - OSMserial.ino
// - PRIMES.ino
// - pus.ino
// - pwms.ino
// - SleepMode.ino
// - TripleRainbow.ino
// Quantum Hex LLC / Ramiro Montes De Oca / 2015

/*
THIS CODE IS DISTRIBUTED UNDER CREATIVE COMMONS SHARE ALIKE 4.0
Attribution-ShareAlike 4.0 International (CC BY-SA 4.0)
You are free to:
Share � copy and redistribute the material in any medium or format
Adapt � remix, transform, and build upon the material
for any purpose, even commercially.
The licensor cannot revoke these freedoms as long as you follow the license terms.
Under the following terms:
Attribution � You must give appropriate credit, provide a link to the license, and indicate if changes were made. You may do so in any reasonable manner, but not in any way that suggests the licensor endorses you or your use.
ShareAlike � If you remix, transform, or build upon the material, you must distribute your contributions under the same license as the original.
http://creativecommons.org/licenses/by-sa/4.0/legalcode
Attribution-ShareAlike 4.0 International (CC BY-SA 4.0)


ACKNOWLEDGE:

Modified code out of:
- Reading a serial ASCII-encoded string. / created 13 Apr 2012 / by Tom Igoe (Arduino.cc)
- Serial Event / Created 9 May 2011 / by Tom Igoe (Arduino.cc)
- PWM Frequencies / 02-15-2012 / by yanngg (Arduino.cc)
- Timer interrupts / June 2012 / by Amanda Ghassaei

Libraries:
- <avr/sleep.h>  * Copyright (C) 2006 MacSimski 2006-12-30 / Copyright (C) 2007 D. Cuartielles 2007-07-08 - Mexico DF


///////////////////////////////////////////////////////////////////////////////////
/// WINDOWS CLEAN INSTALLATION ////////////////////////////////////////////////////
///////////////////////////////////////////////////////////////////////////////////

//////////////////////////////////////////////
CHECKLIST:
-Download Programmer's driver:
http://tinyurl.com/ct8uv49

-Download NEO library (OSM_NEOv1-01.zip): 
http://tinyurl.com/njlwnbw

Download Arduino 1.6.1 installer: 
http://tinyurl.com/o2jbl7d
////////////////////////////////////////////

1a) Install the programmer's driver

1b) Install Arduino 1.6.1

2) Open Arduino

3) Install NEO:
Sketch > Import Library... > Add Library ... (select OSM_NEOv1-01.zip)

4) Open NEO:
File > Examples > OSM_NEOv1>_NEOv1-01

5) Set the port:
 Tools > Ports > COMx (select the port of your programmer)

6) Tools > Boards > (Select "Arduino Uno")

7) Sketch > Verify / Compile

8) File > Upload 
If sucess, you will have a message:
Reading | ########(...)################ | 100% 3.22s
avrdude: verifying ...
avrdude: XXXXX bytes of flash verified
avrdude done.  Thank you.

To keep uploading to the rest of the lights:
9) File > Upload 

Instructions:
http://www.osm.codes/neo/OSM_instructions_v1.pdf

If you run with any issue, please describe the just opening a ticket at:
http://support.osm.codes

///////////////////////////////////////////////////////////////////////////////////
/// MAC OSX CLEAN INSTALLATION ////////////////////////////////////////////////////
///////////////////////////////////////////////////////////////////////////////////

//////////////////////////////////////////////
CHECKLIST:

-Download and install the programmer's drivers:
http://tinyurl.com/dc3jzz

-Download Arduino 1.6.1 for Mac
http://tinyurl.com/ntz8ew5

-Download NEO library (OSM_NEOv1-01.zip): 
http://tinyurl.com/njlwnbw
//////////////////////////////////////////////

1) Install on this order( Drivers, Arduino 1.6.1 for Mac)

2) Open Arduino and go to:
Sketch > Import Library > Add Library...
(select OSM_NEOv1-01.zip)

3) Open:
File > Examples > OSM_NEOv1>_NEOv1-01

4) Select the correct port:
Tools > Port > /dev/tty.SLAB_USBtoUART

5) Select the correct board: 
Tools > Board > Arduino Uno

6) Connect the chip, and Compile:
Sketch > Verify / Compile

7) Program the chip:
File > Upload

Done

Repeat from 7) to reprogram the rest of the lights.

Instructions:
http://www.osm.codes/neo/OSM_instructions_v1.pdf

If you run with any issue, please describe the just opening a ticket at:
http://support.osm.codes

////////////////////////////////////////////////////////////////////////////////////


*/


///////////////////////////////////////////////////////////////////////////////////
///////////////////////////////////////////////////////////////////////////////////
/// THE PROGRAM STARTS HERE ///////////////////////////////////////////////////////
///////////////////////////////////////////////////////////////////////////////////


#define VISUAL // COMMENT TO DISABLE VISUAL NAVIAGTION
#define ACCEL_MMA7660 // ACCELEROMETER ENABLED
#define RED      9   // RED LED
#define GREEN    6   // GREEN LED
#define BLUE     5   // BLUE LED
#define BLUE_ARD 13  // BLUE_ARDUINO LED
#define LDO      A3  // LDO ENABLE
#define DEBUG    7   // DEBUG PIN

#include <avr/sleep.h>   // USED FOR SLEEP FUNCITON
#include <Wire.h>        // I2C LIBRARY
#include <EEPROM.h>      // EEPROM READ AND WRITE
#include <avr/pgmspace.h>// MEMORY SAVING LIBRARY
#include <OSM_NEOv1-01.h>   // HIGHJACKED MMA7660 LIBRARY (FOR BETTER ORGANIZATION)

#define NOP __asm__ __volatile__ ("nop\n\t") // AND THIS IS HOW YOU DEFINE A "NOP" ON ARDUINO AVR

//// SETTING VARIABLES

volatile boolean MODERESET_FLAG = 0;             // RESET FLAG
volatile boolean AllYourBaseAreBelongToUs = 0;   
volatile byte CurrentOffCounter = 0;             
volatile int long TTtime;
volatile boolean Preview[2];
volatile boolean Armed = 1;
volatile boolean GLOBALCHANGE;
volatile int long RoundResult;
volatile float FloatResult;
volatile boolean AUTOCHANGE;
volatile int long BPM_Counter;
volatile int long BPM_Factor;
volatile byte PrimeA;
volatile byte PrimeB;
volatile byte MMAselect;
volatile  byte mmAxis;
volatile byte SenseY;
volatile int Sensitivity;
volatile byte PMMAselect;
volatile byte PmmAxis;
volatile int PAccelSensitivity;
volatile int ColorTime[2];
volatile int BlankTime[2];
volatile byte PrimeType[2];
volatile byte MaxPrimeColors[2];
volatile boolean TipUp;
volatile boolean TiltRight;
volatile boolean UpsideUp;
byte AccTilt;
int accelCounter;
boolean accShake;
volatile byte MemCheck;
int ColorTimeA, BlankTimeA, ColorTimeB,  BlankTimeB;
volatile byte ThisLimit;
volatile boolean Zflipped = 0;
int ThisTime;
volatile boolean SANDBOX = 1;
volatile bool ZEROCOLOR;
volatile byte CurrentMode; 
volatile bool DeleteColor = 0;
boolean FirstPrintFlag = 1;
String inputString = "";         // a string to hold incoming data
boolean stringComplete = false;  // whether the string is complete
int xAcc, yAcc, zAcc;
int EEplus;
int PROGMEMbank;
byte PROGset;
int eeRead;
int Daddress;
int Dvalue;
int ClearCountStart;
int ClearCountEnds;
int ClearCount;
int EEbank;
byte ValueCount;
int ek;
int uuu; 
int kk;
int k;// 
char myChar;
byte CC;
byte CCSET;
byte CR;
byte CG;
byte CB;
volatile boolean shadeFlag = 0;
int shTime;
volatile boolean ONNS = 1;
volatile byte CSHADE = 0;
volatile int time;
volatile byte shade;
volatile byte CCR[2][9];
volatile byte CCG[2][9];
volatile byte CCB[2][9];
volatile byte CCS[2][9];
volatile int CCT[2][9]; // NOT USED?
volatile byte colorSet;
volatile byte color;
volatile const byte BUTTON = 2; // Push Button on Digital Pin 2
byte VariationOffset;
volatile byte VARIATION = 0; // Used @ magnetometer.ino, modes.ino, OSMserial.ino
volatile int offyMinus;
volatile int offyPlus;
volatile boolean MASTER = 0; // SERIAL MASTER ( 1 = TRUE ) IF MASTER INVERT TX/RX CONNECTIONS - ONLY ONE MASTER ALLOWED
volatile boolean JUSTONCE; // WILL RUN ROUTINE ONLY ONCE
volatile boolean ONLYUNO; // WILL RUN ROUTINE ONLY ONCE
volatile boolean JUSTONCECHANGE;
volatile int MixCounter;
volatile byte STATE = 1; 
volatile boolean COLORCHANGE_FLAG = 0;
volatile byte WhatDmode;
unsigned int displayInt;
volatile boolean VirtualPreview = 0;
// TIMER2 INTERRUPT @ 61HZ / 16.40ms
volatile int long Int0count = 0; // Used on INT0
volatile int long Int0countNEG = 0; // Used on INT0
volatile bool Pushed = 0;  // Used on INT0
volatile bool Click = 0;  // Used on INT0
volatile bool OFF_MODE = 0;  // Used on INT0
volatile bool ToBorNotToB = 0;  // Used on INT0
volatile byte BlinkyCount = 0;
volatile boolean DoubleClick; // Used on Timer2 Interrupt
volatile boolean ONCE_RESET_COLOR_MODES = 1;
volatile boolean ONCE_SETUP_COLOR = 1;
volatile boolean ONCE_SAVE_COLOR = 0;
volatile byte CurrentColor = 1;
byte MaxSaved;
volatile int ShadeSet;
volatile byte ShaderFactor;
volatile int ColorSelection;// void TheLoop
volatile int ValueToRead;
// modeChange.ino
volatile byte ColorMaxCount[2];
volatile byte RRmode;
volatile byte cOLORcount;
volatile byte ColorToSet;
volatile byte mathEE_1;
volatile byte mathEE_2;
volatile byte ModeToChange;
volatile int sred;
volatile int sgreen;
volatile int sblue;
volatile boolean SaveDaColor = 0; // interrupts
volatile byte ColorToSave = 0;
volatile boolean COLOR_NAV = 1;
volatile boolean SaveDmode = 0;
volatile byte PrintMaster=0;
volatile byte AsteriscMaster=0;
int ModeMult;
volatile int Val1A;
volatile int Val2A;
volatile int Val1B;
volatile int Val2B;
volatile int Val1[2];
volatile int Val2[2];
volatile byte AccelSensitivity;
volatile byte Axis;
volatile byte ModeSetSRAM [13][36]; // SRAM Space
volatile byte ModeSwap [5] [24];
#if defined(VISUAL)
const PROGMEM char osmCC_flahs_names[] ={"BLANK___/RED_____/SUNSET__/ORANGE__/YELLOW__/LEMON___/CHARTRE_/LAWNGR__/GCAMOL__/GREEN___/IXTAPA__/AQUA____/EBLUE___/CYAN____/JADE____/SKYBLUE_/AZURE___/BLUE____/GRAPE___/BUBBLGUM/MAGENTA_/PINK____/HOT_PINK/DEEP_PNK/FUSCIA__/ALLWIHTE/FIXWHITE/GRNWHITE/BLUWHITE/SFTPINK_/GHSTBLUE/GHSTGRN_/GHSTRED_/"};
#endif



//////////////////////////////////////////////////////////////////////////////////////////////
//// CUSTOM COLORS /// CUSTOM COLORS /// CUSTOM COLORS /// CUSTOM COLORS /// CUSTOM COLORS /// 
//////////////////////////////////////////////////////////////////////////////////////////////

const PROGMEM  uint8_t osmCC_PROGMEM[2][99]  =  
{/// const osmCC_PROGMEM
			//////////  COLOR PALLETTE #0	
			{
0, 0 , 0,    // Color # 0

139 , 0 , 0,   //  Color #1
255 , 63 , 0,   //  Color #2
255 , 127 , 0,   //  Color #3
255 , 191 , 0,   //  Color #4
255 , 255 , 0,   //  Color #5
191 , 255 , 0,   //  Color #6
127 , 255 , 0,   //  Color #7
63 , 255 , 0,   //  Color #8


0 , 255 , 0,   //  Color #9
0 , 255 , 63,   //  Color #10
0 , 255 , 127,   //  Color #11
0 , 255 , 191,   //  Color #12
0 , 255 , 255,   //  Color #13
0 , 191 , 255,   //  Color #14
0 , 127 , 255,   //  Color #15
0 , 63 , 255,   //  Color #16


0 , 0 , 255,   //  Color #17
63 , 0 , 255,   //  Color #18
127 , 0 , 255,   //  Color #19
191 , 0 , 255,   //  Color #20
255 , 0 , 255,   //  Color #21
255 , 0 , 191,   //  Color #22
255 , 0 , 127,   //  Color #23
255 , 0 , 63,   //  Color #24

255 , 255 , 255,   //  Color #25
170 , 255 , 255,    //  Color #26
172 , 241 , 255,   //  Color #27
85 , 96 , 241,   //  Color #28
57 , 0, 23,   //  Color #29
0 , 0 , 6,   //  Color #30
0 , 6 , 0,   //  Color #31
6 , 0 , 0   //  Color #32

			},
			////////////////////////////////////

			//////////  COLOR PALLETTE #1 //////	
			{
0, 0 , 0,    // Color # 0

255 , 0 , 0,   //  Color #1
255 , 63 , 0,   //  Color #2
255 , 127 , 0,   //  Color #3
255 , 191 , 0,   //  Color #4
255 , 255 , 0,   //  Color #5
191 , 255 , 0,   //  Color #6
127 , 255 , 0,   //  Color #7
63 , 255 , 0,   //  Color #8


0 , 255 , 0,   //  Color #9
0 , 255 , 63,   //  Color #10
0 , 255 , 127,   //  Color #11
0 , 255 , 191,   //  Color #12
0 , 255 , 255,   //  Color #13
0 , 191 , 255,   //  Color #14
0 , 127 , 255,   //  Color #15
0 , 63 , 255,   //  Color #16


0 , 0 , 255,   //  Color #17
63 , 0 , 255,   //  Color #18
127 , 0 , 255,   //  Color #19
191 , 0 , 255,   //  Color #20
255 , 0 , 255,   //  Color #21
255 , 0 , 191,   //  Color #22
255 , 0 , 127,   //  Color #23
255 , 0 , 63,   //  Color #24

255 , 255 , 255,   //  Color #25
170 , 255 , 255,    //  Color #26
172 , 241 , 255,   //  Color #27
85 , 96 , 241,   //  Color #28
57 , 0, 23,   //  Color #29
0 , 0 , 6,   //  Color #30
0 , 6 , 0,   //  Color #31
6 , 0 , 0   //  Color #32
			},
			////////////////////////////////////
//

	
 };/// tsnoc osmCC_PROGMEM
 
//////////////////////////////////////////////////////////////////////////////////////////////
//// CUSTOM COLORS /// CUSTOM COLORS /// CUSTOM COLORS /// CUSTOM COLORS /// CUSTOM COLORS /// 
//////////////////////////////////////////////////////////////////////////////////////////////



//volatile  byte CurrentVersion = 212;// CHANGE THIS NUMBER IF YOU WANT TO SAVE A NEW FACTORY DEFAULT


		
// the setup function runs once when you press reset or power the board
void setup()
{ // void setup
			
	OSMsetup();       // Sets I/O @ setup.ino
	TimerMax();       // Sets Timers @ setup.ino
	digitalWrite(DEBUG, HIGH);
	attachInterrupt(0, pushInterrupt, FALLING); // Interrupt on Push Button (Digital 2)
	SerialSetup();    // Sets Serial i/o @ setup.ino
	
	      set_sleep_mode(SLEEP_MODE_PWR_DOWN);
		  
	MMA7660.init();                              
	PrintWelcome1(); // This is the welcome intro for the Serial Communication
		eepromWriteFactory();// Factory Reset (if)
		eepromLoad();// Load EEPROM to SRAM
	PrintWelcome2();
	AnalogBlank(); // turn off LED
	STATE = 1;
	VARIATION = 0;
    digitalWrite(LDO, HIGH); // Power LDO
    digitalWrite(DEBUG, LOW);
	
//DumpEEprom(); // FOR DEBUG
//DumpSRAM();   // FOR DEBUG

}// diov setup

long randNumber;
volatile boolean RandomYes;
volatile int RandomValue;

volatile boolean OgooD;
volatile byte CurrentUserBundle = 0;
volatile byte CurrentUserMode = 1;
volatile byte BPM_Selector;


////////////////////////////////////////////////////////////////////////////////////////////////////////////////
//// CURRENT VERSION  //// CURRENT VERSION  //// CURRENT VERSION  //// CURRENT VERSION  //// CURRENT VERSION ///
volatile  byte CurrentVersion = 115;         // CHANGE THIS NUMBER IF YOU WANT TO SAVE A NEW FACTORY DEFAULT ///
//// CURRENT VERSION  //// CURRENT VERSION  //// CURRENT VERSION  //// CURRENT VERSION  //// CURRENT VERSION ///
////////////////////////////////////////////////////////////////////////////////////////////////////////////////


////////////////////////////////////////////////////////////////////////////////////////////////
//// COLOR MODES  //// COLOR MODES  //// COLOR MODES  //// COLOR MODES  //// COLOR MODES  //////
////////////////////////////////////////////////////////////////////////////////////////////////
const PROGMEM  uint8_t ModeSetFLASH [13][36]= // FACTORY DEFAULT
{
1,1,  7,0,  19,0,  0,0,  0,0,  0,0,  0,0,  0,0,  0,0,   	// Mode 1  // Prime A -Fingers LAWNGR index/ring
2,1,  7,0,  19,0,  0,0,  0,0,  0,0,  0,0,  0,0,  0,0,		// Mode 1  // Prime B -Fingers index/ring


1,1,  19,0,  0,0,  0,0,  0,0,  0,0,  0,0,  0,0,  0,0,    	// Mode 2  // Prime A -Fingers BUBBLGUM middle/pinky
2,1,  7,0,  19,0,  0,0,  0,0,  0,0,  0,0,  0,0,  0,0,		// Mode 3  // Prime B -Fingers middle/pinky


4,1,  7,0,  7,0,  19,0,  19,0,  0,0,  0,0,  0,0,  0,0,    	// Mode 3  // Prime A -Thumbs
0,0,  0,0,  0,0,  0,0,  0,0,  0,0,  0,0,  0,0,  0,0,		// Mode 3  // Prime B -Unused

1,1,  7,0,  0,0,  0,0,  0,0,  0,0,  0,0,  0,0,  0,0,    	// Mode 4   // Prime A -Alt-Fingers LAWNGR index/ring
2,1,  7,0,  19,0,  0,0,  0,0,  0,0,  0,0,  0,0,  0,0,		// Mode 4   // Prime B -Alt-Fingers index/ring


1,1,  19,0,  0,0,  0,0,  0,0,  0,0,  0,0,  0,0,  0,0,    	// Mode 5  // Prime A -Alt-Fingers BUBBLGUM index/ring
2,1,  7,0,  19,0,  0,0,  0,0,  0,0,  0,0,  0,0,  0,0,		// Mode 5  // Prime B -Alt-Fingers index/ring


2,1,  7,0,  19,0,  0,0,  0,0,  0,0,  0,0,  0,0,  0,0,    	// Mode 6  // Prime A -Alt-Thumbs 
8,1,  7,0,  7,2,  7,2,  7,2,  19,0,  19,2,  19,2,  19,0,	// Mode 6  // Prime B -Alt-Thumbs	LAWNGR, low LAWNGR, low LAWNGR, LAWNGR, BUBBLGUM, low BUBBLGUM, low BUBBLGUM, BUBBLGUM


8,1,  7,0,  7,2,  7,0,  7,1,  7,0,  7,2,  7,0,  19,0,    	// Mode 7  // Prime A -Toxin		LAWNGR, low LAWNGR, LAWNGR, mid LAWNGR, LAWNGR, low LAWNGR, BUBBLGUM
8,1,  7,0,  7,2,  7,2,  7,2,  19,0,  19,2,  19,3,  19,0,	// Mode 7  // Prime B -Outbreak		LAWNGR, low LAWNGR, low LAWNGR, lowest LAWNGR, BUBBLGUM, low BUBBLGUM, lowest BUBBLGUM, BUBBLGUM

8,1,  7,0,  7,2,  7,0,  7,1,  7,0,  7,2,  7,0,  19,0,    	// Mode 8  // Prime A -Toxin		LAWNGR, low LAWNGR, LAWNGR, mid LAWNGR, LAWNGR, low LAWNGR, BUBBLGUM
8,1,  7,0,  7,2,  7,2,  7,2,  19,0,  19,2,  19,3,  19,0,	// Mode 8  // Prime B -Outbreak		LAWNGR, low LAWNGR, low LAWNGR, lowest LAWNGR, BUBBLGUM, low BUBBLGUM, lowest BUBBLGUM, BUBBLGUM


1,1,    0,0,  0,0,  0,0,  0,0,  0,0,  0,0,  0,0,  0,17,   // Mode 9 // Prime A
1,1,    0,0,  0,0,  0,0,  0,0,  0,0,  0,0,  0,0,  0,18,   // Mode 9 // Prime B

4,1,    1,0,  9,0,  21,0,  5,0,  11,0,  3,0,  17,0,  22,19,   // Mode 10 // Prime A
3,1,    1,0,  9,0,  21,0,  5,0,  11,0,  3,0,  17,0,  22,20,    // Mode 10 // Prime B

3,1,  9,0,  1,3,  23,0,  0,0,  0,0,  0,0,  0,0,  0,21,    // Mode 11  // Prime A
4,1,  11,0,  24,0,  3,0,  0,0,  0,0,  0,0,  0,0,  0,22,    // Mode 11  // Prime B

4,1,    1,0,  9,0,  21,0,  5,0,  11,0,  3,0,  17,0,  22,23,   // Mode 12 // Prime A
4,1,    1,0,  9,0,  21,0,  5,0,  11,0,  3,0,  17,0,  22,24,   // Mode 12 // Prime B

1,1,    0,0,  0,0,  0,0,  0,0,  0,0,  0,0,  0,0,  0,25,   // Mode 13 // Prime A // RESERVED
1,1,    0,0,  0,0,  0,0,  0,0,  0,0,  0,0,  0,0,  0,26   // Mode 13 // Prime B // RESERVED

};
////////////////////////////////////////////////////////////////////////////////////////////////
//// COLOR MODES  //// COLOR MODES  //// COLOR MODES  //// COLOR MODES  //// COLOR MODES  //////
////////////////////////////////////////////////////////////////////////////////////////////////



////////////////////////////////////////////////////////////////////////////////////////////////
//// BUNLDES //// BUNLDES //// BUNLDES //// BUNLDES //// BUNLDES //// BUNLDES //// BUNLDES /////
////////////////////////////////////////////////////////////////////////////////////////////////
volatile byte UserCmodes[5][14] = // USE: UserCmodes[CurrentUserBundle][CurrentUserMode];
{// byte UserCmodes
	
	
  12,   1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 0, // Bundle 1
  
  12,  2, 4, 1, 3, 5, 6, 7, 8, 9, 10, 11, 12, 0, // Bundle 2

  3,   1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 0, // Bundle 3

  1,   2, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 0, // Bundle 4
  
  5,   1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 0 // Bundle 5
      	
}; // etyb UserCmodes
////////////////////////////////////////////////////////////////////////////////////////////////
//// BUNLDES //// BUNLDES //// BUNLDES //// BUNLDES //// BUNLDES //// BUNLDES //// BUNLDES /////
////////////////////////////////////////////////////////////////////////////////////////////////



////////////////////////////////////////////////////////////////////////////////////////////////
//// BPM AUTO CHANGE ///// BPM AUTO CHANGE ///// BPM AUTO CHANGE ///// BPM AUTO CHANGE /////////
////////////////////////////////////////////////////////////////////////////////////////////////
volatile byte UserBPM[10] =
{
	0,0,        // AUTOCHANGE BPM BUNDLE 1 (0=No, 1=Yes) / BPM 1-255
	0,0,        // AUTOCHANGE BPM BUNDLE 2 (0=No, 1=Yes) / BPM 1-255
	0,0,        // AUTOCHANGE BPM BUNDLE 3 (0=No, 1=Yes) / BPM 1-255
	0,0,        // AUTOCHANGE BPM BUNDLE 4 (0=No, 1=Yes) / BPM 1-255
	1,120,      // AUTOCHANGE BPM BUNDLE 5 (0=No, 1=Yes) / BPM 1-255
} ;
////////////////////////////////////////////////////////////////////////////////////////////////
//// BPM AUTO CHANGE ///// BPM AUTO CHANGE ///// BPM AUTO CHANGE ///// BPM AUTO CHANGE /////////
////////////////////////////////////////////////////////////////////////////////////////////////





volatile byte MaxUserModes = UserCmodes[0][0]; 
volatile byte Mode = UserCmodes[0][1];


void loop()
{ // void Loop



//while (1)// Uncomment and compile for Color Processing 
//{
 //ProcessingRGB();
//}


//////    MODE  0      //////////////////////////////////////////////////////////////////////
JUSTONCE = 1; GLOBALCHANGE = 1;
while (Mode == 0 )
{ // while 0
	Mode_00(); // modes.ino
}// elihw 0
//////    MODE  0      /////////////////////////////////////////////////////////////////////

    
//////    MODE1		//////////////////////////////////////////////////////////////////////////////////////////////////////
	JUSTONCE = 1; GLOBALCHANGE = 1;
	while (Mode == 1 && GLOBALCHANGE )// Mode
	{ //while mode
	//                 				(//-ACCEL SETTINGS-//----PRIME A SETTINGS----//----PRIME B SETTINGS----//)
	osm_MASTER_BUILDER	(	2,		0,		100,			1,  1.5,  10,		0,	0,	0,			1,  3,  23,	0,	0,	0	 	 ) ; } ;
//////    MODE		//////////////////////////////////////////////////////////////////////////////////////////////////////


//////    MODE2		//////////////////////////////////////////////////////////////////////////////////////////////////////
	JUSTONCE = 1; GLOBALCHANGE = 1;
	while (Mode == 2 && GLOBALCHANGE )// Mode
	{ //while mode
	//                 				(//-ACCEL SETTINGS-//----PRIME A SETTINGS----//----PRIME B SETTINGS----//)
	osm_MASTER_BUILDER	(	2,		0,		100,			1,  1.5,  10,		0,	0,	0,			1,  3,  23,	0,	0,	0	 	 ) ; } ;
//////    MODE		//////////////////////////////////////////////////////////////////////////////////////////////////////

//////    MODE3		//////////////////////////////////////////////////////////////////////////////////////////////////////
	JUSTONCE = 1; GLOBALCHANGE = 1;
	while (Mode == 3 && GLOBALCHANGE )// Mode
	{ //while mode
	//                 				(//-ACCEL SETTINGS-//----PRIME A SETTINGS----//----PRIME B SETTINGS----//)
	osm_MASTER_BUILDER	(	0,		0,		100,			1,  750,  0,		0,	0,	0,			0,  0,  0,	0,	0,	0	 	 ) ; } ;
//////    MODE		//////////////////////////////////////////////////////////////////////////////////////////////////////


//////    MODE4		//////////////////////////////////////////////////////////////////////////////////////////////////////
	JUSTONCE = 1; GLOBALCHANGE = 1;
	while (Mode == 4 && GLOBALCHANGE )// Mode
	{ //while mode
	//                 				(//-ACCEL SETTINGS-//----PRIME A SETTINGS----//----PRIME B SETTINGS----//)
	osm_MASTER_BUILDER	(	2,		0,		100,			1,  6,  10,		0,	0,	0,			1,  9,  10,	0,	0,	0	 	 ) ; } ;
//////    MODE		//////////////////////////////////////////////////////////////////////////////////////////////////////


//////    MODE5		//////////////////////////////////////////////////////////////////////////////////////////////////////
	JUSTONCE = 1; GLOBALCHANGE = 1;
	while (Mode == 5 && GLOBALCHANGE )// Mode
	{ //while mode
	//                 				(//-ACCEL SETTINGS-//----PRIME A SETTINGS----//----PRIME B SETTINGS----//)
	osm_MASTER_BUILDER	(	2,		0,		100,			1,  6,  10,		0,	0,	0,			1,  9,  10,	0,	0,	0	 	 ) ; } ;
//////    MODE		//////////////////////////////////////////////////////////////////////////////////////////////////////



//////    MODE6		//////////////////////////////////////////////////////////////////////////////////////////////////////
	JUSTONCE = 1; GLOBALCHANGE = 1;
	while (Mode == 6 && GLOBALCHANGE )// Mode
	{ //while mode
	//                 				(//-ACCEL SETTINGS-//----PRIME A SETTINGS----//----PRIME B SETTINGS----//)
	osm_MASTER_BUILDER	(	2,		0,		500,			1,  375,  0,		0,	0,	0,			1,  2,  3,	0,	0,	0	 	 ) ; } ;
//////    MODE		//////////////////////////////////////////////////////////////////////////////////////////////////////


//////    MODE7		//////////////////////////////////////////////////////////////////////////////////////////////////////
	JUSTONCE = 1; GLOBALCHANGE = 1;
	while (Mode == 7 && GLOBALCHANGE )// Mode
	{ //while mode
	//                 				(//-ACCEL SETTINGS-//----PRIME A SETTINGS----//----PRIME B SETTINGS----//)
	osm_MASTER_BUILDER	(	2,		0,		500,			1,  1.5,  10,		0,	0,	0,			1,  3,  23,	0,	0,	0	 	 ) ; } ;
//////    MODE		//////////////////////////////////////////////////////////////////////////////////////////////////////


//////    MODE8		//////////////////////////////////////////////////////////////////////////////////////////////////////
	JUSTONCE = 1; GLOBALCHANGE = 1;
	while (Mode == 8 && GLOBALCHANGE )// Mode
	{ //while mode
	//                 				(//-ACCEL SETTINGS-//----PRIME A SETTINGS----//----PRIME B SETTINGS----//)
	osm_MASTER_BUILDER	(	2,		0,		500,			1,  6,  10,		0,	0,	0,			1,  6,  3,	0,	0,	0	         ) ; } ;
//////    MODE		//////////////////////////////////////////////////////////////////////////////////////////////////////


//////    MODE     //////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
JUSTONCE = 1; GLOBALCHANGE = 1;
while (Mode == 9 && GLOBALCHANGE )// Mode
{ //while mode
//                 (//------------ACCEL SETTINGS--------//-----------------PRIME A  SETTINGS------------------//-----------------PRIME A  SETTINGS------------------//)
osm_MASTER_BUILDER (      1,       0,        50,               5,       3,         8,        1,    357,    1,         1,       5,         10,       0,    0,    0     ) ;
//                 (  Acc_Select  Axis  AccSensitivity  //  PrimeA  ColorTimeA  BlankTimeA   E1A   E2A   VPB  //  PrimeB  ColorTimeB  BlankTimeB   E1B   E2B   VPB  //) ;
//// Accelerometer:
//// 0 = No_Accelerometer
//// 1 = Tilt
//// 2 = Shake
////
//// Axis: (Available only for Tilt option)
//// 0 = X
//// 1 = Y
//// 2 = Z
////
//// AccSensitivity: 100 Default (1 to 32000)
////
//// PRIME A/B:
//// 1 = Strobe        :  ColorTime(A/B): Time in Milliseconds // BlankTime(A/B): Time in Milliseconds // Extra1(A/B) = N/A                    //  Extra2(A/B) = N/A
//// 2 = Trace         :  ColorTime(A/B): Time in Milliseconds // BlankTime(A/B): Time in Milliseconds // Extra1(A/B) = N/A                    //  Extra2(A/B) = N/A
//// 3 = Morph         :  ColorTime(A/B): Time in Milliseconds // BlankTime(A/B): Time in Milliseconds // Extra1(A/B) = Long Blank Time        //  Extra2(A/B) = N/A
//// 4 = PULSE         :  ColorTime(A/B): Time in Milliseconds // BlankTime(A/B): Time in Milliseconds // Extra1(A/B) = Random?(1=Yes,0=No)    //  Extra2(A/B) = Random Max Value (1-32000)
//// 5 = Triple Rainbow:  ColorTime(A/B): Time in Milliseconds // BlankTime(A/B): Time in Milliseconds // Extra1(A/B) = # of Rainbows (1 to 3) //  Extra2(A/B) = Number of Colors (1-32000)
//// 6 = HeartBeat     :  ColorTime(A/B): Time in Milliseconds // BlankTime(A/B): Time in Milliseconds // Extra1(A/B) = BPM                    //  Extra2(A/B) = N/A
//// 7-12 = Sandbox(1-6 Extra Settings) :  Custom
////
//// VP (Virtual Color Preview)
//// 0 = NO
//// 1 = YES
///////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
}// elihw mode
//////    MODE     ///////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////



//////    MODE     //////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
JUSTONCE = 1; GLOBALCHANGE = 1;
while (Mode == 10 && GLOBALCHANGE )// Mode
{ //while mode
//                 (//------------ACCEL SETTINGS--------//-----------------PRIME A  SETTINGS------------------//-----------------PRIME A  SETTINGS------------------//)
osm_MASTER_BUILDER (      2,       1,        100,              3,       10,         10,       0,    0,    0,         8,       5,         8,         0,    0,    1     ) ;
//                 (  Acc_Select  Axis  AccSensitivity  //  PrimeA  ColorTimeA  BlankTimeA   E1A   E2A   VPB  //  PrimeB  ColorTimeB  BlankTimeB   E1B   E2B   VPB  //) ;
//// Accelerometer:
//// 0 = No_Accelerometer
//// 1 = Tilt
//// 2 = Shake
////
//// Axis: (Available only for Tilt option)
//// 0 = X
//// 1 = Y
//// 2 = Z
////
//// AccSensitivity: 100 Default (1 to 32000)
////
//// PRIME A/B:
//// 1 = Strobe        :  ColorTime(A/B): Time in Milliseconds // BlankTime(A/B): Time in Milliseconds // Extra1(A/B) = N/A                    //  Extra2(A/B) = N/A
//// 2 = Trace         :  ColorTime(A/B): Time in Milliseconds // BlankTime(A/B): Time in Milliseconds // Extra1(A/B) = N/A                    //  Extra2(A/B) = N/A
//// 3 = Morph         :  ColorTime(A/B): Time in Milliseconds // BlankTime(A/B): Time in Milliseconds // Extra1(A/B) = Long Blank Time        //  Extra2(A/B) = N/A
//// 4 = PULSE         :  ColorTime(A/B): Time in Milliseconds // BlankTime(A/B): Time in Milliseconds // Extra1(A/B) = Random?(1=Yes,0=No)    //  Extra2(A/B) = Random Max Value (1-32000)
//// 5 = Triple Rainbow:  ColorTime(A/B): Time in Milliseconds // BlankTime(A/B): Time in Milliseconds // Extra1(A/B) = # of Rainbows (1 to 3) //  Extra2(A/B) = Number of Colors (1-32000)
//// 6 = HeartBeat     :  ColorTime(A/B): Time in Milliseconds // BlankTime(A/B): Time in Milliseconds // Extra1(A/B) = BPM                    //  Extra2(A/B) = N/A
//// 7-12 = Sandbox(1-6 Extra Settings) :  Custom
////
//// VP (Virtual Color Preview)
//// 0 = NO
//// 1 = YES
///////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
}// elihw mode
//////    MODE     ///////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////



//////    MODE     //////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
JUSTONCE = 1; GLOBALCHANGE = 1;
while (Mode == 11 && GLOBALCHANGE )// Mode
{ //while mode
//                 (//------------ACCEL SETTINGS--------//-----------------PRIME A  SETTINGS------------------//-----------------PRIME A  SETTINGS------------------//)
osm_MASTER_BUILDER (      1,       2,        100,             10,       5,         12,        3,    0,    0,        10,       8,         12,        2,    0,    0     ) ;
//                 (  Acc_Select  Axis  AccSensitivity  //  PrimeA  ColorTimeA  BlankTimeA   E1A   E2A   VPB  //  PrimeB  ColorTimeB  BlankTimeB   E1B   E2B   VPB  //) ;
//// Accelerometer:
//// 0 = No_Accelerometer
//// 1 = Tilt
//// 2 = Shake
////
//// Axis: (Available only for Tilt option)
//// 0 = X
//// 1 = Y
//// 2 = Z
////
//// AccSensitivity: 100 Default (1 to 32000)
////
//// PRIME A/B:
//// 1 = Strobe        :  ColorTime(A/B): Time in Milliseconds // BlankTime(A/B): Time in Milliseconds // Extra1(A/B) = N/A                    //  Extra2(A/B) = N/A
//// 2 = Trace         :  ColorTime(A/B): Time in Milliseconds // BlankTime(A/B): Time in Milliseconds // Extra1(A/B) = N/A                    //  Extra2(A/B) = N/A
//// 3 = Morph         :  ColorTime(A/B): Time in Milliseconds // BlankTime(A/B): Time in Milliseconds // Extra1(A/B) = Long Blank Time        //  Extra2(A/B) = N/A
//// 4 = PULSE         :  ColorTime(A/B): Time in Milliseconds // BlankTime(A/B): Time in Milliseconds // Extra1(A/B) = Random?(1=Yes,0=No)    //  Extra2(A/B) = Random Max Value (1-32000)
//// 5 = Triple Rainbow:  ColorTime(A/B): Time in Milliseconds // BlankTime(A/B): Time in Milliseconds // Extra1(A/B) = # of Rainbows (1 to 3) //  Extra2(A/B) = Number of Colors (1-32000)
//// 6 = HeartBeat     :  ColorTime(A/B): Time in Milliseconds // BlankTime(A/B): Time in Milliseconds // Extra1(A/B) = BPM                    //  Extra2(A/B) = N/A
//// 7-12 = Sandbox(1-6 Extra Settings) :  Custom
////
//// VP (Virtual Color Preview)
//// 0 = NO
//// 1 = YES
///////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
}// elihw mode
//////    MODE     ///////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////



//////    MODE     //////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
JUSTONCE = 1; GLOBALCHANGE = 1;
while (Mode == 12 && GLOBALCHANGE )// Mode
{ //while mode
//                 (//------------ACCEL SETTINGS--------//-----------------PRIME A  SETTINGS------------------//-----------------PRIME A  SETTINGS------------------//)
osm_MASTER_BUILDER (      1,       2,        100,              1,       5,         10,        0,    0,    1,         1,       5,         10,        0,    0,    1     ) ;
//                 (  Acc_Select  Axis  AccSensitivity  //  PrimeA  ColorTimeA  BlankTimeA   E1A   E2A   VPB  //  PrimeB  ColorTimeB  BlankTimeB   E1B   E2B   VPB  //) ;
//// Accelerometer:
//// 0 = No_Accelerometer
//// 1 = Tilt
//// 2 = Shake
////
//// Axis: (Available only for Tilt option)
//// 0 = X
//// 1 = Y
//// 2 = Z
////
//// AccSensitivity: 100 Default (1 to 32000)
////
//// PRIME A/B:
//// 1 = Strobe        :  ColorTime(A/B): Time in Milliseconds // BlankTime(A/B): Time in Milliseconds // Extra1(A/B) = N/A                    //  Extra2(A/B) = N/A
//// 2 = Trace         :  ColorTime(A/B): Time in Milliseconds // BlankTime(A/B): Time in Milliseconds // Extra1(A/B) = N/A                    //  Extra2(A/B) = N/A
//// 3 = Morph         :  ColorTime(A/B): Time in Milliseconds // BlankTime(A/B): Time in Milliseconds // Extra1(A/B) = Long Blank Time        //  Extra2(A/B) = N/A
//// 4 = PULSE         :  ColorTime(A/B): Time in Milliseconds // BlankTime(A/B): Time in Milliseconds // Extra1(A/B) = Random?(1=Yes,0=No)    //  Extra2(A/B) = Random Max Value (1-32000)
//// 5 = Triple Rainbow:  ColorTime(A/B): Time in Milliseconds // BlankTime(A/B): Time in Milliseconds // Extra1(A/B) = # of Rainbows (1 to 3) //  Extra2(A/B) = Number of Colors (1-32000)
//// 6 = HeartBeat     :  ColorTime(A/B): Time in Milliseconds // BlankTime(A/B): Time in Milliseconds // Extra1(A/B) = BPM                    //  Extra2(A/B) = N/A
//// 7-12 = Sandbox(1-6 Extra Settings) :  Custom
////
//// VP (Virtual Color Preview)
//// 0 = NO
//// 1 = YES
///////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
}// elihw mode
//////    MODE     ///////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////

}// diov Loop
