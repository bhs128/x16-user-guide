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

This section summarizes the current state of the Commander X16 User Guide, with a detailed chapter-by-chapter review covering content quality, continuity, tone, and suggestions for polish.

### 📖 Detailed Chapter Review

#### ✅ Preface ([preface.tex](preface.tex)) — Complete
**Status:** Publication-ready  
**Content:** Eloquently captures the philosophy and spirit of the Commander X16. Explains why the machine exists as a "technological anachronism" while celebrating its ability to strip away modern abstractions and provide a pure computing experience.  
**Tone:** Warm, inviting, and perfectly aligned with the VIC-20 manual's spirit.  
**Suggestions:** None — this sets the perfect stage for the manual.

---

#### ✅ Setup ([ch00_setup.tex](ch00_setup.tex)) — Complete
**Status:** Publication-ready  
**Content:** Comprehensive coverage of hardware setup including ATX/picoPSU power, VGA/S-Video/Composite video connections, PS/2 keyboard/mouse, audio, SD card, and HDMI adapter guidance. Includes troubleshooting section.  
**Tone:** Clear, step-by-step, accessible to complete beginners.  
**Continuity:** Good transition to Chapter 1.  
**Suggestions:**
- Consider adding a simple diagram showing port locations on the motherboard
- Could mention the official case assembly briefly with screwdriver reference (already present)

---

#### ✅ Chapter 1: Getting to Know Your X16 ([ch01_getting_to_know_commanderx16.tex](ch01_getting_to_know_commanderx16.tex)) — Complete
**Status:** Publication-ready  
**Content:** Excellent introduction covering the start screen, PRINT command, quotation marks, RETURN key, syntax errors, screen clearing, and the first program (X16 infinite loop). Includes key concepts like LIST, RUN, NEW, and line editing.  
**Tone:** Patient and encouraging, with deliberate key-by-key instructions perfect for absolute beginners.  
**Pacing:** Well-paced progression from single commands to a complete program.  
**Continuity:** Strong setup for later chapters; explicitly tells readers they can skip to any chapter.  
**Suggestions:**
- Minor: The chapter references \runstopkey but could note PC equivalent (Esc/Pause) more prominently for non-X16 keyboard users

---

#### ✅ Chapter 2: Using Screen & Keyboard ([ch02_using_screen_and_keyboard.tex](ch02_using_screen_and_keyboard.tex)) — Complete
**Status:** Publication-ready  
**Content:** Thorough coverage of PRINT statement (strings vs. numbers), graphic characters (PETSCII), colors (keyboard shortcuts and COLOR statement), screen modes (SCREEN command, 40/80 column toggle), the full-screen editor (cursor movement, INSERT, DELETE, backspace), and file operations (SAVE, LOAD, SCRATCH).  
**Tone:** Hands-on and explorative, encouraging experimentation.  
**Pacing:** Good progression from simple printing to file management.  
**Continuity:** Natural bridge to Chapter 3 (colors are introduced here, expanded there). Minor concept overlap with Chapter 3's color section is intentional and reinforcing.  
**Suggestions:**
- Add a keyboard layout diagram illustration showing graphic character locations
- The color table appears in both Ch2 and Ch3 — this is acceptable for reference but could note "see Chapter 3 for more detail"

---

#### ✅ Chapter 3: Color and Graphics ([ch03_color_and_graphics.tex](ch03_color_and_graphics.tex)) — Complete
**Status:** Publication-ready  
**Content:** Deep dive into COLOR statement, 16 colors table, foreground/background colors, color keys (CTRL/ALT+number), reverse mode (RVS ON/OFF), screen/border colors, SCREEN modes with borders, LOCATE statement, TAB function, TILE statement with screen codes and color values, random colors, PETSCII keyboard graphics (drawing boxes, pictures), and a color+sound combination example.  
**Tone:** Creative and playful, encouraging artistic exploration.  
**Pacing:** Excellent — builds from simple color changes to complex PETSCII art.  
**Continuity:** The color+sound teaser at the end nicely foreshadows Chapter 5.  
**Suggestions:**
- None significant — comprehensive and well-structured

---

