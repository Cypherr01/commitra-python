# Binary & Number Systems – Phase 0 Lesson

## What Is This?

Binary & Number Systems are the ways computers represent every piece of information using only two symbols—0 (off) and 1 (on).  
Think of a lighthouse that can either shine its light or stay dark; by flashing a pattern of on/off you can spell out any message, just as a computer uses patterns of bits to store numbers, letters, and images.

## How It Works Internally

Below we walk through each bullet‑point from the topic scope, using the four‑layer “How It Works Internally” framework.  

### 1️⃣ Why computers use binary (only two electrical states: on/off)

**Layer 1 – Minimum viable version**  
A computer’s transistor is either conducting electricity (on) or not conducting (off).  

**Layer 2 – Why the simple version breaks**  
If we tried to use three or more voltage levels, noise and manufacturing variations would make it impossible to reliably tell the difference, causing data corruption.  

**Layer 3 – Production version**  
Modern CPUs use millions of transistors that each represent a single bit; the collective pattern of bits encodes all data.  

**Layer 4 – Edge cases**  
- *Edge 1*: In very low‑power devices, voltage margins shrink; designers add error‑detecting circuits to catch mis‑read bits.  
- *Edge 2*: Radiation in space can flip a bit (a “single‑event upset”); ECC memory detects and corrects such flips.  

### 2️⃣ Binary (base‑2) — counting in 0s and 1s

**Layer 1**  
Start counting: 0, 1, 10, 11, 100, 101 … each new digit represents a higher power of two.  

**Layer 2**  
If you stop after a single digit, you can only represent two values; you quickly run out of symbols for larger numbers.  

**Layer 3**  
In practice, computers group bits into bytes (8 bits) so they can represent 0 – 255 in a single chunk.  

**Layer 4**  
- *Edge 1*: When a byte overflows from 11111111 (255) to 00000000, the value wraps around—this is why overflow must be handled.  
- *Edge 2*: Signed numbers use two’s complement; the same 8‑bit pattern can mean +127 or –128 depending on interpretation.  

### 3️⃣ Decimal (base‑10) — how humans count

**Layer 1**  
Humans use ten symbols (0‑9) because we have ten fingers.  

**Layer 2**  
If you tried to count objects larger than nine with only one digit, you would need a new place value, which is exactly what the decimal system does with tens, hundreds, etc.  

**Layer 3**  
Computers still need to translate human‑readable decimal input into binary before any arithmetic can happen.  

**Layer 4**  
- *Edge 1*: Floating‑point numbers store decimal fractions in binary, leading to rounding quirks (e.g., 0.1 cannot be represented exactly).  
- *Edge 2*: Legacy systems sometimes store decimal digits in “packed BCD” (binary‑coded decimal) to avoid those quirks, at the cost of extra hardware.  

### 4️⃣ Hexadecimal (base‑16) — compact binary shorthand (0–9, A–F)

**Layer 1**  
Four binary bits map neatly to one hex digit (e.g., 1010 → A).  

**Layer 2**  
If you wrote long binary strings without grouping, they become unreadable for humans; hex compresses them while staying perfectly convertible.  

**Layer 3**  
Programmers often read memory addresses, color codes, and machine code in hex because each hex digit represents a nibble (4 bits).  

**Layer 4**  
- *Edge 1*: When displaying a 32‑bit address, leading zeros are often omitted, which can cause confusion about the actual size.  
- *Edge 2*: Some debugging tools allow mixed‑radix display (e.g., 0xFF = 255 = 11111111) to help spot errors.  

### 5️⃣ Octal (base‑8) — used in Unix permissions

**Layer 1**  
Three binary bits map to one octal digit (e.g., 111 → 7).  

**Layer 2**  
If you tried to write permissions as raw binary, the string would be nine characters long (rwxrwxrwx) and harder to parse quickly.  

**Layer 3**  
Unix stores file permission bits in a 12‑bit field; the common three‑digit octal notation (e.g., 755) is a human‑friendly shorthand.  

**Layer 4**  
- *Edge 1*: When a set‑uid or sticky bit is set, the octal representation expands to four digits (e.g., 4755).  
- *Edge 2*: Some Windows tools misinterpret octal strings as decimal, leading to incorrect permission settings.  

### 6️⃣ Base conversions: binary ↔ decimal ↔ hex ↔ octal

**Layer 1**  
Conversion is done by repeatedly dividing by the target base and recording remainders.  

**Layer 2**  
If you forget to reverse the order of remainders, the result is backwards and meaningless.  

**Layer 3**  
In practice, calculators and programming languages provide built‑in functions, but the underlying algorithm is the same for every pair of bases.  

**Layer 4**  
- *Edge 1*: Converting very large numbers manually can overflow the intermediate decimal representation; using arbitrary‑precision libraries avoids this.  
- *Edge 2*: When converting negative numbers, you must apply two’s complement before interpreting the bits in the new base.  

### 7️⃣ Two's complement — how negative numbers are stored

**Layer 1**  
Take the binary of the absolute value, invert all bits, then add 1.  

**Layer 2**  
If you forget the “add 1” step, the result is the one's‑complement representation, which has two zeros and behaves incorrectly in arithmetic.  

**Layer 3**  
All modern CPUs perform addition and subtraction on two’s‑complement numbers without extra hardware, making signed arithmetic fast and uniform.  

**Layer 4**  
- *Edge 1*: The most negative value (e.g., –128 in an 8‑bit signed byte) has no positive counterpart; attempting to negate it causes overflow.  
- *Edge 2*: When extending a signed value to a larger bit width, you must sign‑extend (copy the sign bit) rather than zero‑extend.  

