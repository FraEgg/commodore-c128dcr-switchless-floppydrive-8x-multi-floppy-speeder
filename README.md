# Switchless 8x Multi-Floppy Speeder with 32 KB RAM Expansion for the Commodore C128 DCR and Internal 1571 Floppy Drive (DolphinDOS 3 Compatible)

Here is an German version [[German]](https://github.com/FraEgg/commodore-c128dcr-1571-switchless-floppydrive-8x-multi-floppy-speeder/blob/main/README_de.md) !

<img title="8x Multi-Floppy-Speeder 32KB RAM Expasion for the internal 1571 Floppydrive C128DCR - DolphinDos 3" src="https://raw.githubusercontent.com/FraEgg/commodore-c128dcr-1571-switchless-floppydrive-8x-multi-floppy-speeder/refs/heads/main/images/V2.0_C128DCR_Multi-Floppy-Speeder-Set-Title.jpg" alt="loading-ag-1227" data-align="center" style="zoom:25%;">

## Description

This project is an evolution of the very fast and popular DolphinDOS3 for the C128 and 1571 floppy drive. It combines the best from the retro world and modern technology in a way that was previously unavailable. The Switchless 8x Multi-Floppy Speeder works not only with DolphinDOS 3 but can also run up to 8x DOS kernels and C128/C64 kernels, which can be conveniently activated via DOS commands. This means, in addition to the original CBM-DOS and DolphinDOS 3, systems such as JiffyDOS 128 can also be used, ensuring maximum compatibility.

The 32 KB RAM expansion is organized into 4x 8 KB banks and enables ultra-fast parallel data transfer and control of the 4x 8 KB RAM banks (32 KB) in combination with the Peripheral Interface Adapter (PIA, type 6821 or 6521).

The Switchless 8x Multi-Floppy Speeder with 32 KB RAM expansion for the Commodore C128DCR is one of the most versatile accelerators for the internal 1571 floppy drive of the C128DCR. Additionally, the "Switchless 8x Multi-Floppy Speeder" is fully RAMBoard compatible, enabling the use of compatible nibble-copying programs.



## Features

1. 8 x 64 KB ROM banks for C128/C64 kernels.
2. 8 x 64 KB ROM banks for the internal 1571 floppy drive.
3. 32 KB RAM expansion for the 1571 floppy drive (4 banks, switchable via PIA).
4. Parallel port for the 1571 floppy drive (PIA 6821).
5. U32 Kernel Adapter Socket for C128/C64 8x kernel switching (switchless).
6. U4 6526-CIA adapter for the parallel port of the internal 1571 floppy drive.
7. Compatibility with RAMBoard for nibble-copying programs.
   
   

## Benchmark

Here I have created some benchmarks with the 8x Multi-Speeder 32KB RAM [[here]](https://github.com/FraEgg/commodore-c128dcr-1571-switchless-floppydrive-8x-multi-floppy-speeder/blob/main/benchmark/README.md)



## Functionality

The "Switchless 8x Multi-Floppy Speeder" for the Commodore C128DCR is based on the further development of the 8x Multi-Floppy Speeder for the 1541 floppy drive. A 512 KB EPROM (27C040 or 29F040) can store up to eight kernel operating systems for the 1571 floppy drive. A Peripheral Interface Adapter (PIA, type 6821 or 6521) extends the floppy drive with an 8-bit parallel port.

In combination with the 32 KB RAM expansion (SRAM 62256), it is possible to run DolphinDOS 3. This allows the drive to read entire tracks in one revolution, significantly accelerating program loading in DolphinDOS 3 mode on both the C128 and C64 by a factor of 38.

A microcontroller (Atmel ATMEGA328p) manages the operating modes of the speeder. It monitors the data bus of the 6502 CPU in the internal 1571 floppy drive and automatically switches the corresponding ROM banks as soon as a specific command (string) is detected. The U32 Kernel Adapter is also connected to the speeder, allowing the microcontroller to synchronize the switching of the 8 ROM banks. This ensures that the kernel corresponding to the 1571 DOS kernel is automatically activated for C128 or C64 mode. The 8 C128/C64 kernels are also stored in an EPROM (27C040 or 29F040).



## Components

The "Switchless 8x Multi-Floppy Speeder" for the Commodore C128DCR consists of the following parts:

1. Multi-Speeder Board for the 1571 CPU 6502 AD socket (U101).
2. Parallel Port Adapter Board for CIA2 6526 (U4 C128) with a parallel cable (optional for DolphinDOS 3).
3. C128/C64 Kernel Switcher Board for 27256 ROM1 (U32).
   
   

### (1) Multi-Speeder Board

<img title="8x Multi-Speeder 32KB RAM Expansion Module (DolphinDos 3)" src="https://raw.githubusercontent.com/FraEgg/commodore-c128dcr-1571-switchless-floppydrive-8x-multi-floppy-speeder/refs/heads/main/images/V2.0a_Multi-Speeder.jpg" alt="loading-ag-1229" style="zoom:25%;" data-align="center">

The Multi-Speeder Board replaces the CPU 6502 AD of the internal 1571 floppy drive. The CPU is then placed into the 6502 socket on the Multi-Speeder Board. In most cases, the CPU is soldered directly onto the C128DCR motherboard, so it must first be desoldered and replaced with a 40-pin DIP socket before the Multi-Speeder Board can be installed.

This board acts as the core of the system, providing the selected DOS kernels for the 1571, the additional 32 KB RAM organized into 4x 8 KB banks, and the PIA 6821/6521 for the parallel port and RAM bank control. The DOS kernels are stored in a 512 KB EPROM organized into 8x 64 KB banks. The ATMega microcontroller activates the desired ROM bank, enabling the corresponding DOS kernel. If another DOS bank is activated via DOS commands, the microcontroller resets the floppy drive to ensure the newly selected DOS-ROM initializes correctly.



### (2) Parallel Port Adapter Board

<img title="8x Multi-Speeder Parallelport Adapter C128DCR for U4" src="https://raw.githubusercontent.com/FraEgg/commodore-c128dcr-1571-switchless-floppydrive-8x-multi-floppy-speeder/refs/heads/main/images/V2.0a_Parallelport-Adapter.jpg" alt="8x Multi-Speeder Parallelport Adapter C128D for U4CR" style="zoom:25%;" data-align="center">

The Parallel Port Adapter Board replaces the CIA2 6526 (U4) on the C128DCR motherboard. The CIA 6526 is then placed into the 40-pin DIP socket on the adapter board. This adapter replaces the user port’s board connector, which is usually used, leaving the user port of the C128DCR externally accessible and eliminating the need for an external parallel cable. The Parallel Port Adapter Board includes a 10-pin ribbon cable that must be connected to the Multi-Speeder Board. This adapter board and cable are only required if the 1571 floppy drive is to be operated in parallel port mode with DolphinDOS 3.



### (3) C128/C64 Kernel Switcher Board

<img title="8x Multi-Floppy-Speeder Kernal Switcher C128DCR" src="https://raw.githubusercontent.com/FraEgg/commodore-c128dcr-1571-switchless-floppydrive-8x-multi-floppy-speeder/refs/heads/main/images/V2.0_U32_Kernal-Switcher-Platine.jpg" alt="8x Multi-Floppy-Speeder Kernal Switcher C128DCR" style="zoom:25%;" data-align="center">

The Kernel Switcher Board is an adapter board for a 512 KB EPROM (27C040 or 29F040) for the 8x 64 KB kernel ROM banks. It is installed into the U32 socket of the C128DCR. The switcher has an A16/A17/A18 connection that must be connected to the Multi-Speeder Board (J6). The Multi-Speeder Board synchronizes the switching of the floppy drive kernel with the corresponding C128/C64 kernel ROM bank. This allows the simultaneous switching of the 1571 kernel and the C128/C64 kernel via DOS commands. The same ROM banks are always activated.



### ROM/RAM Organization

The firmware (kernals) for the 1571 disk drive and the C128/C64 are each organized into a 512KB EPROM of type 27C040 or 29F040 (PLCC32), divided into 8x 64KB banks. Each bank (0-7) represents the complete 64KB address range.

Here, I have provided test kernals [[here]](https://github.com/FraEgg/commodore-c128dcr-1571-switchless-floppydrive-8x-multi-floppy-speeder/tree/main/kernals).



## 512 KB ROM Internal 1571 Disk Drive

The address decoder of the Multi-Speeder board maps the ROM in the disk drive to the address range `$8000 to $FFFF`.

### 

## 32KB RAM Expansion for the 1571 Disk Drive

The 1571 disk drive, like the 1541 disk drive, only has 2KB of working memory by default. This is very limited, as it cannot store an entire track in memory. DolphinDOS 3 uses additional memory to read a complete track from the disk in a single disk rotation. This requires at least 8KB of additional RAM. The Multi-Speeder is equipped with a 62256 32KB SRAM or a 6264 8KB SRAM. This additional 8KB memory area is made available in the CPU address space of the 1571 disk drive at `$6000 - $7FFF`. When using a 32KB SRAM, the 8K banks of memory can be switched via the PIA chip port PB0 and PB1. If a 32KB SRAM is used, the jumpers A14RAM (J7) and A15RAM (J8) on the Multi-Speeder board must be closed to enable bank switching.



### Memory Map of the 1571 Floppy Drive

| Address         | Description                     |
| --------------- | ------------------------------- |
| `$0000 - $07FF` | 2 KB RAM (Standard)             |
| `$1800 - $180F` | VIA 1 6522 (IEC Bus and Drive)  |
| `$1C00 - $1C0F` | VIA 2 6522 (Signals, Motor)     |
| `$2000 - $4000` | Gate Array (CIA/WD MFM)         |
| `$5000 - $5FFF` | PIA 6821/6521 _2)_              |
| `$6000 - $7FFF` | SRAM 8 KB / 32 KB Bank 0-3 _2)_ |
| `$8000 - $FFFF` | 1571 DOS Kernel Bank 0-7 _2)_   |

