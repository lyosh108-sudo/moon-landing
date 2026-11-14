# Moon Landing / Посадка на Луну

A browser adaptation of a Soviet programmable calculator game from the 1988 book *Five Evenings with a Microcalculator* by I. D. Danilov and G. V. Slavin.

Браузерная версия игры «Посадка на Луну» из книги И. Д. Данилова и Г. В. Славина «Пять вечеров с микрокалькулятором» (Москва: «Финансы и статистика», 1988).

**Играть / Play:** https://lyosh108-sudo.github.io/moon-landing/

## Project History

This project began with a memory of playing “Moon Landing” on a Soviet Elektronika MK-56 programmable calculator around 1988.

The goal was to recreate that particular game—not to build a new simulator with a similar theme, but to translate the original algorithm into a modern implementation.

The game was vibe-coded through a conversation with Perplexity GPT 6.1 Sol with reasoning, from identifying the source and interpreting the calculator program to verifying the calculations, building the interface, and preparing the page for publication on GitHub Pages.

## Sources

The primary sources were scans of pages 67–69 of *Five Evenings with a Microcalculator*, provided by the project creator. These pages contain:

- The original calculator program listing.
- Instructions for starting and controlling the game.
- Initial conditions.
- Explanations of the landing ratings.
- A complete reference flight, including fuel inputs and intermediate results.

An additional source was a video transcript showing the game running on a real MK-56 and being checked against the example in the book.

When reconstructing the algorithm, the scanned book pages took priority over automatically recognized text.

## Reconstructing the Program

### 1. Interpreting the Original Listing

The calculator instructions were translated into ordinary variables and arithmetic expressions.

This is not an MK-56 emulator: the project does not reproduce its processor, keyboard, stack, or internal arithmetic. Instead, it translates the program’s game logic.

The instruction at address `37` was corrected from the printed `ИПВ` (recall register B) to `ИП8` (recall register 8). With this correction, the algorithm reproduces the reference altitudes in the book.

### 2. Verification in Python

The algorithm was first implemented in Python and tested against the complete reference flight.

Results:

- All 19 published reference altitudes matched within the book’s rounding precision.
- The velocity after the third step matched the stated 128.4 m/s.
- The checked fuel balances matched.
- The final rating was `3.1111111`, meaning a hard landing.
- The remaining fuel after landing was 82 metric tonnes.

Two discrepancies were found between the reconstructed algorithm and the book’s narrative:

- After the seventh step, the algorithm gives a velocity of approximately 79.631 m/s, while the book states 76.6 m/s. The reference altitude still matches.
- The full input sequence ends on step 22, while the text states a flight time of 21 seconds.

The implementation was not adjusted to force agreement with these two printed values. It preserves the results of the reconstructed algorithm.

### 3. Bringing the Game to the Browser

After verifying the Python version, the calculations were translated into JavaScript.

The browser engine was tested again using the same reference flight. A built-in verification test is available on the game page; it runs separately without affecting the player’s current flight.

The interface, styles, and game logic are contained in a single standalone HTML file, with no external libraries or network dependencies.

## Running Locally

Download `index.html` and open it in a browser.

No Python installation, local server, or additional packages are required. The game can run without an internet connection.

## Acknowledgments

Thanks to I. D. Danilov and G. V. Slavin for the book that preserved the program and its reference example.
An additional source was a [video demonstration on the “Ретро вычислительные устройства” channel](https://www.youtube.com/watch?v=BK8An3W0VuU), showing the game running on a real Elektronika MK-56 and being checked against the example in the book. A transcript of this video helped identify the source and cross-check the first steps of the reference flight.

This project is a modern adaptation of a historical game. It does not claim authorship of the original calculator program.
