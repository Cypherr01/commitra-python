## What Is This?
Computers "think" in binary—a language of **only 0s and 1s**—because their circuits exist in two electrical states: off (0) or on (1). Imagine a light switch: it can only be "up" (off) or "down" (on). Binary is the foundation of all digital data, from your emails to cat videos. This matters to you because every program you write ultimately reduces to patterns of 0s and 1s controlling hardware.

## How It Works Internally
### Layer 1 — Minimum Viable Version
Computers use **base-2 (binary)** because transistors (tiny electronic switches) have two stable states. Humans use **base-10 (decimal)** because we have 10 fingers. Other bases like **hexadecimal (base-16)** and **octal (base-8)** exist as shorthand for binary. Conversions between bases use division/remainder math. Negative numbers use **two's complement** (flip bits + add 1). Overflow occurs when numbers exceed storage limits.

### Layer 2 — Why the Simple Version Breaks
Naively assuming "more digits = bigger number" fails in binary. Example: An 8-bit system maxes at 255 (11111111). Adding 1 becomes 00000000 (0) with a carry flag—**overflow**. Ignoring two's complement leads to incorrect negatives. Using decimal logic for binary conversions causes errors (e.g., "10" in binary = 2 in decimal, not 10).

### Layer 3 — The Production Version
- **Binary**: Base-2. Each digit represents a power of 2 (right to left: 2⁰, 2¹, 2²...).
- **Decimal**: Base-10. Digits 0-9, powers of 10.
- **Hexadecimal**: Base-16. Digits 0-9 + A-F (10-15). 1 hex digit = 4 binary bits (e.g., F = 1111).
- **Octal**: Base-8. Digits 0-7. 1 octal digit = 3 binary bits.
- **Conversions**: Use repeated division by the base. For two's complement: invert bits and add 1.
- **Overflow**: Hardware triggers a flag; software must handle it (e.g., upgrade to 16-bit numbers).

### Layer 4 — Edge Cases and Failure Modes
1. **Negative Zero in Two's Complement**:  
   Trigger: Calculating -0 (same as 0).  
   Symptom: Wastes computation.  
   Fix: Normalize to positive zero.  
2. **Silent Hex Overflow**:  
   Trigger: Storing FF (255) in 8-bit space as 100 (4) due to wrong base.  
   Symptom: Data corruption.  
   Fix: Validate base during conversion.  
CORE INSIGHT: All numbers are agreements between hardware and software—break the rules, and your data breaks.

## Syntax and Structure
```text
# CONCEPTUAL PSEUDOCODE: Decimal to Binary Conversion
# STEP 1: Take a decimal number (e.g., 13)
# STEP 2: Divide by 2, record remainder (13 / 2 = 6 rem 1)
# STEP 3: Repeat with quotient (6 / 2 = 3 rem 0)
# STEP 4: Continue until quotient is 0 (3/2=1 rem 1; 1/2=0 rem 1)
# STEP 5: Read remainders bottom-to-top: 1101 = binary 13
# STEP 6: For hex: Group binary into 4-bit chunks (pad with leading zeros)
# STEP 7: Map each 4-bit group to hex digits (0001=1, 1010=A)
# In Phase 1 we will write this in real code.
```

## Common Mistakes Beginners Make
1. **Confusing Base Context**: Writing "10" and assuming it's ten in every base.  
   Wrong idea: Binary "10" = decimal 10.  
   Correct idea: Binary "10" = decimal 2.  
2. **Silent Two's Complement Error**:  

```text
   # Pseudocode example:
   # Wrong: Negative = invert bits ONLY
   # Correct: Negative = invert bits THEN add 1
```
3. **Ignoring Overflow at Scale**: Testing with small numbers (e.g., 8-bit max 255) but deploying to systems handling millions.  
4. **Missing Leading Zeros**: Forgetting to pad binary numbers to consistent bit-lengths (e.g., 3 vs 0011).  
5. **Interview Question**:  
   *How does two's complement represent -1 in 8 bits?*  
   Surface answer: "All 1s (11111111)."  
   Production answer: "It simplifies hardware—addition works for negatives without special circuits."

## Verification Task 1 — Debug This
Your system shows **garbage values when storing numbers > 255**. You have **8-bit memory blocks**. Diagnose and fix.

## Solution 1
The system uses 8-bit binary (max 255). Numbers exceeding this cause **overflow**. Fix: Upgrade to 16-bit storage or add overflow checks. This matters because ARIA's sensors generate values beyond 255.

## Verification Task 2 — Design Decision
Building a compact data format. Use **hexadecimal** or **binary** for transmission? Defend using this topic.

## Solution 2
Choose hexadecimal. Why?  
- **Compactness**: 1 hex digit = 4 binary bits → 25% smaller payloads.  
- **Human readability**: Direct mapping (e.g., "FF" vs. "11111111") reduces interpretation errors.  
- **Structural alignment**: Groups binary into 4-bit segments, simplifying integration with byte-level operations (2 hex digits = 1 byte).  

This leverages base relationships and conversion efficiency—core principles of this topic—without referencing future concepts.
## Verification Task 3 — Code Review
Find the bug in this pseudocode conversion:

```text
# Convert decimal 25 to binary:
quotient = 25
binary = ""
while quotient > 0:
    remainder = quotient % 2
    binary = str(remainder) + binary  # BUG HERE
    quotient = quotient // 2
```

## Solution 3
The loop stops when `quotient` becomes 0, but misses the final division. Fix: Add one more remainder capture after the loop. Correct binary: `11001`.

## What Comes Next
The next topic is **Bits, Bytes & Data Representation**. Binary explains *how* numbers are stored, but bits/bytes reveal *where* and *how much* memory they occupy. Understanding binary is prerequisite for mapping data to physical hardware efficiently.

## Reference Summary
Binary (base-2) is computing's foundational language, using 0s/1s to represent all data. Decimal (base-10) and hexadecimal (base-16) serve human readability and binary shorthand. Conversions between bases use division/remainder math, while two's complement enables negative numbers. Overflow occurs when values exceed storage limits, risking data corruption. This topic is critical because ARIA's systems process sensor data in binary, requiring precise conversions for accurate real-world decisions. Mastery here enables efficient memory use in the next topic: Bits, Bytes & Data Representation.