#### ✅ Chapter 4: Animation ([ch04_animation.tex](ch04_animation.tex)) — Complete
**Status:** Publication-ready  
**Content:** Animation fundamentals explained via the "cartoon frames" analogy. Covers TAB-based animation, the classic bouncing ball (with TILE), cursor control characters for animation, VPOKE direct screen memory access, and complex examples (flying birds with wing-flapping, multiple birds with arrays, scrolling starfield).  
**Tone:** Exciting and visual — captures the fun of making things move.  
**Pacing:** Excellent progression from simple horizontal motion to multi-object animation.  
**Continuity:** References Chapter 3 for graphic characters; sets up concepts used in games (Chapter 7).  
**Suggestions:**
- The VPOKE section is well-handled with appropriate "this is advanced" caveats
- Could add a brief mention that sprites exist for more complex animation (covered in appendices/reference guide)

---

#### ✅ Chapter 5: Sound and Music ([ch05_sound_and_music.tex](ch05_sound_and_music.tex)) — Complete
**Status:** Publication-ready  
**Content:** Outstanding coverage of both sound chips (PSG with 16 voices, YM2151 FM with 8 channels). Explains waveforms (pulse, sawtooth, triangle, noise), FM instruments (160+ patches), PSGNOTE/FMNOTE commands, PSGPLAY/FMPLAY music strings, chord commands, sound effects (beep, explosion, laser, siren, power-up), a working piano program, and complete songs (Happy Birthday, Twinkle Twinkle, Frère Jacques with bass).  
**Tone:** Musical and accessible — no prior music knowledge required.  
**Pacing:** Perfect build from single beeps to multi-voice arrangements.  
**Continuity:** References Chapter 3's color+sound example; provides foundation for sound in games (Chapter 7).  
**Suggestions:**
- None — this is exceptionally comprehensive for a user guide

---

#### ✅ Chapter 6: Conversing with Your X16 ([ch06_conversing_with_x16.tex](ch06_conversing_with_x16.tex)) — Complete
**Status:** Publication-ready  
**Content:** Covers INPUT statement, prompts, string variables (with $), numeric variables, variable naming rules (2-character significance), changing variables (X=X+1 pattern), GET statement for instant keypresses, menu creation, and practical programs (temperature converter, number picker).  
**Tone:** Conversational and friendly — the "What's Your Name?" opener matches the VIC-20 perfectly.  
**Pacing:** Well-structured progression from INPUT to GET to practical applications.  
**Continuity:** Builds directly on concepts from Chapters 1-2; essential foundation for Chapter 7's games.  
**Suggestions:**
- None — faithfully follows the VIC-20 structure while being X16-specific

---

