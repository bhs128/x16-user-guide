
# Chapter 1: Overview

The Commander X16 is a modern home computer in the philosophy of Commodore computers like the VIC-20 and the C64.

**Features:**

* 8-bit 65C02S CPU at 8 MHz ([*](#future-65c816-support))
* 512 KB banked RAM (upgradeable to 2 MB on the X16 Developer Edition)
* 512 KB ROM
* Expansion Cards (Gen 1) & Cartridges (Gen 1 and Gen 2)
  * Up to 3.5MB of RAM/ROM
  * 5 32-byte Memory-Mapped IO slots
* VERA video controller
  * Up to 640x480 resolution
  * 256 colors from a palette of 4096
  * 128 sprites
  * VGA, NTSC and RGB output
  * Powered by a Lattice ICE40UP5K FPGA
* Three sound sources
  * Yamaha YM2151: 8 channels, 4-operator FM synthesis
  * VERA PSG: 16 channels, 4 waveforms
  * VERA PCM: Up to 48 kHz, 16 bit, stereo
* Connectivity:
  * PS/2 keyboard and mouse
  * 4 NES/SNES controllers
  * SD card
  * Commodore Serial Bus ("IEC")
  * Many Free GPIOs ("user port")

As a modern sibling of the line of Commodore home computers, the Commander X16 is reasonably compatible with computers of that line.

* Pure BASIC programs are fully backwards compatible with the VIC-20 and the C64.
* POKEs for video and audio are not compatible with any Commodore computer. (There are no VIC or SID chips, for example.)
* Pure machine language programs ($FF81+ KERNAL API) are compatible with Commodore computers.

## Future 65C816 Support

A future upgrade path for the X16 may involve the 65C816. It is almost fully
compatible with the 65C02 except for 4 instructions (`BBRx`, `BBSx`, `RMBx`, and `SMBx`).
It is advisable not to use these instructions when writing programs for the X16.

<!-- For PDF formatting -->
<div class="page-break"></div>

# Chapter 2: Getting Started

This is a brief guide to your first few minutes on the Commander X16. For a
complete New User experience, please refer to the
[Commander X16 User Guide](https://github.com/X16Community/x16-user-guide).

## Finding and starting programs

When starting your Commander X16, you'll notice that it's not like other
computers. There is no GUI, and command line commands like `DIR` or `LS` don't
get you anywhere. Here are some quick tips to getting started:

The Commander X16 uses a full screen interface known as "Editor". This was unique
when it was introduced on the PET in 1977, when most computers still treated the
screen as if it was a teletype display. The full screen Editor lets you use the
arrow keys to move around the screen and edit or re-enter input from previous
interactions.

The first thing you will want to do is view a list of files on your SD card.
Type the below command and press the Return key (or Enter key) to see a list of
files:

### DOS

`DOS "$"`

You can also type `@$` and press Return. All of the commands you type must be
followed by the Return or Enter key, to actually execute the command.

Let's try some variations on this command:

`DOS "$=D"` lists just the subdirectories in the current directory.

To get the DOS command a little faster, try pressing F8, then typing `$=D`. You
can even leave off the last quote; DOS doesn't care.

So now that you have a list of directories, try moving to one:

`DOS "CD:BASIC"`

Press F7 or type `DOS"$` again to list the files in this directory. A file with
.PRG at the end is a "Program" file and can be loaded with the LOAD command. The
shortcut for LOAD" is the F3 key. Try it now:

### LOAD

`LOAD "MAD.PRG"`

You can see that the program list loaded by typing `LIST` and pressing Enter.

### RUN

Now type `RUN` and Enter. This will start the loaded program.

### STOP

STOP isn't a command: it's a key. Press it to stop the running program.

If you are using the official Commander X16 keyboard, the key is labeled
`RUN STOP` and is up near the upper right corner of the keyboard.

If you are using a PC keyboard, it's probably labeled `Pause` or `Pause Brk`.

Holding Control and pressing C (also written as `Control+C` or `^C`) will also
stop the running program.

There are a few ways to get back to the text screen, but the quickest is to
hold Control, Alt, and press the Del key. (Or just press the RESET button.)

## Using The Keyboard

The Commander X16's keyboard is a little different than a standard PC: there are
three distinct modes of operation, and the keyboard can create graphic symbols
known as PETSCII characters. There are also some special keys used for
controlling the computer.

### PETSCII Characters

When the system first boots up, the X16 will be in PETSCII Upper Case/Graphic
mode. Pressing a letter key without the shift key will generate an upper case
letter. Unlike a PC or Mac, this mode does not have any lower case text, so
everything you type is UPPER CASE.

Now, notice the extra symbols on your keycaps? There are two sets of extra
symbols: the ones on the lower-right can be accessed by holding SHIFT and a
letter. Go ahead: try pressing Shift and S. You should see a small heart symbol
on your screen. We know you'll love the Commander X16 as much as we do. Press
Alt and a letter, and you'll get the symbol on the lower-left corner of the
screen. Try pressing Alt and the ` key next to the number 1. You should get a
large + symbol. One of the Plusses of PETSCII is using these line drawing
symbols to draw shapes on the screen.

You can also change colors by pressing Control and a number. Go ahead: Press
Control+1 and type a few letters. Notice they come out in black. Now try Alt+1.
Notice the cursor changes to orange, and notice the next thing you type comes
out orange.

You can also use Control+9 to turn on Reverse Print and Control+0 to turn it off.

There are some unexpected changes to the PC keyboard layout, as follows:

* The Grave key (`) prints a left arrow (←) symbol.
* Shift+Grave prints the Pi symbol (π). This is actually the constant "pi". Try it by typing `PRINT π` and RETURN.
* Shift+6 prints an up arrow (↑)
* The \ key prints the British Pound (£).
* The pipe (|) is replaced with a triangle corner symbol.
* { and } are replaced with two box drawing symbols.
* Underline (Shift+-) is replaced with a | symbol.

Note that programming languages that need {, }, and _ will alter the character
set to show those symbols on the appropriate keys when needed. Or you can use
ISO mode when editing C code in EDIT.

### Lower Case Mode

WORKING IN _PETSCII_ MIGHT MAKE PEOPLE THINK YOU'RE YELLING ALL THE TIME.
Fortunately, there's an upper/lower case mode, too: Hold the Alt key and tap
Shift to activate lower case. Notice that the upper case letters shift to lower
case, and the shifted graphic symbols (such as the heart) shift to upper case
letters. The tradeoff of upper/lower case mode is that half of the graphic
symbols are unavailable, but you you get lower case letters.

Now try typing a command. `print "Hello World"` and press RETURN. Notice that
you need to type `print` in lower case. If you did it right, you should see
"Hello World" appear on the next line.

Now tap Alt+Shift again. The text will change to |ELLO oORLD. Again, this is the
tradeoff: you can have the Shifted graphic symbols or lower case, but not both.

### ISO Mode

Finally, the computer has ISO mode. The ISO mode character set operates more
like a PC, with upper case text, lower case text, and an assortment of accented
and other letters. In addition, ISO mode has the \, ~, {, and } symbols, which
are not available in PETSCII modes. ISO mode is useful when you need PC
compatibility or want the letters with accents. Elsewhere in this guide, we have
a full manual on using the Right Alt key to compose accented symbols, like é or
ō. Getting back to PETSCII mode from ISO mode is a little more complicated.
Press Control+Alt+RESTORE (or Control+Alt+PrintScreen) to warm start BASIC and
switch back to PETSCII mode.

### EDIT text modes

The built-in EDIT utility includes a character set mode switch: Press Control+E
to cycle through Upper/Graphic, Upper/Lower, and ISO mode.

## Special Keys

### RUN STOP

This key actually has two separate functions: "RUN" and "STOP". Holding
Shift+RUN will load the first program on your SD card and automatically run it.
If you are using the SD card that came with your Commander X16, this will print
some information on getting started with your computer.

If you are running a BASIC program, pressing STOP will stop the program.

### RESTORE

As mentioned above, RESTORE can be used with Control+Alt to perform a
warm start of BASIC. Less drastic than a cold boot, this stops a running
program and returns you to the `READY.` prompt. If you had a BASIC program
loaded, you can still re-start it with RUN or view it with LIST.

### Control+Alt_Delete

Yes, the Commander X16 has the famous "3 fingered salute." This performs a cold
boot of the computer, including a full power cycle. You will be returned to the
boot screen, and if you have an AUTOEXEC.X16, it will execute on startup.

### 40/80 DISPLAY

This switches the computer between 80x60 text mode and 40x30 text mode. 40x30
is more useful on CRT screens, so you may want to boot up into 40x30 mode. You
can set these modes with BASIC by typing

`SCREEN 1` or `SCREEN 3`.

Protip: you can force your computer to start in 40-column mode by modifying your
AUTOBOOT.X16 file:

```basic
LOAD "AUTOBOOT.X16"
0 SCREEN 3
SAVE "@:AUTOBOOT.X16"
BOOT
```

Don't worry, if you don't like this change, you can change it back:

```basic
LOAD "AUTOBOOT.X16"
SCREEN 1
SAVE "@:AUTOBOOT.X16"
BOOT
```

### F-KEYS

The F-keys, also known as the "Function Keys" are pre-loaded with special
shortcuts:

**F1** `LIST` Displays your currently loaded BASIC program.

**F2** `SAVE"@:` is a quick shortcut for saving a program. The @: allows you to
overwrite an existing file with the same name.

**F3** `LOAD "` helps you load a program. Protip: if you use @$ to get a
directory listing, you can then use the arrow keys to move up to a line with a
filename. Press F3 and press RETURN to load a file.

**F4** and RETURN swaps between 40 and 80 column screen modes.

**F5** `RUN` runs the currently loaded program

**F6** `MONITOR` Runs the machine monitor. The monitor allows you to directly
edit memory, view assembly language dumps, and even write short assembly
language programs at your keyboard.

**F7** `DOS"$` Lists the current directory

**F8** `DOS"` allows you to enter a disk command, such as CD:. More info can be
found in chapter 13.

## WHAT IS `PC  RA RO AC XR YR SP NV#BDIZC`?

There are times when the computer will drop to the MONITOR prompt. That looks
like this:

```text
C*
   PC  RA RO AC XR YR SP NV#BDIZC
.;E3BB 01 04 00 65 2B F6 ........
.█
```

This is the MONITOR screen. You can get there in BASIC by typing `MON`.

Type `X` and Enter to exit back to BASIC. If you just get bounced to MONITOR
again, then you'll need to Control+Alt+Restore or Control+Alt+Delete to restore
to a working state.

MONITOR is covered in [Chapter 7](X16%20Reference%20-%2007%20-%20Machine%20Language%20Monitor.md#chapter-6-machine-language-monitor).

<!-- For PDF formatting -->
<div class="page-break"></div>

# Chapter 3: Editor

The X16 has a built-in screen editor that is backwards-compatible with the C64, but has many new features.

## Modes

The editor's default mode is 80x60 text mode. The following text mode resolutions are supported:

| Mode | Description |
|------|-------------|
| $00  | 80x60 text  |
| $01  | 80x30 text  |
| $02  | 40x60 text  |
| $03  | 40x30 text  |
| $04  | 40x15 text  |
| $05  | 20x30 text  |
| $06  | 20x15 text  |
| $07  | 22x23 text  |
| $08  | 64x50 text  |
| $09  | 64x25 text  |
| $0A  | 32x50 text  |
| $0B  | 32x25 text  |
| $80  | 320x240@256c<br/>40x30 text |

Mode $80 contains two layers: a text layer on top of a graphics screen. In this mode, text color 0 is translucent instead of black.

To switch modes, use the BASIC statement `SCREEN` or the KERNAL API `screen_mode`. In the BASIC editor, the F4 key toggles between modes 0 (80x60) and 3 (40x30).

<!-- For PDF formatting -->
<div class="page-break"></div>

## ISO Mode

In addition to PETSCII, the X16 also supports the ISO-8859-15 character encoding. In ISO-8859-15 mode ("ISO mode"):

* The character set is switched from Commodore-style (with PETSCII drawing characters) to a new ASCII/ISO-8859-15 compatible set, which covers most Western European writing systems.
* The encoding (`CHR$()` in BASIC and `BSOUT` in machine language) now complies with ASCII and ISO-8859-15.
* The keyboard driver will return ASCII/ISO-8859-15 codes.

This is the encoding:

|        |x0 |x1 |x2 |x3 |x4 |x5 |x6 |x7 |x8 |x9 |xA |xB |xC |xD |xE |xF |
|--------|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| **0x** |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |
| **1x** |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |
| **2x** |   | ! | " | # | $ | % | & | ' | ( | ) | * | + | , | - | . | / |
| **3x** | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | : | ; | < | = | > | ? |
| **4x** | @ | A | B | C | D | E | F | G | H | I | J | K | L | M | N | O |
| **5x** | P | Q | R | S | T | U | V | W | X | Y | Z | [ | \ | ] | ^ | _ |
| **6x** | ` | a | b | c | d | e | f | g | h | i | j | k | l | m | n | o |
| **7x** | p | q | r | s | t | u | v | w | x | y | z | { | \| | } | ~ |   |
| **8x** |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |
| **9x** |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |
| **Ax** |   | ¡ | ¢ | £ | € | ¥ | Š | § | š | © | ª | « | ¬ | 🦋 | ® | ¯ |
| **Bx** | ° | ± | ² | ³ | Ž | µ | ¶ | · | ž | ¹ | º | » | Œ | œ | Ÿ | ¿ |
| **Cx** | À | Á | Â | Ã | Ä | Å | Æ | Ç | È | É | Ê | Ë | Ì | Í | Î | Ï |
| **Dx** | Ð | Ñ | Ò | Ó | Ô | Õ | Ö | × | Ø | Ù | Ú | Û | Ü | Ý | Þ | ß |
| **Ex** | à | á | â | ã | ä | å | æ | ç | è | é | ê | ë | ì | í | î | ï |
| **Fx** | ð | ñ | ò | ó | ô | õ | ö | ÷ | ø | ù | ú | û | ü | ý | þ | ÿ |

* The non-printable areas $00-$1F and $80-$9F in the character set are filled with inverted variants of the codes $40-$5F and $60-$7F, respectively.
* The code $AD is a non-printable soft hyphen in ISO-8859-15. The ROM character set contains the Commander X16 logo at this location.

ISO mode can be enabled and disabled using two new control codes:

* `CHR$($0F)`: enable ISO mode
* `CHR$($8F)`: enable PETSCII mode (default)

You can also enable ISO mode in direct mode by pressing Ctrl+`O`.

**Important:** In ISO mode, BASIC keywords need to be written in upper case, that is, they have to be entered with the Shift key down, and abbreviating keywords is no longer possible.

## Background Color

In regular BASIC text mode, the video controller supports 16 foreground colors and 16 background colors for each character on the screen.

The new "swap fg/bg color" code is useful to change the background color of the cursor, like this:

```basic
PRINT CHR$(1);   : REM SWAP FG/BG
PRINT CHR$($1C); : REM SET FG COLOR TO RED
PRINT CHR$(1);   : REM SWAP FG/BG
```

The new BASIC instruction `COLOR` makes this easier, but the trick above can also be used from machine code programs.

To set the background color of the complete screen, it just has to be cleared after setting the color:

```basic
PRINT CHR$(147);
```

## Scrolling

The C64 editor could only scroll the screen up (when overflowing the last line or printing or entering DOWN on the last line). The X16 editor scrolls both ways: When the cursor is on the first line and UP is printed or entered, the screen contents scroll down by a line.

## New Control Characters

This is the set of all supported PETSCII control characters. Entries in bold indicate new codes compared to the C64:

If there are two meanings listed, the first indicates input (a keypress) and the second indicates output.

| Code  |                            |                           | Code  |
|-------|----------------------------|---------------------------|-------|
| $00  | NULL                       | **VERBATIM MODE**         | $80  |
| $01  | **SWAP COLORS**            | COLOR: ORANGE             | $81  |
| $02  | **PAGE DOWN**              | **PAGE UP**               | $82  |
| $03  | STOP                       | RUN                       | $83  |
| $04  | **END**                    | **HELP**                  | $84  |
| $05  | COLOR: WHITE               | F1                        | $85  |
| $06  | **MENU**                   | F3                        | $86  |
| $07  | **BELL**                   | F5                        | $87  |
| $08  | DISALLOW CHARSET SW (SHIFT+ALT) | F7                        | $88  |
| $09  | **TAB** / ALLOW CHARSET SW | F2                        | $89  |
| $0A  | **LF**                     | F4                        | $8A  |
| $0B  | **LAYOUT SWAP**            | F6                        | $8B  |
| $0C  | -                          | F8                        | $8C  |
| $0D  | RETURN                     | SHIFTED RETURN            | $8D  |
| $0E  | CHARSET: LOWER/UPPER       | CHARSET: UPPER/PETSCII    | $8E  |
| $0F  | **CHARSET: ISO ON**        | **CHARSET: ISO OFF**      | $8F  |
| $10  | **F9**                     | COLOR: BLACK              | $90  |
| $11  | CURSOR: DOWN               | CURSOR: UP                | $91  |
| $12  | REVERSE ON                 | REVERSE OFF               | $92  |
| $13  | HOME                       | CLEAR                     | $93  |
| $14  | DEL (PS/2 BACKSPACE)       | INSERT                    | $94  |
| $15  | **F10**                    | COLOR: BROWN              | $95  |
| $16  | **F11**                    | COLOR: LIGHT RED          | $96  |
| $17  | **F12**                    | COLOR: DARK GRAY          | $97  |
| $18  | **SHIFT+TAB**              | COLOR: MIDDLE GRAY        | $98  |
| $19  | **FWD DEL (PS/2 DEL)**     | COLOR: LIGHT GREEN        | $99  |
| $1A  | -                          | COLOR: LIGHT BLUE         | $9A  |
| $1B  | ESC                        | COLOR: LIGHT GRAY         | $9B  |
| $1C  | COLOR: RED                 | COLOR: PURPLE             | $9C  |
| $1D  | CURSOR: RIGHT              | CURSOR: LEFT              | $9D  |
| $1E  | COLOR: GREEN               | COLOR: YELLOW             | $9E  |
| $1F  | COLOR: BLUE                | COLOR: CYAN               | $9F  |

**Notes:**

* $01: SWAP COLORS swaps the foreground and background colors in text mode
* \$07/\$09/\$0A/\$18/\$1B: have been added for ASCII compatibility. *[\$0A/\$18/\$1B do not have any effect on output. Outputs of \$08/\$09 have their traditional C64 effect]*
* \$80: VERBATIM MODE prints the next character (only!) as a glyph without interpretation. This is similar to quote mode, but also includes codes CR (\$0D) and DEL (\$14).
* F9-F12: these codes match the C65 additions
* $84: This code is generated when pressing SHIFT+END.
* Additionally, the codes \$04/\$06/\$0B/\$0C are interpreted when printing in graphics mode using `GRAPH_put_char`.

<!-- For PDF formatting -->
<div class="page-break"></div>

## Keyboard Layouts

The editor supports multiple keyboard layouts.

## Default Layout

On boot, the US layout (`ABC/X16`) is active:

* In PETSCII mode, it matches the US layout where possible, and can reach all PETSCII symbols.
* In ISO mode, it matches the Macintosh US keyboard and can reach all ISO-8859-15 characters. Some characters are reachable through key combinations:

| Key               | Result |
|-------------------|--------|
| Alt+`1`           | ¡      |
| Alt+`3`           | £      |
| Alt+`4`           | ¢      |
| Alt+`5`           | §      |
| Alt+`7`           | ¶      |
| Alt+`9`           | ª      |
| Alt+`0`           | º      |
| Alt+`q`           | œ      |
| Alt+`r`           | ®      |
| Alt+`t`           | Þ      |
| Alt+`y`           | ¥      |
| Alt+`o`           | ø      |
| Alt+`\`           | «      |
| Alt+`s`           | ß      |
| Alt+`d`           | ð      |
| Alt+`g`           | ©      |
| Alt+`l`           | ¬      |
| Alt+`'`           | æ      |
| Alt+`m`           | µ      |
| Alt+`/`           | ÷      |
| Shift+Alt+`2`     | €      |
| Shift+Alt+`8`     | °      |
| Shift+Alt+`9`     | ·      |
| Shift+Alt+`-`     | X16 logo |
| Shift+Alt+`=`     | ±      |
| Shift+Alt+`q`     | Œ      |
| Shift+Alt+`t`     | þ      |
| Shift+Alt+`\`     | »      |
| Shift+Alt+`a`     | ¹      |
| Shift+Alt+`d`     | Ð      |
| Shift+Alt+`k`     | X16 logo |
| Shift+Alt+`'`     | Æ      |
| Shift+Alt+`c`     | ³      |
| Shift+Alt+`b`     | ²      |
| Shift+Alt+`/`     | ¿      |

(The X16 logo is code point \\xad, SHY, soft-hyphen.)

The following combinations are dead keys:

* Alt+<tt>&#96;</tt>
* Alt+`6`
* Alt+`e`
* Alt+`u`
* Alt+`p`
* Alt+`a`
* Alt+`k`
* Alt+`;`
* Alt+`x`
* Alt+`c`
* Alt+`v`
* Alt+`n`
* Alt+`,`
* Alt+`.`
* Shift+Alt+`S`

They generate additional characters when combined with a second keypress:

| First <br/>Key      | Second <br/>Key | Result |
|--------------------|-----|---|
| Alt+<tt>&#96;</tt> | `a` | à |
| Alt+<tt>&#96;</tt> | `e` | è |
| Alt+<tt>&#96;</tt> | `i` | ì |
| Alt+<tt>&#96;</tt> | `o` | ò |
| Alt+<tt>&#96;</tt> | `u` | ù |
| Alt+<tt>&#96;</tt> | `A` | À |
| Alt+<tt>&#96;</tt> | `E` | È |
| Alt+<tt>&#96;</tt> | `I` | Ì |
| Alt+<tt>&#96;</tt> | `O` | Ò |
| Alt+<tt>&#96;</tt> | `U` | Ù |
| Alt+<tt>&#96;</tt> | `␣` | &#96; |
| Alt+`6`            | `e` | ê |
| Alt+`6`            | `u` | û |
| Alt+`6`            | `i` | î |
| Alt+`6`            | `o` | ô |
| Alt+`6`            | `a` | â |
| Alt+`6`            | `E` | Ê |
| Alt+`6`            | `U` | Û |
| Alt+`6`            | `I` | Î |
| Alt+`6`            | `O` | Ô |
| Alt+`6`            | `A` | Â |
| Alt+`e`            | `e` | é |
| Alt+`e`            | `y` | ý |
| Alt+`e`            | `u` | ú |
| Alt+`e`            | `i` | í |
| Alt+`e`            | `o` | ó |
| Alt+`e`            | `a` | á |
| Alt+`e`            | `E` | É |
| Alt+`e`            | `Y` | Ý |
| Alt+`e`            | `U` | Ú |
| Alt+`e`            | `I` | Í |
| Alt+`e`            | `O` | Ó |
| Alt+`e`            | `A` | Á |
| Alt+`u`            | `e` | ë |
| Alt+`u`            | `y` | ÿ |
| Alt+`u`            | `u` | ü |
| Alt+`u`            | `i` | ï |
| Alt+`u`            | `o` | ö |
| Alt+`u`            | `a` | ä |
| Alt+`u`            | `E` | Ë |
| Alt+`u`            | `Y` | Ÿ |
| Alt+`u`            | `U` | Ü |
| Alt+`u`            | `I` | Ï |
| Alt+`u`            | `O` | Ö |
| Alt+`u`            | `A` | Ä |
| Alt+`p`            | `␣` | , |
| Alt+`a`            | `␣` | ¯ |
| Alt+`k`            | `a` | å |
| Alt+`k`            | `A` | Å |
| Alt+`x`            | `␣` | . |
| Alt+`c`            | `c` | ç |
| Alt+`c`            | `C` | Ç |
| Alt+`v`            | `s` | š |
| Alt+`v`            | `z` | ž |
| Alt+`v`            | `S` | Š |
| Alt+`v`            | `Z` | Ž |
| Alt+`n`            | `o` | õ |
| Alt+`n`            | `a` | ã |
| Alt+`n`            | `n` | ñ |
| Alt+`n`            | `O` | Õ |
| Alt+`n`            | `A` | Ã |
| Alt+`n`            | `N` | Ñ |
| Shift+Alt+`s`      | `␣` | \\xa0 |
| Shift+Alt+`;`      | `=` | × |

"␣" denotes the space bar.

### ROM Keyboard Layouts

The following keyboard layouts are available from ROM. You can select one directly with the BASIC `KEYMAP` command, e.g. `KEYMAP"ABC/X16"`, or via the X16 Control Panel with the BASIC `MENU` command.

| Identifier  | Description                         | Code                                       |
|-------------|-------------------------------------|--------------------------------------------|
| `ABC/X16`   | ABC - Extended (X16)                | -                                          |
| `EN-US/INT` | United States - International       | [00020409](http://kbdlayout.info/00020409) |
| `EN-GB`     | United Kingdom                      | [00000809](http://kbdlayout.info/00000809) |
| `SV-SE`     | Swedish                             | [0000041D](http://kbdlayout.info/0000041D) |
| `DE-DE`     | German                              | [00000407](http://kbdlayout.info/00000407) |
| `DA-DK`     | Danish                              | [00000406](http://kbdlayout.info/00000406) |
| `IT-IT`     | Italian                             | [00000410](http://kbdlayout.info/00000410) |
| `PL-PL`     | Polish (Programmers)                | [00000415](http://kbdlayout.info/00000415) |
| `NB-NO`     | Norwegian                           | [00000414](http://kbdlayout.info/00000414) |
| `HU-HU`     | Hungarian                           | [0000040E](http://kbdlayout.info/0000040E) |
| `ES-ES`     | Spanish                             | [0000040A](http://kbdlayout.info/0000040A) |
| `FI-FI`     | Finnish                             | [0000040B](http://kbdlayout.info/0000040B) |
| `PT-BR`     | Portuguese (Brazil ABNT)            | [00000416](http://kbdlayout.info/00000416) |
| `CS-CZ`     | Czech                               | [00000405](http://kbdlayout.info/00000405) |
| `JA-JP`     | Japanese                            | [Custom IME](https://github.com/X16Community/x16-rom/pull/364) (since r49) |
| `FR-FR`     | French                              | [0000040C](http://kbdlayout.info/0000040C) |
| `DE-CH`     | Swiss German                        | [00000807](http://kbdlayout.info/00000807) |
| `EN-US/DVO` | United States - Dvorak              | [00010409](http://kbdlayout.info/00010409) |
| `ET-EE`     | Estonian                            | [00000425](http://kbdlayout.info/00000425) |
| `FR-BE`     | Belgian French                      | [0000080C](http://kbdlayout.info/0000080C) |
| `EN-CA`     | Canadian French                     | [00001009](http://kbdlayout.info/00001009) |
| `IS-IS`     | Icelandic                           | [0000040F](http://kbdlayout.info/0000040F) |
| `PT-PT`     | Portuguese                          | [00000816](http://kbdlayout.info/00000816) |
| `HR-HR`     | Croatian                            | [0000041A](http://kbdlayout.info/0000041A) |
| `SK-SK`     | Slovak                              | [0000041B](http://kbdlayout.info/0000041B) |
| `SL-SI`     | Slovenian                           | [00000424](http://kbdlayout.info/00000424) |
| `LV-LV`     | Latvian                             | [00000426](http://kbdlayout.info/00000426) |
| `LT-LT`     | Lithuanian IBM                      | [00000427](http://kbdlayout.info/00000427) |

All remaining keyboards are based on the respective Windows layouts. `EN-US/INT` differs from `EN-US` only in Alt/AltGr combinations and some dead keys.

The BASIC command `KEYMAP` allows activating a specific keyboard layout. It can be added to the auto-boot file, e.g.:

```basic
10 KEYMAP"NB-NO"
SAVE"AUTOBOOT.X16
```

PETSCII code 11 ($0B) or Ctrl+K is used to toggle between the current keyboard layout and the previously loaded one.  This function can be activated by pressing Ctrl+K in the BASIC editor or by sending the code to the screen with the BASIC PRINT command or the CHROUT KERNAL API call.  The layout swap function works only with built-in ROM-based layouts and will not properly swap back to a custom layout in RAM.

### Loadable Keyboard Layouts

The tables for the active keyboard layout reside in banked RAM, at $A000 on bank 0:

| Addresses     | Description |
|---------------|-------------|
| \$A000-\$A07F | Table 0     |
| \$A080-\$A0FF | Table 1     |
| \$A100-\$A17F | Table 2     |
| \$A180-\$A1FF | Table 3     |
| \$A200-\$A27F | Table 4     |
| \$A280-\$A07F | Table 5     |
| \$A300-\$A37F | Table 6     |
| \$A380-\$A3FF | Table 7     |
| \$A400-\$A47F | Table 8     |
| \$A480-\$A4FF | Table 9     |
| \$A500-\$A57F | Table 10    |
| \$A580-\$A58F | big-endian bitfield:<br/>keynum codes for which Caps means Shift |
| \$A590-\$A66F | dead key table |
| \$A670-\$A67E | ASCIIZ identifier (e.g. "ABC/X16") |

The first byte of each of the 11 tables is the table ID which contains the encoding and the combination of modifiers that this table is for.

| Bit | Description        |
|-----|--------------------|
| 7   | 0: PETSCII, 1: ISO |
| 6-3 | always 0           |
| 2   | Ctrl               |
| 1   | Alt                |
| 0   | Shift              |

* AltGr is represented by Ctrl+Alt.
* ID $C6 represents Alt _or_ AltGr (ISO only)
* ID $C7 represents Shift+Alt _or_ Shift+AltGr (ISO only)
* Empty tables have an ID of $FF.

The identifier is followed by 127 output codes for the keynum inputs 1-127.

* Dead keys (i.e. keys that don't generate anything by themselves but modify the next key) have a code of 0 and are further described in the dead key table (ISO only)
* Keys that produce nothing have an entry of 0. (They can be distinguished from dead keys as they don't have an entry in the dead key table.)

The dead key table has one section for every dead key with the following layout:

| Byte | Description                                  |
|------|----------------------------------------------|
| 0    | dead key ID (PETSCII/ISO and Shift/Alt/Ctrl) |
| 1    | dead key scancode                            |
| 2    | full length of this table in bytes           |
| 3    | first additional key ISO code                |
| 4    | first effective key ISO code                 |
| 5    | second additional key ISO code               |
| 6    | second effective key ISO code                |
| ...  | ...                                          |
| n-1  | terminator 0xFF                              |

Custom layouts can be loaded from disk like this:

```BASIC
BLOAD"KEYMAP",8,0,$A000
```

Here is an example that activates a layout derived from "ABC/X16", with unshifted Y and Z swapped in PETSCII mode:

```BASIC
100 KEYMAP"ABC/X16"                               :REM START WITH DEFAULT LAYOUT
110 BANK 0                                        :REM ACTIVATE RAM BANK 0
120 FORI=0TO11:B=$A000+128*I:IFPEEK(B)<>0THENNEXT :REM SEARCH FOR TABLE $00
130 POKEB+$2E,ASC("Y")                            :REM SET KEYNUM $2E ('Z') to 'Y'
140 POKEB+$16,ASC("Z")                            :REM SET KEYNUM $16 ('Y') to 'Z'
170 REM
180 REM *** DOING THE SAME FOR SHIFTED CHARACTERS
190 REM *** IS LEFT AS AN EXERCISE TO THE READER
```

### Custom BASIN PETSCII code override handler

**Note**: This behavior only exists in R44 or later

Some use cases of the BASIN (CHRIN) API call may benefit from being able to modify its behavior, such as intercepting or redirecting certain PETSCII codes.  The Machine Language Monitor uses this mechanism to implement custom behavior for F-keys and for loading additional disassembly or memory display when scrolling the screen.

To set up a custom handler, one must configure it before each call to BASIN.

The key handler vector is in RAM bank 0 at addresses $ac03-$ac05.  The first two bytes are the call address, and the next byte is the RAM or ROM bank.  If your callback routine is in low ram, specifying the bank in $ac05 is not necessary.

The editor will call your callback for every keystroke received and pass the PETSCII code in the A register with carry set.  If your handler does not want to override, simply return with carry set.

If you do wish to override, return with carry clear.  The editor will then unblink the cursor and call your callback a second time with carry clear _for the same PETSCII code_.  This is your opportunity to override. Before returning, you are free to update the screen or perform other KERNAL API calls (with the exception of BASIN). At the end of your routine, set `A` to the PETSCII code you wish the editor to process. If you wish to suppress the input keystroke, set `A` to `0`.

```ASM
ram_bank = $00
edkeyvec = $ac03
edkeybk  = $ac05

BASIN    = $ffcf
BSOUT    = $ffd2

.segment "ONCE"
.segment "STARTUP"
    jmp start
.segment "CODE"

keyhandler:
    bcs @check
    cmp #$54 ; 'T'
    bne :+
    lda #$57 ; 'W'
    rts
:   lda #$54 ; 'T'
    rts
@check:
    cmp #$54 ; 'T'
    beq @will_override
    cmp #$57 ; 'W'
    beq @will_override
    sec
    rts
@will_override:
    clc
    rts

enable_basin_callback:
    lda ram_bank
    pha
    stz ram_bank ; RAM bank 0 contains the handler vector
    php
    sei
    lda #<keyhandler
    sta edkeyvec
    lda #>keyhandler
    sta edkeyvec+1
    ; setting the bank is optional and unnecessary
    ; if the handler is in low RAM.
    ; lda #0
    ; sta edkeybk
    plp
    pla
    sta ram_bank
    rts

start:
    jsr enable_basin_callback
    ; T and W are swapped
@1: jsr BASIN
    cmp #13
    bne @1
    jsr BSOUT
    ; normal BASIN
@2: jsr BASIN
    cmp #13
    bne @2

    rts

```

### Custom Keyboard Keynum Code Handler

**Note**: This behavior is for R43 or later, differing from previous releases.

If you need more control over the translation of keynum codes into PETSCII/ISO codes, or if you need to intercept any key down or up event, you can hook the custom scancode handler vector at $032E/$032F.

On all key down and key up events, the keyboard driver calls this vector with

* .A: keycode, where bit 7 (most-significant) is clear on key down, and set on key up.

The keynum codes are enumerated [here](https://github.com/X16Community/x16-rom/blob/master/inc/keycode.inc), and their names, similar to that of PS/2 codes, are based on their function in the US layout.

The handler needs to return a key event the same way in .A

* To remove a keypress so that it is not added to the keyboard queue, return .A = 0.
* To manually add a key to the keyboard queue, use the `kbdbuf_put` KERNAL API.

You can even write a completely custom keyboard translation layer:

* Place the code at $A000-$A58F in RAM bank 0. This is safe, since the tables won't be used in this case, and the active RAM bank will be set to 0 before entry to the handler.
* Fill the locale at $A590.
* For every keynum that should produce a PETSCII/ISO code, use `kbdbuf_put` to store it in the keyboard buffer.
* Always set .A = 0 before return from the custom handler.

```ASM
;EXAMPLE: A custom handler that prints "A" on Alt key down

setup:
    sei
    lda #<keyhandler
    sta $032e
    lda #>keyhandler
    sta $032f
    cli
    rts

keyhandler:
    pha

    and #$ff    ;ensure A sets flags
    bmi exit    ;A & 0x80 is key up

    cmp #$3c    ;Left Alt keynum
    bne exit

    lda #'a'
    jsr $ffd2

exit:
    pla
    rts
```

### Function Key Shortcuts

The following Function key macros are pre-defined for your convenience. These shortcuts only work in the screen editor. When a program is running, the F-keys generate the corresponding PETSCII character code.

| Key | Function   | Comment   |
|-----|------------|-----------|
| F1  | `LIST:`    | Lists the current program |
| F2  | `SAVE"@:`  | Press F2 and then type a filename to save your program. The `@:` instructs DOS to allow overwrite. |
| F3  | `LOAD "`   | Load a file directly, or cursor up over a file listing and press F3 to load a program. |
| F4  | 40/80      | Toggles between 40 and 80 column screen modes, clearing the screen. Pressing return is required to prevent accidental mode switches. |
| F5  | `RUN:`     | Run the current program. |
| F6  | `MONITOR`  | Opens the Supermon machine language monitor. |
| F7  | `DOS"$<cr>`| Displays a directory listing. |
| F8  | `DOS"`     | Issue DOS commands. |
| F9  | -          | Not defined.  Formerly cycled through keyboard layouts. Instead, use the `MENU` command to enter the X16 Control Panel, select one, and optionally save the layout as a boot preference. |
| F10 | -          | Not defined |
| F11 | -          | Not defined |
| F12 | debug      | debug features in emulators |

<!-- For PDF formatting -->
<div class="page-break"></div>
# Chapter 4: BASIC Programming

<!--
********************************************************************************
NOTICE: This file uses two trailing spaces on some lines to indicate line breaks
for GitHub's Markdown flavor. Do not remove!
********************************************************************************
New styling features were used in this document and may not render correctly  
when viewed on github.  PDF output appears correct.
-->

## Table of BASIC Statements and Functions

| Keyword | Type | Summary | Origin |
| - | - | - | - |
| [`ABS`](#abs)  | Numeric Function | Returns absolute value of a number | C64 |
| [`AND`](#and) | Operator | Returns boolean "AND" or bitwise intersection | C64 |
| [`ASC`](#asc) | Numeric Function | Returns numeric PETSCII value from string | C64 |
| [`ATN`](#atn) | Numeric Function | Returns arctangent of a number | C64 |
| [`BANK`](#bank) | Command | Sets the RAM and ROM banks to use for PEEK, POKE, and SYS | C128 |
| [`BASLOAD`](#bank) | Command | Load and tokenize a BASLOAD (.basl) text file | X16 |
| [`BIN$`](#bin) | String Function | Converts numeric to a binary string | X16 |
| [`BINPUT#`](#binput) | I/O Statement | Reads a fixed-length block of data from an open file | X16 |
| [`BLOAD`](#bload) | Command | Loads a headerless binary file from disk to a memory address | X16 |
| [`BOOT`](#boot) | Command | Loads and runs `AUTOBOOT.X16` | X16 |
| [`BSAVE`](#bsave) | Command | Saves a headerless copy of a range of memory to a file | X16 |
| [`BVERIFY`](#bverify) | Command | Verifies that a file on disk matches RAM contents | X16 |
| [`BVLOAD`](#bvload) | Command | Loads a headerless binary file from disk to VRAM | X16 |
| [`CHAR`](#char) | Command | Draws a text string in graphics mode | X16 |
| [`CHR$`](#chr) | String Function | Returns PETSCII character from numeric value | C64 |
| [`CLOSE`](#close) | I/O Statement | Closes a logical file number | C64 |
| [`CLR`](#clr) | Statement | Clears BASIC variable state | C64 |
| [`CLS`](#cls) | Statement | Clears the screen | X16 |
| [`CMD`](#cmd) | I/O Statement | Redirects output to non-screen device | C64 |
| [`COLOR`](#color) | Statement | Sets text foreground and background color | X16 |
| [`CONT`](#cont) | Command | Resumes execution of a BASIC program | C64 |
| [`COS`](#cos) | Function | Returns cosine of an angle in radians | C64 |
| [`DA$`](#da$) | String Function | Returns the date in YYYYMMDD format from the system clock | X16 |
| [`DATA`](#data) | Statement | Declares one or more constants | C64 |
| [`DEF FN`](#def-fn) | Statement | Defines a function for use later in BASIC | C64 |
| [`DIM`](#dim) | Statement | Allocates storage for an array | C64 |
| [`DOS`](#dos) | Command | Disk and SD card directory operations | X16 |
| [`EDIT`](#edit) | Command | Open the built-in text editor | X16 |
| [`END`](#end) | Statement | Terminate program execution and return to `READY.` | C64 |
| [`EXEC`](#exec) | Command | Play back a script from RAM into the BASIC editor | X16 |
| [`EXP`](#exp) | Function | Returns the inverse natural log of a number | C64 |
| [`FMCHORD`](#fmchord) | Statement | Start or stop simultaneous notes on YM2151 | X16 |
| [`FMDRUM`](#fmdrum) | Statement | Plays a drum sound on YM2151 | X16 |
| [`FMFREQ`](#fmfreq) | Statement | Plays a frequency in Hz on YM2151 | X16 |
| [`FMINIT`](#fminit) | Statement | Stops sound and reinitializes YM2151 | X16 |
| [`FMINST`](#fminst) | Statement | Loads a patch preset into a YM2151 channel | X16 |
| [`FMNOTE`](#fmnote) | Statement | Plays a musical note on YM2151 | X16 |
| [`FMPAN`](#fmpan) | Statement | Sets stereo panning on YM2151 | X16 |
| [`FMPLAY`](#fmplay) | Statement | Plays a series of notes on YM2151 | X16 |
| [`FMPOKE`](#fmpoke) | Statement | Writes a value into a YM2151 register | X16 |
| [`FMVIB`](#fmvib) | Statement | Controls vibrato and tremolo on YM2151 | X16 |
| [`FMVOL`](#fmvol) | Statement | Sets channel volume on YM2151 | X16 |
| [`FN`](#fn) | Function | Calls a previously defined function | C64 |
| [`FOR-TO-STEP`](#for-to-step) | Statement | Declares the start of a loop construct | C64 |
| [`FRAME`](#frame) | Statement | Draws an unfilled rectangle in graphics mode | X16 |
| [`FRE`](#fre) | Function | Returns the number of unused BASIC bytes free | C64 |
| [`GET`](#get) | Statement | Polls the keyboard cache for a single keystroke | C64 |
| [`GET#`](#get-1) | I/O Statement | Polls an open logical file for a single character | C64 |
| [`GOSUB`](#gosub) | Statement | Jumps to a BASIC subroutine | C64 |
| [`GOTO`](#goto) | Statement | Branches immediately to a line number | C64 |
| [`HELP`](#help) | Command | Displays a brief summary of online help resources | X16 |
| [`HEX$`](#hex) | String Function | Converts numeric to a hexadecimal string | X16 |
| [`I2CPEEK`](#i2cpeek) | Function | Reads a byte from a device on the I²C bus | X16 |
| [`I2CPOKE`](#i2cpoke) | Statement | Writes a byte to a device on the I²C bus | X16 |
| [`IF-THEN`](#if-then) | Statement | Tests a boolean condition and branches on result | C64 |
| [`INPUT`](#input) | Statement | Reads a line or values from the keyboard | C64 |
| [`INPUT#`](#input-1) | I/O Statement | Reads lines or values from a logical file | C64 |
| [`INT`](#int) | Integer Function | Discards the fractional part of a number | C64 |
| [`JOY`](#joy) | Integer Function | Reads gamepad button state | X16 |
| [`KEYMAP`](#keymap) | Command | Changes the keyboard layout | X16 |
| [`LEFT$`](#left) | String Function | Returns a substring starting from the beginning of a string | C64 |
| [`LEN`](#len) | Integer Function | Returns the length of a string | C64 |
| [`LET`](#let) | Statement | Explicitly declares a variable | C64 |
| [`LINE`](#line) | Statement | Draws a line in graphics mode | X16 |
| [`LINPUT`](#linput) | Statement | Reads a line from the keyboard | X16 |
| [`LINPUT#`](#linput-1) | I/O Statement | Reads a line or other delimited data from an open file | X16 |
| [`LIST`](#list) | Command | Outputs the program listing to the screen | C64 |
| [`LOAD`](#load) | Command | Loads a program from disk into memory | C64 |
| [`LOCATE`](#locate) | Statement | Moves the text cursor to new location | X16 |
| [`LOG`](#log) | Floating-Point Function | Returns the natural logarithm of a number | C64 |
| [`MENU`](#menu) | Command | Invokes the Commander X16 utility menu | X16 |
| [`MID$`](#mid) | String Function | Returns a substring from the middle of a string | C64 |
| [`MOD`](#mod) | Function | Returns the truncated remainder of a division | X16 |
| [`MON`](#mon) | Command | Enters the machine language monitor | X16 |
| [`MOUSE`](#mouse) | Statement | Hides or shows mouse pointer | X16 |
| [`MOVSPR`](#movspr) | Statement | Set the X/Y position of a sprite | X16 |
| [`MX/MY/MB`](#mxmymb) | variable | Reads the mouse position and button state | X16 |
| [`MWHEEL`](#mwheel) | variable | Reads the mouse wheel movement | X16 |
| [`NEW`](#new) | Command | Resets the state of BASIC and clears program memory | C64 |
| [`NEXT`](#next) | Statement | Declares the end of a loop construct | C64 |
| [`NOT`](#not) | Logical Operator | Bitwise or boolean inverse | C64 |
| [`OLD`](#old) | Command | Undoes a NEW command or warm reset | X16 |
| [`ON`](#on) | Statement | A GOTO/GOSUB table based on a variable value | C64 |
| [`OPEN`](#open) | I/O Statement | Opens a logical file to disk or other device | C64 |
| [`OR`](#or) | Logical Operator | Bitwise or boolean "OR" | C64 |
| [`OVAL`](#oval) | Statement | Draws a filled oval in graphics mode | X16 |
| [`PEEK`](#peek) | Function | Returns a value from a memory address | C64 |
| `π` | Function | Returns the constant for the value of pi | C64 |
| [`POINTER`](#pointer) | Function | Returns the address of a BASIC variable | C128 |
| [`POKE`](#poke) | Statement | Assigns a value to a memory address | C64 |
| [`POS`](#pos) | Integer Function | Returns the column position of the text cursor | C64 |
| [`POWEROFF`](#poweroff) | Command | Immediately powers down the Commander X16 | X16 |
| [`PRINT`](#print) | Statement | Prints data to the screen or other output | C64 |
| [`PRINT#`](#print-1) | I/O Statement | Prints data to an open logical file | C64 |
| [`PSET`](#pset) | Statement | Changes a pixel's color in graphics mode | X16 |
| [`PSGCHORD`](#psgchord) | Statement | Starts or stops simultaneous notes on VERA PSG | X16 |
| [`PSGFREQ`](#psgfreq) | Statement | Plays a frequency in Hz on VERA PSG | X16 |
| [`PSGINIT`](#psginit) | Statement | Stops sound and reinitializes VERA PSG | X16 |
| [`PSGNOTE`](#psgnote) | Statement | Plays a musical note on VERA PSG | X16 |
| [`PSGPAN`](#psgpan) | Statement | Sets stereo panning on VERA PSG | X16 |
| [`PSGPLAY`](#psgplay) | Statement | Plays a series of notes on VERA PSG | X16 |
| [`PSGVOL`](#psgvol) | Statement | Sets voice volume on VERA PSG | X16 |
| [`PSGWAV`](#psgwav) | Statement | Sets waveform on VERA PSG | X16 |
| [`READ`](#read) | Statement | Assigns the next `DATA` constant to one or more variables | C64 |
| [`REBOOT`](#reboot) | Command | Performs a warm reboot of the system | X16 |
| [`RECT`](#rect) | Statement | Draws a filled rectangle in graphics mode | X16 |
| [`REM`](#rem) | Statement | Declares a comment | C64 |
| [`REN`](#ren) | Command | Renumbers a BASIC program | X16 |
| [`RESET`](#reset) | Command | Performs a hard reset of the system | X16 |
| [`RESTORE`](#restore) | Statement | Resets the `READ` pointer to a `DATA` constant | C64 |
| [`RETURN`](#return) | Statement | Returns from a subroutine to the statement following a GOSUB | C64 |
| [`RIGHT$`](#right) | String Function | Returns a substring from the end of a string | C64 |
| [`RING`](#ring) | Statement | Draws an oval outline in graphics mode | X16 |
| [`RND`](#rnd) | Floating-Point Function | Returns a floating point number 0 <= n < 1 | C64 |
| [`RPT$`](#rpt) | String Function | Returns a string of repeated characters | X16 |
| [`RUN`](#run) | Command | Clears the variable state and starts a BASIC program | C64 |
| [`SAVE`](#save) | Command | Saves a BASIC program from memory to disk | C64 |
| [`SCREEN`](#screen) | Statement | Selects a text or graphics mode | X16 |
| [`SGN`](#sgn) | Integer Function | Returns the sign of a numeric value | C64 |
| [`SIN`](#sin) | Floating-Point Function | Returns the sine of an angle in radians | C64 |
| [`SLEEP`](#sleep) | Statement | Introduces a delay in program execution | X16 |
| [`SPC`](#spc) | Special Function | Returns a string with a set number of spaces | C64 |
| [`SPRITE`](#sprite) | Statement | Sets attributes for a sprite including visibility | X16 |
| [`SPRMEM`](#sprmem) | Statement | Set the VRAM address for a sprite's visual data | X16 |
| [`SQR`](#sqr) | Floating-Point Function | Returns the square root of a numeric value | C64 |
| [`ST`](#st) | Integer Function | Returns the status of certain DOS/peripheral operations | C64 |
| [`STEP`](#step) | Statement | Used in a `FOR` declaration to declare the iterator step | C64 |
| [`STOP`](#stop) | Statement | Breaks out of a BASIC program | C64 |
| [`STR$`](#str) | String Function | Converts a numeric value to a string | C64 |
| [`STRPTR`](#strptr) | Function | Returns the address of a BASIC string | X16 |
| [`SYS`](#sys) | Command | Transfers control to machine language at a memory address | C64 |
| [`TAB`](#tab) | Special Function | Returns a string with spaces used for column alignment | C64 |
| [`TAN`](#tan) | Floating-Point Function | Return the tangent for an angle in radians | C64 |
| [`TATTR`](#tattr) | Function | Returns a tile attribute from the tile/text layer | X16 |
| [`TDATA`](#tdata) | Function | Returns a tile from the tile/text layer | X16 |
| [`TILE`](#tile) | Command | Changes a tile or character on the tile/text layer | X16 |
| [`TIME`](#time) | Numeric Function | Returns the jiffy timer value | C64 |
| [`TIME$`](#time-1) | String Function | Returns the time HHMMSS from the system clock | C64 |
| [`USR`](#usr) | Floating-Point Function | Call a user-defined function in machine language | C64 |
| [`VAL`](#val) | Numeric Function | Parse a string to return a numeric value | C64 |
| [`VERIFY`](#verify) | Command | Verify that a BASIC program was written to disk correctly | C64 |
| [`VPEEK`](#vpeek) | Function | Returns a value from VERA's VRAM | X16 |
| [`VPOKE`](#vpoke) | Statement | Sets a value in VERA's VRAM | X16 |
| [`VLOAD`](#vload) | Statement | Loads a file to VERA's VRAM | X16 |
| [`WAIT`](#wait) | Statement | Waits for a memory location to match a condition | C64 |

## Commodore 64 Compatibility

The Commander X16 BASIC interpreter is 100% backwards-compatible with the Commodore 64 one. This includes the following features:

* All statements and functions
* Strings, arrays, integers, floats
* Max. 80 character BASIC lines
* Printing control characters like cursor control and color codes, e.g.:
  * `CHR$(147)`: clear screen
  * `CHR$(5)`: white text
  * `CHR$(18)`: reverse
  * `CHR$(14)`: switch to upper/lowercase font
  * `CHR$(142)`: switch to uppercase/graphics font
* The BASIC vector table ($0300-$030B, $0311/$0312)
* [`SYS`](#sys) arguments in RAM

Because of the differences in hardware, the following functions and statements are incompatible between C64 and X16 BASIC programs.

* [`POKE`](#poke): write to a memory address
* [`PEEK`](#peek): read from a memory address
* [`WAIT`](#wait): wait for memory contents
* [`SYS`](#sys): execute machine language code (when used with ROM code)

The BASIC interpreter also currently shares all problems of the C64 version, like the slow garbage collector.

## Saving Files

By default, you cannot automatically overwrite a file with [`SAVE`](#save), [`BSAVE`](#bsave), or [`OPEN`](#open). To overwrite a file, you must prefix the filename with `@:`, like this: `SAVE "@:HELLO WORLD"`. (`"@0:filename"` is also acceptable.)

This follows the Commodore convention, which extended to all of their diskette drives and third party hard drives and flash drive readers.

Always confirm you have successfully saved a file by checking the DOS status. When you use the SAVE command from Immediate (or Direct) mode, the system does this for you. In Program mode, you have to do it yourself.

There are two ways to check the error channel from inside a program:

1. You can use the [`DOS`](#dos) command and make the user perform actions necessary to recover from an error (such as re-saving the file with an @: prefix).
2. You can read the error yourself, using the following BASIC code:

```BASIC
10 OPEN 15,8,15
20 INPUT#15,A,B$
30 PRINT A;B$
40 CLOSE 15
```

Refer to [Chapter 13](X16%20Reference%20-%2013%20-%20Working%20with%20CMDR-DOS.md#chapter-13-working-with-cmdr-dos) for more details on CMDR-DOS and the command channel.

## New Statements and Functions

There are several new statement and functions. Note that all BASIC keywords (such as [`FOR`](#for-to-step)) get converted into tokens (such as `$81`), and the tokens for the new keywords have likely shifted from one ROM version to the next. Therefore, loading BASIC program saved from an old revision of BASIC may mix up keywords. As of ROM version R42, the keyword token positions should no longer shift and programs saved in R42 BASIC should be compatible with future versions.

### ABS

**TYPE: Integer Function**  
**FORMAT: ABS(&lt;expression&gt;)**

**Action:** Returns the absolute value of the given expression, which is its value without a sign.

**EXAMPLE of the ABS Function:**

```BASIC
PRINT ABS(-24)
 24

PRINT ABS(50)
 50
```

### AND

**TYPE: Operator**  
**FORMAT: &lt;expression&gt; AND &lt;expression&gt;**

**Action:** `AND` is used in Boolean operations to test bits.  It can also be used in operations 
to check the truth of both operands.

In Boolean algebra, the result of an `AND` operation is 1 only if both numbers being `AND`ed are 1.  The result is 
0 if either or both operands is 0 (false).

**Simple 1 bit truth table for AND**

|  |  |  |  |  |
| :-- | --: | --: | --: | --: |
| Operand 1 | 0 | 1 | 0 | 1 |
| Operand 2 | 0 | 0 | 0 | 1 |
| Result | 0 | 0 | 0 | 1 |

The Commander X16 BASIC can perform the `AND` operation on numbers in the range -32768 to +32767.  Any fractional values are ignored, and numbers beyond the stated range will cause an `?ILLEGAL QUANTITY` error.  When converted to binary format, the range allowed yields 16 bits for each operand.  Corresponding bits are ANDed together, forming a 16 bit result in the same range.

**EXAMPLES of 16 bit AND Operation:**

```
                                37
                           AND 123
               0000 0000 0010 0101
               0000 0000 0111 1011
Binary Result: 0000 0000 0010 0001
Decimal Result: 33

                                 3
                         AND 21432
               0101 0011 1011 1000
               0000 0000 0000 0011
Binary Result: 0000 0000 0000 0000
Decimal Result: 0

```
When evaluating a number for true or false, the computer assumes the number is true as long as its value isn't 0.  When evaluating a comparison, it assigns a value of -1 if the result is true, while false has a value of 0.  In binary format, -1 is all 1's and 0 is all 0's.  Therefore, when ANDing true/false evaluations, the result will be true if any bits in the result are true.

**EXAMPLES of the AND Operator:**

```BASIC
10 REM Test, set, and clear specific bits in a value
20 A = 321
30 IF A AND 7 THEN PRINT "BIT 7 IS SET"
40 A = A OR 5 : REM Set bit 5
50 IF A AND 5 THEN PRINT "BIT 5 IS SET"
60 A = A AND (255 - 7) : REM Clear bit 7
70 IF NOT A AND 7 THEN PRINT "BIT 7 IS NOT SET"
```

```BASIC
10 REM True/False evaluations.
20 IF A=21 AND B=30 THEN GOTO 40: REM only true if both are true.
30 IF Z AND M=8 THEN GOTO 40: REM True if A is non-zero and M=8 is true.
40 PRINT "DONE."
```

### ASC

**TYPE: Integer Function**  
**FORMAT: ASC(&lt;string&gt;)**

**Action:** Returns an integer value representing the [PETSCII](X16%20Reference%20-%20Appendix%20I%20-%20Character%20Sets.md#pet-uppercase--graphics) code for the first character of &lt;string&gt;. If &lt;string&gt; is an empty ("") string, `ASC` returns 0.

**EXAMPLE of the ASC Function:**

```BASIC
PRINT ASC("A")
 65

PRINT ASC("")
 0
```

### ATN

**TYPE: Integer Function**  
**FORMAT: ATN(&lt;number&gt;)**

**Action:** This mathematical function returns the arctangent of the number given.  The result is the angle (in radians) whose tangent is the number given.  The result is always in the range -&pi; / 2 to +&pi; / 2.

**EXAMPLES of the ATN Function:**

```BASIC
10 PRINT ATN(5)
20 A=ATN(Z) * 180 / PI; : REM Convert to degrees.
```

### BANK

**TYPE: Command**  
**FORMAT: BANK m[,n]**

**Action:** Set the active RAM (m) and ROM bank (n) for the purposes of [`PEEK`](#peek), [`POKE`](#poke), and [`SYS`](#sys).  Specifying the ROM bank is optional. If it is not specified, its previous value is retained.

**EXAMPLE of the BANK Statement:**

```BASIC
BANK 1,10    : REM SETS THE RAM BANK TO 1 AND THE ROM BANK TO 10
PRINT PEEK($A000) : REM PRINTS OUT THE VALUE STORED IN $A000 IN RAM BANK 1
SYS $C063    : REM CALLS ROUTINE AT $C09F IN ROM BANK 10 AUDIO (YM_INIT)
```

Note: In the above example, the `SYS $C063` in ROM bank 10 is a call to [ym_init](X16%20Reference%20-%2011%20-%20Sound%20Programming.md#audio-api-routines), which does the first half of what the BASIC command [`FMINIT`](#fminit) does, without setting any default instruments. It is generally not recommended to call routines in ROM directly this way, and most BASIC programmers will never have a need to call [`SYS`](#sys) directly, but advanced users may find a good reason to do so.

Note: BANK uses its own register to store the command's desired bank numbers; this will not always be the same as the value stored in `$00` or `$01`. In fact, `$01` is always going to read `4` when PEEKing from BASIC. If you need to know the currently selected RAM and/or RAM banks, you should explicitly set them and use variables to track your selected bank number(s).

Note: Memory address `$00`, which is the hardware RAM bank register, will usually report the bank set by the `BANK` statement. The one exception is after a [`BLOAD`](#bload) or [`BVERIFY`](#bverify) inside of a running BASIC program.  `BLOAD` and `BVERIFY` change the RAM bank (as if you called `BANK`) to the bank that `BLOAD` or `BVERIFY` stopped at.

### BASLOAD

**TYPE: Command**  
**FORMAT: BASLOAD &lt;filename&gt;[,<device>]**

**Action:** Loads a plain text file with `BASLOAD` source and converts it into a runnable program.

The device number is optional.  If it's not specified, the current device is used.  The current device is set to 8 at system boot and may be changed with the [`DOS`](#dos) command.

For more information about `BASLOAD`, see [this external documentation](https://github.com/stefan-b-jakobsson/basload-rom)

**EXAMPLE of the BASLOAD Command:**

```BASIC
BASLOAD "MYPROG.BASL"
LOADING...
READY.
LIST

1 PRINT "HELLO, WORLD!"
2 GOTO 1
READY.
```

### BIN&#36;

**TYPE: String Function**  
**FORMAT: BIN$(n)**

**Action:** Return a string representing the binary value of n. If n <= 255, 8 characters are returned and if 255 < n <= 65535, 16 characters are returned.

**EXAMPLE of the BIN$ Function:**

```BASIC
PRINT BIN$(200)   : REM PRINTS 11001000 AS BINARY REPRESENTATION OF 200
PRINT BIN$(45231) : REM PRINTS 1011000010101111 TO REPRESENT 16 BITS
```

### BINPUT&#35;

**TYPE: I/O Statement**  
**FORMAT: BINPUT&#35; &lt;n&gt;,&lt;var$&gt;,&lt;len&gt;**

**Action:** `BINPUT#` Reads a block of data from an open file and stores the data into a string variable. If there are fewer than &lt;len&gt; bytes available to be read from the file, fewer bytes will be stored.  If the end of the file is reached, [`ST`](#st)` AND 64` will be true.

**EXAMPLE of the BINPUT&#35; Statement:**

```BASIC
10 OPEN 8,8,8,"FILE.BIN,S,R"
20 BINPUT#8,A$,10
30 PRINT "I GOT";LEN(A$);"BYTES"
40 IF ST<>0 THEN 20
50 CLOSE 8
```

### BOOT

**TYPE: Command**  
**FORMAT: BOOT**

**Action:** Load and run a PRG file named `AUTOBOOT.X16` from device 8. If the file is not found, nothing is done and no error is printed.

**EXAMPLE of the BOOT Command:**

```BASIC
BOOT
```

### BLOAD

**TYPE: Command**  
**FORMAT: BLOAD &lt;filename&gt;, &lt;device&gt;, &lt;bank&gt;, &lt;address&gt;**

**Action:** Loads a binary file directly into RAM

Note: If the file is loaded to high RAM (starting in the range `$A000-$BFFF`), and the file is larger than what would fit in the current bank, the load will wrap around into subsequent banks.

After a successful load, `$030D` and `$030E` will contain the address of the final byte loaded + 1.  If relevant, the value in memory location `$00` will point to the bank in which the next byte would have been loaded.

**EXAMPLES of the BLOAD Command:**

```BASIC
BLOAD "MYFILE.BIN",8,1,$A000:REM LOADS A FILE NAMED MYFILE.BIN FROM DEVICE 8 STARTING IN BANK 1 AT $A000.
BLOAD "WHO.PCX",8,10,$B000:REM LOADS A FILE NAMED WHO.PCX INTO RAM STARTING IN BANK 10 AT $B000.
```

### BSAVE

**TYPE: Command**  
**FORMAT: BSAVE &lt;filename&gt;, &lt;device&gt;, &lt;bank&gt;, &lt;start address&gt;, &lt;end address&gt;**

**Action:** Saves a region of memory to a binary file.

Note: The save will stop one byte before &lt;end address&gt;.

This command does not allow for automatic bank advancing, but you can achieve a similar result with successive `BSAVE` invocations to append additional memory locations to the same file.

**EXAMPLES of the BSAVE Command:**

```BASIC
BSAVE "MYFILE.BIN",8,1,$A000,$C000
```

The above example saves a region of memory from `$A000` in bank 1 through and including `$BFFF`, stopping before `$C000`.

```BASIC
BSAVE "MYFILE.BIN,S,A",8,2,$A000,$B000
```

The above example appends a region of memory from `$A000` through and including `$AFFF`, stopping before `$B000`.  Running both of the above examples in succession will result in a file MYFILE.BIN 12KiB in size.

**Warning:** Appending to file involves a risk of corrupting the file system of the SD card! See [Appending to file](X16%20Reference%20-%2013%20-%20Working%20with%20CMDR-DOS.md#appending-to-file).

### BVERIFY

**TYPE: Command**  
**FORMAT: BVERIFY &lt;filename&gt;, &lt;device&gt;, &lt;bank&gt;, &lt;start address&gt;, &lt;end address&gt;**

**Action:** Verifies that a file on disk matches RAM contents.

**EXAMPLE of the BVERIFY Command:**

```BASIC
BVERIFY "MYFILE.BIN",8,1,$A000,$C000
```

The above example compares a region of memory from `$A000` in bank 1 through and including `$BFFF`, stopping before `$C000`, against the filename listed.


### BVLOAD

**TYPE: Command**  
**FORMAT: BVLOAD &lt;filename&gt;, &lt;device&gt;, &lt;VERA_high_address&gt;, &lt;VERA_low_address&gt;**

**Action:** Loads a binary file directly into VERA RAM.

**EXAMPLES of the BVLOAD Command:**

```BASIC
BVLOAD "MYFILE.BIN", 8, 0, $4000  :REM LOADS MYFILE.BIN FROM DEVICE 8 TO VRAM $4000.
BVLOAD "MYFONT.BIN", 8, 1, $F000  :REM LOAD A FONT INTO THE DEFAULT FONT LOCATION ($1F000).
```

### CHAR

**TYPE: Statement**  
**FORMAT: CHAR &lt;x&gt;,&lt;y&gt;,&lt;color&gt;,&lt;string&gt;**

**Action:** This command draws a text string on the graphics screen in a given color.

The string can contain printable ASCII characters (`CHR$($20)` to `CHR$($7E)`), as well most PETSCII control codes.

**EXAMPLE of the CHAR Statement:**

```BASIC
10 SCREEN $80
20 A$="The quick brown fox jumps over the lazy dog."
24 CHAR 0,6,0,A$
30 CHAR 0,6+12,0,CHR$($04)+A$   :REM UNDERLINE
40 CHAR 0,6+12*2,0,CHR$($06)+A$ :REM BOLD
50 CHAR 0,6+12*3,0,CHR$($0B)+A$ :REM ITALICS
60 CHAR 0,6+12*4,0,CHR$($0C)+A$ :REM OUTLINE
70 CHAR 0,6+12*5,0,CHR$($12)+A$ :REM REVERSE
```

### CHR$

**TYPE: String Function**  
**FORMAT: CHR$(&lt;number&gt;)**

**Action:** This function converts a Commodore ASCII code to its character equivalent. 
See Appendix I for a list of available character sets and their codes.  The number must 
have a value between 0 and 255 (`$00-$FF`), or an ?ILLEGAL QUANTITY error message will result.

The string can contain printable ASCII characters (`CHR$($20)` to `CHR$($7E)`), as well most PETSCII control codes.

**EXAMPLE of the CHR$ Function:**

```BASIC
10 PRINT CHR$($41) : REM Decimal 65, upper case A
20 Z$ = CHR$(13) : REM 13 = RETURN key
50 B = ASC(A$) : B$ = CHR$(B) : REM Converts to X16 ASCII code and back.
```

### CLOSE

**TYPE: I/O Statement**
**FORMAT: CLOSE &lt;file number&gt;**

**Action:** Closes any files used by [`OPEN`](#open) statements.  The `CLOSE` statement takes a single argument that is the file number to be closed.

**EXAMPLE of the CLOSE I/O Statement:**

```BASIC
CLOSE 0   : REM CLOSE FILE OPENED AS 0
CLOSE 4   : REM CLOSE FILE OPENED AS 4
```

### CLR

**TYPE: Statement**  
**FORMAT: CLR**

**Action:** This statement clears RAM that had been used, but is no longer needed. 
The BASIC program in memory is untouched, but all variables, arrays, [`GOSUB`](#gosub) addresses, [`FOR..NEXT`](#for-to-step) loops, user-defined functions, and files are erased from memory, and their space is made available to new variables, etc.


**EXAMPLE of the CLR Statement:**

```BASIC
CLR
```

### CLS

**TYPE: Command**  
**FORMAT: CLS**

**Action:** Clears the screen. Same effect as `PRINT CHR$(147);`.

**EXAMPLE of the CLS Statement:**

```BASIC
CLS
```

### CMD

**TYPE: I/O Statement**  
**FORMAT: CMD &lt;file number&gt;[, string]**

**Action:** This statement switches the primary output device from the video display to the file specified. This file could be on disk, a printer, or an I/O device like the modem<sup>1</sup>.  The file number must be specified in a prior [OPEN](#open) statement.  The string, when specified, is sent to the file.  This is handy 
for titling printouts, etc.

When this command is in effect, any [`PRINT`](#print) statements and [`LIST`](#list) commands will not display on the screen, but will send the text in the same format to the file.

To re-direct the output back to the screen, the [`PRINT#`](#print-1) command should send a blank line to the [`CMD`](#cmd) device before [`CLOSE`](#close)ing, so it will stop expecting data.  This is called "un-listening" the device.

Any system error (like `?SYNTAX ERROR`) will cause output to return to the screen.  Devices aren't un-listened by this, so you should send a blank line after an error condition.

**EXAMPLE of the CMD I/O Statement:**

```BASIC
OPEN 4,4: CMD 4, "LISTING" : LIST : REM Lists program on the printer
PRINT# 4: CLOSE 4: REM Un-listens and closes printer

10 OPEN 2,8,2, "TEST.TXT,S,W" : REM Create a SEQ file.
20 CMD 2 : REM Direct output to the file not the screen.
30 FOR X = 1 TO 100
40 PRINT X
50 NEXT X
60 PRINT# 2 : REM Un-listen
70 CLOSE 1 : REM Write remaining buffer contents, close file.
```

* <sup>1</sup> Device #2 (RS-232) support has been removed from the X16 KERNAL.

### COLOR

**TYPE: Statement**  
**FORMAT: COLOR &lt;fgcol&gt;[,&lt;bgcol&gt;]**

**Action:** This command works sets the text mode foreground color, and optionally the background color.

**EXAMPLES of the COLOR Statement:**

```BASIC
COLOR 2   : REM SET FG COLOR TO RED, KEEP BG COLOR
COLOR 2,0 : REM SET FG COLOR TO RED, BG COLOR TO BLACK
```

### CONT

**TYPE: Command**  
**FORMAT: CONT**

**Action:** This command re-starts the execution of a program which was halted by a [`STOP`](#stop) or [`END`](#end) statement, or the <mark >**RUN/STOP**</mark> key being pressed.  The program will re-start at the exact place from which it left off.

While the program is stopped, the user can inspect or change any variables or look at the program.  When debugging or examing a program, `STOP` statements can be placed at strategic locations to allow examination of variables and check the flow of the program.

The error message `?CAN'T CONTINUE` will result from editing the program (even just hitting <mark >**RETURN**</mark> with the cursor on an unchanged line), or if the program halted due to an error, or if you caused an error before typing `CONT` to re-start the program.


**EXAMPLE of the CONT Command:**

```BASIC
10 PI=0 : C=1
20 PI=PI+4/C-4/(C+2)
30 PRINT PI
40 C=C+4 : GOTO 20
```

This program calculates the value of PI.  Run this program, and after a few seconds, hit the <mark >**RUN/STOP**</mark> key.  You will see the display:

```
   BREAK IN x
```
Where `x` is the line number where program execution was interrupted.

Type the command `PRINT C` to see how far the Commander X16 has gotten.  Then use `CONT` to resume from where the Commander X16 left off.

### COS

**TYPE: Function**  
**FORMAT: COS(&lt;number&gt;)**

**Action:** This mathematical function calculates the cosine of the number, where the number is an angle expressed in radians.

**EXAMPLES of the COS Function:**

```BASIC
10 PRINT COS(5)
15 A = 232
20 PI = 3.14159265
30 Y = COS(A * PI / 180) : REM Convert degrees to radians.
```

### DA$

**TYPE: String Function**  
**FORMAT: DA$**

**Action:**  Returns or sets the date in the system clock.  The format is YYYYMMDD.

**EXAMPLE of the DA$ String Function**

```BASIC
10 HD$ = DA$
20 PRINT "HOLD DATE IS ";HD$;"."
30 DA$ = "20251121"
40 PRINT "NEW DATE IS NOW ";DA$;"."
50 DA$ = HD$
```

### DATA

**TYPE: Statement**  
**FORMAT: DATA &lt;list of constants&gt;**

**Action:**  `DATA` statements store information within a program.  The program uses the information by means of the [`READ`](#read) statement, which pulls successive constants from the `DATA` statements.

The `DATA` statements don't have to be executed by the program, they only have to be present.  Therefore, they are usually placed at the end of the program.

All data statements in a program are treated as a continuous list.  Data is `READ` from left to right, from the lowest numbered line to the highest.  If the `READ` statement encounters data that doesn't fit the type requested (if it needs a number and finds a string) an error message occurs.

Any characters can be included as data, but if certain ones are used, the data item must be enclosed by quote marks (" ").  These include punctuation like comma (,), colon (:), blank spaces, shifted letters, graphics, and cursor control characters.


**EXAMPLE of DATA Statements**

```BASIC
10 FOR X = 1 TO 5
20 READ Z
30 PRINT Z
40 NEXT X
50 DATA 2, 4, 6, 8, 10
```

### DEF FN

**TYPE: Statement**  
**FORMAT: DEF FN &lt;name&gt; (&lt;variable&gt;) = &lt;expression&gt;**

**Action:** This sets up a user-defined function that can be used later in the program. The function can consist of any mathematical formula.

User-defined functions save space in programs where a long formula is used in several places.  The formula need only be specified once, in the definition statement, and then it is abbreviated as a function name.  It must be executed once, but any subsequent executions are ignored.

The function name is the letters `FN` followed by any variable name. This can be 1 or 2 characters, the first being a letter and the second a letter or digit.

**EXAMPLES of the DEF FN Statement:**

```BASIC
10 DEF FN A(X) = X + 7
20 DEF FN AA(X) = Y * Z
30 DEF FN A9(Q) = INT(RND(1)*Q+1)
```
The function is called later in the program by using the function name with a variable in parenthesis.  This function name is used like any other variable, and its value is automatically calculated.

**EXAMPLES of FN Use:**

```BASIC
40 PRINT FN A(9)
50 R = FNAA(9)
60 G = G + FN A9(10)
```

In line 50 above, the number 9 inside the parenthesis does not affect the outcome of the function because the function definition in line 20 doesn't use the variable in parenthesis.  The result is Y times Z, regardless of the value of X.  In the other two functions, the value in parenthesis does affect the result.

### DIM

**TYPE: Statement**  
**FORMAT: DIM &lt;variable&gt;(&lt;subscripts&gt;) [,&lt;variable&gt;(&lt;subscripts&gt;)... ]**

**Action:** This statement defines an array or matrix of variables.  This allows you to use the variable name with a subscript.  The subscript points to the element being used.  The lowest element number in an array is zero, and the highest is the number given in the `DIM` statement, which has a maximum of 32767.

The `DIM` statement must be executed once and only once for each array.  A `?REDIM'D ARRAY` error occurs if this line is re-executed.  Therefore, most programs perform all `DIM` operations at the very beginning.

There may be any number of dimensions and 255 subscripts in an array, limited only by the amount of RAM memory which is available to hold the variables.  The array may be made up of normal numeric variables, as shown above, or of strings or integer numbers.  If the variables are other than normal numeric, use the `$` or `%` signs after the variable name to indicate string or integer variables.

If an array referenced in a program was never `DIM`ensioned, it is automatically dimensioned to 11 elements in each dimension used in the first reference.

**EXAMPLES of the DIM Statement:**

```BASIC
10 DIM A(100)
20 DIM Z(5,7), Y(3,4,5)
30 DIM Y1%(Q)
40 DIM OH$(1000)
50 Z(5) = 9 : REM Automatically performs DIM Z(10)
```

**CALCULATING MEMORY USED BY DIM:**

 * 5 bytes for the array name.
 * 2 bytes for each dimension.
 * 2 bytes per element for integer variables.
 * 5 bytes per element for floating point variables.
 * 3 bytes per element for string variables.
 * 1 byte for each character in each string element.
  
### DOS

**TYPE: Command**  
**FORMAT: DOS &lt;string or number&gt;**

**Action:** This command works with the command/status channel or the directory of a Commodore DOS device and has different functionality depending on the type of argument.

* Without an argument, `DOS` prints the status string of the current device.
* With a numeric argument, the current device is switched to the given number.
* With a string argument of `"8"` or `"9"`, it switches the current device to the given number.
* With an argument starting with `"$"`, it shows the directory of the device.
* Any other argument will be sent as a DOS command.

**EXAMPLES of the DOS Command:**

```BASIC
DOS"$"          : REM SHOWS DIRECTORY
DOS"S:BAD_FILE" : REM DELETES "BAD_FILE"
DOS             : REM PRINTS DOS STATUS, E.G. "01,FILES SCRATCHED,01,00"
```

### EDIT

**TYPE: Command**  
**FORMAT: EDIT \[&lt;filename&gt;\]**

**Action:** Opens the built-in text editor, X16-Edit, a modeless editor with features similar to GNU Nano.

* Without an argument, the editor begins with an empty file.
* With a string argument, it attempts to load a file before displaying it.

The EDIT command loads the editor in the screen mode and character set that was active at the time the command was run.

**EXAMPLE of the EDIT Statement:**

```BASIC
EDIT "README.TXT"
```

A more elaborate X16-Edit manual can be found [here](https://github.com/X16Community/x16-rom/blob/master/x16-edit/docs/manual.pdf)

### END

**TYPE: Statement**
**FORMAT: END**

**Action:** This finishes a program's execution and displays the `READY` message, returning control to the person operating the computer.  There may be any number of `END` statements within a program.  While it is not necessary to include any `END` statements at all, it is recommended that a program does conclude with one, rather than just running out of lines.

The `END` statement is similar to the [`STOP`](#stop) statement.  The only difference is that `STOP` causes the computer to display the message `BREAK IN XX` and `END` just displays `READY`.  both statements allow the computer to resume execution by typing the [`CONT`](#cont) command.

**EXAMPLES of the END Statement:
```BASIC
10 PRINT "TYPE 'Y' TO END PROGRAM: ";
20 INPUT A$
30 IF A$ = "Y" THEN END
50 PRINT "CONTINUING..."
50 REM The rest of the program...
999 END
```

### EXEC

**TYPE: Command**  
**FORMAT: EXEC &lt;memory address&gt;\[,&lt;ram bank&gt;\]**

**Action:** Plays back a null-terminated script from MEMORY into the BASIC editor. Among other uses, this can be used to "type" in a program from a plain text file.

* If the `ram bank` argument is omitted and the address is in the range \$A000-\$BFFF, the RAM bank selected by the [`BANK`](#bank) command is used.
* The input can span multiple RAM banks. The input will stop once it reaches a null byte ($00) or if a BASIC error occurs.
* The redirected input only applies to BASIC immediate mode. While programs are running, the EXEC handling is suspended.

**EXAMPLE of the EXEC Statement:**

```BASIC
BLOAD "MYPROGRAM.BAS",8,1,$A000 : REM "BANK PEEK(0)" NO LONGER NEEDED
POKE PEEK($30D)+(PEEK($30E)*256),0 : REM NULL TERMINATE IN END BANK
EXEC $A000,1
```

This program will load a plain ASCII or PETSCII FILE.BAS from disk and tokenize
it for you:

```BASIC
10 BLOAD "FILE.BAS", 8, 1, $A000
20 POKE PEEK(781) + 256 * PEEK(782), 0
30 EXEC $A000, 1
40 NEW
```

### EXP

**TYPE: Numeric Function**
**FORMAT: EXP (&lt;number&gt;)**

**Action:** This mathematical function calculates the constant e (2.71828183) raised to the power of the number given.  A value greater than 88.0296919 causes `?OVERFLOW ERROR` to occur.

**EXAMPLES of the EXP Function:**

```BASIC
10 PRINT EXP(12)
20 C = D * EXP(A * B)
```

### FMCHORD

**TYPE: Statement**  
**FORMAT: FMCHORD &lt;first channel&gt;,&lt;string&gt;**

**Action:** This command uses the same syntax as [`FMPLAY`](#fmplay), but instead of playing a series of notes, it will start all of the notes in the string simultaneously on one or more channels. The first parameter to `FMCHORD` is the first channel to use, and will be used for the first note in the string, and subsequent notes in the string will be started on subsequent channels, with the channel after 7 being channel 0.

All macros are supported, even the ones that only affect the behavior of [`PSGPLAY`](#psgplay) and [`FMPLAY`](#fmplay).

The full set of macros is documented [here](X16%20Reference%20-%20Appendix%20A%20-%20Sound.md#basic-fmplay-and-psgplay-string-macros).

**EXAMPLE of the FMCHORD Statement:**

```BASIC
10 FMINIT
20 FMVIB 195,10
30 FMINST 1,16:FMINST 2,16:FMINST 3,16 : REM ORGAN
40 FMVOL 1,50:FMVOL 2,50:FMVOL 3,50 : REM MAKE ORGAN QUIETER
50 FMINST 0,11 : REM VIBRAPHONE
60 FMCHORD 1,"O3CG>E T90" : REM START SOME ORGAN CHORDS (CHANNELS 1,2,3)
70 FMPLAY 0,"O4G4.A8G4E2." : REM PLAY MELODY (CHANNEL 0)
80 FMPLAY 0,"O4G4.A8G4E2."
90 FMCHORD 1,"O2G>DB" : REM SWITCH ORGAN CHORDS (CHANNELS 1,2,3)
100 FMPLAY 0,"O5D2D4<B2" : REM PLAY MORE MELODY
110 FMCHORD 1,"O2F" : REM SWITCH ONE OF THE ORGAN CHORD NOTES
120 FMPLAY 0,"R4" : REM PAUSE FOR THE LENGTH OF ONE QUARTER NOTE
130 FMCHORD 1,"O3CEG" : REM SWITCH ALL THREE CHORD NOTES
140 FMPLAY 0,"O5C2C4<G2." : REM PLAY THE REST OF THE MELODY
150 FMCHORD 1,"RRR" : REM RELEASE THE CHANNELS THAT ARE PLAYING THE CHORD
```

This will play the first few lines of _Silent Night_ with a vibraphone lead and organ accompaniment.

### FMDRUM

**TYPE: Statement**  
**FORMAT: FMDRUM &lt;channel&gt;,&lt;drum number&gt;**

**Action:** Loads a [drum preset](X16%20Reference%20-%20Appendix%20A%20-%20Sound.md#drum-presets "list of drum presets") onto the YM2151 and triggers it. Valid range is from 25 to 87, corresponding to the General MIDI percussion note values. FMDRUM will load a patch preset corresponding to the selected drum into the channel. If you then try to play notes on that same channel without loading an instrument patch, it will use the drum patch that was loaded for the drum sound instead, which may not sound particularly musical.

### FMFREQ

**TYPE: Statement**  
**FORMAT: FMFREQ &lt;channel&gt;,&lt;frequency&gt;**

**Action:** Play a note by frequency on the YM2151. The accepted range is in Hz from 17 to 4434. `FMFREQ` also accepts a frequency of 0 to release the note.

**EXAMPLE of the FMFREQ Statement:**

```BASIC
0 FMINST 0,160 : REM LOAD PURE SINE PATCH
10 FMINST 1,160 : REM HERE TOO
20 FMFREQ 0,350 : REM PLAY A SINE WAVE AT 350 HZ
30 FMFREQ 1,440 : REM PLAY A SINE WAVE AT 440 HZ ON ANOTHER CHANNEL
40 FOR X=1 TO 10000 : NEXT X : REM DELAY A BIT
50 FMFREQ 0,0 : FMFREQ 1,0 : REM RELEASE BOTH CHANNELS
```

The above BASIC program plays a sound similar to a North American dial tone for a few seconds.

### FMINIT

**TYPE: Statement**  
**FORMAT: FMINIT**

**Action:** Initialize the YM2151, silence all channels, and load a set of default patches into all 8 channels.

### FMINST

**TYPE: Statement**  
**FORMAT: FMINST &lt;channel&gt;,&lt;patch&gt;**

Load an instrument onto the YM2151 in the form of a [patch preset](X16%20Reference%20-%20Appendix%20A%20-%20Sound.md#fm-instrument-patch-presets) into a channel. Valid channels range from 0 to 7. Valid patches range from 0 to 162.

### FMNOTE

**TYPE: Statement**  
**FORMAT: FMNOTE &lt;channel&gt;,&lt;note&gt;**

**Action:** Play a note on the YM2151. The note value is constructed as follows. Using hexadecimal notation, the first nybble is the octave, 0-7, and the second nybble is the note within the octave as follows:

| `$x0` | `$x1` | `$x2` | `$x3` | `$x4` | `$x5` | `$x6` | `$x7` | `$x8` | `$x9` | `$xA` | `$xB` | `$xC` | `$xD-$xF` |
|-|-|-|-|-|-|-|-|-|-|-|-|-|-|
| Release | C | C&#9839;/D&#9837; | D | D&#9839;/E&#9837; | E | F | F&#9839;/G&#9837; | G | G&#9839;/A&#9837; | A | A&#9839;/B&#9837; | B | no-op |

Notes can also be represented by negative numbers to skip retriggering, and will thus snap to another note without restarting the playback of the note.

**EXAMPLE of the FMNOTE Statement:**

```BASIC
0 FMINST 1,64 : REM LOAD SOPRANO SAX
10 FMNOTE 1,$4A : REM PLAYS CONCERT A
20 FOR X=1 TO 5000 : NEXT X : REM DELAYS FOR A BIT
30 FMNOTE 1,0 : REM RELEASES THE NOTE
40 FOR X=1 TO 1000 : NEXT X : REM DELAYS FOR A BIT
50 FMNOTE 1,$3A : REM PLAYS A IN THE 3RD OCTAVE
60 FOR X=1 TO 2500 : NEXT X : REM SHORT DELAY
70 FMNOTE 1,-$3B : REM UP A HALF STEP TO A# WITHOUT RETRIGGERING
80 FOR X=1 TO 2500 : NEXT X : REM SHORT DELAY
90 FMNOTE 1,0 : REM RELEASES THE NOTE
```

### FMPAN

**TYPE: Statement**  
**FORMAT: FMPAN &lt;channel&gt;,&lt;panning&gt;**

**Action:** Sets the simple stereo panning on a YM2151 channel. Valid values are as follows:

* 1 = left
* 2 = right
* 3 = both

### FMPLAY

**TYPE: Statement**  
**FORMAT: FMPLAY &lt;channel&gt;,&lt;string&gt;**

**Action:** This command is very similar to `PLAY` on other BASICs such as GWBASIC. It takes a string of notes, rests, tempo changes, note lengths, and other macros, and plays all of the notes synchronously.  That is, the FMPLAY command will not return control until all of the notes and rests in the string have been fully played.

The full set of macros is documented [here](X16%20Reference%20-%20Appendix%20A%20-%20Sound.md#basic-fmplay-and-psgplay-string-macros).

**EXAMPLE of the FMPLAY Statement:**

```BASIC
10 FMINIT : REM INITIALIZE AND LOAD DEFAULT PATCHES, WILL USE E.PIANO
20 FMPLAY 1,"T90 O4 L4" : REM TEMPO 90 BPM, OCTAVE 4, NOTE LENGTH 4 (QUARTER)
30 FMPLAY 1,"CDECCDECEFGREFGR" : REM FIRST TWO LINES OF TUNE
40 FMPLAY 1,"G8A8G8F8EC G8A8G8F8EC" : REM THIRD LINE
50 FMPLAY 1,"C<G>CRC<G>CR" : REM FOURTH LINE
```

### FMPOKE

**TYPE: Statement**  
**FORMAT: FMPOKE &lt;register&gt;,&lt;value&gt;**

**Action:** This command uses the AUDIO API to write a value to one of the YM2151's registers at a low level.

**EXAMPLE of the FMPOKE Statement:**

```BASIC
10 FMINIT
20 FMPOKE $28,$4A : REM SET KC TO A4 (A-440) ON CHANNEL 0
30 FMPOKE $08,$00 : REM RELEASE CHANNEL 0
40 FMPOKE $08,$78 : REM START NOTE PLAYBACK ON CHANNEL 0 W/ ALL OPERATORS
```

### FMVIB

**TYPE: Command**  
**FORMAT: FMVIB &lt;speed&gt;,&lt;depth&gt;**

**Action:** This command sets the LFO speed and the phase and amplitude modulation depth values on the YM2151. The speed value ranges from 0 to 255, and corresponds to an LFO frequency from 0.008 Hz to 32.6 Hz.  The depth value ranges from 0-127 and affects both AMD and PMD.

Only some patch presets (instruments) are sensitive to the LFO. Those are marked in [this table](X16%20Reference%20-%20Appendix%20A%20-%20Sound.md#fm-instrument-patch-presets) with the &#8224; symbol.  The LFO affects all channels equally, and it depends on the instrument as to whether it is affected.

Good values for most instruments are speed somewhere between 190-220. A good light vibrato for most wind instruments would have a depth of 10-15, while tremolo instruments like the Vibraphone or Tremolo Strings are most realistic around 20-30.

**EXAMPLE of the FMVIB Statement:**

```BASIC
10 FMVIB 200,30
20 FMINST 0,11 : REM VIBRAPHONE
30 FMPLAY 0,"T60 O4 CDEFGAB>C"
40 FMVIB 0,0
50 FMPLAY 0,"C<BAGFEDC"
```

The above BASIC program plays a C major scale with a vibraphone patch, first with a vibrato/tremolo effect, and then plays the scale in reverse with the vibrato turned off.

### FMVOL

**TYPE: Statement**  
**FORMAT: FMVOL &lt;channel&gt;,&lt;volume&gt;**

**Action:** This command sets the channel's volume. The volume remains at the requested level until another `FMVOL` command for that channel or [`FMINIT`](#fminit) is called.  Valid range is from 0 (completely silent) to 63 (full volume)

### FN

**TYPE: Numeric Function**  
**FORMAT: FN &lt;name&gt; (&lt;number&gt;)**

**Action:** This function references the previously [`DEF`](#def-fn)ined formula specified by name.  The number is substituted into its place (if any) and the formula is calculated.  The result will be a numeric value.

This function can be used in direct mode, as long as the statement `DEF`ining it has been executed.

If an `FN` is executed before the `DEF` statement which defines it, an `?UNDEF'D FUNCTION` error occurs.

**EXAMPLES the FN (User Defined) Function:**

```BASIC
PRINT FN Z(Q)
135 A = FN A(3) + FN A(21)
210 IF FN X1(A+1) = 42 THEN END
```

### FOR-TO-STEP

**TYPE: Statement**  
**FORMAT: FOR &lt;variable&gt; = &lt;start&gt; TO &lt;limit&gt; [STEP &lt;increment&gt;]**

**Action:** This is a special BASIC statement that lets you easily use a variable as a counter.  You must specify certain parameters: the floating-point variable name, its starting value, the limit of the count, and how much to add during each cycle.

Here is a simple BASIC program that counts from 1 to 10, [`PRINT`](#print)ing each number and [`END`](#end)ing when complete, and using no `FOR` statements:
```BASIC
10 A = 1
20 PRINT A
30 A = A + 1
40 IF A <= 10 THEN 20
50 END
```
Using the `FOR` statement, here is the same program:
```BASIC
10 FOR A = 1 TO 10
20 PRINT A
30 NEXT A
40 END
```

As you can see, the program is shorter and easier to understand using the `FOR` statement.

When the `FOR` statement is executed, several operations take place.  The &lt;start&gt; value is placed in the &lt;variable&gt; being used in the counter.  In the example above, a 1 is placed in `A`.

When the [`NEXT`](#next) statement is reached, the &lt;increment&gt; value is added to the &lt;variable&gt;.  If a `STEP` was not included, the &lt;increment&gt; is set to +1.  The first time the program hits line 30, 1 is added to `A`, so the new value of `A` is 2.

Now the value in the &lt;variable&gt; is compared to the &lt;limit&gt;.  if the &lt;limit&gt; has not been reached yet, the program `GO`es `TO` the line after the original `FOR` statement.  In this case, the value of 2 in `A` is less than the limit of 10, so it `GO`es `TO` line 20.

Eventually, the value of &lt;limit&gt; is exceeded by the &lt;variable&gt;.  At that time, the loop is concluded and the program continues with the line following the `NEXT` statement.  In our example, the value of `A` reaches 11, which exceeds the limit of 10, and the program goes on with line 40.

When the value of &lt;increment&gt; is positive, the &lt;variable&gt; must exceed the &lt;limit&gt;, and when it is negative, it must become less than the &lt;limit&gt;.

**NOTE: A loop always executes at least once.**

**EXAMPLES of the FOR.. TO.. STEP.. Statement:**
```BASIC
10 FOR X = 100 TO 0 STEP -1
10 FOR Z = PI TO 6 * 3.1459 STEP .01
10 FOR ZY = 42 TO 42
```

### FRAME

**TYPE: Statement**  
**FORMAT: FRAME &lt;x1&gt;,&lt;y1&gt;,&lt;x2&gt;,&lt;y2&gt;,&lt;color&gt;**

**Action:** This command draws a rectangle frame on the graphics screen in a given color.

**EXAMPLE of the FRAME Statement:**

```BASIC
10 SCREEN$80
20 FORI=1TO20:FRAMERND(1)*320,RND(1)*200,RND(1)*320,RND(1)*200,RND(1)*128:NEXT
30 GOTO20
```

### FRE

**TYPE: Function**  
**FORMAT: FRE(&lt;variable&gt;)**

**Action:**  This function tells you how much RAM is available for your programs and its variables.  If a program tries to use more space than is available, the `?OUT OF MEMORY` error results.

The number in parenthesis can have any value, and it is not used in the calculation.

**NOTE: If the result of `FRE` is negative, add 65536 to the `FRE` number to get the number of bytes available in memory.**

**EXAMPLES of the FRE Function:**
```BASIC
PRINT FRE(0)
10 FM = (FRE(K) - 1000) / 7
60000 IF FRE(0) < 100 THEN PRINT "NOT ENOUGH ROOM"
```
**NOTE: The following always tells you the current available RAM:**
```BASIC
PRINT FRE(0) - (FRE(0) < 0) * 65536
```

### GET

**TYPE: Statement**  
**FORMAT: GET &lt;variable list&gt;**

**Action:** This statement reads each key typed by the user.  As the user is typing, the characters are stored in the Commander X16's keyboard buffer.  Up to 10 characters are stored here, and any keys struck after the 10th are discarded.  Reading one of the characters with the `GET` statement makes room for another character.

If the `GET` statement specifies numeric data, and the user types a key other than a number, the message `?SYNTAX ERROR` appears.  To be safe, read the keys as strings and convert them to numbers later.

The `GET` statement can be used to avoid some of the limitations of the [`INPUT`](#input) statement.  For more on this, see the section on Using the `GET` Statement in the Programming Techniques<sup>2</sup> section.

**EXAMPLES of the GET Statement:**

```BASIC
10 GET OK$ : IF OK$ = "" THEN 10 : REM Loops until a key is pressed.
20 GET A1$, A2$, A3$, A4$, A5$ : REM Reads 5 keys
30 GET B, B$ : REM Reads a number key (0..9) and any key.
```

* <sup>2</sup>: There is no Programming Techniques section currently.

### GET&#35;

**TYPE: I/O Statement**  
**FORMAT: GET# &lt;file number&gt;, &lt;variable list&gt;**

**Action:** This statement reads characters one-at-a-time from the device or file specified.  It works the same as the [`GET`](#get) statement, except that the data comes from a different place than the keyboard.  If no character is received, the variable list is set to an empty string (equal to "") or to 0 for numeric variables.  Characters used to separate data in files, like the comma `(,)` or <mark>**RETURN**</mark> key code (ASCII code of 13), are received like any other character.
 
 **EXAMPLES of the GET# Statement:**

 ```BASIC
 10 GET# 1, A$
 20 OPEN 1,3 : GET# 1, A3$
 30 GET# 1, A(1), A(2), A$, B$
 ```

### GOSUB

**TYPE: Statement** 
**FORMAT: GOSUB &lt;line number&gt;**

**Action** This is a specialized form of the [`GOTO`](#goto) statement, with one important difference: [`GOSUB`,](#gosub) remembers where it came from.  When the [`RETURN`](#return) statement (different from the <mark>**RETURN**</mark> key on the keyboard) is reached in the program, the program jumps back to the statement immediately following the original `GOSUB` statement.

The major use of a subroutine (`GOSUB` means `GO` to a `SUB`-routine) is when a small section of program is used by different sections of the program.  By using subroutines rather that repeating the same lines over and over at different places in the program, you can save lots of program space.  In this way, `GOSUB` is similar to [`DEF FN`](#def-fn).  `DEF FN` lets you save space when using a formula, while `GOSUB` saves space when using a several-line routine.

**An inefficient program that doesn't use `GOSUB`**
```BASIC
10 PRINT "THIS PROGRAM PRINTS"
20 FOR I = 1 TO 500 : NEXT I
30 PRINT "SLOWLY ON THE SCREEN"
40 FOR I = 1 TO 500 : NEXT I
50 PRINT "USING A SIMPLE LOOP"
60 FOR I = 1 TO 500 : NEXT I
70 PRINT "AS A TIME DELAY"
180 FOR I = 1 TO 500 : NEXT I
```

**The same program using `GOSUB`**
```BASIC
10 PRINT "THIS PROGRAM PRINTS"
20 GOSUB 200
30 PRINT "SLOWLY ON THE SCREEN"
40 GOSUB 200
50 PRINT "USING A SIMPLE LOOP"
60 GOSUB 200
80 PRINT "AS A TIME DELAY"
90 GOSUB 200
100 END
200 FOR I = 1 TO 500 : NEXT I
210 RETURN
```
Each time the program executes a `GOSUB`, the line number and position in the program line are saved in a special area called the "stack", which takes up 256 bytes of memory.  This limits the amount of data that can be stored in the stack.  Therefore, the number of subroutine return addresses that can be stored is limited, and care should be taken to make sure every `GOSUB` hits the corresponding `RETURN`, otherwise you'll run out of memory even though the computer has plenty of bytes free.

### GOTO

**TYPE: Statement**
**FORMAT: GOTO &lt;line number&gt; or GO TO &lt;line number&gt;**

**Action:** This statement allows the BASIC program to execute lines out of numerical order.  The word `GOTO` followed by a number will make the program jump to the line with that number.  `GOTO` NOT followed by a number equals `GOTO 0`.  It must have the line number after the word `GOTO`.

It is possible to create loops with `GOTO` that will never end.  The simplest example of this is a line that `GO`es `TO` itself, like `10 GOTO 10`.

These loops can be stopped by using the <mark>**RUN/STOP**</mark> key on the keyboard.

**EXAMPLES of the GOTO Statement:**
```BASIC
GOTO 25
10 GO TO 100
20 GOTO 12000
```

### HELP

**TYPE: Command**  
**FORMAT: HELP**

**Action:** The `HELP` command displays a brief summary of the ROM build, and points users to this guide at its home on GitHub, and to the community forums website.

### HEX$

**TYPE: String Function**  
**FORMAT: HEX$(n)**

**Action:** Return a string representing the hexadecimal value of n. If n <= 255, 2 characters are returned and if 255 < n <= 65535, 4 characters are returned.

**EXAMPLE of the HEX$ Function:**

```BASIC
PRINT HEX$(200)   : REM PRINTS C8 AS HEXADECIMAL REPRESENTATION OF 200
PRINT HEX$(45231) : REM PRINTS B0AF TO REPRESENT 16 BIT VALUE
```

### I2CPEEK

**TYPE: Integer Function**  
**FORMAT: I2CPEEK(&lt;device&gt;,&lt;register&gt;)**

**Action:** Returns the value from a register on an I²C device.

**EXAMPLE of the I2CPEEK Function:**

```BASIC
PRINT HEX$(I2CPEEK($6F,0) AND $7F)
```

This command reports the seconds counter from the system clock by converting its internal BCD representation to a string.

### I2CPOKE

**TYPE: Statement**  
**FORMAT: I2CPOKE &lt;device&gt;,&lt;register&gt;,&lt;value&gt;**

**Action:** Sets the value to a register on an I²C device.

**EXAMPLE of the I2CPOKE Function:**

```BASIC
I2CPOKE $6F,$40,$80
```

This command sets a byte in NVRAM on the RTC to the value `$80`

### IF-THEN

**TYPE: Statement**  
**FORMAT:**
- **IF &lt;expression&gt; THEN &lt;line number&gt;**
- **IF &lt;expression&gt; GOTO &lt;line number&gt;**
- **IF &lt;expression&gt; &lt;statements&gt;**

**Action:** This is the statement that gives BASIC most of its "intelligence", the ability to evaluate conditions and take different actions depending on the outcome.

The word `IF` is followed by an expression, which can include variables, strings, numbers, comparisons, and logical operators.  The word `THEN` appears on the same line and is followed by either a line number or one or more BASIC statements.  When the expression is false, everything else after the word `THEN` on that line is ignored, and execution continues with the next line number in the program.  A true result makes the program either branch to the line number after the word `THEN` or execute whatever other BASIC statements are found on that line.

**EXAMPLE of the IF...GOTO... Statement:**
```BASIC
10 INPUT "ENTER A NUMBER";N
20 IF N <= 0 GOTO 50
30 PRINT "SQUARE ROOT=";SQR(N)
40 GOTO 10
50 PRINT "NUMBER MUST BE > 0"
60 GOTO 10
```
This program prints out the square root of any positive number.  The `IF` statement here is used to validate the result of the `INPUT`.  When the result of `N` is less than or equal to zero, the program skips to line 50, and when the result is false, the next line to be executed is 30.  Note that `THEN GOTO` is not needed with `IF...THEN`, as in line 20 where `GOTO 50` actually means `THEN GOTO 50`.

**EXAMPLE of the IF...THEN... Statement:**
```BASIC
10 FOR I = 1 TO 100
20 IF RND(1) < .5 THEN X = X + 1 : GOTO 40
30 Y = Y + 1
40 NEXT I
50 PRINT "HEADS= ";X
60 PRINT "TAILS= ";Y
```
The `IF` in line 20 tests a random number to see if it is less than .5.

When the result is true, the whole series of statements following the word `THEN` are executed: first `X` is incremented by 1, then the program skips to line 40.  When the result is false, the program drops to the next statement, line 30.

### INPUT

**TYPE: Statement**  
**FORMAT: INPUT ["&lt;prompt&gt;"] &lt;variable list&gt;**

**Action:** This is a statement that lets the person [`RUN`](#run)ning the program "feed" information into the computer.  When executed, this statement [`PRINT`](#print)s a question mark `(?)` on the screen, and positions the cursor 1 space to the right of the question mark.  Now the computer waits, cursor blinking, for the operator to type in the answer and press the <mark>**RETURN**</mark> key.

The word `INPUT` may be followed by any text contained in quote marks `(" ")`.  This text is `PRINT`ed on the screen, followed by the question mark.

After the text comes a semicolon `(;)` and the name of one or more variables separated by commas.  This variable is where the computer stores the information that the operator types.  The variable can be any legal variable name, and you can have several different variable names, each for a different input.

**EXAMPLES of the INPUT Statement:**
```BASIC
10 INPUT R
20 INPUT E, X, I$
30 INPUT "ENTER ANSWER"; A$(42)
```
When this program `RUN`s, the question mark appears to prompt the operator that the Commander X16 is expecting an input for line 30.  Any number typed goes into A for later use in the program.  If the answer typed was not a number, the `?REDO FROM START` message appears, which means that a string was entered when a number was expected.  If the operator just hits <mark>**RETURN**</mark> without typing anything, the variable's value doesn't change.

Now the question mark for line 20, appears.  If we type only one number and hit <mark>**RETURN**</mark>, the Commander X16 will now display 2 question marks `(??)`, which means that more input is required.  You can just type as many inputs as you need, separated by commas, which prevents the double question mark from appearing.  If you type more data than the `INPUT` statement requested, the `?EXTRA IGNORED` message appears, which means that the extra items you typed were not put into any variables.

Line 30 displays the words ENTER ANSWER before the question mark appears.  The semicolon is required between the prompt and any list of variables.

The `INPUT` statement can never be used outside a program.  The Commander X16 needs space for a buffer for the `INPUT` variables, the same space that is used for commands.

### INPUT&#35;

**TYPE: I/O Statement**  
**FORMAT: INPUT# &lt;file number&gt;, &lt;variable list&gt;**

**Action:**  This is usually the fastest and easiest way to retrieve data stored in a file on disk.  The data is in the form of whole variables of up to 80 characters in length, as opposed to the one-at-a-time method of [`GET#`](#get-1).  First, the file must have been [`OPEN`](#open)ed, then `INPUT#` can fill the variables.

The `INPUT#` command assumes a variable is finished when it reads a [`RETURN`](#return) code ([`CHR$`](#chr)(13)), a comma `(,)`, or colon `(:)`.  Quote marks `(")` can be used to enclose these characters when writing if they are needed (see the [`PRINT#`](#print-1) statement).

If the variable  type used is numeric, and non-numeric characters are received, a `BAD DATA` error results.  `INPUT#` can read strings up to 80 characters long, beyond which a `?STRING TOO LONG` error results.

When used with device #3 (the screen), this statement will read an entire logical line and move the cursor down to the next line.

**EXAMPLES of the INPUT# Statement:**
```BASIC
10 INPUT# 1, FR
20 INPUT# 2, X$, Y$
```

### INT

**TYPE: Integer Function**  
**FORMAT: INT(&lt;numeric&gt;)**

**Action:** Returns the integer value of the expression.  If the expression is positive, the fractional part is left off.  If the expression is negative, any fraction causes the next lower integer to be returned.

**EXAMPLES of the INT Function:**
```BASIC
10 PRINT INT(102.4242), INT(-16.702)
RUN
 102       -17
```

### JOY

**TYPE: Integer Function**  
**FORMAT: JOY(n)**

**Action:** Return the state of a joystick.

`JOY(1)` through `JOY(4)` return the state of SNES controllers connected to the system, and `JOY(0)` returns the state of the "keyboard joystick", a set of keyboard keys that map to the SNES controller layout. See [`joystick_get`](X16%20Reference%20-%2005%20-%20KERNAL.md#function-name-joystick_get) for details.

If no controller is connected to the SNES port (or no keyboard is connected), the function returns -1. Otherwise, the result is a bit field, with pressed buttons [`OR`](#or)ed together:

| Value  | Button |
|--------|--------|
| $800   | A      |
| $400   | X      |
| $200   | L      |
| $100   | R      |
| $080   | B      |
| $040   | Y      |
| $020   | SELECT |
| $010   | START  |
| $008   | UP     |
| $004   | DOWN   |
| $002   | LEFT   |
| $001   | RIGHT  |

Note that this bitfield is different from the `joystick_get` KERNAL API one. Also note that the keyboard joystick will allow LEFT and RIGHT as well as UP and DOWN to be pressed at the same time, while controllers usually prevent this mechanically.

**EXAMPLE of the JOY Function:**

```BASIC
10 REM DETECT CONTROLLER, FALL BACK TO KEYBOARD
20 J = 0: FOR I=1 TO 4: IF JOY(I) >= 0 THEN J = I: GOTO40
30 NEXT
40 :
50 V=JOY(J)
60 PRINT CHR$(147);V;": ";
70 IF V = -1 THEN PRINT"DISCONNECTED ": GOTO50
80 IF V AND 8 THEN PRINT"UP ";
90 IF V AND 4 THEN PRINT"DOWN ";
100 IF V AND 2 THEN PRINT"LEFT ";
110 IF V AND 1 THEN PRINT"RIGHT ";
120 GOTO50
```

### KEYMAP

**TYPE: Command**  
**FORMAT: KEYMAP &lt;string&gt;**

**Action:** This command sets the current keyboard layout. It can be put into an AUTOBOOT file to always set the keyboard layout on boot.

**EXAMPLE of the KEYMAP Statement:**

```BASIC
10 KEYMAP"SV-SE"    :REM SMALL BASIC PROGRAM TO SET LAYOUT TO SWEDISH/SWEDEN
SAVE"AUTOBOOT.X16"  :REM SAVE AS AUTOBOOT FILE
```

### LEFT&#36;

**TYPE: String Function**  
**FORMAT: LEFT$(&lt;string&gt;, &lt;integer&gt;)**

**Action:** Returns a string comprised of the leftmost &lt;integer&gt; characters of the &lt;string&gt;.  The integer argument value must be in the range 0 to 255.  If the integer is greater than the length of the string, the entire string will be returned.  If an &lt;integer&gt; value of zero is used, then a null string (of zero length) is returned.

**EXAMPLES of the LEFT$ Function:**
```BASIC
10 X$ = "COMMANDER X16 COMPUTER"
20 C$ = LEFT$(X$, 9): PRINT C$
RUN

COMMANDER
```

### LEN

**TYPE: Integer Function**  
**FORMAT: LEN(&lt;string&gt;)**

**Action:** Returns the number of characters in the string expression.  Non-printed characters and blanks are counted.

**EXAMPLE of the LEN Function:**
```BASIC
10 CX$ = "COMMANDER X16 COMPUTER"
20 PRINT LEN(CX$)
RUN
 22
```

### LET

**TYPE: Statement**  
**FORMAT: [LET] &lt;variable&gt; = &lt;expression&gt;**

**Action:** The `LET` statement can be used to assign a value to a variable.  However, the word `LET` is optional and therefore most advanced programmers leave `LET` out because it's always understood and wastes valuable memory.  The equal sign `(=)` alone is sufficient when assigning the value of an expression to a variable name.

**EXAMPLES of the LET Statement:**
```BASIC
10 LET A = 42 : REM This is the same as A=12
20 LET A$ = "123"
30 B$ = "WIDGETS"
40 ANS$ = A$ + " " + B$ : REM ANS$ would equal "123 WIDGETS"
```

### LINE

**TYPE: Statement**  
**FORMAT: LINE &lt;x1&gt;,&lt;y1&gt;,&lt;x2&gt;,&lt;y2&gt;,&lt;color&gt;**

**Action:** This statement draws a line on the graphics screen in a given color.

**EXAMPLE of the LINE Statement:**

```BASIC
10 SCREEN128
20 FORA=0TO2*πSTEP2*π/200
30 :  LINE100,100,100+SIN(A)*100,100+COS(A)*100
40 NEXT
```

> **If you're pasting this example into the Commander X16 emulator, use this code block instead so that the &pi; symbol is properly received.**

```BASIC
10 SCREEN128
20 FORA=0TO2*\XFFSTEP2*\XFF/200
30 :  LINE100,100,100+SIN(A)*100,100+COS(A)*100
40 NEXT
```

### LINPUT

**TYPE: Command**  
**FORMAT: LINPUT &lt;var$&gt;**

**Action:** `LINPUT` Reads a line of data from the keyboard and stores the data into a string variable. Unlike [`INPUT`](#input), no parsing or cooking of the input is done, and therefore quotes, commas, and colons are stored in the string as typed. No prompt is displayed, either.

The input is taken from the KERNAL editor, hence the user will have the freedom of all of the features of the editor such as cursor movement, mode switching, and color changing.

Due to how the editor works, an empty line will return `" "`&ndash; a string with a single space, and trailing spaces are not preserved.

**EXAMPLE of the LINPUT Statement:**

```BASIC
10 LINPUT A$
20 IF A$=" " THEN 50
30 PRINT "YOU TYPED: ";A$
40 END
50 PRINT "YOU TYPED AN EMPTY STRING: ";A$
```

### LINPUT&#35;

**TYPE: Command**  
**FORMAT: LINPUT&#35; &lt;n&gt;,&lt;var$&gt;\[,&lt;delimiter&gt;\]**

**Action:** `LINPUT#` Reads a line of data from an open file and stores the data into a string variable. The delimiter of a line by default is 13 (carriage return). The delimiter is not part of the stored value. If the end of the file is reached while reading, [`ST`](#st)` AND 64` will be true.

`LINPUT#` can be used to read structured data from files. It can be particularly useful to extract quoted or null-terminated strings from files while reading.

**EXAMPLE of the LINPUT&#35; Statement:**

```BASIC
10 I=0
20 OPEN 1,8,0,"$"
30 LINPUT#1,A$,$22
40 IF ST<>0 THEN 130
50 LINPUT#1,A$,$22
60 IF I=0 THEN 90
70 PRINT "ENTRY: ";
80 GOTO 100
90 PRINT "LABEL: ";
100 PRINT CHR$($22);A$;CHR$($22)
110 I=I+1
120 IF ST=0 THEN 30
130 CLOSE 1
```

The above example parses and prints out the filenames from a directory listing.

### LIST

**TYPE: Command**  
**FORMAT: LIST [start] [-] [end]**

**Action:** `LIST` Displays the currently loaded BASIC program on the screen.
The start and ending line numbers are both optional.

The start and/or end may be specified. If both are specified, a hyphen must
be included. So `LIST` has 4 modes:

`LIST` by itself will display the entire program.

`LIST 10-20` will display lines 10 to 20, inclusive.

`LIST -100` will display from the start to line 100

`LIST 50-` will display line 50 to the end of the program.

Pressing the <mark>**CTRL**</mark> key during a listing will slow the listing down once
printing reaches the bottom of the screen. Approximately one line per second will
be displayed.  `LIST` is aborted by hitting the <mark>**RUN/STOP**</mark> key.

Pressing the <mark>**SPACE BAR**</mark> during the listing will cause the listing to pause.
Pressing the <mark>**SPACE BAR**</mark> a second time will unpause the listing. You may also
use the down arrow key to scroll by one line or use the `PgDn` key to scroll
approximately one screen full of text.

### LOAD

**TYPE: Command**  
**FORMAT: LOAD ["&lt;filename&gt;"][,&lt;device&gt;][,&lt;address&gt;] LOAD ["&lt;filename&gt;"][,&lt;device&gt;][,&lt;ram bank&gt;, &lt;start address&gt;] **

**Action:** The `LOAD` statement reads the contents of a program file from disk into memory.  That way you can use the information `LOAD`ed or change the information in some way.  The device number is optional, but when it is left out, the Commander X16 will automatically default to 8, the first disk device.  The `LOAD` command closes all open files and if it is used in direct mode, it performs a [`CLR`](#clr) (clear) before reading the program.  If `LOAD` is executed from within a program, the program is `RUN`.  this means that you can use `LOAD` to "chain" several programs together.  None of the variables are cleared during a chain operation.

If you are using file name pattern matching, the first file which matches the pattern is loaded.  The asterisk in quotes by itself `("*")` causes the first file name in the disk directory to be loaded.  If the file name used does not or if it is not a program, the BASIC error message `?FILE NOT FOUND` occurs.

Programs will `LOAD` starting at memory location $0801 (hex) unless a secondary &lt;address&gt; of 1 is used.  If you use the secondary address of 1 this will cause the program to `LOAD` to the memory location from which it was saved. 

If using the second form of the `LOAD` command, &lt;ram bank&gt; sets the back for the load, and &lt;start address&gt; is the location where your data will be `LOAD`ed into.

The value of the &lt;ram bank&gt; argument only affects the `LOAD` when the &lt;start address&gt; is set in the range of `$A000-$BFFF`.

**EXAMPLES of the LOAD Command:**
- LOAD FN$ (uses the contents of FN$ to load from disk)
- LOAD "*",8 (loads the first program from device 8)
- LOAD "GAME",8,1 (loads "GAME" into the same memory address it was saved from)
- LOAD "MUSIC.BIN",8,1,$A000 (loads a file into banked RAM, RAM bank 1, starting at $A000.  The first two bytes of the file are skipped.  To avoid skipping the first two bytes, use the `BLOAD` command instead.)

### LOCATE

**TYPE: Statement**  
**FORMAT: LOCATE &lt;line&gt;[,&lt;column&gt;]**

**Action:** This command positions the text mode cursor at the given location.
The values are 1-based. If no column is given, only the line is changed.

**EXAMPLE of the LOCATE Statement:**

```BASIC
100 REM DRAW CIRCLE ON TEXT SCREEN
110 SCREEN0
120 R=25
130 X0=40
140 Y0=30
150 FORT=0TO360STEP1
160 :  X=X0+R*COS(T)
170 :  Y=Y0+R*SIN(T)
180 :  LOCATEY,X:PRINTCHR$($12);" ";
190 NEXT
```

### LOG

**TYPE: Floating-Point Function** 
**FORMAT: LOG(&lt;numeric&gt;)**

**Action:** Returns the natural logarithm (log to the base of e) of the argument.  If the value of the argument is zero or negative, the BASIC error message `?ILLEGAL QUANTITY` will occur.

**EXAMPLES of the LOG Function:**
```BASIC
10 PRINT LOG(42/9)
RUN
 1.54044504

10 NUM = LOG(ARG) / LOG(10): REM Calculates the LOG of ARG to the base 10)
```

### MID$

**TYPE: String Function**  
**FORMAT: MID$(&lt;string&gt;, &lt;numeric-1&gt;[,&lt;numeric-2&gt;])**

**Action:** The `MID$` function returns a sub-string which is taken from within a larger &lt;string&gt; argument.  The starting position of the sub-string is defined by the &lt;numeric-1&gt; argument and the length of the sub-string by the &lt;numeric-2&gt; argument.  Both of the numeric arguments can have values ranging from 0 to 255.

If the &lt;numeric-1&gt; value is greater than the length of the &lt;string&gt;, or if the &lt;numeric-2&gt; value is zero, then `MID$` gives a null string value.  If the &lt;numeric-2&gt; is left out, then the computer will assume that a length of the rest of the string is to be used.  And if the source string has fewer characters than &lt;numeric-2&gt;, from the starting position to the end of the string argument, then the whole rest of the string is used.

**EXAMPLE of the MID$ Function:**
```BASIC
10 G$ = "GOOD"
20 A$ = "MORNING EVENING AFTERNOON"
30 PRINT G$ + MID$(A$, 8, 8)
RUN
GOOD EVENING
```

### MENU

**TYPE: Command**  
**FORMAT: MENU**

**Action:** This command currently invokes the Commander X16 Control Panel. In the future, the menu may instead present a menu of ROM-based applications and routines.

**EXAMPLE of the MENU Command:**

```BASIC
MENU
```

### MOD

**TYPE: Function**  
**FORMAT: MOD(&lt;dividend&gt;, &lt;divisor&gt;)**

**Action:** Returns the truncated remainder of &lt;dividend&gt; divided by &lt;divisor&gt;

The `MOD` function supports 16bit signed numbers (-32768 to 32767)

**EXAMPLE of the MOD Function:**
```BASIC
PRINT MOD(-17, 5)        :REM RESULT WILL HAVE THE SAME SIGN AS DIVIDEND
-2

PRINT MOD(17, 5)
 2

PRINT MOD(42, 0)         :REM DIVISOR IS 0, RETURN ERROR
?DIVISION BY ZERO ERROR

PRINT MOD(65000, 101)    :REM DIVIDEND IS TOO LARGE FOR A SIGNED 16BIT VALUE
?ILLEGAL QUANTITY ERROR
```

### MON

**TYPE: Command**  
**FORMAT: MON (Alternative: MONITOR)**

**Action:** This command enters the machine language monitor. See the [Chapter 7: Machine Language Monitor](X16%20Reference%20-%2007%20-%20Machine%20Language%20Monitor.md#chapter-7-machine-language-monitor) for a  description.

**EXAMPLE of the MON Command:**

```BASIC
MON
MONITOR
```

### MOUSE

**TYPE: Command**  
**FORMAT: MOUSE &lt;mode&gt;**

**Action:** This command configures the mouse pointer.

| Mode | Description                              |
|------|------------------------------------------|
| 0    | Hide mouse                               |
| 1    | Show mouse, set default mouse pointer    |
| -1   | Show mouse, don't configure mouse cursor |

`MOUSE 1` turns on the mouse pointer and `MOUSE 0` turns it off. If the BASIC program has its own mouse pointer sprite configured, it can use `MOUSE -1`, which will turn the mouse pointer on, but not set the default pointer sprite.

The sprite attributes for the mouse pointer are always read from VERA address $1:FC00-$1:FC07, the attributes for sprite 0. The default cursor will be written to the default sprite 0 data address in VERA at $1:3000 when Mode is set to 1.

The size of the mouse pointer's area will be configured according to the current screen mode. If the screen mode is changed, the MOUSE statement has to be repeated.

**EXAMPLES of MOUSE Statement:**

```BASIC
MOUSE 1 : REM ENABLE MOUSE
MOUSE 0 : REM DISABLE MOUSE
```

### MOVSPR

**TYPE: Statement**  
**FORMAT: MOVSPR &lt;sprite idx&gt;,&lt;x&gt;,&lt;y&gt;**

**Action:** This command positions a sprite's upper left corner at a specific pixel location.  It does not change its visibility.

&lt;sprite idx&gt; is a value between 0-127 inclusive.
`x` and `y` have a range of -32768 to 32767 inclusive, but their meanings wrap every 1024 values. Values approaching 1023 will peek out from the left and top of the screen for x and y respectively as if they were negative and approaching 0. -1024, 1024, 0, and 2048 are all equivalent. Likewise, -10 and 1014 are equivalent.

**EXAMPLE of the MOVSPR Statement:**

```BASIC
10 BVLOAD "MYSPRITE.BIN",8,1,$3000
20 SPRMEM 1,1,$3000,1
30 SPRITE 1,3,0,0,3,3
40 MOVSPR 1,320,200
```

### MX/MY/MB

**TYPE: System variable**  
**FORMAT: MX**  
**FORMAT: MY**  
**FORMAT: MB**

**Action:** Return the horizontal (`MX`) or vertical (`MY`) position of the mouse pointer, or the mouse button state (`MB`).

`MB` returns the sum of the following values depending on the state of the buttons:

| Value | Button |
|-------|--------|
| 0     | none   |
| 1     | left   |
| 2     | right  |
| 4     | third  |

**EXAMPLE of the MX/MY/MB variables:**

```BASIC
REM SIMPLE DRAWING PROGRAM
10 SCREEN$80
20 MOUSE1
25 OB=0
30 TX=MX:TY=MY:TB=MB
35 IFTB=0GOTO25
40 IFOBTHENLINEOX,OY,TX,TY,16
50 IFOB=0THENPSETTX,TY,16
60 OX=TX:OY=TY:OB=TB
70 GOTO30
```

### MWHEEL

**TYPE: System variable**  
**FORMAT: MWHEEL**

**Action:** Return the mouse scroll wheel movement since the value was last read. The value is negative if the scroll wheel is
moved away from the user, and positive if it is moved towards the user. The range of the returned value is -128 to +127.

### NEW

**TYPE: Command**  
**FORMAT: NEW**

**Action:** The `NEW` command is used to delete the program currently in memory and clear all variables.  Before typing in a new program, `NEW` should be used in direct mode to clear memory.  `NEW` can also be used in a program, but you should be aware of the fact that it will erase everything that has gone before and is still in the computer's memory.  This can be particularly troublesome when you're trying to debug your program.

> **BE CAREFUL**: Not clearing out an old program before typing a new one can result in a confusing mix of the two programs.

**EXAMPLES of the NEW Command:**
```BASIC
NEW : REM Clears the program and all variables)
10 NEW : REM Performs a NEW operation and STOPs the program.
```

### NEXT

**TYPE: Statement**  
**FORMAT: NEXT [&lt;counter&gt;],[&lt;counter&gt;]...**

**Action:** The `NEXT` statement is used with [`FOR`](#for-to-step) to establish the end of a `FOR`...`NEXT` loop.  The `NEXT` need not be physically the last statement in the loop, but it is always the last statement executed in a loop.  The &lt;counter&gt; is the loop index's variable name used with `FOR` to start the loop.  A single `NEXT` can stop several nested loops when it is followed by each `FOR`'s &lt;counter&gt; variable name(s).  to do this each name must appear in the order of inner-most nested loop first, to outer-most nested loop last.  When using a single `NEXT` to increment and stop several variable names, each variable name must be separated by commas.  Loops can be nested to 9 levels.  If the counter variable(s) are omitted, the counter associated with the `FOR` of the current level (of the nested loops) is incremented.

When the `NEXT` is reached, the counter value is incremented by 1 or by an optional `STEP` value.  It is then tested against an end-value to see if it's time to stop the loop.  A loop will be stopped when a `NEXT` is found which has its counter value greater than the end-value.

**EXAMPLES of the NEXT Statement:**
```BASIC
10 FOR A=1 TO 5: FOR B=10 TO 20: FOR C=5 TO -10 STEP -1
20 NEXT C, B, A : REM Stopping nested loops

10 FOR A = 1 TO 100
20 FOR B = 1 TO 10
30 NEXT B
500 NEXT A  : REM Note how the loops do NOT cross each other.

10 FOR Z = 1 TO 10
20 FOR X = 1 TO 20
30 NEXT
40 NEXT : REM Notice that no variable names are needed
```

### NOT

**TYPE: Logical Operator**  
**FORMAT: NOT &lt;expression&gt;**

**Action:** The `NOT` logical operator "complements" the value of each bit in its single operand, producing an integer "two's complement" result.  In other words, the `NOT` is really saying, "if it isn't...".  When working with a floating-point number, the operands are converted to integers and any fractions are lost.  The `NOT` operator can also be used in a comparison to reverse the true/false value which was the result of a relationship test and therefore it will reverse the meaning of the comparison.  In the first example below, if the "two's complement" of "I" is equal to "D" and if "D" is `NOT` equal to "JA" then the expression is true.

**EXAMPLES of the NOT Operator:**
```BASIC
10 IF NOT I = D AND NOT (D=JA) THEN...

IA% = NOT 42 : PRINT IA%
-43
```

> **NOTE:** To find the value of `NOT` use the expression X = (-(X+1)).  (The two's complement of any integer is the bit complement plus one.)

### ON

**TYPE: Statement**  
**FORMAT: ON &lt;variable&gt; GOTO / GOSUB &lt;line number&gt; [,&lt;line number&gt;]...**

**Action:** The `ON` statement is used to [`GOTO`](#goto) or [`GOSUB`](#gosub) to one of several given line numbers, depending on the value of a variable.  The value of the variables can range from zero through the number of lines given.  If the value is a non-integer, the fractional portion is left off.  for example, if the variable value is 3, `ON` will `GOTO` (or `GOSUB`) the third line number in the list.

If the value of the variable is negative, the BASIC error message `?ILLEGAL QUANTITY` occurs.  If the number is zero, or greater than the number of items in the list, the program just ignores the statement and continues with the statement following the `ON` statement.

`ON` is really an underused variant of the [`IF...THEN...`](#if-then) statement.  Instead of using a whole lot of `IF` statements each of which sends the program to one specific line, one `ON` statement can replace a list of `IF` statements.  When you look at the first example you should notice that the one `ON` statement replaces four `IF...THEN...` statements.

**EXAMPLES of the ON Statement:**
```BASIC
ON -(X=2) - 2 * (X=6) - 3 * (X < 3) - 4 * (X > 7) GOTO 400, 900, 1000, 100

ON A GOTO 100,130,180,220

ON Z+7 GOSUB 4800, 230, 4800

100 ON NUM GOTO 250, 350, 320, 490

500 ON SUM / 2 + 1 GOSUB 100, 900, 50
```

### OLD

**TYPE: Command**  
**FORMAT: OLD**

**Action:** This command recovers the BASIC program in RAM that has been previously deleted using the [`NEW`](#new) command or through a [`RESET`](#reset).

**EXAMPLE of the OLD Statement:**

```BASIC
OLD
```

### OPEN

**TYPE: I/O Statement**  
**FORMAT: OPEN &lt;file number&gt;, &lt;device&gt; [, &lt;address&gt;] [, "&lt;file name&gt; [,&lt;type&gt;][, &lt;mode&gt;]"]**

**Action** This statement `OPEN`s a channel for input and/or output to a peripheral device.  however, you may NOT need all those ports for every `OPEN` statement.  Some `OPEN` statements require only two codes:

- LOGICAL FILE NUMBER
- DEVICE NUMBER

The &lt;file number&gt; is the logical file number, which relates to the `OPEN`, [`CLOSE`](#close), [`CMD`](#cmd), [`GET#`](#get-1), [`INPUT#`](#input-1), and [`PRINT#`](#print-1) statements to each other and associates them with the file name and the piece of equipment being used.  The logical file number can range from 1 to 255 and you can assign it any number you want in that range.

> **NOTE:** File numbers over 128 were really designed for other uses, so it's good practice to use only numbers below 127 for file numbers.

Each peripheral device (printer, disk drive, etc) in the system has its own number which it answers to.  The &lt;device&gt; number is used with `OPEN` to specify on which device the data file exists. Peripherals like disk drives or printers also answer to several secondary addresses.  Think of these as codes which tell each device what operation to perform.  The device logical file number is used with every `GET#`, `INPUT#`, and `PRINT#`.

If the &lt;device&gt; number is left out the Commander X16 will automatically assume that you want to talk to device #1, which has traditionally been assigned to the tape device.  Since the Commander X16 has no support for the tape device, I/O statements that reference it may operate with no error, but no actual work will be done.  Because of this, it should be assumed that specifying the device address is NOT optional.

For disk files, the secondary addresses 2 through 14 are available for data files, but other numbers have special meanings for DOS commands.  You must use a secondary address when using your disk drive(s).

The &lt;file name&gt; is a string of 1 to 16 characters and is optional for printer files.  If the file &lt;type&gt; is left out, the type of file will automatically default to the Program (PRG) file type unless the &lt;mode&gt; is given.  Sequential (SEQ) files are `OPEN`ed for reading (&lt;mode&gt;=R) unless you specify that files should be `OPEN`ed for writing (&lt;mode&gt;=W)  A file &lt;type&gt; can be used to `OPEN` an existing Relative file.  Use **REL** for &lt;type&gt; with Relative files.  Relative and Sequential files are for disk only.

> **NOTE:** Sequential files written outside of a disk image (.D64, .D81, etc) will appear as **PRG** files when viewing the file listing of the SD card.  This is because the FAT32 file system used by the SD card does not differentiate between file types. 

If you try to access a file before it is `OPEN`ed the BASIC error message `?FILE NOT OPEN` will occur.  If you try to `OPEN` a file for reading which does not exist the BASIC error message `?FILE NOT FOUND` will occur.  If a file is `OPEN`ed to disk and the file name already exists, the DOS error message `FILE EXISTS` occurs.  If a file is `OPEN`ed that is already `OPEN`, the BASIC error message `FILE OPEN` occurs.

**EXAMPLES of the OPEN Statement:**
- OPEN 2, 8, 2, "TEXT FILE, SEQ, W"  (opens a sequential file on disk)
- OPEN 50, 0 (keyboard input)
- OPEN 4, 3 (screen output)
- OPEN 75, 4 (printer output)
- OPEN 1, 8, 15, "COMMAND" (send a command to a disk device)


> **NOTE:** More information on working with disk files can be found in [Chapter 13](X16%20Reference%20-%2013%20-%20Working%20with%20CMDR-DOS.md#chapter-13-working-with-cmdr-dos).

### OR

**TYPE: Logical Operator**  
**FORMAT: &lt;operand&gt; OR &lt;operand&gt;**

**Action:** Just as the relational operators can be used to make decisions regarding program flow, logical operators can connect two or more relations and return a true or false value which can then be used in a decision.  When used in calculations, the logical `OR` gives you a bit result of 1 if the corresponding bit of either, or both, operands is 1.  This will produce an integer as a result, depending on the values of the operands.

When used in comparisons the logical `OR` operator is also used to link two expressions into a single compound expression.  If either of the expressions are true, the combined expression value is true (-1).  In the first example below, if AA is equal to BB `OR` if XX is 20, the expression is true.

Logical operators work by converting their operands to 16 bit, signed, two's complement integers in the range of -32768 to +32767.  If the operands are not in that range, an error message results.  Each bit of thee result is determined by the corresponding bits in the two operands.

**EXAMPLES of the OR Operator:**
```BASIC
10 IF (AA=BB) OR (XX=20) THEN...

50 KK% = 64 OR 32: PRINT KK%
RUN
 96 (64 has a bit value of 1000000 and 100000 for 32. ORing the two together results in 1100000 or 96 decimal)
```

### OVAL

**TYPE: Statement**  
**FORMAT: OVAL &lt;x1&gt;,&lt;y1&gt;,&lt;x2&gt;,&lt;y2&gt;,&lt;color&gt;**

**Action:** This command draws a filled oval on the graphics screen in a given color.

The coordinate arguments define the rectangular bounding box of the oval. To draw a filled circle, make the width and height equal to each other.

**EXAMPLE of the OVAL Statement:**

```BASIC
10 SCREEN $80
20 FORI=1 TO 20:OVAL RND(1)*320,RND(1)*200,RND(1)*320,RND(1)*200,RND(1)*128:NEXT
30 GOTO 20
```

### PEEK

**TYPE: Integer Function**  
**FORMAT: PEEK(&lt;address&gt;)**

**Action:** Returns the value at given memory address

`PEEK`ing values within the BRAM (`$A000`) and KERNAL/Cartridge (`$C000`)
requires using [`BANK`](#bank) to set the banks accordingly.

**EXAMPLE of the PEEK function:**

```BASIC
10 A=PEEK($C000)
20 PRINT A
```

### POINTER

**TYPE: Function**  
**FORMAT: POINTER(&lt;variable&gt;)**

**Action:** Returns the memory address of the internal structure representing a BASIC variable.

**EXAMPLE of the POINTER Function:**

```BASIC
10 A$="MOO"
20 PRINT HEX$(POINTER(A$))
RUN
0823
```

### POKE

**TYPE: Statement**  
**FORMAT: POKE &lt;address&gt;, &lt;value&gt;**

**Action:** Sets the contents of the memory address to given value.

To write to memory within a RAMBANK page, [`BANK`](#bank) must be 
called beforehand with the appropriate arguments.

Writing to values within the KERNAL/Cartridge area (`$C000`)
will not work as expected and may silently fail in KERNAL ROM versions
older than R49. In R49, POKE works as expected assuming the 
area being written to is RAM and that `BANK` has been 
called with appropriate arguments.

**EXAMPLE of the POKE Statement:**

```BASIC
10 POKE $A000,47
```

### POS

**TYPE: Integer Function**  
**FORMAT: POS(&lt;dummy&gt;)**

**Action:** Tells you the current cursor position which, of course, is in the range of 0 (leftmost character) through position 79 on an 80 character logical screen line.  If the Commander X16 is in 40 column mode, any position from 40 to 79 will refer to the second screen line.  The &lt;dummy&gt; argument is ignored.

**EXAMPLE of the POS Function:**
```BASIC
10 IF POS(0) > 38 THEN PRINT CHR$(13)
```

### POWEROFF

**TYPE: Command**  
**FORMAT: POWEROFF**

**Action:** This command instructs the SMC to power down the system. This is equivalent to pressing the physical power switch.

**EXAMPLE of the POWEROFF Statement:**

```BASIC
POWEROFF
```

### PRINT

**TYPE: Statement**  
**FORMAT: PRINT [&lt;variable&gt;][&lt;,/;&gt;&lt;variable&gt;]...**

**Action:** The `PRINT` statement is normally used to write data items to the screen.  However, the [`CMD`](#cmd) statement may be used to redirect that output to any other device in the system.  The &lt;variable(s)&gt; in the output-list are expressions of any type.  If no output-list is present, a blank line is printed.  The position of each printed item is determined by the punctuation used to separate items in the output-list.

The punctuation characters that you can use are blanks, commas, or semicolons.  the 80 character logical screen line is divided into 8 print zones of 10 spaces each.  In the list of expressions, a comma causes the next value to be printed at the beginning of the next zone.  A semicolon causes the next value to be printed immediately following the previous value.  However, there are two exceptions to this rule:

1. Numeric items are followed by an added space.
2. Positive numbers have a space preceding them.

When you use blanks or no punctuation between string constants or variable names, it has the same effect as a semicolon.  However, blanks between a string and a numeric item or between two numeric items will stop output without printing the second item.

If a comma or a semicolon is at the end of the output-list, the next `PRINT` statement begins printing on the same line, and spaced accordingly.  If no punctuation finishes the list, a carriage-return and a line-feed are printed at the end of the data.  The next `PRINT` statement will begin on the next line.  If your output is directed to the screen and the data printed is longer than 40 columns, the output is continued on the next screen line.

There is no statement in BASIC with more variety than the `PRINT` statement.  There are so many symbols, functions, and parameters associated with this statement that it might almost be considered as a language of its own within BASIC; a language specially designed for writing on the screen.

**EXAMPLES of the PRINT Statement:**

```BASIC
10 X = 10
20 PRINT -5 * X, X - 5, X + 5, X / 5
RUN
-50        5         15        2
```
```BASIC
10 X = 9
20 PRINT X; "SQUARED IS";X * X;"AND";
30 PRINT X "MULTIPLIED BY 19 IS" X * 19
RUN
 9 SQUARED IS 81 AND 9 MULTIPLIED BY 19 IS 171
```
```BASIC
10 A$(1)="ALPHA":A$(2)="BRAVO":A$(3)="CHARLIE":A$(4)="DELTA":A$(5)="ECHO"
20 PRINT A$(1)A$(2);A$(3) A$(4),A$(5)
RUN
ALPHABRAVOCHARLIEDELTA        ECHO
```
**Quote Mode**

Once the quote mark ( <mark>**SHIFT**</mark> <mark>**2**</mark> ) is typed, the cursor controls stop operating and start displaying reversed characters which actually stand for the cursor control you are hitting.  This allows you to program these cursor controls, because once the text inside the quotes is `PRINT`ed, they perform their functions.  The <mark>**INST/DEL**</mark> key is the only cursor control not affected by "quote mode".

**1. Cursor Movement**

The cursor controls which can be "programmed" in quote mode are:

> | **KEY** | **APPEARS AS** |
> |---------:|:----------------:|
> | <mark>**CLR/HOME**</mark> | ![Reverse S](images/rvs-S.png) |
> | <mark>**SHIFT**</mark> <mark>**CLR/HOME**</mark> | ![Reverse Heart](images/rvs-heart.png) |
> | <mark>**&uarr;CRSR&darr;**</mark> | ![Reverse Q](images/rvs-Q.png) |
> | <mark>**SHIFT**</mark> <mark>**&uarr;CRSR&darr;**</mark> | ![Reverse Ball](images/rvs-ball.png) |
> | <mark>**&larr;CRSR&rarr;**</mark> | ![Reverse Left Bracket](images/rvs-r-bracket.png) |
> | <mark>**SHIFT**</mark> <mark>**&larr;CRSR&rarr;**</mark> | ![Reverse Bar](images/rvs-bar.png) |

If you wanted the word HELLO to `PRINT` diagonally from the upper left corner of the screen, you would type:

PRINT "<mark>**CLR/HOME**</mark> H <mark>**&uarr;CRSR&darr;**</mark> E <mark>**&uarr;CRSR&darr;**</mark> L <mark>**&uarr;CRSR&darr;**</mark> L <mark>**&uarr;CRSR&darr;**</mark> O"

Which would appear as:

![Cursor Pos. Example](images/print-screen-pos-example.png)

**2. Reverse Characters**

Holding down the <mark>**CTRL**</mark> key and hitting <mark>**9**</mark> will cause <marksq>**R**</marksq> to appear inside the quotes.  This will make all characters print starting in *reverse video* (like a negative of a picture).  To end the reverse printing hit <mark>**CTRL**</mark> <mark>**0**</mark>, which prints a ![](images/norm-lower-bar.png) or else `PRINT` a <mark>**RETURN**</mark> ([`CHR$`](#chr)(13)).  (Just ending the `PRINT` statement without a semicolon or a comma will take care of this.)

**3. Color Controls**

Holding down the <mark>**CTRL**</mark> or the <mark>**ALT**</mark> key with any of the 8 color keys will make a special reversed character which appears in quotes.  When the character is `PRINT`ed, then the color change will occur.

> | **KEY** | **COLOR** | **APPEARS AS** |
> |--------:|:---------:|:--------------:|
> | <mark>**CTRL**</mark> <mark>**1**</mark> | Black | ![Reverse UR Corner](images/rvs-ur-corner.png) |
> | <mark>**CTRL**</mark> <mark>**2**</mark> | White | ![Reverse E](images/rvs-E.png) |
> | <mark>**CTRL**</mark> <mark>**3**</mark> | Red | ![Reverse Pound](images/rvs-pound.png) |
> | <mark>**CTRL**</mark> <mark>**4**</mark> | Cyan | ![Reverse Left Ramp](images/rvs-l-ramp.png) |
> | <mark>**CTRL**</mark> <mark>**5**</mark> | Purple | ![Reverse Left Half Tile](images/rvs-half-tile.png) |
> | <mark>**CTRL**</mark> <mark>**6**</mark> | Green | ![Reverse Up Arrow](images/rvs-up-arr.png) |
> | <mark>**CTRL**</mark> <mark>**7**</mark> | Blue | ![Reverse Left Arrow](images/rvs-l-arr.png) |
> | <mark>**CTRL**</mark> <mark>**8**</mark> | Yellow | ![Reverse Pi](images/rvs-pi.png) |
> | <mark>**ALT**</mark> <mark>**1**</mark> | Orange | ![Reverse Spade](images/rvs-spade.png) |
> | <mark>**ALT**</mark> <mark>**2**</mark> | Brown | ![Reverse Upper Left Corner](images/rvs-ul-corner.png) |
> | <mark>**ALT**</mark> <mark>**3**</mark> | Light Red | ![Reverse X Symbol](images/rvs-x-symbol.png) |
> | <mark>**ALT**</mark> <mark>**4**</mark> | Grey 1 | ![Reverse Circle](images/rvs-circle.png) |
> | <mark>**ALT**</mark> <mark>**5**</mark> | Grey 2 | ![Reverse Club](images/rvs-club.png) |
> | <mark>**ALT**</mark> <mark>**6**</mark> | Light Green | ![Reverse Right Offset Bar](images/rvs-r-offset-bar.png) |
> | <mark>**ALT**</mark> <mark>**7**</mark> | Light Blue | ![Reverse Diamond](images/rvs-diamond.png) |
> | <mark>**ALT**</mark> <mark>**8**</mark> | Grey 3 | ![Reverse Plus Symbol](images/rvs-plus-symbol.png) |

If you wanted to print the word HELLO in cyan and the word THERE in white, type:

PRINT "<mark>**CTRL**</mark> <mark>**4**</mark>HELLO<mark>**CTRL**</mark> <mark>**2**</mark>THERE"

Which would appear as:

![Print Color Example](images/print-color-example.png)

**4. Insert Mode**

The spaces created by using the <mark>**INST/DEL**</mark> key have some of the same characteristics as quote mode.  The cursor controls and color controls show up as reversed characters.  The only difference is in the <mark>**INST**</mark> and <mark>**DEL**</mark> which performs
its normal function even in quote mode, now creates the <marksq>**T**</marksq>.  And <mark>**INST**</mark>, which created a special character in quote mode, inserts spaces normally.

Because of this, it is possible to create a `PRINT` statement containing <mark>**DEL**</mark>etes, which cannot be `PRINT`ed in quote mode.  Here is an example of how this is done:

10 PRINT "HELLO" <mark>**INST/DEL**</mark> <mark>**SHIFT**</mark> <mark>**INST/DEL**</mark> <mark>**SHIFT**</mark> <mark>**INST/DEL**</mark> <mark>**INST/DEL**</mark> <mark>**INST/DEL**</mark>P"

which displays as:

10 PRINT "HELLO<marksq>**T**</marksq><marksq>**T**</marksq>P"

When the above line is [`RUN`](#run), the word displayed will be HELP, because the last two letters are deleted and the P is put in their place.

> **WARNING:** The <mark>**DEL**</mark>etes will work when [`LIST`](#list)ing as well as `PRINT`ing, so editing a line with these characters will be difficult.

The "insert mode" condition is ended when the <mark>**RETURN**</mark> (or <mark>**SHIFT**</mark> <mark>**RETURN**</mark>) key is hit, or when as many characters have been typed as spaces were inserted.

**5. Other Special Characters**

There are some other characters that can be `PRINT`ed for special function, although they are not easily available from the keyboard.  In order to get these in quotes, you must leave empty spaces for them in the line, hit <mark>**RETURN**</mark> or <mark>**SHIFT**</mark> <mark>**RETURN**</mark>, and go back to the spaces with the cursor controls. Now you must hit <mark>**CTRL**</mark> <mark>**RVS/ON**</mark>, to start typing reversed characters, and type the keys shown below:

| Function | Type     | Appears As |
|:--------:|:---------|:-----------|
| <mark>**SHIFT**</mark> <mark>**RETURN**</mark> | <mark>**SHIFT**</mark> <mark>**M**</mark> | ![Reverse Backslash](images/rvs-backslash.png) |
| Switch to lower case | <mark>**N**</mark> | ![Reverse N](images/rvs-N.png) |
| Switch to upper case | <mark>**SHIFT**</mark> <mark>**N**</mark> | ![Reverse Slash](images/rvs-slash.png) |
| Disable case-switching keys | <mark>**H**</mark> | ![Reverse H](images/rvs-H.png) |
| Enable case-switching keys | <mark>**I**</mark> | ![Reverse I](images/rvs-I.png) |

The <mark>**SHIFT**</mark> <mark>**RETURN**</mark> will work in the `LIST`ing as well as `PRINT`ing, so editing will be almost impossible if this character is used.  The `LIST`in will also look very strange.

### PRINT#

**TYPE: I/O Statement**  
**FORMAT: PRINT# &lt;file number&gt; [&lt;variable&gt;][&lt;,/;&gt;&lt;variable&gt;]...** 

**Action:** The `PRINT#` statement is used to write data items to a logical file.  It must use the same number used to `OPEN` the file.  Output goes to the device number used in the [`OPEN`](#open) statement.  The &lt;variable&gt; expressions in the output-list can be of any type.  The punctuation characters between items are the same as with the `PRINT` statement and they can be used in the same ways.  The effects of punctuation are different in one significant respects.

If no punctuation finishes the list, a carriage-return and a line-feed are written at the end of the data.  If a comma or semicolon terminates the output-list, the carriage-return and line-feed are suppressed.  Regardless of the punctuation, the next `PRINT#` statement beings output in the next available character position.  The line-feed will act as a stop when using the [`INPUT#`](#input-1) statement, leaving an empty variable when the next `INPUT#` is executed.  The line-feed can be suppressed or compensated for as shown in the examples below.

The easiest way to write more than one variable to a file is to set a string variable to [`CHR$`](#chr)(13), and use that string in between all the other variables when writing the file.

**EXAMPLES of the PRINT# Statement:**
```BASIC
10 OPEN 1,8,1, "TEXT FILE,SEQ,W"
20 CR$ = CHR$(13)                     :REM By changing the CHR$(13) to CHR$(44)
30 PRINT# 1,1;CR$;2;CR$;3;CR$;4;CR$;5 :REM you put a "," between each variable.
40 PRINT# 1,6                         :REM CHR$(59) would put a ";" between each variable.
```
```BASIC
10 CM$=CHR$(44) : CR$=CHR$(13)
20 PRINT#1, "AAA" CM$ "BBB","CCC";"DDD";"EEE" CR$ "FFF",CR$;
30 REM Result: "AAA,BBB     CCCDDDEEE<CR>FFF<CR>
40 INPUT#1, A$,BCDE$,F$
```
```BASIC
10 CR$=CHR$(13)
20 PRINT#2, "AAA";CR$;"BBB"
30 PRINT#2, "CCC";
40 INPUT#2, A$, B$, DUMMY$, C$
```

### PSET

**TYPE: Statement**  
**FORMAT: PSET &lt;x&gt;,&lt;y&gt;,&lt;color&gt;**

**Action:** This command sets a pixel on the graphics screen to a given color.

**EXAMPLE of the PSET Statement:**

```BASIC
10 SCREEN$80
20 FORI=1TO20:PSETRND(1)*320,RND(1)*200,RND(1)*256:NEXT
30 GOTO20
```

### PSGCHORD

**TYPE: Statement**  
**FORMAT: PSGCHORD &lt;first voice&gt;,&lt;string&gt;**

**Action:** This command uses the same syntax as [`PSGPLAY`](#psgplay), but instead of playing a series of notes, it will start all of the notes in the string simultaneously on one or more voices. The first parameter to `PSGCHORD` is the first voice to use, and will be used for the first note in the string, and subsequent notes in the string will be started on subsequent voices, with the voice after 15 being voice 0.

All macros are supported, even the ones that only affect `PSGPLAY` and [`FMPLAY`](#fmplay).

The full set of macros is documented [here](X16%20Reference%20-%20Appendix%20A%20-%20Sound.md#basic-fmplay-and-psgplay-string-macros).

**EXAMPLE of the PSGCHORD Statement:**

```BASIC
10 PSGINIT
20 PSGCHORD 15,"O3G>CE" : REM STARTS PLAYING A CHORD ON VOICES 15, 0, AND 1
30 PSGPLAY 14,">C<DGB>CDE" : REM PLAYS A SERIES OF NOTES ON VOICE 14
40 PSGCHORD 15,"RRR" : REM RELEASES CHORD ON VOICES 15, 0, AND 1
50 PSGPLAY 14,"O4CAG>C<A" : REM PLAYS A SERIES OF NOTES ON VOICE 14
60 PSGCHORD 0,"O3A>CF" : REM STARTS PLAYING A CHORD ON VOICES 0, 1, AND 2
70 PSGPLAY 14,"L16FGAB->CDEF4" : REM PLAYS A SERIES OF NOTES ON VOICE 
80 PSGCHORD 0,"RRR" : REM RELEASES CHORD ON VOICES 0, 1, AND 2
```

### PSGFREQ

**TYPE: Statement**  
**FORMAT: PSGFREQ &lt;voice&gt;,&lt;frequency&gt;**

**Action:** Play a note by frequency on the VERA PSG. The accepted range is in Hz from 1 to 24319. PSGFREQ also accepts a frequency of 0 to release the note.

**EXAMPLE of the PSGFREQ Statement:**

```BASIC
10 PSGINIT : REM RESET ALL VOICES TO SQUARE WAVEFORM
20 PSGFREQ 0,350 : REM PLAY A SQUARE WAVE AT 350 HZ
30 PSGFREQ 1,440 : REM PLAY A SQUARE WAVE AT 440 HZ ON ANOTHER VOICE
40 FOR X=1 TO 10000 : NEXT X : REM DELAY A BIT
50 PSGFREQ 0,0 : PSGFREQ 1,0 : REM RELEASE BOTH VOICES
```

The above BASIC program plays a sound similar to a North American dial tone for a few seconds.

### PSGINIT

**TYPE: Statement**  
**FORMAT: PSGINIT**

**Action:** Initialize VERA PSG, silence all voices, set volume to 63 on all voices, and set the waveform to pulse and the duty cycle to 63 (50%) for all 16 voices.

### PSGNOTE

**TYPE: Statement**  
**FORMAT: PSGNOTE &lt;voice&gt;,&lt;note&gt;**

**Action:** Play a note on the VERA PSG. The note value is constructed as follows. Using hexadecimal notation, the first nybble is the octave, 0-7, and the second nybble is the note within the octave as follows:

| `$x0` | `$x1` | `$x2` | `$x3` | `$x4` | `$x5` | `$x6` | `$x7` | `$x8` | `$x9` | `$xA` | `$xB` | `$xC` | `$xD-$xF` |
|-|-|-|-|-|-|-|-|-|-|-|-|-|-|
| Release | C | C&#9839;/D&#9837; | D | D&#9839;/E&#9837; | E | F | F&#9839;/G&#9837; | G | G&#9839;/A&#9837; | A | A&#9839;/B&#9837; | B | no-op |

**EXAMPLE of the PSGNOTE Statement:**

```BASIC
10 PSGNOTE 1,$4A : REM PLAYS CONCERT A
20 FOR X=1 TO 5000 : NEXT X : REM DELAYS FOR A BIT
30 PSGNOTE 1,0 : REM RELEASES THE NOTE
40 FOR X=1 TO 2500 : NEXT X : REM SHORT DELAY
50 PSGNOTE 1,$3A : REM PLAYS A IN THE 3RD OCTAVE
60 FOR X=1 TO 2500 : NEXT X : REM SHORT DELAY
70 PSGNOTE 1,0 : REM RELEASES THE NOTE
```

### PSGPAN

**TYPE: Statement**  
**FORMAT: PSGPAN &lt;voice&gt;,&lt;panning&gt;**

**Action:** Sets the simple stereo panning on a VERA PSG voice. Valid values are as follows:

* 1 = left
* 2 = right
* 3 = both

### PSGPLAY

**TYPE: Statement**  
**FORMAT: PSGPLAY &lt;voice&gt;,&lt;string&gt;**

**Action:** This command is very similar to `PLAY` on other BASICs such as GWBASIC. It takes a string of notes, rests, tempo changes, note lengths, and other macros, and plays all of the notes synchronously.  That is, the PSGPLAY command will not return control until all of the notes and rests in the string have been fully played.

The full set of macros is documented [here](X16%20Reference%20-%20Appendix%20A%20-%20Sound.md#basic-fmplay-and-psgplay-string-macros).

**EXAMPLE of the PSGPLAY Statement:**

```BASIC
10 PSGWAV 0,31 : REM PULSE, 25% DUTY CYCLE
20 PSGPLAY 0,"T180 S0 O5 L32" : REM TEMPO 180 BPM, LEGATO, OCTAVE 5, 32ND NOTES
30 PSGPLAY 0,"C<G>CEG>C<G<A-"
40 PSGPLAY 0,">CE-A-E-A->CE-A-"
50 PSGPLAY 0,"E-<<B->DFB-FB->DFB-F" : REM GRAB YOURSELF A MUSHROOM
```

### PSGVOL

**TYPE: Statement**  
**FORMAT: PSGVOL &lt;voice&gt;,&lt;volume&gt;**

**Action:** This statement sets the voice's volume. The volume remains at the requested level until another `PSGVOL` command for that voice or [`PSGINIT`](#psginit) is called.  Valid range is from 0 (completely silent) to 63 (full volume).

### PSGWAV

**TYPE: Statement**  
**FORMAT: PSGWAV &lt;voice&gt;,&lt;w&gt;**

**Action:** Sets the waveform and duty cycle for a PSG voice.

* w = 0-63 -> Pulse: Duty cycle is `(w+1)/128`. A value of 63 means 50% duty cycle.
* w = 64-127 -> Sawtooth (all values have identical effect)
* w = 128-191 -> Triangle (all values have identical effect)
* w = 192-255 -> Noise (all values have identical effect)

**EXAMPLE of the PSGWAV Statement:**

```BASIC
10 FOR O=$20 TO $50 STEP $10:REM OCTAVE LOOP
20 FOR N=1 TO 11 STEP 2:REM NOTE LOOP, EVERY OTHER NOTE
30 PSGNOTE 0,O+N:REM START PLAYBACK OF THE NOTE
40 FOR P=0 TO 30:REM PULSE WIDTH MODULATION LOOP (INCREASING DUTY)
50 PSGWAV 0,P:REM SET PW
60 FOR D=1 TO 30:NEXT D:REM DELAY LOOP
70 NEXT P
80 PSGNOTE 0,O+N+1:REM START PLAYBACK OF THE NOTE + A SEMITONE
90 FOR P=31 TO 1 STEP -1:REM PWM LOOP (DECREASING DUTY)
100 PSGWAV 0,P:REM SET PW
110 FOR D=1 TO 30:NEXT D:REM DELAY LOOP
120 NEXT P
130 NEXT N
140 NEXT O
150 PSGNOTE 0,0:REM STOP SOUND
```

This example plays a chromatic scale while applying pulse-width modulation on the voice.

### READ

**TYPE: Statement**  
**FORMAT: READ &lt;<variable>&gt; [,&lt;variable&gt;]...***

**Action:** The `READ` statement is used to fill variable names from constants in [`DATA`](#data) statements.  The data actually read must agree with the variable types specified or the BASIC error message `?SYNTAX ERROR` will result.  Variables in the `DATA` input-list must be separated by commas.

A single `READ` statement can access on or more `DATA` statements, which will be accessed in order (see [DATA](#data)), or several `READ` statements can access the same `DATA` statement.  If more `READ` statements are executed than the number of elements in `DATA` statement(s), in the program, the BASIC error message `?OUT OF DATA` is printed.  If the number of variables specified is fewer than the number of elements in the `DATA` statement(s), subsequent `READ` statements will continue reading at the next data element. (See [RESTORE](#restore).)

> **NOTE:** The `?SYNTAX ERROR` will appear with the line number from the `DATA` statement, NOT the `READ` statement.

**EXAMPLES of the READ Statement:**
```BASIC
10 READ A, B, C$
20 DATA 4, 42, HELLO
```
```BASIC
10 FOR X = 1 TO 10: READ A(X): NEXT X
20 DATA 3.14, 42.5, 18.32, 103.52, 16.67
30 DATA 1.11, 86.0, 32.54, 5.52, 2.23
```
```BASIC
10 READ CITY$, STATE$, ZIP
20 DATA PUYALLUP, WASHINGTON, 98373
```

### REM

**TYPE: Statement**  
**FORMAT: REM [&lt;remark&gt;]**

**Action:** The `REM` statement makes your programs more easily understood when [`LIST`](#list)ed.  It's a reminder to yourself to tell you what you had in mind when you were writing each section of the program.  For instance, you might want to remember what a variable is used for, or some other useful information.  The `REM`ark can be any text, word, or character including the colon `(:)` or BASIC keywords.  The `REM` statement and anything following it on the same line number are ignored by BASIC, but `REM`arks are printed exactly as entered when the program is listed.  A `REM` statement can be referred to by a [`GOTO`](#goto) or [`GOSUB`](#gosub) statement, and the execution of the program will continue with the next higher program line having executable statements.

**EXAMPLES of the REM Statement:**
```BASIC
10 REM CALCULATE THE AVERAGE VELOCITY OF AN UNLADEN SWALLOW
20 FOR X = 1 TO 20: REM LOOP FOR TWENTY VALUES
30 SUM = SUM + VEL(X) : NEXT X
40 AVG = SUM / 20
```

### RING

**TYPE: Statement**  
**FORMAT: RING &lt;x1&gt;,&lt;y1&gt;,&lt;x2&gt;,&lt;y2&gt;,&lt;color&gt;**

**Action:** This statement draws an oval outline on the graphics screen in a given color.

The coordinate arguments define the rectangular bounding box of the oval. To draw a circle outline, make the width and height equal to each other.

**EXAMPLE of the RING Statement:**

```BASIC
10 SCREEN $80
20 FORI=1 TO 20:RING RND(1)*320,RND(1)*200,RND(1)*320,RND(1)*200,RND(1)*128:NEXT
30 GOTO 20
```

### RECT

**TYPE: Statement**  
**FORMAT: RECT &lt;x1&gt;,&lt;y1&gt;,&lt;x2&gt;,&lt;y2&gt;,&lt;color&gt;**

**Action:** This statement draws a solid rectangle on the graphics screen in a given color.

**EXAMPLE of the RECT Statement:**

```BASIC
10 SCREEN$80
20 FORI=1TO20:RECTRND(1)*320,RND(1)*200,RND(1)*320,RND(1)*200,RND(1)*256:NEXT
30 GOTO20
```

### REBOOT

**TYPE: Command**  
**FORMAT: REBOOT**

**Action:** Performs a software reset of the system by calling the ROM reset vector.

**EXAMPLE of the REBOOT Statement:**

```BASIC
REBOOT
```

### REN

**TYPE: Command**  
**FORMAT: REN [&lt;new line num&gt;[, &lt;increment&gt;[, &lt;first old line num&gt;]]]**

**Action:** Renumbers a BASIC program while updating the line number arguments of [`GOSUB`](#gosub), [`GOTO`](#goto), [`RESTORE`](#restore), [`RUN`](#run), and [`THEN`](#if-then).

Optional arguments:  

* The line number of the first line after renumbering, default: **10**  
* The value of the increment for subsequent lines, default **10**  
* The earliest old line to start renumbering at, default: **0**  

**Please ensure your have saved your program before using this command to renumber.**

> **KNOWN BUG:**  In release R43, due to improper parsing of escape tokens, REN will improperly treat arguments to these statements as line numbers:
> 
> * [`FRAME`](#frame)
> * [`RECT`](#rect)
> * [`MOUSE`](#mouse)
> * [`COLOR`](#color)
> * [`PSGWAV`](#psgwav)
> 
> This behavior has been fixed in R44.


**EXAMPLE of the REN Statement:**

```BASIC
10 PRINT "HELLO"
20 DATA 1,2,3
30 DATA 4,5,6
40 READ X
50 PRINT X
60 RESTORE 30
70 READ X
80 PRINT X
90 GOTO 10

REN 100,5

LIST
100 PRINT "HELLO"
105 DATA 1,2,3
110 DATA 4,5,6
115 READ X
120 PRINT X
125 RESTORE 110
130 READ X
135 PRINT X
140 GOTO 100
READY.
```

### RESET

**TYPE: Command**  
**FORMAT: RESET**

**Action:** This command instructs the SMC to assert the reset line on the system, which performs a hard reset. This is equivalent to pressing the physical reset switch.

**EXAMPLE of the RESET Statement:**

```BASIC
RESET
```

### RESTORE

**TYPE: Statement**  
**FORMAT: RESTORE [&lt;linenum&gt;]**

**Action:** This statement resets the pointer for the [`READ`](#read) command. Without arguments, it will reset the pointer to the first [`DATA`](#data) constant in the program.  With &gt;linenum&gt; parameter, the statement will reset the pointer to the first `DATA` constant at or after that line number.

**EXAMPLE of the RESTORE Statement:**

```BASIC
10 DATA 1,2,3
20 DATA 4,5,6
30 READ Y
40 PRINT Y
50 RESTORE 20
60 READ Y
70 PRINT Y
```

This program will output the number 1 followed by the number 4.

### RETURN

**TYPE: Statement**  
**FORMAT: RETURN**

**Action:** The `RETURN` statement is used to exit from a subroutine called for by a [`GOSUB`](#gosub) statement.  `RETURN` restarts the rest of your program at the next executable statement following the `GOSUB`.  If you are nesting subroutines, each `GOSUB` must be paired with at least one `RETURN` statement.  A subroutine can contain any number of `RETURN` statements, but the first one encountered will exit the subroutine.

**EXAMPLE of the RETURN Statement:**
```BASIC
10 PRINT "THIS IS THE PROGRAM"
20 GOSUB 1000
30 PRINT "THE PROGRAM CONTINUES"
40 GOSUB 1000
60 END
1000 PRINT "THIS IS THE SUBROUTINE." : RETURN
```

### RIGHT$

**TYPE: String Function**  
**FORMAT: RIGHT$(&lt;string&gt;, &lt;numeric&gt;)**

**Action:** The `RIGHT$` function returns a sub-string taken from the right-most end of the &lt;string&gt; argument.  The length of the sub-string is defined by the &lt;numeric&gt; argument which can be any integer in the range of 0 to 255.  If the value of the numeric expression is zero, then a null string `("")` is returned.  If the value you give in the &lt;numeric&gt; argument is greater than the length of the &lt;string&gt; then the entire string is returned.

**EXAMPLE of the RIGHT$ Function:**
```BASIC
10 MSG$ = "COMMANDER X16"
20 PRINT RIGHT$(MSG$, 3)
RUN
X16
```

### RND

**TYPE: Floating-Point Function**  
**FORMAT: RND(&lt;numeric&gt;)**

**Action:** `RND` creates a floating-point random number from 0.0 to 1.0.  the computer generates a sequence of random numbers by performing calculations on a starting number, which in computer jargon is called a "seed".  The `RND` function is seeded on system power-up.  the &lt;numeric&gt; argument is a dummy, except for its sign (positive, zero, or negative).

If the &lt;numeric&gt; argument is positive, the same "pseudorandom" sequence of numbers is returned, starting from a given seed value.  Different number sequences will result from different seeds, but any sequence is repeatable by starting from the same seed number.  Having a known sequence of "random" numbers is useful in testing programs.

If you choose a &lt;numeric&gt; argument of zero, then `RND` generates a number directly from a free-running hardware clock (the system "jiffy clock").  Negative arguments cause the `RND` function to be re-seeded with each function call.

**EXAMPLES of the RND Function:**

```BASIC
10 PRINT INT(RND(0) * 50) : REM Returns random integers from 0 to 49

20 X = INT(RND(1) * 6) + INT(RND(1) * 6) + 2 : REM SIMULATES TWO DICE

30 X = INT(RND(1) * 1000) + 1 : REM RANDOM INTEGERS FROM 0 TO 1000

40 X = INT(RND(1) * 50) + 100 : REM RANDOM NUMBERS FROM 100 TO 249

50 X = RND(1) * (U - L) + L : REM RANDOM NUMBERS BETWEEN UPPER (U) AND LOWER (L) LIMITS.
```

### RPT$

**TYPE: Function**  
**FORMAT: RPT$(&lt;byte&gt;,&lt;count&gt;)**

**Action:** Returns a string of &lt;count&gt; instances of the PETSCII character represented by the numeric value &lt;byte&gt;.  This function is similar in behavior to [`CHR$`](#chr) but takes a second argument as a repeat count.

`RPT$(A,1)` is functionally equivalent to `CHR$(A)`.

**EXAMPLE of the RPT$ Function:**

```BASIC
10 REM TEN EXCLAMATION MARKS
20 PRINT RPT$(33,10)
READY.
RUN
!!!!!!!!!!

READY.
```

### RUN

**TYPE: Command**  
**FORMAT: RUN [&lt;line number&gt;]**

**Action:** The system command `RUN` is used to start the program currently in memory.  The `RUN` command causes an implied [`CLR`](#clr) operation to be performed before starting the program.  You can void the `CLR` operation by using [`CONT`](#cont) or [`GOTO`](#goto) to restart a program instead of `RUN`.  If a &lt;line number&gt; is specified, your program will start on that line.  Otherwise, the `RUN` command starts at the first line of the program.

The `RUN` command can also be used within a program.  if the &lt;line number&gt; you specify doesn't exist, the BASIC error message `?UNDEF'D STATEMENT` occurs.

A `RUN`ning program stops and BASIC returns to direct mode when an [`END`](#end) or [`STOP`](#stop) statement is reached, when the last line of the program is finished, or when a BASIC error occurs during execution.

**EXAMPLES of the RUN Command:**
- RUN - Starts at the first line of a program.
- RUN 500 - Starts at line number 500.
- RUN X - Starts at line X, or `?UNDEF'D STATEMENT error if there is no line X.

### SAVE

**TYPE: Command**
**FORMAT: SAVE &lt;filename&gt; \[, &lt;device&gt;**\]

**Action:** Saves a BASIC program to a file.

This saves the currently loaded BASIC program to a file. If the device number is not supplied, `SAVE` will use the default drive. This is usually the SD card.

Note that `SAVE` will not overwrite an existing file by default. To do this, you must prefix the filename with @:, like this: `SAVE "@:filename"`

**EXAMPLES of the SAVE Command:**

```BASIC
SAVE "HELLO.PRG"
```

The above example saves your Hello World program to the SD card.

```BASIC
SAVE "@:HELLO.PRG",9
```

The above example overwrites an existing file on drive 9, which would be a Commodore style disk drive plugged into the IEC port.

### SCREEN

**TYPE: Statement**  
**FORMAT: SCREEN &lt;mode&gt;**

**Action:** This statement switches screen modes.

**Suported Modes**
| Mode | Description |
|------|-------------|
| $00  | 80x60 text  |
| $01  | 80x30 text  |
| $02  | 40x60 text  |
| $03  | 40x30 text  |
| $04  | 40x15 text  |
| $05  | 20x30 text  |
| $06  | 20x15 text  |
| $07  | 22x23 text  |
| $08  | 64x50 text  |
| $09  | 64x25 text  |
| $0A  | 32x50 text  |
| $0B  | 32x25 text  |
| $80  | 320x240@256c 40x30 text |

Please refer to [Chapter 3: Editor](X16%20Reference%20-%2003%20-%20Editor.md#chapter-3-editor) for more information on text modes.  

The value of -1 toggles between modes $00 and $03.

**EXAMPLE of the SCREEN Statement:**

```BASIC
SCREEN 3 : REM SWITCH TO 40 CHARACTER MODE
SCREEN 0 : REM SWITCH TO 80 CHARACTER MODE
SCREEN -1 : REM SWITCH BETWEEN 40 and 80 CHARACTER MODE
```

### SGN

**TYPE: Integer Function**  
**FORMAT: SGN(&lt;numeric&gt;)**

**Action:** `SGN` gives you an integer value depending upon the sign of the &lt;numeric&gt; argument.  If the argument is positive, the result is 1, if zero the result is also zero, if negative the result is -1.

**EXAMPLE of the SGN Function:**

```BASIC
20 ON SGN(DV) + 2 GOTO 1000, 2000, 3000
25 REM JUMP TO 1000 IF DV IS NEGATIVE, 2000 IF DV IS ZERO, AND 300 IF DV IS POSITIVE.
```

### SIN

**TYPE: Floating-Point Function**  
**FORMAT: SIN(&lt;numeric&gt;)**

**Action:** `SIN` gives you the sine of the &lt;numeric&gt; argument, in radians.  The value of [`COS`](#cos)(x) is equal to `SIN`(x + 3.1415925 / 2).

**EXAMPLE of the SIN Function:**
```BASIC
125 AA = SIN(1.5) : PRINT AA
```
The result is .997494987.

### SLEEP

**TYPE: Statement**  
**FORMAT: SLEEP \[&lt;jiffies&gt;\]**

**Action:** With the default interrupt source configured and enabled, this command waits for `jiffies`+1 VSYNC events and then resumes program execution. In other words, `SLEEP` with no arguments is equivalent to `SLEEP 0`, which waits until the beginning of the next frame. Another useful example, `SLEEP 60`, pauses for approximately 1 second.

Allowed values for `jiffies` is from 0 to 65535, inclusive.

**EXAMPLE of the SLEEP Statement:**

```BASIC
10 FOR I=1 TO 10
20 PRINT I
30 SLEEP 60
40 NEXT
```

### SPC

**TYPE: Special Function:**  
**FORMAT: SPC(&lt;numeric&gt;)**

**Action:** The `SPC` function is used to control the formatting of data, as either an output to the screen or into a logical file.  The number of spaces given by the &lt;numeric&gt; argument are printed, starting at the first available position.  For screen files, the value of the argument is in the range of 0 to 255 and for disk files, up to 254.  For printer files, an automatic carriage-return and line-feed will be performed by the printer if a space is printed in the last character position of a line.  No spaces are printed on the following line.

**EXAMPLE of the SPC Function:**
```BASIC
10 PRINT "FIRST "; "SECOND";
20 PRINT SPC(6) "THIRD" SPC(20) "FOURTH"
RUN
FIRST SECOND      THIRD                    FOURTH
```

### SPRITE

**TYPE: Statement**  
**FORMAT: SPRITE &lt;sprite idx&gt;,&lt;priority&gt;\[,&lt;palette offset&gt;\[,&lt;flip&gt;\[,&lt;x-width&gt;\[,&lt;y-width&gt;\[,&lt;color depth&gt;\]\]\]\]\]**

**Action:** This statement configures a sprite's geometry, palette, and visibility.

The first two arguments are required, but the remainder are optional.

* &lt;sprite idx&gt; is a value between 0-127 inclusive.
* &lt;priority&gt;, also known as z-depth changes the visibility of the sprite and above which layer it is rendered.  Range is 0-3 inclusive.  0 = off, 1 = below layer 0, 2 = in between layers 0 and 1, 3 = above layer 1
* &lt;palette offset&gt; is the palette offset for the sprite. Range is 0-15 inclusive. This value is multiplied by 16 to determine the starting palette index.
* &lt;flip&gt; controls the X and Y flipping of the sprite. Range is 0-3 inclusive. 0 = unflipped, 1 = X is flipped, 2 = Y is flipped, 3 = both X and Y are flipped.
* &lt;x-width&gt; and &lt;y-width&gt; represent the dimensions of the sprite. Range is 0-3 inclusive. 0 = 8px, 1 = 16px, 2 = 32px, 3 = 64px.
* &lt;color depth&gt; selects either 4 or 8-bit color depth for the sprite. 0 = 4-bit, 1 = 8-bit.  This attribute can also be set by the [`SPRMEM`](#sprmem) command.

Note: If VERA's sprite layer is disabled when the `SPRITE` command is called, the sprite layer will be enabled, regardless of the arguments to `SPRITE`.

**EXAMPLE of the SPRITE Statement:**

```BASIC
10 BVLOAD "MYSPRITE.BIN",8,1,$3000
20 SPRMEM 1,1,$3000,1
30 SPRITE 1,3,0,0,3,3
40 MOVSPR 1,320,200
```

### SPRMEM

**TYPE: Statement**  
**FORMAT: SPRMEM &lt;sprite idx&gt;,&lt;VRAM bank&gt;,&lt;VRAM address&gt;\[,&lt;color depth&gt;\]**

**Action:** This command configures the address of where the sprite's pixel data is to be found. It also can change or set the color depth of the sprite.

The first three arguments are required, but the last one is optional.

* &lt;sprite idx&gt; is a value between 0-127 inclusive.
* &lt;VRAM bank&gt; is a value, `0` or `1`, which represents which of the two 64k regions of VRAM to select.
* &lt;VRAM address&gt; is a 16-bit value, \$0000-\$FFFF, is the address within the VRAM bank to point the sprite to. The lowest 5 bits are ignored.
* &lt;color depth&gt; selects either 4 or 8-bit color depth for the sprite. 0 = 4-bit, 1 = 8-bit.  This attribute can also be set by the `SPRITE` command.

**EXAMPLE of the SPRITE Statement:**

```BASIC
10 BVLOAD "MYSPRITE.BIN",8,1,$3000
20 SPRMEM 1,1,$3000,1
30 SPRITE 1,3,0,0,3,3
40 MOVSPR 1,320,200
```

### SQR

**TYPE: Floating-Point Function**  
**FORMAT: SQR(&lt;numeric&gt;)**

**Action:** `SQR` gives you the value of the square root of the &lt;numeric&gt; argument.  The value of the argument must not be negative, or the BASIC error message `?ILLEGAL QUANTITY` will occur.

**EXAMPLE of the SQR Function:**
```BASIC
10 FOR X = 4 TO 10: PRINT X*5, SQR(J * 5): NEXT X
RUN
 20        4.47213595
 25        5
 30        5.47722557
 35        5.91607979
 40        6.32455532
 45        6.70820393
 50        7.07106781
```

### ST

**TYPE Integer Function**  
**FORMAT: ST**

**Action:** Returns a completion status for the last input/output operation which was performed on an open file.  The `ST`atus can be read from any peripheral device.  The `ST` (or `STATUS`) keyword is a system-defined variable name into which the `KERNAL` puts the status of I/O operations.  A table of status code values for printer, disk, and RS-232 file operations are shown below:

| **ST Bit Position** | **ST Numeric Value** | **Serial Bus R/W** | **RS-232** |
|:-------------------:|:--------------------:|:-------------------|:-----------|
| 0 | 1 | Indicates data direction if a timeout occurred;<br> 0 = reading, 1 = writing. | Parity Error |
| 1 | 2 | Timeout error | Framing error |
| 2 | 4 | - | Receive buffer overrun |
| 3 | 8 | - | Receive buffer empty |
| 4 | 16 | [`VERIFY`](#verify) error. | CTS signal missing |
| 5 | 32 | - | - |
| 6 | 64 | EOF | RTS signal missing | 
| 7 | -128 | Device Not Present | BREAK Detected |

**EXAMPLE of the ST Function:**
```BASIC
10 OPEN 1,4: OPEN 2,8,4, "TEXT FILE,SEQ,W"
20 GOSUB 100 : REM CHECK STATUS
30 INPUT#2, A$, B, C
40 IF STATUS AND 64 THEN 80 : REM HANDLE END-OF-FILE
50 GOSUB 100 : REM CHECK STATUS
60 PRINT#1, A$, B, C
70 GOTO 20
80 CLOSE 1 : CLOSE 2
90 GOSUB 100 : END
100 IF ST > 0 THEN 9000 : REM HANDLE I/O ERROR
110 RETURN
```

### STEP

**TYPE: Statement**  
**FORMAT: [STEP &lt;expression&gt;]**

**Action:** The optional `STEP` keyword follows the &lt;end-value&gt; expression in a [`FOR`](#for-to-step) statement.  It defines an increment value for the loop counter variable.  Any value can be used as the `STEP` increment.  Of course, a `STEP` value of zero will loop forever.  If the `STEP` keyword is left out, the increment value will be + 1.  When the [`NEXT`](#next) statement in a `FOR` loop is reached, the `STEP` increment happens.  Then the counter is tested against the end-value to see if the loop is finished.  (See the [`FOR`](#for-to-step) statement for more information.)

> **NOTE:** The `STEP` value cannot be changed once it's in the loop.

**EXAMPLES of the STEP Statement:**
```BASIC
10 FOR AA = 2 TO 20 STEP 2 : REM LOOP REPEATS 10 TIMES
20 FOR K2 = 0 TO -20 STEP -2 : REM LOOP REPEATS 11 TIMES
```

### STOP

**TYPE: Statement:**  
**FORMAT: STOP**

**Action:** The `STOP` statement is used to halt execution of the current program and return to direct mode.  Typing the <mark>**RUN/STOP**</mark> key on the keyboard has the same effect as a `STOP` statement.  The BASIC error message `BREAK IN XX` is displayed on the screen, followed by `READY`.  The "XX" is the line number where the `STOP` occurs.  Any open files remain open and all variables are preserved and can be examined.  The program can be restarted by using the [`CONT`](#cont) or [`GOTO`](#goto) statements.

**EXAMPLES of the STOP Statement:**
```BASIC
10 INPUT#5, AA, BB, CC
20 IF AA = BB AND BB = CC THEN STOP
30 STOP
```
If AA is -1 and BB is equal to CC, the result will be `BREAK IN 20`, otherwise the result will be `BREAK IN 30`.

### STR$

**TYPE: String Function**  
**FORMAT: STR$(&lt;numeric&lt;)**

**Action:** `STR$` gives you the string representation of the numeric value of the argument.  When the `STR$` value is converted to each variable represented in the &lt;numeric&gt; argument, any number shown is followed by a space, and if it's positive, it is also preceded by a space.

**EXAMPLE of the STR$ Function:**
```BASIC
10 ZA = 9.2E5: RZ$ = STR$(ZA)
20 PRINT ZA, RZ$
RUN
 920000     920000
```

### STRPTR

**TYPE: Function**  
**FORMAT: STRPTR(&lt;variable&gt;)**

**Action:** Returns the memory address of the first character of a string contained within a string variable. If the string variable has zero length, this function will likely still return a non-zero value pointing either to the close quotation mark in the literal assignment, or to somewhere undefined in string memory. Programs should check the [`LEN`](#len)gth of string variables before using the pointer returned from `STRPTR`.

**EXAMPLE of the STRPTR function:**

```BASIC
10 A$="MOO"
20 P=STRPTR(A$)
30 FOR I=0 TO LEN(A$)-1
40 PRINT CHR$(PEEK(P+I));
50 NEXT
60 A$=""
70 P=STRPTR(A$)
80 FOR I=0 TO LEN(A$)-1 : REM THIS LOOP WILL STILL ALWAYS HAPPEN ONCE
90 PRINT CHR$(PEEK(P+I));
100 NEXT
RUN
MOO"
READY.
```

In this case, the pointer returned on line 70 pointed to the first character after the open quote on line 60. Since it was an empty string, the pointer ended up pointing to the close quote. To avoid this scenario, we should have checked the `LEN(A$)` before line 80 and skipped over the loop.

### SYS

**TYPE: Command**  
**FORMAT: SYS &lt;address&gt;**

**Action:** The SYS command executes a machine language subroutine located at &lt;address&gt;.
Execution continues until an RTS is executed, and control returns to the BASIC program.

In order to communicate with the routine, you can pre-load the CPU registers by using [`POKE`](#poke) to write to the following
memory locations:

* `$030C`: Accumulator
* `$030D`: X Register
* `$030E`: Y Register
* `$030F`: Status Register/Flags

When the routine is over, the CPU registers will be loaded back in to these locations. So you can read the results of a machine language routine by [`PEEK`](#peek)ing these locations.

**EXAMPLE of the SYS statement:**

Push a &lt;CR&gt; into the keyboard buffer.

```BASIC
POKE $30C,13
SYS $FEC3
```

Run the Machine Language Monitor (Supermon)

```BASIC
SYS  $FECC
```

### TAB

**TYPE: Special Function**  
**FORMAT: TAB(&lt;numeric&gt;)**

**Action:** The `TAB` function moves the cursor to a relative [SPC](#spc) move position on the screen given by the &lt;numeric&gt; argument, starting with the left-most position of the current line.  The value of the argument can range from 0 to 255.  The `TAB` function should only be used with the `PRINT` statement, since it has no effect if used with the [`PRINT#`](#print-1) to a logical file.

**EXAMPLE of the TAB Function:**
```BASIC
10 PRINT "NAME" TAB(25) "AMOUNT": PRINT
20 INPUT#1, NAME$, AMT$
30 PRINT NAME$ TAB(25) AMT$
RUN
NAME                    AMOUNT
ARTHUR DENT             42.00
```

### TAN

**TYPE: Floating-Point Function**  
**FORMAT: TAN(&lt;number&gt;)**

**Action:** Returns the tangent of the value of the &lt;numeric&gt; expression in radians.  If the `TAN` function overflows, the BASIC error message `?DIVISION BY ZERO` is displayed.

**EXAMPLE of the TAN Function:**
```BASIC
10 JP = .8675309 : JJ = TAN(JP) : PRINT JJ
RUN
 1.179404
```

### TATTR

**TYPE: Function**  
**FORMAT: TATTR(&lt;x coordinate&gt;,&lt;y coordinate&gt;)**

**Action:** The `TATTR`function retrieves the text/tile attribute at the given x/y coordinate. It works for tiles or text on Layer 1.

In the default text modes, this can be used to retrieve the color attribute (foreground/background) of a specific coordinate without needing to calculate the VRAM address for [`VPEEK`](#vpeek).

**EXAMPLE of the TATTR Function:**

```BASIC
10 REM COPY BUTTERFLY LOGO WITH COLORS TO CENTER OF 80X60 SCREEN
20 XO = 37 : YO = 27
30 FOR X = 0 TO 6
40 FOR Y = 0 TO 6
50 TD = TDATA(X, Y)
60 TA = TATTR(X, Y)
70 TILE XO+X, YO+Y, TD, TA
80 NEXT:NEXT
```

### TDATA

**TYPE: Function**  
**FORMAT: TDATA(&lt;x coordinate&gt;,&lt;y coordinate&gt;)**

**Action:** The `TDATA` function retrieves the text/tile at the given x/y coordinate. It works for tiles or text on Layer 1.

In the default text modes, this can be used to retrieve the character a specific coordinate without needing to calculate the VRAM address for [`VPEEK`](#vpeek).

**EXAMPLE of the TATTR Function:**

```BASIC
10 REM COPY BUTTERFLY LOGO TO CENTER OF 80X60 SCREEN
20 XO = 37 : YO = 27
30 FOR X = 0 TO 6
40 FOR Y = 0 TO 6
50 TD = TDATA(X, Y)
60 TILE XO+X, YO+Y, TD
70 NEXT:NEXT
```

### TILE

**TYPE: Statement**  
**FORMAT: TILE &lt;x&gt;,&lt;y&gt;,&lt;tile/screen code&gt;\[,&lt;attribute&gt;\]**

**Action:** The `TILE` statement sets the tile or text character at the given x/y tile/character coordinate to the given screen code or tile index, optionally resetting the attribute byte. It works for tiles or text on Layer 1.

In the default text mode, this can be used to quickly change a character on the screen and optionally its foreground/background color without needing to calculate the VRAM address for [`VPOKE`](#vpoke).

However, it can also be used if VERA Layer 1's map base value is changed or the map size is changed.

**EXAMPLE of the TILE Statement:**

```BASIC
10 REM VERY SLOWLY CLEAR THE SCREEN IN STYLE
20 FOR Y=59 TO 0 STEP -1
30 FOR X=79 TO 0 STEP -1
40 FOR I=255 TO 32 STEP -1
50 TILE X,Y,I
60 NEXT:NEXT:NEXT
```

### TIME

**TYPE: Numeric Function**  
**FORMAT: TI**

**Action:** The `TI` function reads the interval `TI`mer.  This type of "clock" is called a "jiffy clock".  The "jiffy clock" value is set at zero (initialized) when you power-up the system.  Each "tick" of the clock is 1/60th of a second.

**EXAMPLE of the TI Function:**
```BASIC
10 PRINT TI/60 "SECONDS SINCE POWER UP."
```

### TIME$

**TYPE: String Function**  
**FORMAT: TI$**

**Action:** The `TI$` timer looks and works like a real clock as long as your system is powered on.  The hardware system clock is read and used to update the value of `TI$`, which will give you a time string of six characters in hours, minutes, and seconds.  The `TI$` timer can also be assigned an arbitrary starting point similar to the way you set your wrist watch.  If you assign a value to `TI$`, it will persist across system restarts.

**EXAMPLE of the TI$ Function:**
```BASIC
10 HH$ = MID$(TI$,1,2)
20 MM$ = MID$(TI$,3,2)
30 SS$ = MID$(TI$,5,2)
40 PRINT "THE TIME IS ";HH$;":";MM$;":";SS$
```

### USR

**TYPE: Floating-Point Function**  
**FORMAT: USR(&lt;numeric&gt;)**

**Action:** The `USR` function jumps to a user callable machine language subroutine which has its starting address pointed to by the contents of memory locations 785 ($0311) and 786 ($0312).  The starting address is established before calling the `USR` function by using [POKE](#poke) statements to set up locations 785 and 786.  Unless [POKE](#poke) statements are used, locations 785 and 786 an `? ILLEGAL QUANTITY` error message.

The value of the &lt;numeric&gt; argument is stored in the floating-point accumulator starting at location 97 ($61), for access by assembler code, and the result of the `USR` function is the value which ends up there when the subroutine returns to BASIC.

**EXAMPLES of the USR Function:**
```BASIC
10 A = T * SIN(ZD)
20 C = USR(A / 2)
30 D = USR(A / 3)
```

### VAL

**TYPE: Numeric Function**  
**FORMAT: VAL(&lt;string&gt;)**

**Action:** Returns a numeric value representing the data in the &lt;string&gt; argument.  If the first non-blank character of the string is not a plus sign `(+)`, minus sign `(-)`, or a digit, the value returned is zero.  String conversion is finished when the end of a string or any non-digit character is found (except decimal point or exponential e).

**EXAMPLE of the VAL Function:**
```BASIC
100 INPUT#1, NAM$, ZIP$
110 IF VAL(ZIP$) > 98100 OR VAL(ZIP$) < 98109 THEN PRINT NAM$ TAB(10) "SEATTLE, WA"
```

### VERIFY

**TYPE: Command**  
**FORMAT: VERIFY ["&lt;file name&gt;"][,&lt;device&gt;]**

**Action:** The `VERIFY` command is used, in direct or program mode, to compare the contents of a BASIC program file on disk with the program currently in memory.  `VERIFY` is normally used right after a [SAVE](#save), to make sure that the program was stored correctly on disk.

If the &lt;device&gt; number is left out, the program is assumed to be on the first disk device, which is device #8.  If any differences in program text are found, the BASIC error message `?VERIFY ERROR` is displayed.

A program name can be given either in quotes `(" ")` or as a string variable.

**EXAMPLES of the VERIFY Command:**

- VERIFY (Checks the first file on the first disk device (#8))
```BASIC
100 SAVE "MYPROG", 8
105 VERIFY "MYPROG", 8
```

### VPEEK

**TYPE: Integer Function**  
**FORMAT: VPEEK (&lt;bank&gt;, &lt;address&gt;)**

**Action:** Return a byte from the video address space. The video address space has 17 bit addresses, which is exposed as 2 banks of 65536 addresses each.

In addition, `VPEEK` can reach add-on VERA cards with higher bank numbers.

BANK 2-3 is for IO3 (VERA at \$9F60-\$9F7F)  
BANK 4-5 is for IO4 (VERA at \$9F80-\$9F9F)  

**EXAMPLE of the VPEEK Function:**

```BASIC
PRINT VPEEK(1,$B000) : REM SCREEN CODE OF CHARACTER AT 0/0 ON SCREEN
```

### VPOKE

**TYPE: Command**  
**FORMAT: VPOKE &lt;bank&gt;, &lt;address&gt;, &lt;value&gt;**

**Action:** Set a byte in the video address space. The video address space has 17 bit addresses, which is exposed as 2 banks of 65536 addresses each.

In addition, `VPOKE` can reach add-on VERA cards with higher bank numbers.

BANK 2-3 is for IO3 (VERA at \$9F60-\$9F7F)  
BANK 4-5 is for IO4 (VERA at \$9F80-\$9F9F)  

**EXAMPLE of the VPOKE Statement:**

```BASIC
VPOKE 1,$B000+1,1 * 16 + 2 : REM SETS THE COLORS OF THE CHARACTER
                             REM AT 0/0 TO RED ON WHITE
```

### VLOAD

**TYPE: Statement**  
**FORMAT: VLOAD &lt;filename&gt;, &lt;device&gt;, &lt;VERA_high_address&gt;, &lt;VERA_low_address&gt;**

**Action:** Loads a file directly into VERA RAM, skipping the two-byte header that is presumed to be in the file.

**EXAMPLES of the VLOAD Statement:**

```BASIC
VLOAD "MYFILE.PRG", 8, 0, $4000  :REM LOADS MYFILE.PRG FROM DEVICE 8 TO VRAM $4000
                                  REM WHILE SKIPPING THE FIRST TWO BYTES OF THE FILE.
```

To load a raw binary file without skipping the first two bytes, use [`BVLOAD`](#bvload)

### WAIT

**TYPE: Statement**  
**FORMAT: WAIT &lt;location&gt;, &lt;mask-1&gt; [,&lt;mask-2&gt;]**

**Action:** The `WAIT` statement causes program execution to be suspended until a given memory address recognizes a specified bit pattern.  In other words, `WAIT` can be used to halt the program until some external event has occurred.  This is done by monitoring the status of bits in the input/output registers.  The data items used with `WAIT` can be any numeric expressions, but they will be converted to integer values.

For most programmers, this statement should never be used.  It causes the program to halt until a specific memory location's bits change in a specific way.  This is used for certain I/O operations and almost nothing else.

The `WAIT` statement takes the value in the memory location and performs a logical [AND](#and) operation with the value in &lt;mask-1&gt;.  If there is a &lt;mask-2&gt; in the statement, the result of the first operation is exclusive-ORed with &lt;mask-2&gt;  In other words, &lt;mask-1&gt; "filters out" any bits that you don't want to test.  Where the bit is 0 in &lt;mask-1&gt;, the corresponding bit in the result will always be 0.  The &lt;mask-2&gt; value flips any bits, so that you can test of an off condition as well as an on condition.  Any bits being tested for a 0 should have a 1 in the corresponding position in &lt;mask-2&gt;

If corresponding bits of the &lt;mask-1&gt; and &lt;mask-2&gt; operands differ, the exclusive-OR operation gives a bit result of 1.  If corresponding bits get the same result, the bit is 0.  It is possible to enter an infinite pause with the `WAIT` statement, in which case the <mark>**RUN/STOP**</mark> and <mark>**RESTORE**</mark> keys can be used to recover.  Hold down the <mark>**RUN/STOP**</mark> key and then press <mark>**RESTORE**</mark>.

**EXAMPLES of WAIT Statements:**
```BASIC
10 WAIT 53273, 6, 6
20 WAIT 32868, 144, 16
```

## Other New Features

### Hexadecimal and Binary Literals

The numeric constants parser supports both hex (`$`) and binary (`%`) literals, like this:

```BASIC
PRINT $EA31 + %1010
```

The size of hex and binary values is only restricted by the range that can be represented by BASIC's internal floating point representation.

### LOAD into VRAM

In BASIC, the contents of files can be directly loaded into VRAM with the [`LOAD`](#load) statement. When a secondary address greater than one is used, the KERNAL will now load the file into the VERA's VRAM address space. The first two bytes of the file are used as lower 16 bits of the address. The upper 4 bits are `(SA-2) & 0x0ff` where `SA` is the secondary address.

Examples:

```BASIC
10 REM LOAD VERA SETTINGS
20 LOAD"VERA.BIN",1,17 : REM SET ADDRESS TO $FXXXX
30 REM LOAD TILES
40 LOAD"TILES.BIN",1,3 : REM SET ADDRESS TO $1XXXX
50 REM LOAD MAP
60 LOAD"MAP.BIN",1,2 : REM SET ADDRESS TO $0XXXX
```

### Default Device Numbers

In BASIC, the [LOAD], [`SAVE`](#save) and [`OPEN`](#open) statements default to the last-used IEEE device (device numbers 8 and above), or 8.

## Internal Representation

Like on the C64, BASIC keywords are tokenized.

* The C64 BASIC V2 keywords occupy the range of \$80 ([`END`](#end)) to \$CB (`GO`).
* BASIC V3.5 also used \$CE (`RGR`) to \$FD (`WHILE`).
* BASIC V7 introduced the \$CE escape code for function tokens \$CE-\$02 (`POT`) to \$CE-\$0A (`POINTER`), and the \$FE escape code for statement tokens \$FE-\$02 ([`BANK`](#bank)) to \$FE-\$38 (`SLOW`).
* The unreleased BASIC V10 extended the escaped tokens up to \$CE-\$0D (`RPALETTE`) and \$FE-\$45 (`EDIT`).

The X16 BASIC aims to be as compatible as possible with this encoding. Keywords added to X16 BASIC that also exist in other versions of BASIC match the token, and new keywords are encoded in the ranges \$CE-\$80+ and \$FE-\$80+.

## Auto-Boot

When BASIC starts, it automatically executes the [`BOOT`](#boot) command, which tries to load a PRG file named `AUTOBOOT.X16` from device 8 and, if successful, runs it. Here are some use cases for this:

* An SD card with a game can auto-boot this way.
* An SD card with a collection of applications can show a menu that allows selecting an application to load.
* The user's "work" SD card can contain a small auto-boot BASIC program that sets the keyboard layout and changes the screen colors, for example.

<!-- For PDF formatting -->
<div class="page-break"></div>

# Chapter 5: KERNAL

<!--
********************************************************************************
NOTICE: This file uses two trailing spaces on some lines to indicate line
breaks for GitHub's Markdown flavor. Do not remove!
********************************************************************************
-->

The Commander X16 contains a version of KERNAL as its operating system in ROM. It contains

* "Channel I/O" API for abstracting devices
* a variable size screen editor
* a color bitmap graphics API with proportional fonts
* simple memory management
* timekeeping
* drivers
  * PS/2 keyboard and mouse
  * NES/SNES controller
  * Commodore Serial Bus ("IEC")
  * I2C bus

## KERNAL Version

The KERNAL version can be read from location \$FF80 in ROM. A value of \$FF indicates a custom build. All other values encode the build number. Positive numbers are release versions (\$02 = release version 2), two's complement negative numbers are prerelease versions (\$FE = $100 - 2 = prerelease version 2).

## Compatibility Considerations

For applications to remain compatible between different versions of the ROM, they can rely upon:

* the KERNAL API calls at \$FF81-\$FFF3
* the KERNAL vectors at \$0314-\$0333

The following features must not be relied upon:

* the zero page and $0200+ memory layout
* direct function offsets in the ROM

## Commodore 64 API Compatibility

The KERNAL [fully supports](#kernal-api-functions) the C64 KERNAL API.

These routines have been stable ever since the C64 came out and are extensively documented
in various resources dedicated to the C64. Currently, they are not documented _here_ so if you
need to look them up, here is a very thorough [reference of these standard kernal routines](https://www.pagetable.com/c64ref/kernal/) (hosted on M. Steil's website).
It integrates a dozen or so different sources for documentation about these routines.

## Commodore 128 API Compatibility

In addition, the X16 [supports a subset](#kernal-api-functions) of the C128 API.

The following C128 APIs have equivalent functionality on the X16 but are not compatible:

| Address | C128 Name | X16 Name             |
|---------|-----------|----------------------|
| $FF5F   | `SWAPPER` | [`screen_mode`](#function-name-screen_mode) |
| $FF62   | `DLCHR`   | [`screen_set_charset`](#function-name-screen_set_charset) |
| $FF74   | `FETCH`   | [`fetch`](#function-name-fetch) |
| $FF77   | `STASH`   | [`stash`](#function-name-stash) |
<!---
*** undocumented - we might remove it
| $FF7A   | `CMPARE`  | `cmpare`             |
--->

## New API for the Commander X16

There are many new APIs.

Some new APIs use the "16 bit" ABI, which uses virtual 16 bit registers r0 through r15, which are located in zero page locations \$02 through \$21: r0 = r0L = \$02, r0H = \$03, r1 = r1L = \$04 etc.

The 16 bit ABI generally follows the following conventions:

* arguments
  * word-sized arguments: passed in r0-r5
  * byte-sized arguments: if three or less, passed in .A, .X, .Y; otherwise in 16 bit registers
  * boolean arguments: c, n
* return values
  * basic rules as above
  * function takes no arguments: r0-r5, else indirect through passed-in pointer
  * arguments in r0-r5 can be "inout", i.e. they can be updated
* saved/scratch registers
  * r0-r5: arguments (saved)
  * r6-r10: saved
  * r11-r15: scratch
  * .A, .X, .Y, c, n: scratch (unless used otherwise)

## KERNAL API functions

| Label | Address | Class | Description | Inputs | Affects | Origin |
|-|-|-|-|-|-|-|
| [`ACPTR`](#function-name-acptr) | `$FFA5` | [CPB](#commodore-peripheral-bus "Commodore Peripheral Bus") | Read byte from peripheral bus | | A X | C64 |
| [`BASIN`](#function-name-basin) | `$FFCF` | [ChIO](#channel-io "Channel I/O") | Get character from file or editor line | | A X | C64 |
| [`BSAVE`](#function-name-bsave) | `$FEBA` | ChIO | Like `SAVE` but omits the 2-byte header | A X Y | A X Y | X16 |
| [`BSOUT`](#function-name-bsout) | `$FFD2` | ChIO | Write byte in A to default output. | A | P | C64 |
| [`CINT`](#function-name-cint) | `$FF81` | Misc | Reset screen/keyboard to default state. | none | A X Y P | C64 |
| `CIOUT` | `$FFA8` | CPB | Send byte to peripheral bus | A | A X | C64 |  
| `CLALL` | `$FFE7` | ChIO | Close all channels | | A X | C64 |
| [`CLOSE`](#function-name-close) | `$FFC3` | ChIO | Close a channel | A | A X Y P | C64 |
| [`CHKIN`](#function-name-chkin) | `$FFC6` | ChIO | Set channel for character input | X | A X | C64 |
| `CHKOUT` | `$FFC9` | ChIO | Set channel for character output | X | A X | C64 |
| [`clock_get_date_time`](#function-name-clock_get_date_time) | `$FF50` | Time | Get the date and time | none | r0 r1 r2 r3 A X Y P | X16
| [`clock_set_date_time`](#function-name-clock_set_date_time) | `$FF4D` | Time | Set the date and time | r0 r1 r2 r3 | A X Y P | X16
| [`CHRIN`](#function-name-basin) | `$FFCF` | ChIO | Alias for `BASIN` | | A X | C64 |
| [`CHROUT`](#function-name-bsout) | `$FFD2` | ChIO | Alias for `BSOUT` | A | P | C64 |
| `CLOSE_ALL` | `$FF4A` | ChIO | Close all files on a device  | | | C128 |
| `CLRCHN` | `$FFCC` | ChIO | Restore character I/O to screen/keyboard | | A X | C64 |
| [`console_init`](#function-name-console_init) | `$FEDB` | Video | Initialize console mode | none | r0 A P | X16
| [`console_get_char`](#function-name-console_get_char) | `$FEE1` | Video | Get character from console | A | r0 r1 r2 r3 r4 r5 r6 r12 r13 r14 r15 A X Y P | X16
| [`console_put_char`](#function-name-console_put_char) | `$FEDE` | Video | Print character to console | A C | r0 r1 r2 r3 r4 r5 r6 r12 r13 r14 r15 A X Y P | X16
| [`console_put_image`](#function-name-console_put_image) | `$FED8` | Video | Draw image as if it was a character | r0 r1 r2 | r0 r1 r2 r3 r4 r5 r14 r15 A X Y P | X16
| [`console_set_paging_message`](#function-name-console_set_paging_message) | `$FED5` | Video | Set paging message or disable paging | r0 | A P | X16
| [`enter_basic`](#function-name-enter_basic) | `$FF47` | Misc | Enter BASIC | C | A X Y P | X16
| [`entropy_get`](#function-name-entropy_get) | `$FECF` | Misc | get 24 random bits | none | A X Y P | X16
| [`extapi`](#function-name-extapi) | `$FEAB` | Misc | Extended API | A X Y P | A X Y P | X16
| [`extapi16`](#function-name-extapi16) | `$FEA8` | Misc | Extended 65C816 API | A X Y P | A X Y P | X16
| [`fetch`](#function-name-fetch) | `$FF74` | Mem | Read a byte from any RAM or ROM bank | (A) X Y | A X P | X16
| [`FB_cursor_next_line`](#function-name-fb_cursor_next_line) &#8224; | `$FF02` | Video | Move direct-access cursor to next line | r0&#8224; | A P | X16
| [`FB_cursor_position`](#function-name-fb_cursor_position) | `$FEFF` | Video | Position the direct-access cursor | r0 r1 | A P | X16
| [`FB_fill_pixels`](#function-name-fb_fill_pixels) | `$FF17` | Video | Fill pixels with constant color, update cursor | r0 r1 A | A X Y P | X16
| [`FB_filter_pixels`](#function-name-fb_filter_pixels) | `$FF1A` | Video | Apply transform to pixels, update cursor | r0 r1 | r14H r15 A X Y P | X16
| [`FB_get_info`](#function-name-fb_get_info) | `$FEF9` | Video | Get screen size and color depth | none | r0 r1 A P | X16
| [`FB_get_pixel`](#function-name-fb_get_pixel) | `$FF05` | Video | Read one pixel, update cursor | none | A | X16
| [`FB_get_pixels`](#function-name-fb_get_pixels) | `$FF08` | Video | Copy pixels into RAM, update cursor | r0 r1 | (r0) A X Y P | X16
| [`FB_init`](#function-name-fb_init) | `$FEF6` | Video | Enable graphics mode | none | A P | X16
| [`FB_move_pixels`](#function-name-fb_move_pixels) | `$FF1D` | Video | Copy horizontally consecutive pixels to a different position | r0 r1 r2 r3 r4 | A X Y P | X16
| [`FB_set_8_pixels`](#function-name-fb_set_8_pixels) | `$FF11` | Video | Set 8 pixels from bit mask (transparent), update cursor | A X | A P | X16
| [`FB_set_8_pixels_opaque`](#function-name-fb_set_8_pixels_opaque) | `$FF14` | Video | Set 8 pixels from bit mask (opaque), update cursor | r0L A X Y| r0L A P | X16
| [`FB_set_palette`](#function-name-fb_set_palette) | `$FEFC` | Video | Set (parts of) the palette | A X r0 | A X Y P | X16
| [`FB_set_pixel`](#function-name-fb_set_pixel) | `$FF0B` | Video | Set one pixel, update cursor | A | none | X16
| [`FB_set_pixels`](#function-name-fb_set_pixels) | `$FF0E` | Video | Copy pixels from RAM, update cursor | r0 r1 | A X P | X16
| [`GETIN`](#function-name-getin) | `$FFE4` | ChIO | Get character from file or keyboard | | A X | C64 |
| [`GRAPH_clear`](#function-name-graph_clear) | `$FF23` | Video | Clear screen | none | r0 r1 r2 r3 A X Y P | X16
| [`GRAPH_draw_image`](#function-name-graph_draw_image) | `$FF38` | Video | Draw a rectangular image | r0 r1 r2 r3 r4 | A P | X16
| [`GRAPH_draw_line`](#function-name-graph_draw_line) | `$FF2C` | Video | Draw a line | r0 r1 r2 r3 | r0 r1 r2 r3 r7 r8 r9 r10 r12 r13 A X Y P | X16
| [`GRAPH_draw_oval`](#function-name-graph_draw_oval) | `$FF35` | Video | Draw an oval or circle (optionally filled) | r0 r1 r2 r3 r4 C | A X Y P | X16
| [`GRAPH_draw_rect`](#function-name-graph_draw_rect) &#8224; | `$FF2F` | Video | Draw a rectangle (optionally filled) | r0 r1 r2 r3 r4 C | A P | X16
| [`GRAPH_get_char_size`](#function-name-graph_get_char_size) | `$FF3E` | Video | Get size and baseline of a character | A X | A X Y P | X16
| [`GRAPH_init`](#function-name-graph_init) | `$FF20` | Video | Initialize graphics | r0 | r0 r1 r2 r3 A X Y P | X16
| [`GRAPH_move_rect`](#function-name-graph_move_rect) &#8224; | `$FF32` | Video | Move pixels | r0 r1 r2 r3 r4 r5 | r1 r3 r5 A X Y P | X16
| [`GRAPH_put_char`](#function-name-graph_put_char) &#8224;| `$FF41` | Video | Print a character | r0 r1 A | r0 r1 A X Y P | X16
| [`GRAPH_set_colors`](#function-name-graph_set_colors) | `$FF29` | Video | Set stroke, fill and background colors | A X Y | none | X16
| [`GRAPH_set_font`](#function-name-graph_set_font) | `$FF3B` | Video | Set the current font | r0 | r0 A Y P | X16
| [`GRAPH_set_window`](#function-name-graph_set_window) &#8224;| `$FF26` | Video | Set clipping region | r0 r1 r2 r3 | A P | X16
| [`i2c_batch_read`](#function-name-i2c_batch_read) | `$FEB4` | I2C | Read multiple bytes from an I2C device | X r0 r1 C | A Y C | X16
| [`i2c_batch_write`](#function-name-i2c_batch_write) | `$FEB7` | I2C | Write multiple bytes to an I2C device | X r0 r1 C | A Y r2 C | X16
| [`i2c_read_byte`](#function-name-i2c_read_byte) | `$FEC6` | I2C | Read a byte from an I2C device | A X Y | A C | X16
| [`i2c_write_byte`](#function-name-i2c_write_byte) | `$FEC9` | I2C | Write a byte to an I2C device | A X Y | A C | X16
| `IOBASE` | `$FFF3` | Misc | Return start of I/O area | | X Y | C64 |
| [`IOINIT`](#function-name-ioinit) | `$FF84` | Misc | Reset serial state and IRQ sources | | A X Y P | C64 |
| [`JSRFAR`](#function-name-jsrfar) | `$FF6E` | Misc | Execute a routine on another RAM or ROM bank | PC+3 PC+5 | none | X16
| [`joystick_get`](#function-name-joystick_get) | `$FF56` | Joy | Get one of the saved controller states | A | A X Y P | X16
| [`joystick_scan`](#function-name-joystick_scan) | `$FF53` | Joy | Poll controller states and save them | none | A X Y P | X16
| [`kbd_scan`](#function-name-kbd_scan) | `$FF9F` | Kbd | Process a keystroke and place it in the buffer | none | A X Y P | C64 |
| [`kbdbuf_get_modifiers`](#function-name-kbdbuf_get_modifiers) | `$FEC0` | Kbd | Get currently pressed modifiers | A | A X P | X16
| [`kbdbuf_peek`](#function-name-kbdbuf_peek) | `$FEBD` | Kbd | Get next char and keyboard queue length | A X | A X P | X16
| [`kbdbuf_put`](#function-name-kbdbuf_put) | `$FEC3` | Kbd | Append a character to the keyboard queue | A | X | X16
| [`keymap`](#function-name-keymap) | `$FED2` | Kbd | Set or get the current keyboard layout Call address | X Y C | A X Y C | X16
| `LISTEN` | `$FFB1` | CPB | Send LISTEN command | A | A X | C64 |
| `LKUPLA` | `$FF59` | ChIO | Search tables for given LA | | | C128 |
| `LKUPSA` | `$FF5C` | ChIO | Search tables for given SA | | | C128 |
| [`LOAD`](#function-name-load) | `$FFD5` | ChIO | Load a file into main memory or VRAM | A X Y | A X Y | C64 |
| [`MACPTR`](#function-name-macptr) | `$FF44` | CPB | Read multiple bytes from the peripheral bus | A X Y C | A X Y P | X16
| [`MCIOUT`](#function-name-mciout) | `$FEB1` | CPB | Write multiple bytes to the peripheral bus | A X Y C | A X Y P | X16
| `MEMBOT` | `$FF9C` | Mem | Get address of start of usable RAM | | | C64 |
| [`MEMTOP`](#function-name-memtop) | `$FF99` | Mem | Get/set number of banks and address of the end of usable RAM | | A X Y | C64 |
| [`memory_copy`](#function-name-memory_copy) | `$FEE7` | Mem | Copy a memory region to a different region | r0 r1 r2 | r2 A X Y P | X16
| [`memory_crc`](#function-name-memory_crc) | `$FEEA` | Mem | Calculate the CRC16 of a memory region | r0 r1 | r2 A X Y P | X16
| [`memory_decompress`](#function-name-memory_decompress) | `$FEED` | Mem | Decompress an LZSA2 block | r0 r1 | r1 A X Y P | X16
| [`memory_fill`](#function-name-memory_fill) | `$FEE4` | Mem | Fill a memory region with a byte value | A r0 r1 | r1 X Y P | X16
| [`monitor`](#function-name-monitor) | `$FECC` | Misc | Enter machine language monitor | none | A X Y P | X16
| [`mouse_config`](#function-name-mouse_config) | `$FF68` | Mouse | Configure mouse pointer | A X Y | A X Y P | X16
| [`mouse_get`](#function-name-mouse_get) | `$FF6B` | Mouse | Get saved mouse sate | X | A (X) P | X16
| [`mouse_scan`](#function-name-mouse_scan) | `$FF71` | Mouse | Poll mouse state and save it | none | A X Y P | X16
| [`OPEN`](#function-name-open) | `$FFC0` | ChIO | Open a channel/file.  | | A X Y | C64 |
| `PLOT` | `$FFF0` | Video | Read/write cursor position | A X Y | A X Y | C64 |
| `PRIMM` | `$FF7D` | Misc | Print string following the caller’s code | | | C128 |
| [`RDTIM`](#function-name-rdtim) | `$FFDE` | Time | Read system clock | | A X Y| C64 |
| `READST` | `$FFB7` | ChIO | Return status byte | | A | C64 |
| [`SAVE`](#function-name-save) | `$FFD8` | ChIO | Save a file from memory | A X Y | A X Y C | C64 |
| [`SCNKEY`](#function-name-kbd_scan) | `$FF9F` | Kbd | Alias for `kbd_scan` | none | A X Y P | C64 |
| [`SCREEN`](#function-name-screen) | `$FFED` | Video | Get the text resolution of the screen | | X Y | C64 |
| [`screen_mode`](#function-name-screen_mode) | `$FF5F` | Video | Get/set screen mode | A C | A X Y P | X16
| [`screen_set_charset`](#function-name-screen_set_charset) | `$FF62` | Video | Activate 8x8 text mode charset | A X Y | A X Y P | X16
| `SECOND` | `$FF93` | CPB | Send LISTEN secondary address | A | A | C64 |
| [`SETLFS`](#function-name-setlfs)| `$FFBA` | ChIO | Set file parameters (LA, FA, and SA). | A X Y | | C64 |
| `SETMSG` | `$FF90` | ChIO | Set verbosity | A | | C64 |
| [`SETNAM`](#function-name-setnam) | `$FFBD` | ChIO | Set file name. | A X Y | | C64 |
| `SETTIM` | `$FFDB` | Time | Write system clock | A X Y | A X Y | C64 |
| `SETTMO` | `$FFA2` | CPB | Set timeout | | | C64 |
| [`sprite_set_image`](#function-name-sprite_set_image) &#8224; | `$FEF0` | Video | Set the image of a sprite | r0 r1 r2L A X Y C | A P | X16
| [`sprite_set_position`](#function-name-sprite_set_position) | `$FEF3` | Video | Set the position of a sprite | r0 r1 A | A X P | X16
| [`stash`](#function-name-stash) | `$FF77` | Mem | Write a byte to any RAM bank | stavec A X Y | (stavec) X P | X16
| `STOP` | `$FFE1` | Kbd | Test for STOP key  | | A X P | C64 |
| `TALK` | `$FFB4` | CPB | Send TALK command  | A | A | C64 |
| `TKSA` | `$FF96` | CPB | Send TALK secondary address | A | A | C64 |
| `UDTIM` | `$FFEA` | Time | Increment the jiffies clock | | A X | C64 |
| `UNLSN` | `$FFAE` | CPB | Send UNLISTEN command | | A | C64 |
| `UNTLK` | `$FFAB` | CPB | Send UNTALK command | | A | C64 |

&#128683; = Currently unimplemented  
&#8224; = Partially implemented  

Some notes:

* For device #8, the Commodore Peripheral Bus calls first talk to the "Computer DOS" built into the ROM to detect an SD card, before falling back to the Commodore Serial Bus.
* The `IOBASE` call returns $9F00, the location of the first VIA controller.
* The `SETTMO` call has been a no-op since the Commodore VIC-20, and has no function on the X16 either.
* The layout of the zero page ($0000-$00FF) and the KERNAL/BASIC variable space ($0200+) are generally **not** compatible with the C64.

### KERNAL Vectors

The KERNAL indirect vectors (\$0314-\$0333) are fully compatible with the C64:

\$0314-\$0315: `CINV` – IRQ Interrupt Routine  
\$0316-\$0317: `CBINV` – BRK Instruction Interrupt  
\$0318-\$0319: `NMINV` – Non-Maskable Interrupt  
\$031A-\$031B: `IOPEN` – Kernal OPEN Routine  
\$031C-\$031D: `ICLOSE` – Kernal CLOSE Routine  
\$031E-\$031F: `ICHKIN` – Kernal CHKIN Routine  
\$0320-\$0321: `ICKOUT` – Kernal CKOUT Routine  
\$0322-\$0323: `ICLRCH` – Kernal CLRCHN Routine  
\$0324-\$0325: `IBASIN` – Kernal CHRIN Routine  
\$0326-\$0327: `IBSOUT` – Kernal CHROUT Routine  
\$0328-\$0329: `ISTOP` – Kernal STOP Routine  
\$032A-\$032B: `IGETIN` – Kernal GETIN Routine  
\$032C-\$032D: `ICLALL` – Kernal CLALL Routine  
\$0330-\$0331: `ILOAD` – Kernal LOAD Routine  
\$0332-\$0333: `ISAVE` – Kernal SAVE Routine  

Additional KERNAL indirect vectors have been added as part of the KERNAL's 65C816 support

\$0334-\$0335: `IECOP` - COP Instruction Interrupt Routine (emulation mode)  
\$0336-\$0337: `IEABORT` - ABORT Routine (emulation mode)  
\$0338-\$0339: `INIRQ` - IRQ Interrupt Routine (native mode)  
\$033A-\$033B: `INBRK` - BRK Instruction Interrupt Routine (native mode)  
\$033C-\$033D: `INNMI` - Non-Maskable Interrupt Routine (native mode)  
\$033E-\$033F: `INCOP` - COP Instruction Interrupt Routine (native mode)  
\$0340-\$0341: `INABORT` - ABORT Routine (native mode)  

#### Handling NMI

If the NMI vector is replaced with a user function and that function does not call 
back to the replaced NMI routine, some cleanup will need to be done. Before the user
NMI function is called, the KERNAL pushes `a` and the rom bank onto the stack. These
values will need to be popped before returning from the NMI:

```
.proc my_awesome_nmi
        ...

	pla
	sta $01
	pla
	rti
.endproc
```

---

### Commodore Peripheral Bus

The X16 adds two new functions for dealing with the Commodore Peripheral Bus ("IEEE"):

\$FEB1: `MCIOUT` - write multiple bytes to peripheral bus
\$FF44: `MACPTR` - read multiple bytes from peripheral bus

---

#### Function Name: ACPTR

Purpose: Read a byte from the peripheral bus  
Call address: $FFA5  
Communication registers: .A  
Preparatory routines: `SETNAM`, `SETLFS`, `OPEN`, `CHKIN`  
Error returns: None  
Registers affected: .A .X .Y .P  

**Description:** This routine gets a byte of data off the peripheral bus. The data is returned in the accumulator.  Errors are returned in the status word which can be read via the `READST` API call.

---

#### Function Name: MACPTR

Purpose: Read multiple bytes from the peripheral bus  
Call address: $FF44  
Communication registers: .A .X .Y c  
Preparatory routines: `SETNAM`, `SETLFS`, `OPEN`, `CHKIN`  
Error returns: None  
Registers affected: .A .X .Y  

**Description:** The routine `MACPTR` is the multi-byte variant of the `ACPTR` KERNAL routine. Instead of returning a single byte in .A, it can read multiple bytes in one call and write them directly to memory.

The number of bytes to be read is passed in the .A register; a value of 0 indicates that it is up to the KERNAL to decide how many bytes to read - up to a maximum of 512 bytes (this corresponds to 1 sector on the SD card). A pointer to where the data is supposed to be written is passed in the .X (lo) and .Y (hi) registers. If carry flag is clear, the destination address will advance with each byte read. If the carry flag is set, the destination address will not advance as data is read. This is useful for reading data directly into VRAM, PCM FIFO, etc.

For reading into Hi RAM, you must set the desired bank prior to calling `MACPTR`. During the read, `MACPTR` will automatically wrap to the next bank as required, leaving the new bank active when finished.

Upon return, a set c flag indicates that the device or file does not support `MACPTR`, and the program needs to read the data byte-by-byte using the `ACPTR` call instead.

If `MACPTR` is supported, c is clear and .X (lo) and .Y (hi) contain the number of bytes read.
*It is possible that this is less than the number of bytes requested to be read! (But is always greater than 0)*

Like with `ACPTR`, the status of the operation can be retrieved using the `READST` KERNAL call.

---

#### Function Name: MCIOUT

Purpose: Write multiple bytes to the peripheral bus  
Call address: $FEB1  
Communication registers: .A .X .Y c  
Preparatory routines: `SETNAM`, `SETLFS`, `OPEN`, `CHKOUT`  
Error returns: None  
Registers affected: .A .X .Y  

**Description:** The routine `MCIOUT` is the multi-byte variant of the `CIOUT` KERNAL routine. Instead of writing a single byte, it can write multiple bytes from memory in one call.

The number of bytes to be written is passed in the .A register; a value of 0 indicates 256 bytes. A pointer to the data to be read from is passed in the .X (lo) and .Y (hi) registers. If carry flag is clear, the source address will advance with each byte read out. If the carry flag is set, the source address will not advance as data is read out. This is useful for saving data directly from VRAM.

For reading from Hi RAM, you must set the desired bank prior to calling `MCIOUT`. During the operation, `MCIOUT` will automatically wrap to the next bank as required, leaving the new bank active when finished.

Upon return, a set c flag indicates that the device or file does not support `MCIOUT`, and the program needs to write the data byte-by-byte using the `CIOUT` call instead.

If `MCIOUT` is supported, c is clear and .X (lo) and .Y (hi) contain the number of bytes written.
*It is possible that this is less than the number of bytes requested to be written! (But is always greater than 0)*

Like with `CIOUT`, the status of the operation can be retrieved using the `READST` KERNAL call.  If an error occurred, `READST` should return nonzero.

---

### Channel I/O

---

#### Function Name: `BSAVE`

Purpose: Save an area of memory to a file without writing an address header.  
Call Address: $FEBA  
Communication Registers: .A .X .Y  
Preparatory routines: SETNAM, SETLFS  
Error returns: c = 0 if no error, c = 1 in case of error and A will contain kernel error code  
Registers affected: .A .X .Y .P  

**Description:** Save the contents of a memory range to a file.  Unlike `SAVE`, this call does not write the start address to the beginning of the output file.

`SETLFS` and `SETNAM` must be called beforehand.  
A is address of zero page pointer to the start address.  
X and Y contain the _exclusive_ end address to save. That is, these should contain the address immediately after the final byte:  X = low byte, Y = high byte.  
Upon return, if C is clear, there were no errors.  C being set indicates an error in which case A will have the error number.  

---

#### Function Name: `BSOUT`

(This routine is also referred to as `CHROUT`)  

Purpose: Write a character to the default output device.  
Call Address: $FFD2  
Communication Registers: .A  
Preparatory routines: OPEN, CHKOUT (Both are only needed when sending to files/other non-screen devices)  
Error returns: c = 0 if no error, c = 1 in case of error  
Registers affected: .P  

**Description:** Writes the character in A to the currently-selected output device. By default, this is the user's screen. By calling `CHKOUT`, however, the default device can be changed and characters can be sent to other devices - a file on an SD card, for example. In order to send output to a file, call `OPEN` first to open the file, then `CHKOUT` to set it as the default output device, then finally `BSOUT` to write the data.  

Upon return, if C is clear, there were no errors. Otherwise, C will be set.  

**Note:** Before returning, this routine uses a `CLI` processor instruction, which will allow IRQ interrupts to be triggered. This makes the `BSOUT` routine inappropriate for use within interrupt handler functions. One possible workaround could be to output text information directly, by writing to the appropriate VERA registers. Care must be taken to save and restore the VERA's state, however, in order to prevent affecting other software running on the system (to include BASIC or the KERNAL itself).  

---

#### Function Name: `BASIN`

(This routine is also referred to as `CHRIN`)  

Purpose: Read a character from the selected input channel, or from the screen editor.  
Call Address: $FFCF  
Communication Registers: .A  
Preparatory routines: `OPEN`, `CHKIN` (Both are only needed when reading from files/other non-screen devices)  
Error returns: none (use `READST`)  
Registers affected: .A .X .Y .P  

**Description:** Reads a character from the currently-selected input device, or a character from the screen editor.

##### Screen editor

After a `CLRCHN`, or without calling `CHKIN`, calling `BASIN` for the first time will invoke the KERNAL screen editor.  The user will be able to type and navigate around the screen with exactly the same behaviors as the BASIC editor. `BASIN` will block until the user presses RETURN/ENTER.

When `BASIN` returns from the editor, .A will contain the first character of the edited line that the user pressed RETURN on.  Subsequent calls to `BASIN` will return immediately with the next character in .A from the edited line.  Code $0D or 13 signals the end of the line.  A call to `BASIN` after this point will re-enter the KERNAL editor to read another line.

##### Channel I/O

After calling `CHKIN`, calling `BASIN` (or `CHRIN`) will fetch a byte from the selected input channel. `BASIN` does not report success or failure itself, but a call to `READST` can indicate failures or the end of file.

Note that on the end-of-file indication is delivered with the last byte of a file in the status returned by `READST`.

---

#### Function Name: `BSOUT`

(This routine is also referred to as `CHROUT`)  

Purpose: Write a character to the default output device.  
Call Address: $FFD2  
Communication Registers: .A  
Preparatory routines: `OPEN`, `CHKOUT` (Both are only needed when sending to files/other non-screen devices)  
Error returns: c = 0 if no error, c = 1 in case of error  
Registers affected: .P  

**Description:** Writes the character in A to the currently-selected output device. By default, this is the user's screen. By calling `CHKOUT`, however, the default device can be changed and characters can be sent to other devices - a file on an SD card, for example. In order to send output to a file, call `OPEN` first to open the file, then `CHKOUT` to set it as the default output device, then finally `BSOUT` to write the data.  

Upon return, if C is clear, there were no errors. Otherwise, C will be set.  

**Note:** Before returning, this routine uses a `CLI` processor instruction, which will allow IRQ interrupts to be triggered. This makes the `BSOUT` routine inappropriate for use within interrupt handler functions. One possible workaround could be to output text information directly, by writing to the appropriate VERA registers. Care must be taken to save and restore the VERA's state, however, in order to prevent affecting other software running on the system (to include BASIC or the KERNAL itself).  

---

#### Function Name: `CLOSE`

Purpose: Close a logical file  
Call address: $FFC3  
Communication registers: .A  
Preparatory routines: None  
Error returns: None  
Registers affected: .A .X .Y .P  

**Description:** `CLOSE` releases resources associated with a logical file number.  If the associated device is a serial device on the IEC bus or is a simulated serial device such as CMDR-DOS backed by the X16 SD card, and the file was opened with a secondary address, a close command is sent to the device or to CMDR-DOS.  

---

#### Function Name: `CHKIN`

Purpose: Set file to be used for character input  
Call address: $FFC6  
Communication registers: .X  
Preparatory routines: OPEN  
Error returns: Carry (Set on Error), .A  
Registers affected: .A .X

**Description:** `CHKIN` sets a file to be used as default input allowing for
subsequent calls to `CHRIN` or other file read functions. The `x` register
should contain the logical file number. `OPEN` will need to have been called prior to using `CHKIN`.

---

#### Function Name: `GETIN`

Purpose: Read a byte from the selected input channel, or a character from the keyboard buffer.  
Call Address: $FFE4  
Communication Registers: .A  
Preparatory routines: `OPEN`, `CHKIN` (Both are only needed when reading from files/other non-keyboard devices)  
Error returns: none (use `READST` for Channel I/O)  
Registers affected: .A .X .Y .P  

**Description:** Reads a byte from the currently-selected input channel, or a character from the keyboard's input buffer.

##### Keyboard

After a `CLRCHN`, or without calling `CHKIN`, calling `GETIN` will return a character from the keyboard's input buffer into the .A register.  If the buffer is empty, .A will contain 0.

As of R49, an alternative to calling `GETIN` for keyboard input if you are simultaneously handling file I/O is to use the `extapi` call `kbdbuf_get`, which isn't affected by the `CHKIN` call.

##### Channel I/O

After calling `CHKIN`, calling `GETIN` behaves nearly identically to `BASIN`.

---

#### Function Name: `LOAD`

Purpose: Load the contents of a file from disk to memory  
Call address: $FFD5  
Communication registers: .A .X .Y  
Preparatory routines: SETNAM, SETLFS  
Error returns: Carry (Set on Error), .A  
Registers affected: .A .X .Y .P  

**Description:** Loads a file from disk to memory.

The behavior of `LOAD` can be modified by parameters passed to prior call to `SETLFS`.  In particular, the .Y register, which usually denotes the _secondary address_, has a specific meaning as follows:

* .Y = 0: load to the address given in .X/.Y to the `LOAD` call, skipping the first two bytes of the file. (like `LOAD "FILE",8` in BASIC)
* .Y = 1: load to the address given by the first two bytes of the file. The address in .X/.Y is ignored. (like `LOAD "FILE",8,1` in BASIC)
* .Y = 2: load the entire file to the address given in .X/.Y to the `LOAD` call. This is also known as a _headerless_ load. (like `BLOAD "FILE",8,1,$A000` in BASIC)

For the `LOAD` call itself, .X and .Y is the memory address to load
the file into. .A controls where the file is to be loaded. On the X16, `LOAD` has an
additional feature to load the contents of a file directly into VRAM.

* If the A register is zero, the kernal loads into system memory.
* If the A register is 1, the kernal performs a verify.
* If the A register is 2, the kernal loads into VRAM, starting from $00000 + the specified starting address.
* If the A register is 3, the kernal loads into VRAM, starting from $10000 + the specified starting address.

(On the C64, if A is greater than or equal to 1, the kernal performs a verify)

For loads into the banked RAM area. The current RAM bank (in location `$00`) is used as the start point for the load along with the supplied address. If the load is large enough to advance to the end of banked RAM (`$BFFF`), the RAM bank is automatically advanced, and the load continues into the next bank starting at `$A000`.

After the load, if c is set, an error occurred and .A will contain the error code. If c is clear, .X/.Y will point to the address of final byte loaded + 1.

Note: One does not need to call `CLOSE` after `LOAD`.

---

#### Function Name: `OPEN`

Purpose: Opens a channel/file  
Call address: $FFC0  
Communication registers: None  
Preparatory routines: SETNAM, SETLFS  
Error returns: Carry (Set on Error), .A  
Registers affected: .A .X .Y  

**Description:** Opens a file or channel.  
The most common pattern is to then redirect the standard input or output to the file using `CHKIN` or `CHKOUT` respectively. Afterwards, I/O from or to the file or channel is done using `BASIN` (`CHRIN`) and `BSOUT` (`CHROUT`) respectively.

For file I/O, the lower level calls `ACPTR` and `MACPTR` can be used in place of `CHRIN`, since `CHKIN` does the low-level setup for this.  Likewise `CIOUT` and `MCIOUT` can be used after `CHKOUT` for the same reason.

When opening a zero length file name on a serial device, this function does not check if the device is present.

---

#### Function Name: `SAVE`

Purpose: Save an area of memory to a file.  
Call Address: $FFD8  
Communication Registers: .A .X .Y  
Preparatory routines: SETNAM, SETLFS  
Error returns: c = 0 if no error, c = 1 in case of error and A will contain kernel error code  
Registers affected: .A .X .Y .P  

**Description:** Save the contents of a memory range to a file. The (little-endian) start address is written to the file as the first two bytes of output, followed by the requested data.

`SETLFS` and `SETNAM` must be called beforehand.  
A is address of zero page pointer to start address.  
X = low byte of end address + 1, Y = high byte of end address.  
If C is zero there were no errors; 1 is an error in which case A will have the error  

---

#### Function Name: `SETLFS`

Purpose: Set file parameters  
Call Address: $FFBA  
Communication Registers: .A .X .Y  
Preparatory routines: SETNAM  
Error returns: None  
Registers affected: .A .X .Y  

**Description:** Set file parameters typically after calling SETNAM

A is the logical file number, X is the device number, and Y is the secondary address.

Since multiple files can be open (with some exceptions), the value of A specifies the file
number. If only one file is being opened at a time, $01 can be used.

The device number corresponds to the hardware device where the file lives. On the X16,
$08 would be the SD card.

The secondary address has some special meanings:  

When used with `OPEN` on disk type devices, the following applies:  

* 0 = Load (open for read)
* 1 = Save (open for write)
* 2-14 = Read mode, by default. Write, Append, and Modify modes can be specified in the SETNAM filename string as the third argument, e.g. `"FILE.DAT,S,W"` for write mode. The seek command "P" is available in any mode.
* 15 = Command Channel (for sending special commands to CMDR-DOS or the disk device)

When used with `LOAD` the following applies:

* 0 = Load the data to address specified in the X and Y register of the LOAD call, regardless of the address header. The two-byte header itself is not loaded into RAM.
* 1 = Load to the address specified in the file's header. The two-byte header itself is not loaded into RAM.
* 2 = Load the data to address specified in the X and Y register of the LOAD call. The entire file is loaded ("headerless").

For more information see [Chapter 13: Working with CMDR-DOS](X16%20Reference%20-%2013%20-%20Working%20with%20CMDR-DOS.md#chapter-13-working-with-cmdr-dos)

---

#### Function Name: `SETNAM`

Purpose: Set file name  
Call Address: $FFBD  
Communication Registers: .A .X .Y  
Preparatory routines: SETLFS  
Error returns: None  
Registers affected: .A .X .Y  

**Description:** Inform the kernal the name of the file that is to later be opened.
 A is filename length, X is low byte of filename pointer, Y is high byte of filename pointer.

For example:

```asm
  lda #$08
  ldx #<filename
  ldy #>filename
  jsr SETNAM
```

`SETLFS` and `SETNAM` both need to be called prior other file commands, such as `OPEN` or
`SAVE`.

To append to a file, add `,?,A` to the filename. See [Appending to file](X16%20Reference%20-%2013%20-%20Working%20with%20CMDR-DOS.md#appending-to-file).

**Warning:** Appending to file involves a risk of corrupting the file system of the SD card! See [Appending to file](X16%20Reference%20-%2013%20-%20Working%20with%20CMDR-DOS.md#appending-to-file).

---

### Memory

\$FEE4: `memory_fill` - fill memory region with a byte value  
\$FEE7: `memory_copy` - copy memory region  
\$FEEA: `memory_crc` - calculate CRC16 of memory region  
\$FEED: `memory_decompress` - decompress LZSA2 block  
\$FF74: `fetch` - read a byte from any RAM or ROM bank  
\$FF77: `stash` - write a byte to any RAM bank
\$FF99: `MEMTOP` - get number of banks and address of end of usable RAM

<!---
*** undocumented - we might remove it
$FF7A: `cmpare` - compare a byte on any RAM or ROM bank
--->
---

#### Function Name: memory_fill

Signature: void memory_fill(word address: r0, word num_bytes: r1, byte value: .A);  
Purpose: Fill a memory region with a byte value.  
Call address: $FEE4

**Description:** This function fills the memory region specified by an address (r0) and a size in bytes (r1) with the constant byte value passed in .A. r0 and .A are preserved, r1 is destroyed.

If the target address is in the \$9F00-\$9FFF range, all bytes will be written to the same address (r0), i.e. the address will not be incremented. This is useful for filling VERA memory (\$9F23 or \$9F24), for example.

---

#### Function Name: memory_copy

Signature: void memory_copy(word source: r0, word target: r1, word num_bytes: r2);  
Purpose: Copy a memory region to a different region.  
Call address: $FEE7

**Description:** This function copies one memory region specified by an address (r0) and a size in bytes (r2) to a different region specified by its start address (r1). The two regions may overlap. r0 and r1 are preserved, r2 is destroyed.

Like with `memory_fill`, source and destination addresses in the \$9F00-\$9FFF range will not be incremented during the copy. This allows, for instance, uploading data from RAM to VERA (destination of \$9F23 or \$9F24), downloading data from VERA (source \$9F23 or \$9F24) or copying data inside VERA (source \$9F23, destination \$9F24). This functionality can also be used to upload, download or transfer data with other I/O devices that have an 8 bit data port.

---

#### Function Name: memory_crc

Signature: (word result: r2) memory_crc(word address: r0, word num_bytes: r1);  
Purpose: Calculate the CRC16 of a memory region.  
Call address: $FEEA

**Description:** This function calculates the CRC16 checksum ([CRC-16/IBM-3740](https://www.crccalc.com/?crc=01%2002%2003%2004&method=CRC-16/IBM-3740&datatype=hex&outtype=hex)) of the memory region specified by an address (r0) and a size in bytes (r1). The result is returned in r2. r0 is preserved, r1 is destroyed.

Like `memory_fill`, this function does not increment the address if it is in the range of \$9F00-\$9FFF, which allows checksumming VERA memory or data streamed from any other I/O device.

Note: ROM R48 and older contains the following bug: If the size of the data is not a multiple of 256, the remainder of the data is processed in the wrong byte order. This bug was fixed in [#382](https://github.com/X16Community/x16-rom/pull/382). Thus, if your data is not a multiple of 256, you will get different CRC depending of ROM version.

---

#### Function Name: memory_decompress

Signature: void memory_decompress(word input: r0, inout word output: r1);  
Purpose: Decompress an LZSA2 block  
Call address: $FEED

**Description:** This function decompresses an LZSA2-compressed data block from the location passed in r0 and outputs the decompressed data at the location passed in r1. After the call, r1 will be updated with the location of the last output byte plus one.

If the target address is in the \$9F00-\$9FFF range, all bytes will be written to the same address (r0), i.e. the address will not be incremented. This is useful for decompressing directly into VERA memory (\$9F23 or \$9F24), for example. Note that decompressing _from_ I/O is not supported.

**Notes**:

* To create compressed data, use the `lzsa` tool[^1] like this:
`lzsa -r -f2 <original_file> <compressed_file>`
* If using the LZSA library to compress data, make sure to use format 2 and include the raw blocks flag, which is what the above command does.
* This function cannot be used to decompress data in-place, as the output data would overwrite the input data before it is consumed. Therefore, make sure to load the input data to a different location.
* It is possible to have the input data stored in banked RAM, with the obvious 8 KB size restriction.
* When decompressing to VRAM, it's recommended to do that through `DATA0`.
* If you'd like to have control of how the LZSA2 data is obtained, check out the [`memory_decompress_from_func`](#extapi-function-name-memory_decompress_from_func) function.

---

#### Function Name: fetch

Purpose: Read a byte from any RAM or ROM bank  
Call address: $FF74  
Communication registers: .A .X .Y .P  

**Description:** This function performs an `LDA (ZP),Y` from any RAM or ROM bank. The the zero page address containing the base address is passed in .A, the bank in .X and the offset from the vector in .Y. The data byte is returned in .A. The flags are set according to .A, .X is destroyed, but .Y is preserved.

---

#### Function Name: stash

Purpose: Write a byte to any RAM bank  
Call address: $FF77  
Communication registers: .A .X .Y  

**Description:** This function performs an `STA (ZP),Y` to any RAM bank. The the zero page address containing the base address is passed in `stavec` ($03B2), the bank in .X and the offset from the vector in .Y. After the call, .X is destroyed, but .A and .Y are preserved.

---

#### Function Name: MEMTOP

Purpose: Get/Set top of RAM, number of usable RAM banks.  
Call address: $FF99  
Communication registers: .A .X .Y .P (Carry)  
Registers affected: .A .X .Y  

**Description:** Original C64 function which gets or
sets the top of the usable address in RAM. On the X16,
it additionally provides the number of RAM banks
available on the system and can even be used to set
this value after boot if desired.

To set the top of RAM, and the number of available banks, clear the carry flag.

To get the top of RAM and the number of available
banks, set carry flag.

Note that the number of RAM banks is for informational
purposes or for use by other programs. The KERNAL
does not use this value itself.

**Getting the number of usable RAM banks:**

On the X16, calling MEMTOP with the carry flag set
will return the number of available RAM banks on
the system in A. For example:

```asm
  sec
  jsr MEMTOP
  sta zp_NUM_BANKS
```

If the system has 512k of banked RAM, zp_NUM_BANKS
will contain \$40 (64). For 1024k, \$80; for 1536k, \$C0.
For 2048k, the result will be \$00 (which can be thought
of as \$100, or 256). It is possible to have other
values (e.g. \$42), such as if the system has bad
banked RAM.

**Setting the top of BASIC RAM**

This routine changes the top of memory, allowing you to save a small machine
language routine at the top of BASIC RAM, just below the I/O space:

```BASIC
10 POKE$30F,1:SYS$FF99
20 Y=$8C:X=$00
30 POKE$30D,X:POKE$30E,Y:POKE$30F,0:SYS$FF99
40 CLR
```

Analysis: 

The SYS command uses memory locations \$30C-\$30F to pre-load the CPU registers,
it then dumps the registers back to these locations after the SYS call is
complete. \$30D is the X register, \$30E is .Y, and \$30F is the flags. The Carry
flag is bit 0, so setting $30F to 1 before calling MEMTOP indicates that this is
a _read_ of the values. 

1. Line 10 reads the current values. Do this to preserve the extended RAM bank
   count.
2. Line 20 uses the X and Y variables to make the code easier to read. Set Y to
   the high byte of the address and X to the low byte. 
3. Line 30 POKEs those values in, clears the Carry bit ($30F is now 0), and
   calls MEMTOP again.
4. Finally, use CLR to lock in the new values. Since this clears all the
   variables, you should _probably_ do this at the top of your program.

The address entered is actually the first byte of free space _after_
your BASIC program space, so if you set MEMTOP to \$9C00, then you can start your
assembly program at \$9C00 with `* = $9C00` or `org $9c00`.

To reserve 256 bytes, set X to \$9E. To reserve 1KB, set X to \$9C. To return to
the default values, set Y=\$9F and X=0.

---

### Clock

\$FF4D: `clock_set_date_time` - set date and time  
\$FF50: `clock_get_date_time` - get date and time  

---

#### Function Name: clock_set_date_time

Purpose: Set the date and time  
Call address: $FF4D  
Communication registers: r0 r1 r2 r3  
Preparatory routines: None  
Error returns: None  
Registers affected: .A .X .Y  

**Description:** The routine `clock_set_date_time` sets the system's real-time-clock.

| Register | Contents          |
|----------|-------------------|
| r0L      | year (1900-based) |
| r0H      | month (1-12)      |
| r1L      | day (1-31)        |
| r1H      | hours (0-23)      |
| r2L      | minutes (0-59)    |
| r2H      | seconds (0-59)    |
| r3L      | jiffies (0-59)    |
| r3H      | weekday (1-7)     |

Jiffies are 1/60th seconds.

---

#### Function Name: clock_get_date_time

Purpose: Get the date and time  
Call address: $FF50  
Communication registers: r0 r1 r2 r3  
Preparatory routines: None  
Error returns: None  
Registers affected: .A .X .Y  

**Description:** The routine `clock_get_date_time` returns the state of the system's real-time-clock. The register assignment is identical to `clock_set_date_time`.

On the Commander X16, the _jiffies_ field is unsupported and will always read back as 0.

---

#### Function Name: RDTIM

Purpose: Read system clock  
Call address: $FFDE  
Communication registers: .A .X .Y  
Preparatory routines: None  
Error returns: None  
Registers affected: .A .X .Y  

**Description:** Original C64 function which reads the system clock.  The clock's resolution is a 60th of a second.  Three bytes are returned by the routine.  The accumulator contains the least significant byte, the X index register contains the next most significant byte, and the Y index register contains the the most significant byte.

The behavior of this Kernal routine is the same on the X16 and C64 despite errors in the _Commodore 64 Programmer's Reference Guide_ and some other period books which incorrectly describe the order/significance of the resulting bytes in the registers.

**EXAMPLE**:

```ASM
jsr RDTIM
sta STARTTIME    ; least significant byte
stx STARTTIME+1
sty STARTTIME+2  ; most significant byte
```

---

### Keyboard

\$FEBD: `kbdbuf_peek` - get first char in keyboard queue and queue length  
\$FEC0: `kbdbuf_get_modifiers` - get currently pressed modifiers  
\$FEC3: `kbdbuf_put` - append a char to the keyboard queue  
\$FED2: `keymap` - set or get the current keyboard layout

---

#### Function Name: kbdbuf_peek

Purpose: Get next char and keyboard queue length  
Call address: $FEBD  
Communication registers: .A .X  
Preparatory routines: None  
Error returns: None  
Registers affected: -  

**Description:** The routine `kbdbuf_peek` returns the next character in the keyboard queue in .A, without removing it from the queue, and the current length of the queue in .X. If .X is 0, the Z flag will be set, and the value of .A is undefined.

---

#### Function Name: kbdbuf_get_modifiers

Purpose: Get currently pressed modifiers  
Call address: $FEC0  
Communication registers: .A  
Preparatory routines: None  
Error returns: None  
Registers affected: -  

**Description:** The routine `kbdbuf_get_modifiers` returns a bitmask that represents the currently pressed modifier keys in .A:

| Bit | Value | Description  | Comment        |
|-----|-------|--------------|----------------|
| 0   | 1     | Shift        |                |
| 1   | 2     | Alt          | C64: Commodore |
| 2   | 4     | Control      |                |
| 3   | 8     | Logo/Windows | C128: Alt      |
| 4   | 16    | Caps         |                |

This allows detecting combinations of a regular key and a modifier key in cases where there is no dedicated PETSCII code for the combination, e.g. Ctrl+Esc or Alt+F1.

---

#### Function Name: kbdbuf_put

Purpose: Append a char to the keyboard queue  
Call address: $FEC3  
Communication registers: .A  
Preparatory routines: None  
Error returns: None  
Registers affected: .X  

**Description:** The routine `kbdbuf_put` appends the char in .A to the keyboard queue.

---

#### Function Name: keymap

Purpose: Set or get the current keyboard layout
Call address: $FED2  
Communication registers: .X .Y  
Preparatory routines: None  
Error returns: c = 1 in case of error  
Registers affected: -  

**Description:** If c is set, the routine `keymap` returns a pointer to a zero-terminated string with the current keyboard layout identifier in .X/.Y. If c is clear, it sets the keyboard layout to the zero-terminated identifier pointed to by .X/.Y. On return, c is set in case the keyboard layout is unsupported.

Keyboard layout identifiers are in the form "DE", "DE-CH" etc.

---

#### Function Name: kbd_scan

Also Known As: SCNKEY  
Purpose: Read a keycode previously fetched from the SMC, apply keymap localization, and add it to the X16's buffer.  
Call address: $FF9F  
Communication registers: None  
Preparatory routines: `ps2data_fetch`  
Error returns: None  
Registers affected: .A .X .Y  

**Description:**

This routine is called by the default KERNAL IRQ hancler in order to process a keystroke previously fetched by `ps2data_fetch`, translate it to the appropriate localized PETSCII or ISO code based on the configured layout, and place it in the KERNAL's keyboard buffer.

Unless the KERNAL IRQ handler is being bypassed or supplemented, it is not normally necessary to call this routine from user code, as both `ps2data_fetch` and `kbd_scan` are both run inside the default IRQ handler.  

---

### Mouse

\$FF68: `mouse_config` - configure mouse pointer  
\$FF71: `mouse_scan` - query mouse  
\$FF6B: `mouse_get` - get state of mouse

---

#### Function Name: mouse_config

Purpose: Configure the mouse pointer  
Call address: $FF68  
Communication registers: .A .X .Y  
Preparatory routines: None  
Error returns: None  
Registers affected: .A .X .Y  

**Description:** The routine `mouse_config` configures the mouse pointer.

The argument in .A specifies whether the mouse pointer should be visible or not, and what shape it should have. For a list of possible values, see the basic statement [MOUSE](X16%20Reference%20-%2004%20-%20BASIC.md#mouse).

The arguments in .X and .Y specify the screen resolution in 8 pixel increments. The values .X = 0 and .Y = 0 keep the current resolution.

**EXAMPLE:**

 SEC
 JSR screen_mode ; get current screen size (in 8px) into .X and .Y
 LDA #1
 JSR mouse_config ; show the default mouse pointer

---

#### Function Name: mouse_scan

Purpose: Query the mouse and save its state  
Call address: $FF71  
Communication registers: None  
Preparatory routines: None  
Error returns: None  
Registers affected: .A .X .Y  

**Description:** The routine `mouse_scan` retrieves all state from the mouse and saves it. It can then be retrieved using `mouse_get`. The default interrupt handler already takes care of this, so this routine should only be called if the interrupt handler has been completely replaced.

---

#### Function Name: mouse_get

Purpose: Get the mouse state  
Call address: $FF6B  
Communication registers: .X  
Preparatory routines: `mouse_config`  
Error returns: None  
Registers affected: .A .X  

**Description:** The routine `mouse_get` returns the state of the mouse. The caller passes the offset of a zero-page location in .X, which the routine will populate with the mouse position in 4 consecutive bytes:

| Offset | Size | Description |
|--------|------|-------------|
| 0      | 2    | X Position  |
| 2      | 2    | Y Position  |

The state of the mouse buttons is returned in the .A register:

| Bit | Description    |
|-----|----------------|
| 0   | Left Button    |
| 1   | Right Button   |
| 2   | Middle Button  |
| 3   | Unused         |
| 4   | Button 4       |
| 5   | Button 5       |

If a button is pressed, the corresponding bit is set. Buttons 4 and 5 are extended buttons not supported by all mice.

If available, the movement of the scroll wheel since the last call to this function is returned in the .X register as an 8-bit signed value. Moving the scroll wheel away from the user is represented
by a negative value, and moving it towards the user is represented by a positive value. If the connected mouse has no scroll wheel, the value 0 is returned in the .X register.

**EXAMPLE:**

```ASM
LDX #$70
JSR mouse_get ; get mouse position in $70/$71 (X) and $72/$73 (Y)
AND #1
BNE BUTTON_PRESSED
```

---

### Joystick

\$FF53: `joystick_scan` - query joysticks  
\$FF56: `joystick_get` - get state of one joystick

---

#### Function Name: joystick_scan

Purpose: Query the joysticks and save their state  
Call address: $FF53  
Communication registers: None  
Preparatory routines: None  
Error returns: None  
Registers affected: .A .X .Y  

**Description:** The routine `joystick_scan` retrieves all state from the four joysticks and saves it. It can then be retrieved using `joystick_get`. The default interrupt handler already takes care of this, so this routine should only be called if the interrupt handler has been completely replaced.

---

#### Function Name: joystick_get

Purpose: Get the state of one of the joysticks  
Call address: $FF56  
Communication registers: .A  
Preparatory routines: `joystick_scan`  
Error returns: None  
Registers affected: .A .X .Y  

**Description:** The routine `joystick_get` retrieves all state from one of the joysticks. The number of the joystick is passed in .A (0 for the keyboard joystick and 1 through 4 for SNES controllers), and the state is returned in .A, .X and .Y.

```ASM
      .A, byte 0:      | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |
                  SNES | B | Y |SEL|STA|UP |DN |LT |RT |

      .X, byte 1:      | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |
                  SNES | A | X | L | R | 1 | 1 | 1 | 1 |
      .Y, byte 2:
                  $00 = joystick present
                  $FF = joystick not present
```

If a button is pressed, the corresponding bit is zero.

(With a dedicated handler, the API can also be used for other devices with an SNES controller connector. The data returned in .A/.X/Y is just the raw 24 bits returned by the device.)

The keyboard joystick uses the standard SNES9X/ZSNES mapping:

| SNES Button    |Keyboard Key  | Alt. Keyboard Key |
|----------------|--------------|-------------------|
| A              | X            | Left Ctrl         |
| B              | Z            | Left Alt          |
| X              | S            |                   |
| Y              | A            |                   |
| L              | D            |                   |
| R              | C            |                   |
| START          | Enter        |                   |
| SELECT         | Left Shift   |                   |
| D-Pad          | Cursor Keys  |                   |

Note that the keyboard joystick will allow LEFT and RIGHT as well as UP and DOWN to be pressed at the same time, while controllers usually prevent this mechanically.

**How to Use:**

If the default interrupt handler is used:

1) Call this routine.

If the default interrupt handler is disabled or replaced:

1) Call `joystick_scan` to have the system query the joysticks.
2) Call this routine.

**EXAMPLE:**

```ASM
      JSR joystick_scan
      LDA #0
      JSR joystick_get
      TXA
      AND #128
      BEQ A_PRESSED
```

---

### I2C

\$FEB4: `i2c_batch_read` - read multiple bytes from an I2C device  
\$FEB7: `i2c_batch_write` - write multiple bytes to an I2C device  
\$FEC6: `i2c_read_byte` - read a byte from an I2C device  
\$FEC9: `i2c_write_byte` - write a byte to an I2C device

---

#### Function Name: i2c_batch_read

Purpose: Read bytes from a given I2C device into a RAM location  
Call address: $FEB4  
Communication registers: .X r0 r1 c  
Preparatory routines: None  
Error returns: c = 1 in case of error  
Registers affected: .A .Y .P  

**Description:** The routine `i2c_batch_read` reads a fixed number of bytes from an I2C device into RAM.  To call, put I2C device (address) in .X, the pointer to the RAM location to which to place the data into r0, and the number of bytes to read into r1.  If carry is set, the RAM location isn't advanced.  This might be useful if you're reading from an I2C device and writing directly into VRAM.

If the routine encountered an error, carry will be set upon return.

**EXAMPLE:**

```ASM
ldx #$50 ; One of the cartridge I2C flash devices
lda #<$0400
sta r0
lda #>$0400
sta r0+1
lda #<500
sta r1
lda #>500
sta r1+1
clc
jsr i2c_batch_read ; read 500 bytes from I2C device $50 into RAM starting at $0400
```

---

#### Function Name: i2c_batch_write

Purpose: Write bytes to a given I2C device with data in RAM  
Call address: $FEB7  
Communication registers: .X r0 r1 r2 c  
Preparatory routines: None  
Error returns: c = 1 in case of error  
Registers affected: .A .Y .P r2  

**Description:** The routine `i2c_batch_write` writes a fixed number of bytes from RAM to an I2C device.  To call, put I2C device (address) in .X, the pointer to the RAM location from which to read into r0, and the number of bytes to write into r1.  If carry is set, the RAM location isn't advanced.  This might be useful if you're reading from an I/O device and writing that data to an I2C device.

The number of bytes written is returned in r2. If the routine encountered an error, carry will be set upon return.

**EXAMPLE:**

```ASM
ldx #$50 ; One of the cartridge I2C flash devices
lda #<$0400
sta r0
lda #>$0400
sta r0+1
lda #<500
sta r1
lda #>500
sta r1+1
clc
jsr i2c_batch_write ; write 500 bytes to I2C device $50 from RAM
                    ; starting at $0400 
                    ; for this example, the first two bytes in
                    ; the $0400 buffer would be the target address
                    ; in the I2C flash. This, of course, varies
                    ; between various I2C device types.
```

---

#### Function Name: i2c_read_byte

Purpose: Read a byte at a given offset from a given I2C device  
Call address: $FEC6  
Communication registers: .A .X .Y  
Preparatory routines: None  
Error returns: c = 1 in case of error  
Registers affected: .A  

**Description:** The routine `i2c_read_byte` reads a single byte at offset .Y from I2C device .X and returns the result in .A. c is 0 if the read was successful, and 1 if no such device exists.

**EXAMPLE:**

```ASM
LDX #$6F ; RTC device
LDY #$20 ; start of NVRAM inside RTC
JSR i2c_read_byte ; read first byte of NVRAM
```

---

#### Function Name: i2c_write_byte

Purpose: Write a byte at a given offset to a given I2C device  
Call address: $FEC9  
Communication registers: .A .X .Y  
Preparatory routines: None  
Error returns: c = 1 in case of error  
Registers affected: .A .P  

**Description:** The routine `i2c_write_byte` writes the byte in .A at offset .Y of I2C device .X. c is 0 if the write was successful, and 1 if no such device exists.

**EXAMPLES:**

```ASM
LDX #$6F ; RTC device
LDY #$20 ; start of NVRAM inside RTC
LDA #'X'
JSR i2c_write_byte ; write first byte of NVRAM

LDX #$42 ; System Management Controller
LDY #$01 ; magic location for system poweroff
LDA #$00 ; magic value for system poweroff
JSR i2c_write_byte ; power off the system

; Reset system at the end of your program
LDX #$42  ; System Management Controller
LDY #$02  ; magic location for system reset
LDA #$00  ; magic value for system poweroff/reset
JSR $FEC9 ; reset the computer
```

---

### Sprites

\$FEF0: `sprite_set_image` - set the image of a sprite  
\$FEF3: `sprite_set_position` - set the position of a sprite

---

#### Function Name: sprite_set_image

Purpose: Set the image of a sprite  
Call address: $FEF0  
Signature: bool sprite_set_image(byte number: .A, width: .X, height: .Y, apply_mask: c, word pixels: r0, word mask: r1, byte bpp: r2L);  
Error returns: c = 1 in case of error

**Description:** This function sets the image of a sprite. The number of the sprite is given in .A, The bits per pixel (bpp) in r2L, and the width and height in .X and .Y. The pixel data at r0 is interpreted accordingly and converted into the graphics hardware's native format. If the c flag is set, the transparency mask pointed to by r1 is applied during the conversion. The function returns c = 0 if converting the data was successful, and c = 1 otherwise. Note that this does not change the visibility of the sprite.

**Note**: There are certain limitations on the possible values of width, height, bpp and apply_mask:

* width and height may not exceed the hardware's capabilities.
* Legal values for bpp are 1, 4 and 8. If the hardware only supports lower depths, the image data is converted down.
* apply_mask is only valid for 1 bpp data.

---

#### Function Name: sprite_set_position

Purpose: Set the position of a sprite or hide it.  
Call address: $FEF3  
Signature: void sprite_set_position(byte number: .A, word x: r0, word y: r1);  
Error returns: None

**Description:** This function shows a given sprite (.A) at a certain position or hides it. The position is passed in r0 and r1. If the x position is negative (&gt;$8000), the sprite will be hidden.

**Note**: This routine only supports setting the position for sprite numbers 0-31.

---

### Framebuffer

The framebuffer API is a low-level graphics API that completely abstracts the framebuffer by exposing a minimal set of high-performance functions. It is useful as an abstraction and as a convenience library for applications that need high performance framebuffer access.

```asm
$FEF6: `FB_init` - enable graphics mode  
$FEF9: `FB_get_info` - get screen size and color depth  
$FEFC: `FB_set_palette` - set (parts of) the palette  
$FEFF: `FB_cursor_position` - position the direct-access cursor  
$FF02: `FB_cursor_next_line` - move direct-access cursor to next line  
$FF05: `FB_get_pixel` - read one pixel, update cursor  
$FF08: `FB_get_pixels` - copy pixels into RAM, update cursor  
$FF0B: `FB_set_pixel` - set one pixel, update cursor  
$FF0E: `FB_set_pixels` - copy pixels from RAM, update cursor  
$FF11: `FB_set_8_pixels` - set 8 pixels from bit mask (transparent), update cursor  
$FF14: `FB_set_8_pixels_opaque` - set 8 pixels from bit mask (opaque), update cursor  
$FF17: `FB_fill_pixels` - fill pixels with constant color, update cursor  
$FF1A: `FB_filter_pixels` - apply transform to pixels, update cursor  
$FF1D: `FB_move_pixels` - copy horizontally consecutive pixels to a different position
```

All calls are vectored, which allows installing a replacement framebuffer driver.

```asm
$02E4: I_FB_init  
$02E6: I_FB_get_info  
$02E8: I_FB_set_palette  
$02EA: I_FB_cursor_position  
$02EC: I_FB_cursor_next_line  
$02EE: I_FB_get_pixel  
$02F0: I_FB_get_pixels  
$02F2: I_FB_set_pixel  
$02F4: I_FB_set_pixels  
$02F6: I_FB_set_8_pixels  
$02F8: I_FB_set_8_pixels_opaque  
$02FA: I_FB_fill_pixels  
$02FC: I_FB_filter_pixels  
$02FE: I_FB_move_pixels
```

The model of this API is based on the direct-access cursor. In order to read and write pixels, the cursor has to be set to a specific x/y-location, and all subsequent calls will access consecutive pixels at the cursor position and update the cursor.

The default driver supports the VERA framebuffer at a resolution of 320x240 pixels and 256 colors. Using `screen_mode` to set mode $80 will enable this driver.

---

#### Function Name: FB_init

Signature: void FB_init();  
Purpose: Enter graphics mode.

The default driver for this call activates VERA layer 0 without changing the state of any other VERA layers.  If layer 1 (such as the KERNAL text layer) is active and opaque, it may occlude layer 0 entirely.

---

#### Function Name: FB_get_info

Signature: void FB_get_info(out word width: r0, out word height: r1, out byte color_depth: .A);  
Purpose: Return the resolution and color depth

---

#### Function Name: FB_set_palette

Signature: void FB_set_palette(word pointer: r0, index: .A, color count: .X);  
Purpose: Set (parts of) the palette

**Description:** `FB_set_palette` copies color data from the address pointed to by r0, updates the color in VERA palette RAM starting at the index A, with the length of the update (in words) in X.  If X is 0, all 256 colors are copied (512 bytes)

---

#### Function Name: FB_cursor_position

Signature: void FB_cursor_position(word x: r0, word y: r1);  
Purpose: Position the direct-access cursor

**Description:** `FB_cursor_position` sets the direct-access cursor to the given screen coordinate. Future operations will access pixels at the cursor location and update the cursor.

---

#### Function Name: FB_cursor_next_line

Signature: void FB_cursor_next_line(word x: r0);  
Purpose: Move the direct-access cursor to next line

**Description:** `FB_cursor_next_line` increments the y position of the direct-access cursor, and sets the x position to the same one that was passed to the previous `FB_cursor_position` call. This is useful for drawing rectangular shapes, and faster than explicitly positioning the cursor.

---

#### Function Name: FB_get_pixel

Signature: byte FB_get_pixel();  
Purpose: Read one pixel, update cursor

---

#### Function Name: FB_get_pixels

Signature: void FB_get_pixels(word ptr: r0, word count: r1);  
Purpose: Copy pixels into RAM, update cursor

**Description:** This function copies pixels into an array in RAM. The array consists of one byte per pixel.

---

#### Function Name: FB_set_pixel

Signature: void FB_set_pixel(byte color: .A);  
Purpose: Set one pixel, update cursor

---

#### Function Name: FB_set_pixels

Signature: void FB_set_pixels(word ptr: r0, word count: r1);  
Purpose: Copy pixels from RAM, update cursor

**Description:** This function sets pixels from an array of pixels in RAM. The array consists of one byte per pixel.

---

#### Function Name: FB_set_8_pixels

Signature: void FB_set_8_pixels(byte pattern: .A, byte color: .X);  
Purpose: Set 8 pixels from bit mask (transparent), update cursor

**Description:** This function sets all 1-bits of the pattern to a given color and skips a pixel for every 0 bit. The order is MSB to LSB. The cursor will be moved by 8 pixels.

---

#### Function Name: FB_set_8_pixels_opaque

Signature: void FB_set_8_pixels_opaque(byte pattern: .A, byte mask: r0L, byte color1: .X, byte color2: .Y);  
Purpose: Set 8 pixels from bit mask (opaque), update cursor

**Description:** For every 1-bit in the mask, this function sets the pixel to color1 if the corresponding bit in the pattern is 1, and to color2 otherwise. For every 0-bit in the mask, it skips a pixel. The order is MSB to LSB. The cursor will be moved by 8 pixels.

---

#### Function Name: FB_fill_pixels

Signature: void FB_fill_pixels(word count: r0, word step: r1, byte color: .A);  
Purpose: Fill pixels with constant color, update cursor

**Description:** `FB_fill_pixels` sets pixels with a constant color. The argument `step` specifies the increment between pixels. A value of 0 or 1 will cause consecutive pixels to be set. Passing a `step` value of the screen width will set vertically adjacent pixels going top down. Smaller values allow drawing dotted horizontal lines, and multiples of the screen width allow drawing dotted vertical lines.

---

#### Function Name: FB_filter_pixels

Signature: void FB_filter_pixels(word ptr: r0, word count: r1);  
Purpose: Apply transform to pixels, update cursor

**Description:** This function allows modifying consecutive pixels. The function pointer will be called for every pixel, with the color in .A, and it needs to return the new color in .A.

---

#### Function Name: FB_move_pixels

Signature: void FB_move_pixels(word sx: r0, word sy: r1, word tx: r2, word ty: r3, word count: r4);  
Purpose: Copy horizontally consecutive pixels to a different position

*[Note: Overlapping regions are not yet supported.]*

---

### Graphics

The high-level graphics API exposes a set of standard functions. It allows applications to easily perform some common high-level actions like drawing lines, rectangles and images, as well as moving parts of the screen. All commands are completely implemented on top of the framebuffer API, that is, they will continue working after replacing the framebuffer driver with one that supports a different resolution, color depth or even graphics device.

\$FF20: `GRAPH_init` - initialize graphics  
\$FF23: `GRAPH_clear` - clear screen  
\$FF26: `GRAPH_set_window` - set clipping region  
\$FF29: `GRAPH_set_colors` - set stroke, fill and background colors  
\$FF2C: `GRAPH_draw_line` - draw a line  
\$FF2F: `GRAPH_draw_rect` - draw a rectangle (optionally filled)  
\$FF32: `GRAPH_move_rect` - move pixels  
\$FF35: `GRAPH_draw_oval` - draw an oval or circle  
\$FF38: `GRAPH_draw_image` - draw a rectangular image  
\$FF3B: `GRAPH_set_font` - set the current font  
\$FF3E: `GRAPH_get_char_size` - get size and baseline of a character  
\$FF41: `GRAPH_put_char` - print a character

---

#### Function Name: GRAPH_init

Signature: void GRAPH_init(word vectors: r0);  
Purpose: Activate framebuffer driver, enter and initialize graphics mode

**Description**: This call activates the framebuffer driver whose vector table is passed in r0. If r0 is 0, the default driver is activated. It then switches the video hardware into graphics mode, sets the window to full screen, initializes the colors and activates the system font.

This function calls `FB_init`, whose default driver activates VERA layer 0 without changing the state of any other VERA layers.  If layer 1 (such as the KERNAL text layer) is active and opaque, it may occlude layer 0 entirely.

---

#### Function Name: GRAPH_clear

Signature: void GRAPH_clear();  
Purpose: Clear the current window with the current background color.

---

#### Function Name: GRAPH_set_window

Signature: void GRAPH_set_window(word x: r0, word y: r1, word width: r2, word height: r3);  
Purpose: Set the clipping region

**Description:** All graphics commands are clipped to the window. This function configures the origin and size of the window. All 0 arguments set the window to full screen.

*[Note: Only text output and GRAPH_clear currently respect the clipping region.]*

---

#### Function Name: GRAPH_set_colors

Signature: void GRAPH_set_colors(byte stroke: .A, byte fill: .X, byte background: .Y);  
Purpose: Set the three colors

**Description:** This function sets the three colors: The stroke color, the fill color and the background color.

---

#### Function Name: GRAPH_draw_line

Signature: void GRAPH_draw_line(word x1: r0, word y1: r1, word x2: r2, word y2: r3);  
Purpose: Draw a line using the stroke color

---

#### Function Name: GRAPH_draw_rect

Signature: void GRAPH_draw_rect(word x: r0, word y: r1, word width: r2, word height: r3, word corner_radius: r4, bool fill: c);  
Purpose: Draw a rectangle.

**Description:** This function will draw the frame of a rectangle using the stroke color. If `fill` is `true`, it will also fill the area using the fill color. To only fill a rectangle, set the stroke color to the same value as the fill color.

*[Note: The border radius is currently unimplemented.]*

---

#### Function Name: GRAPH_move_rect

Signature: void GRAPH_move_rect(word sx: r0, word sy: r1, word tx: r2, word ty: r3, word width: r4, word height: r5);  
Purpose: Copy a rectangular screen area to a different location

**Description:** `GRAPH_move_rect` coll copy a rectangular area of the screen to a different location. The two areas may overlap.

*[Note: Support for overlapping is not currently implemented.]*

---

#### Function Name: GRAPH_draw_oval

Signature: void GRAPH_draw_oval(word x: r0, word y: r1, word width: r2, word height: r3, bool fill: c);  
Purpose: Draw an oval or a circle

**Description:** This function draws an oval filling the given bounding box. If width equals height, the resulting shape is a circle. The oval will be outlined by the stroke color. If `fill` is `true`, it will be filled using the fill color. To only fill an oval, set the stroke color to the same value as the fill color.

---

#### Function Name: GRAPH_draw_image

Signature: void GRAPH_draw_image(word x: r0, word y: r1, word ptr: r2, word width: r3, word height: r4);  
Purpose: Draw a rectangular image from data in memory

**Description:** This function copies pixel data from memory onto the screen. The representation of the data in memory has to have one byte per pixel, with the pixels organized line by line top to bottom, and within the line left to right.

---

#### Function Name: GRAPH_set_font

Signature: void GRAPH_set_font(void ptr: r0);  
Purpose: Set the current font

**Description:** This function sets the current font to be used for the remaining font-related functions. The argument is a pointer to the font data structure in memory, which must be in the format of a single point size GEOS font (i.e. one GEOS font file VLIR chunk). An argument of 0 will activate the built-in system font.

---

#### Function Name: GRAPH_get_char_size

Signature: (byte baseline: .A, byte width: .X, byte height_or_style: .Y, bool is_control: c) GRAPH_get_char_size(byte c: .A, byte format: .X);  
Purpose: Get the size and baseline of a character, or interpret a control code

**Description:** This functionality of `GRAPH_get_char_size` depends on the type of code that is passed in: For a printable character, this function returns the metrics of the character in a given format. For a control code, it returns the resulting format. In either case, the current format is passed in .X, and the character in .A.

* The format is an opaque byte value whose value should not be relied upon, except for `0`, which is plain text.
* The resulting values are measured in pixels.
* The baseline is measured from the top.

---

#### Function Name: GRAPH_put_char

Signature: void GRAPH_put_char(inout word x: r0, inout word y: r1, byte c: .A);  
Purpose: Print a character onto the graphics screen

**Description:** This function prints a single character at a given location on the graphics screen. The location is then updated. The following control codes are supported:

* $01: SWAP COLORS
* $04: ATTRIBUTES: UNDERLINE
* $06: ATTRIBUTES: BOLD
* $07: BELL
* $08: BACKSPACE
* $09: TAB
* $0A: LF
* $0B: ATTRIBUTES: ITALICS
* $0C: ATTRIBUTES: OUTLINE
* \$0D/\$8D: REGULAR/SHIFTED RETURN
* \$11/\$91: CURSOR: DOWN/UP
* $12: ATTRIBUTES: REVERSE
* \$13/\$93: HOME/CLEAR
* $14 DEL
* $92: ATTRIBUTES: CLEAR ALL
* all color codes

Notes:

* CR (\$0D) SHIFT+CR (\$8D) and LF (\$0A) all set the cursor to the beginning of the next line. The only difference is that CR and SHIFT+CR reset the attributes, and LF does not.
* BACKSPACE (\$08) and DEL (\$14) move the cursor to the beginning of the previous character but does not actually clear it. Multiple consecutive BACKSPACE/DEL characters are not supported.
* There is no way to individually disable attributes (underlined, bold, reversed, italics, outline). The only way to disable them is to reset the attributes using code $92, which switches to plain text.
* All 16 PETSCII color codes are supported. Code $01 to swap the colors will swap the stroke and fill colors.
* The stroke color is used to draw the characters, and the underline is drawn using the fill color. In reverse text mode, the text background is filled with the fill color.
* *[BELL (\$07), TAB (\$09) and SHIFT+TAB (\$18) are not yet implemented.]*

---

### Console

\$FEDB: `console_init` - initialize console mode  
\$FEDE: `console_put_char` - print character to console  
\$FED8: `console_put_image` - draw image as if it was a character  
\$FEE1: `console_get_char` - get character from console  
\$FED5: `console_set_paging_message` - set paging message or disable paging

The console is a screen mode that allows text output and input in proportional fonts that support the usual styles. It is useful for rich text-based interfaces.

---

#### Function Name: console_init

Signature: void console_init(word x: r0, word y: r1, word width: r2, word height: r3);  
Purpose: Initialize console mode.  
Call address: $FEDB

**Description:** This function initializes console mode. It sets up the window (text clipping area) passed into it, clears the window and positions the cursor at the top left. All 0 arguments create a full screen console. You have to switch to graphics mode using `screen_mode` beforehand.

---

#### Function Name: console_put_char

Signature: void console_put_char(byte char: .A, bool wrapping: c);  
Purpose: Print a character to the console.  
Call address: $FEDE

**Description:** This function prints a character to the console. The c flag specifies whether text should be wrapped at character (c=0) or word (c=1) boundaries. In the latter case, characters will be buffered until a SPACE, CR or LF character is sent, so make sure the text that is printed always ends in one of these characters.

**Note**: If the bottom of the screen is reached, this function will scroll its contents up to make extra room.

---

#### Function Name: console_put_image

Signature: void console_put_image(word ptr: r0, word width: r1, word height: r2);  
Purpose: Draw image as if it was a character.  
Call address: $FED8

**Description:** This function draws an image (in GRAPH_draw_image format) at the current cursor position and advances the cursor accordingly. This way, an image can be presented inline. A common example would be an emoji bitmap, but it is also possible to show full-width pictures if you print a newline before and after the image.

**Notes**:

* If the bottom of the screen is reached, this function will scroll its contents up to make extra room.
* Subsequent line breaks will take the image height into account, so that the new cursor position is below the image.

---

#### Function Name: console_get_char

Signature: (byte char: .A) console_get_char();  
Purpose: Get a character from the console.  
Call address: $FEE1

**Description:** This function gets a character to the console. It does this by collecting a whole line of character, i.e. until the user presses RETURN. Then, the line will be sent character by character.

This function allows editing the line using BACKSPACE/DEL, but does not allow moving the cursor within the line, write more than one line, or using control codes.

---

#### Function Name: console_set_paging_message

Signature: void console_set_paging_message(word message: r0);  
Purpose: Set the paging message or disable paging.  
Call address: $FED5

**Description:** The console can halt printing after a full screen height worth of text has been printed. It will then show a message, wait for any key, and continue printing. This function sets this message. A zero-terminated text is passed in r0. To turn off paging, call this function with r0 = 0 - this is the default.

**Note:** It is possible to use control codes to change the text style and color. Do not use codes that change the cursor position, like CR or LF. Also, the text must not overflow one line on the screen.

---

### Other

\$FF81: `CINT` - reset screen/keyboard to defaults  
\$FF84: `IOINIT` - reset serial state and IRQ sources to defaults  
\$FF47: `enter_basic` - enter BASIC  
\$FECF: `entropy_get` - get 24 random bits  
\$FEAB: `extapi` - extended API  
\$FECC: `monitor` - enter machine language monitor  
\$FF5F: `screen_mode` - get/set screen mode  
\$FF62: `screen_set_charset` - activate 8x8 text mode charset  
\$FFED: `SCREEN` - get the text resolution  

---

#### Function Name: CINT

Purpose: Reset screen/keyboard to defaults  
Call address: $FF81  
Communication registers: None  
Preparatory routines: None  
Error returns: None  

**Description:** This routine is implicitly called by the system under these circumstances (after calling IOINIT):
* At system powerup
* When NMI is encountered and the default handler is in place
* When BRK is encountered and the default handler is in place

This routine takes no arguments.

The routine does the following:
* Sets up the VERA for VSYNC interrupts and disables other kinds of VERA interrupts
* Resets the default channel I/O output to screen
* Resets the default channel I/O input to keyboard/screen
* Downloads the default PETSCII upper/graph character set to the character set space in VRAM
* Downloads the default system palette to VERA
* Sets up sane defaults for the VERA layers and sprites
* Applies screen preferences (output, resolution, mode) from the active NVRAM profile
* Applies the preferred keyboard layout (KEYMAP) from NVRAM if it exists, otherwise restores to the emulator-given `-layout` parameter, otherwise as a final fallback, restores to `ABC/X16`.
* Applies the preferred typematic (key repeat) parameters from NVRAM.
* Sets up initial KERNAL editor state, including default F-key macros.
* Clears the screen as if the user pressed Shift+HOME/CLR


---

#### Function Name: IOINIT

Purpose: Reset serial state and IRQ sources to defaults  
Call address: $FF84  
Communication registers: None  
Preparatory routines: None  
Error returns: None  

**Description:** This routine is implicitly called by the system under these circumstances:
* At system powerup
* When NMI is encountered and the default handler is in place
* When BRK is encountered and the default handler is in place

This routine takes no arguments.

The routine does the following:
* Waits for the VERA to accept register writes
* Disables the interrupt sources on the VERA, VIA#1, VIA#2, and YM2151
* Sets the values and data direction of the IEC pins on VIA#1 to defaults
* Sets the VIA#1 timer T1 reload value to max ($FFFF) and puts it into freerunning mode for use as an entropy source
* Sets up the VERA for VSYNC interrupts

---

#### Function Name: enter_basic

Purpose: Enter BASIC  
Call address: $FF47  
Communication registers: .P  
Preparatory routines: None  
Error returns: Does not return  

**Description:** Call this to enter BASIC mode, either through a cold start (c=1) or a warm start (c=0).

**EXAMPLE:**

```ASM
CLC
JMP enter_basic ; returns to the "READY." prompt
```

---

#### Function Name: entropy_get

Purpose: Get 24 random bits  
Call address: $FECF  
Communication registers: .A .X .Y  
Preparatory routines: None  
Error returns: None  
Registers affected: .A .X .Y  

**Description:** This routine returns 24 somewhat random bits in registers .A, .X, and .Y. In order to get higher-quality random numbers, this data should be used to seed a pseudo-random number generator, as this is not a proper high quality pseudo-random number generator in and of itself.

**How to Use:**

1) Call this routine.

**EXAMPLE:**

```ASM
    ; throw a die
    again:
      JSR entropy_get
      STX tmp   ; combine 24 bits
      EOR tmp   ; using exclusive-or
      STY tmp   ; to get a higher-quality
      EOR tmp   ; 8 bit random value
      STA tmp
      LSR
      LSR
      LSR
      LSR       ; combine resulting 8 bits
      EOR tmp   ; to get 4 bits
      AND #7    ; we're down to values 0-7
      CMP #0
      BEQ again ; 0 is illegal
      CMP #7
      BEQ again ; 7 is illegal
      ORA #$30  ; convert to ASCII
      JMP $FFD2 ; print character
```

---
#### Function Name: extapi
Purpose: Additional API functions  
Minimum ROM version: R47  
Call address: $FEAB  
Communication registers: .A .X .Y .P  
Preparatory routines: None  
Error returns: Varies, but usually c=1  
Registers affected: Varies  

**Description:** This API slot provides access to various extended calls. The call is selected by the .A register, and each call has its own register use and return behavior.

| Call # | Name                  | Description                          | Inputs     | Outputs  | Preserves |
| -------|-----------------------|--------------------------------------|------------|----------|-----------|
| `$01` | [`clear_status`](#extapi-function-name-clear_status) | resets the KERNAL IEC status to zero | none | none | - |
| `$02` | [`getlfs`](#extapi-function-name-getlfs) | getter counterpart to setlfs | none | .A .X .Y | - |
| `$03` | [`mouse_sprite_offset`](#extapi-function-name-mouse_sprite_offset) | get or set mouse sprite pixel offset | r0 r1 .P | r0 r1 | - |
| `$04` | [`joystick_ps2_keycodes`](#extapi-function-name-joystick_ps2_keycodes) | get or set joy0 keycode mappings | r0L-r6H .P | r0L-r6H  | - |
| `$05` | [`iso_cursor_char`](#extapi-function-name-iso_cursor_char) | get or set the ISO mode cursor char | .X .P | .X | - |
| `$06` | [`ps2kbd_typematic`](#extapi-function-name-ps2kbd_typematic) | set the keyboard repeat delay and rate | .X | - | - |
| `$07` | [`pfkey`](#extapi-function-name-pfkey) | program macros for F1-F8 and the RUN key | .X | - | - |
| `$08` | [`ps2data_fetch`](#extapi-function-name-ps2data_fetch) | Polls the SMC for PS/2 keyboard and mouse data | - | - | - |
| `$09` | [`ps2data_raw`](#extapi-function-name-ps2data_raw) | If the most recent `ps2data_fetch` received a mouse packet or keycode, returns its raw value | - | .A .Y .X .P r0L-r1H | - |
| `$0A` | [`cursor_blink`](#extapi-function-name-cursor_blink) | Blinks or un-blinks the KERNAL editor cursor if appropriate | - | - | - |
| `$0B` | [`led_update`](#extapi-function-name-led_update) | Illuminates or clears the SMC activity LED based on disk activity or error status | - | - | - |
| `$0C` | [`mouse_set_position`](#extapi-function-name-mouse_set_position) | Moves the mouse cursor to a specific X/Y location | .X (.X)-(.X+3) | - | - |
| `$0D` | [`scnsiz`](#extapi-function-name-scnsiz) | Directly sets the kernal editor text dimensions | .X .Y | - | - |
| `$0E` | [`kbd_leds`](#extapi-function-name-kbd_leds) | Set or get the state of the PS/2 keyboard LEDs | .X .P | .X | - |
| `$0F` | [`memory_decompress_from_func`](#extapi-function-name-memory_decompress_from_func) | Decompresses LZSA2 data streamed by a function | r1 r4 | r1 | r4 |
| `$10` | [`default_palette`](#extapi-function-name-default_palette) | Get or upload the default palette | .P | .A .X .Y | - |
| `$11` | [`has_machine_property`](#extapi-function-name-has_machine_property) | Checks for machine environment property | .X | .P | - |
| `$12` | [`kbdbuf_get`](#extapi-function-name-kbdbuf_get) | Fetches a character code from the keyboard buffer | - | .A | - |
| `$13` | [`kbdbuf_clear`](#extapi-function-name-kbdbuf_clear) | Purges the keyboard buffer | - | - | - |
| `$14` | [`blink_enable`](#extapi-function-name-blink_enable) | Enables or disables the blinking cursor | .X | - | - |


---

####  extapi Function Name: clear_status

Purpose: Reset the IEC status byte to 0  
Minimum ROM version: R47  
Call address: $FEAB, .A=1  
Communication registers: none  
Preparatory routines: none  
Error returns: none  
Registers affected: .A  

**Description:** This function explicitly clears the IEC status byte. This is the value which is returned by calling `readst`.

---

####  extapi Function Name: getlfs

Purpose: Return the values from the last call to `setlfs`  
Minimum ROM version: R47  
Call address: $FEAB, .A=2  
Communication registers: .A .X .Y  
Preparatory routines: none  
Error returns: none  
Registers affected: .A .X .Y  

**Description:** This function returns the values from the most recent call to `setlfs`. This is most useful for fetching the most recently-used disk device.

**EXAMPLE:**

```ASM
LOADFILE:
    ; getlfs returns the most recently used disk device (`fa`) in .X
    ; Also returns `la` in .A and `sa` in .Y, but we ignore those
    LDA #2    ; extapi:getlfs
    JSR $FEAB ; extapi
    LDA #1
    LDY #2
    JSR $FFBA ; SETLFS
    LDA #FNEND-FN
    LDX #<FN
    LDY #>FN
    JSR $FFBD ; SETNAM
    LDA #1
    STA $00   ; ram_bank
    LDA #0
    LDX #<$A000
    LDY #>$A000
    JSR $FFD5 ; LOAD
    RTS
FN:
    .byte "MYFILENAME.EXT"
FNEND = *
```

---

#### extapi Function Name: mouse_sprite_offset

Purpose: Set the mouse sprite x/y offset  
Minimum ROM version: R47  
Call address: $FEAB, .A=3  
Communication registers: r0 r1  
Preparatory routines: `mouse_config`  
Error returns: none  
Registers affected: .A .X .Y .P r0 r1

**Description:** This function allows you to set or retrieve the display offset of the mouse sprite, relative to the calculated mouse position. Setting it negative can be useful for mouse sprites in which the locus is not the upper left corner. Combined with configuring a smaller X/Y with mouse_config, it can be set positive to confine the mouse pointer to a limited region of the screen.

* Set: If carry is clear when called, the X and Y sprite offsets are configured from the values in r0 and r1 respectively.
* Get: If carry is set when called, the X and Y sprite offsets are retrieved and placed in r0 and r1 respectively.

**How to Use:**

1) Set up your mouse sprite and call `mouse_config`. Any call to `mouse_config` resets this offset.
2) Load r0 with the 16-bit X offset and r1 with the 16-bit Y offset. Most of the time these values will be negative. For instance, a 16x16 sprite pointer in which the locus is near the center would have an offset of -8 ($FFF8) on both axes.
3) Clear carry and call `mouse_sprite_offset`

**EXAMPLE:**

```ASM
  ; configure your mouse sprite here

  ; configure mouse before setting offset
  LDA #$FF
  LDY #0
  LDX #0
  JSR $FF68 ; mouse_config (resets sprite offsets to zero)

  LDA #<(-8)
  STA r0L
  STA r1L
  LDA #>(-8)
  STA r0H
  STA r1H
  LDA #3    ; mouse_sprite_offset
  CLC
  JSR $FEAB ; extapi
```

---

#### extapi Function Name: joystick_ps2_keycodes

Purpose: Set or get the keyboard mapping for joystick 0  
Minimum ROM version: R47  
Call address: $FEAB, .A=4  
Communication registers: .P r0L-r6H  
Preparatory routines: none  
Error returns: none  
Registers affected: .A .X .Y .P r0L-r6H

**Description:** This function allows you to set or retrieve the list of keycodes that are mapped to joystick 0

* Set: If carry is clear when called, the current values are set based on the contents of the 14 registers r0L-r6H.
* Get: If carry is set when called, the current values are retrieved and placed in the 14 registers r0L-r6H.

| Register | Controller Input | Default                  |
|----------|------------------|--------------------------|
| r0L      | D-pad Right      | KEYCODE_RIGHTARROW ($59) |
| r0H      | D-pad Left       | KEYCODE_LEFTARROW ($4F)  |
| r1L      | D-pad Down       | KEYCODE_DOWNARROW ($54)  |
| r1H      | D-pad Up         | KEYCODE_UPARROW ($53)    |
| r2L      | Start            | KEYCODE_ENTER ($2B)      |
| r2H      | Select           | KEYCODE_LSHIFT ($2C)     |
| r3L      | Y                | KEYCODE_A ($1F)          |
| r3H      | B                | KEYCODE_Z ($2E)          |
| r4L      | B                | KEYCODE_LALT ($3C)       |
| r4H      | R                | KEYCODE_C ($30)          |
| r5L      | L                | KEYCODE_D ($21)          |
| r5H      | X                | KEYCODE_S ($20)          |
| r6L      | A                | KEYCODE_X ($2F)          |
| r6H      | A                | KEYCODE_LALT ($3C)       |

* Note that there are two mappings for the controller button B, and two mappings for the controller button A. Both mapped keys will activate the controller button.

**How to Use:**

1) Unless you're replacing the entire set of mappings, call `joystick_ps2_keycodes` first with carry set to fetch the existing values into r0L-r6H.
2) Load your desired changes into r0L-r6H. The keycodes are enumerated [here](https://github.com/X16Community/x16-rom/blob/master/inc/keycode.inc), and their names, similar to that of PS/2 codes, are based on their function in the ___US layout___.  You can also disable a mapping entirely with the value 0.

3) Clear carry and call `joystick_ps2_keycodes`

**EXAMPLE:**

```ASM
  ; first fetch the original values
  LDA #4    ; joystick_ps2_keycodes
  SEC       ; get values
  JSR $FEAB ; extapi
  LDA #$10  ; KEYCODE_TAB
  STA r2H   ; Tab is to be mapped to the select button
  STZ r4L   ; Disable the secondary B button mapping
  STZ r6H   ; Disable the secondary A button mapping
  LDA #4    ; joystick_ps2_keycodes
  CLC       ; set values
  JSR $FEAB ; extapi (brings the new mapping into effect)
```

---

#### extapi Function Name: iso_cursor_char

Purpose: get or set the ISO mode cursor character  
Minimum ROM version: R47  
Call address: $FEAB, .A=5  
Communication registers: .X .P  
Preparatory routines: none  
Error returns: none  
Registers affected: .A .X .Y .P  

**Description:** This function allows you to set or retrieve the cursor screen code which is used in ISO mode.

* Set: If carry is clear when called, the current value of .X is used as the blinking cursor character if the screen console is in ISO mode.
* Get: If carry is set when called, the current value of the blinking cursor character is returned in .X.

When entering ISO mode, such as by sending a `$0F` to the screen via `BSOUT` or pressing Ctrl+O, the cursor character is reset to the default of `$9F`.

---

#### extapi Function Name: ps2kbd_typematic

Purpose: set the PS/2 typematic delay and repeat rate  
Minimum ROM version: R47  
Call address: $FEAB, .A=6  
Communication registers: .X  
Preparatory routines: none  
Error returns: none  
Registers affected: .A .X .Y .P  

**Description:** This function allows you to set the delay and repeat rate of the PS/2 keyboard. Since the keyboard doesn't allow you to query the current value, there is no getter counterpart to this routine.

NOTE: Since the SMC communicates with the keyboard using PS/2 scancode set 2, there is no way to instruct the keyboard to turn off typematic repeat entirely. However, with a very simple custom KERNAL key handler, you can suppress processing repeated key down events without an intervening key up.

NOTE: **This routine does not work with the emulator**, as the key repeat rate is controlled by the operating system.

This function takes 7 bits of input in .X, a bitfield composed of two parameter options.

* .X = 0ddrrrrr

Where dd is the delay before repeating,

* dd = 00: 250 ms
* dd = 01: 500 ms
* dd = 10: 750 ms
* dd = 11: 1000 ms

and rrrrr is the repeat rate, given this conversion to Hz.

```
 $00 = 30.0 Hz, $01 = 26.7 Hz, $02 = 24.0 Hz, $03 = 21.8 Hz
 $04 = 20.7 Hz, $05 = 18.5 Hz, $06 = 17.1 Hz, $07 = 16.0 Hz
 $08 = 15.0 Hz, $09 = 13.3 Hz, $0a = 12.0 Hz, $0b = 10.9 Hz
 $0c = 10.0 Hz, $0d =  9.2 Hz, $0e =  8.6 Hz, $0f =  8.0 Hz
 $10 =  7.5 Hz, $11 =  6.7 Hz, $12 =  6.0 Hz, $13 =  5.5 Hz
 $14 =  5.0 Hz, $15 =  4.6 Hz, $16 =  4.3 Hz, $17 =  4.0 Hz
 $18 =  3.7 Hz, $19 =  3.3 Hz, $1a =  3.0 Hz, $1b =  2.7 Hz
 $1c =  2.5 Hz, $1d =  2.3 Hz, $1e =  2.1 Hz, $1f =  2.0 Hz
```

---

#### extapi Function Name: pfkey

Purpose: Reprogram a function key macro  
Minimum ROM version: R47  
Call address: $FEAB, .A=7  
Communication registers: .X .Y r0  
Preparatory routines: None  
Error returns: c=1  
Registers affected: .A .X .Y .P r0  

**Description:** This routine can be called to replace an F-key macro in the KERNAL editor with a user-defined string. The maximum length of each macro is 10 bytes, matching the size of the X16 KERNAL's keyboard buffer. It can also replace the action of SHIFT+RUN with a user-defined action.

These macros are only available in the KERNAL editor, which is usually while editing BASIC program, or during a BASIN from the screen. The BASIC statements INPUT and LINPUT also operate in this mode.

Inputs:
* r0 = pointer to string
* .X = key number (1-9)
* .Y = string length

**How to Use:**

1) Load r0L and r0H a pointer to the replacement macro string (ZP locations $02 and $03).
2) Load .X with the key number to replace. Values 1-8 correspond to F1-F8. A value of 9 corresponds to SHIFT+RUN.
3) Load .Y with the string length. This may be a range from 0-10 inclusive. A value of 0 disables the macro entirely.
4) Call `pfkey`. If carry is set when returning, an error occurred. The most likely reason is that one of the input parameters was out of range.

**EXAMPLE:**

Disable the SHIFT+RUN action, and replace the macro in F1 with "HELP" followed by a carriage return.

```ASM
EXTAPI = $FEAB

change_fkeys:
  lda #<string1
  sta $02
  lda #>string1
  sta $03
  lda #$02
  ldx #1
  ldy #<(string1_end-string1)
  jsr EXTAPI
  lda #<string9
  sta $02
  lda #>string9
  sta $03
  lda #7
  ldx #9
  ldy #<(string9_end-string9)
  jsr EXTAPI
  rts

string1: .byte "HELP",13
string1_end:
string9:
string9_end:
```

BASIC equivalent:

```BASIC
10 A$="HELP"+CHR$(13)
20 K=1
30 GOSUB 100
40 A$=""
50 K=9
60 GOSUB 100
70 END
100 AL=LEN(A$)
110 AP=STRPTR(A$)
120 POKE $02,(AP-(INT(AP/256)*256))
130 POKE $03,INT(AP/256)
140 POKE $30C,7
150 POKE $30D,K
160 POKE $30E,AL
170 SYS $FEAB
180 RETURN
```

---

#### extapi Function Name: ps2data_fetch

Purpose: Poll the SMC for PS/2 events  
Minimum ROM version: R47  
Call address: $FEAB, .A=8  
Communication registers: None  
Preparatory routines: None  
Error returns: None  
Registers affected: .A .X .Y .P  

**Description:** This routine is called from the default KERNAL interrupt service handler to fetch a queued keycode, and if the mouse is enabled, a mouse packet. The values are stored inside internal KERNAL state used by subsequent calls to `mouse_scan`, `kbd_scan`, or `ps2data_raw`.

If the mouse has not been enabled via `mouse_config`, no mouse data is polled.

This call is mainly useful when overriding the default KERNAL IRQ handler, and since this function is not re-entrant safe, it is unsafe to call outside of an interrupt handler if interrupts are enabled and the default KERNAL IRQ handler is in place.

---

#### extapi Function Name: ps2data_raw

Purpose: Return the most recently-fetched PS/2 mouse packet and keycode  
Minimum ROM version: R47  
Call address: $FEAB, .A=9  
Communication registers: .A .Y .X .P r0L-r1H  
Preparatory routines: `mouse_config`, `ps2data_fetch`  
Error returns: None  
Registers affected: .A .X .Y .P r0L-r1H  

**Description:** This routine returns the most-recently fetched mouse data packet and keycode. If a mouse packet exists, it sets .X to the length of the packet, either 3 or 4 depending on mouse type, and stores the values into r0L-r1H. If there's no mouse packet to return, .X is set to zero. If there's a keycode to return, .A is set to the keycode, otherwise .A is set to zero. If there's an extended keycode, .A will equal $7F for key down or $FF for key up, and .Y will contain the extended code.

If .X = 0, no mouse packet was received, and r0L-r1H memory is unchanged.

If the zero flag is set, neither the keyboard nor mouse had pending events.

This call is mainly useful when overriding the default KERNAL ISR and implementing a fully custom mouse and keyboard routine.  It is also available when using the default ISR as these values are kept even after processing, until the next `ps2data_fetch` call.

Return values:

##### Keyboard

* .A = keycode

If .A == $7F or .A == $FF

* .Y = extended keycode

##### Mouse

* .X = number of mouse bytes

If .X == 0, memory is left unchanged.

If .X >= 3

* r0L = mouse byte 1
* r0H = mouse byte 2
* r1L = mouse byte 3

If .X == 4

* r1H = mouse byte 4

**How to Use:**

1) Call `mouse_config` with a non-zero value to enable the mouse.
2) If you're overriding the default KERNAL IRQ handler entirely, call `ps2data_fetch`. If not, this will be called for you.
3) Call `ps2data_raw`. If .X is nonzero upon return, memory starting at r0L will contain the raw mouse packet.

**EXAMPLE:**

```ASM
CHROUT = $FFD2
STOP = $FFE1
EXTAPI = $FEAB
MOUSE_CONFIG = $FF68
SCREEN_MODE = $FF5F

TMP1 = $22
r0 = $02

start:
        sec
        jsr SCREEN_MODE ; get the screen size to pass to MOUSE_CONFIG
        lda #1
        jsr MOUSE_CONFIG
loop:
        wai ; wait for interrupt
        lda #9 ; ps2data_raw
        jsr EXTAPI
        beq aftermouse
        stx TMP1
        ora #0
        beq afterkbd
        jsr print_hex_byte
        lda #13
        jsr CHROUT
afterkbd:
        ldx TMP1
        beq aftermouse
        ldx #0
printloop:
        lda r0,x
        phx
        jsr print_hex_byte
        plx
        inx
        cpx TMP1
        bne printloop
        lda #13
        jsr CHROUT
aftermouse:
        jsr STOP
        bne loop
done:
        rts

print_hex_byte:
        jsr byte_to_hex
        jsr CHROUT
        txa
        jsr CHROUT
        rts

byte_to_hex:
        pha
        and #$0f
        tax
        pla
        lsr
        lsr
        lsr
        lsr
        pha
        txa
        jsr @hexify
        tax
        pla
@hexify:
        cmp #10
        bcc @nothex
        adc #$66
@nothex:
        eor #%00110000
        rts

```

---
#### extapi Function Name: cursor_blink

Purpose: Blink or un-blink the cursor in the KERNAL editor  
Minimum ROM version: R47  
Call address: $FEAB, .A=10  
Communication registers: None  
Preparatory routines: None  
Error returns: None  
Registers affected: .A .X .Y .P  

**Description:** This routine is called from the default KERNAL interrupt service handler to cause the text mode cursor to blink on or off as appropriate, depending on the number of times this function has been called since the last blink event. If the editor is not waiting for input, this function has no effect.

This call is mainly useful when overriding the default KERNAL IRQ handler.

---

#### extapi Function Name: led_update

Purpose: Set the illumination status of the SMC's activity LED based on disk status  
Minimum ROM version: R47  
Call address: $FEAB, .A=11  
Communication registers: None  
Preparatory routines: None  
Error returns: None  
Registers affected: .A .X .Y .P  

**Description:** This routine is called from the default KERNAL IRQ handler to update the status of the SMC's activity LED based on CMDR-DOS's status flags. It is illuminated solid during DOS disk activity, and flashes when there was a disk error.

This call is mainly useful when overriding the default KERNAL IRQ handler.

---

#### extapi Function Name: mouse_set_position

Purpose: Move the mouse pointer to an absolute X/Y position  
Minimum ROM version: R47  
Call address: $FEAB, .A=12  
Communication registers: .X (.X)-(.X+3)  
Preparatory routines: `mouse_config`  
Error returns: None  
Registers affected: .A .X .Y .P  

**Description:** This routine set the absolute position of the mouse pointer and updates the pointer sprite.

Inputs:
* .X = the zeropage location from which to read the new values
* $00+X = X position low byte
* $01+X = X position high byte
* $02+X = Y position low byte
* $03+X = Y position high byte

For instance, if you want the function to read the values from memory locations $22 through $25, set .X to #$22.

**How to Use:**

1) Call `mouse_config` with a non-zero value to enable the mouse.
2) Store the new X/Y position in four contiguous zeropage locations as described above. Load .X with the starting zeropage location.
3) Call `mouse_set_position`

**EXAMPLE:**

This demo program causes the mouse pointer to slowly drift down and to the right.

```ASM
r0L = $02
r0H = $03
r1L = $04
r1H = $05

EXTAPI = $FEAB
MOUSE_CONFIG = $FF68
MOUSE_GET = $FF6B
SCREEN_MODE = $FF5F
STOP = $FFE1

start:
        sec
        jsr SCREEN_MODE
        lda #1
        jsr MOUSE_CONFIG
loop:
        ldx #r0L ; starting ZP location for mouse_get
        jsr MOUSE_GET
        inc r0L
        bne :+
        inc r0H
:       inc r1L
        bne :+
        inc r1H
:
        ldx #r0L ; starting ZP location for mouse_set_position
        lda #12 ; mouse_set_position
        jsr EXTAPI
        wai ; delay until next interrupt
        jsr STOP
        bne loop
done:
        rts

```
---

#### extapi Function Name: scnsiz

Purpose: Set the number of text rows and columns for the kernal screen editor  
Minimum ROM version: R48  
Call address: $FEAB, .A=13  
Communication registers: .X .Y  
Preparatory routines: None  
Error returns: c=1  
Registers affected: .A .X .Y .P  

**Description:** This routine is implicitly called by `screen_mode` to set the bounds of the kernal editor's screen, and can be used directly to change the row and column bounds of the screen editor. `scnsiz` does not change the screen scaling.

This call is mainly useful to set custom row and column counts not available from any built-in screen mode.

Due to limits within the KERNAL's editor and what screen sizes it expects to work with, this routine will error and return with carry set if:
* .X &lt; 20
* .X &gt; 80
* .Y &lt; 4
* .Y &gt; 60

If the requested size exceeds the allowed bounds (.X = 20-80, .Y = 4-60), the existing text resolution won't be changed.

**How to Use:**

1) Set .X to the number of desired columns and .Y to the desired number of rows.
2) Call `scnsiz`
3) The in-bounds area of the screen as defined by these new dimensions will be cleared and the cursor will be placed at the upper-left home position.

**EXAMPLE:**

This example assembly routine sets up an 80x25 region, also adding top and bottom border regions so that the viewable area only shows the 80x25 text region.

```ASM

SCREEN_MODE = $FF5F
EXTAPI = $FEAB
E_SCNSIZ = $0D
VERA_CTRL = $9F25
VERA_DC_VSTART = $9F2B
VERA_DC_VSTOP = $9F2C

TOP = 20 ; 20 rows from the top
BOTTOM = 480-20 ; 20 rows from the bottom

do_80x25:
        lda #1
        clc
        jsr SCREEN_MODE ; set screen mode to 80x30, which also clears the screen
        ldx #80
        ldy #25
        lda #E_SCNSIZ
        jsr EXTAPI ; reset to 80x25
        lda #(1 << 1) ; DCSEL = 1
        sta VERA_CTRL
        lda #(TOP >> 1) ; each step in DC_VSTART is 2 pixel rows
        sta VERA_DC_VSTART
        lda #(BOTTOM >> 1) ; each step in DC_VSTOP is 2 pixel rows
        sta VERA_DC_VSTOP
        stz VERA_CTRL
        rts
```

---

#### extapi Function Name: kbd_leds

Purpose: Set or retrieve the PS/2 keyboard LED state  
Minimum ROM version: R48  
Call address: $FEAB, .A=14  
Communication registers: .X .P  
Preparatory routines: None  
Error returns: (none)  
Registers affected: .A .X .Y .P  

**Description:** This routine is used to send a command to the keyboard to set the state of the Num Lock, Caps Lock, and Scroll Lock LEDs. You can also query the KERNAL for its idea of what the state of the LEDs is.

Note: This call does **not** change the state of the kernal's caps lock toggle.

**How to Use:**

1) To query the state of the LEDs, set carry, otherwise to set the LED state, clear carry and set .X to the desired value of the LED register. Bit 0 is Scroll Lock, bit 1 is Num Lock, and bit 2 is Caps Lock.
2) Call `kbd_leds`
3) If carry was set on the call to `kbd_leds`, the routine will return with .X set to the current state, otherwise the routine will send the updated LED state to the keyboard. In this case, there will be no confirmation on whether it was successful.

**EXAMPLE:**

This example toggles the state of the LEDs to the opposite state that they were initially.

```ASM

EXTAPI = $FEAB
E_KBD_LEDS = $0E

flip_leds:
        sec
        lda #E_KBD_LEDS
        jsr EXTAPI ; fetch state
        txa
        eor #7 ; invert the LED state
        tax
        clc
        lda #E_KBD_LEDS
        jsr EXTAPI ; set state and send to keyboard
        rts
```

---

#### extapi Function Name: memory_decompress_from_func

Purpose: Decompress LZSA2 data  
Minimum ROM version: R49  
Call address: $FEAB, .A=15  
Communication registers: r1 r4  
Preparatory routines: None  
Error returns: (none)  
Registers affected: .A .X .Y .P r1  

**Description:** This function works the same way as the regular [`memory_decompress`](#function-name-memory_decompress), but instead of taking a memory address where the LZSA2 data to decompress is located via the `r0` register, it takes an address (passed in `r4`) of a user-defined function that returns LZSA2 data byte by byte. This might be useful for decompressing data from IO devices or Cartridges.

**How to Use:**

1) Design a function that streams LZSA2 data and pass its address to `r4`.
2) Pass a target address to `r1`. If you're decompressing to VRAM, don't forget to set the `VERA_ADDR` registers to the address you want decompressed data to land into.
3) Call `memory_decompress_from_func`

##### LZSA2 Streaming function

In order to use `memory_decompress_from_func`, you obviously have to design a function, that you can provide to the decompressing routine. It should preferably be located in low-ram (it ***may not*** be on a cartridge, it probably can be located in high-ram though, if the decompressed data destination is somewhere else). There are some prerequisites for such a function you need to apply:

- It returns bytes of LZSA2 each call byte by byte via `.A` register. That is, for example, if your LZSA2 data starts with `.byte $65, $02, $66, $55, $00, $22 ...`, your function has to return `$65` of the first call, `$02` on the 2nd, `$66` on the 3rd one and so on.
- It shouldn't fail &ndash; decompressor always assumes that the LZSA fetching function was successful in obtaining data upon returning. There isn't *any* kind of way of informing the decompressor, that the fetcher failed. In case the possibility of the function failing is inavoidable, `BRK` is probably the only possible way you could handle that.
- It **HAS TO** preserve the values of `.X`, `.Y`, `r1`, `r2`, `r3` registers.
- the same applies to VERA registers (both data ports are used by the decompressor) if VRAM is the target.
- The ROM bank must be set to 0 upon returning.
- If you plan to output decompressed data to High-RAM, you should restore the RAM bank upon returning too (you shouldn't set it to constant value, but instead use the value that was there upon entering the function &ndash; this will make it more futureproof against newer kernal versions that may feature a banked output of `memory_decompress`).
- You're free to use **any KERNAL routines you want** inside of it, just remember to restore the stuff mentioned above before returning to the decompressor.

**EXAMPLE:**

In this example, data is decompressed directly from an opened file. Note however, that this particular implementation is pretty slow and instead you should consider designing a better data-fetching function.

```ASM
r1 = $04
r4 = $0a

EXTAPI = $FEAB
GETIN = $FFE4
SETNAM = $FFBD
SETLFS = $FFBA
OPEN = $FFC0
CHKIN = $FFC6
CLOSE = $FFC3
CLRCHN = $FFCC

    ; prepare the file
        lda #filename_len
        ldx #<filename
        ldy #>filename
        jsr SETNAM
        lda #1
        ldx #8
        ldy #2
        jsr SETLFS
        jsr OPEN
        ldx #1
        jsr CHKIN

    ; run decompression
        lda #A0
        sta r1+1
        stz r1
        lda #<fetch_from_file
        sta r4
        lda #>fetch_from_file
        sta r4+1
        lda #15 ; extapi id
        jsr EXTAPI

    ; cleanup
        jsr CLRCHN
        lda #1
        jmp CLOSE



fetch_from_file:
        phy
        phx
        jsr GETIN
        plx
        ply
        rts

filename: .byte "data.lzsa"
filename_len = *-filename
```

---

#### extapi Function Name: default_palette
Purpose: Get or upload the default palette  
Minimum ROM version: R49  
Call address: $FEAB, .A=16  
Communication registers: .A .X .Y .P  
Preparatory routines: None  
Error returns: (none)  
Registers affected: .A .X .Y .P  

**Description:** This routine returns the bank and address of the default palette or uploads the default palette to the VERA.

**How to Use:**

1) To query the default palette's bank and address, set carry. To upload the default palette to the VERA, clear carry.
2) Call `default_palette`.
3) If carry was set on the call to `default_palette`, the routine will return with .A set to the ROM bank containing the palette, .X set to the low byte of the palette address and .Y set to the high byte of the palette address. If carry was clear, the routine will upload the default palette to the VERA.

---

#### extapi Function Name: has_machine_property
Purpose: Check whether the current machine environment has a specific capability or property  
Minimum ROM version: R49  
Call address: $FEAB, .A=17  
Communication registers: .A .X .P  
Preparatory routines: None  
Error returns: (none)  
Registers affected: .A .X .P  

**Description:** This routine takes the input parameter .X, and returns with carry set if the current environment has the property represented by the input value.

The valid input values for .X are as follows:

| Numeric value | Name                         | Description                       |
|---------------|------------------------------|-----------------------------------|
| $00           | MACHINE_PROPERTY_C816        | Running with a 65C816 processor   |
| $01           | MACHINE_PROPERTY_FAR         | Has a 65C816 and a 24-bit memory model and separate memory at addresses >= $010000 |
| $02           | MACHINE_PROPERTY_GSIO        | Not yet implemented: X16 GS I/O semantics at addresses $9F5x |
| $03           | MACHINE_PROPERTY_SHAREDBANK  | Not yet implemented: Banked RAM at $A000 is shared with memory >= $010000 |
| $04           | MACHINE_PROPERTY_BANKMIRROR  | Banked RAM loops every 512KiB. Some X16 clones exhibit this behavior when configured with only 512KiB of high RAM. |


**How to Use:**

1) Set .X to a property you're interested in querying
2) Call `has_machine_property`
3) Check the carry flag to see if the current environment has that property.

**EXAMPLE:**

This example shows a potential check for a game which needs a 65C816 processor, as well as having 24-bit memory accessible at >= $010000.

```ASM

EXTAPI = $FEAB

.setcpu "65816"
    ; instead of using the `has_machine_property` to check for
    ; the presence of a 65C816, it is faster and uses fewer code
    ; bytes to do it this way.  On the 65C02, the SEP opcode
    ; is a two-byte NOP.  In the interest of making it compatible
    ; with older emulators that erroneously treat the SEP opcode
    ; as a single-byte NOP, we can use $03 as the value, which if
    ; treated as an opcode, is itself a one-byte NOP, so we choose
    ; this instead of $01.
    ;
    ; sets carry (and z) if running under a 65C816, otherwise
    ; carry is left clear on the 65C02.
    clc
    sep #$03
    bcc @c02

    lda #17
    ldx #$01 ; MACHINE_PROPERTY_FAR
    jsr EXTAPI
    bcc @nofar

    jmp init_game
@nofar:
    ; tell the user that the system is unsupported because it doesn't have the memory model we need.
    rts

@c02
    ; tell the user that the system is unsupported because it's not a 65C816
    rts

```

---

#### extapi Function Name: kbdbuf_get
Purpose: Fetches a character code from the keyboard buffer  
Minimum ROM version: R49  
Call address: $FEAB, .A=18  
Communication registers: .A .P  
Preparatory routines: None  
Error returns: (none)  
Registers affected: .A .X .Y .P  

**Description:** This routine behaves identically to GETIN while the input device is the keyboard.
However, it has the advantage of being able to fetch a character from the keyboard buffer while reading
from a file, unlike GETIN which requires you to call CLRCHN to switch away from the file first.

---

#### extapi Function Name: kbdbuf_clear
Purpose: Purges any queued character codes in the keyboard buffer  
Minimum ROM version: R49  
Call address: $FEAB, .A=19  
Communication registers: .A .P  
Preparatory routines: None  
Error returns: (none)  
Registers affected: .A .P  

**Description:** Calling this function will immediately empty the keyboard buffer.

Prior to this function being available, the typical method of purging the buffer was to call GETIN repeatedly until it returned 0.

---

#### extapi Function Name: blink_enable
Purpose: Enables or disables the blinking KERNAL cursor
Minimum ROM version: R49  
Call address: $FEAB, .A=20  
Communication registers: .A .X .P  
Preparatory routines: None  
Error returns: (none)  
Registers affected: .A .X .P  

**Description:** The cursor blink enable flag is normally only controlled by the BASIN/CHRIN function.  However, user programs
may want to enable the blinking cursor at other times without implementing their own cursor routine.  Calling this function with .X = 0
will enable the blinking cursor.  Calling with .X set to any other value will disable.

This setting is _not_ persistent and will not prevent CHRIN from enabling the cursor blink if it is called afterwards.
It's mainly useful for custom text input while showing a blinking cursor.

This function is similar to the effect of user programs modifying the contents of memory location $CC on the C64.
This function also takes care to "unblink" the cursor when disabling, which restores the character cell back to the original glyph and color.

**How to Use:**

1) Set .X to 0 (to enable the blinking)
2) Call `blink_enable`
3) Run program code with cursor blinking
4) Set .X to 1 (to disable the blinking)
5) Call `blink_enable`, which makes sure the character under the cursor returns to the correct glyph and color.

**Notes:**
* If you wish to use BSOUT (CHROUT) or PLOT with an active blinking cursor, it is necessary that you disable the blink first, do the BSOUT or PLOT call, then re-enable the blinking.

---

#### Function Name: monitor

Purpose: Enter the machine language monitor  
Call address: $FECC  
Communication registers: None  
Preparatory routines: None  
Error returns: Does not return  
Registers affected: Does not return

**Description:** This routine switches from BASIC to machine language monitor mode. It does not return to the caller. When the user quits the monitor, it will restart BASIC.

**How to Use:**

1) Call this routine.

**EXAMPLE:**

```ASM
      JMP monitor
```

---

#### Function Name: SCREEN

Purpose: Get the text resolution of the screen  
Call address: $FFED  
Communication registers: .X, .Y  
Preparatory routines: None  
Error returns: None  
Registers affected: .A, .X, .Y, .P

**Description:** This routine returns the KERNAL screen editor's view of the text resolution. The column count is returned in .X and the row count is returned in .Y.

In contrast to calling [`screen_mode`](#function-name-screen_mode) with carry set, this function returns the configured resolution if ever it is updated by [`scnsiz`](#extapi-function-name-scnsiz). `screen_mode` only returns the text dimensions the currently configured mode would have configured, ignoring any changes made by calls to `scnsiz`.


**EXAMPLE:**

```ASM
SCREEN = $FFED

get_res:
        jsr SCREEN
        sty my_rows
        stx my_columns
        rts
```

---

#### Function Name: screen_mode

Purpose: Get/Set the screen mode  
Call address: $FF5F  
Communication registers: .A, .X, .Y, .P  
Preparatory routines: None  
Error returns: c = 1 in case of error  
Registers affected: .A, .X, .Y

**Description:** If c is set, a call to this routine gets the current screen mode in .A, the width (in tiles) of the screen in .X, and the height (in tiles) of the screen in .Y. If c is clear, it sets the current screen mode to the value in .A. 
For a list of possible values, see [Chapter 3: Editor](X16%20Reference%20-%2003%20-%20Editor.md#modes). If the mode is unsupported, c will be set, otherwise cleared.

If you use this function to get the text resolution instead of calling [`SCREEN`](#function-name-screen), this function only returns the text dimensions the currently configured mode would have set, ignoring any changes made by calls to [`scnsiz`](#extapi-function-name-scnsiz). If you want to fetch the KERNAL editor's text resolution, call [`SCREEN`](#function-name-screen) instead.

**EXAMPLE:**

```ASM
LDA #$80
CLC
JSR screen_mode ; SET 320x240@256C MODE
BCS FAILURE
```

---

#### Function Name: screen_set_charset

Purpose: Activate a 8x8 text mode charset  
Call address: $FF62

Communication registers: .A, .X, .Y  
Preparatory routines: None  
Registers affected: .A, .X, .Y

**Description:** A call to this routine uploads a character set to the video hardware and activates it. The value of .A decides what charset to upload:

| Value | Description                     |
|-------|---------------------------------|
| 0     | use pointer in .X/.Y            |
| 1     | ISO                             |
| 2     | PET upper/graph                 |
| 3     | PET upper/lower                 |
| 4     | PET upper/graph (thin)          |
| 5     | PET upper/lower (thin)          |
| 6     | ISO (thin)                      |
| 7     | CP437 (since r47)               |
| 8     | Cyrillic ISO (since r47)        |
| 9     | Cyrillic ISO (thin) (since r47) |
| 10    | Eastern Latin ISO (since r47)   |
| 11    | Eastern ISO (thin) (since r47)  |
| 12    | Katakana (thin) (since r48)     |

See [Appendix I](X16%20Reference%20-%20Appendix%20I%20-%20Character%20Sets.md#appendix-i-character-sets)  

If .A is zero, .X (lo) and .Y (hi) contain a pointer to a 2 KB RAM area that gets uploaded as the new 8x8 character set. The data has to consist of 256 characters of 8 bytes each, top to bottom, with the MSB on the left, set bits (1) represent the foreground colored pixels.

**EXAMPLE:**

```ASM
LDA #0
LDX #<MY_CHARSET
LDY #>MY_CHARSET
JSR screen_set_charset ; UPLOAD CUSTOM CHARSET "MY_CHARSET"
```

---

#### Function Name: JSRFAR

Purpose: Execute a routine on another RAM or ROM bank  
Call address: $FF6E  
Communication registers: None  
Preparatory routines: None  
Error returns: None  
Registers affected: None

**Description:** The routine `JSRFAR` enables code to execute some other code located on a specific RAM or ROM bank. This works independently of which RAM or ROM bank the currently executing code is residing in.
The 16 bit address and the 8 bit bank number have to follow the instruction stream. The `JSRFAR` routine will switch both the ROM and the RAM bank to the specified bank and restore it after the routine's `RTS`. Execution resumes after the 3 byte arguments.
**Note**: The C128 also has a `JSRFAR` function at $FF6E, but it is incompatible with the X16 version.

**How to Use:**

1) Call this routine.

**EXAMPLE:**

```ASM
      JSR JSRFAR
      .WORD $C000 ; ADDRESS
      .BYTE 1     ; BANK
```

### 65C816 support

When writing native 65C816 code for the Commander X16, extra care must be given when using the KERNAL API. With the exception of `extapi16`, documented below, the entire kernal API must be called:

* With m=1, x=1 (accumulator and index are 8 bits)
* SP set to the KERNAL stack ($01xx). see 
* DP=$0000 (must be set so that zeropage is the direct page)

$FEA8: `extapi16` - 16-bit extended API for 65C816 native mode  

---

#### Function Name: extapi16

Purpose: API functions for 65C816  
Minimum ROM version: R47  
Call address: $FEA8  
Communication registers: .C, .X, .Y, .P  
Preparatory routines: None  
Error returns: Varies, but usually c=1  
Registers affected: Varies

**Description:** This API slot provides access to various native mode 65C816 calls. The call is selected by the .C register (accumulator), and each call has its own register use and return behavior.

**IMPORTANT**  
* All of the calls behind this API __must__ be called in native 65C816 mode, with m=0, .DP=$0000.  Most will return with m=0, x=0.
* In addition, some of these __must__ be called with `rom_bank` (zp address $01) set to bank 0 (the KERNAL bank) and not via KERNAL support in other ROM banks. If your program is launched from BASIC, the default bank is usually 4 until explicitly changed by your program.

| Call # | Name           | Description                                 | Inputs | Outputs | Additional Prerequisites |
| -------|----------------|---------------------------------------------|--------|---------|--------------------------|
|  `$00` | [`test`](#65c816-extapi16-function-name-test) | Used by unit tests | .X .Y  | .C | -                       |
|  `$01` | [`stack_push`](#65c816-extapi16-function-name-stack_push) | Switches to a new stack context | .X | none | x=0, $01=0 |
|  `$02` | [`stack_pop`](#65c816-extapi16-function-name-stack_pop) | Returns to the previous stack context | none | none | x=0, $01=0 |
|  `$03` | [`stack_enter_kernal_stack`](#65c816-extapi16-function-name-stack_enter_kernal_stack) | Switches to the $01xx stack | none | none | x=0, $01=0 |
|  `$04` | [`stack_leave_kernal_stack`](#65c816-extapi16-function-name-stack_leave_kernal_stack) | Returns to the previous stack context after `stack_enter_kernal_stack` | none | none | x=0, $01=0 |
|  `$05` | [`xmacptr`](#65c816-extapi16-function-name-xmacptr) | 24-bit aware extended implementation of MACPTR | r0L-r1L r2 | r2 c | none |
|  `$06` | [`xmciout`](#65c816-extapi16-function-name-xmciout) | 24-bit aware extended implementation of MCIOUT | r0L-r1L r2 | r2 c | none |
|  `$07` | [`hbload`](#65c816-extapi16-function-name-hbload) | 24-bit aware extended implementation of headerless LOAD | .X r0L-r1L | .A r0L-r1L m=1 x=1 c | prior calls to setnam, setlfs |
|  `$08` | [`get_last_far_bank`](#65c816-extapi16-function-name-get_last_far_bank) | Returns last useful far bank for 24-bit addressing | none | .C | none |

---

#### 65C816 extapi16 Function Name: test

Purpose: Used by unit tests for jsrfar  
Minimum ROM version: R47  
Call address: $FEA8, .C=0  
Communication registers: .C .X .Y  
Preparatory routines: none  
Error returns: none  
Registers affected: .C  

**Description:** This API is used by unit tests and is not useful for applications.

---

#### 65C816 extapi16 Function Name: stack_push

Purpose: Point the SP to a new stack  
Minimum ROM version: R47  
Call address: $FEA8, .C=1  
Communication registers: .X  
Preparatory routines: none  
Error returns: none  
Registers affected: .A .X .Y .P .SP  

**Description:** This function informs the KERNAL that you're moving the stack pointer to a new location so that it can preserve the previous SP, and then brings the new SP into effect. The main purpose of this call is to preserve the position of the $01xx stack pointer (AKA KERNAL stack), and to track the length of the chain of stacks in the case of multiple pushes. In order for the 65C02 code in the emulated mode IRQ handler to run properly, it must be able to temporarily switch to using the KERNAL stack, regardless of the SP in main code.

**How to Use:**

1) Ensure `rom_bank` (ZP $01) is set to `0`. This function will not work if it traverses through `jsrfar`.
2) Load .X with the new SP to switch to, then call the routine. Upon return, .SP will be set to the new stack value. If the stack chain depth is greater than 1, the new stack will also have the old stack's address pushed onto it.
3) To return to the previous stack context, call `stack_pop`.

**Notes:**

* If you wish to preserve your current SP while temporarily switching back to the $01xx stack, for instance, to use the KERNAL API, begin that section of code with a call to `stack_enter_kernal_stack` and end with a call to `stack_leave_kernal_stack`.

---

#### 65C816 extapi16 Function Name: stack_pop

Purpose: Point the SP to the previously-saved stack  
Minimum ROM version: R47  
Call address: $FEA8, .C=2  
Communication registers: none  
Preparatory routines: `stack_push`  
Error returns: none  
Registers affected: .A .X .Y .P .SP  

**Description:** This function informs the KERNAL that you're finished using the stack set previously by `stack_push`. It brings the previous SP into effect.

**How to Use:**

1) Ensure `rom_bank` (ZP $01) is set to `0`. This function will not work if it traverses through `jsrfar`.
2) Ensure the current SP is set to the same value that was set immediately after the return from `stack_push`. In other words, you cannot use this function to bail out early from a deep subroutine chain without taking care to reset the stack first. In addition, you cannot simply reset the stack to the value that _you_ called `stack_push` with since the new stack may have had state pushed by the call to `stack_push`.
3) Call `stack_pop`.  The call will return to the address immediately after, but with the previously-pushed SP.

---

#### 65C816 extapi16 Function Name: stack_enter_kernal_stack

Purpose: Point the SP to the previously-saved \$01xx stack, preserving the current one  
Minimum ROM version: R47  
Call address: \$FEA8, .C=3  
Communication registers: none  
Preparatory routines: `stack_push`  
Error returns: none  
Registers affected: .A .X .Y .P .SP  

**Description:** This function requests that the KERNAL temporarily bring the \$01xx stack into effect during use a different stack. This is useful for applications which have moved the SP away from \$01xx but need to call the KERNAL API or legacy code.

**How to Use:**

1) Ensure `rom_bank` (ZP $01) is set to `0`. This function will not work if it traverses through `jsrfar`.
2) A prior call to `stack_push` must be in effect that hasn't been undone by `stack_pop`, and the current SP must not be the default $01xx stack.
3) Call `stack_enter_kernal_stack`, call the legacy functions, then call `stack_leave_kernal_stack`.

---

#### 65C816 extapi16 Function Name: stack_leave_kernal_stack

Purpose: Point the SP to the previously-preserved stack  
Minimum ROM version: R47  
Call address: $FEA8, .C=4  
Communication registers: none  
Preparatory routines: `stack_enter_kernal_stack`  
Error returns: none  
Registers affected: .A .X .Y .P .SP  

**Description:** This function is the counterpart to `stack_enter_kernal_stack`, and restores the previously preserved stack.

**How to Use:**

1) Ensure `rom_bank` (ZP $01) is set to `0`. This function will not work if it traverses through `jsrfar`.
2) A prior call to `stack_enter_kernal_stack` must be in effect that hasn't been undone by this function.
3) Call `stack_leave_kernal_stack`.

---

#### 65C816 extapi16 Function Name: xmacptr

Purpose: Fetch a block of data up to 65536 bytes from a file on supported device  
Minimum ROM version: R49  
Call address: $FEA8, .C=5  
Communication registers: r0L-r1L r2 c  
Preparatory routines: `CHKIN`  
Error returns: c=1  
Registers affected: .A .X .Y .P r0-r2  

**Description:** This function is the 24-bit counterpart to `MACPTR`, but has a slightly different calling convention.  Supported devices include the SD card and x16emu's HostFS.

While it is mainly useful for loading data onto systems with 24-bit far memory, such as the unreleased X16 GS, or the emulator with the `-gs` flag, this routine can also be used to load data into the first 64K of address space, including banked RAM at $00A000.  Banked RAM loads automatically advance the RAM bank the same as they do for MACPTR.

**How to Use:**

1) Set `r0L-r1L` to the 24-bit target address (little-endian).
2) Set `r2` to the number of bytes to read. The value $0000 is treated as a request for up to 65536 bytes.
3) Call `xmacptr`.
4) `r2` will contain the actual number of bytes read, or $0000 for 65536.  To distinguish the two possible conditions (zero bytes vs 64K), check the carry flag upon return.

---

#### 65C816 extapi16 Function Name: xmciout

Purpose: Write a block of data up to 65536 bytes to a file on a supported device  
Minimum ROM version: R49  
Call address: $FEA8, .C=6  
Communication registers: r0L-r1L r2 c  
Preparatory routines: `CHKOUT`  
Error returns: c=1  
Registers affected: .A .X .Y .P r0-r2  

**Description:** This function is the 24-bit counterpart to `MCIOUT`, but has a slightly different calling convention.  Supported devices include the SD card and x16emu's HostFS.

While it is mainly useful for systems with 24-bit far memory, such as the unreleased X16 GS, or the emulator with the `-gs` flag, this routine can also be used to save data from the first 64K of address space, including banked RAM at $00A000.  Writes from banked RAM automatically advance the RAM bank the same as they do for MCIOUT when passing through $BFFF.

**How to Use:**

1) Set `r0L-r1L` to the 24-bit source address (little-endian).
2) Set `r2` to the number of bytes to write to the file. The value $0000 is treated as a request for up to 65536 bytes.
3) Call `xmciout`.
4) `r2` will contain the actual number of bytes written, or $0000 for 65536.  To distinguish the two possible conditions (zero bytes vs 64K), check the carry flag upon return.

---

#### 65C816 extapi16 Function Name: hbload

Purpose: Load a file from a supported device into 24-bit address space  
Minimum ROM version: R49  
Call address: $FEA8, .C=7  
Communication registers: .X r0L-r1L c  
Preparatory routines: `SETNAM`, `SETLFS`  
Error returns: c=1 .A=errno  
Registers affected: .A .X .Y .P r0-r2  

**Description:** This function is the 24-bit counterpart to a headerless `LOAD`, but has a slightly different calling convention.

This routine is only available on machines with 24-bit far memory, such as the unreleased X16 GS, or the emulator with the `-gs` flag.  Other machine types will return c=1 with .A=40 (unsupported machine).

**How to Use:**

1) Call `SETNAM`
2) Call `SETLFS`.  Unlike for `LOAD`, the .Y value for `SETLFS` is ignored by `HBLOAD`.
3) Set r0L-r1L to the 24-bit starting memory address for the load.
4) Set .X to 0 for LOAD and 1 for VERIFY
5) Call `hbload`.
4) `r0L-r1L` contain the first address _following_ the end of the load.

**Notes:**
`hbload` returns with **m=1, x=1** instead of the usual m=0, x=0 for extapi16 calls.

---

#### 65C816 extapi16 Function Name: get_last_far_bank

Purpose: Return the maximum usable far bank (bits 16-23 of a 24-bit memory address)  
Minimum ROM version: R49  
Call address: $FEA8, .C=8  
Communication registers: .C  
Preparatory routines: none  
Error returns: none  
Registers affected: .A .X .P  

**Description:** This function returns the maximum usable far bank for 24-bit addressing.  A stock dev board with a 65C816 will return $00, as it doesn't have any addressing beyond $00FFFF. A GS system, or the emulator with the `-gs` flag will return `$FF`.

**How to Use:**

1) Call `get_last_far_bank`
2) .C (and by extension, .A) will contain the maximum usable far bank number, ranging from $00-$FF.  The amount of far ram available in bytes is `.C * 65536`.

--

[^1]: [https://github.com/emmanuel-marty/lzsa](https://github.com/emmanuel-marty/lzsa)
  
<!-- For PDF formatting -->
<div class="page-break"></div>

# Chapter 6: Math Library

The Commander X16 contains a floating point Math library with a precision of 40 bits, which corresponds to 9 decimal digits. It is a stand-alone derivative of the library contained in Microsoft BASIC. Except for the different base address, it is compatible with the C128 and C65 libraries.

The full documentation of these functions can be found in the book [C128 Developers Package for Commodore 6502 Development](http://www.zimmers.net/anonftp/pub/cbm/schematics/computers/c128/servicemanuals/C128_Developers_Package_for_Commodore_6502_Development_(1987_Oct).pdf). The Math Library documentation starts in Chapter 13. (PDF page 257)

The following functions are available from machine language code after setting the ROM bank to 4, which is the default.

## Format Conversions

| Address | Symbol   | Description                                                                                  |
|---------|----------|----------------------------------------------------------------------------------------------|
| $FE00   | `AYINT`  | convert floating point to integer (signed word)                                              |
| $FE03   | `GIVAYF` | convert integer (signed word) to floating point                                              |
| $FE06   | `FOUT`   | convert floating point to ASCII string. (See below)                                                       |
| $FE09   | `VAL_1`  | convert ASCII string in .X:.Y length in .A, to floating point in FACC. _Caveat! Read below!_ |
| $FE0C   | `GETADR` | convert floating point to an address (unsigned word)                                         |
| $FE0F   | `FLOATC` | convert address (unsigned word) to floating point                                            |
| $FE8D   | `QINT`   | convert floating point to signed 32-bit integer (which is stored in the FACC mantissa bytes in big-endian order)        |

**Difference in X16 Behavior of FOUT**

The version of FOUT described in the book leaves a pointer to the result string
in the AY register pair; the X16 version does not do that. Instead, rely on the
string always being placed in the FBUFFR location at $0100. 

**Important caveat ragarding the `VAL_1` routine in its current implementation:**

Unlike the other routines in the math library, this routine calls into the VAL implementation
that is inside BASIC, and so it requires much of the BASIC zeropage to be intact to function correctly.
The reason is that that routine ultimately relies on some internal BASIC routines that use a lot of BASIC zero page space.
Ideally in the future, the `VAL_1` routine gets a new implementation that doesn't rely on the code in BASIC, thereby removing this restriction.

**X16 Additions**

The following calls are new to the X16 and were not part of the C128 math library API:

| Address | Symbol   | Description                                     |
|---------|----------|-------------------------------------------------|
| $FE87  | `FLOAT`  | FACC = (s8).A   convert signed byte to float     |
| $FE8A  | `FLOATS` | FACC = (s16)facho+1:facho                        |
| $FE93  | `FOUTC`  | Convert FACC to ASCIIZ string at fbuffr - 1 + .Y |

## Movement

`PACK` indicates a conversion from a normalized floating-point number in FACC to its packed format in memory; `UNPACK` indicates a conversion from the packed format in memory to the normalized format in the destination.

| Address | Symbol   | Description                          |
|---------|----------|--------------------------------------|
| $FE5A  | `CONUPK` | ARG = UNPACK(RAM MEM)                |
| $FE5D  | `ROMUPK` | ARG = UNPACK(ROM MEM) (use `CONUPK`) |
| $FE60  | `MOVFRM` | FACC = UNPACK(RAM MEM) (use `MOVFM`) |
| $FE63  | `MOVFM`  | FACC = UNPACK(ROM MEM)               |
| $FE66  | `MOVMF`  | MEM = PACK(ROUND(FACC))              |
| $FE69  | `MOVFA`  | FACC = ARG                           |
| $FE6C  | `MOVAF`  | FACC = ROUND(FACC); ARG = FACC       |

**X16 Additions**

The following calls are new to the X16 and were not part of the C128 math library API:

| Address | Symbol  | Description                                     |
|---------|---------|-------------------------------------------------|
| $FE81  | `MOVEF` | ARG = FACC                                      |

## Math Functions

| Address | Symbol   | Description                           |
|---------|----------|---------------------------------------|
| $FE12  | `FSUB`   | FACC = MEM - FACC                     |
| $FE15  | `FSUBT`  | FACC = ARG - FACC                     |
| $FE18  | `FADD`   | FACC = MEM + FACC                     |
| $FE1B  | `FADDT`  | FACC = ARG + FACC                     |
| $FE1E  | `FMULT`  | FACC = MEM * FACC                     |
| $FE21  | `FMULTT` | FACC = ARG * FACC                     |
| $FE24  | `FDIV`   | FACC = MEM / FACC                     |
| $FE27  | `FDIVT`  | FACC = ARG / FACC                     |
| $FE2A  | `LOG`    | FACC = natural log of FACC            |
| $FE2D  | `INT`    | FACC = INT() truncate of FACC         |
| $FE30  | `SQR`    | FACC = square root of FACC            |
| $FE33  | `NEGOP`  | negate FACC (switch sign)             |
| $FE36  | `FPWR`   | FACC = raise ARG to the MEM power     |
| $FE39  | `FPWRT`  | FACC = raise ARG to the FACC power    |
| $FE3C  | `EXP`    | FACC = EXP of FACC                    |
| $FE3F  | `COS`    | FACC = COS of FACC                    |
| $FE42  | `SIN`    | FACC = SIN of FACC                    |
| $FE45  | `TAN`    | FACC = TAN of FACC                    |
| $FE48  | `ATN`    | FACC = ATN of FACC                    |
| $FE4B  | `ROUND`  | FACC = round FACC                     |
| $FE4E  | `ABS`    | FACC = absolute value of FACC         |
| $FE51  | `SIGN`   | .A = test sign of FACC                |
| $FE54  | `FCOMP`  | .A = compare FACC with MEM            |
| $FE57  | `RND_0`  | FACC = random floating point number   |

**X16 Additions to math functions**

The following calls are new to the X16 and were not part of the C128 math library API:

| Address | Symbol   | Description                               |
|---------|----------|-------------------------------------------|
| $FE6F  | `FADDH`  | FACC += .5                                |
| $FE72  | `ZEROFC` | FACC = 0                                  |
| $FE75  | `NORMAL` | Normalize FACC                            |
| $FE78  | `NEGFAC` | FACC = -FACC   (just use NEGOP)           |
| $FE7B  | `MUL10`  | FACC *= 10                                |
| $FE7E  | `DIV10`  | FACC /= 10                                |
| $FE84  | `SGN`    | FACC = sgn(FACC)                          |
| $FE90  | `FINLOG` | FACC += (s8).A   add signed byte to float |
| $FE96  | `POLYX`  | Polynomial Evaluation 1 (SIN/COS/ATN/LOG) |
| $FE99  | `POLY`   | Polynomial Evaluation 2 (EXP)             |

## How to use the routines

**Concepts:**

* **FACC** (sometimes abbreviated to FAC): the floating point accumulator. You can compare this to the 6502 CPU's .A register,
  which is the accumulator for most integer operations performed by the CPU.
  FACC is the primary floating point register. Calculations are done on the value in this register,
  usually combined with ARG. After the operation, usually the original value in FACC has been replaced by the result of the calculation.
* **ARG**: the second floating point register, used in most calculation functions. Often the value in this register will be lost after a calculation.
* **MEM**: means a floating point value stored in system memory somewhere.  The format is [40 bits (5 bytes) Microsoft binary format](https://en.wikipedia.org/wiki/Microsoft_Binary_Format).
  To be able to work with given values in calculations, they need to be stored in memory somewhere in this format.
  To do this you'll likely need to use a separate program to pre-convert floating point numbers to this format, unless you are using a compiler that
  directly supports it.

*Note that FACC and ARG are just a bunch of zero page locations. This means you can poke around in them.
But that's not good practice because their locations aren't guaranteed/public, and the format is slightly different
than how the 5-byte floats are normally stored into memory. Just use one of the Movement routines to
copy values into or out of FACC and ARG.*

To perform a floating point calculation, follow the following pattern:

1. load a value into FACC. You can convert an integer, or move a MEM float number into FACC.
1. do the same but for ARG, the second floating point register.
1. call the required floating point calculation routine that will perform a calculation on FACC with ARG.
1. repeat the previous 2 steps if required.
1. the result is in FACC, move it into MEM somewhere or convert it to another type or string.

An example program that calculates and prints the distance an object has fallen over a certain period
using the formula $d = \dfrac{1}{2} g {t}^{2}$

```ASM
; calculate how far an object has fallen:  d = 1/2 * g * t^2.
; we set g = 9.81 m/sec^2, time = 5 sec -> d = 122.625 m.

CHROUT = $ffd2
FOUT   = $fe06
FMULTT = $fe21
FDIV   = $fe24
CONUPK = $fe5a
MOVFM  = $fe63

    lda  #4
    sta  $01         ; rom bank 4 (BASIC) contains the fp routines.
    lda  #<flt_two
    ldy  #>flt_two
    jsr  MOVFM
    lda  #<flt_g
    ldy  #>flt_g
    jsr  FDIV        ; FACC= g/2
    lda  #<flt_time
    ldy  #>flt_time
    jsr  CONUPK      ; ARG = time
    jsr  FMULTT      ; FACC = g/2 * time
    lda  #<flt_time
    ldy  #>flt_time
    jsr  CONUPK      ; again ARG = time
    jsr  FMULTT      ; FACC = g/2 * time * time
    jsr  FOUT        ; to string
    ; print string in AY
    sta  $02
    sty  $03
    ldy  #0
loop:
    lda  ($02),y
    beq  done
    jsr  CHROUT
    iny
    bne  loop
done:
    rts

flt_g:      .byte  $84, $1c, $f5, $c2, $8f  ; float 9.81
flt_time:   .byte  $83, $20, $00, $00, $00  ; float 5.0
flt_two:    .byte  $82, $00, $00, $00, $00  ; float 2.0
```

## Notes

* `RND_0`: For .Z=1, the X16 behaves differently than the C128 and C65 versions. The X16 version takes entropy from .A/.X/.Y instead of from a CIA timer. So in order to get a "real" random number, you would use code like this:

```ASM
LDA #$00
PHP
JSR entropy_get ; KERNAL call to get entropy into .A/.X/.Y
PLP             ; restore .Z=1
JSR RND_0
```

* The calls `FADDT`, `FMULTT`, `FDIVT` and `FPWRT` were broken on the C128/C65. They are fixed on the X16.
* For more information on the additional calls, refer to [Mapping the Commodore 64](http://unusedino.de/ec64/technical/project64/mapping_c64.html) by Sheldon Leemon, ISBN 0-942386-23-X, but note these errata:
  * `FMULT` adds mem to FACC, not ARG to FACC

<!-- For PDF formatting -->
<div class="page-break"></div>

# Chapter 7: Machine Language Monitor

<img src="images/monitor.png">

The built-in machine language monitor can be started with the `MON` BASIC command. It is based on the monitor of the Final Cartridge III and supports most of its features.

If you invoke the monitor by mistake, you can exit with by typing `X`, followed by the `RETURN` key.

Some features specific to this monitor are:

* The `I` command prints a PETSCII/ISO-encoded memory dump.
* The `EC` command prints a binary memory dump. This is also useful for character sets.
* Scrolling the screen with the cursor keys or F3/F5 will continue memory dumps and disassemblies, and even disassemble backwards.

The following commands are used to dump memory contents in various formats:

| Dump | Prefix  | description
|------|---------|---------------
| `M`  |  `:`    | 8 hex bytes
| `I`  |  `'`    | 32 PETSCII/ISO characters
| `EC` |  `[`    | 1 binary byte (character data)
| `ES` |  `]`    | 3 binary bytes (sprite data)
| `D`  |  `,`    | disassemble
| `R`  |  `;`    | registers

Except for `R`, these commands take a start address and an optional end address (inclusive). The dumps are prefixed with one of the "Prefix" characters in the table above, so they can be edited by navigating the cursor over a printed line, changing the data and pressing RETURN.

Note that editing a disassembled line (prefix `,`) only allows changing the 1-3 opcode bytes. To edit the assembly, change the prefix to `A` (see below).

These are the remaining commands:

| Command | Syntax                          | Description            |
|---------|---------------------------------|------------------------|
| `F`     | _start_ _end_ _byte_            | fill                   |
| `H`     | _start_ _end_ _byte_ [_byte_...]| hunt                   |
| `C`     | _start_ _end_ _start_           | compare                |
| `T`     | _start_ _end_ _start_           | transfer               |
| `A`     | _address_ _instruction_         | assemble               |
| `G`     | [_address_]                     | run code               |
| `J`     | [_address_]                     | run subroutine         |
| `$`     | _value_                         | convert hex to decimal |
| `#`     | _value_                         | convert decimal to hex |
| `X`     |                                 | exit monitor           |
| `O`     | _bank_                          | set ROM bank           |
| `K`     | _bank_                          | set RAM/VRAM bank/I2C  |
| `L`     | ["_filename_"[,_dev_[,_start_]]]| load file              |
| `S`     | "_filename_",_dev_,_start_,_end_| save file              |
| `@`     | _command_                       | send drive command     |

* All addresses have to be 4 digits.
* All bytes have to be 2 digits (including device numbers).
* The end address of `S` is exclusive.
* The bank argument for `K` is
  * `00`-`FF`: switch to main RAM, set RAM bank
  * `V0`-`V1`: switch to Video RAM, set VRAM bank
  * `I`: switch to the I2C address space
* The bank argument for `O` is
  * `00`-`FF`: set ROM bank
* `@` takes:
  * `8`, `9` to change the default drive (also for `L`)
  * `$` to display the disk directory
  * anything else as a disk command

Monitor Display
```
MON
C*
   PC  RA RO AC XR YR SP NV#BDIZC
.;E3bb 01 04 00 00 00 F6 ........
.
```
| Column  | Description |
|---------|-------------|
|PC       | Program Counter and the current address
|RA       | Active RAM Bank
|RO       | Active ROM Bank
|AC       | Accumulator Value
|XR       | X Register Value
|YR       | Y Register Value
|SP       | Stack Pointer
|NV#BDIZC | Status Register

| Status Register Bits | Bit Description |
|----------------------|-----------------|
|  N                   | Negative
|  V                   | Overflow Vector
| \#                   | Unused
|  B                   | A Break Point is Active
|  D                   | Decimal Mode Active (also known as Binary Code Decimal)
|  I                   | IRQ is Inhibited
|  Z                   | Zero Bit
|  C                   | Carry Bit

<!-- For PDF formatting -->
<div class="page-break"></div>

# Chapter 8: Memory Map

The Commander X16 has 512 KB of ROM and 2,088 KB (2 MB[^1] + 40 KB) of RAM with up to 3.5MB of RAM or ROM available to cartridges.

Some of the ROM/RAM is always visible at certain address ranges, while the remaining ROM/RAM is banked into one of two address windows.

This is an overview of the X16 memory map:

|Addresses  |Description                                                                             |
|-----------|----------------------------------------------------------------------------------------|
|\$0000-\$9EFF|Fixed RAM (40 KB minus 256 bytes)                                                       |
|\$9F00-\$9FFF|I/O Area (256 bytes)                                                                    |
|\$A000-\$BFFF|Banked RAM (8 KB window into one of 256 banks for a total of 2 MB)                      |
|\$C000-\$FFFF|Banked System ROM and Cartridge ROM/RAM (16 KB window into one of 256 banks, see below) |

## Banked Memory

Writing to the following zero-page addresses sets the desired RAM or ROM bank:

|Address  |Description                                                   |
|---------|--------------------------------------------------------------|
|$0000    |Current RAM bank (0-255)                                      |
|$0001    |Current ROM/Cartridge bank (ROM is 0-31, Cartridge is 32-255) |

The currently set banks can also be read back from the respective memory locations. Both settings default to 0 on RESET.

## ROM Allocations

Here is the ROM/Cartridge bank allocation:

|Bank  |Name   |Description                                            |
|------|-------|-------------------------------------------------------|
|0     |KERNAL |KERNAL operating system and drivers                    |
|1     |KEYBD  |Keyboard layout tables                                 |
|2     |CMDRDOS|The computer-based CMDR-DOS for FAT32 SD cards         |
|3     |FAT32  |The FAT32 driver itself                                |
|4     |BASIC  |BASIC interpreter                                      |
|5     |MONITOR|Machine Language Monitor                               |
|6     |CHARSET|PETSCII and ISO character sets (uploaded into VRAM)    |
|7     |DIAG   |Memory diagnostic                                      |
|8     |GRAPH  |Kernal graph and font routines                         |
|9     |DEMO   |Demo routines                                          |
|10    |AUDIO  |Audio API routines                                     |
|11    |UTIL   |System Configuration (Date/Time, Display Preferences)  |
|12    |BANNEX |BASIC Annex (code for some added BASIC functions)      |
|13-14 |X16EDIT|The built-in text editor                               |
|15    |BASLOAD|A transpiler that converts BASLOAD dialect to BASIC V2 |
|16-31 |–      |_[Currently unused]_                                   |
|32-255|–      |Cartridge RAM/ROM                                      |

**Important**: The layout of the banks may still change.

### Cartridge Allocation

Cartridges can use the remaining 32-255 banks in any combination of ROM, RAM, Memory-Mapped IO, etc. See Kevin's reference cartridge design
for ideas on how this may be used. This provides up to 3.5MB of additional RAM or ROM.

Bootable cartridge: See [Hardware - Booting from Cartridges](X16%20Reference%20-%2014%20-%20Hardware.md#booting-from-cartridges)

**Important**: The layout of the banks is not yet final.

## RAM Contents

This is the allocation of fixed RAM in the KERNAL/BASIC environment.

|Addresses   |Description                                                      |
|------------|-----------------------------------------------------------------|
|\$0000-\$00FF|Zero page                                                       |
|\$0100-\$01FF|CPU stack                                                       |
|\$0200-\$03FF|KERNAL and BASIC variables, vectors                             |
|\$0400-\$07FF|Available for machine code programs or custom data storage      |
|\$0800-\$9EFF|BASIC program/variables; available to the user                  |

The `$0400-$07FF` can be seen as the equivalent of `$C000-$CFFF` on a C64. A typical use would be for helper machine code called by BASIC.

### Zero Page

|Addresses   |Description                             |
|------------|----------------------------------------|
|\$0000-\$0001|Banking registers                      |
|\$0002-\$0021|16 bit registers r0-r15 for KERNAL API |
|\$0022-\$007F|Available to the user                  |
|\$0080-\$009C|Used by KERNAL and DOS                 |
|\$009D-\$00A8|Reserved for DOS/BASIC                 |
|\$00A9-\$00D3|Used by the Math library (and BASIC)   |
|\$00D4-\$00FF|Used by BASIC                          |

Machine code applications are free to reuse the BASIC area, and if they don't use the Math library, also that area.

### Banking

This is the allocation of banked RAM in the KERNAL/BASIC environment.

|Bank |Description                                    |
|-----|-----------------------------------------------|
|0    |Used for KERNAL/CMDR-DOS variables and buffers |
|1-255|Available to the user                          |

(On systems with only 512 KB RAM, banks 64-255 are unavailable.)

During startup, the KERNAL activates RAM bank 1 as the default for the user.

### Bank 0

|Addresses   |Description                             |
|------------|----------------------------------------|
|\$A000-\$BEFF| System Reserved                       |
|\$BF00-\$BFFF| Parameter passing space               |

You can use the space at $0:BF00-0:$BFFF to pass parameters between programs.
This space is initialized to zeroes, so you may use it however you wish.

The suggested use is to store a PETSCII string in this space and use
semicolons to separate parameters. The string should be null terminated:

Example:

`FRANK;3;BLUE\x00`

A program that reads the parameters is responsible for resetting the data to
zeroes, so that another program does not see unexpected data and malfunction.

## I/O Area

This is the memory map of the I/O Area:

|Addresses    |Description                          |Speed|
|-------------|-------------------------------------|-----|
|\$9F00-\$9F0F|VIA I/O controller #1. [Details](X16%20Reference%20-%2012%20-%20IO%20Programming.md#chapter-12-io-programming) |8 MHz|
|\$9F10-\$9F1F|VIA I/O controller #2                |8 MHz|
|\$9F20-\$9F3F|VERA video controller. [Details](X16%20Reference%20-%2009%20-%20VERA%20Programmer's%20Reference.md#registers) |8 MHz|
|\$9F40-\$9F41|YM2151 audio controller. [Details](X16%20Reference%20-%2011%20-%20Sound%20Programming.md#ym2151-opm-fm-synthesis) |2 MHz|
|\$9F42-\$9F5F|Unavailable                          | --- |
|\$9F50-\$9F5F|Planned for X16GS. [Details](https://x16community.github.io/faq/gs-faq.html) | --- |
|\$9F60-\$9F7F|Expansion Card Memory Mapped IO3     |8 MHz|
|\$9F80-\$9F9F|Expansion Card Memory Mapped IO4     |8 MHz|
|\$9FA0-\$9FBF|Expansion Card Memory Mapped IO5     |2 MHz|
|\$9FB0-\$9FBF|Used by emulator. [Details](https://github.com/X16Community/x16-emulator?tab=readme-ov-file#emulator-io-registers) | --- |
|\$9FC0-\$9FDF|Expansion Card Memory Mapped IO6     |2 MHz|
|\$9FE0-\$9FFF|Cartidge/Expansion Memory Mapped IO7 |2 MHz|

### Expansion Cards & Cartridges

Expansion cards can be accessed via memory-mapped I/O (MMIO), as well as I2C. Cartridges are
essentially expansion cards which are housed in an external enclosure and may contain RAM, ROM
and an I2C EEPOM (for save data). Internal expansion cards may also use the RAM/ROM space,
though this could cause conflicts.

While they may be uncommon, since cartridges are essentially external expansion cards in a
shell, that means they can also use MMIO. This is only necessary when a cartridge includes
some sort of hardware expansion and MMIO was desired (as opposed to using the I2C bus). In
that case, it is recommended cartridges use the IO7 range and that range should be the
last option used by expansion cards in the system.
**MMIO is unneeded for cartridges which simply have RAM/ROM.**

For more information, consult the
[Hardware](X16%20Reference%20-%2014%20-%20Hardware.md#chapter-14-hardware-pinouts) section of the manual.

---

[^1]: Current development systems have 2 MB of bankable RAM.
Actual hardware is currently planned to have an option of either 512 KB or 2 MB of RAM.

<!-- For PDF formatting -->
<div class="page-break"></div>

# Chapter 9: VERA Programmer's Reference

This document describes the **V**ersatile **E**mbedded **R**etro **A**dapter or VERA.
Which was originally written and conceived by Frank van den Hoef.

The VERA video chip supports resolutions up to 640x480 with up to 256 colors
from a palette of 4096, two layers of either a bitmap or tiles, 128 sprites of
up to 64x64 pixels in size. It can output VGA as well as a 525 line interlaced
signal, either as NTSC or as RGB (Amiga-style).

The FPGA core used in the Commander X16 has been forked from Version 0.9 of the
VERA. The original documentation can be found
[here](https://github.com/fvdhoef/vera-module/blob/rev4/doc/VERA%20Programmer's%20Reference.md#vera-programmers-reference).

The Commander X16 uses a modified version of VERA which includes extra
functionality, notably the FX Aid additions. See
[Chapter 10](X16%20Reference%20-%2010%20-%20VERA%20FX%20Reference.md#chapter-10-vera-fx-reference)
for more information on the FX additions.

The VERA consists of:

* Video generator featuring:
  * Multiple output formats (VGA, NTSC Composite, NTSC S-Video, RGB video) at a fixed resolution of 640x480@60Hz
  * Support for 2 layers, both supporting either tile or bitmap mode.
  * Support for up to 128 sprites.
  * Embedded video RAM of 128kB.
  * Palette with 256 colors selected from a total range of 4096 colors.
* 16-channel Programmable Sound Generator with multiple waveforms (Pulse, Sawtooth, Triangle, Noise)
* High quality PCM audio playback from an 4kB FIFO buffer featuring up to 48kHz 16-bit stereo sound.
* SPI controller for SecureDigital storage.

# Registers

## \$9F20-\$9F28

<table>
	<tr>
		<th>Addr</th>
		<th>Name</th>
		<th>Bit&nbsp;7</th>
		<th>Bit&nbsp;6</th>
		<th>Bit&nbsp;5 </th>
		<th>Bit&nbsp;4</th>
		<th>Bit&nbsp;3 </th>
		<th>Bit&nbsp;2</th>
		<th>Bit&nbsp;1 </th>
		<th>Bit&nbsp;0</th>
	</tr>
	<tr>
		<td>$9F20</td>
		<td>ADDRx_L (x=ADDRSEL)</td>
		<td colspan="8" align="center">VRAM Address (7:0)</td>
	</tr>
	<tr>
		<td>$9F21</td>
		<td>ADDRx_M (x=ADDRSEL)</td>
		<td colspan="8" align="center">VRAM Address (15:8)</td>
	</tr>
	<tr>
		<td>$9F22</td>
		<td>ADDRx_H (x=ADDRSEL)</td>
		<td colspan="4" align="center">Address Increment</td>
		<td align="center">DECR</td>
		<td align="center">Nibble Increment</td>
		<td align="center">Nibble Address</td>
		<td align="center">VRAM Address (16)</td>
	</tr>
	<tr>
		<td>$9F23</td>
		<td>DATA0</td>
		<td colspan="8" align="center">VRAM Data port 0</td>
	</tr>
	<tr>
		<td>$9F24</td>
		<td>DATA1</td>
		<td colspan="8" align="center">VRAM Data port 1</td>
	</tr>
	<tr>
		<td>$9F25</td>
		<td>CTRL</td>
		<td colspan="1" align="center">Reset</td>
		<td colspan="6" align="center">DCSEL</td>
		<td colspan="1" align="center">ADDRSEL</td>
	</tr>
	<tr>
		<td>$9F26</td>
		<td>IEN</td>
		<td colspan="1" align="center">IRQ line (8)</td>
		<td colspan="1" align="center">Scan line (8)</td>
		<td colspan="2" align="center">-</td>
		<td colspan="1" align="center">AFLOW</td>
		<td colspan="1" align="center">SPRCOL</td>
		<td colspan="1" align="center">LINE</td>
		<td colspan="1" align="center">VSYNC</td>
	</tr>
	<tr>
		<td>$9F27</td>
		<td>ISR</td>
		<td colspan="4" align="center">Sprite collisions</td>
		<td colspan="1" align="center">AFLOW</td>
		<td colspan="1" align="center">SPRCOL</td>
		<td colspan="1" align="center">LINE</td>
		<td colspan="1" align="center">VSYNC</td>
	</tr>
	<tr>
		<td>$9F28</td>
		<td>IRQLINE_L (Write only)</td>
		<td colspan="8" align="center">IRQ line (7:0)</td>
	</tr>
	<tr>
		<td>$9F28</td>
		<td>SCANLINE_L (Read only)</td>
		<td colspan="8" align="center">Scan line (7:0)</td>
	</tr>
</table>

## \$9F29-\$9F2C

<details open>
	<summary>DCSEL=0</summary>
	<table>
		<tr>
			<th>Addr</th>
			<th>Name</th>
			<th>Bit&nbsp;7</th>
			<th>Bit&nbsp;6</th>
			<th>Bit&nbsp;5 </th>
			<th>Bit&nbsp;4</th>
			<th>Bit&nbsp;3 </th>
			<th>Bit&nbsp;2</th>
			<th>Bit&nbsp;1 </th>
			<th>Bit&nbsp;0</th>
		</tr>
		<tr>
			<td>$9F29</td>
			<td>DC_VIDEO</td>
			<td colspan="1" align="center">Current Field</td>
			<td colspan="1" align="center">Sprites Enable</td>
			<td colspan="1" align="center">Layer1 Enable</td>
			<td colspan="1" align="center">Layer0 Enable</td>
			<td colspan="1" align="center">NTSC/RGB: 240P</td>
			<td colspan="1" align="center">NTSC: Chroma Disable / RGB: HV Sync </td>
			<td colspan="2" align="center">Output Mode</td>
		</tr>
		<tr>
			<td>$9F2A</td>
			<td>DC_HSCALE<br></td>
			<td colspan="8" align="center">Active Display H-Scale</td>
		</tr>
		<tr>
			<td>$9F2B</td>
			<td>DC_VSCALE<br></td>
			<td colspan="8" align="center">Active Display V-Scale</td>
		</tr>
		<tr>
			<td>$9F2C</td>
			<td>DC_BORDER<br></td>
			<td colspan="8" align="center">Border Color</td>
		</tr>
	</table>
</details>

<details open>
	<summary>DCSEL=1</summary>
	<table>
		<tr>
			<th>Addr</th>
			<th>Name</th>
			<th>Bit&nbsp;7</th>
			<th>Bit&nbsp;6</th>
			<th>Bit&nbsp;5 </th>
			<th>Bit&nbsp;4</th>
			<th>Bit&nbsp;3 </th>
			<th>Bit&nbsp;2</th>
			<th>Bit&nbsp;1 </th>
			<th>Bit&nbsp;0</th>
		</tr>
		<tr>
			<td>$9F29</td>
			<td>DC_HSTART</td>
			<td colspan="8" align="center">Active Display H-Start (9:2)</td>
		</tr>
		<tr>
			<td>$9F2A</td>
			<td>DC_HSTOP</td>
			<td colspan="8" align="center">Active Display H-Stop (9:2)</td>
		</tr>
		<tr>
			<td>$9F2B</td>
			<td>DC_VSTART</td>
			<td colspan="8" align="center">Active Display V-Start (8:1)</td>
		</tr>
		<tr>
			<td>$9F2C</td>
			<td>DC_VSTOP</td>
			<td colspan="8" align="center">Active Display V-Stop (8:1)</td>
		</tr>
	</table>
</details>

<details open>
	<summary>DCSEL=2</summary>
	<table>
		<tr>
			<th>Addr</th>
			<th>Name</th>
			<th>Bit&nbsp;7</th>
			<th>Bit&nbsp;6</th>
			<th>Bit&nbsp;5 </th>
			<th>Bit&nbsp;4</th>
			<th>Bit&nbsp;3 </th>
			<th>Bit&nbsp;2</th>
			<th>Bit&nbsp;1 </th>
			<th>Bit&nbsp;0</th>
		</tr>
		<tr>
			<td>$9F29</td>
			<td>FX_CTRL</td>
			<td align="center">Transp. Writes</td>
			<td align="center">Cache Write Enable</td>
			<td align="center">Cache Fill Enable</td>
			<td align="center">One-byte Cache Cycling</td>
			<td align="center">16-bit Hop</td>
			<td align="center">4-bit Mode</td>
			<td colspan="2" align="center">Addr1 Mode</td>
		</tr>
		<tr>
			<td>$9F2A</td>
			<td>FX_TILEBASE<br>(Write only)</td>
			<td colspan="6" align="center">FX Tile Base Address (16:11)</td>
			<td align="center">Affine Clip Enable</td>
			<td align="center">2-bit Polygon</td>
		</tr>
		<tr>
			<td>$9F2B</td>
			<td>FX_MAPBASE<br>(Write only)</td>
			<td colspan="6" align="center">FX Map Base Address (16:11)</td>
			<td colspan="2" align="center">Map Size</td>
		</tr>
		<tr>
			<td>$9F2C</td>
			<td>FX_MULT<br>(Write only)</td>
			<td align="center">Reset Accum.</td>
			<td align="center">Accumulate</td>
			<td align="center">Subtract Enable</td>
			<td align="center">Multiplier Enable</td>
			<td colspan="2" align="center">Cache Byte Index</td>
			<td align="center">Cache Nibble Index</td>
			<td align="center">Two-byte Cache Incr. Mode</td>
		</tr>
	</table>
</details>

<details open>
	<summary>DCSEL=3</summary>
	<table>
		<tr>
			<th>Addr</th>
			<th>Name</th>
			<th>Bit&nbsp;7</th>
			<th>Bit&nbsp;6</th>
			<th>Bit&nbsp;5 </th>
			<th>Bit&nbsp;4</th>
			<th>Bit&nbsp;3 </th>
			<th>Bit&nbsp;2</th>
			<th>Bit&nbsp;1 </th>
			<th>Bit&nbsp;0</th>
		</tr>
		<tr>
			<td>$9F29</td>
			<td>FX_X_INCR_L<br>(Write only)</td>
			<td colspan="8" align="center">X Increment (-2:-9) (signed)</td>
		</tr>
		<tr>
			<td>$9F2A</td>
			<td>FX_X_INCR_H<br>(Write only)</td>
			<td align="center">X Incr. 32x</td>
			<td colspan="7" align="center">X Increment (5:-1) (signed)</td>
		</tr>
		<tr>
			<td>$9F2B</td>
			<td>FX_Y_INCR_L<br>(Write only)</td>
			<td colspan="8" align="center">Y/X2 Increment (-2:-9) (signed)</td>
		</tr>
		<tr>
			<td>$9F2C</td>
			<td>FX_Y_INCR_H<br>(Write only)</td>
			<td align="center">Y/X2 Incr. 32x</td>
			<td colspan="7" align="center">Y/X2 Increment (5:-1) (signed)</td>
		</tr>
	</table>
</details>

<details open>
	<summary>DCSEL=4</summary>
	<table>
		<tr>
			<th>Addr</th>
			<th>Name</th>
			<th>Bit&nbsp;7</th>
			<th>Bit&nbsp;6</th>
			<th>Bit&nbsp;5 </th>
			<th>Bit&nbsp;4</th>
			<th>Bit&nbsp;3 </th>
			<th>Bit&nbsp;2</th>
			<th>Bit&nbsp;1 </th>
			<th>Bit&nbsp;0</th>
		</tr>
		<tr>
			<td>$9F29</td>
			<td>FX_X_POS_L<br>(Write only)</td>
			<td colspan="8" align="center">X Position (7:0)</td>
		</tr>
		<tr>
			<td>$9F2A</td>
			<td>FX_X_POS_H<br>(Write only)</td>
			<td align="center">X Pos. (-9)</td>
			<td colspan="4" align="center">-</td>
			<td colspan="3" align="center">X Position (10:8)</td>
		</tr>
		<tr>
			<td>$9F2B</td>
			<td>FX_Y_POS_L<br>(Write only)</td>
			<td colspan="8" align="center">Y/X2 Position (7:0)</td>
		</tr>
		<tr>
			<td>$9F2C</td>
			<td>FX_Y_POS_H<br>(Write only)</td>
			<td align="center">Y/X2 Pos. (-9)</td>
			<td colspan="4" align="center">-</td>
			<td colspan="3" align="center">Y/X2 Position (10:8)</td>
		</tr>
	</table>
</details>

<details open>
	<summary>DCSEL=5</summary>
	<table>
		<tr>
			<th>Addr</th>
			<th>Name</th>
			<th>Bit&nbsp;7</th>
			<th>Bit&nbsp;6</th>
			<th>Bit&nbsp;5 </th>
			<th>Bit&nbsp;4</th>
			<th>Bit&nbsp;3 </th>
			<th>Bit&nbsp;2</th>
			<th>Bit&nbsp;1 </th>
			<th>Bit&nbsp;0</th>
		</tr>
		<tr>
			<td>$9F29</td>
			<td>FX_X_POS_S<br>(Write only)</td>
			<td colspan="8" align="center">X Position (-1:-8)</td>
		</tr>
		<tr>
			<td>$9F2A</td>
			<td>FX_Y_POS_S<br>(Write only)</td>
			<td colspan="8" align="center">Y/X2 Position (-1:-8)</td>
		</tr>
		<tr>
			<td>$9F2B</td>
			<td>FX_POLY_FILL_L<br>(4-bit Mode=0)<br>(Read only)</td>
			<td align="center">Fill Len >= 16</td>
			<td colspan="2" align="center">X Position (1:0)</td>
			<td colspan="4" align="center">Fill Len (3:0)</td>
			<td align="center">0</td>
		</tr>
		<tr>
			<td>$9F2B</td>
			<td>FX_POLY_FILL_L<br>(4-bit Mode=1, 2-bit Polygon=0)<br>(Read only)</td>
			<td align="center">Fill Len >= 8</td>
			<td colspan="2" align="center">X Position (1:0)</td>
			<td align="center">X Pos. (2)</td>
			<td colspan="3" align="center">Fill Len (2:0)</td>
			<td align="center">0</td>
		</tr>
		<tr>
			<td>$9F2B</td>
			<td>FX_POLY_FILL_L<br>(4-bit Mode=1, 2-bit Polygon=1)<br>(Read only)</td>
			<td align="center">X2 Pos. (-1)</td>
			<td colspan="2" align="center">X Position (1:0)</td>
			<td align="center">X Pos. (2)</td>
			<td colspan="3" align="center">Fill Len (2:0)</td>
			<td align="center">X Pos. (-1)</td>
		</tr>
		<tr>
			<td>$9F2C</td>
			<td>FX_POLY_FILL_H<br>(Read only)</td>
			<td colspan="7" align="center">Fill Len (9:3)</td>
			<td align="center">0</td>
		</tr>
	</table>
</details>

<details open>
	<summary>DCSEL=6</summary>
	<table>
		<tr>
			<th>Addr</th>
			<th>Name</th>
			<th>Bit&nbsp;7</th>
			<th>Bit&nbsp;6</th>
			<th>Bit&nbsp;5 </th>
			<th>Bit&nbsp;4</th>
			<th>Bit&nbsp;3 </th>
			<th>Bit&nbsp;2</th>
			<th>Bit&nbsp;1 </th>
			<th>Bit&nbsp;0</th>
		</tr>
		<tr>
			<td>$9F29</td>
			<td>FX_CACHE_L<br>(Write only)</td>
			<td colspan="8" align="center">Cache (7:0) | Multiplicand (7:0) (signed)</td>
		</tr>
		<tr>
			<td>$9F29</td>
			<td>FX_ACCUM_RESET<br>(Read only)</td>
			<td colspan="8" align="center">Reset Accumulator</td>
		</tr>
		<tr>
			<td>$9F2A</td>
			<td>FX_CACHE_M<br>(Write only)</td>
			<td colspan="8" align="center">Cache (15:8) | Multiplicand (15:8) (signed)</td>
		</tr>
		<tr>
			<td>$9F2A</td>
			<td>FX_ACCUM<br>(Read only)</td>
			<td colspan="8" align="center">Accumulate</td>
		</tr>
		<tr>
			<td>$9F2B</td>
			<td>FX_CACHE_H<br>(Write only)</td>
			<td colspan="8" align="center">Cache (23:16) | Multiplier (7:0) (signed)</td>
		</tr>
		<tr>
			<td>$9F2C</td>
			<td>FX_CACHE_U<br>(Write only)</td>
			<td colspan="8" align="center">Cache (31:24) | Multiplier (15:8) (signed)</td>
		</tr>
	</table>
</details>

<details open>
	<summary>DCSEL=63</summary>
	<table>
		<tr>
			<th>Addr</th>
			<th>Name</th>
			<th>Bit&nbsp;7</th>
			<th>Bit&nbsp;6</th>
			<th>Bit&nbsp;5 </th>
			<th>Bit&nbsp;4</th>
			<th>Bit&nbsp;3 </th>
			<th>Bit&nbsp;2</th>
			<th>Bit&nbsp;1 </th>
			<th>Bit&nbsp;0</th>
		</tr>
		<tr>
			<td>$9F29</td>
			<td>DC_VER0<br>(Read only)</td>
			<td colspan="8" align="center">The ASCII character "V"</td>
		</tr>
		<tr>
			<td>$9F2A</td>
			<td>DC_VER1<br>(Read only)</td>
			<td colspan="8" align="center">Major release</td>
		</tr>
		<tr>
			<td>$9F2B</td>
			<td>DC_VER2<br>(Read only)</td>
			<td colspan="8" align="center">Minor release</td>
		</tr>
		<tr>
			<td>$9F2C</td>
			<td>DC_VER3<br>(Read only)</td>
			<td colspan="8" align="center">Minor build number</td>
		</tr>
	</table>
</details>

## \$9F2D-\$9F3F

<table>
	<tr>
		<th>Addr</th>
		<th>Name</th>
		<th>Bit&nbsp;7</th>
		<th>Bit&nbsp;6</th>
		<th>Bit&nbsp;5 </th>
		<th>Bit&nbsp;4</th>
		<th>Bit&nbsp;3 </th>
		<th>Bit&nbsp;2</th>
		<th>Bit&nbsp;1 </th>
		<th>Bit&nbsp;0</th>
	</tr>
	<tr>
		<td>$9F2D</td>
		<td>L0_CONFIG</td>
		<td colspan="2" align="center">Map Height</td>
		<td colspan="2" align="center">Map Width</td>
		<td colspan="1" align="center">T256C</td>
		<td colspan="1" align="center">Bitmap Mode</td>
		<td colspan="2" align="center">Color Depth</td>
	</tr>
	<tr>
		<td>$9F2E</td>
		<td>L0_MAPBASE</td>
		<td colspan="8" align="center">Map Base Address (16:9)</td>
	</tr>
	<tr>
		<td>$9F2F</td>
		<td>L0_TILEBASE</td>
		<td colspan="6" align="center">Tile Base Address (16:11)</td>
		<td colspan="1" align="center">Tile Height</td>
		<td colspan="1" align="center">Tile Width</td>
	</tr>
	<tr>
		<td>$9F30</td>
		<td>L0_HSCROLL_L</td>
		<td colspan="8" align="center">H-Scroll (7:0)</td>
	</tr>
	<tr>
		<td>$9F31</td>
		<td>L0_HSCROLL_H</td>
		<td colspan="4" align="center">-</td>
		<td colspan="8" align="center">H-Scroll (11:8)</td>
	</tr>
	<tr>
		<td>$9F32</td>
		<td>L0_VSCROLL_L</td>
		<td colspan="8" align="center">V-Scroll (7:0)</td>
	</tr>
	<tr>
		<td>$9F33</td>
		<td>L0_VSCROLL_H</td>
		<td colspan="4" align="center">-</td>
		<td colspan="8" align="center">V-Scroll (11:8)</td>
	</tr>
	<tr>
		<td>$9F34</td>
		<td>L1_CONFIG</td>
		<td colspan="2" align="center">Map Height</td>
		<td colspan="2" align="center">Map Width</td>
		<td colspan="1" align="center">T256C</td>
		<td colspan="1" align="center">Bitmap Mode</td>
		<td colspan="2" align="center">Color Depth</td>
	</tr>
	<tr>
		<td>$9F35</td>
		<td>L1_MAPBASE</td>
		<td colspan="8" align="center">Map Base Address (16:9)</td>
	</tr>
	<tr>
		<td>$9F36</td>
		<td>L1_TILEBASE</td>
		<td colspan="6" align="center">Tile Base Address (16:11)</td>
		<td colspan="1" align="center">Tile Height</td>
		<td colspan="1" align="center">Tile Width</td>
	</tr>
	<tr>
		<td>$9F37</td>
		<td>L1_HSCROLL_L</td>
		<td colspan="8" align="center">H-Scroll (7:0)</td>
	</tr>
	<tr>
		<td>$9F38</td>
		<td>L1_HSCROLL_H</td>
		<td colspan="4" align="center">-</td>
		<td colspan="8" align="center">H-Scroll (11:8)</td>
	</tr>
	<tr>
		<td>$9F39</td>
		<td>L1_VSCROLL_L</td>
		<td colspan="8" align="center">V-Scroll (7:0)</td>
	</tr>
	<tr>
		<td>$9F3A</td>
		<td>L1_VSCROLL_H</td>
		<td colspan="4" align="center">-</td>
		<td colspan="8" align="center">V-Scroll (11:8)</td>
	</tr>
	<tr>
		<td>$9F3B</td>
		<td>AUDIO_CTRL</td>
		<td align="center">FIFO Full / FIFO Reset</td>
		<td align="center">FIFO Empty<br />(read-only)</td>
		<td align="center">16-Bit</td>
		<td align="center">Stereo</td>
		<td colspan="4" align="center">PCM Volume</td>
	</tr>
	<tr>
		<td>$9F3C</td>
		<td>AUDIO_RATE</td>
		<td colspan="8" align="center">PCM Sample Rate</td>
	</tr>
	<tr>
		<td>$9F3D</td>
		<td>AUDIO_DATA</td>
		<td colspan="8" align="center">Audio FIFO data (write-only)</td>
	</tr>
	<tr>
		<td>$9F3E</td>
		<td>SPI_DATA</td>
		<td colspan="8" align="center">Data</td>
	</tr>
	<tr>
		<td>$9F3F</td>
		<td>SPI_CTRL</td>
		<td colspan="1" align="center">Busy</td>
		<td colspan="4" align="center">-</td>
		<td colspan="1" align="center">Auto-TX</td>
		<td colspan="1" align="center">Slow clock</td>
		<td colspan="1" align="center">Select</td>
	</tr>
</table>

## VRAM address space layout

| Address range      | Description                 |
| ------------------ | --------------------------- |
| \$0:0000 - \$1:F9BF | Video RAM                  |
| \$1:F9C0 - \$1:F9FF | PSG registers              |
| \$1:FA00 - \$1:FBFF | Palette                    |
| \$1:FC00 - \$1:FFFF | Sprite attributes          |

The X16 KERNAL uses the following video memory layout:

| Addresses        | Description                                                |
|------------------|------------------------------------------------------------|
| \$0:0000-\$1:2BFF | 320x240@256c Bitmap                                       |
| \$1:2C00-\$1:2FFF | *unused* (1024 bytes)                                     |
| \$1:3000-\$1:AFFF | Sprite Image Data (up to $1000 per sprite at 64x64 8-bit) |
| \$1:B000-\$1:EBFF | Text Mode                                                 |
| \$1:EC00-\$1:EFFF | *unused* (1024 bytes)                                     |
| \$1:F000-\$1:F7FF | Charset                                                   |
| \$1:F800-\$1:F9BF | *unused* (448 bytes)                                      |
| \$1:F9C0-\$1:F9FF | VERA PSG Registers (16 x 4 bytes)                         |
| \$1:FA00-\$1:FBFF | VERA Color Palette (256 x 2 bytes)                        |
| \$1:FC00-\$1:FFFF | VERA Sprite Attributes (128 x 8 bytes)                    |

**This memory map is not fixed**: All of the address space between \$0:0000 and \$1:F9BF is available for any use in your programs, if you do not need text displayed by KERNAL or BASIC. This includes allocating multiple text or graphic buffers, or simply re-arranging the buffers to allow for
certain tile set layouts. Just be aware that once you move things around, you'll have to fully manage your bitmaps, tiles, and text/tile buffers. 

To restore the standard text mode, call `CINT` ($FF81). This will reset the screen to the default screen mode. If you have configured custom settings in your NVRAM, these will be used.

Also, the registers in \$1:F9C0-\$1:FFFF are actually write-only. However, they share the same address as part of the video RAM. Be aware that when you read back the register data, you are actually reading the last value sent by the host system, which is not necessarily the value in the register.
To make sure this data is filled with known values, we recommend fully initializng the registers before use. Normally, the X16 KERNAL handles this for you, but if you are writing a cartridge program, using the system with a custom ROM, or even running VERA on another computer, then you'll 
need to make sure this block gets initialized to known values. 

## Video RAM access
The video RAM (VRAM) isn't directly accessible on the CPU bus. VERA only exposes an address space of 32 bytes to the CPU as described in the section [Registers](#registers). To access the VRAM (which is 128kB in size) an indirection mechanism is used. First the address to be accessed needs to be set (ADDRx_L/ADDRx_M/ADDRx_H) and then the data on that VRAM address can be read from or written to via the DATA0/1 register. To make accessing the VRAM more efficient an auto-increment mechanism is present.

There are 2 data ports to the VRAM. Which can be accessed using DATA0 and DATA1. The address and increment associated with the data port is specified in ADDRx_L/ADDRx_M/ADDRx_H. These 3 registers are multiplexed using the ADDR_SEL in the CTRL register. When ADDR_SEL = 0, ADDRx_L/ADDRx_M/ADDRx_H become ADDR0_L/ADDR0_M/ADDR0_H.  
When ADDR_SEL = 1, ADDRx_L/ADDRx_M/ADDRx_H become ADDR1_L/ADDR1_M/ADDR1_H.

By setting the 'Address Increment' field in ADDRx_H, the address will be increment after each access to the data register. The increment register values and corresponding increment amounts are shown in the following table:

| Register value | Increment amount |
| -------------: | ---------------: |
| 0              | 0                |
| 1              | 1                |
| 2              | 2                |
| 3              | 4                |
| 4              | 8                |
| 5              | 16               |
| 6              | 32               |
| 7              | 64               |
| 8              | 128              |
| 9              | 256              |
| 10             | 512              |
| 11             | 40               |
| 12             | 80               |
| 13             | 160              |
| 14             | 320              |
| 15             | 640              |

Setting the **DECR** bit, will decrement instead of increment by the value set by the 'Address Increment' field.

## Reset

When **RESET** in **CTRL** is set to 1, the FPGA will reconfigure itself. All registers will be reset. The palette RAM will be set to its default values.

## Interrupts

Interrupts will be generated for the interrupt sources set in the lower 4 bits of **IEN**.
**ISR** will indicate the interrupts that have occurred. Writing a 1 to one of the lower 3 bits in **ISR** will clear that interrupt status. **AFLOW** can only be cleared by filling the audio FIFO for at least 1/4.

**IRQ_LINE** (write-only) specifies at which line the **LINE** interrupt will be generated. Note that bit 8 of this value is present in the **IEN** register. For interlaced modes the interrupt will be generated each field and the bit 0 of **IRQ_LINE** is ignored.

**SCANLINE** (read-only) indicates the current scanline being sent to the screen. Bit 8 of this value is present in the **IEN** register. The value is 0 during the first visible line and 479 during the last. This value continues to count beyond the last visible line, but returns $1FF for lines 512-524 that are beyond its 9-bit resolution. **SCANLINE** is not affected by interlaced modes and will return either all even or all odd values during an even or odd field, respectively. Note that VERA renders lines ahead of scanout such that line 1 is being rendered while line 0 is being scanned out. Visible changes may be delayed one scanline because of this.

The upper 4 (read-only) bits of the **ISR** register contain the [sprite collisions](#sprite-collisions) as determined by the sprite renderer.


## Display composer

The display composer is responsible of combining the output of the 2 layer renderers and the sprite renderer into the image that is sent to the video output.

The video output mode can be selected using OUT_MODE in DC_VIDEO.

| OUT_MODE | Description                                        |
| -------: | -------------------------------------------------- |
| 0        | Video disabled                                     |
| 1        | VGA output                                         |
| 2        | NTSC (composite/S-Video)                           |
| 3        | RGB 15KHz, composite or separate H/V sync, via VGA connector |

Setting **'Chroma Disable'** disables output of chroma in NTSC composite mode and will give a better picture on a monochrome display. *(Setting this bit will also disable the chroma output on the S-video output.)*

Setting **'HV Sync'** enables separate HSync/VSync signals in RGB output mode. Clearing the bit will enable the default of composite sync over RGB.

Setting **'240P'** enables 240P progressive mode over NTSC or RGB. It has no effect if the VGA output mode is active. Instead of 262.5 scanlines per field, this mode outputs 263 scanlines per field.  On CRT displays, the scanlines from both the even and odd fields will be displayed on even scanlines.

**'Current Field'** is a read-only bit which reflects the active interlaced field in composite and RGB modes. In non-interlaced modes, this reflects if the current line is even or odd. (0: even, 1: odd)

Setting **'Layer0 Enable'** / **'Layer1 Enable'** / **'Sprites Enable'** will respectively enable output from layer0 / layer1 and the sprites renderer.

**DC_HSCALE** and **DC_VSCALE** will set the fractional scaling factor of the active part of the display. Setting this value to 128 will output 1 output pixel for every input pixel. Setting this to 64 will output 2 output pixels for every input pixel.

**DC_BORDER** determines the palette index which is used for the non-active area of the screen.

**DC_HSTART**/**DC_HSTOP** and **DC_VSTART**/**DC_VSTOP** determines the active part of the screen. The values here are specified in the native 640x480 display space. HSTART=0, HSTOP=640, VSTART=0, VSTOP=480 will set the active area to the full resolution. Note that the lower 2 bits of **DC_HSTART**/**DC_HSTOP** and the lower 1 bit of **DC_VSTART**/**DC_VSTOP** isn't available. This means that horizontally the start and stop values can be set at a multiple of 4 pixels, vertically at a multiple of 2 pixels.

**DC_VER0**, **DC_VER1**, **DC_VER2**, and **DC_VER3** can be queried for the version number of the VERA bitstream.  If reading **DC_VER0** returns `$56`, the remaining registers returns values forming the major, minor, and build numbers respectively.  If **DC_VER0** returns a value other than `$56`, the VERA bitstream version number is undefined.

## Layer 0/1 registers

**'Map Base Address'** specifies the base address of the tile map. *Note that the register only specifies bits 16:9 of the address, so the address is always aligned to a multiple of 512 bytes.*

**'Tile Base Address'** specifies the base address of the tile data. *Note that the register only specifies bits 16:11 of the address, so the address is always aligned to a multiple of 2048 bytes.*

**'H-Scroll'** specifies the horizontal scroll offset. A value between 0 and 4095 can be used. Increasing the value will cause the picture to move left, decreasing will cause the picture to move right.
Hardware scrolling is only possible in tile mode; in bitmap mode, this register is not functional for scrolling. Also half of it is repurposed: the **'H-Scroll (11:8)'** register is instead used to specify the palette offset for the bitmap.

**'V-Scroll'** specifies the vertical scroll offset. A value between 0 and 4095 can be used. Increasing the value will cause the picture to move up, decreasing will cause the picture to move down.
Hardware scrolling is only possible in tile mode; in bitmap mode, this register is not functional.

**'Map Width'**, **'Map Height'** specify the dimensions of the tile map:

| Value | Map width / height |
| ----: | ------------------ |
| 0     | 32 tiles           |
| 1     | 64 tiles           |
| 2     | 128 tiles          |
| 3     | 256 tiles          |

**'Tile Width'**, **'Tile Height'** specify the dimensions of a single tile:

| Value | Tile width / height |
| ----: | ------------------- |
| 0     | 8 pixels            |
| 1     | 16 pixels           |


### Layer display modes

The features of the 2 layers are the same. Each layer supports a few different modes which are specified using **T256C** / **'Bitmap Mode'** / **'Color Depth'** in Lx_CONFIG.

**'Color Depth'** specifies the number of bits used per pixel to encode color information:

| Color Depth | Description |
| ----------: | ----------- |
| 0           | 1 bpp       |
| 1           | 2 bpp       |
| 2           | 4 bpp       |
| 3           | 8 bpp       |

The layer can either operate in tile mode or bitmap mode. This is selected using the **'Bitmap Mode'** bit; 0 selects tile mode, 1 selects bitmap mode.

The handling of 1 bpp tile mode is different from the other tile modes. Depending on the **T256C** bit the tiles use either a 16-color foreground and background color or a 256-color foreground color. Other modes ignore the **T256C** bit.

### Tile mode 1 bpp (16 color text mode)

**T256C** should be set to 0.

**MAP_BASE** points to a tile map containing tile map entries, which are 2 bytes each:

<table>
	<tr>
		<th>Offset</th>
		<th>Bit&nbsp;7</th>
		<th>Bit&nbsp;6</th>
		<th>Bit&nbsp;5</th>
		<th>Bit&nbsp;4</th>
		<th>Bit&nbsp;3</th>
		<th>Bit&nbsp;2</th>
		<th>Bit&nbsp;1</th>
		<th>Bit&nbsp;0</th>
	</tr>
	<tr>
		<td>0</td>
		<td align="center" colspan="8">Character index</td>
	</tr>
	<tr>
		<td>1</td>
		<td align="center" colspan="4">Background color</td>
		<td align="center" colspan="4">Foreground color</td>
	</tr>
</table>

**TILE_BASE** points to the tile data.

Each bit in the tile data specifies one pixel. If the bit is set the foreground color as specified in the map data is used, otherwise the background color as specified in the map data is used.

### Tile mode 1 bpp (256 color text mode)

**T256C** should be set to 1.

**MAP_BASE** points to a tile map containing tile map entries, which are 2 bytes each:

<table>
	<tr>
		<th>Offset</th>
		<th>Bit&nbsp;7</th>
		<th>Bit&nbsp;6</th>
		<th>Bit&nbsp;5</th>
		<th>Bit&nbsp;4</th>
		<th>Bit&nbsp;3</th>
		<th>Bit&nbsp;2</th>
		<th>Bit&nbsp;1</th>
		<th>Bit&nbsp;0</th>
	</tr>
	<tr>
		<td>0</td>
		<td align="center" colspan="8">Character index</td>
	</tr>
	<tr>
		<td>1</td>
		<td align="center" colspan="8">Foreground color</td>
	</tr>
</table>

**TILE_BASE** points to the tile data.

Each bit in the tile data specifies one pixel. If the bit is set the foreground color as specified in the map data is used, otherwise color 0 is used (transparent).

### Tile mode 2/4/8 bpp

**MAP_BASE** points to a tile map containing tile map entries, which are 2 bytes each:

<table>
	<tr>
		<th>Offset</th>
		<th>Bit&nbsp;7</th>
		<th>Bit&nbsp;6</th>
		<th>Bit&nbsp;5</th>
		<th>Bit&nbsp;4</th>
		<th>Bit&nbsp;3</th>
		<th>Bit&nbsp;2</th>
		<th>Bit&nbsp;1</th>
		<th>Bit&nbsp;0</th>
	</tr>
	<tr>
		<td>0</td>
		<td align="center" colspan="8">Tile index (7:0)</td>
	</tr>
	<tr>
		<td>1</td>
		<td align="center" colspan="4">Palette offset</td>
		<td align="center">V-flip</td>
		<td align="center">H-flip</td>
		<td align="center" colspan="2">Tile index (9:8)</td>
	</tr>
</table>

**TILE_BASE** points to the tile data.

Each pixel in the tile data gives a color index of either 0-3 (2bpp), 0-15 (4bpp), 0-255 (8bpp). This color index is modified by the palette offset in the tile map data using the following logic:

* Color index 0 (transparent) and 16-255 are unmodified.
* Color index 1-15 is modified by adding 16 x palette offset.
* T256C causes bit 7 of the color index to become 1.

Note that 2bpp mode packs 4 pixels per byte and 4bpp mode packs 2 pixels per byte. For packed pixels, bit 7 refers to the leftmost pixel and bit 0 refers to the rightmost pixel.

### Bitmap mode 1/2/4/8 bpp

**MAP_BASE** isn’t used in these modes. **TILE_BASE** points to the bitmap data.

**TILEW** specifies the bitmap width. TILEW=0 results in 320 pixels width and TILEW=1 results in 640 pixels width.

When a layer is in bitmap mode, it can no longer be hardware scrolled using the HSCROLL and VSCROLL registers.
**'H-Scroll (7:0)'** and both **'V-Scroll (7:0)'** and **'V-Scroll (11:8)'** are not functional in this mode.

The palette offset (in **'H-Scroll (11:8)'**), as well as T256C in non-1bpp mode modifies the color indexes of the bitmap in the same way as in the tile modes.

## SPI controller

VERA contains a built-in SPI controller. This is connected to both the SD card connector, and the flash chip used for VERA bitstream.

An SPI transfer causes one byte to be clocked out to the slave, simultaneously as one byte is clocked in to the master, one bit at a time.

When JP1 jumper is unconnected, chip-select will select the SD card. When JP1 jumper is connected, chip-select will select the flash chip.

The speed of the clock output of the SPI controller can be controlled by the **'Slow Clock'** bit. When this bit is 0 the clock is 12.5MHz, when 1 the clock is about 390kHz. The slow clock speed is to be used during the initialization phase of the SD card. Some SD cards require a clock less than 400kHz during part of the initialization.

A transfer can be started by writing to **SPI_DATA**. While the transfer is in progress the **BUSY** bit will be set. After the transfer is done, the received byte can be read from the **SPI_DATA** register.

The chip select can be controlled by writing the **SELECT** bit. Writing 1 will assert the chip-select (logic-0) and writing 0 will release the chip-select (logic-1).

If the **Auto-TX** bit is set, reading from **SPI_DATA** will automatically start a new SPI transfer, in addition to returning the latest received value. Useful when reading many consecutive bytes from SPI. The new SPI transfer will transmit the dummy byte $FF.


## Palette

The palette translates 8-bit color indexes into 12-bit output colors. The palette has 256 entries, each with the following format:

<table>
	<tr>
		<th>Offset</th>
		<th>Bit&nbsp;7</th>
		<th>Bit&nbsp;6</th>
		<th>Bit&nbsp;5</th>
		<th>Bit&nbsp;4</th>
		<th>Bit&nbsp;3</th>
		<th>Bit&nbsp;2</th>
		<th>Bit&nbsp;1</th>
		<th>Bit&nbsp;0</th>
	</tr>
	<tr>
		<td>0</td>
		<td align="center" colspan="4">Green</td>
		<td align="center" colspan="4">Blue</td>
	</tr>
	<tr>
		<td>1</td>
		<td align="center" colspan="4">-</td>
		<td align="center" colspan="4">Red</td>
	</tr>
</table>

At reset, the palette will contain a predefined palette:

![A picture of the Commander X16 palette](images/cx16palette.png)

* Color indexes 0-15 contain a palette somewhat similar to the C64 color palette.
* Color indexes 16-31 contain a grayscale ramp.
* Color indexes 32-255 contain various hues, saturation levels, brightness levels.

## Sprite attributes

128 entries of the following format:

<table>
	<tr>
		<th>Offset</th>
		<th>Bit&nbsp;7</th>
		<th>Bit&nbsp;6</th>
		<th>Bit&nbsp;5</th>
		<th>Bit&nbsp;4</th>
		<th>Bit&nbsp;3</th>
		<th>Bit&nbsp;2</th>
		<th>Bit&nbsp;1</th>
		<th>Bit&nbsp;0</th>
	</tr>
	<tr>
		<td>0</td>
		<td align="center" colspan="8">Address (12:5)</td>
	</tr>
	<tr>
		<td>1</td>
		<td>Mode</td>
		<td align="center" colspan="3">-</td>
		<td align="center" colspan="4">Address (16:13)</td>
	</tr>
	<tr>
		<td>2</td>
		<td align="center" colspan="8">X (7:0)</td>
	</tr>
	<tr>
		<td>3</td>
		<td align="center" colspan="6">-</td>
		<td align="center" colspan="2">X (9:8)</td>
	</tr>
	<tr>
		<td>4</td>
		<td align="center" colspan="8">Y (7:0)</td>
	</tr>
	<tr>
		<td>5</td>
		<td align="center" colspan="6">-</td>
		<td align="center" colspan="2">Y (9:8)</td>
	</tr>
	<tr>
		<td>6</td>
		<td align="center" colspan="4">Collision mask</td>
		<td align="center" colspan="2">Z-depth</td>
		<td align="center">V-flip</td>
		<td align="center">H-flip</td>
	</tr>
	<tr>
		<td>7</td>
		<td align="center" colspan="2">Sprite height</td>
		<td align="center" colspan="2">Sprite width</td>
		<td align="center" colspan="4">Palette offset</td>
	</tr>
</table>

| Mode | Description |
| ---- | ----------- |
| 0    | 4 bpp       |
| 1    | 8 bpp       |

| Z-depth | Description                           |
| ------- | ------------------------------------- |
| 0       | Sprite disabled                       |
| 1       | Sprite between background and layer 0 |
| 2       | Sprite between layer 0 and layer 1    |
| 3       | Sprite in front of layer 1            |

| Sprite width / height | Description |
| --------------------- | ----------- |
| 0                     | 8 pixels    |
| 1                     | 16 pixels   |
| 2                     | 32 pixels   |
| 3                     | 64 pixels   |

**Rendering Priority** The sprite memory location dictates the order in which it is rendered. The sprite whose attributes are at the lowest location will be rendered in front of all other sprites; the sprite at the highest location will be rendered behind all other sprites, and so forth.

**Palette offset** works in the same way as with the layers.

## Composite video

### Color bleed
CRT Televisions and composite monitors experience color bleeding when certain colors are placed next to each other.  Color bleed is especially apparent when choosing text color against certain background colors.  Sprite pixel colors, character colors, and tiles will require careful color choice for better contrast.  This chart shows which color combinations to avoid, and which work especially well together.

<img src="images/CompositeColors.png">

### Overscan

Overscan is the border region in composite televisions and monitors that extend off screen.  This overscan region varies by device, so there are no exact pixel measurements to describe the overscan region.  Enabling the border can be a guideline for the visible draw region.

<img src="images/CompositeOverscan.png">

A game or application developer can use techniques adjust on-screen artifacts when composite video is in use.  

- V-scale and H-scale registers to shrink the screen 
- move some of the screen assets in closer
- develop in a screen mode with an enabled border

Setting to screen mode 3 or 11 while RGB or NTSC out is selected will also set 240p mode for games that are 320x240.  However, a high resolution program may have poor presentation in 240p.

## Sprite collisions

At the start of the vertical blank **Collisions** in **ISR** is updated. This field indicates which groups of sprites have collided. If the field is non-zero the **SPRCOL** interrupt will be set. The interrupt is generated once per field / frame and can be cleared by making sure the sprites no longer collide.

*Note that collisions are only detected on lines that are actually rendered. This can result in subtle differences between non-interlaced and interlaced video modes.*


## VERA FX

The FX feature set is available in VERA firmware version v0.3.1 or later. The Commander X16 emulators also have this feature officially as of R44.

FX is a set of mainly addressing mode changes. VERA FX does not accelerate rendering, but it merely assists the CPU with some of the slower tasks, and when used cleverly, can allow for the programmer to perform some limited perspective transforms or basic 3D effects.

FX features are controlled mainly by registers $9F29-$9F2C with DCSEL set to 2 through 6.  FX_CTRL ($9F29 w/ DCSEL=2) is the master switch for enabling or disabling FX behaviors.  When writing an application that uses FX, it is important that the FX mode be preserved and disabled in interrupt handlers in cases where the handler accesses VERA registers or VRAM, including the PSG sound registers. Reading from FX_CTRL returns the current state, and writing 0 to FX_CTRL suspends the FX behaviors so that the VERA can be accessed normally without mutating other FX state.

Preliminary documentation for the feature can be found in [Chapter 10](X16%20Reference%20-%2010%20-%20VERA%20FX%20Reference.md#chapter-10-vera-fx-reference), but as this is a brand new
 feature, examples and documentation still need to be written.

## Audio

The audio functionality contains of 2 independent systems. The first is the PSG or Programmable Sound Generator. The second is the PCM (or Pulse-Code Modulation) playback system.

### Programmable Sound Generator (PSG)

The PSG consists of 16 voices, each with their own set of registers:

<table>
	<tr>
		<th>Offset</th>
		<th>Bit&nbsp;7</th>
		<th>Bit&nbsp;6</th>
		<th>Bit&nbsp;5</th>
		<th>Bit&nbsp;4</th>
		<th>Bit&nbsp;3</th>
		<th>Bit&nbsp;2</th>
		<th>Bit&nbsp;1</th>
		<th>Bit&nbsp;0</th>
	</tr>
	<tr>
		<td>0</td>
		<td align="center" colspan="8">Frequency word (7:0)</td>
	</tr>
	<tr>
		<td>1</td>
		<td align="center" colspan="8">Frequency word (15:8)</td>
	</tr>
	<tr>
		<td>2</td>
		<td align="center" colspan=1">Right</td>
		<td align="center" colspan=1">Left</td>
		<td align="center" colspan=6">Volume</td>
	</tr>
	<tr>
		<td>3</td>
		<td align="center" colspan="2">Waveform</td>
		<td align="center" colspan="6">Pulse Width / XOR</td>
	</tr>
</table>

**Frequency word** sets the frequency of the sound.
The formula for calculating the output frequency is:

    sample_rate = 25MHz / 512 = 48828.125 Hz

    output_frequency = sample_rate / (2^17) * frequency_word

Thus the output frequency can be set in steps of about 0.373 Hz.

*Example: to output a frequency of 440Hz (note A4) the **Frequency word** should be set to  440 / (48828.125 / (2^17)) = 1181*

**Volume** controls the volume of the sound with a logarithmic curve; 0 is silent, 63 ($3F)
is the loudest. The **Left** and **Right** bits control to which channels the sound
should be output.

**Waveform** controls the waveform of the sound:

| Waveform | Description |
| -------: | ----------- |
| 0        | Pulse       |
| 1        | Sawtooth    |
| 2        | Triangle    |
| 3        | Noise       |

**Pulse Width / XOR** controls the duty cycle of the pulse waveform or the XOR 
permutation when used with the triangle or saw. For pulse, a value of 63 ($3F) will
give a 50% duty cycle or square wave, 0 will give a very narrow pulse.

When the triangle or saw waveform is selected, the value influences an XOR calculation
that changes the resulting waveform. This is most noticeable with the triangle waveform.
It can be used to provide an NES-like fuzzy triangle as well as an overdriven saw sound
(similar to the VRC6 NES chip) among several other varieties of sounds.

When used with the saw, the result is more subtle. It adds some overtones to the saw.

Setting the PW/XOR to 0 for Tri/Saw inverts the waveform from what it was prior
to the addition of the XOR feature, and PW of 63 results in the original waveform.
Be aware of phasing effects that this difference could cause.

**Noise** Just like the other waveform types, the frequency of the noise waveform can be controlled using frequency. In this case a higher frequency will give brighter noise and a lower value will give darker noise. The PWM/XOR values do not influence
the noise shape.

### PCM audio

For PCM playback, VERA contains a 4kB FIFO buffer. This buffer needs to be filled in a timely fashion by the CPU. To facilitate this an **AFLOW** (Audio FIFO low) interrupt can be generated when the FIFO is less than 1/4 filled.

#### Audio registers

#### `AUDIO_CTRL ($9F3B)` ####

**FIFO Full** (bit 7) is a read-only flag that indicates whether the FIFO is full. Any writes to the FIFO while this flag is 1 will be ignored. Writing a 1 to this register
**FIFO Reset** will perform a FIFO reset, which will clear the contents of the FIFO buffer.

**FIFO Empty** (bit 6) is a read-only flag that indicates whether the FIFO is empty.

**16-bit** (bit 5) sets the data format to 16-bit. If this bit is 0, 8-bit data is expected.

**Stereo** (bit 4) sets the data format to stereo. If this bit is 0 (mono), the same audio data is send to both channels.

**PCM Volume** (bits 0..3)controls the volume of the PCM playback, this has a logarithmic curve. A value of 0 is silence, 15 is the loudest.

##### `AUDIO_RATE ($9F3C)` #####

**PCM sample rate** controls the speed at which samples are read from the FIFO. A few example values:

| PCM sample rate | Description                                 |
| --------------: | ------------------------------------------- |
| 128             | normal speed   (25MHz / 512 = 48828.125 Hz) |
| 64              | half speed     (24414 Hz)                   |
| 32              | quarter speed  (12207 Hz)                   |
| 0               | stop playback                               |
| *>128*          | *invalid*                                   |

Using a value of 128 will give the best quality (lowest distortion); at this value for every output sample, an input sample from the FIFO is read. Lower values will output the same sample multiple times to the audio DAC. Input samples are always read as a complete set (being 1/2/4 bytes).

##### `AUDIO_DATA ($9F3D)` #####

**Audio FIFO data** Writes to this register add one byte to the PCM FIFO. If the FIFO is full, the write will be ignored.

*NOTE: When setting up for PCM playback it is advised to first set the sample rate at 0 to stop playback. First fill the FIFO buffer with some initial data and then set the desired sample rate. This can prevent undesired FIFO underruns.*


### Audio data formats

Audio data is two's complement signed.
Depending on the selected mode the data needs to be written to the FIFO in the following order:

| Mode          | Order in which to write data to FIFO                                                        |
| ------------- | ------------------------------------------------------------------------------------------- |
| 8-bit mono    | &lt;mono sample&gt;                                                                             |
| 8-bit stereo  | &lt;left sample&gt; &lt;right sample&gt;                                                            |
| 16-bit mono   | &lt;mono sample (7:0)&gt; &lt;mono sample (15:8)&gt;                                                |
| 16-bit stereo | &lt;left sample (7:0)&gt; &lt;left sample (15:8)&gt; &lt;right sample (7:0)&gt; &lt;right sample (15:8)&gt; |

<!-- For PDF formatting -->
<div class="page-break"></div>

# Chapter 10: VERA FX Reference

*Author: MooingLemur, based on documentation written by JeffreyH*

**This is preliminary documentation and the specification can still change at any point.**

# Introduction

This is a reference for the VERA FX features.  It is meant to be a complement to the tutorial, currently found [here](https://docs.google.com/document/d/1q34uWOiM3Be2pnaHRVgSdHySI-qsiQWPTo_gfE54PTg).

The FX Update mainly adds "helpers" inside of VERA that can be used by the CPU. There is no "magic button" that allows you to do 3D graphics for example. It mainly helps at certain CPU time-consuming tasks, most notably the ones that are present in the (deep) inner-loop of a game/graphics engine. The FX Update does therefore not fundamentally change the architecture or nature of VERA, it extends and improves it.

In other words: the CPU is still the orchestrator of all that is done, but it is alleviated from certain operations where it is not (very) good at or does not have direct access to.

**FX Update extends addressing modes, it does not add or extend renderers.**

# Usage

### DCSEL

VERA is mapped as 32 8-bit registers in the memory space of the Commander X16, starting at address \$9F20 and ending at \$9F3F. Many of these are (fully) used, but some bits remain unused. The DCSEL bits in register \$9F25 (also called CTRL) has been extended to 6-bits to allow for the 4 registers \$9F29-\$9F2C to have additional meanings.

<table>
	<tr>
		<th>Addr</th>
		<th>Name</th>
		<th>Bit&nbsp;7</th>
		<th>Bit&nbsp;6</th>
		<th>Bit&nbsp;5</th>
		<th>Bit&nbsp;4</th>
		<th>Bit&nbsp;3</th>
		<th>Bit&nbsp;2</th>
		<th>Bit&nbsp;1</th>
		<th>Bit&nbsp;0</th>
	</tr>
	<tr>
		<td>$9F25</td>
		<td>CTRL</td>
		<td colspan="1" align="center">Reset</td>
		<td colspan="6" align="center"><b>DCSEL</b><br><img src="images/redunderline.png"></td>
		<td colspan="1" align="center">ADDRSEL</td>
	</tr>
</table>

The FX features use DCSEL values 2, 3, 4, 5, and 6. This effectively gives FX 20 8-bit registers. Note that 15 of these registers are *write-only*, 2 of them are *read-only* and 3 are both *readable* and *writable*.  In addition, DCSEL value 63 is read-only, and reports the VERA version.  DCSEL values 7-62 are currently unused, but behave like DCSEL value 63.

***Important***: *If the only DCSEL values used are 0 and 1, the behavior of VERA is exactly the same as it was before the FX update. This ensures that the FX update is backwards compatible with traditional non-FX uses of VERA.*

### Addr1 Mode

When DCSEL=2, the main FX configuration register becomes available (FX_CTRL/$9F29), which is both readable and writable. The 2 lower bits are the addr1 mode bits, which will change the behavior of how and when ADDR1 is updated. This puts the FX helpers in a certain "role". 

<table>
	<tr>
		<th>Addr</th>
		<th>Name</th>
		<th>Bit&nbsp;7</th>
		<th>Bit&nbsp;6</th>
		<th>Bit&nbsp;5</th>
		<th>Bit&nbsp;4</th>
		<th>Bit&nbsp;3</th>
		<th>Bit&nbsp;2</th>
		<th>Bit&nbsp;1</th>
		<th>Bit&nbsp;0</th>
	</tr>
	<tr>
		<td>$9F29</td>
		<td>FX_CTRL<br>(DCSEL=2)</td>
		<td align="center">Transp. Writes</td>
		<td align="center">Cache Write Enable</td>
		<td align="center">Cache Fill Enable</td>
		<td align="center">One-byte Cache Cycling</td>
		<td align="center">16-bit Hop</td>
		<td align="center">4-bit Mode</td>
		<td colspan="2" align="center"><b>Addr1 Mode</b><br><img src="images/redunderline.png"></td>
	</tr>
</table>

|Addr1 Mode|Description|
|-|-|
|0|Traditional VERA behavior|
|1|Line draw helper|
|2|Polygon filler helper|
|3|Affine helper|


By default, Addr1 Mode is set to 0 (=00b), which is the **normal** and already-known behavior of `ADDR1`.

<!-- For PDF formatting -->
<div class="page-break"></div>

# Line draw helper

When Addr1 Mode is set to 1 (=01b) the **line draw helper** is enabled.

### Setting up the line draw helper

* Set `ADDR1` to the address of the starting pixel
* Determine the octant (see below) you are going to draw in, which will inform your `ADDR0` and `ADDR1` increments.
	* Set `ADDR1` increment in the direction you will ***always*** increment each step
		* For 8-bit mode: (+1, -1, -320, or +320)
		* For 4-bit mode: (-0.5, +0.5, -160, or +160)
	* Set `ADDR0` increment in the direction you will ***sometimes*** increment. Even though this is the increment for `ADDR0`, we are using it in line draw mode as an incrementer for `ADDR1`.
		* For 8-bit mode: (+1, -1, -320, or +320).
		* For 4-bit mode: (-0.5, +0.5, -160, or +160)
	* For 4-bit mode, the half increments are set via the Nibble Increment bit and optionally the DECR bit in `ADDRx_H`. For the Nibble Increment bit to have effect, the main Address Increment must be set to 0, and the 4-bit Mode bit must be set in FX_CTRL ($9F29, DCSEL=2).
<table>
	<tr>
		<th>Addr</th>
		<th>Name</th>
		<th>Bit&nbsp;7</th>
		<th>Bit&nbsp;6</th>
		<th>Bit&nbsp;5</th>
		<th>Bit&nbsp;4</th>
		<th>Bit&nbsp;3</th>
		<th>Bit&nbsp;2</th>
		<th>Bit&nbsp;1</th>
		<th>Bit&nbsp;0</th>
	</tr>
	<tr>
		<td>$9F22</td>
		<td>ADDRx_H (x=ADDRSEL)</td>
		<td colspan="4" align="center">Address Increment</td>
		<td align="center"><b>DECR</b><br><img src="images/redunderline.png"></td>
		<td align="center"><b>Nibble Increment</b><br><img src="images/redunderline.png"></td>
		<td align="center">Nibble Address</td>
		<td align="center">VRAM Address (16)</td>
	</tr>
</table>

![Figure 1, The 8 octants](images/fx_fig1.png)

|Octant|8-bit `ADDR1` increment|8-bit `ADDR0` increment|4-bit `ADDR1` increment|4-bit `ADDR0` increment|
|-|-|-|-|-|
|0|+1|-320|+0.5|-160|
|1|-320|+1|-160|+0.5|
|2|-320|-1|-160|-0.5|
|3|-1|-320|-0.5|-160|
|4|-1|+320|-0.5|+160|
|5|+320|-1|+160|-0.5|
|6|+320|+1|+160|+0.5|
|7|+1|+320|+0.5|+160|

* Set your slope into the two "X Increment" registers (DCSEL=3, see below). Note that increment registers are 15-bit signed fixed-point numbers, and for this mode, the range should be 0.0 to 1.0 inclusive, so you'll either want to store the value of 1, or you'll want to set only the fractional part.

<table>
	<tr>
		<th>Addr</th>
		<th>Name</th>
		<th>Bit&nbsp;7</th>
		<th>Bit&nbsp;6</th>
		<th>Bit&nbsp;5</th>
		<th>Bit&nbsp;4</th>
		<th>Bit&nbsp;3</th>
		<th>Bit&nbsp;2</th>
		<th>Bit&nbsp;1</th>
		<th>Bit&nbsp;0</th>
	</tr>
	<tr>
		<td>$9F29</td>
		<td>FX_X_INCR_L<br>(DCSEL=3)<br>(Write only)</td>
		<td colspan="8" align="center"><b>X Increment (-2:-9) (signed)</b><br><img src="images/redunderline.png"></td>
	</tr>
	<tr>
		<td>$9F2A</td>
		<td>FX_X_INCR_H<br>(DCSEL=3)<br>(Write only)</td>
		<td align="center">X Incr. 32x</td>
		<td colspan="5" align="center">X Increment (5:1) (signed)</td>
		<td align="center"><b>X Incr. (0)</b><br><img src="images/redunderline.png"></td>
		<td align="center"><b>X Incr. (-1)</b><br><img src="images/redunderline.png"></td>
	</tr>
</table>

*Note: Of the two incrementers, the line draw helper uses only the X incrementer. However depending on the octant you are drawing in, this incrementer will be used to depict either x or y pixel increments. So the "X" should not be taken literally here, it just means the first of the two incrementers.*

* As a side effect of in line draw mode, by setting `FX_X_INCR_H` ($9F2A, DCSEL=3), the fractional part (the lower 9 bits) of *X Position* are automatically set to half a pixel. Furthermore, the lowest bit of the pixel position (which acts as an overflow bit) is set to 0 as well. This effectively sets the starting X-position to 0.5 (the center) of a pixel.


*Note: There is no need to set the higher bits of the X position, since the FX X position (accumulator) is only used to track the fractional (subpixel) part of the line draw.*

<!-- For PDF formatting -->
<div class="page-break"></div>

## Polygon filler helper

When Addr1 Mode is set to 2 (=10b) the polygon filler helper is enabled.

### Setting up the polygon filler helper

Assuming a 320 pixel-wide screen
* Set `ADDR0` to the address of the y-position of the top point of the triangle and x=0 (so on the left of the screen). Set its increment to +320 (for 8-bit mode) or +160 (for 4-bit mode).
	* Note: `ADDR0` is used as "base address" for calculating `ADDR1` for each horizontal line of the triangle. `ADDR0` should therefore start at the top of the triangle and increment exactly one line each time.
	* There is no need to set `ADDR1`. This is done by VERA.
* Calculate your slopes (dx/dy) for both the left and right point. Unlike the line draw helper, these slopes can be negative and can exceed 1.0. They are not dependent on octant, but cover the whole 180 degrees downwards. Below is an illustration of some (not-to-scale) examples of increments:
![Figure 2, examples of Bresenham's slope increment values](images/fx_fig2.png)
* Set `ADDR1` increment to +1 (for 8-bit mode) or +0.5 (for 4-bit mode)
	* `ADDR1` increment can also be +4 if you use 32-bit cache writes, explained later)
* Set your left slope into the two "X increment" registers and your right slope into the two "Y increment" registers (DCSEL=3, see below).
	* Important: They should be set to half the increment (or decrement) per horizontal line! This is because the polygon filler increments in two steps per line.
* Note that increment registers are 15-bit signed fixed-point numbers:
* 6 bits for the integer pixel increment 
* 9 bits for the fractional (subpixel) increment
* 1 additional bit that indicates the actual value should be multiplied by 32

<table>
	<tr>
		<th>Addr</th>
		<th>Name</th>
		<th>Bit&nbsp;7</th>
		<th>Bit&nbsp;6</th>
		<th>Bit&nbsp;5</th>
		<th>Bit&nbsp;4</th>
		<th>Bit&nbsp;3</th>
		<th>Bit&nbsp;2</th>
		<th>Bit&nbsp;1</th>
		<th>Bit&nbsp;0</th>
	</tr>
	<tr>
		<td>$9F29</td>
		<td>FX_X_INCR_L<br>(DCSEL=3)<br>(Write only)</td>
		<td colspan="8" align="center">X Increment (-2:-9) (signed)</td>
	</tr>
	<tr>
		<td>$9F2A</td>
		<td>FX_X_INCR_H<br>(DCSEL=3)<br>(Write only)</td>
		<td align="center">X Incr. 32x</td>
		<td colspan="6" align="center">X Increment (5:0) (signed)</td>
		<td align="center">X Incr. (-1)</
	</tr>
	<tr>
		<td>$9F2B</td>
		<td>FX_Y_INCR_L<br>(DCSEL=3)<br>(Write only)</td>
		<td colspan="8" align="center">Y/X2 Increment (-2:-9) (signed)</td>
	</tr>
	<tr>
		<td>$9F2C</td>
		<td>FX_Y_INCR_H<br>(DCSEL=3)<br>(Write only)</td>
		<td align="center">Y/X2 Incr. 32x</td>
		<td colspan="6" align="center">Y/X2 Increment (5:0) (signed)</td>
		<td align="center">Y/X2 Incr. (-1)</
	</tr>
</table>

* Due to the fact that we are in "polygon fill"-mode, by setting the high bits of the "X increment" ($9F2A, DCSEL=3), the "X position" (the lower 9 bits of the position in DCSEL=4 and DCSEL=5) are automatically set to half a pixel. The same goes for the high bits of the Y/X2 increment ($9F2C, DCSEL=3) and Y/X2 position. 
* Set the "X position" and "Y/X2 position” to the x-pixel-position of the top triangle point.

<table>
	<tr>
		<th>Addr</th>
		<th>Name</th>
		<th>Bit&nbsp;7</th>
		<th>Bit&nbsp;6</th>
		<th>Bit&nbsp;5</th>
		<th>Bit&nbsp;4</th>
		<th>Bit&nbsp;3</th>
		<th>Bit&nbsp;2</th>
		<th>Bit&nbsp;1</th>
		<th>Bit&nbsp;0</th>
	</tr>
	<tr>
		<td>$9F29</td>
		<td>FX_X_POS_L<br>(DCSEL=4)<br>(Write only)</td>
		<td colspan="8" align="center"><b>X Position (7:0)</b><br><img src="images/redunderline.png"></td>
	</tr>
	<tr>
		<td>$9F2A</td>
		<td>FX_X_POS_H<br>(DCSEL=4)<br>(Write only)</td>
		<td align="center">X Pos. (-9)</td>
		<td colspan="4" align="center">-</td>
		<td colspan="3" align="center"><b>X Position (10:8)</b><br><img src="images/redunderline.png"></td>
	</tr>
	<tr>
		<td>$9F2B</td>
		<td>FX_Y_POS_L<br>(DCSEL=4)<br>(Write only)</td>
		<td colspan="8" align="center"><b>Y/X2 Position (7:0)</b><br><img src="images/redunderline.png"></td>
	</tr>
	<tr>
		<td>$9F2C</td>
		<td>FX_Y_POS_H<br>(DCSEL=4)<br>(Write only)</td>
		<td align="center">Y/X2 Pos. (-9)</td>
		<td colspan="4" align="center">-</td>
		<td colspan="3" align="center"><b>Y/X2 Position (10:8)</b><br><img src="images/redunderline.png"></td>
	</tr>
</table>

Steps that are needed for filling a triangle part with lines:
* Read from `DATA1`
	* This will not return any useful data but will do two things in the background:
		* Increment/decrement the X1 and X2 positions by their corresponding increment values.
		* Set `ADDR1` to `ADDR0` + X1

* Then read the “Fill length (low)”-register.  Its output depends on whether you're in 4 or 8-bit mode.
<table>
	<tr>
		<th>Addr</th>
		<th>Name</th>
		<th>Bit&nbsp;7</th>
		<th>Bit&nbsp;6</th>
		<th>Bit&nbsp;5</th>
		<th>Bit&nbsp;4</th>
		<th>Bit&nbsp;3</th>
		<th>Bit&nbsp;2</th>
		<th>Bit&nbsp;1</th>
		<th>Bit&nbsp;0</th>
	</tr>
	<tr>
		<td>$9F2B</td>
		<td>FX_POLY_FILL_L<br>(DCSEL=5, 4-bit Mode=0)<br>(Read only)</td>
		<td align="center">Fill Len >= 16</td>
		<td colspan="2" align="center">X Position (1:0)</td>
		<td colspan="4" align="center">Fill Len (3:0)</td>
		<td align="center">0</td>
	</tr>
	<tr>
		<td>$9F2B</td>
		<td>FX_POLY_FILL_L<br>(DCSEL=5, 4-bit Mode=1, 2-bit Polygon=0)<br>(Read only)</td>
		<td align="center">Fill Len >= 8</td>
		<td colspan="2" align="center">X Position (1:0)</td>
		<td align="center">X Pos. (2)</td>
		<td colspan="3" align="center">Fill Len (2:0)</td>
		<td align="center">0</td>
	</tr>
</table>
* If fill_len >= 16 (or >= 8 in 4-bit mode) then also read the “Fill length (high)”-register:
<table>
	<tr>
		<th>Addr</th>
		<th>Name</th>
		<th>Bit&nbsp;7</th>
		<th>Bit&nbsp;6</th>
		<th>Bit&nbsp;5</th>
		<th>Bit&nbsp;4</th>
		<th>Bit&nbsp;3</th>
		<th>Bit&nbsp;2</th>
		<th>Bit&nbsp;1</th>
		<th>Bit&nbsp;0</th>
	</tr>
	<tr>
		<td>$9F2C</td>
		<td>FX_POLY_FILL_H<br>(DCSEL=5)<br>(Read only)</td>
		<td colspan="7" align="center">Fill Len (9:3)</td>
		<td align="center">0</td>
	</tr>
</table>
**Important**: when the two highest bits of Fill Len (bits 8 and 9) are both 1, it means there is a negative fill length. The line should not be drawn!

* Together they give you 10-bits of fill length (ignore the other bits for now). Since `ADDR1` is already set properly you can immediately start drawing this number of pixels (given by Fill Len).
	* `sta DATA1` ; as many times as Fill Len states
* Then read from `DATA0`: this will (also) increment X1 and X2
* Check if all lines of this triangle part have been drawn, if not go to the first step.

There is also a 2-bit polygon mode, which is better explained in the [tutorial](https://docs.google.com/document/d/1q34uWOiM3Be2pnaHRVgSdHySI-qsiQWPTo_gfE54PTg)


## Affine helper

When Addr1 Mode is set to 3 (=11b) the affine (transformation) helper is enabled.

When reading from ADDR1 in this mode, the affine helper reads tile data from a special tile area defined by two new FX registers:
* FX_TILEBASE is pointed to a set of 8x8 tiles in either 4-bit or 8-bit depth. FX can support up to 256 tile definitions, and can overlap the traditional layer tile bases.
* FX_MAPBASE points to a square-shaped tile map, one byte per tile. This tile map has no attribute bytes. unlike the traditional layer 0/1 tile maps.

<table>
	<tr>
		<th>Addr</th>
		<th>Name</th>
		<th>Bit&nbsp;7</th>
		<th>Bit&nbsp;6</th>
		<th>Bit&nbsp;5</th>
		<th>Bit&nbsp;4</th>
		<th>Bit&nbsp;3</th>
		<th>Bit&nbsp;2</th>
		<th>Bit&nbsp;1</th>
		<th>Bit&nbsp;0</th>
	</tr>
	<tr>
		<td>$9F2A</td>
		<td>FX_TILEBASE<br>(DCSEL=2)<br>(Write only)</td>
		<td colspan="6" align="center"><b>FX Tile Base Address (16:11)</b><br><img src="images/redunderline.png"></td>
		<td align="center"><b>Affine Clip Enable</b><br><img src="images/redunderline.png"></td>
		<td align="center">2-bit Polygon</td>
	</tr>
	<tr>
		<td>$9F2B</td>
		<td>FX_MAPBASE<br>(DCSEL=2)<br>(Write only)</td>
		<td colspan="6" align="center"><b>FX Map Base Address (16:11)</b><br><img src="images/redunderline.png"></td>
		<td colspan="2" align="center"><b>Map Size</b><br><img src="images/redunderline.png"></td>
	</tr>
</table>

* **Affine Clip Enable** changes the behavior when the X/Y positions are outside of the tile map such that it always reads data from tile 0. The default behavior is to wrap the X/Y position to the opposite side of the map.
* **Map Size** is a 2 bit value that affects both the width and height of the tile map.

|Map Size|Dimensions|
|-|-|
|0|2×2|
|1|8×8|
|2|32×32|
|3|128×128|

* The **Transparent Writes** toggle in FX_CTRL is especially useful in Affine helper mode.  Setting this toggle causes a write of zero to leave the byte (or the nibble) at the target address intact.  This toggle is not limited to affine helper mode, and it affects writes to both DATA0 and DATA1.

<table>
	<tr>
		<th>Addr</th>
		<th>Name</th>
		<th>Bit&nbsp;7</th>
		<th>Bit&nbsp;6</th>
		<th>Bit&nbsp;5</th>
		<th>Bit&nbsp;4</th>
		<th>Bit&nbsp;3</th>
		<th>Bit&nbsp;2</th>
		<th>Bit&nbsp;1</th>
		<th>Bit&nbsp;0</th>
	</tr>
	<tr>
		<td>$9F29</td>
		<td>FX_CTRL<br>(DCSEL=2)</td>
		<td align="center"><b>Transp. Writes</b><br><img src="images/redunderline.png"></td>
		<td align="center">Cache Write Enable</td>
		<td align="center">Cache Fill Enable</td>
		<td align="center">One-byte Cache Cycling</td>
		<td align="center">16-bit Hop</td>
		<td align="center">4-bit Mode</td>
		<td colspan="2" align="center">Addr1 Mode</td>
	</tr>
</table>

When using the affine helper, the X and Y position registers (DCSEL=4) are used to set ADDR1 to the source pixel indirectly in the aforementioned tile map, while the X and Y increments determine the step after each read of ADDR1.

<table>
	<tr>
		<th>Addr</th>
		<th>Name</th>
		<th>Bit&nbsp;7</th>
		<th>Bit&nbsp;6</th>
		<th>Bit&nbsp;5</th>
		<th>Bit&nbsp;4</th>
		<th>Bit&nbsp;3</th>
		<th>Bit&nbsp;2</th>
		<th>Bit&nbsp;1</th>
		<th>Bit&nbsp;0</th>
	</tr>
	<tr>
		<td>$9F29</td>
		<td>FX_X_POS_L<br>(DCSEL=4)<br>(Write only)</td>
		<td colspan="8" align="center"><b>X Position (7:0)</b><br><img src="images/redunderline.png"></td>
	</tr>
	<tr>
		<td>$9F2A</td>
		<td>FX_X_POS_H<br>(DCSEL=4)<br>(Write only)</td>
		<td align="center">X Pos. (-9)</td>
		<td colspan="4" align="center">-</td>
		<td colspan="3" align="center"><b>X Position (10:8)</b><br><img src="images/redunderline.png"></td>
	</tr>
	<tr>
		<td>$9F2B</td>
		<td>FX_Y_POS_L<br>(DCSEL=4)<br>(Write only)</td>
		<td colspan="8" align="center"><b>Y/X2 Position (7:0)</b><br><img src="images/redunderline.png"></td>
	</tr>
	<tr>
		<td>$9F2C</td>
		<td>FX_Y_POS_H<br>(DCSEL=4)<br>(Write only)</td>
		<td align="center">Y/X2 Pos. (-9)</td>
		<td colspan="4" align="center">-</td>
		<td colspan="3" align="center"><b>Y/X2 Position (10:8)</b><br><img src="images/redunderline.png"></td>
	</tr>
</table>

The affine helper supports the full range of X and Y increment values, including negative values.

<table>
	<tr>
		<th>Addr</th>
		<th>Name</th>
		<th>Bit&nbsp;7</th>
		<th>Bit&nbsp;6</th>
		<th>Bit&nbsp;5</th>
		<th>Bit&nbsp;4</th>
		<th>Bit&nbsp;3</th>
		<th>Bit&nbsp;2</th>
		<th>Bit&nbsp;1</th>
		<th>Bit&nbsp;0</th>
	</tr>
	<tr>
		<td>$9F29</td>
		<td>FX_X_INCR_L<br>(DCSEL=3)<br>(Write only)</td>
		<td colspan="8" align="center">X Increment (-2:-9) (signed)</td>
	</tr>
	<tr>
		<td>$9F2A</td>
		<td>FX_X_INCR_H<br>(DCSEL=3)<br>(Write only)</td>
		<td align="center">X Incr. 32x</td>
		<td colspan="6" align="center">X Increment (5:0) (signed)</td>
		<td align="center">X Incr. (-1)</
	</tr>
	<tr>
		<td>$9F2B</td>
		<td>FX_Y_INCR_L<br>(DCSEL=3)<br>(Write only)</td>
		<td colspan="8" align="center">Y/X2 Increment (-2:-9) (signed)</td>
	</tr>
	<tr>
		<td>$9F2C</td>
		<td>FX_Y_INCR_H<br>(DCSEL=3)<br>(Write only)</td>
		<td align="center">Y/X2 Incr. 32x</td>
		<td colspan="6" align="center">Y/X2 Increment (5:0) (signed)</td>
		<td align="center">Y/X2 Incr. (-1)</
	</tr>
</table>

## 32-bit cache

When the CPU reads a byte via DATA0 or DATA1, and "cache fill enable" is set, the value read will be copied into an indexed location inside the 32-bit cache.

<table>
	<tr>
		<th>Addr</th>
		<th>Name</th>
		<th>Bit&nbsp;7</th>
		<th>Bit&nbsp;6</th>
		<th>Bit&nbsp;5</th>
		<th>Bit&nbsp;4</th>
		<th>Bit&nbsp;3</th>
		<th>Bit&nbsp;2</th>
		<th>Bit&nbsp;1</th>
		<th>Bit&nbsp;0</th>
	</tr>
	<tr>
		<td>$9F29</td>
		<td>FX_CTRL<br>(DCSEL=2)</td>
		<td align="center">Transp. Writes</td>
		<td align="center">Cache Write Enable</td>
		<td align="center"><b>Cache Fill Enable</b><br><img src="images/redunderline.png"></td>
		<td align="center">One-byte Cache Cycling</td>
		<td align="center">16-bit Hop</td>
		<td align="center">4-bit Mode</td>
		<td colspan="2" align="center">Addr1 Mode</td>
	</tr>
</table>

 In 8-bit mode, a byte is cached, but in 4-bit mode, a nibble is cached instead. Afterwards, by default, the index into the cache is incremented, and loops back around to 0 after the last index.  The index can be set explicitly via the FX_MULT register.  8-bit mode uses bits 3:2 and ranges from 0-3.  4-bit mode uses bits 3:1 and ranges from 0-7.

<table>
	<tr>
		<th>Addr</th>
		<th>Name</th>
		<th>Bit&nbsp;7</th>
		<th>Bit&nbsp;6</th>
		<th>Bit&nbsp;5</th>
		<th>Bit&nbsp;4</th>
		<th>Bit&nbsp;3</th>
		<th>Bit&nbsp;2</th>
		<th>Bit&nbsp;1</th>
		<th>Bit&nbsp;0</th>
	</tr>
 	<tr>
		<td>$9F2C</td>
		<td>FX_MULT<br>(DCSEL=2)<br>(Write only)</td>
		<td align="center">Reset Accum.</td>
		<td align="center">Accumulate</td>
		<td align="center">Subtract Enable</td>
		<td align="center">Multiplier Enable</td>
		<td colspan="2" align="center"><b>Cache Byte Index</b><br><img src="images/redunderline.png"></td>
		<td align="center"><b>Cache Nibble Index</b><br><img src="images/redunderline.png"></td>
		<td align="center">Two-byte Cache Incr. Mode</td>
	</tr>
</table>

Alternatively, the cache index can cycle between two adjacent bytes: 0, 1, and back to 0; or 2, 3, and back to 2. This option only has effect in 8-bit mode.

<table>
	<tr>
		<th>Addr</th>
		<th>Name</th>
		<th>Bit&nbsp;7</th>
		<th>Bit&nbsp;6</th>
		<th>Bit&nbsp;5</th>
		<th>Bit&nbsp;4</th>
		<th>Bit&nbsp;3</th>
		<th>Bit&nbsp;2</th>
		<th>Bit&nbsp;1</th>
		<th>Bit&nbsp;0</th>
	</tr>
 	<tr>
		<td>$9F2C</td>
		<td>FX_MULT<br>(DCSEL=2)<br>(Write only)</td>
		<td align="center">Reset Accum.</td>
		<td align="center">Accumulate</td>
		<td align="center">Subtract Enable</td>
		<td align="center">Multiplier Enable</td>
		<td colspan="2" align="center">Cache Byte Index</td>
		<td align="center">Cache Nibble Index</td>
		<td align="center"><b>Two-byte Cache Incr. Mode</b><br><img src="images/redunderline.png"></td>
	</tr>
</table>

### Setting the cache data directly

Instead of filling the cache by reading from DATA0 or DATA1, the cache data can also be set directly by writing to the FX_CACHE* registers. Setting the cache directly does not affect the cache index.

<table>
	<tr>
		<th>Addr</th>
		<th>Name</th>
		<th>Bit&nbsp;7</th>
		<th>Bit&nbsp;6</th>
		<th>Bit&nbsp;5</th>
		<th>Bit&nbsp;4</th>
		<th>Bit&nbsp;3</th>
		<th>Bit&nbsp;2</th>
		<th>Bit&nbsp;1</th>
		<th>Bit&nbsp;0</th>
	</tr>
	<tr>
		<td>$9F29</td>
		<td>FX_CACHE_L<br>(DCSEL=6)<br>(Write only)</td>
		<td colspan="8" align="center">Cache (7:0) | Multiplicand (7:0) (signed)</td>
	</tr>
	<tr>
		<td>$9F2A</td>
		<td>FX_CACHE_M<br>(DCSEL=6)<br>(Write only)</td>
		<td colspan="8" align="center">Cache (15:8) | Multiplicand (15:8) (signed)</td>
	</tr>
	<tr>
		<td>$9F2B</td>
		<td>FX_CACHE_H<br>(DCSEL=6)<br>(Write only)</td>
		<td colspan="8" align="center">Cache (23:16) | Multiplier (7:0) (signed)</td>
	</tr>
	<tr>
		<td>$9F2C</td>
		<td>FX_CACHE_U<br>(DCSEL=6)<br>(Write only)</td>
		<td colspan="8" align="center">Cache (31:24) | Multiplier (15:8) (signed)</td>
	</tr>
</table>

### Writing the cache to VRAM

If "Cache write enabled" is set, the cache contents are written to VRAM when writing to DATA0 or DATA1.  The primary use is to write all or part of the 32-bit cache to the 4-byte-aligned region of memory at the current address.

Control over which parts are written are chosen by the value written to DATA0 or DATA1. The value written is treated as a **nibble mask** where a 0-bit writes the data and a 1-bit masks the data from being written.In other words, writing a 0 will flush the entire 32-bit cache. Writing `#%00001111` will write the second and third byte in the cache to VRAM in the second and third memory locations in the 4-byte-aligned region.


<table>
	<tr>
		<th>Addr</th>
		<th>Name</th>
		<th>Bit&nbsp;7</th>
		<th>Bit&nbsp;6</th>
		<th>Bit&nbsp;5</th>
		<th>Bit&nbsp;4</th>
		<th>Bit&nbsp;3</th>
		<th>Bit&nbsp;2</th>
		<th>Bit&nbsp;1</th>
		<th>Bit&nbsp;0</th>
	</tr>
	<tr>
		<td>$9F29</td>
		<td>FX_CTRL<br>(DCSEL=2)</td>
		<td align="center">Transp. Writes</td>
		<td align="center"><b>Cache Write Enable</b><br><img src="images/redunderline.png"></td>
		<td align="center">Cache Fill Enable</td>
		<td align="center">One-byte Cache Cycling</td>
		<td align="center">16-bit Hop</td>
		<td align="center">4-bit Mode</td>
		<td colspan="2" align="center">Addr1 Mode</td>
	</tr>
</table>


### Transparency writes

Transparent writes, when enabled, also applies to cache writes. If enabled, zero bytes (or zero nibbles in 4-bit mode) in the cache, which are treated as transparency pixels, are not written.

<table>
	<tr>
		<th>Addr</th>
		<th>Name</th>
		<th>Bit&nbsp;7</th>
		<th>Bit&nbsp;6</th>
		<th>Bit&nbsp;5</th>
		<th>Bit&nbsp;4</th>
		<th>Bit&nbsp;3</th>
		<th>Bit&nbsp;2</th>
		<th>Bit&nbsp;1</th>
		<th>Bit&nbsp;0</th>
	</tr>
	<tr>
		<td>$9F29</td>
		<td>FX_CTRL<br>(DCSEL=2)</td>
		<td align="center"><b>Transp. Writes<b><br><img src="images/redunderline.png"></td>
		<td align="center">Cache Write Enable</td>
		<td align="center">Cache Fill Enable</td>
		<td align="center">One-byte Cache Cycling</td>
		<td align="center">16-bit Hop</td>
		<td align="center">4-bit Mode</td>
		<td colspan="2" align="center">Addr1 Mode</td>
	</tr>
</table>

When "one-byte cache cycling" is turned on and DATA0 or DATA1 is written to, the byte at the current cache index is written to VRAM. When "Cache write enable" is set as well, the byte is duplicated 4 times when writing to VRAM. 

Usually the incrementing of the cache index is only triggered by reading from DATA0 or DATA1 when cache filling is enabled. However it can also be triggered by reading from DATA0 in polygon mode when cache filling is not enabled and "one-byte cache cycling" is enabled. 

<table>
	<tr>
		<th>Addr</th>
		<th>Name</th>
		<th>Bit&nbsp;7</th>
		<th>Bit&nbsp;6</th>
		<th>Bit&nbsp;5</th>
		<th>Bit&nbsp;4</th>
		<th>Bit&nbsp;3</th>
		<th>Bit&nbsp;2</th>
		<th>Bit&nbsp;1</th>
		<th>Bit&nbsp;0</th>
	</tr>
	<tr>
		<td>$9F29</td>
		<td>FX_CTRL<br>(DCSEL=2)</td>
		<td align="center">Transp. Writes</td>
		<td align="center">Cache Write Enable</td>
		<td align="center">Cache Fill Enable</td>
		<td align="center"><b>One-byte Cache Cycling</b><br><img src="images/redunderline.png"></td>
		<td align="center">16-bit Hop</td>
		<td align="center">4-bit Mode</td>
		<td colspan="2" align="center">Addr1 Mode</td>
	</tr>
</table>

## Multiplier and accumulator

The 32-bit cache also doubles as an input to the hardware multiplier when Multiplier Enable is set.

<table>
	<tr>
		<th>Addr</th>
		<th>Name</th>
		<th>Bit&nbsp;7</th>
		<th>Bit&nbsp;6</th>
		<th>Bit&nbsp;5</th>
		<th>Bit&nbsp;4</th>
		<th>Bit&nbsp;3</th>
		<th>Bit&nbsp;2</th>
		<th>Bit&nbsp;1</th>
		<th>Bit&nbsp;0</th>
	</tr>
 	<tr>
		<td>$9F2C</td>
		<td>FX_MULT<br>(DCSEL=2)<br>(Write only)</td>
		<td align="center">Reset Accum.</td>
		<td align="center">Accumulate</td>
		<td align="center">Subtract Enable</td>
		<td align="center"><b>Multiplier Enable</b><br><img src="images/redunderline.png"></td>
		<td colspan="2" align="center">Cache Byte Index</td>
		<td align="center">Cache Nibble Index</td>
		<td align="center">Two-byte Cache Incr. Mode</td>
	</tr>
</table>

To do a single multiplication, put the two 16-bit inputs into the two halves of the 32-bit cache.

```x86asm
	lda #(2 << 1)
	sta VERA_CTRL        ; $9F25
	stz VERA_FX_CTRL     ; $9F29 (mainly to reset Addr1 Mode to 0)
	lda #%00010000
	sta VERA_FX_MULT     ; $9F2C
	lda #(6 << 1)
	sta VERA_CTRL        ; $9F25
	lda #<69
	sta VERA_FX_CACHE_L  ; $9F29
	lda #>69
	sta VERA_FX_CACHE_M  ; $9F2A
	lda #<420
	sta VERA_FX_CACHE_H  ; $9F2B
	lda #>420
	sta VERA_FX_CACHE_U  ; $9F2C
```

The accumulator can be used to accumulate the sum of several multiplications.  Before doing this single multiplication, ensure this is reset this to zero, otherwise the output will be added to the value of the accumulator before being written.  There are two methods to do this. The first is to write a 1 into bit 7 of FX_MULT ($9F2C, DCSEL=2).  The other, more conveniently, is to read FX_ACCUM_RESET (the same register location as VERA_FX_CACHE_L).

```x86asm
	lda FX_ACCUM_RESET   ; $9F29 (DCSEL=6)
```

To perform the multiplication, it must be written to VRAM first.  This is done via the cache write mechanism. Usually the cache itself is written to VRAM if "Cache Write Enable" is set.  However, if the "Multiplier Enable" bit is also enabled, the multiplier result is written to VRAM instead.

```x86asm
	; Set the ADDR0 pointer to $00000 and write our multiplication result there
	lda #(2 << 1)
	sta VERA_CTRL        ; $9F25
	lda #%01000000       ; Cache Write Enable
	sta VERA_FX_CTRL     ; $9F29
	stz VERA_ADDRx_L     ; $9F20 (ADDR0)
	stz VERA_ADDRx_M     ; $9F21
	stz VERA_ADDRx_H     ; $9F22 ; no increment
	stz VERA_DATA0       ; $9F23 ; multiply and write out result
	lda #%00010000       ; Increment 1
	sta VERA_ADDRx_H     ; $9F22 ; so we can read out the result
	lda VERA_DATA0
	sta $0400
	lda VERA_DATA0
	sta $0401
	lda VERA_DATA0
	sta $0402
	lda VERA_DATA0
	sta $0403
```

*Note*: the VERA works by pre-fetching the contents from VRAM whenever the address pointer is changed or incremented. This happens even when the address increment is 0. Due to this behavior, it is possible to have stale data latched in one of the two data ports if the underlying VRAM is changed via the other data port. This example avoids this scenario by only using ADDR0/DATA0. This potential gotcha was not introduced by the FX update, but rather has always been how VERA behaves.

#### Accumulation

One can also trigger the multiplication and add it to (or subtract it from) the multiplication accumulator by calling "accumulate" in one of two different ways. We could write a 1 into bit 6 of FX_MULT ($9F2C, DCSEL=2), but more conveniently, we can read FX_ACCUM (the same register location as VERA_FX_CACHE_M)

```x86asm
	lda FX_ACCUM         ; $9F2A (DCSEL=6)
```

Once the accumulation is triggered, the result of the operation is stored back into the accumulator.

The default accumulation operation is (multiply then) add. This can be switched to subtraction by setting the Subtract Enable bit in FX_MULT

<table>
	<tr>
		<th>Addr</th>
		<th>Name</th>
		<th>Bit&nbsp;7</th>
		<th>Bit&nbsp;6</th>
		<th>Bit&nbsp;5</th>
		<th>Bit&nbsp;4</th>
		<th>Bit&nbsp;3</th>
		<th>Bit&nbsp;2</th>
		<th>Bit&nbsp;1</th>
		<th>Bit&nbsp;0</th>
	</tr>
 	<tr>
		<td>$9F2C</td>
		<td>FX_MULT<br>(DCSEL=2)<br>(Write only)</td>
		<td align="center">Reset Accum.</td>
		<td align="center">Accumulate</td>
		<td align="center"><b>Subtract Enable</b><br><img src="images/redunderline.png"></td>
		<td align="center">Multiplier Enable</td>
		<td colspan="2" align="center">Cache Byte Index</td>
		<td align="center">Cache Nibble Index</td>
		<td align="center">Two-byte Cache Incr. Mode</td>
	</tr>
</table>

If the multiplication accumulator has a nonzero value, any multiplications carried out via a VRAM Cache write will be offset by the value of the accumulator (either added to or subtracted from the accumulator), but they will not change the value of the accumulator.

### 16-bit hop

There is a special address increment mode that can be used to read pairs of bytes via ADDR1. 

<table>
	<tr>
		<th>Addr</th>
		<th>Name</th>
		<th>Bit&nbsp;7</th>
		<th>Bit&nbsp;6</th>
		<th>Bit&nbsp;5</th>
		<th>Bit&nbsp;4</th>
		<th>Bit&nbsp;3</th>
		<th>Bit&nbsp;2</th>
		<th>Bit&nbsp;1</th>
		<th>Bit&nbsp;0</th>
	</tr>
	<tr>
		<td>$9F29</td>
		<td>FX_CTRL<br>(DCSEL=2)</td>
		<td align="center">Transp. Writes</td>
		<td align="center">Cache Write Enable</td>
		<td align="center">Cache Fill Enable</td>
		<td align="center">One-byte Cache Cycling</td>
		<td align="center"><b>16-bit Hop</b><br><img src="images/redunderline.png"></td>
		<td align="center">4-bit Mode</td>
		<td colspan="2" align="center">Addr1 Mode</td>
	</tr>
</table>

In this mode, setting ADDR1's increment to +4 will result in alternating increments of +1 and +3. Setting it to +320 will result in alternating increments of +1 and +319. All other increment values, including negative increments, lack this special hop property.

After this bit is set, writing to ADDRx_L resets the hop alignment such that the first increment is +1.

This mode is useful for reading out a series of 16-bit values after a series of multiplications.

For a more detailed explanation of chained math operations, see the [tutorial](https://docs.google.com/document/d/1q34uWOiM3Be2pnaHRVgSdHySI-qsiQWPTo_gfE54PTg).

<!-- For PDF formatting -->
<div class="page-break"></div>

# Chapter 11: Sound Programming

## Audio bank API

The Commander X16 provides many convenience routines for controlling the YM2151 and VERA PSG. These are called similarly to how KERNAL API calls are done in machine language.

In order to gain access to these routines, you must either use `jsrfar` from the KERNAL API:

```ASM
AUDIO_BANK = $0A
  
jsr jsrfar  ; $FF6E
.word ym_init ; $C063
.byte AUDIO_BANK
```

or switch to ROM bank `$0A` directly:

```ASM
lda #$0A ; Audio bank number
sta $01  ; ROM bank register
```

Conveniently, the KERNAL API still exists in this bank, and calling a KERNAL API routine will automatically switch your ROM bank back to the KERNAL bank to perform the routine and then switch back right before returning, so there's usually no need for your audio-centric program to switch away from the audio bank to perform the occasional KERNAL API call.

### Audio API routines

For the audio chips, some of the documentation uses the words _channel_ and _voice_ interchangeably. This table of API routines uses _channel_ for the 8 on the YM2151, and _voice_ for the 16 on the PSG.

| Label | Address | Class | Description | Inputs | Returns | Preserves |
|-|-|-|-|-|-|-|
| `audio_init` | `$C09F` | - | Wrapper routine that calls both `psg_init` and `ym_init` followed by `ym_loaddefpatches`. This is the routine called by the KERNAL at reset. | none | none | none |
| `bas_fmchordstring` | `$C08D` | BASIC | Starts playing all of notes specified in a string. This uses the same parser as `bas_fmplaystring` but instead of playing the notes in sequence, it starts playback of each note in the string, on many channels as is necessary, then returns to the caller without delay. The first FM channel that is used is the one specified by calling `bas_playstringvoice` prior to calling this routine. The string pointer must point to low RAM (`$0000`-`$9EFF`). | .A = string length <br/> .X .Y = pointer to string | none | none |
| `bas_fmfreq` | `$C000` | BASIC | Plays a note specified in Hz on an FM channel | .A = channel <br/> .X .Y = 16-bit frequency in Hz <br/> c clear = normal <br/> c set = no retrigger | c clear = success <br/> c set = error | none |
| `bas_fmnote` | `$C003` | BASIC | Plays a note specified in BASIC format on an FM channel | .A = channel <br/> .X = note (BASIC format) </br> .Y = fractional semitone <br/> c clear = normal <br/> c set = no retrigger | c clear = success <br/> c set = error | none |
| `bas_fmplaystring` | `$C006` | BASIC | Plays a note script using the FM channel which was specified on a previous call to `bas_playstringvoice`. This string pointer must point to low RAM (`$0000`-`$9EFF`). This routine depends on interrupts being enabled. In particular, it uses `WAI` as a delay for timing, so it expects IRQ to be asserted and acknowledged once per video frame, which is the case by default on the system. Stops playback and returns control if the STOP key is pressed. | .A = string length <br/> .X .Y = pointer to string | none | none |
| `bas_fmvib` | `$C009` | BASIC | Sets the LFO speed and both amplitude and frequency depth based on inputs. Also sets the LFO waveform to triangle. | .A = speed </br> .X = PMD/AMD depth | c clear = success <br/> c set = error | none |
| `bas_playstringvoice` | `$C00C` | BASIC | Preparatory routine for `bas_fmplaystring` and `bas_psgplaystring` to set the voice/channel number for playback | .A = PSG/YM voice/channel | none | .A .X |
| `bas_psgchordstring` | `$C090` | BASIC | Starts playing all of notes specified in a string. This uses the same parser as `bas_psgplaystring` but instead of playing the notes in sequence, it starts playback of each note in the string, on many voices as is necessary, then returns to the caller without delay. The first PSG voice that is used is the one specified by calling `bas_playstringvoice` prior to calling this routine. The string pointer must point to low RAM (`$0000`-`$9EFF`). | .A = string length <br/> .X .Y = pointer to string | none | none |
| `bas_psgfreq` | `$C00F` | BASIC | Plays a note specified in Hz on a PSG voice | .A = voice <br/> .X .Y = 16-bit frequency | c clear = success <br/> c set = error | none |
| `bas_psgnote` | `$C012` | BASIC | Plays a note specified in BASIC format on a PSG voice | .A = voice <br/> .X = note (BASIC format) </br> .Y = fractional semitone | c clear = success <br/> c set = error | none |
| `bas_psgwav` | `$C015` | BASIC | Sets a waveform and duty cycle for a PSG voice | .A = voice </br> .X 0-63 = Pulse, 1/128 - 64/128 duty cycle <br/> .X 64-127 = Sawtooth <br/> .X 128-191 = Triangle <br/> .X 192-255 = Noise | c clear = success <br/> c set = error | none |
| `bas_psgplaystring` | `$C018` | BASIC | Plays a note script using the PSG voice which was specified on a previous call to `bas_playstringvoice`. This string pointer must point to low RAM (`$0000`-`$9EFF`). This routine depends on interrupts being enabled. In particular, it uses `WAI` as a delay for timing, so it expects IRQ to be asserted and acknowledged once per video frame, which is the case by default on the system. Stops playback and returns control if the STOP key is pressed. | .A = string length <br/> .X .Y = pointer to string | none | none |
| `notecon_bas2fm` | `$C01B` | Conversion | Convert a note in BASIC format to a YM2151 KC code | .X = note (BASIC format) | .X = note (YM2151 KC) <br/> c clear = success <br/> c set = error | .Y |
| `notecon_bas2midi` | `$C01E` | Conversion | Convert a note in BASIC format to a MIDI note number | .X = note (BASIC format) | .X = MIDI note <br/> c clear = success <br/> c set = error | .Y |
| `notecon_bas2psg` | `$C021` | Conversion | Convert a note in BASIC format to a PSG frequency | .X = note (BASIC format) <br/> .Y = fractional semitone | .X .Y = PSG frequency <br/> c clear = success <br/> c set = error | none |
| `notecon_fm2bas` | `$C024` | Conversion | Convert a note in YM2151 KC format to a note in BASIC format | .X = YM2151 KC  | .X = note (BASIC format) <br/> c clear = success <br/> c set = error | .Y |
| `notecon_fm2midi` | `$C027` | Conversion | Convert a note in YM2151 KC format to a MIDI note number | .X = YM2151 KC  | .X = MIDI note <br/> c clear = success <br/> c set = error | .Y |
| `notecon_fm2psg` | `$C02A` | Conversion | Convert a note in YM2151 KC format to a PSG frequency | .X = YM2151 KC <br/> .Y = fractional semitone | .X .Y = PSG frequency <br/> c clear = success <br/> c set = error | none |
| `notecon_freq2bas` | `$C02D` | Conversion | Convert a frequency in Hz to a note in BASIC format and a fractional semitone | .X .Y = 16-bit frequency in Hz | .X = note (BASIC format) <br/> .Y = fractional semitone <br/> c clear = success <br/> c set = error | none |
| `notecon_freq2fm` | `$C030` | Conversion | Convert a frequency in Hz to YM2151 KC and a fractional semitone (YM2151 KF) | .X .Y = 16-bit frequency in Hz | .X = YM2151 KC <br/> .Y = fractional semitone (YM2151 KF) <br/> c clear = success <br/> c set = error | none |
| `notecon_freq2midi` | `$C033` | Conversion | Convert a frequency in Hz to a MIDI note and a fractional semitone | .X .Y = 16-bit frequency in Hz | .X = MIDI note <br/> .Y = fractional semitone <br/> c clear = success <br/> c set = error | none |
| `notecon_freq2psg` | `$C036` | Conversion | Convert a frequency in Hz to a VERA PSG frequency | .X .Y = 16-bit frequency in Hz | .X .Y = 16-bit frequency in VERA PSG format <br/> c clear = success <br/> c set = error | none |
| `notecon_midi2bas` | `$C039` | Conversion | Convert a MIDI note to a note in BASIC format | .X = MIDI note | .X = note (BASIC format) <br/> c clear = success <br/> c set = error | .Y |
| `notecon_midi2fm` | `$C03C` | Conversion | Convert a MIDI note to a YM2151 KC. Fractional semitone is unneeded as it is identical to KF already. | .X = MIDI note. | .X = YM2151 KC <br/> c clear = success <br/> c set = error | .Y |
| `notecon_midi2psg` | `$C03F` | Conversion | Convert a MIDI note and fractional semitone to a PSG frequency | .X = MIDI note <br/> .Y = fractional semitone | .X .Y = 16-bit frequency in VERA PSG format <br/> c clear = success <br/> c set = error | none |
| `notecon_psg2bas` | `$C042` | Conversion | Convert a frequency in VERA PSG format to a note in BASIC format and a fractional semitone | .X .Y = 16-bit frequency in VERA PSG format | .X = note (BASIC format) <br/> .Y = fractional semitone <br/> c clear = success <br/> c set = error | none |
| `notecon_psg2fm` | `$C045` | Conversion | Convert a frequency in VERA PSG format to YM2151 KC and a fractional semitone (YM2151 KF) | .X .Y = 16-bit frequency in VERA PSG format | .X = YM2151 KC <br/> .Y = fractional semitone (YM2151 KF) <br/> c clear = success <br/> c set = error | none |
| `notecon_psg2midi` | `$C048` | Conversion | Convert a frequency in VERA PSG format to a MIDI note and a fractional semitone | .X .Y = 16-bit frequency in VERA PSG format | .X = MIDI note <br/> .Y = fractional semitone <br/> c clear = success <br/> c set = error | none |
| `psg_getatten` | `$C093` | VERA PSG | Retrieve the attenuation value for a voice previously set by `psg_setatten` | .A = voice | .X = attenuation value | .A |
| `psg_getpan` | `$C096` | VERA PSG | Retrieve the simple panning value that is currently set for a voice. | .A = voice | .X = pan value | .A |
| `psg_init` | `$C04B` | VERA PSG | Initialize the state of the PSG. Silence all voices. Reset the attenuation levels to 0. Set "playstring" defaults including `O4`, `T120`, `S1`, and `L4`. Set all PSG voices to the pulse waveform at 50% duty with panning set to both L+R | none | none | none |
| `psg_playfreq` | `$C04E` | VERA PSG | Turn on a PSG voice at full volume (factoring in attenuation) and set its frequency | .A = voice <br/> .X .Y = 16 bit frequency in VERA PSG format | none | none |
| `psg_read` | `$C051` | VERA PSG | Read a value from one of the VERA PSG registers. If the selected register is a volume register, return either the cooked value (attenuation applied) or the raw value (as received by `psg_write` or `psg_setvol`, or as set by `psg_playfreq`) depending on the state of the carry flag | .X = PSG register address (offset from `$1F9C0`) <br/> c clear = if volume, return raw <br/> c set = if volume, return cooked | .A = register value | .X |
| `psg_setatten` | `$C054` | VERA PSG | Set the attenuation value for a PSG voice. The valid range is from `$00` (full volume) to `$3F` (fully muted). API routines which affect volume will deduct the attenuation value from the intended volume before setting it. Calls to this routine while a note is playing will change the output volume of the voice immediately. This control can be considered a "master volume" for the voice. | .A = voice <br/> .X = attenuation | none | none |
| `psg_setfreq` | `$C057` | VERA PSG | Set the frequency of a PSG voice without changing any other attributes of the voice | .A = voice <br/> .X .Y = 16 bit frequency in VERA PSG format | none | none |
| `psg_setpan` | `$C05A` | VERA PSG | Set the simple panning for the voice. A value of `0` will silence the voice entirely until another pan value is set. | .A = voice <br/> .X 0 = none <br/> .X 1 = left <br/> .X 2 = right <br/> .X 3 = both | none | none |
| `psg_setvol` | `$C05D` | VERA PSG | Set the volume for the voice. The volume that's written to the VERA has attenuation applied. Valid volumes range from `$00` to `$3F` inclusive | .A = voice <br/> .X = volume | none | none |
| `psg_write` | `$C060` | VERA PSG | Write a value to one of the VERA PSG registers. If the selected register is a volume register, attenuation will be applied before the value is written to the VERA | .A = value <br/>.X = PSG register address (offset from `$1F9C0`) | none | .A .X |
| `psg_write_fast` | `$C0A2` | VERA PSG | Same effect as `psg_write` but does not preserve the state of the VERA CTRL and ADDR registers. It also assumes VERA_CTRL bit 0 is clear, VERA_ADDR0_H = $01 (auto increment 0 recommended), and VERA_ADDR0_M = $F9.  This routine is meant for use by sound engines that typically write out multiple PSG registers in a loop. | .A = value <br/>.X = PSG register address (offset from `$1F9C0`) | none | .A .X |
| `ym_getatten` | `$C099` | YM2151 | Retrieve the attenuation value for a channel previously set by `ym_setatten` | .A = channel | .X = attenuation value | .A |
| `ym_getpan` | `$C09C` | YM2151 | Retrieve the simple panning value that is currently set for a channel. | .A = channel | .X = pan value | .A |
| `ym_init` | `$C063` | YM2151 | Initialize the state of the YM chip. Silence all channels by setting the release part of the ADSR envelope to max and then setting all channels to released. Reset all attenuation levels to 0. Set "playstring" defaults including `O4`, `T120`, `S1`, and `L4`. Set panning for all channels set to both L+R. Reset LFO state. Set all of the other registers to `$00` | none | c clear = success <br/> c set = error | none |
| `ym_loaddefpatches` | `$C066` | YM2151 | Load a default set of patches into the 8 channels.<br/> `C0: Piano (0)`<br/>`C1: E. Piano (5)`<br/>`C2: Vibraphone (11)`<br/>`C3: Fretless (35)`<br/> `C4: Violin (40)`<br/>`C5: Trumpet (56)`<br/>`C6: Blown Bottle (76)`<br/>`C7: Fantasia (88)` | none | c clear = success <br/> c set = error | none |
| `ym_loadpatch` | `$C069` | YM2151 | Load into a channel a patch preset by number (0-161) from the audio bank, or from an arbitrary memory location. High RAM addresses (`$A000`-`$BFFF`) are accepted in this mode. | .A = channel<br/>c clear = .X .Y = patch address<br/>c set = .X = patch number | c clear = success <br/> c set = error | none |
| `ym_loadpatchlfn` | `$C06C` | YM2151 | Load patch into a channel by way of an open logical file number. This routine will read 26 bytes from the open file, or possibly fewer bytes if there's an error condition. The routine will leave the file open on return. On return if c is set, check .A for the error code. | .A = channel<br/>.X = Logical File Number | c clear = success <br/> c set .A=0 = YM error <br/> c set .A&3=2 = read timeout <br/> c set .A&3=3 = file not open<br/> c set .A&64=64 = EOF<br/> c set .A&128=128 = device not present | none |
| `ym_playdrum` | `$C06F` | YM2151 | Load a patch associated with a MIDI drum note number and trigger it on a channel. Valid drum note numbers mirror the General MIDI percussion standard and range from 25 (Snare Roll) through 87 (Open Surdo). Note 0 will release the note. After the drum is played, the channel will still contain the patch for the drum sound and thus may not sound musical if you attempt to play notes on it before loading another instrument patch. | .A = channel<br/>.X = drum note | c clear = success <br/> c set = error | none |
| `ym_playnote` | `$C072` | YM2151 | Set a KC/KF on a channel and optionally trigger it. | .A = channel<br/>.X = KC<br/>.Y = KF (fractional semitone)<br/>c clear = trigger<br/>c set = no trigger | c clear = success <br/> c set = error | none |
| `ym_setatten` | `$C075` | YM2151 | Set the attenuation value for a channel. The valid range is from `$00` (full volume) to `$7F` (fully muted). API routines which affect TL or CON will add the attenuation value to the intended TL on operators that are carriers before setting it. Calls to this routine will change the TL of the channel's carriers immediately. This control can be considered a "master volume" for the channel. | .A = channel <br/> .X = attenuation | c clear = success <br/> c set = error | .A .X |
| `ym_setdrum` | `$C078` | YM2151 | Load a patch associated with a MIDI drum note number and set the KC/KF for it on a channel. Called by `ym_playdrum`. | .A = channel<br/>.X = drum note | c clear = success <br/> c set = error | none |
| `ym_setnote` | `$C07B` | YM2151 | Set a KC/KF on a channel. Called by `ym_playnote`. | .A = channel<br/>.X = KC<br/>.Y = KF (fractional semitone) | c clear = success <br/> c set = error | none |
| `ym_setpan` | `$C07E` | YM2151 | Set the simple panning for the channel. A value of `0` will silence the channel entirely until another pan value is set. | .A = channel <br/> .X 0 = none <br/> .X 1 = left <br/> .X 2 = right <br/> .X 3 = both | c clear = success <br/> c set = error | none |
| `ym_read` | `$C081` | YM2151 | Read a value from the in-RAM shadow of one of the YM2151 registers. The YM2151's internal registers cannot be read from, but this API keeps state of what was written, so this routine will be able to retrieve chip values for you. If the selected register is a TL register, return either the cooked value (attenuation applied) or the raw value (as received by `ym_write`) depending on the state of the carry flag | .X = YM2151 register address <br/> c clear = if TL, return raw <br/> c set = if TL, return cooked | .A = register value<br/>c clear = success <br/> c set = error | .X |
| `ym_release` | `$C084` | YM2151 | Release a note on a channel. If a note is not playing, this routine has no tangible effect | .A = channel | c clear = success <br/> c set = error | none |
| `ym_trigger` | `$C087` | YM2151 | Trigger the currently configured note on a channel, optionally releasing the channel first depending on the state of the carry flag. | .A = channel <br/>c clear = release first<br/> c set = no release | c clear = success <br/> c set = error | none |
| `ym_write` | `$C08A` | YM2151 | Write a value to one of the YM2151 registers and to the in-RAM shadow copy. If the selected register is a TL register, attenuation will be applied before the value is written. Writes which affect which operators are carriers will have TL values for that channel appropriately recalculated and rewritten | .A = value <br/>.X = YM register address | c clear = success <br/> c set = error | .A .X |

## A note on semitones (get it?)

It may be advantageous to consider storing note data internally as the MIDI
representation with a fractional component if you want things like pitch slides
to behave the same way between the PSG and YM2151.

Essentially, it can be thought of as an 8.8 fixed point 16-bit number.

The YM2151 handles semitones differently than the PSG and requires converting
the MIDI note to the appropriate KC value using `notecon_midi2fm`. KF is the
fractional semitone (albeit with only the top 6-bits used)
and requires no conversion.

The PSG, by contrast, operates with linear pitch which is why
`notecon_midi2psg` also takes the fractional component (y) as input.

Thus, if you manage all your pitch slides using MIDI notes along with a fractional
component, you can then convert this directly over to PSG or YM2151 as required
and end up with the same pitch (or close enough to it).

## Direct communication with the YM2151 and VERA PSG vs API

Use of the API routines above is not required to access the capabilities of the sound chips. However, mixing raw writes to a chip and API access for the same chip is not recommended, particularly where PSG volumes and YM2151 TL and RLFBCON registers are concerned. The API processes volumes, calculating attenuation and adjusting the output volume accordingly, and the API will be oblivious to direct manipulation of the sound chips.

The sections below describe how to do raw access to the sound chips outside of the API.

## VERA PSG and PCM Programming

* For VERA PSG and PCM, refer to [Chapter 9](X16%20Reference%20-%2009%20-%20VERA%20Programmer's%20Reference.md#chapter-9-vera-programmers-reference).

## YM2151 (OPM) FM Synthesis

The Yamaha YM2151 (OPM) sound chip is an FM synthesizer ASIC in the Commander X16.
It is connected to the system bus at I/O address `0x9F40` (address register) and at `0x9F41` (data register). It has 8 independent voices with 4 FM operators each. Each
voice is capable of left/right/both audio channel output. The four operators of each channel may be connected in one of 8 pre-defined "connection algorithms" in order to produce a wide variety of timbres.

### YM2151 Communication

There are 3 basic operations to communicate with the YM chip: Reading its status,
address select, and data write. These are performed by reading from or writing to
one of the two I/O addresses as follows:

Address|Name|Read Action|Write Action
--|--|-----|-----
0x9F40|`YM_address`|Undefined (returns ?)|Selects the internal register address where data is written.
0x9F41|`YM_data`|Returns the `YM_status` byte|Writes the value into the currently-selected internal address.

The values stored in the YM's internal registers are write-only. If you need
to know the values in the registers, you must store a copy of the values somewhere in memory as you write updates to the YM.

### YM Write Procedure

1. Ensure YM is not busy (see Write Timing below).
2. Select the desired internal register address by writing it into `YM_address`.
3. Write the new value for this register into `YM_data`.

*Note:* You may write into the same register multiple times without repeating a write to `YM_address`. The same register will be updated with each data write.

### Write Timing

**The YM2151 is sensitive to the speed at which you write data into it. If you
make writes when it is not ready to receive them, they will be dropped and the sound output will be corrupted.**

You must include a delay between writes to the address select register ($9F40) and the subsequent data write. 10 CPU cycles is the recommended minimum delay.

The YM becomes `BUSY` for approximately 150 CPU cycles' (at 8Mhz) whenever it receives a data write. *Any writes into YM_data during this `BUSY` period will be ignored!*

In order to avoid this, you can use the `BUSY` flag which is bit 7 of the `YM status` byte. Read the status byte from `YM_data` ($9F41). If the top bit (7) is set, the YM may not be written into at this time. Note that it is not _required_ that you read `YM_status`, only that writes occur no less than ~150 CPU cycles apart. For instance, BASIC executes slowly enough that you are in no danger of writing into the YM too quickly, so BASIC programs may skip checking `YM_status`.

Lastly, the `BUSY` flag sometimes takes a (very) short period before it goes high. This has only been observed when IMMEDIATELY polling the flag after a write into `YM_data.` As long as your code does not do so, this quirk should not be an issue.

### Example Code

**Assembly Language:**

```ASM
check_busy:
    BIT YM_data      ; check busy flag
    BMI check_busy   ; wait until busy flag is clear
    LDA #$08         ; Select YM register $08 (Key-Off/On)
    STA YM_addr      ;
    NOP              ;<-+
    NOP              ;  |
    NOP              ;  +--slight pause before writing data
    NOP              ;  |
    NOP              ;<-+
    LDA #$04         ; Write $04 (Release note on channel 4).
    STA YM_data
    RTS
```

**BASIC:**

```BASIC
10 YA=$9F40      : REM YM_ADDRESS
20 YD=$9F41      : REM YM_DATA
30 POKE YA,$29   : REM CHANNEL 1 NOTE SELECT
40 POKE YD,$4A   : REM SET NOTE = CONCERT A
50 POKE YA,$08   : REM SELECT THE KEY ON/OFF REGISTER
60 POKE YD,$00+1 : REM RELEASE ANY NOTE ALREADY PLAYING ON CHANNEL 1
70 POKE YD,$78+1 : REM KEY-ON VOICE 1 TO PLAY THE NOTE
80 FOR I=1 TO 100 : NEXT I : REM DELAY WHILE NOTE PLAYS
90 POKE YD,$00+1 : REM RELEASE THE NOTE
```

## YM2151 Internal Addressing

The YM register address space can be thought of as being divided into 3 ranges:

Range|Type|Description
--|---|----
00 .. 1F|Global Values|Affect individual global parameters such as LFO frequency, noise enable, etc.
20 .. 3F|Channel CFG|Parameters in groups of 8, one per channel. These affect the whole channel.
40 .. FF|Operator CFG|Parameters in groups of 32 - these map to individual operators of each voice.

## YM2151 Register Map

### Global Settings

<table>
  <tr>
    <th>Addr</th>
    <th>Register</th>
    <th>Bit 7</th>
    <th>Bit 6</th>
    <th>Bit 5</th>
    <th>Bit 4</th>
    <th>Bit 3</th>
    <th>Bit 2</th>
    <th>Bit 1</th>
    <th>Bit 0</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>$01</td>
    <td>Test Register</td>
    <td>!</td>
    <td>!</td>
    <td>!</td>
    <td>!</td>
    <td>!</td>
    <td>!</td>
    <TD>LR</TD>
    <td>!</td>
    <td>
      Bit 1 is the LFO reset bit. Setting it disables the LFO and holds the oscillator at 0. Clearing it enables the LFO.<br />
      All other bits control various test functions and should not be written into.
    </td>
  </tr>
  <tr>
    <td>$08</td>
    <td>Key Control</td>
    <td>.</td>
    <td>C2</td>
    <td>M2</td>
    <td>C1</td>
    <td>M1</td>
    <td colspan="3">CHA</td>
    <td>
      Starts and Releases notes on the 8 channels.<br />
      Setting/Clearing bits for M1,C1,M2,C2 controls the key state
      for those operators on channel CHA.<br />
      NOTE: The operator order is different than the order they
      appear in the Operator configuration registers!
    </td>
  </tr>
  <tr>
    <td>$0F</td>
    <td>Noise Control</td>
    <td>NE</td>
    <td>.</td>
    <td>.</td>
    <td colspan="5">NFRQ</td>
    <td>
      NE = Noise Enable<br />
      NFRQ = Noise Frequency<br />
      When eabled, C2 of channel 7 will use a noise waveform instead
      of a sine waveform.
    </td>
  </tr>
  <tr>
    <td>$10</td>
    <td>Ta High</td>
    <td colspan="8">CLKA1</td>
    <td>Top 8 bits of Timer A period setting</td>
  </tr>
  <tr>
    <td>$11</td>
    <td>Ta Low</td>
    <td>.</td>
    <td>.</td>
    <td>.</td>
    <td>.</td>
    <td>.</td>
    <td>.</td>
    <td colspan="2">CLKA2</td>
    <td>Bottom 2 bits of Timer A period setting</td>
  </tr>
  <tr>
    <td>$12</td>
    <td>Timer B</td>
    <td colspan="8">CLKB</td>
    <td>Timer B period setting</td>
  </tr>
  <tr>
    <td>$14</td>
    <td>IRQ Control</td>
    <td>CSM</td>
    <td>.</td>
    <td colspan="2">Clock ACK</td>
    <td colspan="2">IRQ EN</td>
    <td colspan="2">Clock Start</td>
    <td>
      CSM: When a timer expires, trigger note key-on for all channels.<br />
      For the other 3 fields, lower bit = Timer A, upper bit = Timer B.<br />
      Clock ACK: clears the timer's bit in the YM_status byte and acknowledges the IRQ.<br />
    </td>
  </tr>
  <tr>
    <td>$18</td>
    <td>LFO Freq.</td>
    <td colspan="8">LFRQ</td>
    <td>Sets LFO frequency.<br />
    $00 = ~0.008Hz<br />
    $FF = ~32.6Hz</td>
  </tr>
  <tr>
    <td rowspan="2">$19</td>
    <td rowspan="2">LFO Amplitude</td>
    <td>0</td>
    <td colspan="7">AMD</td>
    <td rowspan="2">
      AMD = Amplitude Modulation Depth<br />
      PMD = Phase Modulation (vibrato) Depth<br />
      Bit 7 determines which parameter is being set when writing into
      this register.
    </td>
  </tr>
  <tr>
    <td>1</td>
    <td colspan="7">PMD</td>
  </tr>
  <tr>
    <td>$1B</td>
    <td>CT / LFO Waveform</td>
    <td colspan="2">CT</td>
    <td>.</td>
    <td>.</td>
    <td>.</td>
    <td>.</td>
    <td colspan="2">W</td>
    <td>
      CT: sets output pins CT1 and CT1 high or low. (not connected to anything in X16)<br />
      W: LFO Waveform: 0-4 = Saw, Square, Triangle, Noise<br />
      For sawtooth: PM->////  AM->\\\\
    </td>
  </tr>
</table>

#### Channel CFG Registers

<table>
  <tr>
    <th>Register Range</th>
    <th>Bit 7</th>
    <th>Bit 6</th>
    <th>Bit 5</th>
    <th>Bit 4</th>
    <th>Bit 3</th>
    <th>Bit 2</th>
    <th>Bit 1</th>
    <th>Bit 0</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>$20 + channel</td>
    <td colspan="2">RL</td>
    <td colspan="3">FB</td>
    <td colspan="3">CON</td>
    <td rowspan="4">
      <dl>
        <dt>RL</dt><dd>Right/Left Output Enable</dd>
        <dt>FB</dt><dd>M1 Feedback Level</dd>
        <dt>CON</dt><dd>Operator connection algorithm</dd>
        <dt>KC</dt><dd>Key Code</dd>
        <dt>KF</dt><dd>Key Fraction</dd>
        <dt>PMS</dt><dd>Phase Modulation Sensitivity</dd>
        <dt>AMS</dt><dd>Amplitude Modulation Sensitivity</dd>
      </dl>
    </td>
  </tr>
  <tr>
    <td>$28 + channel</td>
    <td>.</td>
    <td colspan="7">KC</td>
  </tr>
  <tr>
    <td>$30 + channel</td>
    <td colspan="6">KF</td>
    <td>.</td>
    <td>.</td>
  </tr>
  <tr>
    <td>$38 + channel</td>
    <td>.</td>
    <td colspan="3">PMS</td>
    <td>.</td>
    <td>.</td>
    <td colspan="2">AMS</td>
  </tr>
</table>

#### Operator CFG Registers

<table>
  <tr>
    <th>Register Range</th>
    <th>Operator</th>
    <th>Bit 7</th>
    <th>Bit 6</th>
    <th>Bit 5</th>
    <th>Bit 4</th>
    <th>Bit 3</th>
    <th>Bit 2</th>
    <th>Bit 1</th>
    <th>Bit 0</th>
    <th>Description</th>
  </tr>
  <tr>
    <td rowspan="4" valign="top">$40</td>
    <td>M1: $40+channel</td>
    <td rowspan="4" >.</td>
    <td rowspan="4" colspan="3">DT1</td>
    <td rowspan="4" colspan="4">MUL</td>
    <td rowspan="4" valign="top">
      <dl>
        <dt>DT1</dt><dd>Detune Amount (fine)</dd>
        <dt>MUL</dt><dd>Frequency Multiplier</dd>
      </dl>
    </td>
  </tr>
  <tr>
    <td>M2: $48+channel</td>
  </tr>
  <tr>
    <td>C1: $50+channel</td>
  </tr>
  <tr>
    <td>C2: $58+channel</td>
  </tr>
  <tr>
    <td rowspan="4" valign="top">$60</td>
    <td>M1: $60+channel</td>
    <td rowspan="4" >.</td>
    <td rowspan="4" colspan="7">TL</td>
    <td rowspan="4" valign="top">
      <dl>
        <dt>TL</dt><dd>Total Level (volume attenuation)<br/>
                       (0=max, $7F=min)
        </dd>
      </dl>
    </td>
  </tr>
  <tr>
    <td>M2: $68+channel</td>
  </tr>
  <tr>
    <td>C1: $70+channel</td>
  </tr>
  <tr>
    <td>C2: $78+channel</td>
  </tr>
  <tr>
    <td rowspan="4" valign="top">$80</td>
    <td>M1: $80+channel</td>
    <td rowspan="4" colspan="2">KS</td>
    <td rowspan="4" >.</td>
    <td rowspan="4" colspan="5">AR</td>
    <td rowspan="4" valign="top">
      <dl>
        <dt>KS</dt><dd>Key Scaling (ADSR rate scaling)</dd>
        <dt>AR</dt><dd>Attack Rate</dd>
      </dl>
    </td>
  </tr>
  <tr>
    <td>M2: $88+channel</td>
  </tr>
  <tr>
    <td>C1: $90+channel</td>
  </tr>
  <tr>
    <td>C2: $98+channel</td>
  </tr>
  <tr>
    <td rowspan="4" valign="top">$A0</td>
    <td>M1: $A0+channel</td>
    <td rowspan="4">A<br />M<br /><br />E<br />n<br />a</td>
    <td rowspan="4" >.</td>
    <td rowspan="4" >.</td>
    <td rowspan="4" colspan="5">D1R</td>
    <td rowspan="4" valign="top">
      <dl>
        <dt>AM-Ena</dt><dd>Amplitude Modulation Enable</dd>
        <dt>D1R</dt><dd>Decay Rate 1<br />
                        (From peak down to sustain level)
        </dd>
      </dl>
    </td>
  </tr>
  <tr>
    <td>M2: $A8+channel</td>
  </tr>
  <tr>
    <td>C1: $B0+channel</td>
  </tr>
  <tr>
    <td>C2: $B8+channel</td>
  </tr>
  <tr>
    <td rowspan="4" valign="top">$C0</td>
    <td>M1: $C0+channel</td>
    <td rowspan="4" colspan="2">DT2</td>
    <td rowspan="4" >.</td>
    <td rowspan="4" colspan="5">D2R</td>
    <td rowspan="4" valign="top">
      <dl>
        <dt>DT2</dt><dd>Detune Amount (coarse)</dd>
        <dt>D2R</dt><dd>Decay Rate 2<br />
                        (During sustain phase)
        </dd>
      </dl>
    </td>
  </tr>
  <tr>
    <td>M2: $C8+channel</td>
  </tr>
  <tr>
    <td>C1: $D0+channel</td>
  </tr>
  <tr>
    <td>C2: $D8+channel</td>
  </tr>
  <tr>
    <td rowspan="4" valign="top">$E0</td>
    <td>M1: $E0+channel</td>
    <td rowspan="4" colspan="4">D1L</td>
    <td rowspan="4" colspan="4">RR</td>
    <td rowspan="4" valign="top">
      <dl>
        <dt>D1L</dt><dd>Decay 1 Level (Sustain level)<br />
                        Level at which decay switches from D1R to D2R
        </dd>
        <dt>RR</dt><dd>Release Rate</dd>
      </dl>
    </td>
  </tr>
  <tr>
    <td>M2: $E8+channel</td>
  </tr>
  <tr>
    <td>C1: $F0+channel</td>
  </tr>
  <tr>
    <td>C2: $F8+channel</td>
  </tr>
</table>

# YM2151 Register Details

## Global Parameters

**LR** (LFO Reset)

Register $01, bit 1

Setting this bit will disable the LFO and hold it at level 0. Clearing this bit
allows the LFO to operate as normal. (See LFRQ for further info)

**KON** (KeyON)

Register $08

* Bits 0-2: Channel_Number

* Bits 3-6: Operator M1, C1, M2, C2 control bits:
  * 0: Releases note on operator
  * 0->1: Triggers note attack on operator
  * 1->1: No effect

Use this register to start/stop notes. Typically, all 4 operators are triggered/released
together at once. Writing a value of $78+channel_number will start a note on all 4 OPs,
and writing a value of $00+channel_number will stop a note on all 4 OPs.

**NE** (Noise Enable)

Register $0F, Bit 7

When set, the C2 operator of channel 7 will use a noise waveform instead of a sine.

**NFRQ** (Noise Frequency)

Register $0F, Bits 0-4

Sets the noise frequency, $00 is the lowest and $1F is the highest. NE bit must be
set in order for this to have any effect. Only affects operator C2 on channel 7.

**CLKA1** (Clock A, high order bits)

Register $10, Bits 0-7

This is the high-order value for Clock A (a 10-bit value).

**CLKA2** (Clock A, low order bits)

Register $11, Bits 0-1

Sets the 2 low-order bits for Clock A (a 10-bit value).

Timer A's period is
Computed as (64*(1024-ClkA)) / PhiM ms.  (PhiM = 3579.545Khz)

**CLKB** (Clock B)

Register $12, Bits 0-7

Sets the Clock B period. The period for Timer B is computed as (1024*(256-CLKB)) / PhiM ms. (PhiM = 3579.545Khz)

**CSM**

Register $14, Bit 7

When set, the YM2151 will generate a KeyON attack on all 8 channels whenever TimerA overflows.

**Clock ACK**

Register $14, Bits 4-5

Clear (acknowledge) IRQ status generated by TimerA and TimerB (respectively).

**IRQ EN**

Register $14, Bits 2-3

When set, enables IRQ generation when TimerA or TimerB (respectively) overflow.
The IRQ status of the two timers is checked by reading from the YM2151_STATUS byte.
Bit 0 = Timer A IRQ status, and Bit 1 = Timer B IRQ status. Note that these status
bits are only active if the timer has overflowed AND has its IRQ_EN bit set.

**Clock Start**

Register $14, Bits 0-1

When set, these bits clear the TimerA and TimerB (respectively) counters and starts
it running.

**LFRQ** (LFO Frequency)

Register $18, Bits 0-7

Sets the LFO frequency.

* $00 = ~0.008Hz
* $FF = ~32.6Hz

Note that even setting the value zero here results in a positive LFO frequency. Any channels sensitive to the LFO will still be affected by the LFO unless the `LR` bit is set in register $01 to completely disable it.

**AMD** (Amplitude Modulation Depth)

Register $19 Bits 0-6, Bit 7 clearParameters

Sets the peak strength of the LFO's Amplitude Modulation effect. Note that bit 7 of the value written into $19 must be clear in order to set the AMD. If bit 7 is set, the write will be interpreted as PMD.

**PMD** (Phase Modulation Depth)

Register $19 Bits 0-6, Bit 7 set

Sets the peak strength of the LFO's Phase Modulation effect. Note that bit 7 of the value written into $19 must be set in order to set the PMD. If bit 7 is clear, the value is interpreted as AMD.

**CT** (Control pins)

Register $1B, Bits 6-7

These bits set the electrical state of the two CT pins to on/off. These pins are not connected to anything in the X16 and have no effect.

**W** (LFO Waveform)

Register $1B, Bits 0-1

Sets the LFO waveform:
0: Sawtooth, 1: Square (50% duty cycle), 2: Triangle, 3: Noise

## Channel Control Parameters

**RL** (Right/Left output enable)

Register $20 (+ channel), Bits 6-7

Setting/Clearing these bits enables/disables audio output for the selected channel. (bit6=left, bit7=right)

**FB** (M1 Self-Feedback)

Register $20 (+ channel), bits 3-5

Sets the amount of self feedback on operator M1 for the selected channel. 0=none, 7=max

**CON** (Connection Algorithm)

Register $20 (+ channel), bits 0-2

Sets the selected channel to connect the 4 operators in one of 8 arrangements.

  [insert picture here]

**KC** (Key Code - Note selection)

Register $28 + channel, bits 0-6

Sets the octave and semitone for the selected channel.
Bits 4-6 specify the octave (0-7) and bits 0-3 specify the semitone:

0|1|2|4|5|6|8|9|A|C|D|E
-|-|-|-|-|-|-|-|-|-|-|-
C&#9839;|D|D&#9839;|E|F|F&#9839;|G|G&#9839;|A|A&#9839;|B|C

Note that natural C is at the TOP of the selected octave, and that
each 4th value is skipped. Thus if concert A (A-4, 440hz) is KC=$4A, then middle C is KC=$3E

**KF** (Key Fraction)

Register $30 + channel, Bits 2-7

Raises the pitch by 1/64th of a semitone * the KF value.

**PMS** (Phase Modulation Sensitivity)

Register $38 + channel, Bits 4-6

Sets the Phase Modulation (vibrato) sensitivity of the selected channel. The resulting vibrato depth is determined by the combination of the global PMD setting (see above) modified by each channel's PMS.

Sensitivity values: (+/- cents)

0|1|2|3|4|5|6|7
-|-|-|-|-|-|-|-
0|5|10|20|50|100|400|700

**AMS** (Amplitude Modulation Sensitivity)

Register $38 + channel, Bits 0-1

Sets the Amplitude Modulation sensitivity of the selected channel. Note that each operator may individually enable or disable this effect on its output by setting/clearing the AMS-Ena bit (see below). Operators acting as outputs will exhibit a tremolo effect (varying volume) and operators acting as modulators will vary their effectiveness on the timbre when enabled for amplitude modulation.

Sensitivity values: (dB)

0|1|2|3
-|-|-|-
0|23.90625|47.8125|95.625

## Operator Control Parameters

Operators are arranged as follows:

name|M1|M2|C1|C2
-|-|-|-|-
index|0|1|2|3

These are the names used throughout this document for consistency, but they may function as either modulators or carriers, depending on which `CON` ALG is used.

The Operator Control parameters are mapped to channels/operators as follows: Register + 8\*op + channel. You may also choose to think of these register addresses as using bits 0-2 = channel, bits 3-4 = operator, and bits 5-7 = parameter. This reference will refer to them using the address range, e.g. $60-$7F = TL. To set TL for channel 2, operator 1, the register address would be $6A ($60 + 1\*8 + 2).

**DT1** (Detune 1 - fine detune)

Registers \$40-\$5F, Bits 4-6

Detunes the operator from the channel's main pitch. Values 0 and 4=no detuning.
Values 1-3=detune up, 5-7 = detune down.<br/>
The amount of detuning varies with pitch. It decreases as the channel's pitch increases.

**MUL** (Frequency Multiplier)

Registers \$40-\$5F, Bits 0-3

If MUL=0, it multiplies the operator's frequency by 0.5<br/>
Otherwise, the frequency is multiplied by the value in MUL (1,2,3...etc)

**TL** (Total Level - attenuation)

Registers \$60-\$7F, Bits 0-6

This is essentially "volume control" - It is an attenuation value, so $00 = maximum level and $7F is minimum level. On output operators, this is the volume output by that operator. On modulating operators, this affects the amount of modulation done to other operators.

**KS** (Key Scaling)

Registers \$80-\$9F, Bits 6-7

Controls the speed of the ADSR progression. The KS value sets four different levels of scaling. Key scaling increases along with the pitch set in KC. 0=min, 3=max

**AR** (Attack Rate)

Registers \$80-\$9F, Bits 0-4

Sets the attack rate of the ADSR envelope. 0=slowest, $1F=fastest

**AMS-Enable** (Amplitude Modulation Sensitivity Enable)

Registers \$A0-\$BF, Bit 7

If set, the operator's output level will be affected by the LFO according to the channel's AMS setting. If clear, the operator will not be affected.

**D1R** (Decay Rate 1)

Registers \$A0-\$BF, Bits 0-4

Controls the rate at which the level falls from peak down to the sustain level (D1L). 0=none, $1F=fastest.

**DT2** (Detune 2 - coarse)

Registers \$C0-\$DF, Bits 6-7

Sets a strong detune amount to the operator's frequency. Yamaha suggests that this is most useful for sound effects. 0=off,

**D2R** (Decay Rate 2)

Registers \$C0-\$DF, Bits 0-4

Sets the Decay2 rate, which takes effect once the level has fallen from peak down to the sustain level (D1L). This rate continues
until the level reaches zero or until the note is released.

0=none, $1F=fastest

**D1L**

Registers \$E0-\$FF, Bits 4-7

Sets the level at which the ADSR envelope changes decay rates from D1R to D2R. 0=minimum (no D2R), $0F=maximum (immediately at peak, which effectively disables D1R)

**RR**

Registers \$E0-\$FF, Bitst 0-3

Sets the rate at which the level drops to zero when a note is released. 0=none, $0F=fastest

<br/>

___

# Getting sound out of the YM2151 (a brief tutorial)

While there is a large number of parameters that affect the sound of the YM2151, its operation can be thought of in simplified terms if you consider that there are basically three components to deal with: Instrument configuration (patch), voice pitch selection,
and "pressing/releasing" the "key" to trigger (begin) and release (end) notes. It's essentially the
same as using a music keyboard. Pressing an instrument button (e.g. Marimba) makes the keyboard
sound like a Marimba. Once this is done, you press a key on the keyboard to play a note,
and release it to stop the note. With the YM, loading a patch (pressing the Marimba button) entails setting all of
the various operators' registers on the voice(s) you want the instrument to be used on.
On the music keyboard, pitch and note stop/start are done with a single piano key. In the
YM2151, these are two distinct actions.

For this tutorial, we will start with the simplest operation, (triggering notes) and proceed to note selection, and finally patch configuration.

## Triggering and Releasing Notes

**Key On/Off (KON) Register ($08):**

This is probably the most important single register in the YM2151. It is used to trigger and release notes. It controls the key on/off state for all 8 channels. A note is triggered whenever its key state changes from off to on, and is released whenever the state changes from on to off. Repeated writes of the same state (off->off or on->on) have no effect.

Whenever an operator is triggered, it progresses through the states of attack, decay1, and sustain/decay2. Whenever an active note is released, it enters the release state where the volume decreases until reaching zero. It then remains silent until the next time the operator is triggered. If you are familiar with the C64 SID chip, this is the same behavior as the "gate" bit on that chip.

Key state and voice selection are both contained in the value written into the KON register as follows:

* Key ON = $78 + channel number
* Key OFF = $0 + channel number

**Simple Examples:**

To release the note in channel 4: write $08 to `YM_address` ($9F40) and then write \$04 (\$00+4) to `YM_data` (\$9F41).

To begin a note on channel 7, write $08 into `YM_address` to select the KON register. Then write \$7F (\$78+7) into `YM_data`

If the current key state of a channel is not known, you can write key off and then key on immediately (after waiting for the YM busy period to end, of course):

```BASIC
POKE $9F40,$08 : REM SELECT KEY ON/OFF REGISTER
POKE $9F41,$07 : REM KEY OFF FOR VOICE 7
POKE $9F41,$7F : REM KEY ON  FOR VOICE 7
```

*Remember: BASIC is slow enough that you do not need to poll the `YM_status` byte, but assembly and other languages will need to do so.*

The ADSR parameters will be discussed in more detail later.

**Advanced:**

Each channel (voice) of the YM2151 uses 4 operators which can be gated together or independently. Independent triggering gives lots of advanced possibilities. To trigger and release operators independently, you use different values than \$78 or \$00. These values are composed by 4 bits which signal the on/off state for each operator.

Suppose a note is playing on channel 2 with all 4 operators active. You can release only the M1 operator by writing \$72 into register \$08.

**The KON value format:**

<table>
  <tr>
    <td>7</td>
    <td>6</td>
    <td>5</td>
    <td>4</td>
    <td>3</td>
    <td>2</td>
    <td>1</td>
    <td>0</td>
  </tr>
  <tr>
    <td> - </td>
    <td>C2</td>
    <td>M2</td>
    <td>C1</td>
    <td>M1</td>
    <td colspan="3">Channel</td>
  </tr>
</table>

## Pitch Control

### YM Registers

* `KC` = $28 + channel number
* `KF` = $30 + channel number

For note selection, each voice has two parameters: `KC` (Key Code) and `KF` (Key Fraction).
These are set in register ranges $28 and $30, respectively. The KC codes correspond
directly to the notes of the chromatic scale. Each value maps to a specific octave & semitone. The `KF` value can even be ignored
for basic musical playback. It is mostly useful for vibrato or pitch bend effects. `KF` raises
the pitch selected in `KC` in 1/64th increments of the way up to the next semitone.

Like all registers in the YM, whenever a channel's `KC` or `KF` value is written, it takes effect immediately. If a note is playing, its pitch immediately changes. When triggering new notes, it is not important whether you write the pitch or key the note first. This happens quickly in real-time and you will not hear any real difference. Changing the pitch without re-triggering the ADSR envelope is how to achieve pitch slides or a legato effect.

#### Key Code (KC)

`KC` codes are "conveniently" arranged so that the upper nybble is the octave (0-7) and the
lower nybble is the pitch. The pitches are arranged as follows within an octave:

Note|C&#9839;|D|D&#9839;|E|F|F&#9839;|G|G&#9839;|A|A&#9839;|B|C
--|-|-|-|-|-|-|-|-|-|-|-|-
Low Nybble (hex)|0|1|2|4|5|6|8|9|A|C|D|E

(Note that every 4th value is skipped.)

Combine the above with an octave to get a note's `KC` value. For instance: concert A (440hz) is (by sheer coincidence) `$4A`. Middle C is `$3E`, and so forth.

#### Key Fraction (KF)

`KF` values are written into the top 6 bits of the voice's `KF` register. Basically the value is `0, 1<<2, 2<<2, .. 63<<2`

## Loading a patch

The patch configuration is by far the most complicated aspect of using the YM. If you take as given that a voice has a patch loaded, then playing notes on it is fairly straightforward. For the
moment, we will assume a pre-patched voice.

To get started quickly, here is some BASIC code to patch voice 0 with a marimba tone:

```BASIC
5 YA=$9F40 : YD=$9F41 : V=0
10 REM: MARIMBA PATCH FOR YM VOICE 0 (SET V=0..7 FOR OTHER VOICES)
20 DATA $DC,$00,$1B,$67,$61,$31,$21,$17,$1F,$0A,$DF,$5F,$DE
30 DATA $DE,$0E,$10,$09,$07,$00,$05,$07,$04,$FF,$A0,$16,$17
40 READ D
50 POKE YA,$20+V : POKE YD,D
60 FOR A=$38 TO $F8 STEP 8
70 READ D : POKE YA,A+V : POKE YD,D
80 NEXT A
```

Once a voice has been patched as above, you can now POKE notes into it with very few commands for each note.

Patches consist mostly of ADSR envelope parameters. A complete patch contains values for the \$20 range register (LR|FB|CON), for the \$38 range register (AMS|PMS), and 4 values for each of the parameter ranges starting at \$40. (4 operators per voice means 4 values per parameter). Since this is a huge amount of flexibility, it is recommended to experiment with instrument creation in an application such as a chip tracker or VST, as the creative process of instrument design is very hands-on and subjective.

## Using the LFO

There is a single global LFO in the YM2151 which can affect the level (volume) and/or pitch of all 8 channels simultaneously. It has a single frequency and waveform setting which must be shared among all channels, and shared between both phase and amplitude modulation. The global parameters `AMD` and `PMD` act as modifiers to the sensitivity settings of the channels. While the frequency and waveform of the LFO pattern must be shared, the depths of the two types of modulation are independent of each other.

You can re-trigger the LFO by setting and then clearing the `LR` bit in the test register ($01).

### Vibrato

Use Phase Modulation on the desired channels. The `PMS` parameter for each channel allows them to vary their vibrato depths individually. Channels with `PMS` set to zero will have no vibrato. The values given earlier in the `PMS` parameter description represent their maximum amount of affect. These values are modified by the global `PMD.` A `PMD` value of \$7F means 100% effectiveness, \$40 means all channels' vibrato depths will be reduced by half, etc.

The vibrato speed is global, depending solely on the value set to `LFRQ.`

### Amplitude Modulation

Amplitude modulation works similarly to phase modulation, except that the intensity is a combination of the per-channel `AMS` value modified by the global `AMD` value. Additionally, within channels having non-zero amplitude modulation sensitivity, individual operators must have their `AMS-en` bit enabled in order to be affected by the modulation.

If the active operators are acting as carriers (generating output directly), then amplitude modulation will vary the volume of the sound being produced by that operator. This can be described as a "tremolo" effect. If the operators are acting as modulators, then the timbre of the voice will vary as the output level of the affected operators increases and decreases. You may simultaneously enable amplitude modulation on both types of operators.

The amplitude modulation speed is global, depending solely on the value set to `LFRQ.`

<!-- For PDF formatting -->
<div class="page-break"></div>

# Chapter 12: I/O Programming

There are two 65C22 "Versatile Interface Adapter" (VIA) I/O controllers in the system, VIA#1 and VIA#2. The address range \$9F00 to \$9F0F maps to VIA#1's internal registers \$0 to \$F. Likewise, the address range \$9F10 to \$9F1F maps to VIA#2's internal registers. Details on the internal registers can be found in the published datasheet: <https://www.westerndesigncenter.com/wdc/documentation/w65c22.pdf>.

The IRQ out pin of VIA#1 is connected to the CPU's IRQ line, while the IRQ out pin of VIA#2 can be configured via jumper to connect to either the CPU's IRQ or NMI line on production boards (those beginning with serial PR), or hardwired to the CPU's IRQ line on earlier boards.

The-following tables describe the connections of the I/O pins:

**VIA#1**

|Pin  |Name      | Description                     |
|-----|----------|---------------------------------|
| PA0 | I2CDATA  | I2C Data                        |
| PA1 | I2CCLK   | I2C Clock                       |
| PA2 | NESLATCH | NES LATCH (for all controllers) |
| PA3 | NESCLK   | NES CLK   (for all controllers) |
| PA4 | NESDAT3  | NES DATA  (controller 3)        |
| PA5 | NESDAT2  | NES DATA  (controller 2)        |
| PA6 | NESDAT1  | NES DATA  (controller 1)        |
| PA7 | NESDAT0  | NES DATA  (controller 0)        |
| PB0 | _Unused_ |                                 |
| PB1 | _Unused_ |                                 |
| PB2 | _Unused_ |                                 |
| PB3 | SERATNO  | Serial ATN  out                 |
| PB4 | SERCLKO  | Serial CLK  out                 |
| PB5 | SERDATAO | Serial DATA out                 |
| PB6 | SERCLKI  | Serial CLK  in                  |
| PB7 | SERDATAI | Serial DATA in                  |
| CA1 | _Unused_ |                                 |
| CA2 | _Unused_ |                                 |
| CB1 | IECSRQ   |                                 |
| CB2 | _Unused_ |                                 |

The KERNAL uses Timer 2 for timing transmissions on the Serial Bus.

**VIA#2**

The second VIA is completely unused by the KERNAL. All its 16 GPIOs and 4 handshake I/Os can be freely used by user software.

## I2C Bus

The Commander X16 contains an I2C bus, which is implemented through two pins of VIA#1. The system management controller (SMC) and the real-time clock (RTC) are connected through this bus. The KERNAL APIs `i2c_read_byte` and `i2c_write_byte` allow talking to these devices.

| Address             | Target                                                                      |
|---------------------|-----------------------------------------------------------------------------|
| `1000010 ($42)`     | [System Management Controller (SMC)](#system-Management-Controller)         |
| `1010??? ($50-$57)` | [Non-volatile storage for cartridges](#non-volatile-storage-for-cartridges) |
| `1101111 ($6F)`     | [Real-Time Clock (RTC)](#real-time-clock)                                   |


### System Management Controller

**I2C address: $42**

The system management controller (SMC) is device $42 on the I2C bus. It controls the activity LED, and can be used to power down the system or inject RESET and NMI signals. It also handles communication with
the PS/2 keyboard and mouse.

| Register | Value          | Description               |
|----------|----------------|---------------------------|
| $01      | $00            | Power off                 |
| $01      | $01            | Hard reboot               |
| $02      | $00            | Inject RESET              |
| $03      | $00            | Inject NMI                |
| $05      | \$00/\$FF      | Activity LED off/on       |
| $07      | -              | Read from keyboard buffer |
| $08      | \$00..\$FF     | Echo                      |
| $18      | -              | Read ps2 status           |
| $19      | \$00..\$FF     | Send ps2 command          |
| $1A      | \$0000..\$FFFF | Send ps2 command (2 bytes) |
| $20      | $00            | Set mouse device ID, standard mouse |
| $20      | $03            | Set mouse device ID, Intellimouse with scroll wheel |
| $20      | $04            | Set mouse device ID, Intellimouse with scroll wheel+extra buttons |
| $21      | -              | Read from mouse buffer    |
| $22      | -              | Get mouse device ID |
| $30      | -              | Get SMC firmware version, major |
| $31      | -              | Get SMC firmware version, minor |
| $32      | -              | Get SMC firwmare version, patch |
| $8F      | $31            | Start bootloader, if present |  

### Non-volatile storage for cartridges

**I2C address: $50-$57**

#### Commander X16 ROM Cartridge
[Commander X16 ROM Cartridge](https://texelec.com/product/commander-x16-cartridge/) supports up to 4 128kB EEPROM chips in the $50-$57 address range. Address is chosen based on IC slot on the PCB. Chip type: **Onsemi CAT24M01**

#### ROAM Commander X16 Cartridge
[ROAM Commander X16 Cartridge](https://www.tindie.com/products/wavicle/roam-commander-x16-cartridge/), by Wavicle, features 1 8kB FRAM chip in the $50-$57 address range. Address is configurable by dip-switches. Chip type: **FM24C64B**

### Real-Time-Clock

**I2C address: $6F**

The Commander X16 contains a battery-backed Microchip MCP7940N real-time-clock (RTC) chip as device $6F. It provides a real-time clock/calendar, two alarms and 64 bytes of battery-backed SRAM (non-volatile RAM).

| Register | Description        |
|----------|--------------------|
| $00      | Clock seconds      |
| $01      | Clock minutes      |
| $02      | Clock hours        |
| $03      | Clock weekday      |
| $04      | Clock day          |
| $05      | Clock month        |
| $06      | Clock year         |
| $07      | Control            |
| $08      | Oscillator trim    |
| $09      | _reserved_         |
| $0A      | Alarm 0 seconds    |
| $0B      | Alarm 0 minutes    |
| $0C      | Alarm 0 hours      |
| $0D      | Alarm 0 weekday    |
| $0E      | Alarm 0 day        |
| $0F      | Alarm 0 month      |
| $10      | _reserved_         |
| $11      | Alarm 1 seconds    |
| $12      | Alarm 1 minutes    |
| $13      | Alarm 1 hours      |
| $14      | Alarm 1 weekday    |
| $15      | Alarm 1 day        |
| $16      | Alarm 1 month      |
| $17      | _reserved_         |
| $18      | Power-fail minutes |
| $19      | Power-fail hours   |
| $1A      | Power-fail day     |
| $1B      | Power-fail month   |
| $1C      | Power-up minutes   |
| $1D      | Power-up hours     |
| $1E      | Power-up day       |
| $1F      | Power-up month     |
| \$20-\$5F  | 64 Bytes SRAM      |

####  SRAM (NVRAM)
| Register  | Description        |
|-----------|--------------------|
| \$20-\$3F | User NVRAM         |
| \$40-\$5F | KERNAL NVRAM       |
| $40       | Active profile     |
| \$41-\$4D | Profile 0 (80x60)  |
| \$4E-\$5A | Profile 1 (40x30)  |
| \$41/\$4E | Screen mode        |
| \$42/\$4F | VERA_DC_VIDEO      |
| \$43/\$50 | VERA_DC_HSCALE     |
| \$44/\$51 | VERA_DC_VSCALE     |
| \$45/\$52 | VERA_DC_BORDER     |
| \$46/\$53 | VERA_DC_HSTART     |
| \$47/\$54 | VERA_DC_HSTOP      |
| \$48/\$55 | VERA_DC_VSTART     |
| \$49/\$56 | VERA_DC_VSTOP      |
| \$4A/\$57 | Color (bg/fg)      |
| \$4B/\$58 | Keymap             |
| \$4C/\$59 | Typematic          |
| \$4D/\$5A | Unused             |
| \$5B-\$5E | Expansion (unused) |
| $5F       | Checksum           |


The second half of the RTC's SRAM (NVRAM) is reserved for use by the KERNAL. \$20-\$3F is available for use by user programs.

For more information, please refer to this device's datasheet.

<!-- For PDF formatting -->
<div class="page-break"></div>

# Chapter 13: Working With CMDR-DOS

This manual describes Commodore DOS on FAT32, aka CMDR-DOS.

## CMDR-DOS

Commander X16 duplicates and extends the programming interface used by Commodore's line of disk drives, including the
famous (or infamous) VIC-1541. CMDR-DOS uses the industry-standard FAT-32 format. Partitions can be 32MB up to
(in theory) 2TB and supports CMD-style partitions, subdirectories, timestamps and filenames up to 255 characters.
It is the DOS built into the [Commander X16](https://www.commanderx16.com).

There are three basic interfaces for CMDR-DOS: the binary interface (LOAD, SAVE, etc.), the data file interface (OPEN,
PRINT#, INPUT#, GET#), and the command interface. We will give a brief summary of BASIC commands here, but please refer
to  [Chapter 4: BASIC Programming](X16%20Reference%20-%2004%20-%20BASIC.md#chapter-4-basic-programming) for full syntax of each command.

If you are familiar with the SD2IEC or the CMD hard drive, navigating partitions and subdirectories is similar, with "CD", "MD", and "RD" commands
to navigate directories.

## Binary Load/Save

The primary use of the binary interface is loading and saving program files and loading binary files into RAM.

Your binary commands are LOAD, SAVE, BLOAD, VLOAD, BVLOAD, VERIFY, and BVERIFY.

This is a brief summary of the LOAD and SAVE commands. For full documentation, refer to [Chapter 4: BASIC Programming](X16%20Reference%20-%2004%20-%20BASIC.md#chapter-4-basic-programming).

### LOAD

`LOAD <filename> [,device][,secondary_address]`
`LOAD <filename> [,device][,ram_bank,start_address]`

This reads a program file from disk. The first two bytes of the file are the memory location to which the file will be
loaded, with the low byte first. BASIC programs will start with $01 $08, which translates to $0801, the start of BASIC
memory.
The device number should be 8 for reading from the SD card.

If using the first form, secondary_address has multiple meanings:

* 0 or not present: load the data to address $0801, regardless of the address header.

* 1: load to the address specified in the file's header

* 2: load the file headerless to the location $0801.

If using the second form, ram_bank sets the bank for the load, and start_address is the location to read your data into.

The value of the ram_bank argument only affects the load when the start_address is set in the range of \$A000-\$BFFF.

Examples:

`LOAD "ROBOTS.PRG",8,1` loads the program "ROBOTS.PRG" into memory at the address encoded in the file.

`LOAD "HELLO",8` loads a program to the start of BASIC at $0801.

`LOAD "*",8,1` loads the first program in the current directory. See the section below on wildcards for more
information about using * and ? to access files of a certain type or with unprintable characters.

`LOAD "DATA.BIN",8,1,$A000` loads a file into banked RAM, RAM bank 1, starting at $A000. The first two bytes of the file are skipped. To avoid skipping the first two bytes, use the `BLOAD` command instead.

### SAVE

`SAVE <filename>[,device]`

Saves a file from the computer to the SD card. SAVE always reads from the beginning of BASIC memory at $0801, up to the
end of the BASIC program. Device is optional and defaults to 8 (the SD card, or an IEC disk drive, if one is plugged in.)

One word of caution: CMDR-DOS will not let you overwrite a file by default. To overwrite a file, you need to prefix
the filename with @:, like this:

`SAVE "@:DEMO.PRG"`

### BSAVE

`BSAVE <filename>,<device>,<ram_bank>,<start_address>,<end_address>`

Saves an arbitrary region of memory to a file without a two-byte header. To allow concatenating multiple regions of RAM into a single file with multiple successive calls to BSAVE, BSAVE allows the use of append mode in the filename string. To make use of this option, the first call to BSAVE can be called normally, which creates the file anew, while subsequent calls should be in append mode to the same file.

Another way to save arbitrary binary data from arbitrary locations is to use the S command in the MONITOR: [Chapter 7: Machine Language Monitor](X16%20Reference%20-%2007%20-%20Machine%20Language%20Monitor.md#chapter-7-machine-language-monitor).

`S "filename",8,<start_address>,<end_address>`

Where <start_address> and <end_address> are a 16-bit hexadecimal address.

After a SAVE or BSAVE, the DOS command is implicitly run to show the drive status. The Commodore file I/O model does not report certain failures back to BASIC, so you should double-check the result after a write operation.

```BASIC
00, OK,00,00

READY.
```

An OK reply means the file saved correctly. Any other result is an error that should be addressed:

```BASIC
63,FILE EXISTS,00,00
```

CMDR-DOS does not allow files to be overwritten without special handling. If you get FILE EXISTS, either change your file's name or save it with the @: prefix, like this:

`SAVE "@:HELLO"`

### BLOAD

BLOAD loads a file _without an address header_ to an arbitrary location in memory. Usage is similar to LOAD. However, BLOAD does not require
or use the 2-byte header. The first byte in the file is the first byte loaded into memory.
  
`BLOAD "filename",8,<ram_bank>,<start_address>`

### VLOAD

Read binary data into VERA. VLOAD skips the 2-byte address header and starts reading at the third byte of the file.

`VLOAD "filename",8,<vram_bank>,<start_address>`

### BVLOAD

Read binary data into VERA without a header. This works like BLOAD, but into VERA RAM.

`BVLOAD "filename",8,<vram_bank>,<start_address>`

### DOS WEDGE

The DOS wedge allows you to issue quick commands from BASIC with the > or @
symbol.

| Command | Action |
|-|-|
| `/<filename>` | Load a BASIC program into RAM |
| `%<filename>` | Load a machine language program into RAM (like `,8,1`) |
| `↑<filename>` | Load a BASIC program into RAM and then unconditionally run it |
| `←<filename>` | Save a BASIC program to disk |
| `@` | Display (and clear) the disk drive status |
| `@$` | Display the disk directory without overwriting the BASIC program in memory |
| `@#<device number>` | Change default DOS device |
| `@<command>` | Execute a disk drive command (e.g. `@S0:<filename>`) |
| `><command>` | Execute a disk drive command (e.g. `>CD:<dir>`) |

## Sequential Files

Sequential files have two basic modes: read and write. The OPEN command opens a file for reading or writing. The PRINT# command writes to a file, and the GET# and INPUT# commands read from the file.

todo: examples

## Command Channel

The command channel allows you to send commands to the CMDR-DOS interface. You can open and write to the command channel using the OPEN command, or you can use the DOS command to issue commands and read the status. While DOS can be used in immediate mode or in a program, only the combination of OPEN/INPUT# can read the command response back into a variable for later processing.

In either case, the ST pseudo-variable will allow you to quickly check the status. A status of 64 is "okay", and any
other value should be checked by reading the error channel (shown below.)

To open the command channel, you can use the OPEN command with secondary address 15.

`10 OPEN 15,8,15`

If you want to issue a command immediately, add your command string at the end of the OPEN statement:

`10 OPEN 15,8,15, "CD:/"`

This example changes to the root directory of your SD card.

To know whether the OPEN command succeeded, you must open the command channel and read the result. To read the command channel (and clear the error status if an error occurred), you need to read four values:

`20 INPUT#15,A,B$,C,D`

A is the error number. B$ is the error message. C and D are unused in CMDR-DOS for most responses, but will return the track and sector when used with a disk drive on the IEC connector.

```BASIC
30 PRINT A;B$;C;D
40 CLOSE 15
```

So the entire program looks like:

```BASIC
10 OPEN 15,8,15, "CD:/"
20 INPUT#15,A,B$,C,D
30 PRINT A;B$;C;D
40 CLOSE 15
```

If the error number (`A`) is less than 20, no error occurred. Usually this result is 0 (or 00) for OK.

You can also use the DOS command to send a command to CMDR-DOS. Entering DOS by itself will print the drive's status on the screen. Entering a command in quotes or a string variable will execute the command. We will talk more about the status variable and DOS status message in the next section.

```BASIC
DOS
00, 0K, 00, 00
READY.
DOS "CD:/"
```

The special case of `DOS "$"` will print a directory listing.

`DOS "$"`

You can also read the name of the current directory with DOS"$=C"

`DOS "$=C"`

## DOS Features

This is the base features set compared to other Commodore DOS devices:

| Feature          | 1541 | 1571/1581 | CMD HD/FD | SD2IEC   | _CMDR-DOS_      |
|------------------|------|-----------|-----------|----------|-----------------|
| Sequential files | yes  | yes       | yes       | yes      | yes             |
| Relative files   | yes  | yes       | yes       | yes      | not yet         |
| Block access     | yes  | yes       | yes       | yes      | not yet         |
| Code execution   | yes  | yes       | yes       | no       | yes             |
| Burst commands   | no   | yes       | yes       | no       | no              |
| Timestamps       | no   | no        | yes       | yes      | yes             |
| Time API         | no   | no        | yes       | yes      | not yet         |
| Partitions       | no   | no        | yes       | yes      | yes             |
| Subdirectories   | no   | no        | yes       | yes      | yes             |

It consists of the following components:

* Commodore DOS interface
  * `dos/main.s`: TALK/LISTEN dispatching
  * `dos/parser.s`: filename/path parsing
  * `dos/cmdch.s`: command channel parsing, status messages
  * `dos/file.s`: file read/write
* FAT32 interface
  * `dos/match.s`: FAT32 character set conversion, wildcard matching
  * `dos/dir.s`: FAT32 directory listing
  * `dos/function.s`: command implementations for FAT32
* FAT32 implementation
  * `fat32/*`: [FAT32 for 65c02 library](https://github.com/X16Community/x16-rom/tree/master/fat32)

All currently unsupported commands are decoded in `cmdch.s` anyway, but hooked into `31,SYNTAX ERROR,00,00`, so adding features should be as easy as adding the implementation.

CMDR-DOS implements the TALK/LISTEN layer (Commodore Peripheral Bus layer 3), it can therefore be directly hooked up to the Commodore IEEE KERNAL API (`talk`, `tksa`, `untlk`, `listn`, `secnd`, `unlsn`, `acptr`, `ciout`) and be used as a computer-based DOS, like on the C65 and the X16.

CMDR-DOS does not contain a layer 2 implementation, i.e. IEEE-488 (PET) or Commodore Serial (C64, C128, ...). By adding a Commodore Serial (aka "IEC") implementation, CMDR-DOS could be adapted for use as the system software of a standalone 65c02-based Serial device for Commodore computers, similar to an sd2iec device.

The Commodore DOS side and the FAT32 side are well separated, so a lot of code could be reused for a DOS that uses a different filesystem.

Or the core feature set, these are the supported functions:

| Feature                          | Syntax                        | Supported | Comment                                                                                                                       |
|----------------------------------|-------------------------------|-----------|-------------------------------------------------------------------------------------------------------------------------------|
| Reading                          | `,?,R`                        | yes       |                                                                                                                               |
| Writing                          | `,?,W`                        | yes       |                                                                                                                               |
| Appending                        | `,?,A`                        | yes       | Warning, see below<sup>1</sup>                                                                                                |
| Modifying                        | `,?,M`                        | yes       |                                                                                                                               |
| Types                            | `,S`/`,P`/`,U`/`,L`           | yes       | ignored on FAT32                                                                                                              |
| Overwriting                      | `@:`                          | yes       |                                                                                                                               |
| Magic channels 0/1               |                               | yes       |                                                                                                                               |
| Channel 15 command               | _command_`:`_args_...         | yes       |                                                                                                                               |
| Channel 15 status                | _code_`,`_string_`,`_a_`,`_b_ | yes       |                                                                                                                               |
| CMD partition syntax             | `0:`/`1:`/...                 | yes       |                                                                                                                               |
| CMD subdirectory syntax          | `//DIR/:`/`/DIR/:`            | yes       |                                                                                                                               |
| Directory listing                | `$`                           | yes       |                                                                                                                               |
| Dir with name filtering          | `$:FIL*`                      | yes       |                                                                                                                               |
| Dir with name and type filtering | `$:*=P`/`$:*=D`/`$:*=A`       | yes       |                                                                                                                               |
| Dir with timestamps              | `$=T`                         | yes       | with ISO-8601 times                                                                                                           |
| Dir with time filtering          | `$=T<`/`$=T>`                 | not yet   |                                                                                                                               |
| Dir long listing                 | `$=L`                         | yes       | shows human readable file size instead of blocks, time in ISO-8601 syntax, attribute byte, and exact file size in hexadecimal |
| Partition listing                | `$=P`                         | yes       |                                                                                                                               |
| Partition filtering              | `$:NAME*=P`                   | no        |                                                                                                                               |
| Current Working Directory        | `$=C`                         | yes       |                                                                                                                               |

* <sup>1</sup>: Warning: Risk of corrupting SD cards on older ROM versions, see [Appending to file](#appending-to-file)

And this table shows which of the standard commands are supported:

| Name             | Syntax                                                | Description                     | Supported |
|------------------|-------------------------------------------------------|---------------------------------|-----------|
| BLOCK-ALLOCATE   | `B-A` _medium_ _medium_ _track_ _sector_              | Allocate a block in the BAM     | no<sup>1</sup>|
| BLOCK-EXECUTE    | `B-E` _channel_ _medium_ _track_ _sector_             | Load and execute a block        | not yet   |
| BLOCK-FREE       | `B-F` _medium_ _medium_ _track_ _sector_              | Free a block in the BAM         | no<sup>1</sup>|
| BLOCK-READ       | `B-R` _channel_ _medium_ _track_ _sector_             | Read block                      | no<sup>1</sup>|
| BLOCK-STATUS     | `B-S` _channel_ _medium_ _track_ _sector_             | Check if block is allocated     | no<sup>1</sup>|
| BLOCK-WRITE      | `B-W` _channel_ _medium_ _track_ _sector_             | Write block                     | no<sup>1</sup>|
| BUFFER-POINTER   | `B-P` _channel_ _index_                               | Set r/w pointer within buffer   | not yet   |
| CHANGE DIRECTORY | `CD`[_path_]`:`_name_                                 | Change the current sub-directory| yes       |
| CHANGE DIRECTORY | `CD`[_medium_]`:←`                                    | Change sub-directory up         | yes       |
| CHANGE PARTITION | `CP` _num_                                            | Make a partition the default    | yes       |
| COPY             | `C`[_path_a_]`:`_target_name_`=`[_path_b_]`:`_source_name_[`,`...] | Copy/concatenate files | yes   |
| COPY             | `C`_dst_medium_`=`_src_medium_                        | Copy all files between disk     | no<sup>1</sup>|
| DUPLICATE        | `D:`_dst_medium_``=``_src_medium_                     | Duplicate disk                  | no<sup>1</sup>|
| FILE LOCK        | `F-L`[_path_]`:`_name_[`,`...]                        | Enable file write-protect       | yes       |
| FILE RESTORE     | `F-R`[_path_]`:`_name_[`,`...]                        | Restore a deleted file          | not yet   |
| FILE UNLOCK      | `F-U`[_path_]`:`_name_[`,`...]                        | Disable file write-protect      | yes       |
| GET DISKCHANGE   | `G-D`                                                 | Query disk change               | yes       |
| GET PARTITION    | `G-P`[_num_]                                          | Get information about partition | yes       |
| INITIALIZE       | `I`[_medium_]                                         | Re-mount filesystem             | yes       |
| LOCK             | `L`[_path_]`:`_name_                                  | Toggle file write protect       | yes       |
| MAKE DIRECTORY   | `MD`[_path_]`:`_name_                                 | Create a sub-directory          | yes       |
| MEMORY-EXECUTE   | `M-E` _addr_lo_ _addr_hi_                             | Execute code                    | yes       |
| MEMORY-READ      | `M-R` _addr_lo_ _addr_hi_ [_count_]                   | Read RAM                        | yes       |
| MEMORY-WRITE     | `M-W` _addr_lo_ _addr_hi_ _count_ _data_              | Write RAM                       | yes       |
| NEW              | `N`[_medium_]`:`_name_`,`_id_`,FAT32`                 | File system creation            | yes<sup>3</sup>|
| REMOVE DIRECTORY | `RD`[_path_]`:`_name_                                 | Delete a sub-directory          | yes       |
| RENAME           | `R`[_path_]`:`_new_name_`=`_old_name_                 | Rename file                     | yes       |
| RENAME-HEADER    | `R-H`[_medium_]`:`_new_name_                          | Rename a filesystem             | yes       |
| RENAME-PARTITION | `R-P:`_new_name_`=`_old_name_                         | Rename a partition              | no<sup>1</sup>|
| SCRATCH          | `S`[_path_]`:`_pattern_[`,`...]                       | Delete files                    | yes       |
| SWAP             | `S-`{`8`&#x7c;`9`&#x7c;`D`}                           | Change primary address          | yes       |
| TIME READ ASCII  | `T-RA`                                                | Read Time/Date (ASCII)          | no<sup>4</sup>|
| TIME READ BCD    | `T-RB`                                                | Read Time/Date (BCD)            | no<sup>4</sup>|
| TIME READ DECIMAL| `T-RD`                                                | Read Time/Date (Decimal)        | no<sup>4</sup>|
| TIME READ ISO    | `T-RI`                                                | Read Time/Date (ISO)            | no<sup>4</sup>|
| TIME WRITE ASCII | `T-WA` _dow_ _mo_`/`_da_`/`_yr_ _hr_`:`_mi_`:`_se_ _ampm_ | Write Time/Date (ASCII)     | no<sup>4</sup>|
| TIME WRITE BCD   | `T-WB` _b0_ _b1_ _b2_ _b3_ _b4_ _b5_ _b6_ _b7_ _b8_   | Write Time/Date (BCD)           | no<sup>4</sup>|
| TIME WRITE DECIMAL| `T-WD` _b0_ _b1_ _b2_ _b3_ _b4_ _b5_ _b6_ _b7_       | Write Time/Date (Decimal)       | no<sup>4</sup>|
| TIME WRITE ISO   | `T-WI` _yyyy_`-`_mm_`-`_dd_`T`_hh_`:`_mm_`:`_ss_ _dow_| Write Time/Date (ISO)           | no<sup>4</sup>|
| U1/UA            | `U1` _channel_ _medium_ _track_ _sector_              | Raw read of a block             | not yet   |
| U2/UB            | `U2` _channel_ _medium_ _track_ _sector_              | Raw write of a block            | not yet   |
| U3-U8/UC-UH      | `U3` - `U8`                                           | Execute in user buffer          | not yet   |
| U9/UI            | `UI`                                                  | Soft RESET                      | yes       |
| U:/UJ            | `UJ`                                                  | Hard RESET                      | yes       |
| USER             | `U0>` _pa_                                            | Set unit primary address        | yes       |
| USER             | `U0>B` _flag_                                         | Enable/disable Fast Serial      | yes<sup>6</sup>|
| USER             | `U0>D`_val_                                           | Set directory sector interleave | no<sup>1</sup>|
| USER             | `U0>H` _number_                                       | Select head 0/1                 | no<sup>1</sup>|
| USER             | `U0>L`_flag_                                          | Large REL file support on/off   | no        |
| USER             | `U0>M` _flag_                                         | Enable/disable 1541 emulation mode| no<sup>1</sup>|
| USER             | `U0>R` _num_                                          | Set number fo retries           | no<sup>1</sup>|
| USER             | `U0>S` _val_                                          | Set sector interleave           | no<sup>1</sup>|
| USER             | `U0>T`                                                | Test ROM checksum               | no<sup>5</sup>|
| USER             | `U0>V` _flag_                                         | Enable/disable verify           | no<sup>1</sup>|
| USER             | `U0>` _pa_                                            | Set unit primary address        | yes       |
| USER             | `UI`{`+`&#x7c;`-`}                                    | Use C64/VIC-20 Serial protocol  | no<sup>1</sup>|
| UTILITY LOADER   | `&`[[_path_]`:`]_name_                                | Load and execute program        | no<sup>1</sup>|
| VALIDATE         | `V`[_medium_]                                         | Filesystem check                | no<sup>2</sup>|
| WRITE PROTECT    | `W-`{`0`&#x7c;`1`}                                    | Set/unset device write protect  | yes       |

* <sup>1</sup>: outdated API, not useful, or can't be supported on FAT32
* <sup>2</sup>: is a no-op, returns `00, OK,00,00`
* <sup>3</sup>: third argument `FAT32` _has_ to be passed
* <sup>4</sup>: CMDR-DOS was architected to run on the main computer, so it shouldn't be DOS that keeps track of the time
* <sup>5</sup>: Instead of testing the ROM, this command currently verifies that no buffers are allocated, otherwise it halts. This is used by unit tests to detect leaks.
* <sup>6</sup>: Repurposed for SD card read and write mode. _flag_ selects whether fast read (auto_tx) and fast writes are enabled. 0=none, 1=auto_tx, 2=fast writes, 3=both

The following special file syntax and `OPEN` options are specific to CMDR-DOS:

| Feature               | Syntax      | Description                                                                    |
|-----------------------|-------------|--------------------------------------------------------------------------------|
| Open for Read & Write | `,?,M`      | Allows arbitrarily reading, writing and setting the position (`P`)<sup>7</sup> |
| Get current working directory | `$=C` | Produces a directory listing containing the name of the current working directory followed by all parent directory names all the way up to `/` |

* <sup>7</sup>: once the EOF has been reached while reading, no further reads or writes are possible.

The following added command channel features are specific to CMDR-DOS:

| Feature               | Syntax      | Description                                                                    |
|-----------------------|-------------|--------------------------------------------------------------------------------|
| FATLBA<sup>9</sup>    | `FL` _channel_ | Return the current LBA, cluster number, sector index, and cluster shift; channel arg is binary |
| POSITION              | `P` _channel_ _p0_ _p1_ _p2_ _p3_  | Set position within file (like sd2iec); all args binary |
| TELL<sup>8</sup>      | `T` _channel_ | Return the current position within a file and the file's size; channel arg is binary |

* <sup>8</sup>: available in ROM version R48 and later
* <sup>9</sup>: available in ROM version R49 and later

To use the FATLBA, POSITION, and TELL commands, you need to open two channels: a data channel and the command channel. The _channel_ argument should be the same as the secondary address of the data channel.

If FATLBA succeeds, `07,llllllll cccccccc,ii,ss` is returned on the command channel, where `llllllll` is a hexadecimal representation of the raw LBA at the file's current position, `cccccccc` is a hexadecimal representation of the associated cluster within the filesystem, `ii` is a decimal index of the sector within a cluster, and `ss` is a decimal representation of the _cluster shift_ value.  Cluster shift relates to the filesystem's cluster size, where the cluster size in bytes is 2<sup>9+`ss`</sup>.  Note that `ii` can add a third digit when the value exceeds 99, as cluster shift 7 has sector index values up to 127.  

If POSITION succeeds, `00, OK,00,00` is returned on the command channel.  

If TELL succeeds, `07,pppppppp ssssssss,00,00` is returned on the command channel, where `pppppppp` is a hexadecimal representation of the position, and `ssssssss` is a hexadecimal representation of the file's size.  

### Examples

```BASIC
OPEN 1,8,2,"LEVEL.DAT,S,R"
OPEN 15,8,15,"P"+CHR$(2)+CHR$(0)+CHR$(1)+CHR$(0)+CHR$(0)
```

The above opens LEVEL.DAT for reading and positions the read/write pointer at byte 256.

```BASIC
10 OPEN 2,8,5,"LEVEL.DAT,S,R"
20 OPEN 15,8,15,"T"+CHR$(5)
30 INPUT#15,A,A$,T,S
40 CLOSE 15
50 IF A>=20 THEN 90
60 SZ=VAL("$"+MID$(A$,10))
70 PRINT "SIZE=";SZ
80 GOTO 100
90 PRINT"ERROR"
100 CLOSE 2
```

This time, the secondary address is 5, and we're fetching only the file's size.

### Current Working Directory

The $=C command will list the current working directory and its parent path. The current directory will be at the top of the listing, with each parent
directory beneath, with / at the bottom.

```BASIC
DOS"$=C"

0 "/TEST            " 
0    "TEST"             DIR
0    "/"                DIR
65535 BLOCKS FREE.
```
### Appending to file

To append data to an existing file, open the file with `,?,A` and write to it.

**Warning:** Appending to an empty file using R48 or older, will corrupt the file system, due to a severe Kernal bug. The bug is fixed in [#369](https://github.com/X16Community/x16-rom/pull/369). Keep this in mind when releasing software which appends to files, as some users may have older ROM versions installed.

## License

Copyright 2020-2025 Michael Steil <<mist64@mac.com>>, et al.

Redistribution and use in source and binary forms, with or without modification, are permitted provided that the following conditions are met:

1. Redistributions of source code must retain the above copyright notice, this list of conditions and the following disclaimer.

2. Redistributions in binary form must reproduce the above copyright notice, this list of conditions and the following disclaimer in the documentation and/or other materials provided with the distribution.

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

<!-- For PDF formatting -->
<div class="page-break"></div>

# Chapter 14: Hardware Pinouts

This chapter covers pinout for the I/O ports and headers.

## Port and Socket Listing

* VERA Connectors
* SNES Controller Ports (x2)
* IEC Port
* PS/2 Keyboard and mouse
* Expansion Slots (x4 in Gen1)
* User Port Header
* ATX Power Supply
* Front Panel

Chip sockets are not listed; pinouts are available on their respective data sheets.

## Disclaimer

The instructions and information in this document are the best available information at the time of writing. This information is subject to change, and no warranty is implied. We are not liable for damage or injury caused by use or misuse of this information, including damage caused by inaccurate information. Interfacing and modifying your Commander X16 is done solely at your own risk.

If you attempt to upgrade your firmware and the process fails, one of our community members may be able to help. Please visit the forums or the Discord community, both of which can be reached through <https://commanderx16.com>.

### SNES Ports

The computer contains two SNES style ports and will work with Super Nintendo compatible game pads. An on-board pin header is accessible to connect two additional SNES ports.

![SNES Controller Port](images/SNES_Controller_Female.png)

| Pin # | Description | Wire Color  |
|-------|-------------|-------------|
| 1     | +5v         | White       |
| 2     | Data Clock  | Yellow/Red  |
| 3     | Data Latch  | Orange      |
| 4     | Serial Data | Red/Yellow  |
| 5     | N/C         | -           |
| 6     | N/C         | -           |
| 7     | Ground      | Brown       |

The Data Clock and Data Latch are generated by the computer and are shared across all SNES ports. The Serial Data line is unique per controller.

Thanks to [Console Mods Wiki](https://consolemods.org/wiki/SNES:Connector_Pinouts)

### IEC Port

The IEC port is a female 6 pin DIN 45322 connector. The pinout and specifications are the same as the Commodore 128 computer, with the required lines for Fast IEC, as used by the 1571 and 1581 diskette drives. 1541 drives are also compatible, using standard IEC mode at 400-600 bytes/sec.

![IEC Serial Port](images/iec_port.gif)

|Pin | Description  | Signal Direction  | Remark |
|----|--------------|-------------------|--------|
| 1  | SERIAL SRQ   | IN                | Serial Service Request In, at the C128 "Fast Serial Clock" |
| 2  | GND          | -                 | Ground, signal ground (0V) |
| 3  | SERIAL ATN   | OUT               | Attention, for the selection of a device at beginning/end of a transmission |
| 4  | SERIAL CLK   | IN/OUT            | Clock (for data transmission) |
| 5  | SERIAL DATA  | IN/OUT            | Data  |
| 6  | SERIAL RESET | OUT(/IN)          | Reset |

The IEC protocol is beyond the scope of this document. Please see [Wikipedia](https://en.wikipedia.org/wiki/Commodore_bus) for more information.

### PS/2 Keyboard and Mouse

![PS/2 Pinout](images/ps2_pinout.png)

| Pin | Name  | Description    |
|-----|-------|----------------|
| 1   | +DATA | Data           |
| 2   | NC    | Not connected  |
| 3   | GND   | Ground         |
| 4   | Vcc   | +5 VDC         |
| 5   |+CLK   | Clock          |
| 6   | NC    | Not Connected  |

### Expansion Cards / Cartridges

The expansion slots can be used for I/O modules and RAM/ROM cartridges and expose the
full CPU address and data bus, plus the ROM bank select lines, stereo audio, and 5 IO select lines.

The expansion/cartridge port is a 60-pin edge connector with 2.54mm pitch.
Pin 1 is in the rear-left corner.

|   Desc |  Pin |   | Pin  | Desc |
|-------:|-----:|---|------|------|
|   -12V |   1 |\[ \]| 2  | +12V  |
|    GND |   3 |\[ \]| 4  | +5V   |
|AUDIO_L |   5 |\[ \]| 6  | GND   |
|AUDIO_R |   7 |\[ \]| 8  | ROMB7 |
|    IO3 |   9 |\[ \]| 10 | ROMB0 |
|    IO4 |  11 |\[ \]| 12 | ROMB1 |
|    IO7 |  13 |\[ \]| 14 | ROMB6 |
|    IO5 |  15 |\[ \]| 16 | ROMB2 |
|    IO6 |  17 |\[ \]| 18 | ROMB5 |
|   RESB |  19 |\[ \]| 20 | ROMB3 |
|    RDY |  21 |\[ \]| 22 | ROMB4 |
|   IRQB |  23 |\[ \]| 24 | PHI2  |
|     BE |  25 |\[ \]| 26 | RWB   |
|   NMIB |  27 |\[ \]| 28 | MLB   |
|   SYNC |  29 |\[ \]| 30 | D0    |
|     A0 |  31 |\[ \]| 32 | D1    |
|     A1 |  33 |\[ \]| 34 | D2    |
|     A2 |  35 |\[ \]| 36 | D3    |
|     A3 |  37 |\[ \]| 38 | D4    |
|     A4 |  39 |\[ \]| 40 | D5    |
|     A5 |  41 |\[ \]| 42 | D6    |
|     A6 |  43 |\[ \]| 44 | D7    |
|     A7 |  45 |\[ \]| 46 | A15   |
|     A8 |  47 |\[ \]| 48 | A14   |
|     A9 |  49 |\[ \]| 50 | A13   |
|    A10 |  51 |\[ \]| 52 | A12   |
|    A11 |  53 |\[ \]| 54 | SDA   |
|    GND |  55 |\[ \]| 56 | SCL   |
|    +5V |  57 |\[ \]| 58 | GND   |
|   +12V |  59 |\[ \]| 60 | -12V  |

To simplify address decoding, pins IO3-IO7 are active for specific, 32-byte memory mapped IO
(MMIO) address ranges.

| Address     | Usage                                    |Speed|
|-------------|------------------------------------------|-----|
|$9F60-$9F7F|Expansion Card Memory Mapped IO3            |8 MHz|
|$9F80-$9F9F|Expansion Card Memory Mapped IO4            |8 MHz|
|$9FA0-$9FBF|Expansion Card Memory Mapped IO5            |2 MHz|
|$9FC0-$9FDF|Expansion Card Memory Mapped IO6            |2 MHz|
|$9FE0-$9FFF|Cartridge/Expansion Memory Mapped IO7, POST |2 MHz|

Expansion cards can use the IO3-IO6 lines as enable lines to provide their IO address range
(s), or decode the address from the address bus directly. To prevent conflicts with other
devices, expansion boards should allow the user to select their desired I/O bank with jumpers
or DIP switches. IO7 is given priority to external cartridges that use MMIO and should be
only used by an expansion card if there are no other MMIO ranges available. Doing so may
cause a bus conflict with cartridges that make use of MMIO (such as those with expansion
hardware). See below for more information on cartridges.

As of R49, the last I/O address inside IO7 (`$9FFF`) can have POST codes written to it under
certain conditions during boot.  See [Appendix E: Diagnostic Bank](X16%20Reference%20-%20Appendix%20E%20-%20Diagnostic%20Bank.md#POST)
for details, and for what to expect when configuring an expansion card at this address.

ROMB0-ROMB7 are connected to the ROM bank latch at address `$01`. Values 0-31 (`$00`-`$1F`)
address the on-board ROM chips, and 32-255 are intended for expansion ROM or RAM chips
(typically used by cartridges, see below). This allows for a total of 3.5MB of address space
in the `$C000-$FFFF` address range.

SCL and SDA pins are shared with the i2c connector on J9 and can be used to access i2c
peripherals on cartridges or expansion cards.

AUDIO_L and AUDIO_R are routed to J10, the audio option header.

The other pins are connected to the system bus and directly to the 65C02 processor.

#### Cartridges

Cartridges are essentially an expansion card housed in an external enclosure. Typically they are
used for applications (e.g. games) with the X16 being able to boot directly from a cartridge at
power on. They contain banked ROM and/or RAM and an optional I2C EEPROM
(for storing game save states).

They can also function as an expansion card which means they can also use MMIO. Similarly an internal
expansion card could contain RAM/ROM as well.

Because of this, while developers are free to use the hardware as they please, to avoid
conflcits, the banked ROM/RAM space is suggested to be used only by cartridges and
cartridges should avoid using MMIO IO3-IO6. Instead, IO7 should be the default option
for cartridges and the last option for expansion cards (only used if there are no
other IO ranges available).

This helps avoid bus conflicts and an otherwise bad user experience given a
cartridge should be simple to use from the standpoint of the user
("insert game -> play game").

These are soft guidelines. There is nothing physically preventing an expansion card from using
banked ROM/RAM or a cartridge using any of the MMIO addresses. Doing so risks conflicts and
compatibility issues.

Cartridges with additional hardware would be similar to expansion chips found on some NES and
SNES cartridges (think VRC6, Super FX, etc.) and could be used for really anything,
such as having a MIDI input for a cartridge that is meant as a music maker;
some sort of hardware accelerator FPGA; network support, etc.

For more information about the memory map visit
[Chapter 8: Memory Map](X16%20Reference%20-%2008%20-%20Memory%20Map.md#chapter-8-memory-map).

##### Booting from Cartridges

After the X16 finishes it's hardware initialization, the kernel checks bank 32 for the signature "CX16"
at `$C000`. If found, it then jumps to `$C004` and leaves interrupts disabled.

### ATX Power Supply

The Commander X16 has a socket for an industry standard 24-pin ATX power supply connector. Either a 24-pin or 20-pin PSU connector can be plugged in, though only the pins for the older 20-pin standard are used by the computer. You don't need an expensive power supply, but it must supply the -12v rail. Not all do, so check your unit to make sure. If you can't tell from the label, you can check Pin 12 and COM. If the clip side is facing away from you, pin 14 will be the second pin on the left on the clip side. For a 20-pin cable, -12v is on pin 12, but at the same relative position &mdash; the second pin on the left on the clip side.

|24-pin ATX power connector, cable end|
|-|
|![Cable end view of ATX power connector](images/atx_24_pin-small.png)|

By CalvinTheMan - Own work, CC BY-SA 4.0, <https://commons.wikimedia.org/w/index.php?curid=50881708>

The Commander X16 does not use the 4-pin CPU power, GPU power, 4-pin drive power, or SATA power connectors.

To save space, when running a bare motherboard, we recommend a "Pico PSU" power supply, which derives all of the necessary power lines from a single 12V source.

### J1 ROM Write Protect

Remove J1 to write protect system ROM. With J1 installed, users can program the system ROM using an appropriate ROM flash program.

### J2 NMI

Connect a button here to generate an Non Maskable Interrupt (NMI) on the CPU. This will execute a BASIC warm start, which will stop any existing program, clear the screen, and print the READY prompt.

### J3 Parallel/user port pullup resistors

When connected, activates 4.7k pullup resistors for PB0, PB4, PB6, PB7 and CA1 of the user port.

Printed on PCB: Connect J8 for LPT Compat. (TODO: Is this the Centronics parallel port mode Lorin hinted at early on?)

### J4 Extra 65C22 Pins

PRxxxxx:
| Pin | Desc |
|-----|------|
|  1  | PB0  |
|  2  | PB1  |
|  3  | PB2  |
|  4  | CB2  |

DEVxxxxx:
| Pin | Desc |
|-----|------|
|  1  | CA1  |
|  2  | CA2  |
|  3  | PB0  |
|  4  | PB1  |
|  5  | PB2  |
|  6  | CB2  |

These pins are connected to VIA 1 at $9F00-$9F0F.

### J5 SMC I2C (DEVxxxxx boards only)

DEVxxxxx boards: Remove jumpers from J5 to disconnect SMC from I2C bus. This allows serial programming of SMC via J9.

PRxxxxx boards: J5 is not present. On-board serial programming of SMC is not possible.

| Desc    | Pin |   | Pin | Desc    |
|--------:|----:|---|-----|---------|
| SCL_SMC |  1  |. .|  2  | SDA_SMC |
| SCL     |  3  |. .|  4  | SDA     |

### J6 System Speed

| Pin    | Desc          |
|--------|---------------|
|  1 - 2 | 8 MHz         |
|  3 - 4 | 4 MHz         |
|  5 - 6 | 2 MHz         |

### J7 SNES 3/4

| Desc  | Pin |   | Pin | Desc |
|------:|----:|---|-----|------|
| CLC   |  1  |. .|  2  | VCC  |
| LATCH |  3  |. .|  4  | DAT4 |
| DAT3  |  5  |. .|  6  | GND  |

These pins will allow for two additional SNES controllers, for a total of four controllers on the system.

### J8 Front Panel

|   Desc    | Pin |   | Pin | Desc      |
|----------:|----:|---|-----|-----------|
| HDD LED+  |  1  |. .|  2  | POW LED + |
| HDD LED-  |  3  |. .|  4  | POW LED - |
| RESET BUT |  5  |. .|  6  | POW BUT   |
| RESET BUT |  7  |. .|  7  | POW BUT   |
| +5VDC     |  9  |. .|  10 | NC        |

This pinout is compatible with newer ATX style motherboards. AT motherboards and older ATX cases may still have a 3-pin power LED connector (with a blank pin in the middle.) You will need to move the + (red) wire on the power LED connector to the center pin, if this is the case. Or you can use two Male-Female breadboard cables to jumper the header to your power LED connector.

There is no on-board speaker header. Instead, all audio is routed to the rear panel headphone jack via the Audio Option header.

### J9 I2C/SMC Header

There are two different layouts for the SMC header.

This is the layout on the production boards (PRxxxxx):

| Desc             | Pin |   | Pin | Desc        |
|-----------------:|----:|---|-----|-------------|
| I2C SDA           |  1  |. .|  2  | +5V        |
| RTC MFP           |  3  |. .|  4  | SMC TX     |
| RESB              |  5  |. .|  6  | SMC RX     |
| I2C SCL           |  7  |. .|  8  | GND        |
| 5VSB              |  9  |. .|  10 | GND        |

This is the layout on the DEVxxxxx boards:

| Desc             | Pin |   | Pin | Desc        |
|-----------------:|----:|---|-----|-------------|
| SMC MOSI/I2C SDA  |  1  |. .|  2  | +5VSB      |
| RTC MFP           |  3  |. .|  4  | SMC TX     |
| SMC Reset         |  5  |. .|  6  | SMC RX     |
| SMC SCK/I2C SCL   |  7  |. .|  8  | GND        |
| MISO              |  9  |. .|  10 | GND        |

DEVxxxxx boards supports in-system serial programming using J9 and J5. This is not possible with PRxxxxx boards.

Note that pin 5 is connected to different SMC pins for DEV and PR boards, despite similar names. "SMC reset" (DEV) resets SMC, while "RESB" (PR) resets the rest of the system.

### J10 Audio Option

| Desc   | Pin |   | Pin | Desc  |
|-------:|----:|---|-----|-------|
| SDA    |  1  |. .|  2  | RESB  |
| SCL    |  3  |. .|  4  | VCC   |
|        |  5  |. .|  6  |       |
| +12V   |  7  |. .|  8  | -12V  |
|        |  9  |. .| 10  |       |
| VERA_L | 11  |. .| 12  | BUS_L |
|        | 13  |. .| 14  |       |
| VERA_R | 15  |. .| 16  | BUS_R |
|        | 17  |. .| 18  |       |
| YM_L   | 19  |. .| 20  | OUT_L |
|        | 21  |. .| 22  |       |
| YM_R   | 23  |. .| 24  | OUT_R |

5,6,9,10,13,14,17,18,21,22 - GND

Next to the audio header is a set of jumper pads, JP1-JP6. Cutting these traces allows you to extract isolated audio from each of the system devices or build a mixer to adjust the relative balance of the audio devices.

In order to avoid ground loop and power supply noise, we recommend installing a ground loop isolator when using an external mixer. 2 or 3 isolators will be required (one for each stereo pair.)  (TODO: measure noise and test with pro audio gear.)

### J12 User Port

| Desc    | Pin |   | Pin | Desc    |
|--------:|----:|---|-----|---------|
| PB0     |  1  |. .|  2  | PB4     |
| PA0     |  3  |. .|  4  | PB5     |
| PA1     |  5  |. .|  6  | PB6/CB1 |
| PA2     |  7  |. .|  8  | PB7/CB2 |
| PA3     |  9  |. .| 10  | GND     |
| PA4     | 11  |. .| 12  | GND     |
| PA5     | 13  |. .| 14  | GND     |
| PA6     | 15  |. .| 16  | GND     |
| PA7     | 17  |. .| 18  | GND     |
| CA1     | 19  |. .| 20  | GND     |
| PB1     | 21  |. .| 22  | GND     |
| PB2     | 23  |. .| 24  | GND     |
| PB3/CA2 | 25  |. .| 16  | VCC     |

User port is connected to VIA 2 at address $9F10-$9F1F. This can be used for serial or parallel port I/O. Commander X16 does not have support for a serial port device in the KERNAL.

## VERA Video Header (J11)

| Desc    | Pin |   | Pin | Desc    |
|--------:|----:|---|-----|---------|
| VCC     |  1  |. .|  2  | GND     |
| D7      |  3  |. .|  4  | D6      |
| D5      |  5  |. .|  6  | D4      |
| D3      |  7  |. .|  8  | D2      |
| D1      |  9  |. .| 10  | D0      |
| /IO1    | 11  |. .| 12  | RESB    |
| /MEMWE  | 13  |. .| 14  | IRQB    |
| A4      | 15  |. .| 16  | /MEMOE  |
| A2      | 17  |. .| 18  | A3      |
| A0      | 19  |. .| 20  | A1      |
| GND     | 21  |. .| 22  | GND     |
| VERA_L  | 23  |. .| 24  | VERA_R  |

VERA is connected to I/O ports at $9F20-$9F3F. See [Chapter 9: VERA Programmer's Reference](X16%20Reference%20-%2009%20-%20VERA%20Programmer's%20Reference.md#chapter-9-vera-programmers-reference)
for details.

### VGA Connector

![VGA Connector](images/VGA_Port.png)

| Pin | Desc      |
|-----|-----------|
| 1   | RED |
| 2   | GREEN |
| 3   | BLUE |
| 4   | |
| 5   | GND |
| 6   | RED_RTN |
| 7   | GREEN_RTN |
| 8   | BLUE_RTN |
| 9   | |
| 10  | GND |
| 11  | |
| 12  | |
| 13  | HSync |
| 14  | VSync |
| 15  | |

The VGA connector is a female [DE-15](https://en.wikipedia.org/wiki/D-subminiature#Description,_nomenclature,_and_variants) jack.

The video resolution is 640x480 59.5FPS progressive scan, RGB color, and separated H/V sync.

In interlace mode, both horizontal and vertical sync pulses will appear on the HSync pin. (TODO: Test with OSSC).

VERA does not use the ID/DDC lines.

### Composite Connector

The Composite video is a standard RCA connector. Center pin carries signal. Shield is signal ground.

The signal is NTSC Composite baseband video.

The video is 480 lines 59.97Hz interlaced. Composite is not available when VGA is running at 59.5Hz progressive scan.

### S-Video Connector

![S-Video Connector](images/s_video.png)

| Pin | Desc      |                       |
|-----|-----------|-----------------------|
| 1   | GND (Y)   |                       |
| 2   | GND (C)   |                       |
| 3   | Y         | Intensity (Luminance) |
| 4   | C         | Color (Chrominance)   |

The connector is a 4-pin Mini-DIN connector. While the same size as a PS/2 connector, the PS/2 connector has a plastic key at the bottom. Do not attempt to plug a keyboard or mouse into the S-Video port, or bent pins will occur.

The signal is NTSC baseband Y/C separated video. S-Video provides better resolution than composite, since the color and intensity are provided on separate pins. you can use a splitter cable to separate the Y and C signals to drive a Commodore 1702 or compatible monitor.

The video is 480 lines 59.97Hz interlaced. Composite is not available when VGA is running at 59.5Hz progressive scan.

### J2 VERA Programming Interface

| Pin | Desc          |
|-----|---------------|
|  1  | +5V           |
|  2  | FPGA_CDONE    |
|  3  | FPGA_CRESET_B |
|  4  | SPI_MISO      |
|  5  | SPI_MOSI      |
|  6  | SPI_SCK       |
|  7  | SPI_SSEL_N    |
|  8  | GND           |

### VERA J7 Remote SD Card Option

| Pin | Desc |
|-----|------|
|  1  | CS   |
|  2  | SCK  |
|  3  | MOSI |
|  4  | MISO |
|  5  | +5V  |
|  6  | GND  |

This requires an EEPROM programmer and an interface board to program. See [Chapter 15](X16%20Reference%20-%2015%20-%20Upgrade%20Guide.md#chapter-15-upgrade-guide) for the programming adapter and instructions.

<!-- For PDF formatting -->
<div class="page-break"></div>

# Chapter 15: Upgrade Guide

This chapter provides tips for running upgrades on the various programmable chips.

**WARNING**: flashing any of these components has a risk of leading to an unbootable system. At the current time, doing hardware flash updates requires skill and knowledge beyond that of an ordinary end user and is not recommended without guidance from the community on the Commander X16 Discord.

Under the headings of each component is a matrix which indicates which software tools can be used to perform the flash of that component, depending on which flashing hardware you have access to and the operating system of the computer you have the device connected to. Some components of the Commander X16 can be self-flashed, but the risk of a failed flash rendering your X16 unbootable is high, in which case an external programmer must be used to flash the component and thus "unbrick" the system.

### Flashable components
* System ROM
* SMC (PS/2 and Power controller)
* VERA

## System ROM

Official community system ROMs will be posted as releases at [X16Community/x16-emulator](https://github.com/X16Community/x16-emulator/releases) inside the distribution for the Emulator.

TODO: link to instructions for each solution in the matrix

| ↓ Hardware / OS → | Windows | Linux | Mac OS | Commander X16 |
|-|-|-|-|-|
| Commander X16 | - | - | - | x16-flash |
| XGecu TL866II+ | Xgpro | minipro | minipro | - |
| XGecu TL866-3G / T48 | Xgpro | - | - | - |

## SMC

Official community SMC ROMs will be posted as releases at [X16Community/x16-smc](https://github.com/X16Community/x16-smc/releases).

TODO: link to instructions for each solution in the matrix

| ↓ Hardware / OS → | Windows | Linux | Mac OS | Commander X16 |
|-|-|-|-|-|
| Commander X16 | - | - | - | - |
| USBtinyISP | arduino | arduino | arduino | - |
| XGecu TL866II+ | Xgpro | - | - | - |
| XGecu TL866-3G / T48 | Xgpro | - | - | - |

## VERA 

TODO: link to instructions for each solution in the matrix

Official community VERA bitstreams will be posted as releases at [X16Community/vera-module](https://github.com/X16Community/vera-module/releases)

| ↓ Hardware / OS → | Windows | Linux | Mac OS | Commander X16 |
|-|-|-|-|-|
| Commander X16 | - | - | - | flashvera |
| XGecu TL866II+ | Xgpro | minipro | minipro | - |
| XGecu TL866-3G / T48 | [Xgpro](X16%20Reference%20-%20Appendix%20B%20-%20VERA%20Recovery.md#appendix-b-vera-firmware-recovery) | - | - | - |

<!-- For PDF formatting -->
<div class="page-break"></div>

# Appendix A: Sound

## FM instrument patch presets
| # | Instrument Name | | # | Instrument Name |
|-|-|-|-|-|
| 0 | Acoustic Grand Piano | | 64 | Soprano Sax &#8224; |
| 1 | Bright Acoustic Piano | | 65 | Alto Sax &#8224; |
| 2 | Electric Grand Piano | | 66 | Tenor Sax &#8224; |
| 3 | Honky-tonk Piano | | 67 | Baritone Sax |
| 4 | Electric Piano 1 | | 68 | Oboe &#8224; |
| 5 | Electric Piano 2 | | 69 | English Horn &#8224; |
| 6 | Harpsichord | | 70 | Bassoon |
| 7 | Clavinet | | 71 | Clarinet &#8224; |
| 8 | Celesta | | 72 | Piccolo |
| 9 | Glockenspiel | | 73 | Flute &#8224; |
| 10 | Music Box | | 74 | Recorder |
| 11 | Vibraphone &#8224; | | 75 | Pan Flute |
| 12 | Marimba | | 76 | Blown Bottle |
| 13 | Xylophone | | 77 | Shakuhachi |
| 14 | Tubular Bells | | 78 | Whistle &#8224; |
| 15 | Dulcimer | | 79 | Ocarina |
| 16 | Drawbar Organ &#8224; | | 80 | Lead 1 (Square) &#8224; |
| 17 | Percussive Organ &#8224; | | 81 | Lead 2 (Sawtooth) &#8224; |
| 18 | Rock Organ &#8224; | | 82 | Lead 3 (Triangle) &#8224; |
| 19 | Church Organ | | 83 | Lead 4 (Chiff+Sine) &#8224; |
| 20 | Reed Organ | | 84 | Lead 5 (Charang) &#8224; |
| 21 | Accordion | | 85 | Lead 6 (Voice) &#8224; |
| 22 | Harmonica | | 86 | Lead 7 (Fifths) &#8224; |
| 23 | Bandoneon | | 87 | Lead 8 (Solo) &#8224; |
| 24 | Acoustic Guitar (Nylon) | | 88 | Pad 1 (Fantasia) &#8224; |
| 25 | Acoustic Guitar (Steel) | | 89 | Pad 2 (Warm) &#8224; |
| 26 | Electric Guitar (Jazz) | | 90 | Pad 3 (Polysynth) &#8224; |
| 27 | Electric Guitar (Clean) | | 91 | Pad 4 (Choir) &#8224; |
| 28 | Electric Guitar (Muted) | | 92 | Pad 5 (Bowed) |
| 29 | Electric Guitar (Overdriven) | | 93 | Pad 6 (Metallic) |
| 30 | Electric Guitar (Distortion) | | 94 | Pad 7 (Halo) &#8224; |
| 31 | Electric Guitar (Harmonics) | | 95 | Pad 8 (Sweep) &#8224; |
| 32 | Acoustic Bass | | 96 | FX 1 (Raindrop) |
| 33 | Electric Bass (finger) | | 97 | FX 2 (Soundtrack) &#8224; |
| 34 | Electric Bass (picked) | | 98 |FX 3 (Crystal) |
| 35 | Fretless Bass | | 99 | FX 4 (Atmosphere) &#8224; |
| 36 | Slap Bass 1 | | 100 | FX 5 (Brightness) &#8224; |
| 37 | Slap Bass 2 | | 101 | FX 6 (Goblin) |
| 38 | Synth Bass 1 | | 102 | FX 7 (Echo) |
| 39 | Synth Bass 2 | | 103 | FX 8 (Sci-Fi) &#8224; |
| 40 | Violin &#8224; | | 104 | Sitar |
| 41 | Viola &#8224; | | 105 | Banjo |
| 42 | Cello &#8224; | | 106 | Shamisen |
| 43 | Contrabass &#8224; | | 107 | Koto |
| 44 | Tremolo Strings &#8224; | | 108 | Kalimba |
| 45 | Pizzicato Strings | | 109 | Bagpipe |
| 46 | Orchestral Harp | | 110 | Fiddle &#8224; |
| 47 | Timpani | | 111 | Shanai &#8224; |
| 48 | String Ensemble 1 &#8224; | | 112 | Tinkle Bell |
| 49 | String Ensemble 2 &#8224; | | 113 | Agogo |
| 50 | Synth Strings 1 &#8224; | | 114 | Steel Drum |
| 51 | Synth Strings 2 &#8224; | | 115 | Woodblock |
| 52 | Choir Aahs &#8224; | | 116 | Taiko Drum |
| 53 | Voice Doos | | 117 | Melodic Tom |
| 54 | Synth Voice &#8224; | | 118 | Synth Drum |
| 55 | Orchestra Hit | | 119 | Reverse Cymbal |
| 56 | Trumpet &#8224; | | 120 | Fret Noise |
| 57 | Trombone | | 121 | Breath Noise |
| 58 | Tuba | | 122 | Seashore &#8224; |
| 59 | Muted Trumpet &#8224; | | 123 | Bird Tweet |
| 60 | French Horn | | 124 | Telephone Ring |
| 61 | Brass Section | | 125 | Helicopter |
| 62 | Synth Brass 1 | | 126 | Applause &#8224; |
| 63 | Synth Brass 2 | | 127 | Gunshot |

&#8224; Instrument is affected by the LFO, giving it a vibrato or tremolo effect.

## FM extended instrument patch presets
These presets exist mainly to support playback of drum sounds, and many of them only work correctly or sound musical at certain pitches or within a small range of pitches.

| # | Instrument Name | | # | Instrument Name |
|-|-|-|-|-|
| 128 | Silent | | 146 | Vibraslap | |
| 129 | Snare Roll | | 147 | Bongo | |
| 130 | Snap | | 148 | Maracas | |
| 131 | High Q | | 149 | Short Whistle |
| 132 | Scratch | | 150 | Long Whistle |
| 133 | Square Click | | 151 | Short Guiro |
| 134 | Kick | | 152 | Long Guiro |
| 135 | Rim | | 153 | Mute Cuica |
| 136 | Snare | | 154 | Open Cuica |
| 137 | Clap | | 155 | Mute Triangle |
| 138 | Tom | | 156 | Open Triangle |
| 139 | Closed Hi-Hat | | 157 | Jingle Bell |
| 140 | Pedal Hi-Hat | | 158 | Bell Tree |
| 141 | Open Hi-Hat | | 159 | Mute Surdo |
| 142 | Crash | | 160 | Pure Sine |
| 143 | Ride Cymbal | | 161 | Timbale |
| 144 | Splash Cymbal | | 162 | Open Surdo |
| 145 | Tambourine | |

## Drum presets
These are the percussion instrument mappings for the drum number argument of the `ym_playdrum` and `ym_setdrum` API calls, and the `FMDRUM` BASIC command.

| # | Instrument Name | | # | Instrument Name |
|-|-|-|-|-|
| | | | 56 | Cowbell |
| 25 | Snare Roll | | 57 | Crash Cymbal 2 |
| 26 | Finger Snap | | 58 | Vibraslap |
| 27 | High Q | | 59 | Ride Cymbal 2 |
| 28 | Slap | | 60 | High Bongo |
| 29 | Scratch Pull | | 61 | Low Bongo |
| 30 | Scratch Push | | 62 | Mute High Conga |
| 31 | Sticks | | 63 | Open High Conga |
| 32 | Square Click | | 64 | Low Conga |
| 33 | Metronome Bell | | 65 | High Timbale |
| 34 | Metronome Click | | 66 | Low Timbale |
| 35 | Acoustic Bass Drum | | 67 | High Agogo |
| 36 | Electric Bass Drum | | 68 | Low Agogo |
| 37 | Side Stick | | 69 | Cabasa |
| 38 | Acoustic Snare | | 70 | Maracas |
| 39 | Hand Clap | | 71 | Short Whistle |
| 40 | Electric Snare | | 72 | Long Whistle |
| 41 | Low Floor Tom | | 73 | Short Guiro |
| 42 | Closed Hi-Hat | | 74 | Long Guiro |
| 43 | High Floor Tom | | 75 | Claves |
| 44 | Pedal Hi-Hat | | 76 | High Woodblock |
| 45 | Low Tom | | 77 | Low Woodblock |
| 46 | Open Hi-Hat | | 78 | Mute Cuica |
| 47 | Low-Mid Tom | | 79 | Open Cuica |
| 48 | High-Mid Tom | | 80 | Mute Triangle |
| 49 | Crash Cymbal 1 | | 81 | Open Triangle |
| 50 | High Tom | | 82 | Shaker |
| 51 | Ride Cymbal 1 | | 83 | Jingle Bell |
| 52 | Chinese Cymbal | | 84 | Belltree |
| 53 | Ride Bell | | 85 | Castanets |
| 54 | Tambourine | | 86 | Mute Surdo |
| 55 | Splash Cymbal | | 87 | Open Surdo |

___

## BASIC FMPLAY and PSGPLAY string macros

### Overview

The play commands use a string of tokens to define sequences of notes to be played on a single voice of the corresponding sound chip. Tokens cause various effects to happen, such as triggering notes, changing the playback speed, etc. In order to
minimize the amount of text required to specify a sequence of sound, the player
maintains an internal state for most note parameters.

##### Stateful Player Behavior:

Playback parameters such as tempo, octave, volume, note duration, etc do not need to be specified for each note. These states are global between all voices of both the FM and PSG sound chips. The player maintains parameter state during and after playback. For instance, setting the octave to 5 in an `FMPLAY` command will result in subsequent `FMPLAY` and `PSGPLAY` statements beginning with the octave set to 5.

The player state is reset to default values whenever `FMINIT` or `PSGINIT` are used.

Parameter    |Default|Equivalent Token
-------------|-------|----------------
Tempo        | 120   | T120
Octave       | 4     | O4
Length       | 4     | L4
Note Spacing | 1     | S1


##### Using Tokens:
The valid tokens are: **`A-G,I,K,L,O,P,R,S,T,V,<,>`**.

Each token may be followed by optional modifiers such as numbers or symbols. Options to a token must be given in the order they are expected, and must have no spacing between them. Tokens may have spaces between them as desired. Any unknown
characters are ignored.

Example:
```BASIC
FMPLAY 0,"L4"      : REM DEFAULT LENGTH = QUARTER NOTE
FMPLAY 0,"A2. C+." : REM VALID
FMPLAY 0,"A.2 C.+" : REM INVALID
```
The valid command plays A as a dotted half, followed by C&#9839; as a dotted quarter.

The invalid example would play A as a dotted quarter (not half) because length must come before dots. Next, it would ignore the 2 as garbage. Then it would play natural C (not sharp) as a dotted quarter. Finally, it would ignore the + as garbage, because sharp/flat must precede length and dot.

### Token definitions:

### Musical notes
* Synopsis: Play a musical note, optionally setting the length.
* Syntax: `<A-G>[<+/->][<length>][.]`

Example:
```BASIC
FMPLAY 0,"A+2A4C.G-8."
```
On the YM2151 using channel 0, plays in the current octave an **A&#9839;** [half note<sup>?</sup>](# "minim") followed by an **A** [quarter note<sup>?</sup>](# "crotchet"), followed by **C** dotted quarter note, followed by **G&#9837;** dotted [eighth note<sup>?</sup>](# "quaver").

Lengths and dots after the note name or rest set the length just for the current note or rest.  To set the default length for subsequent notes and rests, use the `L` macro.


### Rests
* Synopsis: Wait for a period of silence equal to the length of a note, optionally setting the length.
* Syntax: `R[<length>][.]`

Example:
```BASIC
PSGPLAY 0,"CR2DRE"
```
On the VERA PSG using voice 0, plays in the current octave a **C** quarter note, followed by a half rest (silence), followed by a quarter **D**, followed by a quarter rest (silence), and finally a quarter **E**.

The numeral `2` in `R2` sets the length for the `R` itself but does not alter the
default note length (assumed as 4 - quarter notes in this example).

### Note Length
* Synopsis: Set the default length for notes and rests that follow
* Syntax: `L[<length>][.]`

Example values:
* L4 = quarter note (crotchet)
* L16 = sixteenth note (semiquaver)
* L12 = 8th note triplets (quaver triplet)
* L4. = dotted quarter note (1.5x the length)
* L4.. = double-dotted quarter note (1.75x the length)

Example program:
```BASIC
10 FMPLAY 0,"L4"
20 FOR I=1 TO 2
30 FMPLAY 0,"CDECL8"
40 NEXT
```
On the YM2151 using channel 0, this program, when RUN, plays in the current octave the sequence **C** **D** **E** **C** first as quarter notes, then as eighth notes the second time around.

### Articulation
* Synopsis: Set the spacing between notes, from legato to extreme staccato
* Syntax: `S<0-7>`

`S0` indicates legato. For FMPLAY, this also means that notes after the first in a phrase don't implicitly retrigger.

`S1` is the default value, which plays a note for 7/8 of the duration of the note, and releases the note for the remaining 1/8 of the note's duration.

You can think of `S` is, out of 8, how much space is put between the notes.

Example:
```BASIC
FMPLAY 0,"L4S1CDES0CDES4CDE"
```
On the YM2151 using channel 0, plays in the current octave the sequence **C** **D** **E** three times, first with normal articulation, next with legato (notes all run together and without retriggering), and finally with a moderate staccato.


### Explicit retrigger
* Synopsis: on the YM2151, when using `S0` legato, retrigger on the next note.
* Syntax: `K`

Example:
```BASIC
FMPLAY 0,"S0CDEKFGA"
```
On the YM2151 using channel 0, plays in the current octave the sequence **C** **D** **E** using legato, only triggering on the first note, then the sequence **F** **G** **A** the same way. The note **F** is triggered without needing to release the previous note early.


### Octave
* Synopsis: Explicitly set the octave number for notes that follow
* Syntax: `O<0-7>`

Example:
```BASIC
PSGPLAY 0,"O4AO2AO6CDE"
```
On the VERA PSG using voice 0, changes to octave 4 and plays **A** (440Hz), then switches to octave 2, and plays **A** (110Hz), then switches to octave 6 and plays the sequence **C** **D** **E**

### Octave Up
* Synopsis: Increases the octave by 1
* Syntax: `>`

If the octave would go above 7, this macro has no effect.

Example:
```BASIC
PSGPLAY 0,"O4AB>C+DE"
```
On the VERA PSG using voice 0, changes to octave 4 and plays the first five notes of the **A major** scale by switching to octave 5 starting at the **C&#9839;**

### Octave Down
* Synopsis: Decreases the octave by 1
* Syntax: `<`

If the octave would go below 0, this macro has no effect.
Example:
```BASIC
PSGPLAY 0,"O5GF+EDC<BAG"
```
On the VERA PSG using voice 0, changes to octave 5 and plays the **G major** scale from the top down by switching to octave 4 starting at the **B**

### Tempo
* Synopsis: Sets the BPM, the number of quarter notes per minute
* Syntax: `T<1-255>`

High tempo values and short notes tend to have inaccurate lengths due to quantization error. Delays within a string do keep track of fractional frames so the overall playback length should be relatively consistent.

Low tempo values that cause delays (lengths) to exceed 255 frames will also end up being inaccurate. For very long notes, it may be better to use legato to string several together.

Example:
```BASIC
10 FMPLAY 0,"T120C4CGGAAGR"
20 FMPLAY 0,"T180C4CGGAAGR"
```
On the YM2151 using channel 0, plays in the current octave the first 7 notes of *Twinkle Twinkle Little Star*, first at 120 beats per minute, then again 1.5 times as fast at 180 beats per minute.

### Volume
* Synopsis: Set the channel or voice volume
* Syntax: `V<0-63>`

This macro mirrors the `PSGVOL` and `FMVOL` BASIC commands for setting a channel or voice's volume. 0 is silent, 63 is maximum volume.

Example:
```BASIC
FMPLAY 0,"V40ECV45ECV50ECV55ECV60ECV63EC"
```
On the YM2151 using channel 0, starting at a moderate volume, plays the sequence **E** **C**, repeatedly, increasing the volume steadily each time.


### Panning
* Synopsis: Sets the stereo output of a channel or voice to left, right, or both.
* Syntax: `P<1-3>`

1 = Left  
2 = Right  
3 = Both  

Example:
```BASIC
10 FOR I=1 TO 4
20 PSGPLAY 0,"P1CP2B+"
30 NEXT I
40 PSGPLAY 0,"P3C"
```
On the VERA PSG using voice 0, in the current octave, repeatedly plays a **C** out of the left speaker, then a **B&#9839;** (effectively a **C** one octave higher) out of the right speaker.  After 4 such loops, it plays a **C** out of both speakers.

### Instrument change
* Synopsis: Sets the FM instrument (like FMINST) or PSG waveform (like PSGWAV)
* Syntax: `I<0-255>` (0-162 for FM)

Note: This macro is available starting in ROM version R43.

Example:
```BASIC
10 FMINIT
20 FMVIB 200,15
30 FMCHORD 0,"I11CI11EI11G"
```
This program sets up appropriate vibrato/tremolo and plays a C major chord with the vibraphone patch across FM channels 0, 1, and 2.

<!-- For PDF formatting -->
<div class="page-break"></div>

# Appendix B: VERA Firmware Recovery

**WARNING: This is a draft that may contain errors or omissions that could damage your hardware.**

## Using a Windows PC to upgrade or recover a VERA

**Target Component:** VERA  
**Programmer:** TL866-3G/T48  
**Software:** Xgpro  
**Host OS:** Windows  


### Before You Start

Before starting, it is recommended to disconnect the Commander X16's PSU's power from the wall socket.  You will need to reconnect power later, but while connecting the programmer to the system, it is safer to disconnect mains power from the power supply. Power is supplied to parts of the main board even when the computer is turned off.use_directory_urls
To perform the upgrade, you will need the following:
- A TL866-3G/T48 programmer
- The Xgpro software
- Female-to-female jumper wires


### Programmer Wiring Setup

The VERA 8-pin header should be connected as follows:

| VERA J2 Pin   | Connect to                       |
|---------------|----------------------------------|
| 1 (+5V)       | Not connected                    |
| 2 (CDONE)     | Not connected                    |
| 3 (CRESET_B)  | VERA, J7 GND pin                 |
| 4 (SPI_MISO)  | TL866-3G/T48, ICSP pin 5 (MISO)  |
| 5 (SPI_MOSI)  | TL866-3G/T48, ICSP pin 15 (MOSI) |
| 6 (SPI_SCK)   | TL866-3G/T48, ICSP pin 7 (SCK)   |
| 7 (SPI_SEL_N) | TL866-3G/T48, ICSP pin 1 (/CS)   |
| 8 (GND)       | TL866-3G/T48, ICSP pin 16 (GND)  |

Image 1: Vera J2 programming header and J7 header.<br>
<img src="images/vera-prg-hdr.jpg" width="400" />

Image 2: TL866-3G/T48 ICSP header.<br>
<img src="images/tl866-3g-icsp.jpg" width="400" />

Image 3: Schematics for connection between the VERA board and the TL866-3G/T48.<br>
<img src="images/tl866-3g-to-vera.png" width="400" />


### Powering the Target Component

The VERA board is programmed while it is still mounted in the Commander X16 and 
will be powered by the computer's PSU, not by the programmer.

Before proceeding with the firmware upgrade, ensure that the wiring is correct. 
Then, connect the Commander X16 to the wall socket and press the computer's power 
button to ensure that 5V is supplied to the VERA board.

Please note that the VERA's FPGA is held in reset because 
VERA pin 3 (CRESET_B) is connected to ground. As a result, 
you will not see any screen output during the upgrade process.


### Programmer Software Setup

Open the Xgpro software and configure the following settings:

- Select target chip: W25Q16JV
- Setup interface: 
    - Choose ICSP port
    - Uncheck ICSP_VCC_Enable (as VERA is powered by the X16)
- Click on "ID Check" to verify the connection
    - The response value should be EF 40 15
    - If it is not, double-check the wiring before proceeding
      
<img width="600" alt="xgpro-window" src="https://github.com/user-attachments/assets/cdaebea2-df90-4abe-8805-a2e42f936f87" />

### Update/Flash Procedure

In the Xgpro software, follow these steps:

- Click on "Load" to load the firmware into the software buffer
- After loading the firmware into the software buffer, click on "Prog." to upload the firmware to the VERA board.

Once the update is complete, press the power button to turn off the Commander X16. Then, disconnect the computer from the wall socket. Finally, remove all wires from the VERA pin header.

Congratulations! The firmware update for VERA is now complete.

<!-- For PDF formatting -->
<div class="page-break"></div>

# Appendix C: The 65C02 Processor

This is not meant to be a complete manual on the 65C02 processor, though is
meant to serve as a convenient quick reference. Much of this information comes
from 6502.org and pagetable.com. It is been placed here for convenience though
further information can be found at those (and other) sources.

## Overview

The WDC65C02 CPU is a modern version of the MOS6502 with a few additional
instructions and addressing modes and is capable of running at up to 14 MHz. On
the Commander X16, it is clocked at 8 MHz.

## A note about 65C816 Compatibility

The Commander X16 may be upgraded at some point to use the WDC 65C816 CPU.
The 65C816 is mostly compatible with the 65C02, except for 4 instructions
(`BBRx`, `BBSx`, `RMBx`, and `SMBx`).

These instructions *may* be deprecated in a future release of the emulator, and
so we suggest not using these instructions. Some people are already using the
65C816 in their X16 systems, and so using these instructions will cause your
programs to malfunction on these computers.

## Instruction Tables

## Instructions By Number

|    | x0          | x1          | x2          | x3 | x4          | x5          | x6          | x7            | x8          | x9          | xA          | xB          | xC          | xD          | xE          | xF            |
|----|-------------|-------------|-------------|----|-------------|-------------|-------------|---------------|-------------|-------------|-------------|-------------|-------------|-------------|-------------|---------------|
| 0x | [BRK](#brk) | [ORA](#ora) |             |    | [TSB](#tsb) | [ORA](#ora) | [ASL](#asl) | [RMB0](#rmbx) | [PHP](#pha) | [ORA](#ora) | [ASL](#asl) |             | [TSB](#tsb) | [ORA](#ora) | [ASL](#asl) | [BBR0](#bbrx) |
| 1x | [BPL](#bcc) | [ORA](#ora) | [ORA](#ora) |    | [TRB](#trb) | [ORA](#ora) | [ASL](#asl) | [RMB1](#rmbx) | [CLC](#clc) | [ORA](#ora) | [INC](#inc) |             | [TRB](#trb) | [ORA](#ora) | [ASL](#asl) | [BBR1](#bbrx) |
| 2x | [JSR](#jsr) | [AND](#and) |             |    | [BIT](#bit) | [AND](#and) | [ROL](#rol) | [RMB2](#rmbx) | [PLP](#pla) | [AND](#and) | [ROL](#rol) |             | [BIT](#bit) | [AND](#and) | [ROL](#rol) | [BBR2](#bbrx) |
| 3x | [BMI](#bcc) | [AND](#and) | [AND](#and) |    | [BIT](#bit) | [AND](#and) | [ROL](#rol) | [RMB3](#rmbx) | [SEC](#sec) | [AND](#and) | [DEC](#dec) |             | [BIT](#bit) | [AND](#and) | [ROL](#rol) | [BBR3](#bbrx) |
| 4x | [RTI](#rti) | [EOR](#eor) |             |    |             | [EOR](#eor) | [LSR](#lsr) | [RMB4](#rmbx) | [PHA](#pha) | [EOR](#eor) | [LSR](#lsr) |             | [JMP](#jmp) | [EOR](#eor) | [LSR](#lsr) | [BBR4](#bbrx) |
| 5x | [BVC](#bcc) | [EOR](#eor) | [EOR](#eor) |    |             | [EOR](#eor) | [LSR](#lsr) | [RMB5](#rmbx) | [CLI](#cli) | [EOR](#eor) | [PHY](#pha) |             |             | [EOR](#eor) | [LSR](#lsr) | [BBR5](#bbrx) |
| 6x | [RTS](#rts) | [ADC](#adc) |             |    | [STZ](#stz) | [ADC](#adc) | [ROR](#ror) | [RMB6](#rmbx) | [PLA](#pla) | [ADC](#adc) | [ROR](#ror) |             | [JMP](#jmp) | [ADC](#adc) | [ROR](#ror) | [BBR6](#bbrx) |
| 7x | [BVS](#bcc) | [ADC](#adc) | [ADC](#adc) |    | [STZ](#stz) | [ADC](#adc) | [ROR](#ror) | [RMB7](#rmbx) | [SEI](#sei) | [ADC](#adc) | [PLY](#pla) |             | [JMP](#jmp) | [ADC](#adc) | [ROR](#ror) | [BBR7](#bbrx) |
| 8x | [BRA](#bcc) | [STA](#sta) |             |    | [STY](#sty) | [STA](#sta) | [STX](#stx) | [SMB0](#smbx) | [DEY](#dec) | [BIT](#bit) | [TXA](#txx) |             | [STY](#sty) | [STA](#sta) | [STX](#stx) | [BBS0](#bbsx) |
| 9x | [BCC](#bcc) | [STA](#sta) | [STA](#sta) |    | [STY](#sty) | [STA](#sta) | [STX](#stx) | [SMB1](#smbx) | [TYA](#txx) | [STA](#sta) | [TXS](#txx) |             | [STZ](#stz) | [STA](#sta) | [STZ](#stz) | [BBS1](#bbsx) |
| Ax | [LDY](#ldy) | [LDA](#lda) | [LDX](#ldx) |    | [LDY](#ldy) | [LDA](#lda) | [LDX](#ldx) | [SMB2](#smbx) | [TAY](#txx) | [LDA](#lda) | [TAX](#txx) |             | [LDY](#ldy) | [LDA](#lda) | [LDX](#ldx) | [BBS2](#bbsx) |
| Bx | [BCS](#bcc) | [LDA](#lda) | [LDA](#lda) |    | [LDY](#ldy) | [LDA](#lda) | [LDX](#ldx) | [SMB3](#smbx) | [CLV](#clv) | [LDA](#lda) | [TSX](#txx) |             | [LDY](#ldy) | [LDA](#lda) | [LDX](#ldx) | [BBS3](#bbsx) |
| Cx | [CPY](#cpy) | [CMP](#cmp) |             |    | [CPY](#cpy) | [CMP](#cmp) | [DEC](#dec) | [SMB4](#smbx) | [INY](#inc) | [CMP](#cmp) | [DEX](#dec) | [WAI](#wai) | [CPY](#cpy) | [CMP](#cmp) | [DEC](#dec) | [BBS4](#bbsx) |
| Dx | [BNE](#bcc) | [CMP](#cmp) | [CMP](#cmp) |    |             | [CMP](#cmp) | [DEC](#dec) | [SMB5](#smbx) | [CLD](#cld) | [CMP](#cmp) | [PHX](#pha) | [STP](#stp) |             | [CMP](#cmp) | [DEC](#dec) | [BBS5](#bbsx) |
| Ex | [CPX](#cpx) | [SBC](#sbc) |             |    | [CPX](#cpx) | [SBC](#sbc) | [INC](#inc) | [SMB6](#smbx) | [INX](#inc) | [SBC](#sbc) | [NOP](#nop) |             | [CPX](#cpx) | [SBC](#sbc) | [INC](#inc) | [BBS6](#bbsx) |
| Fx | [BEQ](#bcc) | [SBC](#sbc) | [SBC](#sbc) |    |             | [SBC](#sbc) | [INC](#inc) | [SMB7](#smbx) | [SED](#sed) | [SBC](#sbc) | [PLX](#pla) |             |             | [SBC](#sbc) | [INC](#inc) | [BBS7](#bbsx) |

<!-- For PDF formatting -->
<div class="page-break"></div>

## Instructions By Name

|             |             |             |               |               |             |             |               |             |             |             |             |             |             |               |             |
|-------------|-------------|-------------|---------------|---------------|-------------|-------------|---------------|-------------|-------------|-------------|-------------|-------------|-------------|---------------|-------------|
| [ADC](#adc) | [AND](#and) | [ASL](#asl) | [BBRx](#bbrx) | [BBSx](#bbsx) | [BCC](#bcc) | [BCS](#bcc) | [BEQ](#bcc)   | [BIT](#bit) | [BMI](#bcc) | [BNE](#bcc) | [BPL](#bcc) | [BRA](#bcc) | [BRK](#brk) | [BVC](#bcc)   | [BVS](#bcc) |
| [CLC](#clc) | [CLD](#cld) | [CLI](#cli) | [CLV](#clv)   | [CMP](#cmp)   | [CPX](#cpx) | [CPY](#cpy) | [DEC](#dec)   | [DEX](#dec) | [DEY](#dec) | [EOR](#eor) | [INC](#inc) | [INX](#inc) | [INY](#inc) | [JMP](#jmp)   | [JSR](#jsr) |
| [LDA](#lda) | [LDX](#ldx) | [LDY](#ldy) | [LSR](#lsr)   | [NOP](#nop)   | [ORA](#ora) | [PHA](#pha) | [PHP](#pha)   | [PHX](#pha) | [PHY](#pha) | [PLA](#pla) | [PLP](#pla) | [PLX](#pla) | [PLY](#pla) | [RMBx](#rmbx) | [ROL](#rol) |
| [ROR](#ror) | [RTI](#rti) | [RTS](#rts) | [SBC](#sbc)   | [SEC](#sec)   | [SED](#sed) | [SEI](#sei) | [SMBx](#smbx) | [STA](#sta) | [STP](#stp) | [STX](#stx) | [STY](#sty) | [STZ](#stz) | [TAX](#txx) | [TAY](#txx)   | [TRB](#trb) |
| [TSB](#tsb) | [TSX](#txx) | [TXA](#txx) | [TXS](#txx)   | [TYA](#txx)   | [WAI](#wai) |             |               |             |             |             |             |             |             |               |             |

## Instructions By Category

|                     |               |               |             |             |             |             |             |             |             |
|---------------------|---------------|---------------|-------------|-------------|-------------|-------------|-------------|-------------|-------------|
| Arithmetic          | [ADC](#adc)   | [SBC](#sbc)   |             |             |             |             |             |             |             |
| Boolean             | [AND](#and)   | [EOR](#eor)   | [ORA](#ora) |             |             |             |             |             |             |
| Bit Shift           | [ASL](#asl)   | [LSR](#lsr)   | [ROL](#rol) | [ROR](#ror) |             |             |             |             |             |
| Branch              | [BBRx](#bbrx) | [BBSx](#bbsx) |             |             |             |             |             |             |             |
| Test Bit            | [BIT](#bit)   | [TRB](#trb)   | [TSB](#tsb) |             |             |             |             |             |             |
| Branching           | [BCC](#bcc)   | [BCS](#bcc)   | [BEQ](#bcc) | [BMI](#bcc) | [BNE](#bcc) | [BPL](#bcc) | [BVC](#bcc) | [BVS](#bcc) | [BRA](#bcc) |
| Misc                | [BRK](#brk)   | [NOP](#nop)   | [STP](#stp) | [WAI](#wai) |             |             |             |             |             |
| Flags               | [CLC](#clc)   | [CLD](#cld)   | [CLI](#cli) | [CLV](#clv) | [SEC](#sec) | [SED](#sed) | [SEI](#sei) |             |             |
| Compare             | [CMP](#cmp)   | [CPX](#cpx)   | [CPY](#cpy) |             |             |             |             |             |             |
| Increment/Decrement | [DEC](#dec)   | [DEX](#dec)   | [DEY](#dec) | [INX](#inc) | [INY](#inc) | [INC](#inc) |             |             |             |
| Flow                | [JMP](#jmp)   | [JSR](#jsr)   | [RTI](#rti) | [RTS](#rts) |             |             |             |             |             |
| Load Data           | [LDA](#lda)   | [LDX](#ldx)   | [LDY](#ldy) |             |             |             |             |             |             |
| Stack               | [PHA](#pha)   | [PHP](#pha)   | [PHX](#pha) | [PHY](#pha) | [PLA](#pla) | [PLP](#pla) | [PLX](#pla) | [PLY](#pla) |             |
| Bit Operations      | [RMBx](#rmbx) | [SMBx](#smbx) |             |             |             |             |             |             |             |
| Store Data          | [STA](#sta)   | [STX](#stx)   | [STY](#sty) | [STZ](#stz) |             |             |             |             |             |
| Transfer            | [TAX](#txx)   | [TXA](#txx)   | [TAY](#txx) | [TYA](#txx) | [TSX](#txx) | [TXS](#txx) |             |             |             |

<!-- For PDF formatting -->
<div class="page-break"></div>

### ADC

Add with Carry

```text
SYNTAX       MODE           HEX  LEN  CYCLES  FLAGS    
ADC #$20     Immediate      $69   2     2     NV----ZC 
ADC $20      Zero Page      $65   2     3     NV----ZC 
ADC $20,X    Zero Page,X    $75   2     4     NV----ZC 
ADC $8080    Absolute       $6D   3     4     NV----ZC 
ADC $8080,X  Absolute,X     $7D   3     4+    NV----ZC +p
ADC $8080,Y  Absolute,Y     $79   3     4+    NV----ZC +p
ADC ($20,X)  Indirect,X     $61   2     6     NV----ZC 
ADC ($20),Y  Indirect,Y     $71   2     5+    NV----ZC +p
ADC ($20)    ZP Indirect    $72   2     5     NV----ZC +c
```

Add a number to the Accumulator and stores the result in A.

Use the Carry (C) or Overflow (V) flags to determine whether the result was too
large for an 8 bit number.

If C is set before operation, then 1 will be added to the result.

C is set when result is more than 255 ($FF)  
Z is set when result is zero  
V is set when signed result is too large. (Goes below -128 or above 127).  
N is set when result is negative (bit 7=1)  

+p: Add 1 cycle if a page boundary is crossed when forming address.  
+c: New for the 65C02

---
[[Opcodes](#instructions-by-number)] | [[By Name](#instructions-by-name)] | [[By Category](#instructions-by-category)]

### AND

Logical And

```text
SYNTAX       MODE           HEX  LEN  CYCLES  FLAGS    
AND #$20     Immediate      $29   2     2     N-----Z- 
AND $20      Zero Page      $25   2     3     N-----Z- 
AND $20,X    Zero Page,X    $35   2     4     N-----Z- 
AND $8080    Absolute       $2D   3     4     N-----Z- 
AND $8080,X  Absolute,X     $3D   3     4+    N-----Z- +p
AND $8080,Y  Absolute,Y     $39   3     4+    N-----Z- +p
AND ($20,X)  Indirect,X     $21   2     6     N-----Z- 
AND ($20),Y  Indirect,Y     $31   2     5+    N-----Z- +p
AND ($20)    ZP Indirect    $32   2     5     N-----Z- +c
```

Bitwise AND the provided value with the Accumulator.

- Sets N (Negative) flag if the bit 7 of the result is 1, and otherwise
clears it.
- Sets Z (Zero) is the result is zero, and otherwise clears it  

`AND #$FF` will leave A unaffected (but still set the flags).  
`AND #$00` will clear A.  
`AND #$0F` will clear the high nibble of A, leaving a value of $00 to $0F
in A.  

| M | A | Result |
|---|---|--------|
| 0 | 0 | 0      |
| 0 | 1 | 0      |
| 1 | 0 | 0      |
| 1 | 1 | 1      |

**Other Boolean Instructions:**  
[EOR](#eor) exclusive-OR  
[ORA](#ora) bitwise OR  

+p: Add 1 cycle if a page boundary is crossed when forming address.  
+c: New for the 65C02

---
[[Opcodes](#instructions-by-number)] | [[By Name](#instructions-by-name)] | [[By Category](#instructions-by-category)]

### ASL

Arithmetic Shift Left

```text
SYNTAX       MODE           HEX  LEN  CYCLES  FLAGS    
ASL A        Accumulator    $0A   1     2     N-----ZC 
ASL $20      Zero Page      $06   2     5     N-----ZC
ASL $20,X    Zero Page,X    $16   2     6     N-----ZC
ASL $8080    Absolute       $0E   3     6     N-----ZC
ASL $8080,X  Absolute,X     $1E   3     6+    N-----ZC +p
```

Shifts all bits to the left by one position, moving 0 into the low bit.

0 is shifted into bit 0.  
Bit 7 is shifted to Carry.  

**Similar instructions:**  
[LSR](#lsr) is the opposite instruction and shifts to the right.  
[ROL](#rol) shifts left through Carry.

+p: Add 1 cycle if a page boundary is crossed when forming address.  

---
[[Opcodes](#instructions-by-number)] | [[By Name](#instructions-by-name)] | [[By Category](#instructions-by-category)]

### BBRx

Branch on Bit Reset

```text
SYNTAX       MODE           HEX  LEN  CYCLES  FLAGS    
BBR0 $20,$8080 ZP Relative    $0F   3     5     -------- +c -816
BBR1 $20,$8080 ZP Relative    $1F   3     5     -------- +c -816
BBR2 $20,$8080 ZP Relative    $2F   3     5     -------- +c -816
BBR3 $20,$8080 ZP Relative    $3F   3     5     -------- +c -816
BBR4 $20,$8080 ZP Relative    $4F   3     5     -------- +c -816
BBR5 $20,$8080 ZP Relative    $5F   3     5     -------- +c -816
BBR6 $20,$8080 ZP Relative    $6F   3     5     -------- +c -816
BBR7 $20,$8080 ZP Relative    $7F   3     5     -------- +c -816
```

Branch to LABEL if bit x of zero page address is 0 where x is the number of the
specific bit (0-7).

+c: New for the 65C02
-816: *Not available* on the 65C816  

#### BBR Example

```asm
  check_flag:
    BBR3 zeropage_flag, flag_not_set
  flag_set:
    NOP
    ...
  flag_not_set:
    NOP
    ...
```

The above BBR3 looks at value in zeropage_flag (here it's a label to an actual
zero page address) and if bit 3 of the value is *zero* the branch would be
taken to `@flag_not_set`.

---
[[Opcodes](#instructions-by-number)] | [[By Name](#instructions-by-name)] | [[By Category](#instructions-by-category)]

### BBSx

Branch on Bit Set

```text
SYNTAX       MODE           HEX  LEN  CYCLES  FLAGS    
BBS0 $20,$8080 ZP Relative    $8F   3     5     -------- +c -816
BBS1 $20,$8080 ZP Relative    $9F   3     5     -------- +c -816
BBS2 $20,$8080 ZP Relative    $AF   3     5     -------- +c -816
BBS3 $20,$8080 ZP Relative    $BF   3     5     -------- +c -816
BBS4 $20,$8080 ZP Relative    $CF   3     5     -------- +c -816
BBS5 $20,$8080 ZP Relative    $DF   3     5     -------- +c -816
BBS6 $20,$8080 ZP Relative    $EF   3     5     -------- +c -816
BBS7 $20,$8080 ZP Relative    $FF   3     5     -------- +c -816
```

Branch to LABEL if bit x of zero page address is 1 where x is the number
of the specific bit (0-7).

+c: New for the 65C02
-816: *Not available* on the 65C816  

#### BBS Example

```asm
check_flag:
    BBS3 zeropage_flag, flag_set
flag_not_set:
    NOP
    ...
flag_set:
    NOP
    ...
```

The above BBR3 looks at value in zeropage_flag (here it's a label to an actual
zero page address) and if bit 3 of the value is *zero* the branch would be
taken to `@flag_set`.

---
[[Opcodes](#instructions-by-number)] | [[By Name](#instructions-by-name)] | [[By Category](#instructions-by-category)]

### BIT

Test Bit

```text
SYNTAX       MODE           HEX  LEN  CYCLES  FLAGS    
BIT $20      Zero Page      $24   2     3     NV----Z- 
BIT $8080    Absolute       $2C   3     4     NV----Z- 
BIT #$20     Immediate      $89   2     2     ------Z- +c
BIT $20,X    Zero Page,X    $34   2     4     NV----Z- +c
BIT $8080,X  Absolute,X     $3C   3     4+    NV----Z- +c +p
```

- Sets Z (Zero) flag based on an AND of value provided to the Accumulator.
- Sets N (Negative) flag to the value of bit 7 at the provided address (NOTE: not with immediate).
- Sets V (Overflow) flag to the value of bit 6 at the provided address (NOTE: not with immediate).

+p: Add 1 cycle if a page boundary is crossed when forming address.  
+c: New for the 65C02  

---
[[Opcodes](#instructions-by-number)] | [[By Name](#instructions-by-name)] | [[By Category](#instructions-by-category)]

### B*cc*

Branch Instructions

```text
SYNTAX       MODE           HEX  LEN  CYCLES  FLAGS    
BCC $8080    Relative       $90   2    2/3+   -------- +p Carry Clear
BCS $8080    Relative       $B0   2    2/3+   -------- +p Carry Set
BEQ $8080    Relative       $F0   2    2/3+   -------- +p Equal: Zero bit set
BMI $8080    Relative       $30   2    2/3+   -------- +p Negative bit set
BNE $8080    Relative       $D0   2    2/3+   -------- +p Not Equal: Zero bit clear
BPL $8080    Relative       $10   2    2/3+   -------- +p Negative bit clear
BVC $8080    Relative       $50   2    2/3+   -------- +p oVerflow Clear
BVS $8080    Relative       $70   2    2/3+   -------- +p oVerflow Set
BRA $8080    Relative       $80   2    3/4+   -------- +p +c Always
```

The branch instructions take the branch when the related flag is Set (1) or
Clear (0).

When combined with CMP, this is the 6502's "IF THEN" construct.

```asm
LDA $1234  ; Reads the value of address $1234
CMP #$20   ; Compares it with the literal $20 (32)
BEQ Match  ; If they are equal, move to the label "Match".
```

The operand is a *relative* address, based on the Program Counter at the start
of the next opcode. As a result, you can only branch 127 bytes forward or 128
bytes back. However, most assemblers take a label or an address literal. So
the assembled value will be computed based on the PC and the entered value.

For example, if the PC is `$1000`, the statement `BCS $1023` will be `$B0 $21`.

`BCC` also functions as "branch less-than" (`<`) after a comparison (some
assemblers support a `BLT` macro/alias).
Similarly, `BCS` also functions as "branch greater-than-or-equal" (`>=`) after
a comparison (some assemblers support a `BGE` macro/alias).

+p: Execution takes one additional cycle when branching crosses a page boundary.
+c: New for the 65C02

---
[[Opcodes](#instructions-by-number)] | [[By Name](#instructions-by-name)] | [[By Category](#instructions-by-category)]

### BRK

Break: Software Interrupt

```text
SYNTAX       MODE           HEX  LEN  CYCLES  FLAGS    
BRK          Implied        $00   1     7     ---BD--- 
```

BRK is a software interrupt. With any interrupt several things happen:

1. The Program Counter is incremented by 2 bytes.
2. The new PC and flags are pushed onto the stack (pushed flags has B set on BRK).
3. The B flag is set (but only valid in stack memory flags interrupt pushed).
4. The D (Decimal) flag is cleared, forcing the CPU into binary mode.
5. The CPU reads the address from the IRQ vector at $FFFE and jumps there.

On the X16, BRK will jump out of the running program to the machine monitor.
You can then examine the state of the CPU registers and memory.

The B flag (as pushed on the stack) is used to distinguish a BRK from an NMI. An
interrupt triggered by asserting the NMI pin does not set the B flag, and so the X16
does a warm boot of BASIC, rather than jumping to MONitor.

---
[[Opcodes](#instructions-by-number)] | [[By Name](#instructions-by-name)] | [[By Category](#instructions-by-category)]

### CLC

Clear Carry

```text
SYNTAX       MODE           HEX  LEN  CYCLES  FLAGS    
CLC          Implied        $18   1     2     -------C 
```

Clears the Carry flag. This is useful before ADC to prevent an extra 1 during
addition. C is also often used in KERNAL routines to alter the operation of the
routine or return certain information.

---
[[Opcodes](#instructions-by-number)] | [[By Name](#instructions-by-name)] | [[By Category](#instructions-by-category)]

### CLD

Clear Decimal Flag

```text
SYNTAX       MODE           HEX  LEN  CYCLES  FLAGS    
CLD          Implied        $D8   1     2     ----D--- 
```

Clears the Decimal flag. This switches the CPU back to binary operation if it
was previously in BCD mode.

---
[[Opcodes](#instructions-by-number)] | [[By Name](#instructions-by-name)] | [[By Category](#instructions-by-category)]

### CLI

Clear Interrupt Disable

```text
SYNTAX       MODE           HEX  LEN  CYCLES  FLAGS    
CLI          Implied        $58   1     2     -----I-- 
```

Clear Interrupt disable. This allows IRQ interrupts to proceed normally. NMI
and RST are always enabled.

Use SEI to disable interrupts

---
[[Opcodes](#instructions-by-number)] | [[By Name](#instructions-by-name)] | [[By Category](#instructions-by-category)]

### CLV

Clear oVerflow

```text
SYNTAX       MODE           HEX  LEN  CYCLES  FLAGS    
CLV          Implied        $B8   1     2     -V------ 
```

Clear the Overflow (V) flag after an arithmetic operation, such as ADC or SBC.

---
[[Opcodes](#instructions-by-number)] | [[By Name](#instructions-by-name)] | [[By Category](#instructions-by-category)]

### CMP

Compare A to memory

```text
SYNTAX       MODE           HEX  LEN  CYCLES  FLAGS    
CMP #$20     Immediate      $C9   2     2     N-----ZC 
CMP $20      Zero Page      $C5   2     3     N-----ZC 
CMP $20,X    Zero Page,X    $D5   2     4     N-----ZC 
CMP $8080    Absolute       $CD   3     4     N-----ZC 
CMP $8080,X  Absolute,X     $DD   3     4+    N-----ZC +p
CMP $8080,Y  Absolute,Y     $D9   3     4+    N-----ZC +p
CMP ($20,X)  Indirect,X     $C1   2     6     N-----ZC 
CMP ($20),Y  Indirect,Y     $D1   2     5+    N-----ZC +p
CMP ($20)    ZP Indirect    $D2   2     5     N-----ZC +c
```

Compares the value in the Accumulator (A) with the given value. It sets flags
based on subtracting A - *Value*.

- Sets C (Carry) flag if the value in A is >= given value
- Clears C (Carry) flag if the value in A is < given value
- Sets Z (Zero) flag if the values are equal
- Clears Z (Zero) flag if the values are not equal
- Sets N (Negative) flag if value in A is < given value

+p: Add 1 cycle if a page boundary is crossed when forming address.  
+c: New for the 65C02  

---
[[Opcodes](#instructions-by-number)] | [[By Name](#instructions-by-name)] | [[By Category](#instructions-by-category)]

### CPX

Compare X to memory

```text
SYNTAX       MODE           HEX  LEN  CYCLES  FLAGS    
CPX #$20     Immediate      $E0   2     2     N-----ZC 
CPX $20      Zero Page      $E4   2     3     N-----ZC 
CPX $8080    Absolute       $EC   3     4     N-----ZC 
```

Compares the value in the X register with the given value. It sets flags
based on subtracting X - *Value*.

- Sets C (Carry) flag if the value in X is >= given value
- Clears C (Carry) flag if the value in X is < given value
- Sets Z (Zero) flag if the values are equal
- Clears Z (Zero) flag if the values are not equal
- Sets N (Negative) flag if value in X is < given value

---
[[Opcodes](#instructions-by-number)] | [[By Name](#instructions-by-name)] | [[By Category](#instructions-by-category)]

### CPY

Compare Y to memory

```text
SYNTAX       MODE           HEX  LEN  CYCLES  FLAGS    
CPY #$20     Immediate      $C0   2     2     N-----ZC 
CPY $20      Zero Page      $C4   2     3     N-----ZC 
CPY $8080    Absolute       $CC   3     4     N-----ZC 
```

Compares the value in the Y register with the given value. It sets flags
based on subtracting Y - *Value*.

- Sets C (Carry) flag if the value in Y is >= given value
- Clears C (Carry) flag if the value in Y is < given value
- Sets Z (Zero) flag if the values are equal
- Clears Z (Zero) flag if the values are not equal
- Sets N (Negative) flag if value in Y is < given value

---
[[Opcodes](#instructions-by-number)] | [[By Name](#instructions-by-name)] | [[By Category](#instructions-by-category)]

### DEC

Decrement Value

```text
SYNTAX       MODE           HEX  LEN  CYCLES  FLAGS    
DEC A        Accumulator    $3A   1     2     N-----Z- +c
DEC $20      Zero Page      $C6   2     5     N-----Z- 
DEC $20,X    Zero Page,X    $D6   2     6     N-----Z- 
DEC $8080    Absolute       $CE   3     6     N-----Z- 
DEC $8080,X  Absolute,X     $DE   3     7     N-----Z- 
DEX          Implied        $CA   1     2     N-----Z- 
DEY          Implied        $88   1     2     N-----Z- 
```

Decrement value by one: this subtracts 1 from memory or the designated register,
leaving the new value in its place.

`DEC` with an operand operates on memory.

`DEX` operates on the X register  
`DEY` operates on the Y register  
`DEC A` or `DEC` operates on the Accumulator.

- Sets N (Negative) flag if the two's compliment value is negative
- Sets Z (Zero) flag is the value is zero

+c: New for the 65C02  

#### 16-bit DEC Example

You can perform a 16-bit DEC by chaining two DECs together, testing the low
byte before decrementing the high byte:

```asm
;16 bit decrement
      LDA Num_Low
      BNE skip
      DEC Num_High
skip: DEC Num_Low
```

---
[[Opcodes](#instructions-by-number)] | [[By Name](#instructions-by-name)] | [[By Category](#instructions-by-category)]

### EOR

Exclusive OR

```text
SYNTAX       MODE           HEX  LEN  CYCLES  FLAGS    
EOR #$20     Immediate      $49   2     2     N-----Z- 
EOR $20      Zero Page      $45   2     3     N-----Z- 
EOR $20,X    Zero Page,X    $55   2     4     N-----Z- 
EOR $8080    Absolute       $4D   3     4     N-----Z- 
EOR $8080,X  Absolute,X     $5D   3     4+    N-----Z- +p
EOR $8080,Y  Absolute,Y     $59   3     4+    N-----Z- +p
EOR ($20,X)  Indirect,X     $41   2     6     N-----Z- 
EOR ($20),Y  Indirect,Y     $51   2     5+    N-----Z- +p
EOR ($20)    ZP Indirect    $52   2     5     N-----Z- +c
```

Perform an exclusive OR of the given value in A
(the accumulator), storing the result in A.

The exclusive OR version of [ORA](#ora).

- Sets N (Negative) flag if the two's compliment value is negative
- Sets Z (Zero) flag is the value is zero

Exclusive OR returns a 1 bit for each bit that is different in the values
tested. It returns a 0 for each bit that is the same.

`EOR #$00` has no effect on A, but still sets the Z and N flags.  
`EOR #$FF` inverts the bits in A.  

| M | A | Result |
|---|---|--------|
| 0 | 0 | 0      |
| 0 | 1 | 1      |
| 1 | 0 | 1      |
| 1 | 1 | 0      |

**Other Boolean Instructions:**  
[ORA](#ora) bitwise OR  
[AND](#and) bitwise AND  

+p: Add 1 cycle if a page boundary is crossed when forming address.  
+c: New for the 65C02  

---
[[Opcodes](#instructions-by-number)] | [[By Name](#instructions-by-name)] | [[By Category](#instructions-by-category)]

### INC

Increment Value

```text
SYNTAX       MODE           HEX  LEN  CYCLES  FLAGS    
INC A        Accumulator    $1A   1     2     N-----Z- +c
INC $20      Zero Page      $E6   2     5     N-----Z- 
INC $20,X    Zero Page,X    $F6   2     6     N-----Z- 
INC $8080    Absolute       $EE   3     6     N-----Z- 
INC $8080,X  Absolute,X     $FE   3     6/7   N-----Z- 
INX          Implied        $E8   1     2     N-----Z- 
INY          Implied        $C8   1     2     N-----Z- 
```

Increment by one: this adds 1 to memory or the designated register, leaving the
new value in its place.

- Sets N (Negative) flag if the two's compliment value is negative
- Sets Z (Zero) flag is the value is zero

`INC oper` operates on memory.  
`INX` operates on the X register.  
`INY` operates on the Y register.  
`INC A` or `INC` with no operand operates on the Accumulator.  

+c: New for the 65C02  

#### 16-bit INC Example

You can perform a 16-bit INC by chaining two INCs together, testing the low
byte after incrementing it.

```asm
;16 bit increment
        INC Addr_Low
        BNE skip
        INC Addr_High
skip:   ...
```

---
[[Opcodes](#instructions-by-number)] | [[By Name](#instructions-by-name)] | [[By Category](#instructions-by-category)]

### JMP

Jump to new address

```text
SYNTAX       MODE           HEX  LEN  CYCLES  FLAGS    
JMP $8080    Absolute       $4C   3     3     -------- 
JMP ($8080)  Indirect       $6C   3     5     -------- 
JMP $8080,X  Absolute,X     $7C   3     6     -------- +c
```

Jump to specified memory location and begin execution from this point.

Note for indirect jumps: The CPU does not correctly retrieve the second byte
of the pointer from the next page, so you should never use a pointer address
on the last byte of a page. ie: $12FF. *[Issue is fixed on 65C02]*

+c: New for the 65C02  

#### (Absolute,X) and Jump Tables

(Absolute,X) is an additional mode for the 65C02 and is commonly used for
implementing jump tables.

So we might have something like:

```asm
important_jump_table:
  .word routine1
  .word routine2
...

LDX #$02     ; table index * 2
JMP (important_jump_table,x)
```

The above would jump to the address of `routine2`, and is much faster than
the old 6502 method of pushing the two bytes onto the stack and performing
an RTS.

---
[[Opcodes](#instructions-by-number)] | [[By Name](#instructions-by-name)] | [[By Category](#instructions-by-category)]

### JSR

Jump to Subroutine

```text
SYNTAX       MODE           HEX  LEN  CYCLES  FLAGS    
JSR $8080    Absolute       $20   3     6     -------- 
```

Stores the address of the Program Counter to the stack.  
Jump to specified memory location and begin execution from this point.  

This is used to run subroutines in user programs, as well as running KERNAL
routines. RTS is used at the end of the routine to return to the instruction
immediately after the JSR.

Be careful to always match JSR and RTS, as imbalanced JSR/RTS operations will
either overflow or underflow the stack.

---
[[Opcodes](#instructions-by-number)] | [[By Name](#instructions-by-name)] | [[By Category](#instructions-by-category)]

### LDA

Read memory to Accumulator

```text
SYNTAX       MODE           HEX  LEN  CYCLES  FLAGS    
LDA #$20     Immediate      $A9   2     2     N-----Z- 
LDA $20      Zero Page      $A5   2     3     N-----Z- 
LDA $20,X    Zero Page,X    $B5   2     4     N-----Z- 
LDA $8080    Absolute       $AD   3     4     N-----Z- 
LDA $8080,X  Absolute,X     $BD   3     4+    N-----Z- +p
LDA $8080,Y  Absolute,Y     $B9   3     4+    N-----Z- +p
LDA ($20,X)  Indirect,X     $A1   2     6     N-----Z- 
LDA ($20),Y  Indirect,Y     $B1   2     5+    N-----Z- +p
LDA ($20)    ZP Indirect    $B2   2     5     N-----Z- +c
```

Place the given value from memory into the accumulator (A).

- Sets N (Negative) flag if the two's compliment value is negative
- Sets Z (Zero) flag is the value is zero

+p: Add 1 cycle if a page boundary is crossed when forming address.  
+c: New for the 65C02  

---
[[Opcodes](#instructions-by-number)] | [[By Name](#instructions-by-name)] | [[By Category](#instructions-by-category)]

### LDX

Read memory to X Index Register

```text
SYNTAX       MODE           HEX  LEN  CYCLES  FLAGS    
LDX #$20     Immediate      $A2   2     2     N-----Z- 
LDX $20      Zero Page      $A6   2     3     N-----Z- 
LDX $20,Y    Zero Page,Y    $B6   2     4     N-----Z- 
LDX $8080    Absolute       $AE   3     4     N-----Z- 
LDX $8080,Y  Absolute,Y     $BE   3     4+    N-----Z- +p
```

Place the given value from memory into the X register.

- Sets N (Negative) flag if the two's compliment value is negative
- Sets Z (Zero) flag is the value is zero

+p: Add 1 cycle if a page boundary is crossed when forming address.  

---
[[Opcodes](#instructions-by-number)] | [[By Name](#instructions-by-name)] | [[By Category](#instructions-by-category)]

### LDY

Read memory to Y Index Register

```text
SYNTAX       MODE           HEX  LEN  CYCLES  FLAGS    
LDY #$20     Immediate      $A0   2     2     N-----Z- 
LDY $20      Zero Page      $A4   2     3     N-----Z- 
LDY $20,X    Zero Page,X    $B4   2     4     N-----Z- 
LDY $8080    Absolute       $AC   3     4     N-----Z- 
LDY $8080,X  Absolute,X     $BC   3     4+    N-----Z- +p
```

Place the given value from memory into the Y register.

- Sets N (Negative) flag if the two's compliment value is negative
- Sets Z (Zero) flag is the value is zero

+p: Add 1 cycle if a page boundary is crossed when forming address.  

---
[[Opcodes](#instructions-by-number)] | [[By Name](#instructions-by-name)] | [[By Category](#instructions-by-category)]

### LSR

Logical Shift Right

```text
SYNTAX       MODE           HEX  LEN  CYCLES  FLAGS    
LSR A        Accumulator    $4A   1     2     N-----Z- 
LSR $20      Zero Page      $46   2     5     N-----Z- 
LSR $20,X    Zero Page,X    $56   2     6     N-----Z- 
LSR $8080    Absolute       $4E   3     6     N-----Z- 
LSR $8080,X  Absolute,X     $5E   3    6/7    N-----Z-
```

Shifts all bits to the right by one position.

Bit 0 is shifted into Carry.  
0 shifted into bit 7.  

**Similar instructions:**  
[ASL](#asl) is the opposite instruction, shifting to the left.  
[ROR](#ror) rotates bit 0 through Carry to bit 7.  

---
[[Opcodes](#instructions-by-number)] | [[By Name](#instructions-by-name)] | [[By Category](#instructions-by-category)]

### NOP

No Operation

```text
SYNTAX       MODE           HEX  LEN  CYCLES  FLAGS    
NOP          Implied        $EA   1     2     -------- 
```

NOP simply does nothing for 2 clock cycles. No registers are affected, and no
memory reads or writes occur. This can be used to delay the clock by 2 ticks.

It's also a useful way to blank out unwanted instructions in memory or in
a machine language program on disk. By changing the byte values of the opcode
and operands to $EA, you can effectively cancel out an instruction.

It is also useful for adding small delays to your code. For instance, to add a
bit of delay when writing to the YM2151 chip (see [Chapter 11 - YM Write Procedure](X16%20Reference%20-%2011%20-%20Sound%20Programming.md#vera-psg-and-pcm-programming)).

---
[[Opcodes](#instructions-by-number)] | [[By Name](#instructions-by-name)] | [[By Category](#instructions-by-category)]

### ORA

Logical OR

```text
SYNTAX       MODE           HEX  LEN  CYCLES  FLAGS    
ORA #$20     Immediate      $09   2     2     N-----Z- 
ORA $20      Zero Page      $05   2     3     N-----Z- 
ORA $20,X    Zero Page,X    $15   2     4     N-----Z- 
ORA $8080    Absolute       $0D   3     4     N-----Z- 
ORA $8080,X  Absolute,X     $1D   3     4+    N-----Z- +p
ORA $8080,Y  Absolute,Y     $19   3     4+    N-----Z- +p
ORA ($20,X)  Indirect,X     $01   2     6     N-----Z- 
ORA ($20),Y  Indirect,Y     $11   2     5+    N-----Z- +p
ORA ($20)    ZP Indirect    $12   2     5     N-----Z- +c
```

Perform a logical OR of the given value in A
(the Accumulator), storing the result in A.

- Sets N (Negative) flag if the two's compliment value is negative
- Sets Z (Zero) flag is the value is zero

`OR #$00` has no effect on A, but still sets the Z and N flags.  
`OR #$FF` results in $FF.

| M | A | Result |
|---|---|--------|
| 0 | 0 | 0      |
| 0 | 1 | 1      |
| 1 | 0 | 1      |
| 1 | 1 | 1      |

**Other Boolean Instructions:**  
[EOR](#eor) exclusive-OR  
[AND](#and) bitwise AND  

+p: Add 1 cycle if a page boundary is crossed when forming address.  
+c: New for the 65C02  

---
[[Opcodes](#instructions-by-number)] | [[By Name](#instructions-by-name)] | [[By Category](#instructions-by-category)]

### PHA

Push to stack

```text
SYNTAX       MODE           HEX  LEN  CYCLES  FLAGS    
PHA          Implied        $48   1     3     -------- 
PHP          Implied        $08   1     3     -------- 
PHX          Implied        $DA   1     3     -------- +c
PHY          Implied        $5A   1     3     -------- +c
```

Pushes a register to the stack.

This instruction copies the value in the affected register to the address
of the stack pointer, then moves the stack pointer downward by one byte.

Be careful to match Push and Pull operations so that you don't accidentally
overflow or underflow the stack.

PHP pushes the Flags, also called P for Program Status Register.

The corresponding "Pull" instructions are [PLA](#pla), [PHP](#pla), [PHX](#pla),
and [PHY](#pla).

+c: New for the 65C02  

---
[[Opcodes](#instructions-by-number)] | [[By Name](#instructions-by-name)] | [[By Category](#instructions-by-category)]

### PLA

Pull from stack

```text
SYNTAX       MODE           HEX  LEN  CYCLES  FLAGS    
PLA          Implied        $68   1     4     N-----Z- 
PLP          Implied        $28   1     4     NV--DIZC 
PLX          Implied        $FA   1     4     N-----Z- +c
PLY          Implied        $7A   1     4     N-----Z- +c
```

Pulls a value from the stack into a register.

This instruction moves the stack pointer up by one byte, then copies the value
from the address of the stack pointer to the affected register.

Be careful to match Push and Pull operations so that you don't accidentally
overflow or underflow the stack.

PLP pulls the Flags, also called P for Program Status Register.

Use TXS or TSX to directly manage the stack pointer.

The corresponding "Push" instructions are [PHA](#pha), [PHP](#pha), [PHX](#pha),
and [PHY](#pha).

+c: New for the 65C02  

---
[[Opcodes](#instructions-by-number)] | [[By Name](#instructions-by-name)] | [[By Category](#instructions-by-category)]

### RMBx

Memory Bit Operations

```text
SYNTAX       MODE           HEX  LEN  CYCLES  FLAGS    
RMB0 $20     Zero Page      $07   2     5     -------- +c -816
RMB1 $20     Zero Page      $17   2     5     -------- +c -816
RMB2 $20     Zero Page      $27   2     5     -------- +c -816
RMB3 $20     Zero Page      $37   2     5     -------- +c -816
RMB4 $20     Zero Page      $47   2     5     -------- +c -816
RMB5 $20     Zero Page      $57   2     5     -------- +c -816
RMB6 $20     Zero Page      $67   2     5     -------- +c -816
RMB7 $20     Zero Page      $77   2     5     -------- +c -816
```

Set bit x to 0 at the given zero page address where x is the number of the
specified bit (0-7).

Often used in conjunction with [BBR](#bbrx) and [BBS](#bbsx).

+c: New for the 65C02
-816: *Not available* on the 65C816  

---
[[Opcodes](#instructions-by-number)] | [[By Name](#instructions-by-name)] | [[By Category](#instructions-by-category)]

### ROL

Rotate Left

```text
SYNTAX       MODE           HEX  LEN  CYCLES  FLAGS    
ROL A        Accumulator    $2A   1     2     N-----ZC 
ROL $20      Zero Page      $26   2     5     N-----ZC 
ROL $20,X    Zero Page,X    $36   2     6     N-----ZC 
ROL $8080    Absolute       $2E   3     6     N-----ZC 
ROL $8080,X  Absolute,X     $3E   3    6/7    N-----ZC +p
```

Rotate all bits to the left one position. The value in the carry (C) flag is
shifted into bit 0 and the original bit 7 is shifted into the carry (C).

[ASL](#asl) shifts left, moving 0 into bit 0  
[ROR](#ror) rotates to the right.

+p: Add 1 cycle if a page boundary is crossed when forming address.  

---
[[Opcodes](#instructions-by-number)] | [[By Name](#instructions-by-name)] | [[By Category](#instructions-by-category)]

### ROR

Rotate Right

```text
SYNTAX       MODE           HEX  LEN  CYCLES  FLAGS    
ROR A        Accumulator    $6A   1     2     N-----ZC 
ROR $20      Zero Page      $66   2     5     N-----ZC 
ROR $20,X    Zero Page,X    $76   2     6     N-----ZC 
ROR $8080    Absolute       $7E   3     6     N-----ZC 
ROR $8080,X  Absolute,X     $6E   3    6/7    N-----ZC +p
```

Rotate all bits to the right one position. The value in
the carry (C) flag is shifted into bit 7 and the original
bit 0 is shifted into the carry (C).

[LSR](#lsr) shifts right, placing 0 into bit 7.  
[ROL](#rol) rotates to the left.  

+p: Add 1 cycle if a page boundary is crossed when forming address.  

---
[[Opcodes](#instructions-by-number)] | [[By Name](#instructions-by-name)] | [[By Category](#instructions-by-category)]

### RTI

Return from Interrupt

```text
SYNTAX       MODE           HEX  LEN  CYCLES  FLAGS    
RTI          Implied        $40   1     6     -------- 
```

Return from an interrupt by popping three values off the stack.
The first is for the status register (P) followed by the two bytes of the
program counter.

Note that unlike [RTS](#rts), the popped address is the actual
return address (rather than address-1).

---
[[Opcodes](#instructions-by-number)] | [[By Name](#instructions-by-name)] | [[By Category](#instructions-by-category)]

### RTS

Return from Subroutine

```text
SYNTAX       MODE           HEX  LEN  CYCLES  FLAGS    
RTS          Implied        $60   1     6     -------- 
```

Typically used at the end of a subroutine. It jumps
back to the address after the [JSR](#jsr) that called it
by popping the top 2 bytes off the stack and transferring
control to that address +1.

---
[[Opcodes](#instructions-by-number)] | [[By Name](#instructions-by-name)] | [[By Category](#instructions-by-category)]

### SBC

Subtract With Carry

```text
SYNTAX       MODE           HEX  LEN  CYCLES  FLAGS    
SBC #$20     Immediate      $E9   2     2     NV----ZC 
SBC $20      Zero Page      $E5   2     3     NV----ZC 
SBC $20,X    Zero Page,X    $F5   2     4     NV----ZC 
SBC $8080    Absolute       $ED   3     4     NV----ZC 
SBC $8080,X  Absolute,X     $FD   3     4+    NV----ZC +p
SBC $8080,Y  Absolute,Y     $F9   3     4+    NV----ZC +p
SBC ($20,X)  Indirect,X     $E1   2     6     NV----ZC 
SBC ($20),Y  Indirect,Y     $F1   2     5+    NV----ZC +p
SBC ($20)    ZP Indirect    $F2   2     5     NV----ZC +c
```

Subtract the operand from A and places the result in A.

When Carry is 0, an additional 1 is subtracted.

There is no "Subtract without carry". To do that, use SEC first to set the Carry
flag.

If D=1, subtraction is Binary Coded Decimal. If D=0 then subtraction is binary.

C is clear when result is less than 0. (ie: Borrow took place)  
Z is set when result is zero  
V is set when signed result goes below -128 or above 127.  
N is set when result is negative (bit 7=1)  

+p: Add 1 cycle if a page boundary is crossed when forming address.  
+c: New for the 65C02

---
[[Opcodes](#instructions-by-number)] | [[By Name](#instructions-by-name)] | [[By Category](#instructions-by-category)]

### SEC

Set Carry

```text
SYNTAX       MODE           HEX  LEN  CYCLES  FLAGS    
SEC          Implied        $38   1     2     -------C 
```

Sets the Carry flag. This is used before SBC to prevent an extra subtract. C
is also often used in KERNAL routines to alter the operation of the routine
or return certain information.

---
[[Opcodes](#instructions-by-number)] | [[By Name](#instructions-by-name)] | [[By Category](#instructions-by-category)]

### SED

Set Decimal

```text
SYNTAX       MODE           HEX  LEN  CYCLES  FLAGS    
SED          Implied        $F8   1     2     ----D--- 
```

Sets the Decimal flag. This will put the CPU in BCD mode, which affects the
behavior of ADC and SBC.

In binary mode, adding 1 to $09 will set the Accumulator to $0F.  
In BCD mode, adding 1 to $09 will set the Accumulator to $10.  

Using BCD allows for easier conversion of binary numbers to decimal. BCD also
allows for storing decimal numbers without loss of precision due to power-of-2
rounding.

---
[[Opcodes](#instructions-by-number)] | [[By Name](#instructions-by-name)] | [[By Category](#instructions-by-category)]

### SEI

Set Interrupt Disable

```text
SYNTAX       MODE           HEX  LEN  CYCLES  FLAGS    
SEI          Implied        $78   1     2     -----I-- 
```

Sets or clears the Interrupt Disable flag. When I is set, the CPU will not
execute IRQ interrupts, even if the line is asserted. Use CLI to re-enable
interrupts.

---
[[Opcodes](#instructions-by-number)] | [[By Name](#instructions-by-name)] | [[By Category](#instructions-by-category)]

### SMBx

Set Memory Bit

```text
SYNTAX       MODE           HEX  LEN  CYCLES  FLAGS    
SMB0 $20     Zero Page      $87   2     5     -------- +c -816
SMB1 $20     Zero Page      $97   2     5     -------- +c -816
SMB2 $20     Zero Page      $A7   2     5     -------- +c -816
SMB3 $20     Zero Page      $B7   2     5     -------- +c -816
SMB4 $20     Zero Page      $C7   2     5     -------- +c -816
SMB5 $20     Zero Page      $D7   2     5     -------- +c -816
SMB6 $20     Zero Page      $E7   2     5     -------- +c -816
SMB7 $20     Zero Page      $F7   2     5     -------- +c -816
```

Set bit x to 1 at the given zero page address where x is the number
of the specific bit (0-7).

Often used in conjunction with [BBR](#bbrx) and [BBS](#bbsx).

Specific to the 65C02 (*unavailable on the 65C816*)

+c: New for the 65C02
-816: *Not available* on the 65C816  

---
[[Opcodes](#instructions-by-number)] | [[By Name](#instructions-by-name)] | [[By Category](#instructions-by-category)]

### STA

Store Accumulator contents to memory

```text
SYNTAX       MODE           HEX  LEN  CYCLES  FLAGS    
STA $20      Zero Page      $85   2     3     -------- 
STA $20,X    Zero Page,X    $95   2     4     -------- 
STA $8080    Absolute       $8D   3     4     -------- 
STA $8080,X  Absolute,X     $9D   3     5+    -------- +p
STA $8080,Y  Absolute,Y     $99   3     5+    -------- +p
STA ($20,X)  Indirect,X     $81   2     6     -------- 
STA ($20),Y  Indirect,Y     $91   2     6+    -------- +p
STA ($20)    ZP Indirect    $92   2     5     -------- +c
```

Place the given value from the accumulator (A) into memory.

+p: Add 1 cycle if a page boundary is crossed when forming address.  
+c: New for the 65C02

---
[[Opcodes](#instructions-by-number)] | [[By Name](#instructions-by-name)] | [[By Category](#instructions-by-category)]

### STP

Stop

```text
SYNTAX       MODE           HEX  LEN  CYCLES  FLAGS    
STP          Implied        $DB   1     3     -------- +c
```

Stops (or halts) the processor and places it in a lower power state until a
hardware reset occurs. For the X16 emulator, when the debugger is enabled
using the `-debug` command-line parameter, the STP instruction will break into
the debugger automatically.

If debugging is not enabled, the emulator will prompt the user to close the
emulator or reset the emulation.

+c: New for the 65C02

---
[[Opcodes](#instructions-by-number)] | [[By Name](#instructions-by-name)] | [[By Category](#instructions-by-category)]

### STX

Save X Index Register contents to memory

```text
SYNTAX       MODE           HEX  LEN  CYCLES  FLAGS    
STX $20      Zero Page      $86   2     3     -------- 
STX $20,Y    Zero Page,Y    $96   2     4     -------- 
STX $8080    Absolute       $8E   3     4     -------- 
```

---
[[Opcodes](#instructions-by-number)] | [[By Name](#instructions-by-name)] | [[By Category](#instructions-by-category)]

### STY

Save Y Index Register contents to memory

```text
SYNTAX       MODE           HEX  LEN  CYCLES  FLAGS    
STY $20      Zero Page      $84   2     3     -------- 
STY $20,X    Zero Page,X    $94   2     4     -------- 
STY $8080    Absolute       $8C   3     4     -------- 
```

---
[[Opcodes](#instructions-by-number)] | [[By Name](#instructions-by-name)] | [[By Category](#instructions-by-category)]

### STZ

Set memory to zero

```text
SYNTAX       MODE           HEX  LEN  CYCLES  FLAGS    
STZ $20      Zero Page      $64   2     3     -------- +c
STZ $20,X    Zero Page,X    $74   2     4     -------- +c
STZ $8080    Absolute       $9C   3     4     -------- +c
STZ $8080,X  Absolute,X     $9E   3     5     -------- +c
```

+c: New for the 65C02

---
[[Opcodes](#instructions-by-number)] | [[By Name](#instructions-by-name)] | [[By Category](#instructions-by-category)]

### TRB

Test and reset bit

```text
SYNTAX       MODE           HEX  LEN  CYCLES  FLAGS    
TRB $20      Zero Page      $14   2     5     ------Z- +c
TRB $8080    Absolute       $1C   3     5     ------Z- +c
```

Effectively an inverted AND between memory and the Accumulator. The bits that
are 1 in the Accumulator are set to 0 in memory.

- Sets Z (Zero) flag if all bits from the AND are zero.

+c: New for the 65C02

#### TRB Example

```asm
          ; Assume location $20 has a value of $11.
LDA #$01  ; Load a bit mask of 0000 0001
TRB $20   ; Apply the mask and reset bit 0
          ; Location $20 now has a value of $10.
```

This is conceptually similar to

```asm
LDA #$01 ; We want to clear bit 1 of the data
EOR #$FF ; Invert the mask, so $01 becomes $FE (1111 1110)
AND $20  ; AND with memory, saving the result in .A
STA $20  ; Store it back to memory.
```

---
[[Opcodes](#instructions-by-number)] | [[By Name](#instructions-by-name)] | [[By Category](#instructions-by-category)]

### TSB

Test and set bit

```text
SYNTAX       MODE           HEX  LEN  CYCLES  FLAGS    
TSB $20      Zero Page      $04   2     5     ------Z- +c
TSB $8080    Absolute       $0C   3     5     ------Z- +c
```

Performs an OR with each bit in the accumulator and memory.
Each bit that is 1 in the Accumulator is set to 1 in memory. This is similar to
an ORA operation, except that the result is stored in memory, not in A.

The Z flag is set based on the final result of the operation, ie: the memory
data is 0.

+c: New for the 65C02

---
[[Opcodes](#instructions-by-number)] | [[By Name](#instructions-by-name)] | [[By Category](#instructions-by-category)]

### Txx

Transfer between registers

```text
SYNTAX       MODE           HEX  LEN  CYCLES  FLAGS    
TAX          Implied        $AA   1     2     N-----Z- Copy from .A to .X
TXA          Implied        $8A   1     2     N-----Z- Copy from .X to .A
TAY          Implied        $A8   1     2     N-----Z- Copy from .A to .Y
TYA          Implied        $98   1     2     N-----Z- Copy from .Y to .A
TSX          Implied        $BA   1     2     N-----Z- Copy from Stack Pointer to .X
TXS          Implied        $9A   1     2     -------- Copy from .X to Stack Pointer
```

Copies data from one register to another.

TSX and TSX copy between the Stack Pointer and the X register. This is the only
way to directly control the Stack Pointer. To initialize the Stack Pointer to
a specific address, you can use the following instructions.

```asm
LDX #$FF
TXS
```

---
[[Opcodes](#instructions-by-number)] | [[By Name](#instructions-by-name)] | [[By Category](#instructions-by-category)]

### WAI

Wait

```text
SYNTAX       MODE           HEX  LEN  CYCLES  FLAGS    
WAI          Implied        $CB   1     3     -------- +c
```

Effectively stops the processor until a hardware interrupt occurs. The interrupt
is processed immediately, and execution resumes in the Interrupt handler.

NMI, IRQ, and RST (Reset) will recover from the WAI condition.

Normally, an instruction completes its operation before actually handling an
interrupt. But if WAI has executed, the CPU does not need to defer the
interrupt, and so the interrupt can be handled immediately.

+c: New for the 65C02

---
[[Opcodes](#instructions-by-number)] | [[By Name](#instructions-by-name)] | [[By Category](#instructions-by-category)]

## Status Flags

Flags are stored in the P register. PHP and PLP can be used
to directly manipulate this register. Otherwise the flags
are used to indicate certain statuses and changed by
various instructions.

P-Register:

`NV1B DIZC`

  N = Negative  
  V = oVerflow  
  1 = Always 1  
  B = Interrupt Flag  
  D = Decimal Mode  
  I = Interrupts Disabled  
  Z = Zero  
  C = Carry  

## Replacement Macros for Bit Instructions

Since `BBRx`, `BBSx`, `RMBx`, and `SMBx` should not be used, to maintain
compatibility with the 65C816, here are some example macros that can be
used to help convert existing software that may have been using these
instructions:

```asm
.macro bbs bit_position, data, destination
 .if (bit_position = 7)
  bit data
  bmi destination
 .else
  .if (bit_position = 6)
   bit data
   bvs destination
  .else
   lda data
   and #1 << bit_position
   bne destination
  .endif
  .endif
.endmacro

.macro bbr bit_position, data, destination
 .if (bit_position = 7)
  bit data
  bpl destination
 .else
  .if (bit_position = 6)
   bit data
   bvc destination
  .else
   lda data
   and #1 << bit_position
   beq destination
  .endif
 .endif
.endmacro

.macro rmb bit, destination
 lda #$1 << bit
 trb destination
.endmacro

.macro smb bit, destination
 lda #$1 << bit
 tsb destination
.endmacro
```

The above is CA65 specific but the code should work similarly for other
languages. The logic can also be used to if using an assembly language tool
that does not have macro support with small changes.

## Further Reading

- <http://www.6502.org/tutorials/6502opcodes.html>
- <http://6502.org/tutorials/65c02opcodes.html>
- <https://www.pagetable.com/c64ref/6502/?cpu=65c02>
- <http://www.oxyron.de/html/opcodesc02.html>
- <https://www.nesdev.org/wiki/Status_flags>
- <https://skilldrick.github.io/easy6502/>
- <https://www.westerndesigncenter.com/wdc/documentation/w65c02s.pdf>
- <https://www.westerndesigncenter.com/wdc/documentation/w65c816s.pdf>

a different page  

<!-- For PDF formatting -->
<div class="page-break"></div>

# Appendix D: Official Expansion Cards

This is just a stub as a proposal for how to document official expansion cards
(namely those made by the core X16 team).

## Serial/MIDI UART/Wavetable Expansion Card

Kevin is designing an EIA compliant UART expansion card which is capable of supporting 
standard serial as well as MIDI and even has a header to install wavetable cards.
It uses the Texas Instruments [TL16C2550](https://www.ti.com/product/TL16C2550).

![Prototype Serial Card](images/Appendix_B/X16-Serial.png)

As the card is still in development there are not any demos or code examples available,
though the datasheet contains information on how to set things up (see below). Kevin
also provided [some information](https://discord.com/channels/547559626024157184/548715649065811989/1183801692878295101) on how to set up the card in his original announcement on the community Discord.

<!-- For PDF formatting -->
<div class="page-break"></div>

# Appendix E: Diagnostic Bank

The Diagnostic ROM bank can run a full diagnostic on the system memory (base + 512K-2048K extended) of the Commander X16.

## Index

* [Running Diagnostics](#Running-Diagnostics)
* [Progress indicators](#Progress-Indicators)
	* [Without screen](#without-screen)
	* [With screen](#with-screen)
* [Error communication](#Error-communication)
* [Test algorithm](#test-algorithm)
	* [Theory](#theory)
	* [Implementation](#implementation)

## Running Diagnostics
### POST
As of R49, short, rudimentary diagnostics are run against the VIA#1,
zeropage, and stack RAM upon every powerup. If either of these tests
fail, the diagnostic ROM will attempt to initialize the VERA to show
a failure code on screen.

During these rudimentary tests and upon failure, POST codes can be sent to I/O address
$9FFF, which resides in the IO7 range.  Before writing a code to this
address, the system will attempt to read from $9FFF to check for
an expansion card's presence. If there is no card present, or if the
card handling the range does not respond to reads at this address, it
will act as an open bus read, and return $9F.  An open bus read will
cause the POST code to be written.  If any other value besides $9F is
read from $9FFF, the write is skipped.  This design allows POST codes
to be written in the presence of passive logical analysis hardware
while hopefully avoiding putting other expansion cards into a bad
state.

POST code format: `%FSSSCCCC`  
F = 1 for a critical fault (system will not continue booting), 0 for normal operation  
`SSS` = subsystem  
`CCCCCCC` = code  

| Subsystem | Description    |
|-----------|----------------|
| `%000`    | Generic status |
| `%001`    | VERA           |
| `%010`    | VIA#1          |
| `%011`    | RAM            |

The following table is a list of POST codes. In rows containing two codes,
the first code indicates the check is about to start, and the second code
indicates a failure of the check.

| Code      | Description                              |
|-----------|------------------------------------------|
| `$01`     | POST complete                            |
| `$20/$A0` | Check VIA#1                              |
| `$30/$B0` | Check zeropage RAM                       |
| `$31/$B1` | Check stack RAM                          |
| `$90`     | POST failure: Waiting for VERA init      |
| `$91`     | POST failure: Initializing VERA          |
| `$92`     | POST failure: VERA not ready             |

### Functional system
The memory diagnostics can be started in two different ways. If the system is functional enough to actually boot into BASIC, the diagnostics can be started from there with the following:  
```BASIC
BANK 0,7: SYS $C000
```

It is also possible to jump directly to the diagnostic ROM bank from assembly.  
```asm
	lda	#$07    ; ROM bank 7 is the diagnostic bank
	sta	$01     ; Write ROM bank to ROM bank registers
	jmp	$C000   ; Jump to beginning of diagnostic ROM
```  

NOTE: The Diagnostic ROM is not able to return to BASIC or any program that has called. The only way to exit the Diagnostic ROM is by resetting or power cycling the system.
### Non functional system
If the Commander X16 is not able to boot into BASIC, the memory diagnostics can be started by keeping the power button pressed for about a second when powering on the system.  
This will make the Commander X16 boot directly into the diagnostic ROM bank and start the memory diagnostics.

## Progress indicators
### Without screen
When the diagnostic ROM bank starts, it will use the activity LED to indicate the progress.  
* ON - while zero-page memory is tested (very brief)
* OFF - for 1st test of base memory (\$0100-\$9EFF)
* ON - for 2nd test of base memory (\$0100-\$9EFF)
* OFF - for 3rd test of base memory (\$0100-\$9EFF)
* ON - for 4th test of base memory (\$0100-\$9EFF)
  
After the initial test of base memory, the number of available memory banks is tested, VERA is initialized and both the activity LED and the keyboard LEDs are used to indicate the progress.  
The keyboard LEDs are used as a binary counter:  
| Num | Binary | Num Lock | Caps Lock | Scroll Lock |
|-----|--------|----------|-----------|-------------|
|  0  |  000   |    0     |     0     |      0      |
|  1  |  001   |    0     |     0     |      1      |
|  2  |  010   |    0     |     1     |      0      |
|  3  |  011   |    0     |     1     |      1      |
|  4  |  100   |    1     |     0     |      0      |
|  5  |  101   |    1     |     0     |      1      |
|  6  |  110   |    1     |     1     |      0      |
|  7  |  111   |    1     |     1     |      1      |
  
#### Main test loop
During the first test iteration, the keyboard LEDs will display 0 0 1  
When the test is done, the activity light will blink once.  
During the second test iteration, the keyboard LEDs will display 0 1 0  
When the test is done, the activity light will blink once.  
During the third test iteration, the keyboard LEDs will display 0 1 1  
When the test is done, the activity light will blink once.  
During the fourth test iteration, the keyboard LEDs will display 1 0 0  
When the test is done, the activity light will blink once.  

As the last part of the test loop, the base memory is tested. Keyboard LEDs will show 1 0 1  
When the test loop is done, keyboard LEDs will show 1 1 1 and the activity LED will blink 3 times before starting over.
### With screen
When the base memory has been tested the first time, VERA is initialized with output to VGA.  
On the screen there is detailed information about the progress of each test iteration.  
Each time through the main test loop, the output of VERA will be switched between VGA and Composite/S-Video.  

## Error communication
If an error is detected before VERA is initialized, the error will be reported with the activity LED by blinking every half second 3 times, staying off for 1 second and repeating. - All tests stop.  
  
This means that if an error occurs before VERA is initialized, you have no way of figuring out exactly where the error is, but you do know that the error has happened in base memory.  
  
When the initial test of base memory has succeeded and VERA is initialized, any errors will be reported to the display. Only if more than 32 errors are encountered, will the tests stop and the activity LED will flash the same way as when an error is encountered before VERA initialization.  
  
Even when tests are stopped, VERA output will still be switched between VGA and Composite/S-Video about every minute.
  
The error codes on screen are as follows:
![Error code definition](images/Appendix_E/mem-diag-error-code.jpg)

## Test algorithm
### Theory
RAM diagnostics are performed with the March C- algorithm. This algorithm should be fairly good at finding most common memory errors.  
  
In short, the algorithm is described as follows:
1. Write 0 to all memory cells
2. For each cell, check that it contains 0 and write 1 in ascending order
3. For each cell, check that it contains 1 and write 0 in ascending order
4. For each cell, check that it contains 0 and write 1 in descending order
5. For each cell, check that it contains 1 and write 0 in descending order
6. Check that all cells contain 0
  
On the Commander X16 and most other 6502 based computers, above algorithm would take a very long time to complete. For this reason, the algorithm has been modified slightly to write and compare entire bytes instead of single bits.
To catch most memory errors, the following bit patterns are tested:
* 0000 0000
* 0101 0101
* 0011 0011
* 0000 1111
  
The algorithm is then implemented in the following way:
1. Write pattern to all memory addresses
2. For each address, check the pattern and write the inverted pattern in ascending order
3. For each address, check the inverted pattern and write the original pattern in ascending order
4. For each address, check the original pattern and write the inverted pattern in descending order
5. For each address, check the inverted pattern and write the original pattern in descending order
6. Check all addresses contain the original pattern
### Implementation
When memory test starts, the first thing that happens is that zero-page is tested by itself. If this test passes, the rest of base memory is tested from \$0100-\$9EFF while ensuring that these tests do not affect zero-page memory.  
  
When base memory has passed the initial test, zero-page is used for variables and stack pointer is initialized to enable pushing and popping of registers and function calls.  
VERA is initialized and the number of memory banks is tested.  
  
All available memory banks are tested together as opposed to checking and clearing a single memory page at a time.  
When all memory banks have been tested, the base memory \$0200-\$9EFF is tested again.  
  
Memory banks and base memory is tested in continuous loop.  
  
If an error is detected, this is either communicated through the activity LED, if VERA has not yet been initialized, or by writing information about the error on the display.
<!-- For PDF formatting -->
<div class="page-break"></div>

# Appendix F: The 65C816 Processor

## Table Of Contents

1. [Overview](#overview)
2. [Compatibility with the 65C02](#compatibility-with-the-65c02)
3. [Registers](#registers)
4. [Status Flags](#status-flags)
5. [16 bit mode](#16-bit-mode)
6. [Address Modes](#address-modes)
7. [Vectors](#vectors)
8. [Instruction Tables](#instruction-tables)

## Overview

This document is a brief introduction and quick reference for the 65C816
Microprocessor. For more details, see the [65C816 data
sheet](https://www.westerndesigncenter.com/wdc/documentation/w65c816s.pdf) or
[Programming the 65816: Including the 6502, 65C02, and 65802](https://www.amazon.com/Programming-65816-Including-65C02-65802-ebook/dp/B01855HL7Q).

The WDC65C816 CPU is an 8/16 bit CPU and a follow-up to the 65C02 processor. The
familiar 65C02 instructions and address modes are retained, and some new ones
are added.

The CPU can optionally operate in 16-bit mode, extending the utility of math
instruction (16-bit adds!) and the coverage of .X and .Y indexed modes to 64KB.

Zero Page has been renamed to Direct Page, and Direct Page can now be relocated
anywhere in the first 64K of RAM. As a result, all of the Zero Page instructions
are now "Direct" instructions and can operate anywhere in the X16's address
range.

Likewise, the Stack can also be relocated, and the stack pointer is now 16 bits.
This allows for a much larger stack, and the combination of stack and DP
relocation offer interesting multitasking opportunities.

## Compatibility with the 65C02

The 65C816 CPU is generally compatible with the 65C02 instruction set, with the
exception of the `BBRx`, `BBSx`, `RMBx`, and `SMBx` instructions. We recommend
programmers avoid these instructions when writing X16 software, using the more
conventional Boolean logic instructions, instead.

## Registers

| Notation  | Name             | Description     |
|-----------|------------------|-----------------|
| A         | Accumulator      | The accumulator. It stores the result of moth math and logical operations.  |
| X         | X Index          | .X is mostly used as a counter and to offset addresses with X indexed modes |
| Y         | Y Index          | .Y is mostly used as a counter and to offset addresses with Y indexed modes |
| S         | Stack Pointer    | SP points to the next open position on the stack.                           |
| DB or DBR | Data Bank        | Data bank is the default bank for operations that use a 16 bit address.     |
| K or  PBR | Program Bank     | The default address for 16 bit JMP and JSR operations. Can only be set with a 24 bit JMP or JSR. |
| P         | Processor Status | The flags. |
| PC        | Program Counter  | The address of the current CPU instruction |

.A, .X, and .Y can be 8 or 16 bits wide, based on the flag settings (see below).

The Stack Pointer (.S) is 16 bits wide in Native mode and 8 bits wide (and fixed
to the $100-1FF range) in Emulation mode.

.DB and .K are the bank registers, allowing programs and data to occupy separate
64K banks on computers with more than 64K of RAM. (The X16 does not use the bank
registers, instead using addresses \$00 and \$01 for banking.)

## Status Flags

The native mode flags are as follows:

`nvmx dizc e`

  n = Negative  
  v = oVerflow  
  m = Memory width (0=16 bit, 1=8 bit)  
  x = Index register width (0=16 bit, 1=8 bit)  
  d = Decimal Mode  
  i = Interrupts Disabled  
  z = Zero  
  c = Carry  
  e = Emulation mode (0=65C816 mode, 1=65C02 mode)

In emulation mode, the **m** and **x** flags are always set to 1.

Here are the 6502 and 65C02 registers, for comparison:

`nv1b dizc`

  n = Negative  
  v = oVerflow  
  1 = this bit is always 1  
  b = brk: set during a BRK instruction interrupt  
  d = Decimal Mode  
  i = Interrupts Disabled  
  z = Zero  
  c = Carry  

Note the missing **b** flag on the 65C816. This is no longer needed in native
mode, since the BRK instruction now has its own vector. 

The **e** flag can only be accessed via the XCE instruction, which swaps Carry and
the Emulation flag.

The other flags can all be manipulated with SEP and REP, and the various
branch instructions (BEQ, BCS, etc) test some of the flags. The rest
can only be tested indirectly through the stack.

When a BRK or IRQ is triggered in _emulation_ mode, a ghost **b** flag
will be pushed to the stack instead of the **x** flag. This can be used
to test for a BRK vs IRQ in the Interrupt handler.

## 16 bit mode

The 65C816 CPU boots up in emulation mode. This locks the register width to
8 bits and locks out certain operations.

If you want to use the '816 features, including 16-bit operation, you will
need to enable _native_ mode. Clearing **e** switches the CPU to native mode.
However, it's not as simple as just setting a flag. The **e** flag can only
be accessed through the XCE instruction, which swaps the Carry and Emulation
flags.

To switch to native mode, use the following steps:

```
CLC  ; clear the Carry bit
XCE  ; swap the Emulation and Carry bit
```

To switch back to emulation mode, _set_ the Carry flag and perform an XCE again.

```
SEC  ; Set Carry
XCE  ; and push the 1 into the Emulation flag.
```

Once **e** is cleared, the **m** and **x** flags can be set to 1 or 0 to control
the register width.

When the **m** flag is *clear*, Accumulator operations and memory reads and writes
will be 16-bit operations. The CPU reads two bytes at a time with LDA, writes
two bytes at a time with STA, and all math involving .A is 16 bits wide.

Likewise, when **x** is clear, the .X and .Y index registers are 16 bits wide.
INX and INY will now count up to 65535, and indexed instructions like `LDA addr,X`
can now cover 64K.

You can use `REP #$10` to enable 16-bit index registers, and `REP #$20` to
enable 16-bit memory and Accumulator. `SEP #$10` or `SEP #$20` will switch back
to 8-bit operation. You can also combine the operand and use `SEP #$30` or 
`REP #$30` to flip both bits at once.

And now we reach the 16-bit assembly trap: the actual assembly opcodes are the
same, regardless of the **x** and **m** flags. This means the assembler needs
to track the state of these flags internally, so it can correctly write one or
two bytes when assembling immediate mode instructions like LDA #$01.

You can help the assembler out by using _hints_. Different assemblers have different
hinting systems, so we will focus on 64TASS and cc65.

[64TASS](https://sourceforge.net/projects/tass64/) accepts `.as` (.A short) and
`.al` (.A long) to  tell the assembler to store 8 bits or 16 bits in an immediate
mode operand. For LDX and LDY, use the `.xs` and `.xl` hints.

The hints for [ca65](https://cc65.github.io/) are `.a8`, `.a16`, `.i8`, and `.i16`

Note that this has no effect on _absolute_ or _indirect_ addressing modes, such
as `LDA $1234` and `LDA ($1000)`, since the operand for these modes is always
16 bits.

To make it easy to remember the modes, just remember that **e**, **m**, and **x**
all _emulate_ 65C02 behavior when _set_.

****

## Address Modes

The 65C816 now has 24 distinct address modes, although most are variations on a
theme. Make note of the new syntax for Stack relative instructions (,S), the use
of brackets for [24 bit indirect] addressing, and the fact that Zero Page has
been renamed to Direct Page. This means that \$0001 and \$01 are now two different
addresses (although they would be the same if .DP is set to \$00.

| Mode                            | Syntax    | Description |
| ------------------------------- | --------- | ------------------------------------------------------------------ |
| Immediate                       | #$12      | Value is supplied in the program stream                            |
| Absolute                        | $1234     | Data is at this address.                                           |
| Absolute X Indexed              | $1234,X   | Address is offset by X. If X=2 this is $1236.                      |
| Absolute Y Indexed              | $1234,Y   | Address is offset by X. If Y=2 this is $1236.                      |
| Direct                          | $12       | Direct Page address. Operand is 1 byte.                            |
| Direct X Indexed                | $12,X     | Address on Direct Page is offset by .X                             |
| Direct Y Indexed                | $12,Y     | Address on Direct Page is offset by .Y                             |
| Direct Indirect                 | ($12)     | Value at $12 is a 16-bit address.                                  |
| Direct Indirect Y Indexed       | ($12),Y   | Resolve pointer at $12 then offset by Y.                           |
| Direct X Indexed Indirect       | ($12,X)   | Start at $12, offset by X, then read that address.                 |
| Direct Indirect Long            | [$12]     | 24 bit pointer on Direct Page.                                     |
| Direct Indirect Long Y Indexed   | [$12],Y   | Resolve address at $12, then offset by Y.                          |
| Indirect                        | ($1234)   | Read pointer at $1234 and get data from the resultant address      |
| Indirect X Indexed              | ($1234,X) | Read pointer at $1234 offset by X, get data from resultant address |
| Indirect Long                   | [$1234]   | Pointer is a 24-bit address.                                       |
| Absolute Long                   | $123456   | 24 bit address.                                                    |
| Absolute Indexed Long           | $123456,X | 24 bit address, offset by X.                                       |
| Stack Relative Indexed          | $12,S     | Stack relative.                                                    |
| Stack Relative Indirect Indexed | ($12,S),Y | Resolve Pointer at $12, then offset by Y.                          |
| Accumulator (implied)           |           | Operation acts on .A                                               |
| Implied                         |           | Target is part of the opcode name.                                 |
| Relative Address (8 bit signed) | $1234     | Branches can only jump by -128 to 127 bytes.                       |
| 16 bit relative address         | $1234     | BRL can jump by 32K bytes.                                         |
| Block Move                      | #\$12,#\$34 | Operands are the bank numbers for block move/copy.                 |

## Vectors

The 65C816 has two different sets of interrupt vectors. In emulation mode, the
vectors are the same as the 65C02. In native mode (.e = 0), the native vectors
are used. This allows you to switch to the desired operation mode, based on the
operating mode of your interrupt handlers.

The Commander X16 operates mostly in emulation mode, so native mode interrupts
on the X16 will switch to emulation mode, then simply call the 8-bit interrupt
handlers.

The vectors are:

| Name  | Emu   | Native |
|-------|-------|--------|
| COP   | FFF4  | 00FFE4 |
| BRK   | FFFE  | 00FFE6 |
| ABORT | FFF8  | 00FFE8 |
| NMI   | FFFA  | 00FFEA |
| RESET | FFFC  |        |
| IRQ   | FFFE  | 00FFEE |

The 65C02 shares the same interrupt for BRK and IRQ, and the **b** flag tells
the interrupt handler whether to execute a break or interrupt.

In emulation mode, the 65C816 pushes a modified version of the flags to the
stack. The BRK instruction actually pushes a 1 in bit 4, which can then be
tested in the Interrupt Service Routine. In native mode, however, the flags are
pushed verbatim, since BRK has its own handler.

There is also no native RESET vector, since the CPU always boots to emulation
mode. The CPU always starts at the address stored in $FFFC.

## Decimal Mode

When the **d** flag is set, the CPU operates in Decimal mode. In this mode, a
byte is treated as two decimal digits, rather than a binary number. As a result,
you can easily add, subtract, and display decimal numbers.

While in Decimal mode, the lower nibble of a byte contains the 1s digit, and the
upper nibble contains the 10s digit. Each nibble can only contain value from
0-9, and addition will wrap from 9 to 0. Subtraction works similarly, wrapping
down from 0 to 9.

[SED](#sed) enables Decimal mode. At that point, ADC and SBC will perform base-10
addition and subtraction. [CLD](#cld) clears Decimal mode and returns to binary
mode.

When adding, the Carry bit will be set if the result is 100 or greater. The
total result can never exceed 199, so two digits plus Carry is all that is
needed to represent values from 0 to 199.

If you perform an ADC with the Carry bit set, this will add an extra 1 to the
result. 

Examples

| Operation | .A   | Result | Notes                         |
|-----------|------|--------|-------------------------------|
| ADC #$01  | $09  | $10    |                               |
| ADC #$01  | $99  | $00    | Carry is set, indicating 100. |

When subtracting, the Carry bit operates as a _borrow_ bit, and the sense is
inverted: 0 indicates a borrow took place, and 1 means it did not.

| Operation | .A   | Result | Notes                               |
|-----------|------|--------|-------------------------------------|
| SBC #$01  | $10  | $09    | Carry is set, indicating no borrow. |
| SBC #$01  | $00  | $99    | Carry is clear, indicating a borrow.|

In the second example (\$00 - \$01), the final result was \$99 with a borrow. 

Note that the **n** flag tracks the high bit, but two's complement doesn't work
as expected in Decimal mode. Instead, we have to use _Ten's complement_. 

Simply put, \$00 - \$01 gives you \$99. So when working in signed BCD, any value
where the high digit is 5-9 is actually a negative value. To convert negative
values to positive values for printing, you would subtract from 99 and add 1.

For example: the integer -49 is $51 in BCD. `99 - 51 + 1 = 49`. You'd print that
as `-49`.

## Instruction Tables

### Instructions By Opcode

|           |x0         |x1         |x2         |x3         |x4         |x5         |x6         |x7         |x8         |x9         |xA         |xB         |xC         |xD         |xE         |xF         |
|-----------|-----------|-----------|-----------|-----------|-----------|-----------|-----------|-----------|-----------|-----------|-----------|-----------|-----------|-----------|-----------|-----------|
|        0x |[BRK](#brk)|[ORA](#ora)|[COP](#cop)|[ORA](#ora)|[TSB](#tsb)|[ORA](#ora)|[ASL](#asl)|[ORA](#ora)|[PHP](#php)|[ORA](#ora)|[ASL](#asl)|[PHD](#phd)|[TSB](#tsb)|[ORA](#ora)|[ASL](#asl)|[ORA](#ora)|
|        1x |[BPL](#bpl)|[ORA](#ora)|[ORA](#ora)|[ORA](#ora)|[TRB](#trb)|[ORA](#ora)|[ASL](#asl)|[ORA](#ora)|[CLC](#clc)|[ORA](#ora)|[INC](#inc)|[TCS](#tcs)|[TRB](#trb)|[ORA](#ora)|[ASL](#asl)|[ORA](#ora)|
|        2x |[JSR](#jsr)|[AND](#and)|[JSL](#jsl)|[AND](#and)|[BIT](#bit)|[AND](#and)|[ROL](#rol)|[AND](#and)|[PLP](#plp)|[AND](#and)|[ROL](#rol)|[PLD](#pld)|[BIT](#bit)|[AND](#and)|[ROL](#rol)|[AND](#and)|
|        3x |[BMI](#bmi)|[AND](#and)|[AND](#and)|[AND](#and)|[BIT](#bit)|[AND](#and)|[ROL](#rol)|[AND](#and)|[SEC](#sec)|[AND](#and)|[DEC](#dec)|[TSC](#tsc)|[BIT](#bit)|[AND](#and)|[ROL](#rol)|[AND](#and)|
|        4x |[RTI](#rti)|[EOR](#eor)|[WDM](#wdm)|[EOR](#eor)|[MVP](#mvp)|[EOR](#eor)|[LSR](#lsr)|[EOR](#eor)|[PHA](#pha)|[EOR](#eor)|[LSR](#lsr)|[PHK](#phk)|[JMP](#jmp)|[EOR](#eor)|[LSR](#lsr)|[EOR](#eor)|
|        5x |[BVC](#bvc)|[EOR](#eor)|[EOR](#eor)|[EOR](#eor)|[MVN](#mvn)|[EOR](#eor)|[LSR](#lsr)|[EOR](#eor)|[CLI](#cli)|[EOR](#eor)|[PHY](#phy)|[TCD](#tcd)|[JML](#jml)|[EOR](#eor)|[LSR](#lsr)|[EOR](#eor)|
|        6x |[RTS](#rts)|[ADC](#adc)|[PER](#per)|[ADC](#adc)|[STZ](#stz)|[ADC](#adc)|[ROR](#ror)|[ADC](#adc)|[PLA](#pla)|[ADC](#adc)|[ROR](#ror)|[RTL](#rtl)|[JMP](#jmp)|[ADC](#adc)|[ROR](#ror)|[ADC](#adc)|
|        7x |[BVS](#bvs)|[ADC](#adc)|[ADC](#adc)|[ADC](#adc)|[STZ](#stz)|[ADC](#adc)|[ROR](#ror)|[ADC](#adc)|[SEI](#sei)|[ADC](#adc)|[PLY](#ply)|[TDC](#tdc)|[JMP](#jmp)|[ADC](#adc)|[ROR](#ror)|[ADC](#adc)|
|        8x |[BRA](#bra)|[STA](#sta)|[BRL](#brl)|[STA](#sta)|[STY](#sty)|[STA](#sta)|[STX](#stx)|[STA](#sta)|[DEY](#dey)|[BIT](#bit)|[TXA](#txa)|[PHB](#phb)|[STY](#sty)|[STA](#sta)|[STX](#stx)|[STA](#sta)|
|        9x |[BCC](#bcc)|[STA](#sta)|[STA](#sta)|[STA](#sta)|[STY](#sty)|[STA](#sta)|[STX](#stx)|[STA](#sta)|[TYA](#tya)|[STA](#sta)|[TXS](#txs)|[TXY](#txy)|[STZ](#stz)|[STA](#sta)|[STZ](#stz)|[STA](#sta)|
|        Ax |[LDY](#ldy)|[LDA](#lda)|[LDX](#ldx)|[LDA](#lda)|[LDY](#ldy)|[LDA](#lda)|[LDX](#ldx)|[LDA](#lda)|[TAY](#tay)|[LDA](#lda)|[TAX](#tax)|[PLB](#plb)|[LDY](#ldy)|[LDA](#lda)|[LDX](#ldx)|[LDA](#lda)|
|        Bx |[BCS](#bcs)|[LDA](#lda)|[LDA](#lda)|[LDA](#lda)|[LDY](#ldy)|[LDA](#lda)|[LDX](#ldx)|[LDA](#lda)|[CLV](#clv)|[LDA](#lda)|[TSX](#tsx)|[TYX](#tyx)|[LDY](#ldy)|[LDA](#lda)|[LDX](#ldx)|[LDA](#lda)|
|        Cx |[CPY](#cpy)|[CMP](#cmp)|[REP](#rep)|[CMP](#cmp)|[CPY](#cpy)|[CMP](#cmp)|[DEC](#dec)|[CMP](#cmp)|[INY](#iny)|[CMP](#cmp)|[DEX](#dex)|[WAI](#wai)|[CPY](#cpy)|[CMP](#cmp)|[DEC](#dec)|[CMP](#cmp)|
|        Dx |[BNE](#bne)|[CMP](#cmp)|[CMP](#cmp)|[CMP](#cmp)|[PEI](#pei)|[CMP](#cmp)|[DEC](#dec)|[CMP](#cmp)|[CLD](#cld)|[CMP](#cmp)|[PHX](#phx)|[STP](#stp)|[JML](#jml)|[CMP](#cmp)|[DEC](#dec)|[CMP](#cmp)|
|        Ex |[CPX](#cpx)|[SBC](#sbc)|[SEP](#sep)|[SBC](#sbc)|[CPX](#cpx)|[SBC](#sbc)|[INC](#inc)|[SBC](#sbc)|[INX](#inx)|[SBC](#sbc)|[NOP](#nop)|[XBA](#xba)|[CPX](#cpx)|[SBC](#sbc)|[INC](#inc)|[SBC](#sbc)|
|        Fx |[BEQ](#beq)|[SBC](#sbc)|[SBC](#sbc)|[SBC](#sbc)|[PEA](#pea)|[SBC](#sbc)|[INC](#inc)|[SBC](#sbc)|[SED](#sed)|[SBC](#sbc)|[PLX](#plx)|[XCE](#xce)|[JSR](#jsr)|[SBC](#sbc)|[INC](#inc)|[SBC](#sbc)|

### Instructions By Name

|             |             |             |             |             |             |             |             |             |             |
|-------------|-------------|-------------|-------------|-------------|-------------|-------------|-------------|-------------|-------------|
| [ADC](#adc) | [AND](#and) | [ASL](#asl) | [BCC](#bcc) | [BCS](#bcs) | [BEQ](#beq) | [BIT](#bit) | [BMI](#bmi) | [BNE](#bne) | [BPL](#bpl) |
| [BRA](#bra) | [BRK](#brk) | [BRL](#brl) | [BVC](#bvc) | [BVS](#bvs) | [CLC](#clc) | [CLD](#cld) | [CLI](#cli) | [CLV](#clv) | [CMP](#cmp) |
| [COP](#cop) | [CPX](#cpx) | [CPY](#cpy) | [DEC](#dec) | [DEX](#dex) | [DEY](#dey) | [EOR](#eor) | [INC](#inc) | [INX](#inx) | [INY](#iny) |
| [JMP](#jmp) | [JML](#jml) | [JSL](#jsl) | [JSR](#jsr) | [LDA](#lda) | [LDX](#ldx) | [LDY](#ldy) | [LSR](#lsr) | [MVN](#mvn) | [MVP](#mvp) |
| [NOP](#nop) | [ORA](#ora) | [PEA](#pea) | [PEI](#pei) | [PER](#per) | [PHA](#pha) | [PHB](#phb) | [PHD](#phd) | [PHK](#phk) | [PHP](#php) |
| [PHX](#phx) | [PHY](#phy) | [PLA](#pla) | [PLB](#plb) | [PLD](#pld) | [PLP](#plp) | [PLX](#plx) | [PLY](#ply) | [REP](#rep) | [ROL](#rol) |
| [ROR](#ror) | [RTI](#rti) | [RTL](#rtl) | [RTS](#rts) | [SBC](#sbc) | [SEC](#sec) | [SED](#sed) | [SEI](#sei) | [SEP](#sep) | [STA](#sta) |
| [STP](#stp) | [STX](#stx) | [STY](#sty) | [STZ](#stz) | [TAX](#tax) | [TAY](#tay) | [TCD](#tcd) | [TCS](#tcs) | [TDC](#tdc) | [TRB](#trb) |
| [TSB](#tsb) | [TSC](#tsc) | [TSX](#tsx) | [TXA](#txa) | [TXS](#txs) | [TXY](#txy) | [TYA](#tya) | [TYX](#tyx) | [WAI](#wai) | [WDM](#wdm) |
| [XBA](#xba) | [XCE](#xce) |             |             |             |             |             |             |             |             |

### Instructions By Category

|Category       |Instructions   |
|---------------|---------------|
| Arithmetic    | [ADC](#adc) , [SBC](#sbc) |
| Boolean       | [AND](#and) , [EOR](#eor) , [ORA](#ora) |
| Shift         | [ASL](#asl) , [LSR](#lsr) , [ROL](#rol) , [ROR](#ror) |
| Branch        | [BCC](#bcc) , [BCS](#bcs) , [BEQ](#beq) , [BMI](#bmi) , [BNE](#bne) , [BPL](#bpl) , [BRA](#bra) , [BRK](#brk) , [BRL](#brl) , [BVC](#bvc) , [BVS](#bvs) |
| Test          | [BIT](#bit) , [TRB](#trb) , [TSB](#tsb) |
| Flags         | [CLC](#clc) , [CLD](#cld) , [CLI](#cli) , [CLV](#clv) , [REP](#rep) , [SEC](#sec) , [SED](#sed) , [SEI](#sei) , [SEP](#sep) |
| Compare       | [CMP](#cmp) , [CPX](#cpx) , [CPY](#cpy) |
| Interrupt     | [COP](#cop) , [STP](#stp) , [WAI](#wai) |
| Inc/Dec       | [DEC](#dec) , [DEX](#dex) , [DEY](#dey) , [INC](#inc) , [INX](#inx) , [INY](#iny) |
| Flow          | [JMP](#jmp) , [JML](#jml) , [JSL](#jsl) , [JSR](#jsr) , [NOP](#nop) , [RTI](#rti) , [RTL](#rtl) , [RTS](#rts) , [WDM](#wdm) |
| Load          | [LDA](#lda) , [LDX](#ldx) , [LDY](#ldy) |
| Block Move    | [MVN](#mvn) , [MVP](#mvp) |
| Stack         | [PEA](#pea) , [PEI](#pei) , [PER](#per) , [PHA](#pha) , [PHB](#phb) , [PHD](#phd) , [PHK](#phk) , [PHP](#php) , [PHX](#phx) , [PHY](#phy) , [PLA](#pla) , [PLB](#plb) , [PLD](#pld) , [PLP](#plp) , [PLX](#plx) , [PLY](#ply) |
| Store         | [STA](#sta) , [STX](#stx) , [STY](#sty) , [STZ](#stz) |
| Register Swap | [TAX](#tax) , [TAY](#tay) , [TCD](#tcd) , [TCS](#tcs) , [TDC](#tdc) , [TSC](#tsc) , [TSX](#tsx) , [TXA](#txa) , [TXS](#txs) , [TXY](#txy) , [TYA](#tya) , [TYX](#tyx) , [XBA](#xba) , [XCE](#xce) |

#### ADC

**Add with Carry**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
ADC #$20/#$1234  imm        69  3-m 3-m         nv....zc .
ADC $20          dir        65  2   4-m+w       nv....zc .
ADC $20,X        dir,X      75  2   5-m+w       nv....zc .
ADC $20,S        stk,S      63  2   5-m         nv....zc .
ADC $1234        abs        6D  3   5-m         nv....zc .
ADC $1234,X      abs,X      7D  3   6-m-x+x*p   nv....zc .
ADC $1234,Y      abs,Y      79  3   6-m-x+x*p   nv....zc .
ADC $FEDBCA      long       6F  4   6-m         nv....zc .
ADC $FEDCBA,X    long,X     7F  4   6-m         nv....zc .
ADC ($20)        (dir)      72  2   6-m+w       nv....zc .
ADC ($20),Y      (dir),Y    71  2   7-m+w-x+x*p nv....zc .
ADC ($20,X)      (dir,X)    61  2   7-m+w       nv....zc .
ADC ($20,S),Y    (stk,S),Y  73  2   8-m         nv....zc .
ADC [$20]        [dir]      67  2   7-m+w       nv....zc .
ADC [$20],Y      [dir],Y    77  2   7-m+w       nv....zc .
```

ADC adds the accumulator (.A), the supplied operand, and the Carry bit (0 or 1).
The result is stored in .A.

Since Carry is always added in, you should always remember to use CLC (Clear
Carry) before performing an addition operation. When adding larger numbers (16,
24, 32, or more bits), you can use the Carry flag to chain additions.

Here is an example of a 16-bit add, when in 8 bit mode:

```asm
CLC
LDA Addend1
ADC Addend2
STA Result1
LDA Addend1+1  ; Reads the high byte of the addend
ADC Addend2+1  ; (the +1 refers to the *address* of Addend, not the value)
STA Result1+1  ;
done:
; the final result is at Result1
```

Flags:

* **n** is set when the high bit of .A is set. This indicates a negative number
when using Two's Complement signed values.
* **v** (overflow) is set when the sum exceeds the maximum *signed* value for .A.
(More on that below). * **n** is set when the high bit is 1.
* **z** is set when the result is zero. This is useful for loop counters and can be
tested with BEQ and BNE. (BEQ and BNE test the Zero bit, which is also the
"equal" bit when performing subtraction or Compare operations.)
* **c** is set when the unsigned result exceeds the register's capacity (255 or
65535).

#### Overflow vs Carry

The CPU detects addition that goes past the 7 or 15 bit boundary of a signed
number, as well as the 8 bit boundary of an unsigned number.

In 8-bit mode, when you add two positive numbers that result in a sum
higher than 127 or add two negative numbers that result in a sum below -128, you
will get a signed overflow, and the v flag will be set.

When the sum of the two numbers exceeds 255 or 65535, then the Carry flag will
be set. This bit can be added to the next higher byte with ADC #0.

```asm
CLC
LDA #$7F
ADC #$10
BRK
```


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### AND

**Boolean AND**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
AND #$20/#$1234  imm        29  3-m 3-m         n.....z. .
AND $20          dir        25  2   4-m+w       n.....z. .
AND $20,X        dir,X      35  2   5-m+w       n.....z. .
AND $20,S        stk,S      23  2   5-m         n.....z. .
AND $1234        abs        2D  3   5-m         n.....z. .
AND $1234,X      abs,X      3D  3   6-m-x+x*p   n.....z. .
AND $1234,Y      abs,Y      39  3   6-m-x+x*p   n.....z. .
AND $FEDBCA      long       2F  4   6-m         n.....z. .
AND $FEDCBA,X    long,X     3F  4   6-m         n.....z. .
AND ($20)        (dir)      32  2   6-m+w       n.....z. .
AND ($20),Y      (dir),Y    31  2   7-m+w-x+x*p n.....z. .
AND ($20,X)      (dir,X)    21  2   7-m+w       n.....z. .
AND ($20,S),Y    (stk,S),Y  33  2   8-m         n.....z. .
AND [$20]        [dir]      27  2   7-m+w       n.....z. .
AND [$20],Y      [dir],Y    37  2   7-m+w       n.....z. .
```

Perform a logical AND operation with the operand and .A

AND compares each bit of the operands and sets the result bit to 1 only when the
matching bit of each operand is 1.

AND is useful for reading a group of bits from a byte. For example, `AND #$0F`
will clear the top nibble of .A, returning the bits from the lower nibble.

Truth table for AND:

```text
Operand 1: 1100
Operand 2: 1010
Result:    1000
```

Flags:

* **n** is set when the high bit of the result is 1
* **z** is set when the result is Zero

See also: [ORA](#ora), [EOR](#eor)


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### ASL

**Arithmetic Shift Left**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
ASL              acc        0A  1   2           n.....zc .
ASL $20          dir        06  2   7-2*m+w     n.....zc .
ASL $20,X        dir,X      16  2   8-2*m+w     n.....zc .
ASL $1234        abs        0E  3   8-2*m       n.....zc .
ASL $1234,X      abs,X      1E  3   9-2*m       n.....zc .
```

ASL shifts the target left one place. It shifts the high bit of the operand into
the Carry flag and a zero into the low bit.

See also: [LSR](#lsr), [ROL](#rol), [ROR](#ror)


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### BCC

**Branch on Carry Clear**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
BCC LABEL        rel8       90  2   2+t+t*e*p   ........ .
```

Jumps to the target address when the Carry flag (**c**) is Zero.

BCC can be used after add, subtract, or compare operations. After a compare,
**c** is as follows:

* When A < Operand, **c** is clear.
* When A >= Operand, **c** is set.

A branch operation uses an 8 bit signed value internally, starting from the
instruction after the branch. So the branch destination can be 126 bytes before
or 128 bytes after the branch instruction.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### BCS

**Branch on Carry Set**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
BCS LABEL        rel8       B0  2   2+t+t*e*p   ........ .
```

Jumps to the target address when the Carry flag is 1.

BCC can be used after add, subtract, or compare operations. After a compare,
**c** is as follows:

* When A < Operand, **c** is clear.
* When A >= Operand, **c** is set.

A branch operation uses an 8 bit signed value internally, starting from the
instruction after the branch. So the branch destination can be 126 bytes before
or 128 bytes after the branch instruction.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### BEQ

**Branch on Equal.**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
BEQ LABEL        rel8       F0  2   2+t+t*e*p   ........ .
```

Jumps to the target address when the Zero flag is 1. While this is most commonly
used after a compare (see [CMP](#cmp) ) operation, it's also useful to test if a
number is zero after a Load operation, or to test if a loop is complete after a
DEC operation.

A branch operation uses an 8 bit signed value internally, starting from the
instruction after the branch. So the branch destination can be 126 bytes before
or 128 bytes after the branch instruction.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### BIT

**Bit Test**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
BIT #$20/#$1234  imm        89  3-m 3-m         ......z. .
BIT $20          dir        24  2   4-m+w       nv....z. .
BIT $20,X        dir,X      34  2   5-m+w       nv....z. .
BIT $1234        abs        2C  3   5-m         nv....z. .
BIT $1234,X      abs,X      3C  3   6-m-x+x*p   nv....z. .
```

Tests the operand against the Accumulator. The ALU does an AND
operation internally, setting **z** if the result is 0.

When **m**=1, **n** and **v** are set based on the value of bits 7 and 6 in
memory.

When **m**=0, **n** and **v** are set based on the value of bits 15 and 14 in
memory.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### BMI

**Branch on Minus**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
BMI LABEL        rel8       30  2   2+t+t*e*p   ........ .
```

Jumps to the specified address when the Negative flag (**n**) is set.

**n** is set when ALU operations result in a negative number, or when the high bit
of an ALU operation is 1.

A branch operation uses an 8 bit signed value internally, starting from the
instruction after the branch. So the branch destination can be 126 bytes before
or 128 bytes after the branch instruction.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### BNE

**Branch on Not Equal.**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
BNE LABEL        rel8       D0  2   2+t+t*e*p   ........ .
```

Jumps to the target address when the Zero flag is 0. While this is most commonly
used after a compare (CMP) operation, it's also useful to test if a number is
zero after a Load operation, or to test if a loop is complete after a DEC
operation.

A branch operation uses an 8 bit signed value internally, starting from the
instruction after the branch. So the branch destination can be 126 bytes before
or 128 bytes after the branch instruction.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### BPL

**Branch on Plus**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
BPL LABEL        rel8       10  2   2+t+t*e*p   ........ .
```

Jumps to the specified address when the Negative flag (**n**) is clear.

**n** is clear when ALU operations result in a positive number, or when the high bit
of an ALU operation is 0.

A branch operation uses an 8 bit signed value internally, starting from the
instruction after the branch. So the branch destination can be 126 bytes before
or 128 bytes after the branch instruction.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### BRA

**Branch Always**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
BRA LABEL        rel8       80  2   3+e*p       ........ .
```

Jumps to the specified address.

A branch operation uses an 8 bit signed value internally, starting from the
instruction after the branch. So the branch destination can be 126 bytes before
or 128 bytes after the branch instruction.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### BRK

**Break**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
BRK #$20         imm        00  1   8-e         ....di.. .
```

Perform a break interrupt. The exact behavior changes slightly, based on whether
the CPU is in native or emulation mode. (e is 1 in emulation mode.)

Since the Program Counter is incremented

In emulation mode:

1. .PC (Program Counter) is incremented by 1 byte.
1. If the CPU is in Native mode, the Program Bank is pushed to the stack.
1. .PC is pushed onto the stack.
1. .P (flags) is pushed to the stack. (the **b** bit, bit 4, is set to 1.)
1. The **d** (Decimal) flag is cleared, forcing the CPU into binary mode.
1. The CPU reads the address from the IRQ vector at $FFFE and jumps there.

An IRQ is similar, except that IRQ clears bit 4 (**b**) during the push to the
stack. So an Interrupt Service Routine can read the last byte on the stack to
determine whether an emulation-mode interrupt is a BRK or IRQ.

On the X16, the IRQ services the keyboard, mouse, game pads, updates the clock,
blinks the cursor, and updates the LEDs.

In native mode:

1. .PC is incremented by 1 byte.
1. .X (Program Bank) is pushed the stack
1. .PC is pushed to the stack
1. .P (flags) is pushed to the stack
1. The **d** (Decimal) flag is cleared, forcing the CPU into binary mode.
1. The CPU reads the address from the BRK vector at $00FFE6 and jumps there.

Since the Native Mode has a distinct BRK vector, you do not need to query the
stack to dispatch a BRK vs IRQ interrupt. You can just handle each immediately.

The RTI instruction is used to return from an interrupt. It pulls the values
back off the stack (this varies, depending on the CPU mode) and returns to the
pushed PC address.

RTI

See the [Vectors](#vectors) section for the break vector.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### BRL

**Branch Long**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
BRL LABEL        rel16      82  3   4           ........ .
```

BRL is a 16 bit _branch_ instruction, meaning assembly creates a relative
address. Unlike BRA and the other branch instructions, BRL uses a 16-bit
address, which allows for an offset of -32768 to 32767 bytes away from the
instruction _following_ The BRL.

Of course, due to wrapping of the 64K bank, this means that the entire 64K
region is accessible. Values below 0 will simply wrap around and start from
\$FFFF, and values above \$FFFF will wrap around to 0.

Since this is a _relative_ branch, that means code assembled with BRL, instead of
JMP, can be moved around in memory without the need for re-assembly.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### BVC

**Branch on Overflow Clear**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
BVC LABEL        rel8       50  2   2+t+t*e*p   ........ .
```

Branches to the specified address when the Overflow bit is 0.

A branch operation uses an 8 bit signed value internally, starting from the
instruction after the branch. So the branch destination can be 126 bytes before
or 128 bytes after the branch instruction.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### BVS

**Branch on Overflow Set**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
BVS LABEL        rel8       70  2   2+t+t*e*p   ........ .
```

Branches to the specified address when the Overflow bit is 1.

A branch operation uses an 8 bit signed value internally, starting from the
instruction after the branch. So the branch destination can be 126 bytes before
or 128 bytes after the branch instruction.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### CLC

**Clear Carry**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
CLC              imp        18  1   2           .......c .
```

Clears the Carry bit in the flags. You'll usually use CLC before addition and
SEC before subtraction. You'll also want to use CLC or SEC appropriately before
calling certain KERNAL routines that use the **c** bit as an input value.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### CLD

**Clear Decimal**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
CLD              imp        D8  1   2           ....d... .
```

Clears the Decimal flag, returning the CPU to 8-bit or 16-bit binary operation.

When Decimal is set, the CPU will store numbers in Binary Coded Decimal format.
Clearing this flag restores the CPU to binary operation. See
[Decimal Mode](#decimal-mode) for more information.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### CLI

**Clear Interrupt Flag**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
CLI              imp        58  1   2           .....i.. .
```

Clears the **i** flag, _allowing interrupts to be handled_.

The **i** flag operates somewhat non-intuitively: when **i** is set (1), IRQ is
suppressed. When **i** is clear (0), interrupts are handled. So CLI _allows_
interrupts to be handled.

See [BRK}(#brk) for more information on interrupt handling.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### CLV

**Clear Overflow**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
CLV              imp        B8  1   2           .v...... .
```

Overflow is _set_ when the result of an addition operation goes up through \$80
or subtraction goes down through \$80.

CLV clears the overflow flag. There is no "SEV" instruction, but overflow can be
set with SEP #$40.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### CMP

**Compare**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
CMP #$20/#$1234  imm        C9  3-m 3-m         n.....zc .
CMP $20          dir        C5  2   4-m+w       n.....zc .
CMP $20,X        dir,X      D5  2   5-m+w       n.....zc .
CMP $20,S        stk,S      C3  2   5-m         n.....zc .
CMP $1234        abs        CD  3   5-m         n.....zc .
CMP $1234,X      abs,X      DD  3   6-m-x+x*p   n.....zc .
CMP $1234,Y      abs,Y      D9  3   6-m-x+x*p   n.....zc .
CMP $FEDBCA      long       CF  4   6-m         n.....zc .
CMP $FEDCBA,X    long,X     DF  4   6-m         n.....zc .
CMP ($20)        (dir)      D2  2   6-m+w       n.....zc .
CMP ($20),Y      (dir),Y    D1  2   7-m+w-x+x*p n.....zc .
CMP ($20,X)      (dir,X)    C1  2   7-m+w       n.....zc .
CMP ($20,S),Y    (stk,S),Y  D3  2   8-m         n.....zc .
CMP [$20]        [dir]      C7  2   7-m+w       n.....zc .
CMP [$20],Y      [dir],Y    D7  2   7-m+w       n.....zc .
```

Compares the Accumulator with memory. This performs a subtract operation
between .A and the operand and sets the **n**, **z**, and **c** flags based on
the result. The Accumulator is not altered.

* WHen A = Operand, **z** is set.
* When A < Operand, **c** is clear.
* When A <> Operand, **z** is clear.
* When A >= Operand, **c** is set.

You can use the Branch instructions (BEQ, BNE, BPL, BMI, BCC, BCS) to jump to
different parts of your program based on the results of CMP. Here are some BASIC
comparisons and the equivalent assembly language steps.

```asm65816
; IF A = N THEN 1000
CMP N
BEQ $1000

; IF A <> N THEN 1000
CMP N
BNE $1000

; IF A < N THEN 1000
CMP N
BCC $1000

; IF A >= N THEN 1000
CMP N
BCS $1000

; IF A > N THEN 1000
CMP N
BEQ skip
BCS $1000
skip:

; IF A <= N THEN 1000
CMP N
BEQ $1000
BCC $1000
```

As you can see, some comparisons will require two distinct branch instructions.

Also, note that the Branch instructions (except BRL) require that the target
address be within 128 bytes of the instruction after the branch. If you need to
branch further, the usual method is to invert the branch instruction and use a
JMP to take the branch.

For example, the following two branches behave the same, but the second one can
jump to any address on the computer, whereas the first can only jump -128/+127
bytes away:

```asm65816
short_branch:
CMP N
BEQ target

longer_branch:
CMP N
BNE skip
JMP target
skip:
```


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### COP

**COP interrupt.**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
COP #$20         imm        02  2   8-e         ....di.. .
```

COP is similar to BRK, but uses the FFE4 or FFF4 vectors. The intent is to COP
is to switch to a Co-Processor, but this can be used for any purpose on the X16
(including triggering a DMA controller, if that's what you want to do.)


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### CPX

**Compare X Register**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
CPX #$20/#$1234  imm        E0  3-x 3-x         n.....zc .
CPX $20          dir        E4  2   4-x+w       n.....zc .
CPX $1234        abs        EC  3   5-x         n.....zc .
```

This compares the X register to an operand and sets the flags accordingly.

See [CMP](#cmp) for more information.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### CPY

**Compare Y Register**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
CPY #$20/#$1234  imm        C0  3-x 3-x         n.....zc .
CPY $20          dir        C4  2   4-x+w       n.....zc .
CPY $1234        abs        CC  3   5-x         n.....zc .
```

This compares the Y register to an operand and sets the flags accordingly.

See [CMP](#cmp) for more information.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### DEC

**Decrement**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
DEC              acc        3A  1   2           n.....z. .
DEC $20          dir        C6  2   7-2*m+w     n.....z. .
DEC $20,X        dir,X      D6  2   8-2*m+w     n.....z. .
DEC $1234        abs        CE  3   8-2*m       n.....z. .
DEC $1234,X      abs,X      DE  3   9-2*m       n.....z. .
```

Decrement .A or memory. The **z** flag is set when the value reaches zero. This
makes DEC, DEX, and DEY useful as a loop counter, by setting the number of
iterations, the repeated operation, then DEX followed by BNE.

**z** is set when the counter reaches zero.
**n** is set when the high bit gets set.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### DEX

**Decrement .X**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
DEX              imp        CA  1   2           n.....z. .
```

Decrement .X The **z** flag is set when the value reaches zero. This
makes DEC, DEX, and DEY useful as a loop counter, by setting the number of
iterations, the repeated operation, then DEX followed by BNE.

**z** is set when the counter reaches zero.
**n** is set when the high bit gets set.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### DEY

**Decrement .Y**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
DEY              imp        88  1   2           n.....z. .
```

Decrement .X The **z** flag is set when the value reaches zero. This
makes DEC, DEX, and DEY useful as a loop counter, by setting the number of
iterations, the repeated operation, then DEX followed by BNE.

**z** is set when the counter reaches zero.
**n** is set when the high bit gets set.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### EOR

**Exclusive OR**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
EOR #$20/#$1234  imm        49  3-m 3-m         n.....z. .
EOR $20          dir        45  2   4-m+w       n.....z. .
EOR $20,X        dir,X      55  2   5-m+w       n.....z. .
EOR $20,S        stk,S      43  2   5-m         n.....z. .
EOR $1234        abs        4D  3   5-m         n.....z. .
EOR $1234,X      abs,X      5D  3   6-m-x+x*p   n.....z. .
EOR $1234,Y      abs,Y      59  3   6-m-x+x*p   n.....z. .
EOR $FEDBCA      long       4F  4   6-m         n.....z. .
EOR $FEDCBA,X    long,X     5F  4   6-m         n.....z. .
EOR ($20)        (dir)      52  2   6-m+w       n.....z. .
EOR ($20),Y      (dir),Y    51  2   7-m+w-x+x*p n.....z. .
EOR ($20,X)      (dir,X)    41  2   7-m+w       n.....z. .
EOR ($20,S),Y    (stk,S),Y  53  2   8-m         n.....z. .
EOR [$20]        [dir]      47  2   7-m+w       n.....z. .
EOR [$20],Y      [dir],Y    57  2   7-m+w       n.....z. .
```

Perform an Exclusive OR operation with the operand and .A

EOR compares each bit of the operands and sets the result bit to 1 if one of the
two bits is 1. If both bits are 1, the result is 0. If both bits are 0, the
result is 0.

EOR is useful for _inverting_ the bits in a byte. `EOR #$FF` will flip an entire
byte. (This will always flip the low byte in .A. To flip both bytes when **m**
is 0, you would use `EOR #$FFFF`.)

Truth table for EOR:

```text
Operand 1: 1100
Operand 2: 1010
Result:    0110
```


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### INC

**Increment**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
INC              acc        1A  1   2           n.....z. .
INC $20          dir        E6  2   7-2*m+w     n.....z. .
INC $20,X        dir,X      F6  2   8-2*m+w     n.....z. .
INC $1234        abs        EE  3   8-2*m       n.....z. .
INC $1234,X      abs,X      FE  3   9-2*m       n.....z. .
```

Increment .A or memory

Adds 1 to the value in .A or the specified memory address. The **n** and **z**
flags are set, based on the resultant value.

INC is useful for reading strings and operating on large areas of memory,
especially with indirect and indexed addressing modes.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### INX

**Increment .X**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
INX              imp        E8  1   2           n.....z. .
```

Increment the X register.

The following routine prints a null-terminated string (**a** should be 1.)

```asm65816
LDX #$0
loop:
LDA string_addr, X
BEQ done
JSR CHROUT
INX
BRA loop
done:
```

See [INC}(#inc)


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### INY

**Increment .Y**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
INY              imp        C8  1   2           n.....z. .
```

Increment the Y register.

See [INC}(#inc)


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### JMP

**Jump**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
JMP $2034        abs        4C  3   3           ........ .
JMP ($2034)      (abs)      6C  3   5           ........ .
JMP ($2034,X)    (abs,X)    7C  3   6           ........ .
```

Jump to a different address in memory, continuing program execution at the
specified address.

Instructions like `JMP ($1234,X)` make it possible to branch to a selectable
subroutine by setting X to the index into the vector table.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### JML

**Jump Long**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
JML $FEDCBA      long       5C  4   4           ........ .
JMP [$2034]      [abs]      DC  3   6           ........ .
```

Jump to a different address in memory, continuing program execution at the
specified address. JML accepts a 24-bit address, allowing the program to change
program banks.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### JSL

**Jmp to Subroutine Long**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
JSL $203456      long       22  4   8           ........ .
```

This is a 24-bit instruction, which can jump to a subroutine located in another
program bank.

Use the [RTL](#rtl) instruction to return to the instruction following the JSL.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### JSR

**Jump to Subroutine**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
JSR $2034        abs        20  3   6           ........ .
JSR ($2034,X)    (abs,X)    FC  3   8           ........ .
```

Jumps to a new operating address in memory. Also pushes the return address to
the stack, allowing an RTS instruction to pick up at the address following the
JSR.

The [RTS](#rts) instruction returns to the instruction following JSR.

The actual address pushed to the stack is the _before_ the next instruction.
This means that the CPU still needs to increment the PC by 1 step during the
RTS.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### LDA

**Load Accumulator**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
LDA #$20/#$1234  imm        A9  3-m 3-m         n.....z. .
LDA $20          dir        A5  2   4-m+w       n.....z. .
LDA $20,X        dir,X      B5  2   5-m+w       n.....z. .
LDA $20,S        stk,S      A3  2   5-m         n.....z. .
LDA $1234        abs        AD  3   5-m         n.....z. .
LDA $1234,X      abs,X      BD  3   6-m-x+x*p   n.....z. .
LDA $1234,Y      abs,Y      B9  3   6-m-x+x*p   n.....z. .
LDA $FEDBCA      long       AF  4   6-m         n.....z. .
LDA $FEDCBA,X    long,X     BF  4   6-m         n.....z. .
LDA ($20)        (dir)      B2  2   6-m+w       n.....z. .
LDA ($20),Y      (dir),Y    B1  2   7-m+w-x+x*p n.....z. .
LDA ($20,X)      (dir,X)    A1  2   7-m+w       n.....z. .
LDA ($20,S),Y    (stk,S),Y  B3  2   8-m         n.....z. .
LDA [$20]        [dir]      A7  2   7-m+w       n.....z. .
LDA [$20],Y      [dir],Y    B7  2   7-m+w       n.....z. .
```

Reads a value from memory into .A. This sets **n** and **z** appropriately,
allowing you to use BMI, BPL, BEQ, and BNE to act based on the value being read.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### LDX

**Load X Register**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
LDX #$20/#$1234  imm        A2  3-x 3-x         n.....z. .
LDX $20          dir        A6  2   4-x+w       n.....z. .
LDX $20,Y        dir,Y      B6  2   5-x+w       n.....z. .
LDX $1234        abs        AE  3   5-x         n.....z. .
LDX $1234,Y      abs,Y      BE  3   6-2*x+x*p   n.....z. .
```

Read a value into .X. This sets **n** and **z** appropriately, allowing you to
use BMI, BPL, BEQ, and BNE to act based on the value being read.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### LDY

**Load X Register**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
LDY #$20/#$1234  imm        A0  3-x 3-x         n.....z. .
LDY $20          dir        A4  2   4-x+w       n.....z. .
LDY $20,X        dir,X      B4  2   5-x+w       n.....z. .
LDY $1234        abs        AC  3   5-x         n.....z. .
LDY $1234,X      abs,X      BC  3   6-2*x+x*p   n.....z. .
```

Read a value into .Y. This sets **n** and **z** appropriately, allowing you to
use BMI, BPL, BEQ, and BNE to act based on the value being read.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### LSR

**Logical Shift Right**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
LSR              acc        4A  1   2           n.....zc .
LSR $20          dir        46  2   7-2*m+w     n.....zc .
LSR $20,X        dir,X      56  2   8-2*m+w     n.....zc .
LSR $1234        abs        4E  3   8-2*m       n.....zc .
LSR $1234,X      abs,X      5E  3   9-2*m       n.....zc .
```

Shifts all bits to the right by one position.

Bit 0 is shifted into Carry.;
0 shifted into the high bit (7 or 15, depending on the **m** flag.)

**Similar instructions:**;
[ASL](#asl) is the opposite instruction, shifting to the left.;
[ROR](#ror) rotates bit 0 through Carry to bit 7.;

+p Adds a cycle if ,X crosses a page boundary.;
+c New for the 65C02;


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### MVN

**Block Copy/Move Negative**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
MVN #$20,#$34    src,dest   54  3   7           ........ .
```

This performs a block copy. Use MVN when the source and destination ranges
overlap and dest < source.

Copying anything other than page zero requires 16-bit index registers, so it's
wise to clear **m** and **x** with `REP #$30`.

* Set .X to the source address
* Set .Y to the destination address
* Set .A to size-1
* MVN #source_bank, #dest_bank


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### MVP

**Block Copy/Move Positive**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
MVP #$20,#$34    src,dest   44  3   7           ........ .
```

This performs a block copy. Use MVP when the source and destination ranges
overlap and dest > source.

Copying anything other than page zero requires 16-bit index registers, so it's
wise to clear **m** and **x** with `REP #$30`.

* Set .X to the source_address + size - 1
* Set .Y to the destination_address
* Set .A to size-1
* MVP #source_bank, #dest_bank


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### NOP

**No Operation**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
NOP              imp        EA  1   2           ........ .
```

The CPU performs no operation. This is useful when blocking out instructions, or
reserving space for later use.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### ORA

**Boolean OR**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
ORA #$20/#$1234  imm        09  3-m 3-m         n.....z. .
ORA $20          dir        05  2   4-m+w       n.....z. .
ORA $20,X        dir,X      15  2   5-m+w       n.....z. .
ORA $20,S        stk,S      03  2   5-m         n.....z. .
ORA $1234        abs        0D  3   5-m         n.....z. .
ORA $1234,X      abs,X      1D  3   6-m-x+x*p   n.....z. .
ORA $1234,Y      abs,Y      19  3   6-m-x+x*p   n.....z. .
ORA $FEDBCA      long       0F  4   6-m         n.....z. .
ORA $FEDCBA,X    long,X     1F  4   6-m         n.....z. .
ORA ($20)        (dir)      12  2   6-m+w       n.....z. .
ORA ($20),Y      (dir),Y    11  2   7-m+w-x+x*p n.....z. .
ORA ($20,X)      (dir,X)    01  2   7-m+w       n.....z. .
ORA ($20,S),Y    (stk,S),Y  13  2   8-m         n.....z. .
ORA [$20]        [dir]      07  2   7-m+w       n.....z. .
ORA [$20],Y      [dir],Y    17  2   7-m+w       n.....z. .
```

Perform a Boolean OR operation with the operand and .A

ORA compares each bit of the operands and sets the result bit to 1 if either or
both of the two bits is 1. If both bits are 0, the result is 0.

ORA is useful for *setting* a specific bit in a byte.

Truth table for ORA:

```text
Operand 1: 1100
Operand 2: 1010
Result:    1110
```


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### PEA

**Push Absolute**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
PEA $2034        abs        F4  3   5           ........ .
```

PEA, PEI, and PER push values to the stack *without* affecting registers.

PEA pushes the operand value onto the stack. The literal operand is used, rather
than an address.

This seems inconsistent with the absolute address syntax, as PEA and PEI follow
their own syntax rules.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### PEI

**Push Effective Indirect Address**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
PEI ($20)        (dir)      D4  2   6+w         ........ .
```

PEI takes a _pointer_ as an operand. The value written to the stack is the two
bytes at the supplied address.

Example:
```
; data at $20 is $1234
PEI ($20)
; pushes $1234 onto the stack.
```

The written form of PEI is inconsistent with the usual indirect mode syntax, as
PEI and PEA follow their own syntax rules.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### PER

**Push Effective PC Relative Indirect Address**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
PER LABEL        rel16      62  3   6           ........ .
```

PER pushes the address _relative to the program counter_. This allows you to
mark the current executing location and push that to the stack.

When used in conjunction with BRL, PER can form a relocatable JSR instruction.

Consider the following ca65 macro:

```asm65816
.macro bsr addr
per .loword(:+ - 1)
brl addr
:
.endmacro
```

This gets the address following the BRL instruction and pushes that to the
stack. See [JSR](#jsr) to understand why the -1 is required.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### PHA

**Push Accumulator**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
PHA              imp        48  1   4-m         ........ .
```

Pushes the Accumulator to the stack. This will push 1 byte when **m** is 1 and
two bytes when **m** is 0 (16-bit memory/.A mode.)

An 8-bit stack push writes data at the Stack Pointer address, then moves SP down
by 1 byte.

A 16-bit push writes the high byte first, decrements the PC, then writes the low
byte, and decrements the PC again.

In Emulation mode, the Stack Pointer will always be an address in the \$100-\$1FF
range, so there is only room for 256 bytes on the stack. In native mode, the
stack can be anywhere in the first 64KB of RAM.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### PHB

**Push Data Bank register.**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
PHB              imp        8B  1   3           ........ .
```

The data bank register sets the top 8 bits used when reading data with LDA, LDX,
and LDY.

This is always an 8-bit operation.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### PHD

**Push Direct Page**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
PHD              imp        0B  1   4           ........ .
```

Pushes the 16-bit Direct Page register to the stack. This is useful for
preserving the location of .D before relocating Direct Page for another use
(such as an operating system routine.)


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### PHK

**Push Program Bank**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
PHK              imp        4B  1   3           ........ .
```

Pushes the Program Bank register to the stack. The Program Bank is the top 8
bits of the 24-bit Program Counter address.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### PHP

**Push Program Status (Flags)**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
PHP              imp        08  1   3           ........ .
```

The CPU writes the flags in the order `nvmx dizc`. (**e** does
not get written to the stack.)

Note: the 6502 and 65C02 use bit 4 (**x** on the '816) for the Break flag. While
**b** does get written to the stack in a BRK operation, bit 4 in .P always
reflects the state of the 8-bit-index flag. Since the flags differ slightly in
behavior, make sure your Interrupt handler code reads from the stack, not the .P
bits, when dispatching an IRQ/BRK interrupt.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### PHX

**Push X Register**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
PHX              imp        DA  1   4-x         ........ .
```

Pushes the X register to the stack. This will push 1 byte when **x** is 1 and
two bytes when **x** is 0 (16-bit index mode.)

An 8-bit stack push writes data at the Stack Pointer address, then moves SP down
by 1 byte. A 16-bit stack push moves the stack pointer down 2 bytes.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### PHY

**Push Y Register**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
PHY              imp        5A  1   4-x         ........ .
```

Pushes the Y register to the stack. This will push 1 byte when **y** is 1 and
two bytes when **y** is 0 (16-bit index mode.)

An 8-bit stack push writes data at the Stack Pointer address, then moves SP down
by 1 byte. A 16-bit stack push moves the stack pointer down 2 bytes.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### PLA

**Pull Accumulator**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
PLA              imp        68  1   5-m         n.....z. .
```

Pulls the Accumulator from the stack.

In the opposite of PHA, the PLA instruction reads the current value from the
stack and _increments_ the stack pointer by 1 or 2 bytes.

The number of bytes read is based on the value of the **m** flag.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### PLB

**Pull Data Bank Register**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
PLB              imp        AB  1   4           n.....z. .
```

Pull the Data Bank register from the stack.

In the opposite of PHB, the PLB instruction reads the current value from the
stack and _increments_ the stack pointer by 1 byte.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### PLD

**Pull Direct Page Register**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
PLD              imp        2B  1   5           n.....z. .
```

This pulls a word from the stack and loads it into the Direct Page register.

That value can be placed on the stack in several ways, such as PHA, PHX, or PEA.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### PLP

**Pull Program Status Byte (flags)**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
PLP              imp        28  1   4           nvmxdizc .
```

This reads the flags back from the stack. Since the flags affect the state of
the **m** and **x** register-width flags, this should be performed *before* a
PLA, PLX, or PLY operation.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### PLX

**Pull X Register**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
PLX              imp        FA  1   5-x         n.....z. .
```

Pulls the X Register from the stack.

In the opposite of PHX, the PLX instruction reads the current value from the
stack and _increments_ the stack pointer by 1 or 2 bytes.

The number of bytes read is based on the value of the **x** flag.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### PLY

**Pull Y Register**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
PLY              imp        7A  1   5-x         n.....z. .
```

Pulls the Y Register from the stack.

In the opposite of PHY, the PLY instruction reads the current value from the
stack and _increments_ the stack pointer by 1 or 2 bytes.

The number of bytes read is based on the value of the **x** flag.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### REP

**Reset Program Status Bit**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
REP #$20/#$1234  imm        C2  2   3           nvmxdizc .
```

This clears (to 0) flags in the Program Status Byte. The 1 bit will be
cleared in the flags, so REP #$30 will set the **a** and **x** bits low.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### ROL

**Rotate Left**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
ROL              acc        2A  1   2           n.....zc .
ROL $20          dir        26  2   7-2*m+w     n.....zc .
ROL $20,X        dir,X      36  2   8-2*m+w     n.....zc .
ROL $1234        abs        2E  3   8-2*m       n.....zc .
ROL $1234,X      abs,X      3E  3   9-2*m       n.....zc .
```

Shifts bits in the accumulator or memory left one bit. The Carry bit (**c**) is
shifted into bit 0. The high bit (7 or 15) is shifted into **c**.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### ROR

**Rotate Right**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
ROR              acc        6A  1   2           n.....zc .
ROR $20          dir        66  2   7-2*m+w     n.....zc .
ROR $20,X        dir,X      76  2   8-2*m+w     n.....zc .
ROR $1234        abs        6E  3   8-2*m       n.....zc .
ROR $1234,X      abs,X      7E  3   9-2*m       n.....zc .
```

Shifts bits in the accumulator or memory right one bit. The Carry bit (**c**) is
shifted into the high bit (15 or 7). The low bit (0) is shifted into **c**.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### RTI

**Return From Interrupt**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
RTI              imp        40  1   7-e         nvmxdizc .
```

This returns control to the executing program. The following steps happen, in
order:

1. The CPU pulls the flags from the stack (including **m** and **x**, which
switch to 8/16 bit mode, as appropriate.
2. The CPU pulls the Program Counter from the stack.
3. If the CPU is in native mode, the CPU pulls the Program Bank register.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### RTL

**Return From Subroutine Long**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
RTL              imp        6B  1   6           ........ .
```

This returns to the caller at the end of a subroutine. This should be used to
return to the instruction following a [JSL](#jsl) instruction.

This reads 3 bytes from the stack and loads them into the Program Counter and
Program Bank register. The next instruction executed will then be the
instruction after the JSL that jumped to the subroutine.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### RTS

**Return From Subroutine**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
RTS              imp        60  1   6           ........ .
```

Return to a calling routine after a [JSR](#jsr).

RTS reads a 2 byte address from the stack and loads that address into the
Program Counter. The next instruction executed will then be the
instruction after the JSR that jumped to the subroutine.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### SBC

**Subtract With Carry**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
SBC #$20/#$1234  imm        E9  3-m 3-m         nv....zc .
SBC $20          dir        E5  2   4-m+w       nv....zc .
SBC $20,X        dir,X      F5  2   5-m+w       nv....zc .
SBC $20,S        stk,S      E3  2   5-m         nv....zc .
SBC $1234        abs        ED  3   5-m         nv....zc .
SBC $1234,X      abs,X      FD  3   6-m-x+x*p   nv....zc .
SBC $1234,Y      abs,Y      F9  3   6-m-x+x*p   nv....zc .
SBC $FEDBCA      long       EF  4   6-m         nv....zc .
SBC $FEDCBA,X    long,X     FF  4   6-m         nv....zc .
SBC ($20)        (dir)      F2  2   6-m+w       nv....zc .
SBC ($20),Y      (dir),Y    F1  2   7-m+w-x+x*p nv....zc .
SBC ($20,X)      (dir,X)    E1  2   7-m+w       nv....zc .
SBC ($20,S),Y    (stk,S),Y  F3  2   8-m         nv....zc .
SBC [$20]        [dir]      E7  2   7-m+w       nv....zc .
SBC [$20],Y      [dir],Y    F7  2   7-m+w       nv....zc .
```

Subtract a value from .A. The result is left in .A.

When performing subtraction, the Carry bit indicates a Borrow and operates in
reverse from addition: when **c** is 0, SBC subtracts one from the final result,
to account for the borrow.

After the operation, **c** will be set to 0 if a borrow took place and 1 if it
did not.

When **m** is 0, this will be a 16 bit add, and the CPU will read two bytes from
memory.

Since there is no "subtract with no carry", you should always use SEC before the
first SBC in a sequence, to ensure that the Carry bit is _set_, going into a
subtraction.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### SEC

**Set Carry**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
SEC              imp        38  1   2           .......c .
```

Sets the Carry bit to 1


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### SED

**Set Decimal**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
SED              imp        F8  1   2           ....d... .
```

Sets the Decimal bit to 1, setting the CPU to BCD mode.

When Decimal is set, the CPU will store numbers in Binary Coded Decimal format.
Clearing this flag restores the CPU to binary operation. See
[Decimal Mode](#decimal-mode) for more information.

In binary mode, adding 1 to \$09 will set the Accumulator to \$0A. In BCD mode,
adding 1 to \$09 will set the Accumulator to \$10.

Using BCD allows for easier conversion of binary numbers to decimal. BCD also
allows for storing decimal numbers without loss of precision due to power-of-2
rounding.

An add or subtract (ADC or SBC) is required to actually trigger BCD conversion.
So if you have a number like \$1A on the accumulator and you SED, you can convert
.A to \$20 with the instruction `ADC #$00`.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### SEI

**Set IRQ Disable**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
SEI              imp        78  1   2           .....i.. .
```

Sets **i**, which inhibits IRQ handling. When **i** is set, the CPU will not
respond to the IRQ pin. When **i** is clear, the CPU will perform an interrupt
when the IRQ pin is asserted.

The **i** flag operates somewhat non-intuitively: when **i** is set (1), IRQ is
suppressed. When **i** is clear (0), interrupts are handled. So CLI _allows_
interrupts to be handled and SEI _blocks_ interrupt handling.

See [BRK](#brk) for a brief description of interrupts.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### SEP

**Set Processor Status Bit**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
SEP #$20/#$1234  imm        E2  2   3           nvmxdizc .
```

Reset Program Status Bit

This sets (to 1) a flag in the Program Status Byte. The operand value will be
loaded into the flags, so SEP #$30 will set the **a** and **x** bits high.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### STA

**Store Accumulator to Memory**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
STA $20          dir        85  2   4-m+w       ........ .
STA $20,X        dir,X      95  2   5-m+w       ........ .
STA $20,S        stk,S      83  2   5-m         ........ .
STA $1234        abs        8D  3   5-m         ........ .
STA $1234,X      abs,X      9D  3   6-m         ........ .
STA $1234,Y      abs,Y      99  3   6-m         ........ .
STA $FEDBCA      long       8F  4   6-m         ........ .
STA $FEDCBA,X    long,X     9F  4   6-m         ........ .
STA ($20)        (dir)      92  2   6-m+w       ........ .
STA ($20),Y      (dir),Y    91  2   7-m+w       ........ .
STA ($20,X)      (dir,X)    81  2   7-m+w       ........ .
STA ($20,S),Y    (stk,S),Y  93  2   8-m         ........ .
STA [$20]        [dir]      87  2   7-m+w       ........ .
STA [$20],Y      [dir],Y    97  2   7-m+w       ........ .
```

Stores the value in .A to a memory address.

When **m** is 0, the value saved will be a 16-bit number, using two bytes of
memory. When **m** is 1, the value will be an 8-bit number, using one byte of
RAM.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### STP

**Stop the Clock**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
STP              imp        DB  1   3           ........ .
```

Halts the CPU. The CPU will no longer process instructions until the Reset pin
is asserted.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### STX

**Store Index X to Memory**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
STX $20          dir        86  2   4-x+w       ........ .
STX $20,Y        dir,Y      96  2   5-x+w       ........ .
STX $1234        abs        8E  3   5-x         ........ .
```

Stores the value in .X to a memory address.

When the flag **x** is 0, the value saved will be a 16-bit number, using two
bytes of memory. When **x** is 1, the value will be an 8-bit number, using one
byte of RAM.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### STY

**Store Index Y to Memory**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
STY $20          dir        84  2   4-x+w       ........ .
STY $20,X        dir,X      94  2   5-x+w       ........ .
STY $1234        abs        8C  3   5-x         ........ .
```

Stores the value in .Y to a memory address.

When the flag **x** is 0, the value saved will be a 16-bit number, using two
bytes of memory. When **x** is 1, the value will be an 8-bit number, using one
byte of RAM.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### STZ

**Store Zero to Memory**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
STZ $20          dir        64  2   4-m+w       ........ .
STZ $20,X        dir,X      74  2   5-m+w       ........ .
STZ $1234        abs        9C  3   5-m         ........ .
STZ $1234,X      abs,X      9E  3   6-m         ........ .
```

Stores a zero to a memory address.

When **m** is 0, the value saved will be a 16-bit number, using two bytes of
memory. When **m** is 1, the value will be an 8-bit number, using one byte of
RAM.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### TAX

**Transfer Accumulator to Index X**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
TAX              imp        AA  1   2           n.....z. .
```

Copies the contents of .A to .X.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### TAY

**Transfer Accumulator to Index Y**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
TAY              imp        A8  1   2           n.....z. .
```

Copies the contents of .A to .Y.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### TCD

**Transfer C Accumulator to Direct Register**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
TCD              imp        5B  1   2           n.....z. .
```

This copies the 16-bit value from the 16-bit Accumulator to the Direct Register,
allowing you to relocate Direct Page anywhere in the first 64K of RAM.

This is one of the times that the 16-bit Accumulator is called .C, as it always
operates on a 16-bit value, regardless of the state of the **m** flag.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### TCS

**Transfer C Accumulator to Stack Pointer**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
TCS              imp        1B  1   2           ........ .
```

This copies the 16-bit value from the 16-bit Accumulator to the Stack Pointer,
allowing you to relocate the stack anywhere in the first 64K of RAM.

This is one of the times that the 16-bit Accumulator is called .C, as it always
operates on a 16-bit value, regardless of the state of the **m** flag.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### TDC

**Transfer Direct Register to C Accumulator**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
TDC              imp        7B  1   2           n.....z. .
```

Copies the value of the Direct Register to the Accumulator.

This is one of the times that the 16-bit Accumulator is called .C, as it always
operates on a 16-bit value, regardless of the state of the **m** flag.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### TRB

**Test and Reset Bit**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
TRB $20          dir        14  2   7-2*m+w     ......z. .
TRB $1234        abs        1C  3   8-2*m       ......z. .
```

TRB does two things with one operation: it tests specified bits in a memory
location, and it clears (resets) those bits after the test.

First, TRB performs a logical AND between the memory address specified and the
Accumulator. If the result of the AND is zero, the **z** flag will be set.

Second, TRB clears bits in the memory value based on the bit mask in the
accumulator. Any bit that is 1 in .A will be changed to 0 in memory.

So to _clear_ a bit in a memory value, set that value to 1 in .A, like this:

```
; memory at $2000 contains $84
LDA #$80
TRB $2000
; memory at $2000 now contains $04, and z flag is clear

; memory at $1234 contains $20
LDA #$01
TRB $1234
; memory at $1234 contains $20 and z flag is set
; because $20 AND $01 == 0.
```


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### TSB

**Test and Set Bit**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
TSB $20          dir        04  2   7-2*m+w     ......z. .
TSB $1234        abs        0C  3   8-2*m       ......z. .
```

TSB does two things with one operation: it tests specified bits in a memory
location, and it clears (resets) those bits after the test.

First, TSB performs a logical AND between the memory address specified and the
Accumulator. If the result of the AND is zero, the **z** flag will be set.

TSB also _sets_ the bits that are 1 in the accumulator, similar to an OR
operation.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### TSC

**Transfer Stack Pointer to C accumulator**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
TSC              imp        3B  1   2           n.....z. .
```

Copies the Stack Pointer to the 16-bit Accumulator.

This is one of the times that the 16-bit Accumulator is called .C, as it always
operates on a 16-bit value, regardless of the state of the **m** flag.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### TSX

**Transfer Stack Pointer X Register**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
TSX              imp        BA  1   2           n.....z. .
```

Copies the Stack Pointer to the X register.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### TXA

**Transfer X Register to Accumulator**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
TXA              imp        8A  1   2           n.....z. .
```

Copies the value in .X to .A


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### TXS

**Transfer X Register to Stack Pointer**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
TXS              imp        9A  1   2           ........ .
```

Copies the X register to the Stack Pointer. This is used to reset the stack to a
known location, usually at boot or when context-switching.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### TXY

**Transfer X Register to Accumulator**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
TXY              imp        9B  1   2           n.....z. .
```

Copies the value in .X to .Y


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### TYA

**Transfer Y Register to Accumulator**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
TYA              imp        98  1   2           n.....z. .
```

Copies the value in .Y to .A


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### TYX

**Transfer Y Register to X Register**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
TYX              imp        BB  1   2           n.....z. .
```

Copies the value in .Y to .X


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### WAI

**Wait For Interrupt**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
WAI              imp        CB  1   3           ........ .
```

Stops the CPU until the next interrupt is triggered. This allows the CPU to
respond to an interrupt immediately, rather than waiting for an instruction to
complete.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### WDM

**WDM**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
WDM              imm        42  2   2           ........ .
```

WDM is a 2 byte NOP: the WDM opcode and the operand byte following are both
read, but not executed.

The WDM opcode is reserved for future use and should be avoided in 65C816
programs.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### XBA

**Exchange B and A Accumulator**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
XBA              imp        EB  1   3           n.....z. .
```

Swaps the values in .A and .B. This exchanges the high and low bytes of the
Accumulator. XBA functions the same in both 8 and 16 bit modes.


[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---

#### XCE

**Exchange Carry and Emulation Flags**

```text
SYNTAX           MODE       HEX LEN CYCLES      FLAGS   
XCE              imp        FB  1   2           .......c e
```

This allows the CPU to switch between Native and Emulation modes.

To switch into native mode:

```asm65816
CLC
XCE
```

To switch to 65C02 emulation mode:

```asm65816
SEC
XCE
```

[[Opcodes](#instructions-by-opcode)] [[By Name](#instructions-by-name)] [[By Category](#instructions-by-category)]

---


<!-- For PDF formatting -->
<div class="page-break"></div>

# Appendix G: ZSM File Format

#### Zsound Repo

The Zsound suite of Commander X16 audio tools contains the original ZSM reference player, found at:  
https://github.com/ZeroByteOrg/zsound/

A newer, more flexible, and more recently maintained library with PCM support, ZSMKit, is available at:  
https://github.com/mooinglemur/ZSMKit/

#### Current ZSM Revision: 1

ZSM is a standard specifying both a data stream format and a file structure for containing the data stream. This document provides the standard for both the ZSM stream format and for the ZSM container file format.

Whenever it becomes necessary to modify the ZSM standard in such a way that existing software will not be compatible with files using the newer standard, this version number will be incremented, up to a maximum value of 254.

Version 255 (-1) is reserved for internal use by the player

#### Headerless Data File Format:

 Since Kernal version r39, it is possible to load data files that do not have the CBM 2-byte load-to-address header. As of version r41, this functionality is equally accessible in the standard interactive BASIC interface. As the "PRG" header is no longer necessary, ZSM files will NOT contain this header in order to appear as any other common data file such as ``.wav``, ``.png``, etc. As such, users and programs must use the "headerless mode" when loading a ZSM into memory on the Commander X16. The previously-suggested dummy PRG header has been incorporated to the ZSM header as a magic header for file identity verification purposes.


## ZSM file composition

 Offset|Length|Field
 --|--|--
 0x00|16|ZSM HEADER
 0x10|variable|ZSM STREAM
 ?|?|(optional) PCM HEADER
 ?|variable|(optional) PCM DATA

### ZSM Header

The ZSM header is 16 bytes long.

- All multi-byte values are little endian unless specified otherwise
- All offsets are relative to the beginning of the ZSM header

Offset|Length|Field|Description
---|---|---|---
0x00|2|Magic Header| The string 'zm' (binary 0x7a 0x6d)
0x02|1|Version| ZSM Version. 0-0xFE (0xFF is reserved)
0x03|3|Loop Point|Offset to the starting point of song loop. 0 = no loop.
0x06|3|PCM offset|Offset to the beginning of the PCM index table (if present). 0 = no PCM header or data is present.
0x09|1|FM channel mask|Bit 0-7 are set if the corresponding OPM channel is used by the music.
0x0a|2|PSG channel mask|Bits 0-15 are set if the corresponding PSG channel is used by the music.
0x0c|2|Tick Rate|The rate (in Hz) for song delay ticks. *60Hz (one tick per frame) is recommended.*
0x0e|2|reserved| Reserved for future use. Set to zero.


### ZSM Music Data Stream Format

Byte 0|Byte 1 (variable)|Byte n|Byte n+1 (variable)|...|End of stream
---|---|---|---|---|---
CMD|DATA|CMD|DATA|...|0x80

#### CMD (command) byte values
CMD bytes are bit-packed to hold a command Type ID and a value (n) as follows:

CMD|Bit Pattern|Type|Arg. Bytes|Action
---|--|--|--|-----
0x00-0x3F|`00nnnnnn`|PSG write|1  | Write the following byte into PSG register offset *n*. (from 0x1F9C0 in VRAM)
 0x40     |`01000000`|EXTCMD  |1+?| The following byte is an extension command. (see below for EXTCMD syntax)
 0x41-0x7F|`01nnnnnn`|FM write |2*n*  | Write the following *n* reg/val pairs into the YM2151.
0x80|`10000000`|EOF   |0  |This byte MUST be present at the end of the data stream. Player may loop or halt as necessary.
0x81-0xFF|`1nnnnnnn`|Delay   |0  |Delay *n* ticks.

#### EXTCMD:
The EXTCMD byte is formatted as `ccnnnnnn` where `c`=channel and `n`=number of bytes that follow. If the player wishes to ignore a channel, it can simply advance `n` bytes and continue processing. See EXTCMD Channel Specifications below for more details.

### PCM Header

If the PCM header exists in the ZSM file, it will immediately follow the 0x80 end-of-data marker. The PCM header exists only if at least one PCM instrument exists.

Since each instrument defined is 16 bytes, the size of the PCM header can be calculated
as 4+(16*(last_instrument_index+1)).

Offset|Type|Value
--|--|--
0x00-0x02|String|"PCM"
0x03|Byte|The last PCM instrument index
0x04-0x13|Mixed|Instrument definition for instrument 0x00
0x14-0x23|Mixed|(optional) Instrument definition for instrument 0x01
...

### Instrument definition
Offset|Type|Value
--|--|--
0x00|Byte|This instrument's index
0x01|Bitmask|AUDIO_CTRL: 00**DC**0000: D is set for 16-bit, and clear for 8-bit. C is set for stereo and clear for mono
0x02-0x04|24-bit int|Little-endian offset into the PCM data block
0x05-0x07|24-bit int|Little-endian length of PCM data
0x08|Bitmask|Features: **L**xxxxxxx: L is set if the sample is looped
0x09-0x0b|24-bit int|Little-endian loop point offset (relative, 0 is the beginning of this instrument's sample)
0x0c-0x0f|...|Reserved for expansion

Any offset values contained in the PCM data header block are relative to the beginning of the PCM sample data section, not to the PCM header or ZSM header. The intention is to present the digital audio portion as a set of digi clips ("samples" in tracker terminology) whose playback can be triggered by EXTCMD channel zero.

### PCM Sample Data

This is a blob of PCM data with no internal formatting. Offsets into this blob are provided via the PCM header. The end of this blob will be the end of the ZSM file.

## EXTCMD Channel Specifications

Extension commands provide optional functionality within a ZSM music file. EXTCMD may be ignored by any player. EXTCMD defines 4 "channels" of message streams. Players may implement support for any, all, or none of the channels as desired. An EXTCMD may specify up to 63 bytes of data. If more data than this is required, then it must be broken up into multiple EXTCMDs.

##### EXTCMD in ZSM stream context:

...|CMD 0x40|EXTCMD|N bytes|CMD|...
---|---|---|---|---|---

##### EXTCMD byte format:

Bit Pattern|C|N
--|--|--
`ccnnnnnn`|Extension Channel ID|Number of bytes that follow



##### EXTCMD Channels:
0. PCM instrument channel
1. Expansion Sound Devices
2. Synchronization events
3. Custom

The formatting of the data within these 4 channels is presently a work in progress. Definitions for channels 0-3 will be part of the official ZSM specifications and implemented in the Zsound library. Significant changes within one of these three channels' structure may result in a new ZSM version number being issued. The formatting and content of the 3 official EXTCMD channels will be covered here.

The Custom channel data may take whatever format is desired for any particular purpose with the understanding that the general ecosystem of ZSM-aware applications will most likely ignore them.

### EXTCMD Channel:
#### 0: PCM audio

This EXTCMD stream can contain one or more command + argument pairs.

command|meaning|argument|description
---|---|---|---
0x00|AUDIO_CTRL byte|byte|This byte sets PCM channel volume and/or clears the FIFO
0x01|AUDIO_RATE byte|byte|A value from 0x00-0x80 to set the sample rate (playback speed)
0x02|Instrument trigger|byte|Triggers the PCM instrument specified by this byte index

#### 1: Expansion Sound Devices

This channel is for data intended for "well-known" expansion hardware used with the Commander X16. As the community adopts various expansion hardware, such devices will be given a standard "ID" number so that all ZSM files will agree on which device is being referenced by expansion HW data.

The specification of new chip IDs should not affect the format of ZSM itself, and thus will not result in a ZSM version update. Players will simply need to update their list of known hardware.

Players implementing this channel should implement detection routines during init to determine which (if any) expansion hardware is present. Any messages intended for a chip that is not present in the system should be skipped.

An expansion HW write will contain the following data:

Chip ID|`nnnnnn-1` bytes of data
--|--
one byte|nnnnnn-1 bytes

- The length of the EXTCMD `nnnnnn` encompasses the chip_id byte and the data bytes which follow.

##### Chip IDs
* 0x00 - reserved
* 0x01 - MIDI 1 (Primary MIDI)
    * MIDI data embedded in ZSM is limited to status bytes 0x80-0xF8 inclusive, and their arguments, i.e. data which is intended to be transmitted to a synthesizer.
    * Metadata such as MIDI header data, ticks per beat, track names, lyrics, and tempo are not included in the data.
    * Delta times are not embedded in the MIDI data. Native ZSM delays are used instead.
    * With the exception of multiple EXTCMDs for the same Chip ID within the same tick, the first byte of data must be a status byte 0x80-0xF8.
    * Status continuation is not permitted from prior ticks, but is allowed within the same tick.
        * This restriction allows for simultaneous access to the MIDI device by multiple agents, such as a song player and sound effects player on non-overlapping MIDI channels.
    * An example of an EXTCMD containing a single note-on event might look as follows: `0x40 0x44 0x01 0x90 0x69 0x7F`
* 0x02 - MIDI 2 (Secondary MIDI)
    * A second separate MIDI stream can be used by players that support multiple active MIDI devices. The data format and restrictions are the same as for Chip ID 0x01.
* 0x03 - reserved
* 0x70-0x7F - Private use area
    * These will be ignored by the stock reference players, but can be used for testing or for custom purposes for a particular application.
* 0x80-0xFF - reserved for possible expansion to 15-bit chip IDs

#### 2: Synchronization Events

The purpose of this channel is to provide for music synchronization cues that applications may use to perform operations in sync with the music (such as when the Goombas jump in New Super Mario Bros in time with the BOP! BOP! notes in the music). It is intended for the reference player to provide a sync channel callback, passing the data bytes to the callback function, and then to proceed with playback.

The synchronization format currently defines these event types:

Event Type|Description|Message Format
--|--|--
`0x00`|Generic sync message|`xx` (any value from `0x00`-`0xff`)
`0x01`|Song tuning|a signed byte indicating an offset from A-440 tuning represented in 256ths of a semitone

An example of an EXTCMD containing one sync event might look as follows: `0x40 0x82 0x00 0x05`


#### 3: Custom

The purpose for this channel is that any project with an idea that does not fit neatly into the above categories may pack data into the project's music files in whatever form is required. It should be understood that these ZSMs will not be expected to use the extended behaviors outside of the project they were designed for. The music itself, however, should play properly. The only constraint is that the data must conform to the EXTCMD byte - supplying exactly the specified number of bytes per EXTCMD.

The reference playback library in Zsound will implement this channel as a simple callback passing the memory location and data size to the referenced function, and take no further action internally.

<!-- For PDF formatting -->
<div class="page-break"></div>



# Appendix H: How to update your X16 to latest release

These instructions will guide you how to update your X16 firmware from any previous version to the latest version. This guide will be updated once there are new releases. This guide is applicable for Gen 1 hardware, PRxxxxx boards.

## Table Of Contents

1. [Latest release](#latest-release)
2. [Requirements](#requirements)
3. [Update instructions](#update-instructions)
4. [Appendix: Release history](#appendix-release-history)
5. [Appendix: Stock version numbers](#appendix-stock-version-numbers)
6. [Appendix: How to downgrade from latest release to first release](#appendix-how-to-downgrade-from-latest-release-to-first-release)

## Latest release

| Firmware        | Version | Date       | Link                                                               |
|-----------------|---------|------------|--------------------------------------------------------------------|
| ROM             | R48     | 2024-09-06 | https://github.com/X16Community/x16-rom/releases/tag/r48           |
| SMC             | 48.0.0  | 2024-12-23 | https://github.com/X16Community/x16-smc/releases/tag/r48.0.0       |
| VERA            | 48.0.1  | 2025-01-08 | https://github.com/X16Community/vera-module/releases/tag/v48.0.1   |
| SMC bootloader  | 3       | 2024-09-13 | https://github.com/X16Community/x16-smc-bootloader/releases/tag/v3 |


## Requirements
| Property | Requirement            |
|----------|------------------------|
| Hardware | Gen 1 PRxxxxx board    |
| ROM      | Minimum version R43    |
| SMC      | Minimum version 43.0.0 |
| VERA     | No minimum version     |


## Update instructions


### Step 1: Note down your current ROM/SMC/VERA versions (recommended)

#### 1.1 ROM/SMC/VERA versions
Use the `HELP` command to see which versions you currently have.
You may want to take a picture of the screen or write it down, for future reference.

#### 1.2 SMC bootloader version
- Poll bootloader version with this command: `PRINT I2CPEEK($42,$8E)`
	- This should be 2 if you have a stock PR board. Note that if you have bootloader 3 it may incorrectly display as 255.
- If you have SMC version 47.2.3 or later, you can use the tool "SMCBLD7.PRG" inside [smc tools] (see step 3) to identify bootloader version based on its CRC-16 checksum, making this a more accurate bootloader test.
- Take a picture of the screen, for future reference.


### Step 2: Take a backup of what you have

#### 2.1 SD card (highly recommended)
- Plug SD card in your PC and make a backup of all files. In case SD card gets corrupted, damaged, or you loose your files otherwise.
- If needed, you can download the latest version of the SD card bundle here: https://github.com/cx16forum/sdcard

#### 2.2 ROM/SMC/VERA (optional)
- If you know your current version numbers (step 1), and do not care about rolling back, you can safely skip this step.
- If you like to preserve the history, and your version is not already archived, you may want to dump it before overwriting it.

<details><summary>CLICK FOR DETAILS</summary>
<p>

If your version is not archived (e.g. ROM prerelease), you may want to make a backup of this one (and give a heads-up on Discord, #kernel).
  - Dump tool for ROM/SMC/VERA/RTC: https://cx16forum.com/forum/viewtopic.php?p=34970
- Archive of official releases:
  - ROM: https://github.com/X16Community/x16-rom/releases/
  - SMC: https://github.com/X16Community/x16-smc/releases/
  - VERA: https://github.com/X16Community/vera-module/releases/
  - SMC bootloaders: https://github.com/X16Community/x16-smc-bootloader/releases
- Unofficial releases, known to have been delivered with some machines:
  - SMC 45.1.0: Dump: https://github.com/FlightControl-User/x16-flash/releases/download/r3.0.0/R45-BINS.zip
  - SMC bootloader v2(bad): Dump: Inside [bootloader tools] https://github.com/X16Community/x16-smc/pull/53#issuecomment-2362330198 / src: https://github.com/X16Community/x16-smc/pull/20
  - ROM R47 prerelease git 8929A57+: Dump: https://cx16forum.com/forum/viewtopic.php?p=31112 / src: X16Community/x16-rom#213 (exact source is ambiguous due to the +)
  - ROM R47 prerelease git 33ACE3A4: Dump: https://cx16forum.com/forum/viewtopic.php?p=31112 / src: X16Community/x16-rom#241
</p>
</details>

### Step 3: Download files and place on SD card

- BIN files and their associated programming tool must stay in the same folder
- Note that the x16-flash tool (UPDATE.PRG) will attempt to program both ROM, SMC and VERA if it finds associated .BIN files in its folder, so make sure that its folder only contains ROM.BIN

#### Suggested folder structure:
- UPDATE
	- VERA
		- FLASHVERA.PRG
		- VERA.BIN (downloaded file must be renamed to VERA.BIN)
	- ROM
		- UPDATE.PRG
		- ROM.BIN
	- SMC
		- SMCUPDATE-x.x.x.PRG (do not rename)
	- SMCTOOLS
		- SMCBLD7.PRG
		- SMCBLW19.PRG
		- BOOT3.BIN

To organize multiple ROM and VERA versions on the SD card, you may e.g. add folders with version numbers, and place firmware inside.

#### Downloads:
- VERA 48.0.1
	- https://github.com/X16Community/vera-module/releases/tag/v48.0.1
		- Download Assets -> VERA_48.0.1.BIN
    - https://github.com/mooinglemur/flashvera/releases/tag/v0.2
		- Download Assets -> FLASHVERA.PRG
- ROM R48
	- https://github.com/X16Community/x16-rom/releases/tag/r48
		- Download Assets -> Release.R48.ROM.Image.zip
			- Extract "rom.bin"
	- https://github.com/FlightControl-User/x16-flash/releases/tag/r3.0.0
		- Download Assets -> CX16-UPDATE-R3.0.0.PRG
- SMC 48.0.0
	- https://github.com/X16Community/x16-smc/releases/tag/r48.0.0
		- Download Assets -> X16-SMC_r48.0.0.zip
			- Extract "SMCUPDATE-48.0.0.PRG"
- SMC tools v6
	- https://github.com/X16Community/x16-smc/pull/53#issuecomment-2362330198
		- Download smc-flash-manipulation-6.zip
			- Extract files mentioned under SMCTOOLS above

#### Copy to SD card
- Prepare the folder structure on the SD card.
- Copy downloaded files to SD card, inside the folder structure mentioned above.
- Rename files as needed. Uppercase/lowercase is not important.

#### Navigating the file system on X16
- To list files in current folder, or change folder, you use the commands `DOS"$"` or `DOS"CD:folder"`.
- A shortcut is to use the `@` prefix, e.g. `@$` and `@CD:folder`
- To enter the VERA folder, you can e.g. use the command `@CD:/UPDATE/VERA`
- You can also navigate like this:

```
@CD:/UPDATE
@$
@CD:VERA
@$
```

### Step 4: Update VERA to 48.0.1
VERA have best backward compatibility, and should be flashed first.
- 48.0.1 supports at least ROM 47 prerelease, and probably older ROMs as well.
- Release page: https://github.com/X16Community/vera-module/releases/tag/v48.0.1
- Follow instructions on release page to program VERA.

```
@CD:/UPDATE/VERA
LOAD "FLASHVERA.PRG"
RUN
```

- After programming, restart machine and type `HELP` to verify VERA version.

### Step 5: Update ROM to R48
- Minimum SMC version: 43.0.0
- Minimum VERA version: 0.3.1
- You may follow this guide: https://github.com/FlightControl-User/x16-flash

```
@CD:/UPDATE/ROM
LOAD "UPDATE.PRG"
RUN
```

- Follow the instructions on screen.
- Note that the J1 jumper must be on, to allow ROM to be reprogrammed. Disconnect jumper after programming, to ensure ROM is write protected.
- Important: Only program ROM in this step, not VERA or SMC.


### Step 6: Update SMC to 48.0.0
- To update SMC, a little program on the SMC called "bootloader" is used to replace its main program.
- All PR boards up to ~900 seem to have been delivered with version 45.1.0, and with a bootloader which claims to be version 2, but, unfortunately, is a corrupt version of version 2 (also referred to as the "bad" bootloader). This have the consequence that, if you attempt to program, the x16 will hang at the end of programming. If you attempt to fix the hang problem by disconnecting power, and plug it back in, your SMC will be "bricked", and you cannot use your x16 until you disconnect the SMC and program it manually using an external programmer or Arduino [recovery-with-arduino].
- To update your SMC with bad bootloader, you have 2 options:
	- Option 1: Disconnect the SMC, connect to an external programmer, and install latest firmware https://github.com/X16Community/x16-smc/blob/main/doc/recovery-with-arduino.md
	- Option 2: Reset the SMC by shorting its reset pin to GND, using a jumper wire. Instruction: https://github.com/X16Community/x16-smc/blob/main/doc/update-with-bad-bootloader-v2.md
		- NB: If you plan to do option 2, ref the instructions, you should practice doing this reset while at the READY prompt. Once you get the hang of it, you can do it during programming. It is important that you get it correct at the critical moment when the SMC is hanging inside the bad bootloader.
- If you have a different SMC version than 45.1.0, you most likely do not have the bad bootloader.

#### Recommended install method, SMCUPDATE-48.0.0.PRG
- The recommended method to upgrade SMC to latest version 48.0.0, is to use an installer with version 48.0.0 bundled together with the installer.
- If there is a risk of having the bad v2 bootloader, have a jumper wire ready
- Load and run the installer
```
@CD:/UPDATE/SMC
LOAD "SMCUPDATE-48.0.0.PRG"
RUN
```
- Use the jumper wire if needed, ref the "update-with-bad-bootloader-v2.md" instructions

#### Alternative tools

<details><summary>CLICK FOR DETAILS</summary>
<p>

- The tool SMCUPDATE 2.0 allows you to specify a .hex file to install
	- This tool works with bootloader 2, but not with bootloader 3
	- Tool: https://github.com/stefan-b-jakobsson/x16-smc-update/releases/tag/2.0
	- When prompted for file name, enter "x16-smc.ino.hex"
- The tool x16-flash allows you to program the .bin file from the release page
	- This tool ignores bootloader version, and works with both v2 and v3
	- If bootloader version is 2, you cannot reprogram with the same version
	- This tool gives bad recommendation in the case of bad bootloader
	- Tool: https://github.com/FlightControl-User/x16-flash/releases/tag/r3.0.0
- These tools can work with the .hex and .bin files found in the release page
	- https://github.com/X16Community/x16-smc/releases/tag/r48.0.0

</p>
</details>



### Step 7: Install bootloader v3
Follow instructions inside the text file in [smc tools] ("smc-flash-manipulation-6.zip")

- Run SMCBLD7.PRG to get bootloader checksum, version and failsafe status
```
@CD:/UPDATE/SMCTOOLS
LOAD "SMCBLD7.PRG"
RUN
```
- Run SMCBLW19.PRG to install BOOT3.BIN
```
@CD:/UPDATE/SMCTOOLS
LOAD "SMCBLW19.PRG"
RUN
```
- Run SMCBLD7.PRG to validate checksum again, confirm it BF63 (v3)
- To install "Boot v3 failsafe", you need to update SMC a second time (repeat step 6)
- Run SMCBLD7.PRG, to confirm that boot v3 failsafe is installed

With Boot V3 failsafe installed, you have a fallback mechanism in case SMC firmware gets corrupted.


## Appendix: Release history
| Date       | ROM               | SMC     | VERA   | SMC bootloader | Notes                           |
|------------|-------------------|---------|--------|----------------|---------------------------------|
| 2025-01-08 |                   |         | 48.0.1 |                | XOR Sawtooth + bus stability    |
| 2024-12-23 |                   | 48.0.0  |        |                | Kbd initstate, read fuse++      |
| 2024-09-13 |                   |         |        | 3              | Boot v3, with failsafe          |
| 2024-09-06 | R48               |         |        |                | Release R48 ("Cadmium")         |
| 2024-07-05 |                   | 47.2.3  |        |                | Bootloader manipulation ++      |
| 2024-03-30 | R47               | 47.0.0  | 47.0.2 |                | Release R47 ("Roswell")         |
| 2023-12-24 | R47 pre 33ACE3A4* |         |        |                | Unreleased ROM version*         |
| 2023-11-20 |                   |         | 0.3.2  |                | Experimental FX                 |
| 2023-11-06 | R47 pre 8929A57+* |         |        |                | Unreleased ROM version*         |
| 2023-11-06 | R46               |         |        |                | Release R46 ("Winnipeg")        |
| 2023-10-18 |                   | 45.1.0* |        |                | Unreleased*, bootloader support |
| 2023-10-17 | R45               |         |        |                | Release R45 ("Nuuk")            |
| 2023-10-04 |                   |         |        | 2              | Boot v2, auto power off         |
| 2023-10-04 |                   |         |        | 2 (bad)*       | Bad version*                    |
| 2023-08-14 | R44               |         |        |                | Release R44 ("Milan")           |
| 2023-08-09 |                   |         | 0.3.1  |                | Experimental FX                 |
| 2023-05-17 | R43               | 43.0.0  |        |                | Release R43 ("Stockholm")       |
| 2023-04-19 |                   |         |        | 1              | Boot v1                         |
| 2023-03-23 |                   |         | 0.1.1  |                | VERA 0.1.1                      |
| 2023-03-07 | R42               | R42     |        |                | Release R42 ("Cambridge")       |

* A few releases are not official, but, these have been delivered with some of the machines, see below.


## Appendix: Stock version numbers


<details><summary>CLICK FOR DETAILS</summary>
<p>

This is based on feedback from users on Discord, and is very approximate. If you have updated info, feel free to send a message on Discord.

### PR00001 to PR00300

| Firmware        | Version              | Date       | Link                                                                                                                                                                  |
|-----------------|----------------------|------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ROM             | R47pre git 8929A57+* | 2023-11-06 | Build: https://cx16forum.com/forum/viewtopic.php?p=31112 / src: https://github.com/X16Community/x16-rom/pull/213 (exact source is ambiguous due to the +)             |
| SMC             | 45.1.0*              | 2023-10-18 | Build: https://github.com/FlightControl-User/x16-flash/blob/main/arduino/x16-smc-r45.1-bootloader.hex / src: https://github.com/X16Community/x16-smc/pull/20          |
| VERA            | 0.3.2                | 2023-11-20 | https://github.com/X16Community/vera-module/releases/tag/v0.3.2                                                                                                       |
| SMC bootloader  | 2 (bad)*             | 2023-10-04 | Build: https://github.com/FlightControl-User/x16-flash/blob/main/arduino/x16-smc-r45.1-bootloader.hex / src: https://github.com/stople/x16-smc-bootloader/tree/bad_v2 |

### PR00301 to PR00900

| Firmware        | Version              | Date       | Link                                                                                                             |
|-----------------|----------------------|------------|------------------------------------------------------------------------------------------------------------------|
| ROM             | R47pre git 33ACE3A4* | 2023-12-24 | Build: https://cx16forum.com/forum/viewtopic.php?p=31112 / src: https://github.com/X16Community/x16-rom/pull/241 |
| SMC             | 45.1.0*              | 2023-10-18 |                                                                                                                  |
| VERA            | 0.3.2                | 2023-11-20 |                                                                                                                  |
| SMC bootloader  | 2 (bad)*             | 2023-10-04 |                                                                                                                  |

### PR00901 to PR01000

| Firmware        | Version | Date       | Link                                                               |
|-----------------|---------|------------|--------------------------------------------------------------------|
| ROM             | R47     | 2024-03-30 | https://github.com/X16Community/x16-rom/releases/tag/r47           |
| SMC             | 47.0.0  | 2024-03-30 | https://github.com/X16Community/x16-smc/releases/tag/r47.0.0       |
| VERA            | 47.0.2  | 2024-03-30 | https://github.com/X16Community/vera-module/releases/tag/v47.0.2   |
| SMC bootloader  | 2       | 2023-10-04 | https://github.com/X16Community/x16-smc-bootloader/releases/tag/v2 |

### PR01001 to PR?????

| Firmware        | Version | Date       | Link                                                               |
|-----------------|---------|------------|--------------------------------------------------------------------|
| ROM             | R48     | 2024-09-06 | https://github.com/X16Community/x16-rom/releases/tag/r48           |
| SMC             | 47.2.3  | 2024-07-05 | https://github.com/X16Community/x16-smc/releases/tag/r47.2.3       |
| VERA            | 47.0.2  | 2024-03-30 | https://github.com/X16Community/vera-module/releases/tag/v47.0.2   |
| SMC bootloader  | 2       | 2023-10-04 | https://github.com/X16Community/x16-smc-bootloader/releases/tag/v2 |

### Some stock versions
| Machine | ROM                  | SMC     | VERA   | SMC bootloader |
|---------|----------------------|---------|--------|----------------|
| PR00015 | R47pre git 8929A57+* |         |        |                |
| PR00102 | R47pre git 8929A57+* | 45.1.0* | 0.3.2  | 2 (bad)*       |
| PR00499 | R47pre git 33ACE3A4* |         |        |                |
| PR00831 | R47pre git 33ACE3A4* | 45.1.0* | 0.3.2  | 2 (bad)*       |
| PR00923 | R47                  | 47.0.0  | 47.0.2 | 2              |
| PR01011 | R48                  | 47.2.3  | 47.0.2 | 2              |

</p>
</details>


## Appendix: How to downgrade from latest release to first release

<details><summary>CLICK FOR DETAILS</summary>
<p>

### Step 1: Downgrade bootloader
This is optional, as all bootloaders are backward compatible. If you do not plan to downgrade bootloader, go to step 2.

Run SMCBLD7.PRG. Check if "Boot v3 failsafe" is installed. If it is, and you plan to downgrade to bootloader v2 or older, you must:
- Ensure [any working SMC programming tool and SMC version] is present on SD card
	- SMCUPDATE-47.2.3 can be used
	- NB: x16-flash with bootloader 2 rejects programming SMC to the same version!
- Downgrade bootloader, using SMCBLW19.PRG
- Computer is now in a critical state. If you power it off, it is bricked.
- In this state, you must perform a SMC programming, to any version, with any tool, to uninstall "boot v3 failsafe".
	- If you installed bad v2 bootloader, remember to reset it using jumper wire

### Step 2: Downgrade SMC
Downgrade SMC using any tool
- SMCUPDATE or x16-update
- Note that SMC 45.1.0* or newer is needed if you want to use the bootloader afterwards
- SMC older than R42 is intended for an incompatible hardware revision

### Step 3: Downgrade ROM
Downgrade ROM
- ROM older than R42 is intended for an incompatible hardware revision

### Step 4: Downgrade VERA
Downgrade VERA
- If using VERA.BIN from release page, use the associated FLASHVERA
- If using VERA.BIN released together with x16-flash, use x16-flash to program it

</p>
</details>


<!-- For PDF formatting -->
<div class="page-break"></div>

# Appendix I: Character Sets

From ROM version R48 there are a total of 12 character sets build in. The different character sets are listed below with a short description of their history and/or use cases.

## Index

1) [ISO](#iso)
2) [PET Uppercase / Graphics](#pet-uppercase--graphics)
3) [PET Uppercase / Lowercase](#pet-uppercase--lowercase)
4) [PET Uppercase / Graphics (thin)](#pet-uppercase--graphics-thin)
5) [PET Uppercase / Lowercase (thin)](#pet-uppercase--lowercase-thin)
6) [ISO (thin)](#iso-thin)
7) [CP437](#cp437)
8) [Cyrillic ISO](#cyrillic-iso)
9) [Cyrillic ISO (thin)](#cyrillic-iso-thin)
10) [Eastern Latin ISO](#eastern-latin-iso)
11) [Eastern ISO (thin)](#eastern-iso-thin)
12) [Katakana (thin)](#katakana-thin)

<div style="page-break-after: always; visibility: hidden;"></div>

# ISO
![ISO](images/Appendix_I/01ISO.png)  
Added to the kernal early on to provide a characterset with international letters and glyphs.

<div style="page-break-after: always; visibility: hidden;"></div>

# PET Uppercase / Graphics
![PET upper/graphic](images/Appendix_I/02PETupper-graph.png)  
The default character set of the Commodore 64 and Commander X16, usually referred to as PETSCII. It provides only uppercase letters along with glyphs that can be used for doing simple text based drawings.

<div style="page-break-after: always; visibility: hidden;"></div>

# PET Uppercase / Lowercase
![PET upper/lower](images/Appendix_I/03PETupper-lower.png)  
This character set is also present in the Commodore 64 kernal and provides both upper- and lowercase letters at the expense of some of the glyphs used for text based drawing.

<div style="page-break-after: always; visibility: hidden;"></div>

# PET Uppercase / Graphics (thin)
![PET upper/graphic (thin)](images/Appendix_I/04PETupper-graph-thin.png)  
The default PETSCII character set, but with thinner characters to give a different aesthetic.

<div style="page-break-after: always; visibility: hidden;"></div>

# PET Uppercase / Lowercase (thin)
![PET upper/lower (thin)](images/Appendix_I/05PETupper-lower-thin.png)  
The standard upper- and lowercase PETSCII character set made thin for a different aesthetic.

<div style="page-break-after: always; visibility: hidden;"></div>

# ISO (thin)
![ISO (thin)](images/Appendix_I/06ISOthin.png)  
The ISO character set with thin characters for a different aesthetic.

<div style="page-break-after: always; visibility: hidden;"></div>

# CP437
![CP437](images/Appendix_I/07CP437.png)  
Added in ROM version R47. This is the character set of the original IBM PC, sometimes referred to as the ANSI character set. It is useful for displaying text created on a PC for example when connecting to BBS'es.

<div style="page-break-after: always; visibility: hidden;"></div>

# Cyrillic ISO
![Cyrillic ISO](images/Appendix_I/08CyrillicISO.png)  
Added in ROM version R47. Provides Cyrillic letters used in languages such as Bulgarian, Belarusian, Russian, Serbian and Macedonian. Also known as ISO-8859-5.

<div style="page-break-after: always; visibility: hidden;"></div>

# Cyrillic ISO (thin)
![Cyrillic ISO (thin)](images/Appendix_I/09CyrillicISOthin.png)  
Added in ROM version R47. Thin version of the Cyrillic character set.

<div style="page-break-after: always; visibility: hidden;"></div>

# Eastern Latin ISO
![Eastern Latin ISO](images/Appendix_I/10EasternLatinISO.png)  
Added in ROM version R47. Provides eastern european letters used in languages such as Albanian, Croatian, Hungarian, Polish, Romanian, Serbian and Slovenian, but also French, German and Italian. Also known as ISO-8859-16.

<div style="page-break-after: always; visibility: hidden;"></div>

# Eastern ISO (thin)
![Eastern ISO (thin)](images/Appendix_I/11EasternISOthin.png)  
Added in ROM version R47. Thin version of the Eastern Latin ISO character set.

<div style="page-break-after: always; visibility: hidden;"></div>

# Katakana (thin)
![Katakana (thin)](images/Appendix_I/12Katakana-thin.png)  
Added in ROM version R48. Provides katakana characters for the Japanese and Ainu languages.

# Appendix J: ROM Recovery

**WARNING: This is a draft that may contain errors or omissions that could damage your hardware.**


## Option 1: Using a PC to upgrade or recover ROM using Relatively Universal ROM Programmer (RURP)

**Target Component:** ROM

**Programmer:** Relatively Universal ROM Programmer (RURP) + Arduino UNO

**Software:** Firestarter

**Host OS:** Windows (should also be compatible with Mac/Linux)


### Before you start: Read project page and watch instruction videos (optional)

https://github.com/AndersBNielsen/Relatively-Universal-ROM-Programmer

https://hackaday.io/project/192273-relatively-universal-rom-programmer

https://www.youtube.com/watch?v=SZQ50XZlk5o

https://www.youtube.com/watch?v=JDHOKbyNnrE

https://discord.com/invite/kmhbxAjQc3


### Warning: SST39SF040 only

These instructions are only intended for the SST39SF040 parallel flash chip, used by X16.

If you follow these instructions but have a different chip, make sure to adjust voltage and jumpers accordingly. You may also want to consult with the videos and/or the RURP discord server.

These instructions have only been tested with V2 hardware.


### Get the programmer

Follow instructions at https://github.com/AndersBNielsen/Relatively-Universal-ROM-Programmer . You also need an Arduino Uno.

(Pro tip: Buy one additional black ZIF socket. It can be placed directly into the ROM socket, no soldering needed. Makes it much easier to remove the ROM IC later.)


### Solder through-hole components

Instruction video: https://www.youtube.com/watch?v=SZQ50XZlk5o

For use with the x16 rom (SST39SF040), you only need to solder the Arduino headers and the socket. Jumper and OLED headers are not needed, assuming HW revision 2.


### Install Firestarter app

Instruction video: https://www.youtube.com/watch?v=JDHOKbyNnrE

Firestarter is a 3rd party software/firmware improvement to the ROM programmer, which includes a large database of chip definitions, including SST39SF040.

Install using `pip install firestarter`

Test version using `firestarter --version`. These instructions are tested with app version 1.3.39.

Firestarter commands are explained by adding `-h` to it. To get more detailed output, use `-v`.


### Install Firestarter firmware

Do not have anything connected to your Arduino UNO. Connect the UNO to the PC.

Use `firestarter fw -h` to get instructions for how to program and verify firmware.

Install the firmware using the command `firestarter fw -i`. You may need to specify path to avrdude, if it is not in path. On Windows, it may be here: `C:\Program Files (x86)\Arduino\hardware\tools\avr\bin`. You may also specify path to avrdude.conf, e.g `-c "C:\Program Files (x86)\Arduino\hardware\tools\avr\etc"`.

After install, confirm version using `firestarter fw`. These instructions are tested with firmware 1.4.2.

Disconnect UNO from PC. Connect RURP shield to Arduino, without any ROM chip. Connect UNO to PC.

Identify hardware revision using `firestarter hw`. These instructions are tested with Rev2.


### Disconnect ROM chip

Disconnect power from the Commander X16. Remove the ROM chip, which is a SST39SF040 parallel flash IC, inside the "SYSTEM ROM" socket in the lower left corner of the board.


### Warning: High voltage

EEPROM chips requires high voltage (12-24V) to program and to erase. The parallel flash chip used by X16 does not need high voltage for anything. However, RURP can output high voltage to some of the pins, based on the control register. During Arduino reset, this control register is uninitialized, and may be in a state where it causes high voltage to some pins, which may damage a flash IC. Because of this, it is NOT recommended to connect an IC to RURP while it is powered off. Instead, power on RURP first, and then connect your IC just before programming it.


### Insert ROM chip into programmer

Send the command `firestarter info SST39SF040` to view the IC details and jumper config, based on the database. For HW rev2, no jumper is needed.

Make sure RURP is powered.

Connect the IC. The notch should go toward the nearest PCB edge. (For the record: If connecting a 24 or 28 pin IC, connect it according to the drawing on the back of the PCB).

To test communication with the flash chip, send `firestarter id SST39SF040`.

If you want to dump the contents of the chip, use the command `firestarter read SST39SF040`. This should dump to `SST39SF040.bin`, taking approx. 2 minutes.


### Program new rom file

Make sure the new rom file (e.g `rom.bin` for r48) is in the current folder.

To erase the chip and program this rom file, use the command `firestarter write SST39SF040 rom.bin`. This command will erase the chip, then verify that the entire chip is blank (0xFF), and then program the file.

Erase + blank check takes 45 seconds. Writing 256 kB, takes 1.5 additional minutes.

After write, you may want to verify that the contents of flash matches the contents of the `rom.bin` file. This can be done with `firestarter verify SST39SF040 rom.bin`. This takes a little over 1 minute.


### Insert ROM chip into X16

Make sure there are no blinkenlight activity on the RURP. There may be a few red stationary LEDs.

Remove the flash IC from RURP. If you have a ZIF socket on RURP, it is likely least risk of damaging anything if IC is disconnected while RURP is powered, since a sudden reconnect may give high voltage to a pin.

Insert the flash IC into X16, while X16 is disconnected from power. (You may optionally insert a ZIF socket into the ROM socket first, to make the ROM easier to remove next time.)

Power on your X16. Enjoy!


## Option 2: Using a cartridge to program/recover ROM

**Target Component:** ROM

**Programmer:** X16 + cartridge

**Software:** CX16-UPDATE

**Host OS:** CBM Basic


### Description

If you have a working Commander X16, and a cartridge with a ROM socket, and an extra ROM IC (SST39SF040), you can use it to make a backup ROM IC using CX16-UPDATE. In case you later brick your ROM IC, you can replace it with the backup. Using the backup, you can program the ROM IC again, using CX16-UPDATE.


### Connect ROM via cartridge to CX16

Disconnect power from the Commander X16.

Ensure that there is a working ROM in CX16.

Connect the ROM to be programmed, to a socket in the cartridge.

If the cartridge requires a "write enable" jumper, insert it.

Connect cartridge to CX16.


### Prepare SD card

Prepare a new folder on the SD card which contains CX16-UPDATE, and the rom.bin file to program.

Rename rom.bin to e.g "ROM1.BIN", if the ROM IC is inserted into the slot corresponding to ROM bank 32-63, which is the cartridge starting point. (You can also use ROM2.BIN .. ROM7.BIN, depending on how this ROM IC is accessed by the system).

Ensure that there are no files called rom.bin, smc.bin or vera.bin in this folder. Only CX16-UPDATE.PRG and e.g ROM1.BIN.


### Power on the machine and enter BASIC

Power on the machine.

If you get the READY prompt, proceed to the next step.

If not, Commander X16 may try to boot the cartridge. This is done if the machine reads "CX16" at offset $20:$C000.

If you have ROM R49 or newer:
- Press and hold the "shift" key, while powering on CX16. This will bypass cartridge boot.

If you have older ROM:
- Press NMI. This may start BASIC or monitor.

If you are in monitor:
- Change RO to 00 (set ROM bank to $00)
- Set carry flag (ensure it have an asterisk, "*")
- Press "enter" at end of line to apply the new registers
- Enter `R` (show registers, confirm that registers are updated)
- Enter `G FF47` (Jump to FF47, enter_basic)


### Start CX16-UPDATE

Enter the correct folder using `@CD:name_of_folder`. Use `@$` to view contents of current folder.

Start CX16-UPDATE.

Run the program. This should program the IC with the contents from e.g ROM1.BIN.

Power off the machine. Disconnect power. Place the ROM IC where appropriate (backup storage, or, into ROM socket).


<!-- For PDF formatting -->
<div class="page-break"></div>
