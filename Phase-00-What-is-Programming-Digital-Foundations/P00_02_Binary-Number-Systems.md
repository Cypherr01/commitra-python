## What Is This?
Computers "think" in electricity, which only has two stable states: **on** (charged) or **off** (uncharged). Binary is the language of these states, using 0s and 1s to represent all data—from text to images. Imagine a relay baton in a race: it’s either *held* (1) or *not held* (0) at each handoff. Binary’s simplicity makes it reliable for machines, but humans need translations like decimal or hex to interact meaningfully.

## How It Works Internally
### Layer 1 — Minimum Viable Version
Binary (base-2) uses only **0** and **1** to count. Each position represents a power of 2:  
`1` = 2⁰ (1), `10` = 2¹ (2), `11` = 2¹ + 2⁰ (3).  
Decimal (base-10) uses digits 0–9, each a power of 10:  
`3` = 3×10⁰, `42` = 4×10¹ + 2×10⁰.  
Hexadecimal (base-16) compresses binary into 0–9 and A–F (10–15), where each hex digit = 4 binary bits. Octal (base-8) uses 0–7, historically used in Unix permissions.

### Layer 2 — Why the Simple Version Breaks
**Problem 1:** Negative numbers. Basic binary can’t represent them.  
**Problem 2:** Large numbers exceed bit limits (e.g., 8 bits max = 255). Adding 1 causes **overflow**, wrapping to 0.  
**Problem 3:** Base confusion. Misinterpreting `11` as binary (3) vs. decimal (11) corrupts data.

### Layer 3 — The Production Version
- **Two’s complement** solves negatives: invert bits and add 1 (e.g., -5 in 8-bit: `11111011`).  
- **Base conversions** use division/remainder algorithms (e.g., decimal to hex: divide by 16, map remainders to 0–F).  
- **Overflow handling** requires checking arithmetic results against bit limits (e.g., 32-bit integers: -2³¹ to 2³¹−1).

### Layer 4 — Edge Cases and Failure Modes
1. **Overflow in sensors**: A temperature sensor using 8-bit unsigned integers (0–255) reads -1°C as `255` (wrapping).  
   *Fix: Use signed integers or 16-bit ranges.*  
2. **Hex misinterpretation**: A memory address `0x1A` (26 decimal) is read as decimal `114` (corrupting data).  
   *Fix: Explicitly label hex values (e.g., `0x` prefix).*  
CORE INSIGHT: All numbers are stored as binary patterns; bases are human translations.

## Syntax and Structure
```text
# STEP 1: Represent the decimal number 25 in binary
#   Divide by 2, record remainders: 25 / 2 = 12 rem 1 → LSB
#   12 / 2 = 6 rem 0
#   6 / 2 = 3 rem 0
#   3 / 2 = 1 rem 1
#   1 / 2 = 0 rem 1 → MSB
#   Binary: 11001 (MSB to LSB)
# STEP 2: Convert binary 11001 to hexadecimal
#   Split into 4-bit chunks: 1 1001 → pad to 0001 1001
#   0001 = 1, 1001 = 9 → Hex: 0x19
# STEP 3: Store -5 using 8-bit two's complement
#   Binary +5: 00000101 → invert → 11111010 → add 1 → 11111011
# STEP 4: Detect overflow in 8-bit unsigned math (250 + 15 = 14)
#   If result < min(operand) → overflow occurred
In Phase 1 we will write this in real code.
```

## Common Mistakes Beginners Make
- **Wrong idea**: "Binary digits are called `bytes`."  
  Correct idea: A **bit** is one 0/1. A **byte** = 8 bits (e.g., `01101010`).  
- **Silent bug**: Forgetting two’s complement in temperature checks:  

```text
  # Pseudocode example (Phase 1 concept)
  if temperature > 0:  # Fails for -5 stored as 251 (unsigned)
      shut_down_reactor()
```
  Trigger: Negative values treated as large positives.  
- **Scale breaker**: Ignoring bit limits in IoT devices. An 8-bit moisture sensor overflowing at 256% humidity crashes irrigation systems.  
- **Missed config**: Omitting `0x` in hex literals. `FF` vs. `0xFF` causes syntax errors in tools.  
- **Interview question**: "Convert `0x1A` to binary and decimal."  
  Surface answer: `00011010` (binary), 26 (decimal).  
  Production answer: "Also check if the system uses signed/unsigned integers to avoid overflow."

## Verification Task 1 — Debug This
**Symptom**: A digital thermostat displays `-256°C` instead of `-1°C`.  
**Evidence**: It uses 8-bit signed integers (two’s complement). Diagnose the error.

## Solution 1
The thermostat stored `-1` as `11111111` (correct two’s complement). However, the display code treats it as an **unsigned integer** (255), then subtracts 256 (assuming signed overflow). Fix: Use consistent signedness in storage and interpretation.

## Verification Task 2 — Design Decision
Building a memory-efficient temperature logger. Use **8-bit unsigned integers** (0–255) or **8-bit signed two’s complement** (-128–127)? Defend your choice.

## Solution 2
Choose **8-bit signed two’s complement** if temperatures can be negative. While it reduces positive range (127 vs. 255), it avoids separate sign bits and handles arithmetic uniformly. For non-negative data (e.g., GPU textures), use unsigned.

## Verification Task 3 — Concept Check
**Flawed explanation**: "Hexadecimal `A` is 1010 in binary. Just replace each hex digit with 4 bits!"  
What’s wrong?

## Solution 3
Hex digits map to **4-bit groups**, but leading zeros matter. For example, hex `A` = `1010`, but hex `3` = `0011` (not `11`). Omitting padding breaks conversions (e.g., `0x3A` becomes `00111010`, not `111010`).

## What Comes Next
The next topic is **Bits, Bytes & Data Representation**. This follows directly because binary is the foundation: understanding how individual bits (0s/1s) group into bytes and represent complex data (integers, text, images) is essential for memory management and file formats. The two’s complement and overflow concepts from this topic will reappear when analyzing byte-level storage.

## Reference Summary
Binary (base-2) is computing’s native language, using 0/1 to represent all data. Humans use decimal (base-10) and hexadecimal (base-16) for readability, while octal (base-8) appears in legacy systems. Conversions between bases and two’s complement (for negatives) are critical for avoiding overflow errors. Misinterpreting number bases or signedness causes silent corruption in production. This topic matters because it underpins data storage, networking, and low-level system operations in projects like ARIA, where binary efficiency is non-negotiable. Mastery enables you to debug hardware-level glitches and optimize memory usage.