_2)_ Provided additionally by the Multi-Floppy Speeder.



### Switchless - Selecting Operating Modes (ROM Bank)

#### Switching the ROM Bank

Banks 0–7 are called using the commands `1@RNROM` to `8@RNROM`.

Switching the speeder can be triggered on the computer using simple commands. The following example demonstrates switching in C64 mode:



### Switchless - Selecting Operating Modes (ROM Bank)

#### Switching the ROM Bank

Banks 0–7 are called using the commands `1@RNROM` to `8@RNROM`.

Switching the speeder can be triggered on the computer using simple commands. The following example demonstrates switching in C64 mode:



1. **Switch to Bank 2 (JiffyDOS 64):**
   `   LOAD"3@RNROM",8,1`
   The drive switches to Bank 2 and restarts automatically.

2. **Switch to Bank 0 (DolphinDOS 3):**
   `   OPEN 1,8,15,"I:1@RNROM":CLOSE 1`
   The microcontroller switches to Bank 0, the drive's LED blinks, and the drive restarts.

3. **Switch to Bank 7 (CBMDOS):**
   `   @I:8@RNROM`
   The microcontroller recognizes the command, switches to Bank 7, the LED blinks, and the drive restarts.

4. **Temporarily Disable the Switchless Mode:**
   `   @I:0@RNROM or LOAD"0@RNROM",8,1`
   The switchless mode is temporarily disabled until the drive is restarted.
   
   

