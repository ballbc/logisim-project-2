# S23-CSCE211-001: Project 2

### Group Members: Bee Ball, Nia Sparacino, Joshua Ramon-Cruz

- Bee: Decimal Logic Solving, Simplifying, README, Github Creation, Logisim Evolution Implementation, Logisim Conversion, General Collaboration, Support
- Nia: Hex Logic Solving, Conversion to SOP Form, General Collaboration, Support
- Joshua: README, Group Communication, General Collaboration, Support

---

## Implementation Description:

### General Outline:

- First the implementation of the requirements was assigned the corresponding logic so that the counters and their drivers may act and react according to the inputs and outputs.
- Then, using the truth tables, the logic was implemented in such a manner to achieve the desired output. First implemented in Logisim Evolution and then converted to Logisim. 

We implemented this project by first creating a four-bit adder made from two two-bit adders, made out of two one-bit adders. All circuits were created from scratch. 

We then reused the decimal display driver logic from project 1, and created a second chip that would output the unchanged output from the adder if that number was less than binary 10, and would output 10 subtracted from that number if it was over binary 10, as well as an extra pin to signal whether the tens place digit is 0 or 1. 

Two counters, one linked to the other such that the second driver will increment once each time the first driver has enumerated 0-9, both with decimal displays inline, will be added with the 4-bit adder, then that binary digit is passed to the special chip which will separate the 4-bit binary number into it's proper decimal representation, and display that value with two more 7 segment displays.

---

## Truth Tables:

### 1-bit adder:

|A|B |Cin|0|C0|C|Cj|A|B |0|C0|
| :- | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- |
|<p>0</p><p>0</p>|<p>0</p><p>0</p>|<p>0</p><p>1</p>|<p>0</p><p>1</p>|<p>0</p><p>0</p>|0|<p>0</p><p>0</p>|<p>0</p><p>0</p>|<p>0</p><p>1</p>|<p>0</p><p>1</p>|<p>0</p><p>0</p>|
|<p>0</p><p>0</p>|<p>1</p><p>1</p>|<p>0</p><p>1</p>|<p>1</p><p>0</p>|<p>0</p><p>1</p>|C|<p>0</p><p>0</p>|<p>1</p><p>1</p>|<p>0</p><p>1</p>|<p>1</p><p>0</p>|<p>0</p><p>1</p>|
|<p>1</p><p>1</p>|<p>0</p><p>0</p>|<p>0</p><p>1</p>|<p>1</p><p>0</p>|<p>0</p><p>1</p>|<p>C</p><p></p>|<p>1</p><p>1</p>|<p>0</p><p>0</p>|<p>0</p><p>1</p>|<p>1</p><p>0</p>|<p>0</p><p>1</p>|
|<p>1</p><p>1</p>|<p>1</p><p>1</p>|<p>0</p><p>1</p>|<p>0</p><p>1</p>|<p>1</p><p>1</p>|<p>1</p><p></p>|<p>1</p><p>1</p>|<p>1</p><p>1</p>|<p>0</p><p>1</p>|<p>0</p><p>1</p>|<p>1</p><p>1</p>|

### "Nia's Chip" - Subtract 10 Logic Truth Table:
- A0 = S4+S3S2+S3S1
- B3 = Sc1S1+S3S’2+S’1
- B2 = S’3S2+S2S1+S4S’1
- B1 = S4S’1+S’4S
- B0= S0

||a|b|c|d|e||10’s Place|1’s Place|1’s Place|1’s Place|1’s Place|
| :- | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- |
||S4|S3|S2|S1|S0||A0|B3|B2|B1|B0|
|0|0|0|0|0|0||0|0|0|0|0|
|1|0|0|0|0|1||0|0|0|0|1|
|2|0|0|0|1|0||0|0|0|1|0|
|3|0|0|0|1|1||0|0|0|1|1|
|4|0|0|1|0|0||0|0|1|0|0|
|5|0|0|1|0|1||0|0|1|0|1|
|6|0|0|1|1|0||0|0|1|1|0|
|7|0|0|1|1|1||0|0|1|1|1|
|8|0|1|0|0|0||0|1|0|0|0|
|9|0|1|0|0|1||0|1|0|0|1|
|10|0|1|0|1|0||1|0|0|0|0|
|11|0|1|0|1|1||1|0|0|0|1|
|12|0|1|1|0|0||1|0|0|1|0|
|13|0|1|1|0|1||1|0|0|1|1|
|14|0|1|1|1|0||1|0|1|0|0|
|15|0|1|1|1|1||1|0|1|0|1|
|16|1|0|0|0|0||1|0|1|1|0|
|17|1|0|0|0|1||1|0|1|1|1|
|18|1|0|0|1|0||1|1|0|0|0|
|19|1|0|0|1|1||X|X|X|X|X|
|20|1|0|1|0|0||X|X|X|X|X|
|21|1|0|1|0|1||X|X|X|X|X|
|22|1|0|1|1|0||X|X|X|X|X|
|23|1|0|1|1|1||X|X|X|X|X|
|24|1|1|0|0|0||X|X|X|X|X|
|25|1|1|0|0|1||X|X|X|X|X|
|26|1|1|0|1|0||X|X|X|X|X|
|27|1|1|0|1|1||X|X|X|X|X|
|28|1|1|1|0|0||X|X|X|X|X|
|29|1|1|1|0|1||X|X|X|X|X|
|30|1|1|1|1|0||X|X|X|X|X|
|31|1|1|1|1|1||X|X|X|X|X|

---

## Quirks:

Some problems were encountered when transferring material from Logisim Evolution to Logisim. Such as gate inputs being increased and wires not fully displaying. These were manually fixed.