### 8️⃣ Why overflow happens and what it looks like

**Layer 1**  
Overflow occurs when a calculation produces a result larger than the maximum value a fixed‑size bit field can hold.  

**Layer 2**  
If you ignore overflow, the result silently wraps around, producing a completely different number (e.g., 255 + 1 → 0 in an 8‑bit unsigned byte).  

**Layer 3**  
Languages and hardware provide flags (carry, overflow) that can be checked; higher‑level code often uses saturating arithmetic or larger types to avoid it.  

**Layer 4**  
- *Edge 1*: In cryptographic code, unnoticed overflow can leak secret keys.  
- *Edge 2*: In graphics, overflow of color channels can cause visual artifacts like banding.  

**CORE INSIGHT**: All number systems are just different lenses on the same underlying bits; mastering how to read and translate those lenses is the key to every later programming concept.

## Syntax and Structure

```text
# STEP 1: Identify the numeric base you need (binary, decimal, hex, octal)
# STEP 2: For conversion, write down the original digits
# STEP 3: Apply the appropriate positional weights (2ⁿ, 10ⁿ, 16ⁿ, 8ⁿ)
# STEP 4: Sum the weighted values to obtain the target representation
# STEP 5: For negative numbers, flip bits and add 1 (two's complement)
# STEP 6: Check if the result fits in the chosen bit width; if not, overflow occurs
# → In Phase 1 we will write this in real code.
```

## Practical Example

```python
print('Binary 1010 equals decimal 10')  # shows a binary pattern and its decimal meaning
```

## How This Connects to the Project

**BEFORE** the museum metadata module stored IDs as plain text strings, making sorting and range queries slow and error‑prone.  
**AFTER** the module stores each artifact’s ID as a fixed‑width binary integer, enabling fast numeric comparisons and compact storage.  
The relevant code lives in `metadata/ids.py` inside the function `encode_id_to_binary()`.  
A real‑world example is **NASA**, which stores telemetry packet identifiers in binary to minimize bandwidth and guarantee deterministic parsing.

## Common Mistakes Beginners Make

**Most common mistake:**  
*Wrong idea:* Assuming a binary string like `1010` can be added directly to another binary string.  
*Correct idea:* Binary addition must be performed bit‑by‑bit with carries, just like decimal addition.

**Looks right but is silently wrong:**  

```text
# Attempting to show a hex value without the 0x prefix
print('FF')  # This prints the characters F and F, not the numeric value 255
```

The code runs, but the program treats the output as text, not as the intended numeric value.

**Seems optional but critical at scale:**  
Ignoring overflow when aggregating large counts leads to wrap‑around bugs that only appear after processing thousands of artifacts.

**Missed config or flag:**  
Failing to specify the bit width (e.g., 16‑bit vs 32‑bit) when encoding IDs causes mismatched storage sizes across different modules.

**Interview question this topic generates:**  
*Question:* “Explain how you would store a negative temperature reading in a binary file.”  
*Surface answer:* “Use two’s complement.”  
*Production answer:* “Choose a signed integer type of sufficient width, convert the absolute value to binary, invert the bits, add 1, and ensure the file format records the chosen bit width so the reader can decode correctly.”

## Verification Task 1 – Debug This

**Prompt:** Your system shows an artifact ID of `0` after you saved the value `255`. You have evidence that the ID field is an 8‑bit unsigned integer. Diagnose and fix the problem.

### Solution 1
1. Recognize that `255 + 1` exceeds the maximum of an 8‑bit unsigned integer (255).  
2. The value wrapped around to `0` because of overflow.  
3. Fix by storing IDs in a larger field (e.g., 16‑bit) or by checking for overflow before incrementing.

## Verification Task 2 – Design Decision

**Prompt:** Building the Digital Museum, you must decide whether to store artifact timestamps in decimal (human‑readable) or binary (compact). Defend your choice.

### Solution 2
I would store timestamps in binary because the underlying hardware already works with binary integers, making arithmetic (differences, sorting) fast and memory‑efficient. The binary value can later be formatted as a human‑readable date when displayed, preserving both performance and usability.

## Verification Task 3 – Code Review

**Prompt:** Find and fix the subtle bug in the following snippet that attempts to display a binary ID.

```text
# STEP 1: Print the binary representation of an ID
print('Binary ID: 1010')  # Intended to show the ID 10, but treats it as text
```

### Solution 3
The bug is that the ID is hard‑coded as a string, so any change to the actual numeric ID will not be reflected. The fix is to replace the literal with a placeholder that will later be filled by a real conversion routine (e.g., `print(f'Binary ID: {binary_id}')` in Phase 1). For Phase 0 we simply note that the line only demonstrates the *appearance* of a binary value, not the dynamic conversion.

## What Comes Next

The next topic in the roadmap is **Operating System Basics**. Knowing how binary encodes numbers is essential because an operating system must manage memory addresses, file permissions, and process identifiers—all of which are stored as binary values. The two’s‑complement representation of signed integers will reappear when the OS handles arithmetic on counters and timestamps.

## Reference Summary

Binary & Number Systems are the universal language of computers, translating electrical on/off states into meaningful data through base‑2, base‑10, hexadecimal, and octal representations. Understanding why computers use binary, how to count, convert, and represent negative numbers with two’s complement, and how overflow manifests equips you to store and manipulate data reliably. A frequent production mistake is neglecting overflow, which silently corrupts values. Mastery of these concepts lets you encode artifact metadata compactly in the Digital Museum project, paving the way for the next lesson on Operating System Basics, where binary addresses and permission bits become central.