**Note:**

When the 1571 floppy disk drive operates in 2 MHz mode (C128 mode/DolphinDos), it may happen that the ROM switching does not always work reliably. The ATmega328 microcontroller then encounters timing issues when reading commands from the data bus. It works reliably if the Y1 crystal on the board is replaced from 20 MHz to 22.1184 MHz. Although the manufacturer specifies a maximum clock rate of 20 MHz for the ATmega328, in practice, the microcontroller also operates smoothly at 22 MHz.*



### Overview of C128/C64 and DOS Kernals

* * *

#### C128/C64 Kernals U32

The C128/C64 Kernal Switcher board for the U32 socket is organized as follows. It is important to note that, for the 512KB EPROMs 27C040 and 29F040, only the upper ROM area of 32KB from the 64KB banks, ranging from `$x8000 - $xFFFF`, is currently utilized. Therefore, the kernals must be placed starting at `$x8000`.

The Kernal ROM 27256 (U32) (C128/C64 Kernals) is generally structured as follows on the C128DCR:

| ROM Address Range | ROM Type                     | Size |
| ----------------- | ---------------------------- | ---- |
| `$0000 - $1FFF`   | C64 Basic V2 `$A000 - $BFFF` | 8KB  |
| `$2000 - $3FFF`   | C64 Kernal `$E000 - $FFFF`   | 8KB  |
| `$4000 - $7FFF`   | C128 Kernal/System           | 16KB |

* * *

#### 1571 DOS Kernal (U101 Multi-Speeder)

The drive's Kernal ROM starts at `$x8000 - $xFFFF`, and depending on the active bank (0-7), the corresponding section is mapped into the CPU's address space.

| Bank | Switch  | EPROM Address     | CPU Address     |
| ---- | ------- | ----------------- | --------------- |
| 0    | 1@RNROM | `$08000 - $0FFFF` | `$8000 - $FFFF` |
| 1    | 2@RNROM | `$18000 - $1FFFF` | `$8000 - $FFFF` |
| 2    | 3@RNROM | `$28000 - $2FFFF` | `$8000 - $FFFF` |
| 3    | 4@RNROM | `$38000 - $3FFFF` | `$8000 - $FFFF` |
| 4    | 5@RNROM | `$48000 - $4FFFF` | `$8000 - $FFFF` |
| 5    | 6@RNROM | `$58000 - $5FFFF` | `$8000 - $FFFF` |
| 6    | 7@RNROM | `$68000 - $6FFFF` | `$8000 - $FFFF` |
| 7    | 8@RNROM | `$78000 - $7FFFF` | `$8000 - $FFFF` |

* * *

#### ROM Bank Configuration (Example Setup)

