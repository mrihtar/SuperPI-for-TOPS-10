# SuperPI for TOPS-10
Program calculates number π to N decimal places using the original Machin's
formula from 1706:

```
π = 16*arctg(1/5) - 4*arctg(1/239)
```

It's written in **MACRO-10 assembler for TOPS-10**. Originally (in 1987)
it run on a DECsystem-10 mainframe with KL 10-E processor and 2 MW of memory.
This enabled the calculation of 65000 decimals of π. On a SIMH PDP-10 simulator
with KS 10 and 1 MW you can only get around 48000 decimals.

## Usage

There are two versions of program: original for the larger amount of memory,
which also detaches itself from the terminal (it took several hours to produce
the result) and the *modern* one for the SIMH PDP-10 simulator.

Copy ```pi6.mac``` to your TOPS-10 system and compile it like this:

```
.load pi6
MACRO:	PI6
LINK:	Loading

EXIT

.save pi6
PI6 saved

.dir pi6.*

PI6     MAC    14  <057>   19-Oct-18    DSKB:   [1,2]
PI6     REL     5  <057>   19-Oct-18
PI6     EXE    16  <057>   19-Oct-18
  Total of 35 blocks in 3 files on DSKB: [1,2]

.run pi6
(press Ctrl-T to see what's going on)
Day: 4.66 Run: 4.66 Rd:0 Wr:0 PI6 377+1P Ctx:1 RN*  PC:776055
```

The program will continue to run without any messages until it finishes.
Every 500 internal cycles (which was around 600 seconds on the original machine)
program saves its memory on the disk (PISAV.EXE), so you could continue to run
it from there, if it was interrupted.

## Result

The result is written to file PI.DAT in the same directory.
```
.type pi.dat

.14159 26535 89793 23846 26433 83279 50288 41971 69399 37510
 58209 74944 59230 78164 06286 20899 86280 34825 34211 70679
 82148 08651 32823 06647 09384 46095 50582 23172 53594 08128
 48111 74502 84102 70193 85211 05559 64462 29489 54930 38196
 ...
```
