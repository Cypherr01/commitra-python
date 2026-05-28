## What Is This?

The concept of Binary & Number Systems refers to the way computers represent and manipulate information using binary digits (0s and 1s). 

Imagine you are at a library where books are organized using a simple system of two labels: "available" and "borrowed". This binary system allows librarians to quickly determine the status of each book. Similarly, computers use binary to represent information, making it easy to process and store data.

## How It Works Internally

### Why Computers Use Binary

Computers use binary because it is based on the two electrical states of a computer's circuitry: on (1) and off (0). This simplicity makes it reliable and efficient for electronic devices.

### Binary (Base-2) — Counting in 0s and 1s

In binary, counting works like this:
- 0 (zero)
- 1 (one)
- 10 (two)
- 11 (three)
- 100 (four)

And so on. This system is known as base-2.

### Decimal (Base-10) — How Humans Count

Humans use a decimal (base-10) system, which includes digits 0 through 9. This is how we normally count.

### Hexadecimal (Base-16) — Compact Binary Shorthand

Hexadecimal is a base-16 system that uses digits 0-9 and letters A-F to represent numbers. It's often used as a compact way to express binary numbers.

### Octal (Base-8) — Used in Unix Permissions

Octal is a base-8 system that uses digits 0-7. It's commonly used in computing for representing file permissions, especially in Unix.

### Base Conversions: Binary ↔ Decimal ↔ Hex ↔ Octal

Converting between these number systems is essential in computing. For example, converting binary to decimal helps in understanding and working with binary data in a more familiar format.

### Two's Complement — How Negative Numbers Are Stored

Two's complement is a method for representing signed numbers in binary. It works by inverting the bits of the number and then adding 1. This allows for the representation of negative numbers.

### Why Overflow Happens and What It Looks Like

Overflow occurs when a calculation produces a value that exceeds the maximum limit of the data type. For example, if you add 1 to the binary number 1111 (15 in decimal), you get 10000 (16 in decimal), but if the maximum limit is 15, this causes an overflow.

## LAYERED MECHANICS

### LAYER 1: Minimum Viable Version

```text
# STEP 1: Computer has two states - on (1) and off (0)
# STEP 2: These states are used to represent information
# STEP 3: Information is processed using binary operations
# STEP 4: Binary operations are used to perform calculations
# STEP 5: Calculations are used to make decisions
```

### LAYER 2: Why the Simple Version Breaks

The simple version breaks when dealing with large amounts of data or complex calculations. For example, when trying to represent a large number in binary, it can become very long and difficult to work with.

### LAYER 3: Production Version

In a production environment, computers use a combination of binary, decimal, hexadecimal, and octal number systems to represent and manipulate information. This allows for efficient processing, storage, and communication of data.

### LAYER 4: Two Specific Edge Cases

- **Edge Case 1:** When dealing with signed numbers, two's complement is used to represent negative numbers. However, if not implemented correctly, it can lead to incorrect results.
- **Edge Case 2:** When performing calculations, overflow can occur if the result exceeds the maximum limit of the data type. This can cause errors and incorrect results.

CORE INSIGHT: Understanding binary and number systems is crucial for working with computers and programming.

## Syntax and Structure

```text
# STEP 1: Define the problem to be solved
# STEP 2: Choose the appropriate number system
# STEP 3: Convert data to the chosen number system
# STEP 4: Perform calculations or operations
# STEP 5: Convert result back to the original number system
# STEP 6: Verify the result
In Phase 1 we will write this in real code.
```

## Common Mistakes Beginners Make

- **Most Common Mistake:** Not understanding the differences between binary, decimal, hexadecimal, and octal number systems.
- **Looks Right but Is Silently Wrong:** Using the wrong number system for a calculation, leading to incorrect results.
- **Seems Optional but Critical at Scale:** Not considering overflow when performing calculations, leading to errors.
- **Missed Config or Flag:** Not using two's complement correctly when working with signed numbers.
- **Interview Question:** "How would you represent a negative number in binary?" (Answer: Using two's complement.)

## Verification Tasks

### Task 1: Debug This

Your system shows an incorrect result for a binary calculation. You have the binary code and the expected result. Diagnose and fix.

## Solution 1

1. Review the binary code and the calculation being performed.
2. Check for any errors in the calculation or data representation.
3. Verify that the correct number system is being used.
4. Test the calculation with a smaller input to isolate the issue.

### Task 2: Design Decision

Building a digital museum artifact metadata storage system. Use binary or hexadecimal for storing artifact IDs.

## Solution 2

Use hexadecimal for storing artifact IDs because it provides a compact and human-readable representation of binary data.

### Task 3: Code Review

Find and fix the bug in the following code snippet:

```text
# STEP 1: Define the artifact ID in binary
# STEP 2: Convert the binary ID to decimal
# STEP 3: Store the decimal ID in the database
```

## Solution 3

The bug is that the code snippet does not handle overflow correctly. To fix this, add a check for overflow when converting the binary ID to decimal.

## What Comes Next

The next topic is **Operating System Basics**. Understanding binary and number systems is a prerequisite for Operating System Basics because it provides the foundation for understanding how computers process and store information, which is crucial for working with operating systems.

## How This Connects to the Project

- **BEFORE:** Without understanding binary and number systems, the digital museum artifact metadata storage system would not be able to accurately store and retrieve artifact information.
- **AFTER:** With a solid understanding of binary and number systems, the system can efficiently store and retrieve artifact metadata.
- **Exact File and Function Name:** The concept of binary and number systems will be used in the `artifact_storage.py` file, specifically in the `store_artifact_id()` function.
- **Real Company:** Google uses a similar approach to store and retrieve large amounts of data in their data centers.

## Reference Summary

Binary and number systems are the foundation of computer programming, enabling computers to represent and manipulate information using binary digits (0s and 1s). Understanding the differences between binary, decimal, hexadecimal, and octal number systems is crucial for working with computers and programming. A common mistake is not considering overflow when performing calculations, leading to errors. In the digital museum project, understanding binary and number systems enables efficient storage and retrieval of artifact metadata. This concept is used in the `artifact_storage.py` file and is essential for building a reliable and efficient system. Google and other companies rely on a solid understanding of binary and number systems to build and maintain their systems.