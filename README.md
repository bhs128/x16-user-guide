# Commander X16 User's Guide

This is an unofficial User's Guide for the Commander X16
(https://www.commanderx16.com) written by by the community.  It aims to be
considered good enough to be adopted officially by 8-Bit Industries and the
Commander X16 project team.

---

## Download the User Guide

**Just want the PDF?** Head over to the [**GitHub Releases**](https://github.com/X16Community/x16-user-guide/releases) page to download the latest version of the Commander X16 User's Guide.

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

## 📚 VIC-20 vs X16 User Guide Chapter Comparison

The following table shows how the Commander X16 User Guide follows the VIC-20 User Guide structure, while adding new X16-exclusive content.

### Chapter Structure Comparison

| VIC-20 User Guide | X16 User Guide | Status | Notes |
|-------------------|----------------|--------|-------|
| **Preface** | **Preface** | ✅ Match | Philosophy & welcome message |
| **Unpacking & Connecting** | **Setup (ch00)** | ✅ Match | Hardware setup, connections |
| | | | |
| **Ch 1: Getting to Know Your VIC** | **Ch 1: Getting to Know Your X16** | ✅ Match | |
| • Getting Started | • Getting Started | ✅ Match | Start screen, PRINT, RETURN |
| • Your First Computer Program | • Your First Computer Program | ✅ Match | GOTO, RUN, LIST |
| | | | |
| **Ch 2: Using Screen & Keyboard** | **Ch 2: Using Screen & Keyboard** | ✅ Match | |
| • Graphic Characters | • Graphic Characters | ✅ Match | PETSCII symbols |
| • Keyboard Tour | • (integrated throughout) | ✅ Match | Keys explained as used |
| • Printing on the Screen | • The PRINT Statement | ✅ Match | Strings vs numbers |
| • Calculator | • (expanded in Ch 7) | ✅ Match | Math operations |
| • Introduction to Color | • Colors | ✅ Match | COLOR statement basics |
| | • Screen Modes | 🆕 X16 | 40/80 column, SCREEN command |
| | • Editing Text | ✅ Match | Full-screen editor |
| | • File Operations | ✅ Match | SAVE, LOAD, SCRATCH |
| | • Using the Mouse | 🆕 X16 | Mouse cursor, MX/MY/MB |
| | | | |
| **Ch 3: Color and Graphics** | **Ch 3: Color and Graphics** | ✅ Match | |
| • Programming in Color | • Programming in Color | ✅ Match | COLOR statement detail |
| • Color Keys | • The Color Keys | ✅ Match | CTRL+1-8, ALT+1-8 |
| • Screen/Border Colors | • Screen and Border Colors | ✅ Match | Border modes |
| • Screen Locations | • Screen Locations | ✅ Match | LOCATE, TAB |
| | • The TILE Statement | 🆕 X16 | Direct character placement |
| | • Direct Screen Memory (VPOKE) | ✅ Enhanced | VERA video memory |
| • Random Colors | • Random Colors | ✅ Match | RND for colors |
| • Keyboard Graphics | • Keyboard Graphics | ✅ Match | Drawing with PETSCII |
| | • VERA Graphics Mode | 🆕 X16 | LINE, RECT, FRAME, OVAL, PSET |
| | • Introduction to Sprites | 🆕 X16 | SPRITE, SPRMEM, MOVSPR, SPRCOL |
| | | | |
| **Ch 4: Animation** | **Ch 4: Animation** | ✅ Match | |
| • Flying Birds | • Flying Objects | ✅ Match | Multi-character animation |
| • Bouncing Ball | • The Bouncing Ball | ✅ Match | Classic animation |
| • Cursor Control | • Cursor Control for Animation | ✅ Match | Cursor movement characters |
| • POKE/PEEK Animation | • (VPOKE used throughout) | ✅ Match | Direct memory animation |
| | • Graphics Mode Animation | 🆕 X16 | LINE-based animation |
| | • Sprite Animation | 🆕 X16 | Hardware sprite movement, collision detection |
| | | | |
| **Ch 5: Sound and Music** | **Ch 5: Sound and Music** | ✅ Match | |
| • Making Music | • Making Your First Sound | ✅ Match | Basic sound commands |
| • Four Voices of VIC | • The Voices of the X16 | ✅ Enhanced | 16 PSG voices + 8 FM channels |
| • White Noise | • (PSG noise waveform) | ✅ Match | Noise for effects |
| • Piano Program | • Using the X16 as a Piano | ✅ Match | Interactive keyboard |
| • Playing Songs | • Playing Songs | ✅ Match | Multi-voice songs |
| • POKE for Sound | • Sound Commands Summary | ✅ Enhanced | FMPLAY, PSGPLAY, FMNOTE, PSGNOTE |
| | • Sound Effects | ✅ Match | Beep, explosion, laser, siren |
| | | | |
| **Ch 6: Conversing with Your VIC** | **Ch 6: Conversing with Your X16** | ✅ Match | |
| • What's Your Name? | • What's Your Name? | ✅ Match | Classic opener |
| • Variables | • Introducing Variables | ✅ Match | String vs numeric |
| • Choose a Note | • Choose a Number | ✅ Match | User input examples |
| • GET Statement | • The GET Statement | ✅ Match | Instant keypress |
| | • Temperature Converter | ✅ Match | Practical application |
| | | | |
| **Ch 7: Introduction to Programming** | **Ch 7: Introduction to Programming** | ✅ Match | |
| • BASIC Commands | • (distributed throughout) | ✅ Match | Commands taught in context |
| • Random Numbers | • Random Numbers | ✅ Match | RND, INT formula |
| | • Making Decisions (IF...THEN) | ✅ Match | Conditionals |
| | • Loops (FOR...NEXT) | ✅ Match | Counting loops |
| | • Guess the Number Game | ✅ Match | Capstone project |
| | • Roll the Dice | ✅ Match | Additional game |

### Appendix Comparison

| VIC-20 Appendix | X16 Appendix | Status | Notes |
|-----------------|--------------|--------|-------|
| VIC System Accessories | — | ❌ Removed | Not applicable to X16 |
| Working with Tape | — | ❌ Removed | X16 uses SD cards |
| BASIC Vocabulary | BASIC Commands Reference | ✅ Enhanced | Comprehensive with origins |
| Command Abbreviations | (in BASIC reference) | ✅ Match | Documented per command |
| Color Combinations | (in Chapter 3) | ✅ Match | Integrated into chapters |
| Musical Notes | (in Chapter 5) | ✅ Match | Integrated into chapters |
| Sample Sound Effects | (in Chapter 5) | ✅ Match | Integrated into chapters |
| Screen Display Codes | Screen Codes Table | ✅ Match | Full character set |
| Screen Memory Map | Memory Map | ✅ Enhanced | VERA memory layout |
| ASCII/Character Codes | PETSCII Codes Table | ✅ Match | Full code tables |
| Mathematical Functions | (in BASIC reference) | ✅ Match | Documented per function |
| I/O Pinouts | — | ❌ Removed | Hardware reference |
| Programs to Try | Sample Programs | ✅ Enhanced | 8 complete programs |
| Error Messages | Error Messages | ✅ Match | All BASIC errors |
| — | Music PLAY Macros | 🆕 X16 | FMPLAY/PSGPLAY reference |
| — | YM2151 Patch Table | 🆕 X16 | FM instrument presets |

### Legend

| Symbol | Meaning |
|--------|---------|
| ✅ Match | Content follows VIC-20 structure |
| ✅ Enhanced | VIC-20 concept with significant X16 enhancements |
| 🆕 X16 | New content exclusive to Commander X16 |
| ❌ Removed | VIC-20 content not applicable to X16 |

### Key X16-Exclusive Features Documented

The following Commander X16 features have no VIC-20 equivalent and represent new content:

1. **VERA Video Chip** — Advanced video capabilities with dedicated video RAM
2. **Graphics Mode** — Bitmap graphics with LINE, RECT, FRAME, OVAL, PSET commands  
3. **Hardware Sprites** — 128 sprites with SPRITE, SPRMEM, MOVSPR commands
4. **Sprite Collision** — SPRCOL function for game development
5. **FM Sound (YM2151)** — 8-channel FM synthesis with 160+ instrument patches
6. **16-Voice PSG** — VERA's programmable sound generator
7. **FMPLAY/PSGPLAY** — Music string commands for easy melody creation
8. **Mouse Support** — Native PS/2 mouse with MOUSE, MX, MY, MB
9. **80-Column Mode** — High-resolution text display
10. **SD Card Storage** — Modern file storage (replaces tape/disk)
11. **TILE Statement** — Direct character/color placement
12. **Screen Modes** — Multiple display modes via SCREEN command

---

## Building & Contributing

See **[CONTRIBUTING.md](CONTRIBUTING.md)** for:
- Build dependencies and instructions
- How to submit contributions (LaTeX knowledge not required!)
- LaTeX formatting guide (keys, screen boxes, bubbles, tips, notes, etc.) 

---

## 📊 Chapter Status Summary

All chapters are **publication-ready** and follow the VIC-20 User Guide structure.

| Chapter | File | Status | Key Content |
|---------|------|--------|-------------|
| Preface | [preface.tex](preface.tex) | ✅ Complete | Philosophy, welcome message |
| Setup | [ch00_setup.tex](ch00_setup.tex) | ✅ Complete | Hardware connections, troubleshooting |
| Ch 1 | [ch01_getting_to_know_commanderx16.tex](ch01_getting_to_know_commanderx16.tex) | ✅ Complete | PRINT, GOTO, RUN, LIST, first program |
| Ch 2 | [ch02_using_screen_and_keyboard.tex](ch02_using_screen_and_keyboard.tex) | ✅ Complete | PETSCII, colors, screen modes, file I/O, mouse |
| Ch 3 | [ch03_color_and_graphics.tex](ch03_color_and_graphics.tex) | ✅ Complete | COLOR, TILE, VPOKE, graphics mode, sprites |
| Ch 4 | [ch04_animation.tex](ch04_animation.tex) | ✅ Complete | Bouncing ball, flying birds, sprite animation |
| Ch 5 | [ch05_sound_and_music.tex](ch05_sound_and_music.tex) | ✅ Complete | PSG/FM sound, piano program, songs |
| Ch 6 | [ch06_conversing_with_x16.tex](ch06_conversing_with_x16.tex) | ✅ Complete | INPUT, variables, GET statement |
| Ch 7 | [ch07_introduction_to_programming.tex](ch07_introduction_to_programming.tex) | ✅ Complete | RND, IF/THEN, FOR/NEXT, guessing game |

### Appendices

| Appendix | File | Content |
|----------|------|---------|
| BASIC Commands | [appendix/basic_commands.tex](appendix/basic_commands.tex) | Complete reference with origin tags (C64/X16/C128) |
| Screen Codes | [appendix/screen_codes_table.tex](appendix/screen_codes_table.tex) | Full character set table |
| PETSCII Codes | [appendix/petscii_codes_table.tex](appendix/petscii_codes_table.tex) | ASCII/PETSCII code reference |
| Memory Map | [appendix/memory_map.tex](appendix/memory_map.tex) | VERA and system memory layout |
| Music Macros | [appendix/music_play_macros.tex](appendix/music_play_macros.tex) | FMPLAY/PSGPLAY string reference |
| Patch Table | [appendix/patch_table.tex](appendix/patch_table.tex) | YM2151 FM instrument presets |
| Error Messages | [appendix/error_messages.tex](appendix/error_messages.tex) | All BASIC error codes explained |
| Sample Programs | [appendix/sample_programs.tex](appendix/sample_programs.tex) | 8 complete type-in programs |

---

## Reference Materials

The following source documents in the `sources/` folder inform this guide:

| File | Description |
|------|-------------|
| `vic20_userguide.txt` | VIC-20 User Guide excerpts (primary structural inspiration) |
| `c64ug.txt` | Commodore 64 User Guide (tone and content reference) |
| `X16_ref_guide.md` | Commander X16 Reference Guide (technical accuracy) |
| `x16_hw_setup.txt` | X16 hardware setup notes |
| `x16_xiphod_faq.txt` | Community FAQ reference |

---