| Bank | Switch  | System            | U32 C128 | U32 C64      | U101 1571    | EPROM Address   |
| ---- | ------- | ----------------- | -------- | ------------ | ------------ | --------------- |
| 0    | 1@RNROM | CBM               | CBM      | CBM          | CBM          | `$08000-$0FFFF` |
| 1    | 2@RNROM | CBM RAM Exp       | CBM      | CBM          | CBM RAM Exp. | `$18000-$1FFFF` |
| 2    | 3@RNROM | DolphinDos 3      | DD3      | DD3          | DD3          | `$28000-$2FFFF` |
| 3    | 4@RNROM | DolphinDos 3      | DD3      | DD3-Custom   | DD3          | `$38000-$3FFFF` |
| 4    | 5@RNROM | CBM-DD-SD2IEC     | CBM      | DD-JD-SD2IEC | CBM RAM Exp. | `$48000-$4FFFF` |
| 5    | 6@RNROM | CBM               | CBM      | JaffyDos 1.3 | CBM RAM Exp. | `$58000-$5FFFF` |
| 6    | 7@RNROM | CBM (reserved JD) | CBM      | CBM          | CBM RAM Exp. | `$68000-$6FFFF` |
| 7    | 8@RNROM | CBM (reserved JD) | CBM      | CBM          | CBM RAM Exp. | `$78000-$7FFFF` |



**CBM RAM Exp.** refers to the original CBMDOS of the 1571 with a patch for the Multi-Speeder's RAM expansion. This patch includes a track cache, allowing the 1571 disk drive to read an entire track at once. This significantly accelerates the loading process. A version of JiffyDOS 128 with this patch is also available, further speeding up reading by 20%.

