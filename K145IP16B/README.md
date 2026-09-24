# К145ИП16Б (K145IP16B)

Single-chip calculator LSI used in the Soviet *Elektronika* **MK-35** and **MK-66 / MK-66A** microcalculators. It contains the arithmetic unit, control logic, keyboard scanning and the display drivers, and works directly with the **ИЛЦ2-12/8Л** 12-position vacuum-fluorescent display.

Marked **КР145ИП16Б** on plastic-packaged parts and **К145ИП16Б** on others; 48 pins.

Display format: 12 positions = mantissa sign + 8 mantissa digits + exponent sign + 2 exponent digits.

---

## Pinout

Signal names below are transcribed from the **MK-35 schematic**, which is the only one of the two sheets that names the nets (column *Цепь*). Pin numbers are from the same sheet.

### Display drive — mantissa (*МАНТИССА*)

Digit/grid strobes. **Р** = *разряд*, "digit position".

| Pin | Original | Function |
|--:|:--|:--|
| 40 | − | Mantissa sign position |
| 39 | 1Р | Mantissa digit 1 |
| 38 | 2Р | Mantissa digit 2 |
| 37 | 3Р | Mantissa digit 3 |
| 36 | 4Р | Mantissa digit 4 |
| 35 | 5Р | Mantissa digit 5 |
| 34 | 6Р | Mantissa digit 6 |
| 33 | 7Р | Mantissa digit 7 |
| 32 | 8Р | Mantissa digit 8 |

### Display drive — exponent (*ПОРЯДОК*)

| Pin | Original | Function |
|--:|:--|:--|
| 41 | − | Exponent sign position |
| 44 | 1Р | Exponent digit 1 |
| 42 | 2Р | Exponent digit 2 |

### Display drive — segments (*СЕГМЕНТЫ*)

| Pin | Original | Segment |
|--:|:--|:--|
| 20 | а | a (top) |
| 23 | б | b (top right) |
| 29 | в | c (bottom right) |
| 28 | г | d (bottom) |
| 25 | д | e (bottom left) |
| 27 | е | f (top left) |
| 26 | ж | g (middle) |
| 30 | и | decimal point |

Russian segment lettering follows а б в г д е ж, which maps to the Western a b c d e f g in the order above; **и** is the decimal point.

### Keyboard inputs

| Pin | Original | Function |
|--:|:--|:--|
| 8 | инф. вход 1 | Information (data) input 1 |
| 9 | инф. вход 2 | Information (data) input 2 |
| 10 | инф. вход 3 | Information (data) input 3 |
| 11 | инф. вход 4 | Information (data) input 4 |
| 18 | инф. вход 5 | Information (data) input 5 |

The keyboard is a matrix scanned by the same digit strobes that drive the display, and read back on these five inputs.

### Clock, power and control

| Pin | Original | Function |
|--:|:--|:--|
| 2 | контр. fт | Clock frequency test point (fт = *тактовая частота*, clock frequency) |
| 4 | контр. fт | Clock frequency test point |
| 5 | Rf | Clock-frequency setting resistor (R24 in the MK-35: 68 k / 82 k / 120 k selected on test) |
| 7 | Uп | Supply voltage (*напряжение питания*) |
| 12 | Уст. "0" | Set to zero — reset |
| 13 | Корпус | Common / case (ground) |
| 16 | Ускор. ввод | "Accelerated input" — see notes |
| 31 | Корпус | Common / case (ground) |
| 46 | рад./град. | Radian / degree select, driven by switch SA2 |

Pins not listed above are not named on either schematic.

---

## Notes from the MK-35 schematic

- *"Rf and Uп are set in accordance with the parameters of chip D1"* — the resistors at pins 5 and 7 are selected per individual chip, not fixed values.
- Switch positions for the documented measurements: SA1 = On, SA2 = "Degrees".
- Operating conditions were measured with a В7-27А voltmeter at a microcalculator supply of −5 V, tolerance ±10 %.
- Waveforms 1–20, 22 and 23 were measured with respect to the positive terminal of the supply, using a С1-76 oscilloscope. Waveforms 13–20 were taken while the display showed **−9.1415926 −87**, which is a useful reference pattern when probing the digit and segment lines.

---

## Uncertainties

- **Pin 16, *Ускор. ввод*.** Literally "accelerated input". On the MK-35 sheet it sits on the same node as the supply capacitors and the ground pins, so it may be supply-related rather than a functional input. Not verified against a datasheet.
- **Pins 2 and 4, *контр. fт*.** Named as clock-frequency monitoring points; whether they are the oscillator's own RC pins or buffered test outputs is not stated on the sheet.

## What the MK-66 schematic shows

The MK-66 sheet gives no net names for D1 — only pin numbers — so it cannot confirm the groupings above. Two things are worth recording:

- D1 is lettered **"К145 ИП15"** on that drawing, not ИП16Б. The scan is faint and this may be a drawing error or a different production run.
- The pins shown along the top edge of D1 (display side), left to right, are: 40, 19, 20, 21, 22, 23, 24, 25, 26, 39, 38, 37, 36, 35, 34, 33, 32, 30, 29, 28, 27. The band 19–26 is wider than the segment group on the MK-35 sheet, which suggests the exponent positions may be on different pins in this design — or that 19, 21, 22 and 24 are misreadings of a faint scan.
- The keypad block's own connector numbering is 1–13: columns 7, 8, 9, 10, 11; rows 1, 3, 4, 5, 6; the power switch SA1 on 2; the degree/radian switch SA2 on 12 and 13. These are keypad terminal numbers, not chip pins.

## Sources

- *Схема электрическая принципиальная микрокалькулятора "Электроника МК35"* — pin/net table for D1 КР145ИП16Б.
- *Схема электрическая принципиальная микрокалькулятора "Электроника МК 66"* — pin numbers only.