#### ✅ Chapter 7: Introduction to Programming ([ch07_introduction_to_programming.tex](ch07_introduction_to_programming.tex)) — Complete
**Status:** Publication-ready  
**Content:** Comprehensive programming fundamentals including RND function, INT function, the random number formula (INT(N*RND(1))+1), IF...THEN conditionals, comparison operators (<, >, =, <>, <=, >=), string comparisons, FOR...NEXT loops, STEP keyword, negative STEP for countdown, delay loops, REM comments, and complete games (basic guessing game, improved guessing game with hints and scoring, dice roller).  
**Tone:** Empowering and game-focused — readers finish ready to create.  
**Pacing:** Builds logically to the guessing game as a capstone project.  
**Continuity:** Brings together INPUT (Ch6), RND (new), and logic to create real programs.  
**Suggestions:**
- Could briefly mention READ/DATA for larger games (or note it's in the BASIC reference appendix)
- The "Best Strategy" tip about binary search is a delightful touch

---

### 📊 Summary Status Table

| Chapter | Status | Completeness | Polish Level |
|---------|--------|--------------|--------------|
| Preface | ✅ Complete | 100% | Publication-ready |
| Setup | ✅ Complete | 100% | Publication-ready |
| Ch 1: Getting to Know | ✅ Complete | 100% | Publication-ready |
| Ch 2: Screen & Keyboard | ✅ Complete | 100% | Minor polish (keyboard diagram) |
| Ch 3: Color and Graphics | ✅ Complete | 100% | Publication-ready |
| Ch 4: Animation | ✅ Complete | 100% | Publication-ready |
| Ch 5: Sound and Music | ✅ Complete | 100% | Publication-ready |
| Ch 6: Conversing | ✅ Complete | 100% | Publication-ready |
| Ch 7: Intro to Programming | ✅ Complete | 100% | Publication-ready |
| Appendices | ✅ Complete | 100% | Publication-ready |

**Appendix Notes:**
- **BASIC Commands Reference** now includes origin tags (Commodore 64 / Commander X16 / Commodore 128) for each command, statement, function, and system variable
- Added missing X16-specific commands: `BASLOAD`, `BSAVE`, `JOY`, `MOD`
- Removed separate BASIC keyword table (consolidated into main reference)
- Removed YM2151 Registers appendix (too advanced for beginner user guide)

### 🔍 Continuity & Cross-Reference Review

**Strengths:**
- Each chapter's opening type-in program effectively previews the chapter content
- Concepts build naturally: PRINT → colors → animation → sound → input → programming
- Appropriate forward/backward references between chapters
- Consistent use of VIC-20-style "bubbles" for visual explanations
- Unified tip/note/tryit boxes throughout

**Minor Overlaps (Acceptable):**
- Color table appears in both Ch2 and Ch3 — serves as reference in both contexts
- PRINT fundamentals reviewed briefly in Ch2 after Ch1 introduction — reinforcing, not repetitive

**No Gaps Found:**
- All VIC-20 chapter topics are covered
- X16-specific features (VERA, FM/PSG, TILE, VPOKE) are appropriately integrated
- File operations (LOAD/SAVE) covered in Ch2

### 📋 Remaining Polish Items

| Priority | Item | Location | Effort |
|----------|------|----------|--------|
| 🟢 Low | Add keyboard diagram illustration | Ch 2 | Medium (requires artwork) |
| 🟢 Low | Note PC keyboard equivalents for special keys | Ch 1, Ch 2 | Small |
| 🟢 Low | Brief sprite mention as "advanced topic" | Ch 4 | Small |

### 🆕 Suggested Future Enhancements (Post-v1.0)

These topics would extend the guide beyond VIC-20 parity. They could be added as appendices or bonus chapters:

| Topic | Priority | Rationale |
|-------|----------|-----------|
| **SD Card & DOS Commands** | 🟡 Medium | Directory navigation, file management beyond SAVE/LOAD |
| **Sprites via BASIC** | 🟡 Medium | X16's 128 sprites are a major feature |
| **Bitmap Graphics (LINE, RECT, CIRCLE)** | 🟡 Medium | X16 BASIC includes drawing commands |
| **Using the Emulator** | 🟢 Low | Helpful for testing/development |

### Original VIC-20 User's Guide Chapters (Reference)

The VIC-20 User's Guide is considered one of the best computer manuals ever written—the primary inspiration for this X16 guide.

| Chapter | Content Summary |
|---------|----------------|
| **Preface** | Welcome, philosophy of the manual |
| **Setup** | Hardware setup, TV hookup, first power-on |
| **Ch 1**: Getting to Know Your VIC | Getting Started, Your First Computer Program |
| **Ch 2**: Using the Screen and Keyboard | Graphic characters, keyboard tour, printing, calculator, intro to color |
| **Ch 3**: Color and Graphics | COLOR, color keys, screen/border colors, screen locations, keyboard graphics |
| **Ch 4**: Animation | Flying birds, bouncing ball, cursor control, PEEK/POKE animation |
| **Ch 5**: Sound and Music | Making music, four voices, white noise, piano program, songs |
| **Ch 6**: Conversing with Your VIC | INPUT, variables, GET statement |
| **Ch 7**: Introduction to Programming | BASIC commands, random numbers, IF/THEN, FOR/NEXT |
| **Appendices** | BASIC reference, screen codes, memory map, sample programs, error messages |

### ✅ VIC-20 Parity Checklist

| VIC-20 Feature | X16 Coverage | Status |
|----------------|--------------|--------|
| Welcome & philosophy | Preface | ✅ Complete |
| Hardware setup | Ch 0 | ✅ Complete |
| First program (PRINT, GOTO) | Ch 1 | ✅ Complete |
| Keyboard & graphic characters | Ch 2 | ✅ Complete |
| Colors (keyboard & statements) | Ch 2, Ch 3 | ✅ Complete |
| Screen modes | Ch 2, Ch 3 | ✅ Complete |
| Animation techniques | Ch 4 | ✅ Complete |
| Sound & music | Ch 5 | ✅ Complete |
| INPUT & variables | Ch 6 | ✅ Complete |
| GET statement | Ch 6 | ✅ Complete |
| RND, IF/THEN, FOR/NEXT | Ch 7 | ✅ Complete |
| Sample programs | Appendix | ✅ Complete |
| Error messages | Appendix | ✅ Complete |
| BASIC reference | Appendix | ✅ Complete |
| Screen/PETSCII codes | Appendix | ✅ Complete |
| Memory map | Appendix | ✅ Complete |

### Legend

- ✅ **Complete** — Chapter is written, reviewed, and publication-ready
- 🔶 **Needs Polish** — Minor improvements suggested
- 🟡 **Medium Priority** — Important enhancement for future versions
- 🟢 **Low Priority** — Nice to have

---

