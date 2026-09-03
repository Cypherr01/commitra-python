## What Is This?
Computers speak in pulses of electricity — **on** or **off**, like a light switch. Binary is their native language: a system of counting using only two digits (0 and 1) to represent every number, instruction, and piece of data. Imagine Morse code for machines: sequences of dots (1) and dashes (0) encode entire messages. This matters to you because binary is the foundation of all digital systems — without it, your code, photos, and even this lesson would be unreadable to a computer.

## How It Works Internally

### Layer 1 — Minimum Viable Version
- **Why binary?** Transistors (tiny switches) in CPUs have two stable states: 0 volts (off) or full voltage (on). This reliability makes binary ideal for error-free computation.
- **Binary (base-2):** Counts like this: 0, 1, 10, 11, 100... Each position represents a power of 2 (rightmost is 2⁰=1, next 2¹=2, etc.).
- **Decimal (base-10):** Humans use 10 digits (0-9) because we have 10 fingers. Each position is a power of 10 (e.g., 345 = 3×10² + 4×10¹ + 5×10⁰).
- **Hexadecimal (base-16):** Uses 0-9 and A-F (10-15). Compact shorthand for binary: 1 hex digit = 4 binary bits (e.g., hex "F" = binary "1111").
- **Octal (base-8):** Uses 0-7. Rarely used today, but critical for Unix file permissions (e.g., "755" defines read/write/execute access).
- **Conversions:** Algorithms translate between bases. For example, decimal → binary via repeated division by 2.
- **Two's complement:** Stores negative numbers by inverting bits and adding 1 (e.g., -5 in 8-bit: `11111011`).
- **Overflow:** When a calculation exceeds a number's allocated space (e.g., 8-bit max is 255; 256 becomes 0).

### Layer 2 — Why the Simple Version Breaks
**Naive misunderstanding:** Beginners often assume numbers work like decimal everywhere. Reality: Fixed-size storage (e.g., 8-bit) limits range. For example, adding 255 + 1 in 8-bit binary wraps to 0 (overflow), not 256. Ignoring this causes silent corruption in sensors, game scores, or financial systems.

### Layer 3 — The Production Version
Computers use **fixed-width binary** (e.g., 8/16/32/64 bits) for numbers. Key additions:
- **Sign bit:** Leftmost bit flags negative numbers (1 = negative).
- **Two's complement:** Enables subtraction using addition (e.g., 5 - 3 = 5 + (-3)).
- **Overflow handling:** Hardware flags warn when results exceed storage capacity.
- **Hex/octal shortcuts:** Engineers use hex for memory addresses (e.g., `0x7F`) and octal for permissions (e.g., `chmod 644`).

### Layer 4 — Edge Cases and Failure Modes
1. **Negative zero:** In two's complement, `-0` equals `0` but wastes storage space. Trigger: Storing -0 in a register. Fix: Normalize to positive zero.
2. **Overflow in counters:** A game's 8-bit score (max 255) resets to 0 at 256. Detection: Check overflow flag after increment. Fix: Use 16-bit storage.
CORE INSIGHT: All numbers are binary approximations — understand their limits to avoid silent failures.

## Syntax and Structure
```text
# STEP 1: Take a decimal number (e.g., 42)
# STEP 2: Divide by 2 → quotient 21, remainder 0 (least significant bit)
# STEP 3: Divide quotient (21) by 2 → 10 rem 1
# STEP 4: Repeat: 10/2 → 5 rem 0; 5/2 → 2 rem 1; 2/2 → 1 rem 0; 1/2 → 0 rem 1
# STEP 5: Collect remainders from last to first: 101010 (binary 42)
# STEP 6: For hex: Group binary into 4-bit chunks (pad with leading zeros if needed)
# STEP 7: Map each 4-bit group to hex (e.g., 0010 → 2; 1010 → A → decimal 42 = hex 2A)
# In Phase 1 we will write this in real code.
```

## Common Mistakes Beginners Make
1. **Ignoring bit width:** Assuming "binary" means infinite precision. Reality: 8-bit storage can't hold 300 → overflow occurs.
2. **Hexadecimal confusion:**  
   Wrong idea: `G` is a valid hex digit.  
   Correct idea: Only 0-9 and A-F (10-15). `G` causes parsing errors.
3. **Skipping two's complement:** Treating negative numbers as "minus positive." This breaks calculations in embedded systems (e.g., thermostats).
4. **Octal permission typos:** Using `777` (full access) instead of `644` (secure files). This exposes sensitive data.
5. **Interview question:**  
   *Convert decimal 255 to 8-bit binary and hexadecimal.*  
   Surface answer: `11111111` binary, `FF` hex.  
   Production answer: Note that 255 is the 8-bit max; adding 1 causes overflow to 0.

## Verification Task 1 — Debug This
Your system shows **temperature readings stuck at -1°C**. You have:  
- Sensor data stored in 8-bit two's complement.  
- Raw value: `11111111`.  
Diagnose and fix.

## Solution 1
The value `11111111` in 8-bit two's complement represents -1. The sensor likely returned an error code instead of valid data. Fix: Add error-checking to reject out-of-range values before storage.

## Verification Task 2 — Design Decision
Building a compact data format for IoT sensors. Use **hexadecimal** or **binary** for transmitting numbers? Defend using this topic.

## Solution 2
Choose hexadecimal. Reason: Hex reduces 4 binary digits to 1 character (e.g., `FF` vs `11111111`), cutting transmission size by 75%. This saves bandwidth and battery life, critical for IoT.

## Verification Task 3 — Code Review
Find the bug in this pseudocode for decimal-to-binary conversion:
```text
# INPUT: decimal_num = 42
# STEP 1: binary_str = ""
# STEP 2: WHILE decimal_num > 0:
# STEP 3:     remainder = decimal_num % 2
# STEP 4:     binary_str = str(remainder) + binary_str
# STEP 5:     decimal_num = decimal_num // 2
# STEP 6: PRINT binary_str
```

## Solution 3
The loop stops when `decimal_num` becomes 0, but **misses the final remainder**. Fix: Add one final division after the loop to capture the last `1` (e.g., for 42, the loop ends at 1 → `10101`, but needs `101010`).

## What Comes Next
The next topic is **Bits, Bytes & Data Representation**. Binary is the foundation: bits (binary digits) combine into bytes (8-bit units) to store all data. This topic teaches how memory allocates space for numbers, text, and images — directly using the base conversions and overflow concepts you just learned.

## Reference Summary
Binary (base-2) is computing's native language, using 0s and 1s to represent all data. Computers rely on fixed-width storage (e.g., 8/16/32 bits), making overflow handling critical. Hexadecimal (base-16) and octal (base-8) provide compact binary shorthand for engineers. Two's complement enables negative numbers, while base conversions bridge human (decimal) and machine (binary/hex) workflows. In ARIA, this ensures sensors and systems encode data efficiently. Mastery prevents silent corruption from overflow and invalid values.