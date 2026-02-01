# Commander X16 User's Guide

This is an unofficial User's Guide for the Commander X16
(https://www.commanderx16.com) written by by the community.  It aims to be
considered good enough to be adopted officially by 8-Bit Industries and the
Commander X16 project team.

---

## Inspiration and Structure

This User's Guide takes inspiration (often shamelessly) from the Commodore
VIC-20 User's Guide.  This was chosen for multiple reasons, not least of which
is the reputation that the VIC-20 User's Guide holds in the retro computing
community for being one of the best computer manuals ever printed.  When David
Murray (the 8-Bit Guy) released his [first Building my Dream Computer
video](https://www.youtube.com/watch?v=ayh0qebfD2g), he introduced us to the
project by explaining his experience as a 6-year-old going through the
Commodore VIC-20 manual.  In his [second Building my Dream Computer
video](https://www.youtube.com/watch?v=sg-6Cjzzg8s) he explained how the VIC-20
was now a major inspiration for the Commander X16's new hardware design.
Because the concept and the hardware already draw inspiration from the VIC-20,
it only makes sense that the User's Guide follow suit.

One of the most important features of the VIC-20 User's Guide is that it
specifically targets a wide audience of both experienced computer users and
programmers, as well as people who have never even touched a computer before.
Therefore it needed to explain usage of the computer with no prior knowledge of
computers, starting with many things we take for granted nowadays.  The
Commander X16 User's Guide should likewise not make any assumptions.  After
all, the Commander X16 is intended to provide the experience David had as a
6-year-old in dawn of the home computing era.  The User's Guide must be
something that an inquisitive 6-year-old can read, even if they've never
touched a keyboard before.

Another feature of the VIC-20 User's Guide was that it allowed the reader to
skip to any chapter they may find interesting.  All that was required was that
the user read the first introductory chapter, and then they were encouraged to
explore the capabilities of the computer that captivated them the most.  The
X16 User's Guide should be structured likewise.  There is a chapter for
understanding the basics of operating the computer, and then there are chapters
for diving into the specifics.  Each of these chapters begins with a short
type-in BASIC program that gives the user a preview of what they are going to
learn, and then the rest of the chapter explains what they did in detail.  This
pattern should be followed all througout the book.

---
## Building & Contributing

See **[CONTRIBUTING.md](CONTRIBUTING.md)** for:
- Build dependencies and instructions
- How to submit contributions (LaTeX knowledge not required!)
- LaTeX formatting guide (keys, screen boxes, bubbles, tips, notes, etc.) 

---
## 📚 Chapter Overview & Progress

This section summarizes the current state of the Commander X16 User Guide, comparing it to the beloved VIC-20 User Guide that inspired it.

### Current X16 User Guide Chapters (VIC-20 Structure)

| Chapter | File | Status | Lines | Description |
|---------|------|--------|-------|-------------|
| **Preface** | [preface.tex](preface.tex) | ✅ Complete | 48 | Introduction to the X16 and manual philosophy |
| **Setup** | [ch00_setup.tex](ch00_setup.tex) | 🚧 Placeholder | 58 | Lorem ipsum only - needs hardware setup content |
| **Ch 1: Getting to Know Your X16** | [ch01_getting_to_know_commanderx16.tex](ch01_getting_to_know_commanderx16.tex) | ✅ Good | 506 | Start screen, PRINT, GOTO, first program, errors |
| **Ch 2: Using Screen & Keyboard** | [ch02_using_screen_and_keyboard.tex](ch02_using_screen_and_keyboard.tex) | 🔶 Partial | 432 | PRINT statement done, graphic characters started |
| **Ch 3: Color and Graphics** | [ch03_color_and_graphics.tex](ch03_color_and_graphics.tex) | 🚧 Placeholder | 66 | Has type-in example, section stubs with TODOs |
| **Ch 4: Animation** | [ch04_animation.tex](ch04_animation.tex) | 🚧 Placeholder | 61 | Has type-in example, section stubs with TODOs |
| **Ch 5: Sound and Music** | [ch05_sound_and_music.tex](ch05_sound_and_music.tex) | 🚧 Placeholder | 75 | Has FM type-in example, section stubs with TODOs |
| **Ch 6: Conversing with Your X16** | [ch06_conversing_with_x16.tex](ch06_conversing_with_x16.tex) | ✅ Complete | 549 | INPUT, variables, GET statement, temperature converter, interactive programs |
| **Ch 7: Introduction to Programming** | [ch07_introduction_to_programming.tex](ch07_introduction_to_programming.tex) | ✅ Complete | 503 | RND, INT, IF...THEN, FOR...NEXT, guessing game, dice roller |
| **Appendix: BASIC Commands** | [appendix/basic_commands.tex](appendix/basic_commands.tex) | ✅ Extensive | 3982 | Comprehensive BASIC reference documentation |
| **Appendix: BASIC Table** | [appendix/basic_table.tex](appendix/basic_table.tex) | ✅ Reference | 147 | Quick reference table |
| **Appendix: Screen Codes** | [appendix/screen_codes_table.tex](appendix/screen_codes_table.tex) | ✅ Reference | 222 | Screen character codes |
| **Appendix: PETSCII Codes** | [appendix/petscii_codes_table.tex](appendix/petscii_codes_table.tex) | ✅ Reference | 97 | Character code tables |
| **Appendix: Memory Map** | [appendix/memory_map.tex](appendix/memory_map.tex) | ✅ Reference | 157 | X16 memory layout |
| **Appendix: 65C02 Op Codes** | [appendix/65c02_op_codes.tex](appendix/65c02_op_codes.tex) | 🚧 Stub | 2 | Needs content |
| **Appendix: Patch Table** | [appendix/patch_table.tex](appendix/patch_table.tex) | ✅ Reference | 150 | ROM patch information |
| **Appendix: MUSIC PLAY Macros** | [appendix/music_play_macros.tex](appendix/music_play_macros.tex) | ✅ Reference | 404 | Music string notation |
| **Appendix: YM2151** | [appendix/ym2151.tex](appendix/ym2151.tex) | ✅ Reference | 552 | FM sound chip documentation |
| **Appendix: Error Messages** | [appendix/error_messages.tex](appendix/error_messages.tex) | 🔶 Partial | 54 | Basic structure, 7 errors listed, needs completion |
| **Appendix: Sample Programs** | [appendix/sample_programs.tex](appendix/sample_programs.tex) | 🚧 Placeholder | 48 | Section stubs only, no actual programs yet |

### Original VIC-20 User's Guide Chapters

The VIC-20 User's Guide is considered one of the best computer manuals ever written—the primary inspiration for this X16 guide. David Murray (the 8-Bit Guy) has cited his experience with this manual as a 6-year-old as foundational to the Commander X16 project.

| Chapter | Content Summary |
|---------|----------------|
| **Preface** | Welcome, philosophy of the manual |
| **Setup**: Unpacking and Connecting | Hardware setup, TV hookup, first power-on |
| **Ch 1**: Getting to Know Your VIC | Getting Started, Your First Computer Program |
| **Ch 2**: Using the Screen and Keyboard | First graphic character, keyboard tour, printing, VIC calculator, intro to color |
| **Ch 3**: Color and Graphics | Programming in color, color keys, screen/border colors, screen locations, random colors, sound+color combo, keyboard graphics |
| **Ch 4**: Animation | Flying birds, bouncing ball, cursor control, animating with POKEs and PEEKs |
| **Ch 5**: Sound and Music | Making music, four voices of VIC, white noise, using VIC as piano, playing songs |
| **Ch 6**: Conversing with Your VIC | INPUT ("What's Your Name?"), introducing variables, GET statement |
| **Ch 7**: Introduction to Programming | First BASIC commands, random numbers |
| **Appendices A-N** | Accessories, tape cassettes, BASIC vocabulary, abbreviations, colors, musical notes, sound effects, screen codes, memory map, ASCII/CHR$, math functions, pinouts, sample programs, error messages |

### Original Commodore 64 User Guide Chapters

The C64 User Guide built on the VIC-20's approach, with expanded coverage for the C64's enhanced capabilities (sprites, SID chip):

| Chapter | Content Summary |
|---------|----------------|
| **Introduction** | Computer overview, features (sprites, sound), peripherals |
| **Ch 1**: Setup | Unpacking, TV connections, power, troubleshooting chart, color adjustment |
| **Ch 2**: Getting Started | Keyboard layout, special keys, loading/saving (tape & disk), PRINT, calculations, precedence |
| **Ch 3**: Beginning BASIC | Line numbers, GOTO, editing, variables (int, float, string), IF...THEN, FOR...NEXT |
| **Ch 4**: Advanced BASIC | Animation, nested loops, INPUT, GET, RND, CHR$/ASC, sample games |
| **Ch 5**: Advanced Color & Graphics | PRINTing colors, CTRL codes, PEEK/POKE, screen memory, color memory |
| **Ch 6**: Sprite Graphics | Sprite creation, animation, collision detection, binary arithmetic |
| **Ch 7**: Creating Sound | Sound structure, music notation, ADSR envelopes, sound effects |
| **Ch 8**: Advanced Data Handling | READ/DATA, arrays (1D and 2D), DIM statement |
| **Appendices A-P** | Accessories, cassette operation, BASIC reference, abbreviations, screen codes, ASCII/CHR$, memory maps, math functions, pinouts, sample programs, error messages, sprite registers, sound settings |

### Comparison: VIC-20 vs X16 Guide Structure

| VIC-20 Chapter | VIC-20 Content | X16 File | X16 Status | Work Needed |
|----------------|----------------|----------|------------|-------------|
| **Preface** | Welcome, philosophy | [preface.tex](preface.tex) | ✅ Complete | None |
| **Setup** | Hardware setup, TV hookup | [ch00_setup.tex](ch00_setup.tex) | 🚧 Placeholder | HDMI/VGA, SD card, USB, controllers, audio |
| **Ch 1**: Getting to Know | First program, PRINT/GOTO | [ch01_getting_to_know_commanderx16.tex](ch01_getting_to_know_commanderx16.tex) | ✅ Good | Minor polish |
| **Ch 2**: Screen & Keyboard | Printing, keyboard tour, calculator | [ch02_using_screen_and_keyboard.tex](ch02_using_screen_and_keyboard.tex) | 🔶 Partial | Complete graphic characters, keyboard diagram |
| **Ch 3**: Color and Graphics | COLOR, screen colors, PETSCII art | [ch03_color_and_graphics.tex](ch03_color_and_graphics.tex) | 🚧 Placeholder | All sections need content |
| **Ch 4**: Animation | Bouncing ball, flying birds, PEEK/POKE | [ch04_animation.tex](ch04_animation.tex) | 🚧 Placeholder | All sections need content |
| **Ch 5**: Sound and Music | Making music, piano, songs | [ch05_sound_and_music.tex](ch05_sound_and_music.tex) | 🚧 Placeholder | All sections need content (has FM type-in) |
| **Ch 6**: Conversing | INPUT, variables, GET | [ch06_conversing_with_x16.tex](ch06_conversing_with_x16.tex) | ✅ Complete | None - follows VIC-20 structure |
| **Ch 7**: Intro to Programming | BASIC commands, RND, IF/THEN, FOR/NEXT | [ch07_introduction_to_programming.tex](ch07_introduction_to_programming.tex) | 🚧 Placeholder | All sections need content |
| **Appendices** | BASIC ref, screen codes, samples, errors | [appendix/](appendix/) | 🔶 Mixed | Error messages partial, sample programs needed |

### 📋 Priority TODO List

| Priority | Chapter/Section | Current State | Work Required |
|----------|-----------------|---------------|---------------|
| 🔴 High | **Ch 0: Setup** | Lorem ipsum | Write HDMI/VGA/composite setup, SD card prep, controller connection |
| 🔴 High | **Ch 3: Color and Graphics** | Section stubs | Write COLOR command tutorial, color keys, PETSCII art examples |
| 🔴 High | **Ch 5: Sound and Music** | Section stubs | Write PSG basics, FMPLAY/PSGPLAY tutorials, piano program |
| 🟡 Medium | **Ch 2: Screen & Keyboard** | Partial | Complete graphic characters section, add keyboard diagram |
| 🟡 Medium | **Ch 4: Animation** | Section stubs | Write bouncing ball, cursor control, PEEK/POKE animation |
| 🟡 Medium | **Ch 7: Programming** | Section stubs | Write RND, IF/THEN, FOR/NEXT tutorials, sample game |
| 🟡 Medium | **Appendix: Sample Programs** | Section stubs | Add 5-10 type-in programs |
| 🟢 Low | **Appendix: Error Messages** | 7 errors | Complete full error list |
| 🟢 Low | **Appendix: 65C02 Op Codes** | Empty | Add instruction reference (or remove if covered elsewhere) |

### 🆕 Suggested Future X16-Specific Content

These topics could be added as sections within existing chapters or as appendices, following the VIC-20's approach of keeping main chapters accessible while providing deeper reference material in appendices:

| Topic | Where to Add | Priority | Description |
|-------|--------------|----------|-------------|
| **SD Card & File Operations** | Ch 7 or Appendix | 🔴 High | LOAD, SAVE, DOS commands, directory navigation |
| **VERA Graphics Overview** | Ch 3 (Color/Graphics) | 🟡 Medium | Brief intro to screen modes, layers |
| **Sprites** | Appendix | 🟡 Medium | VERA sprite system (128 sprites, 64x64 max) |
| **Bitmap Drawing** | Ch 3 or Appendix | 🟡 Medium | LINE, RECT, CIRCLE commands |
| **Controllers/Joysticks** | Appendix | 🟡 Medium | JOY() function, SNES controller support |
| **Banked Memory** | Appendix | 🟢 Low | Using 512KB+ high RAM |
| **Using the Emulator** | Appendix | 🟢 Low | Development with official emulator |

### Legend

- ✅ **Complete** - Chapter is written and usable
- 🔶 **Partial** - Some content exists but incomplete  
- 🚧 **Placeholder** - Structure exists but content is TODOs/stubs
- 🔴 **High Priority** - Essential for a usable guide
- 🟡 **Medium Priority** - Important but not blocking
- 🟢 **Low Priority** - Nice to have

---