More details are available on GitHub by ytmytm: [GitHub - ytmytm/1571-TrackCacheROM: A firmware patch for Commodore 1571 drive and internal C128D drive enabling RAM expansion use for track cache](https://github.com/ytmytm/1571-TrackCacheROM).



JiffyDOS 128 runs perfectly on the Multi-Speeder. Especially with the RAM expansion patch, JiffyDOS is considerably faster on the C128 and C64. I have not offered JiffyDOS for download, as it is still distributed commercially.



### Important Notes:

1. **Removal of Original DOS-ROM (U102):**  
   When using the Multi-Speeder board, the original DOS-ROM U102 must be removed entirely. The Multi-Speeder now provides the selected DOS kernal via its own EPROM. Leaving it in place would cause an address conflict, rendering the disk drive non-functional.

2. **Switching Issues in 2MHz Mode:**  
   Switching issues may occur when operating the disk drive in 2MHz mode. If this happens, repeatedly attempt to switch the ROM (e.g., using `LOAD"x@RNROM",8,1`) until the desired ROM is successfully loaded. The problem is caused by timing issues related to the interaction of the ATMega and 74AHTC273 Flip-Flop under 2MHz. The system works best with an NXP 74AHTC273, though these are difficult to source.
   
   

### Peripheral Interface Adapter (PIA)

The Peripheral Interface Adapter (PIA) controls the parallel data transfer between the floppy drive and the C128/C64 via the Parallel Port Adapter Board or a parallel user port cable. I have tested the following PIA versions:

1. **MC68B21P** (Motorola) (2MHz) 
2. **W65C21N6TPG-14** or **W65C21S6TPG-14** (Western Design Center)   
3. **EF68B21** (STMicroelectronics) (2MHz)
4. **R65C21P2** (Rockwell) (2MHz)

## Diagnostic tool

I have created a program to test the RAM for the Multi-Speeder-DD3. It tests the access to the RAM and the RAM bank switching. The tool is written for the C64 mode, so that it can be used for the C64/1541 version of the Multi-Speeder-DD3.  [Link](https://github.com/FraEgg/commodore-c128dcr-1571-switchless-floppydrive-8x-multi-floppy-speeder/tree/main/tools)



## Bill of Materials

The BOM list is available for download > [here](https://github.com/FraEgg/commodore-c128dcr-1571-switchless-floppydrive-8x-multi-floppy-speeder/tree/main/bom) <.



### Example of ram bank switching via PIA (for developers)

It would be really great if there were developers who could help exploit the possibilities of the Multi-Speeder. Here is an example in Asembler for developers how to change the memory banks of the Multi-Speeder in 1571. The memory is divided into four 8K banks. These are displayed at `$6000 - $7FFF` in the 1571. The banks are easily switched by the 65c21/6821 PIA via ports PB0 = A13 and PB1 = A14. By default, A13/A15 are set to high.
 

```
LDA #$00           ; PIA DDR for output ($00)
STA $5003          ; Init PIA DDR Port PB0-PB7 output direction
LDA #$FF           ; Set PIA output for Port PB0-PB7
STA $5002          ; Init PIA Port PB0-PB7 aktiv

LDA #$00
STA $5002          ; Set PIA Port PB0-PB1 low        (RAM BANK 0 active)
...
LDA #$01
STA $5002         ; Set PIA Port PB0 high / PB1 low  (RAM BANK 1 active)
...
LDA #$02
STA $5002         ; Set PIA Port PB0 low / PB1 high  (RAM BANK 2 active)
...
LDA #$03
STA $5002         ; Set PIA Port PB0 high / PB1 high (RAM BANK 3 active)`
```





### BOM - Multi-Speeder

| Reference                           | Value                            | Datasheet                                                                                                                                                            | Footprint                                                                                           | Qty | DNP | Note                                                                                                                                                                                                                                                                                   |
| ----------------------------------- | -------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- | --- | --- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| PCB 8xMulti-Speeder-PCB for C128DCR |                                  |                                                                                                                                                                      |                                                                                                     | 1   |     |                                                                                                                                                                                                                                                                                        |
| C1,C2,C5,C6,C7                      | Capacitor 0,1uF                  | https://www.aliexpress.com/item/1005002771940165.html                                                                                                                | C_Disc_D3.0mm_W2.0mm_P2.50mm                                                                        | 5   |     |                                                                                                                                                                                                                                                                                        |
| C3,C4                               | Capacitor 22 pF                  | https://www.aliexpress.com/item/1005002771940165.html                                                                                                                | C_Disc_D3.0mm_W2.0mm_P2.50mm                                                                        | 2   |     |                                                                                                                                                                                                                                                                                        |
| CN1                                 | Connector                        | https://www.aliexpress.com/item/1005008071308576.html                                                                                                                | MicroMatch 1,27 mm,2X05 (MICMA10B)                                                                  | 1   |     | recommend                                                                                                                                                                                                                                                                              |
| D1                                  | LED GREEN                        |                                                                                                                                                                      | LED_THT:LED_D3.0mm                                                                                  | 1   |     |                                                                                                                                                                                                                                                                                        |
| R2,R4,R5                            | Resistor 10K,1/4W                |                                                                                                                                                                      | R_Axial_DIN0204_L3.6mm_D1.6mm_P5.08mm_Horizontal                                                    | 3   |     |                                                                                                                                                                                                                                                                                        |
| R3                                  | Resistor 560R, 1/4               |                                                                                                                                                                      | R_Axial_DIN0204_L3.6mm_D1.6mm_P5.08mm_Horizontal                                                    | 1   |     |                                                                                                                                                                                                                                                                                        |
| SW1                                 | JTP-1130                         | https://www.aliexpress.com/item/1005005810426286.html                                                                                                                | 6X6x5mm 4PIN dip TACT push button switch Micro key power tactile switches 6x6x5 6*6*5MM Light touch | 1   |     |                                                                                                                                                                                                                                                                                        |
| U1                                  | Socket                           |                                                                                                                                                                      | DIP-40_W15.24mm_Socket                                                                              | 2   |     |                                                                                                                                                                                                                                                                                        |
| U2                                  | Pin Header                       | https://www.aliexpress.com/item/1005007564228387.html                                                                                                                | 2.54mm Pin Header Male Single Row 20/40 Pin 2.54mm Round Pin Connector                              | 2   |     |                                                                                                                                                                                                                                                                                        |
| U3                                  | Socket                           |                                                                                                                                                                      | PLCC-32_THT-Socket                                                                                  | 1   |     |                                                                                                                                                                                                                                                                                        |
| U3                                  | EPROM 29F040                     | https://www.aliexpress.com/item/1005007299303666.html                                                                                                                | PLCC-32                                                                                             | 1   |     | alternativ 27C040 PLCC-32                                                                                                                                                                                                                                                              |
| U4                                  | IC W65C21N6TPG-14                | https://www.mouser.de/datasheet/2/436/w65c21-661.pdf <br/>https://de.aliexpress.com/item/1005006827509758.html<br/>https://de.aliexpress.com/item/4001175531491.html | DIP-40 W15.24mm                                                                                     | 1   |     | alternativ<br/>MC68B21P, R65C21P2                                                                                                                                                                                                                                                      |
| U5                                  | IC 74AHCT273N                    | https://www.nexperia.com/product/74AHCT273D                                                                                                                          | DIP-28_W7.62mm                                                                                      | 1   |     |                                                                                                                                                                                                                                                                                        |
| U6                                  | IC ATmega328P                    | https://www.aliexpress.com/item/32901846548.html                                                                                                                     | Package_DIP:DIP-28_W7.62mm                                                                          | 1   |     |                                                                                                                                                                                                                                                                                        |
| U7                                  | IC ATF16V8B                      | https://www.aliexpress.com/item/4000830127120.html                                                                                                                   | Package_DIP:DIP-20_W7.62mm                                                                          | 1   |     | GAL16V8                                                                                                                                                                                                                                                                                |
| U8                                  | IC HM62256LFP-12T SRAM 32KB      | https://www.aliexpress.com/item/1005006266772362.html                                                                                                                | Package_SO:SOP-28_8.4x18.16mm_P1.27mm                                                               | 1   |     | alternativ<br/>LY62256SL-70LL<br/>UT62256CSC-70LL<br/>CY62256NL-70SNXC                                                                                                                                                                                                                 |
| Y1                                  | Crystal 22.1184 MHz HC-49S       | https://www.aliexpress.com/item/1005007425032260.html                                                                                                                | Crystal_HC49-4H_Vertical                                                                            | 1   |     | The manufacturer specifies 20 MHz as the maximum clock rate for the ATmega328. However, this can lead to timing issues with ROM switching in 2 MHz mode on the 1571. A 22.1184 MHz clock resolves the issue. In practice, this is not a problem for the ATmega328, and it runs stably. |
| PCB                                 | PCB 8x Multi-Speeder for C128DCR |                                                                                                                                                                      |                                                                                                     | 1   |     |                                                                                                                                                                                                                                                                                        |
| CN2                                 | Connector                        | https://www.aliexpress.com/item/1005004266492521.html                                                                                                                | IDC-Header_2x05_P2.54mm_Vertical                                                                    | 1   |     | optional                                                                                                                                                                                                                                                                               |
| R1                                  | Resistor 3,3K, 1/4W              |                                                                                                                                                                      | R_Axial_DIN0204_L3.6mm_D1.6mm_P5.08mm_Horizontal                                                    | 1   |     | optional only for W65C02 WDC CPU                                                                                                                                                                                                                                                       |
| J4                                  | Connector                        | https://www.aliexpress.com/item/4000694229610.html                                                                                                                   | PinHeader_1x03_P2.54mm_Vertical                                                                     | 1   |     | optional                                                                                                                                                                                                                                                                               |
| J5                                  | Connector                        | https://www.aliexpress.com/item/4000988113226.html                                                                                                                   | PinHeader_2x03_P2.54mm_Vertical                                                                     | 1   |     | optional                                                                                                                                                                                                                                                                               |
| J6                                  | Connector                        | https://www.aliexpress.com/item/4000694229610.html                                                                                                                   | PinHeader_1x03_P2.54mm_Vertical                                                                     | 1   |     | optional                                                                                                                                                                                                                                                                               |



### BOM - Parallelport-Adapter-Platine

| Reference                        | Value                                                  | Datasheet                                             | Footprint                                                                                                                | Qty | DNP | Note      |
| -------------------------------- | ------------------------------------------------------ | ----------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------ | --- | --- | --------- |
| PCB Parallelport-Adapter-Platine |                                                        |                                                       |                                                                                                                          | 1   |     |           |
| CN1                              | Connector                                              | https://www.aliexpress.com/item/1005008071308576.html | MicroMatch 1,27 mm,2X05 (MICMA10B)                                                                                       | 1   |     | recommend |
| U4                               | Gold Round Female Male Pin Sensor Crystal Socket       | https://www.aliexpress.com/item/32972142300.html      | D0.5mm D0.45-0.6mm PCB Gold Round Female Male Pin Sensor Crystal Socket Dim1.4*7.4mm,No Plastic for 2.54 Hole Pin Header | 40  |     |           |
| Cable                            | Flat Ribbon                                            | https://www.aliexpress.com/item/1005004316520454.html | 1.27mm PITCH color Flat Ribbon Cable Rainbow DuPont Wire for FC dupont Connector 2.54mm IDC                              | 1   |     |           |
| CN1                              | Micromatch IDC Header Connector                        | https://www.aliexpress.com/item/4001278233965.html    | Micromatch Red 2.54mm Pitch Double Row Female IDC Box Header Connector 10P 2x05                                          | 2   |     |           |
| CN2                              | Connector                                              | https://www.aliexpress.com/item/1005004266492521.html | IDC-Header_2x05_P2.54mm_Vertical                                                                                         | 1   |     | optional  |
| CN2                              | tch Female IDC Socket Connector Ribbon Cable Connector | https://www.aliexpress.com/item/1005002804645942.html | 2.54mm Pitch Female IDC Socket Connector Ribbon Cable Connector 10 PIN                                                   | 2   |     | optional  |



### BOM - C128/C64 Kernal-Switcher-Platine

| Reference                            | Value        | Datasheet                                             | Footprint                                                           | Qty | DNP | Note                      |
| ------------------------------------ | ------------ | ----------------------------------------------------- | ------------------------------------------------------------------- | --- | --- | ------------------------- |
| PCB C128/C64 Kernal-Switcher-Platine |              |                                                       |                                                                     | 1   |     |                           |
| J3                                   | Connector    | https://www.aliexpress.com/item/4000694229610.html    | Connector_PinHeader_2.54mm:PinHeader_1x04_P2.54mm_Vertical          | 1   |     |                           |
| U1                                   | Pin Header   | https://www.aliexpress.com/item/1005007564228387.html | 2.54mm Pin Header Male Single Row 14 Pin 2.54mm Round Pin Connector | 2   |     |                           |
| U2                                   | Socket       |                                                       | PLCC-32_THT-Socket                                                  | 1   |     |                           |
| U2                                   | EPROM 29F040 | https://www.aliexpress.com/item/1005007299303666.html | PLCC-32                                                             | 1   |     | alternativ 27C040 PLCC-32 |



## ATMega 328P

The Atmel ATMega 328P microcontroller monitors the data bus, controls the ROM banks, and is responsible for switching operating modes. The firmware can be programmed using an Arduino board or an AV programmer. I use the XGecu T48 Universal Programmer with a `.mpj` project file. When programming with the XGecu using the `.mpj` file, please ensure the EEPROM is not programmed as this would cause an error. This can be disabled in the XGecu menu.



<img title="" src="https://raw.githubusercontent.com/FraEgg/commodore-c128dcr-1571-switchless-floppydrive-8x-multi-floppy-speeder/refs/heads/main/images/XGecuT48UniversalProgrammerEEPROM.png" alt="" data-align="center" style="zoom:25%;">

<img title="" src="https://raw.githubusercontent.com/FraEgg/commodore-c128dcr-1571-switchless-floppydrive-8x-multi-floppy-speeder/refs/heads/main/images/XGecuT48UniversalProgrammerConfig.png" alt="" style="zoom:25%;" data-align="center">

## Installation C128DCR

<img title="8x Multi-Speeder Install C128DCR  Mainboard" src="https://github.com/FraEgg/commodore-c128dcr-1571-switchless-floppydrive-8x-multi-floppy-speeder/blob/main/images/V2.0_C128DCR_Overview.jpg?raw=true" alt="8x Multi-Speeder Install C128DCR  Mainboard" style="zoom:50%;" data-align="center">

### Installation of the Multi-Speeder on the C128DCR Mainboard

The Multi-Speeder is installed in place of the 6502 CPU (U101). The 6502 CPU is inserted into the CPU socket on the Multi-Speeder (bottom right). The Kernal Switcher is located at the bottom left and is inserted into the socket (U32) in place of the original kernal. The Parallel Adapter is installed in place of the CIA 6526 (U4) in a socket. The CIA 6526 is then inserted into the Parallel Adapter Board. The Kernal Switcher is connected to the Multi-Speeder using a three-pin cable. The Parallel Adapter is also connected to the Multi-Speeder Board using a 10-pin cable (parallel port).

## Downloads

1. [ATF16V8 (GAL16V8) Files](https://github.com/FraEgg/commodore-c128dcr-1571-switchless-floppydrive-8x-multi-floppy-speeder/tree/main/pld-atf16v8-gal16v8)

2. [ATMEL ATMega328 P Files](https://github.com/FraEgg/commodore-c128dcr-1571-switchless-floppydrive-8x-multi-floppy-speeder/tree/main/atmega328p)

3. [Gerber Files for PCB Manufacturing](https://github.com/FraEgg/commodore-c128dcr-1571-switchless-floppydrive-8x-multi-floppy-speeder/tree/main/gerber)

4. [Schematics for 8x Multi-Speeder 32KB RAM Expansion (DolphinDos3)](https://github.com/FraEgg/commodore-c128dcr-1571-switchless-floppydrive-8x-multi-floppy-speeder/tree/main/schematics)

5. [Photogallery](https://github.com/FraEgg/commodore-c128dcr-1571-switchless-floppydrive-8x-multi-floppy-speeder/tree/main/images)

6. [Additional Documents](https://github.com/FraEgg/commodore-c128dcr-1571-switchless-floppydrive-8x-multi-floppy-speeder/tree/main/docs)
   
   

## Shared Projects on PCBWay.com

1. [8x Multi-Floppy Speeder 32KB RAM Expansion for the Commodore C128DCR](https://www.pcbway.com/project/shareproject/Switchless_8x_Multi_Floppy_Speeder_with_32_KB_RAM_Expansion_for_the_Commodore_C1_557a83c8.html)

2. [C128/C64 Kernal-Switcher for 8x Multi-Floppy-Speeder C128DCR](https://www.pcbway.com/project/shareproject/C128_C64_U32_Kernal_Switcher_Adapter_for_Switchless_8x_Multi_Floppy_Speeder_with_f113e895.html)

3. [Parallel-Port-Adapter for 8x Multi-Floppy-Speeder C128DCR](https://www.pcbway.com/project/shareproject/Parallelport_Adapter_U4_for_Switchless_8x_Multi_Floppy_Speeder_with_32_KB_RAM_Ex_558623e7.html)
   
   
   
   

### Weitere Projekte auf PCBWay.com:

### Commodore 1541 Switchless 8x Multi-Speeder

1. [Switchless Floppy Drive 8x Multi Floppy Speeder (THT) for the Commodore 1541 Disk Drive (V2.2c)](https://www.pcbway.com/project/shareproject/Switchless_Floppy_Drive_8x_Multi_Floppy_Speeder_for_the_Commodore_1541_Disk_Driv_369dbba4.html)

2. [Switchless Floppy Drive 8x Multi Floppy Speeder (SMD) for the Commodore 1541 Disk Drive (V2.2c)](https://www.pcbway.com/project/shareproject/Switchless_Floppy_Drive_8x_Multi_Floppy_Speeder_for_the_Commodore_1541_Disk_Driv_33eedf94.html)

3. [Parallel Cable Sets for the Commodore 1541 Disk Drive (SpeedDOS, DolphinDOS) with the C64/C128](https://www.pcbway.com/project/shareproject/C64_Userport_Adapter_Parallel_Cable_Set_for_the_Commodore_1541_Disk_Drive_Spe_3b86d1f8.html)

### Commodore 1541 Parallel Port Adapter VIA 6522

1. [1541-I/1541-II Parallel Adapter (Duo/Slim) - Parallel Cable Set for the Commodore 1541 Disk Drive (SpeedDOS, DolphinDOS) with the C64/C128](https://www.pcbway.com/project/shareproject/1541_I_1541_II_Parallel_Adapter_Duo_Slim_Parallel_Cable_Set_for_the_Commodor_57072954.html)

2. [1541-I/1541C Parallel Adapter - Parallel Cable Set for the Commodore 1541 Disk Drive (SpeedDOS, DolphinDOS) with the C64/C128](https://www.pcbway.com/project/shareproject/1541_I_1541C_Parallel_Adapter_Parallel_Cable_Set_for_the_Commodore_1541_Disk_D_a27176a6.html)

3. [C64 User Port Adapter - Parallel Cable Set for the Commodore 1541 Disk Drive (SpeedDOS, DolphinDOS) with the C64/C128](https://www.pcbway.com/project/shareproject/C64_Userport_Adapter_Parallel_Cable_Set_for_the_Commodore_1541_Disk_Drive_Spe_3b86d1f8.html)
   
   
   
   

## Useful links

1. DolphinDos [Dolphin DOS – C64-Wiki](https://www.c64-wiki.de/wiki/Dolphin_DOS) & https://project64.c64.org/hw/dolphindos.txt

2. RAMBoard: [RAMBOard – C64-Wiki](https://www.c64-wiki.de/wiki/RAMBOard) & [https://www.c64copyprotection.com/ramboard/](https://www.c64copyprotection.com/ramboard/) & [[CSDb] - Super-Card 6 Plus RAMboard [scpu] by Master (2018)](https://csdb.dk/release/?id=164372)
   
   

Thank You
---------

This project is the result of the contributions of many and reflects the efforts of numerous developers. I would like to extend special thanks to the following individuals:

1. **Jan Bubela and Gunther Jilg**, for developing DolphinDos.

2. **RetroNynjah**, who helped integrate his switchless Multi-ROM into the 8x Multi-Speeder.  
   [GitHub - RetroNynjah/Switchless-Multi-ROM-for-27128-27256](https://github.com/RetroNynjah/Switchless-Multi-ROM-for-27128-27256)

3. **Jim Drew and Joeri van Haren**, for Help and Revised Version 2.1 by Jim Drew 

4. The informative site with technical details about DD3 by **silverdr**.  
   [DolphinDOS3](https://e4aws.silverdr.com/projects/dolphindos3/)

5. **Ytmytm**, for his TrackCache:  
   [GitHub - ytmytm/1571-TrackCacheROM: A firmware patch for Commodore 1571 drive and internal C128D drive enabling RAM expansion use for track cache](https://github.com/ytmytm/1571-TrackCacheROM)

6. Stefan Kauf for his support with the idea of the Mult-Speeder and its templates.
   
   

### Disclaimer

I have designed and tested this project with great care, but errors can always happen. This project is a hobby project. Therefore, I do not guarantee its functionality or take responsibility for any potential damage caused by the installation or use of this project in any way.



### Donations

I have invested many hours into this project. If you would like to support my work, you can contribute to my coffee fund. Thank you! [Click here to donate via PayPal!](https://www.paypal.com/donate/?cmd=_s-xclick&hosted_button_id=Q8HXKYARXKT4L&ssrt=1714757590172)



### Usage Rights / Copyright

You are welcome to use this project for private purposes. Commercial use, such as selling or other distribution of my Multi-Floppy-Speeder, is prohibited without my permission.

I wish you much joy with my 8x Multi-Floppy-Speeder 32KB RAM Expansion for the C128DCR.



Best regards,  
Frank Eggen

E-Mail: [retro@emden.net](mailto:retro@emden.net)



## Update

* 2024-12-07 PCB Gerber file update to version 2.0b - Errors R2 and R3 corrected. 5V must be applied between pull-up resistors R2-R3.
* 2025-01-02 Add links 1541 8x Switchless Multi-Speeder 32KB


