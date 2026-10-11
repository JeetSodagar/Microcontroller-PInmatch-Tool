PinMatch

A single-file web tool for comparing two microcontroller pinouts side by side, to work out whether one part can replace another on an existing board.

Matching pins by hand across two datasheets is slow and error-prone — especially the power, reset and boot pins, which decide whether the board even starts. PinMatch puts both packages on screen, colour-codes every pin by how well it matches, and tells you what would have to change.

Quick start

Open pinmatch.html in any browser. There is no install, no build step, no server and no network access — everything, including the device library, is in the one file.

Pick manufacturer → series → device → package on the left (the part you have).
Do the same on the right (the candidate replacement).
Press Match pins.

Four presets are built in if you just want to see it work.

What you get

Package drawings. Both parts are drawn to their real package outline — QFP-style for LQFP/TQFP/QFN/UFQFPN/VFQFPN, two-row for PDIP/SOIC — with pin numbers, pin names and pin-1 marker. Hovering a pin highlights the same pin number on both chips and in the table. Clicking one opens a detail panel comparing that pin on both devices.

Colour coding.

Colour	Meaning
Green — Exact	Same pin, same function
Blue — Compatible	Same role, different name (e.g. NRST ↔ MCLR, OSC2 ↔ RA6/OSC2)
Amber — Check	GPIO that needs a reroute or a firmware remap
Red — Conflict	Incompatible pin class — e.g. a supply pin landing on a GPIO
Grey — Not present	Pin missing on one side

Power, reset and boot table. The section that answers the real question first. It lists VDD/VCC, VSS/GND, analog supply and reference, VSSA, VBAT, VCAP/DEC, reset, BOOT0, BOOT1, both crystals and the debug pins, with the pin numbers on each part and a same/different verdict.

Specifications. Max clock, supply voltage, flash, RAM, EEPROM, GPIO count, peripheral counts and temperature range, with every difference highlighted.

Pin-by-pin table. All pins with their alternate functions on both parts, filterable by Conflicts / Needs attention / Power & control / Matching, and searchable by pin name.

Export. CSV of the full comparison, including the data sources for both parts, for design reviews.

Also: a dark theme, keyboard-visible focus, and a layout that works down to phone width.

Device library

66 devices. The full list, with the sources used for each, is in pinmatch-sources.md.

Vendor	Devices	Packages covered
STMicroelectronics	25	LQFP32/48/64/100/144, UFQFPN32/48, VFQFPN36
Microchip / Atmel AVR	27	PDIP8/14/20/28/40, TQFP32/44
Microchip PIC	13	PDIP8/28/40
Nordic Semiconductor	1	QFN48

STM32 covers F0, F1, F3, F4, G0, L0, L1 and L4. AVR covers the ATmega48/88/168/328 family, ATmega8A/16A/32A, the ATmega164/324/644/1284 family, and ATtiny13A/24/44/84/ 25/45/85/2313A/4313. PIC covers PIC16F87X and PIC16F87XA, PIC16F88X, PIC12F629/675/683 and PIC18FXX2.
