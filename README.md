# Commander X16 User's Guide

This is an unofficial User's Guide for the Commander X16
(https://www.commanderx16.com) written by by the community.  It aims to be
considered good enough to be adopted officially by 8-Bit Industries and the
Commander X16 project team.

---

## 📚 Chapter Overview & Progress

This section summarizes the current state of the Commander X16 User Guide, comparing it to the beloved Commodore 64 User Guide that inspired it.

### Current X16 User Guide Chapters

| Part/Chapter | File | Status | Description |
|-------------|------|--------|-------------|
| **Preface** | [preface.tex](preface.tex) | ✅ Complete | Introduction to the X16 and manual philosophy |
| **Part: Setup** | [setup.tex](setup.tex) | 🚧 Placeholder | Lorem ipsum placeholder text only |
| ↳ Initial Setup | [setup.tex](setup.tex) | 🚧 Placeholder | Needs real content |
| ↳ Monitor Setup | [setup.tex](setup.tex) | 🚧 Placeholder | Needs real content |
| **Part: Getting to Know Your X16** | [getting_to_know_commanderx16.tex](getting_to_know_commanderx16.tex) | ✅ Good | Core intro chapter with PRINT/GOTO example |
| ↳ Getting Started | [getting_to_know_commanderx16.tex](getting_to_know_commanderx16.tex) | ✅ Good | Start screen, quick experiments, errors |
| **Part: Using Screen & Keyboard** | [using_screen_and_keyboard.tex](using_screen_and_keyboard.tex) | 🔶 Partial | PRINT statement, graphic characters started |
| ↳ The PRINT Statement | [using_screen_and_keyboard.tex](using_screen_and_keyboard.tex) | 🔶 Partial | String vs numeric printing explained |
| ↳ Graphic Characters | [using_screen_and_keyboard.tex](using_screen_and_keyboard.tex) | 🔶 Partial | Started but incomplete |
| **Part: Graphics** | [graphics.tex](graphics.tex) | 🚧 Placeholder | Has type-in example, lorem ipsum body |
| **Part: Sound** | [sound.tex](sound.tex) | 🚧 Placeholder | Has FM synthesis type-in, lorem ipsum body |
| **Appendix: Commander X16 BASIC** | [appendix/basic_commands.tex](appendix/basic_commands.tex) | ✅ Extensive | ~4000 lines of BASIC reference documentation |
| **Appendix: 65C02 Op Codes** | [appendix/65c02_op_codes.tex](appendix/65c02_op_codes.tex) | ✅ Reference | CPU instruction reference |
| **Appendix: Memory Map** | [appendix/memory_map.tex](appendix/memory_map.tex) | ✅ Reference | X16 memory layout |
| **Appendix: PETSCII Codes** | [appendix/petscii_codes_table.tex](appendix/petscii_codes_table.tex) | ✅ Reference | Character code tables |
| **Appendix: Screen Codes** | [appendix/screen_codes_table.tex](appendix/screen_codes_table.tex) | ✅ Reference | Screen character codes |
| **Appendix: YM2151** | [appendix/ym2151.tex](appendix/ym2151.tex) | ✅ Reference | FM sound chip documentation |
| **Appendix: MUSIC PLAY Macros** | [appendix/music_play_macros.tex](appendix/music_play_macros.tex) | ✅ Reference | Music string notation |

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

### Comparison: VIC-20 vs C64 vs X16 Guide Structure

| Topic | VIC-20 | C64 | X16 Status | Notes |
|-------|--------|-----|------------|-------|
| **Welcoming Intro** | ✅ Preface | ✅ Intro | ✅ Preface | All three set a friendly, encouraging tone |
| **Setup/Hardware** | ✅ Setup | ✅ Ch 1 | 🚧 Placeholder | X16 needs: HDMI/VGA, SD card, USB, controllers |
| **First Program** | ✅ Ch 1 | ✅ Ch 2-3 | ✅ Good | Core "Hello World" experience covered |
| **Keyboard Tour** | ✅ Ch 2 | ✅ Ch 2 | 🔶 Partial | X16 has similar PETSCII keyboard |
| **PRINT & Calculator** | ✅ Ch 2 | ✅ Ch 2 | ✅ Good | Math operations, printing to screen |
| **Color Basics** | ✅ Ch 2-3 | ✅ Ch 5 | 🚧 Placeholder | X16 has COLOR command (easier than POKE) |
| **Graphics Characters** | ✅ Ch 2-3 | ✅ Ch 5 | 🔶 Partial | Keyboard graphics, PETSCII art |
| **Screen/Border Colors** | ✅ Ch 3 | ✅ Ch 5 | 🚧 Placeholder | Screen locations, color memory |
| **Animation** | ✅ Ch 4 | ✅ Ch 4 | ❌ Missing | Bouncing ball, flying birds examples |
| **PEEK/POKE** | ✅ Ch 4 | ✅ Ch 5 | 📖 Appendix | Direct memory access |
| **Sound Basics** | ✅ Ch 5 | ✅ Ch 7 | 🚧 Placeholder | X16 has PSG + YM2151 FM |
| **Music/Piano** | ✅ Ch 5 | ✅ Ch 7 | 🚧 Placeholder | FMPLAY/PSGPLAY commands |
| **INPUT Statement** | ✅ Ch 6 | ✅ Ch 4 | ❌ Missing | "What's Your Name?" - essential for interaction |
| **Variables** | ✅ Ch 6 | ✅ Ch 3 | 📖 Appendix | In reference, needs tutorial chapter |
| **GET Statement** | ✅ Ch 6 | ✅ Ch 4 | 📖 Appendix | Single keypress input |
| **BASIC Commands** | ✅ Ch 7 | ✅ Ch 3 | 📖 Appendix | RUN, LIST, NEW, etc. |
| **Random Numbers** | ✅ Ch 7 | ✅ Ch 4 | 📖 Appendix | RND function, games |
| **Loading/Saving** | ✅ App B | ✅ Ch 2 | ❌ Missing | **High priority** - SD card workflow needed |
| **IF...THEN** | ✅ App C | ✅ Ch 3 | ❌ Missing | Core programming construct |
| **FOR...NEXT Loops** | ✅ App C | ✅ Ch 3 | ❌ Missing | Essential for all programs |
| **GOSUB/Subroutines** | ✅ App C | ✅ Ch 4 | 📖 Appendix | Program organization |
| **Sprites** | ❌ N/A | ✅ Ch 6 | ❌ Missing | X16 has VERA sprites (128 of them!) |
| **Bitmap Graphics** | ❌ N/A | ❌ Limited | ❌ Missing | **X16-specific**: VERA bitmap modes |
| **Tile/Layer Graphics** | ❌ N/A | ❌ N/A | ❌ Missing | **X16-specific**: VERA layers |
| **Joystick/Controllers** | ✅ App L | ✅ Appendix | ❌ Missing | X16: SNES controllers + joystick |
| **Error Messages** | ✅ App N | ✅ App L | ❌ Missing | Add to appendix |
| **Sample Programs** | ✅ App M | ✅ App J | ❌ Missing | Type-in programs collection |

### 📋 Chapter Comparison & TODO List

| Topic | C64 Guide | X16 Guide Status | Priority | Notes |
|-------|-----------|------------------|----------|-------|
| **Setup/Unboxing** | Ch 1 ✅ | 🚧 Placeholder | 🔴 High | Needs: X16 connections (HDMI/VGA, USB, SD card, audio, PS/2, SNES controllers) |
| **Keyboard & Navigation** | Ch 2.1 ✅ | 🔶 Partial | 🔴 High | Needs: Full keyboard diagram, special keys (F1-F8, PETSCII entry) |
| **Loading/Saving** | Ch 2.3 ✅ | ❌ Not written | 🔴 High | Needs: SD card usage, DOS commands, file management |
| **PRINT & Calculations** | Ch 2.4-2.6 ✅ | ✅ Good | 🟢 Low | Covered in getting_to_know_commanderx16.tex |
| **Beginning BASIC** | Ch 3 ✅ | 🔶 Partial | 🟡 Medium | Variables partially covered in appendix; needs tutorial chapter |
| **IF...THEN, FOR...NEXT** | Ch 3.4-3.5 ✅ | ❌ Not written | 🟡 Medium | Essential programming constructs |
| **Advanced BASIC (INPUT, GET)** | Ch 4 ✅ | ❌ Not written | 🟡 Medium | User interaction, games |
| **Color & Graphics Basics** | Ch 5 ✅ | 🚧 Placeholder | 🔴 High | Has type-in, needs VERA basics, screen modes, COLOR command |
| **Sprite Graphics** | Ch 6 ✅ | ❌ Not written | 🟡 Medium | X16 sprite system differs from C64 |
| **Bitmap Graphics** | (limited in C64) | ❌ Not written | 🟡 Medium | **X16-specific**: VERA bitmap modes, LINE, RECT, etc. |
| **Tile Maps** | N/A | ❌ Not written | 🟡 Medium | **X16-specific**: VERA tile layers |
| **Sound/Music** | Ch 7 ✅ | 🚧 Placeholder | 🔴 High | Has FMPLAY type-in; needs PSG & VERA PSG explanation |
| **FM Synthesis** | N/A | 🚧 Placeholder | 🟡 Medium | **X16-specific**: YM2151 detailed usage |
| **Data Handling** | Ch 8 ✅ | ❌ Not written | 🟡 Medium | READ/DATA, arrays |
| **Error Messages** | Appendix L ✅ | ❌ Not written | 🟢 Low | Add to appendix |
| **Sample Programs** | Appendix J ✅ | ❌ Not written | 🟡 Medium | Type-in programs collection |

### 🆕 Suggested New X16-Specific Chapters

These chapters would cover capabilities unique to the Commander X16:

| Chapter | Priority | Description |
|---------|----------|-------------|
| **VERA Graphics System** | 🔴 High | Overview of VERA chip: layers, sprites, tile modes, bitmap modes |
| **Working with the SD Card** | 🔴 High | File operations, DOS commands, directory navigation |
| **Banked Memory** | 🟡 Medium | Using the 512KB+ high RAM via banking |
| **The X16 Emulator** | 🟡 Medium | Using the official emulator for development |
| **Connecting Controllers** | 🟡 Medium | SNES gamepad support, joystick reading |
| **Assembly Language Intro** | 🟢 Low | Brief intro to 65C02 assembly on X16 |
| **Expansion & I2C** | 🟢 Low | Using expansion slots and I2C bus |

### Legend

- ✅ **Complete** - Chapter is written and usable
- 🔶 **Partial** - Some content exists but incomplete  
- 🚧 **Placeholder** - Structure exists but content is lorem ipsum
- ❌ **Not written** - Chapter doesn't exist yet
- � **In Appendix** - Covered in reference material, needs tutorial
- 🔴 **High Priority** - Essential for a usable guide
- 🟡 **Medium Priority** - Important but not blocking
- 🟢 **Low Priority** - Nice to have

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
