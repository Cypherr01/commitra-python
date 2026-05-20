# Topic: Binary & Number Systems

## What Is This?
Binary and number systems are the foundation of computer programming, allowing computers to understand and process information. A real-world analogy for this concept is a light switch, which can be either on or off, representing the two states of binary: 0 and 1. Just as a light switch can be used to control a light, binary is used to control the flow of information in a computer.

## How It Works Internally
The internal mechanics of binary and number systems can be broken down into several key points:
1. **Why computers use binary**: Computers use binary because it is the most basic and efficient way to represent information using only two electrical states: on and off.
2. **Binary (base-2)**: Binary is a number system that uses only two digits: 0 and 1. It is used to count in 0s and 1s, and is the basis for all computer programming.
3. **Decimal (base-10)**: Decimal is the number system used by humans, which uses ten digits: 0-9. It is used to count and represent numbers in a way that is easy for humans to understand.
4. **Hexadecimal (base-16)**: Hexadecimal is a compact binary shorthand that uses sixteen digits: 0-9 and A-F. It is used to represent binary information in a more readable and compact form.
5. **Octal (base-8)**: Octal is a number system that uses eight digits: 0-7. It is used in Unix permissions and is another way to represent binary information.
6. **Base conversions**: Base conversions are used to convert between different number systems, such as binary, decimal, hexadecimal, and octal. This is important because computers use binary, but humans use decimal, and being able to convert between the two is essential.
7. **Two's complement**: Two's complement is a method used to represent negative numbers in binary. It works by inverting the bits of the positive number and then adding 1.
8. **Overflow**: Overflow occurs when a number is too large to be represented in a particular number system. This can happen when a computer is doing calculations and the result is larger than the maximum value that can be stored.

## Syntax and Structure
```text
# STEP 1: The computer receives a binary instruction, such as 1010
# STEP 2: The computer decodes the instruction and determines what action to take
# STEP 3: The computer performs the action, such as adding two numbers together
# STEP 4: The computer stores the result in memory, using binary to represent the number
# STEP 5: The computer converts the binary number to decimal or hexadecimal for display
# STEP 6: The computer checks for overflow and handles it accordingly
In Phase 1 we will write this in real code.
```
This pseudocode demonstrates the basic steps involved in processing binary information in a computer.

## Practical Example
A concrete real-world scenario is a digital clock, which uses binary to represent the time. The clock's microcontroller uses binary to count the seconds, minutes, and hours, and then converts the binary information to decimal for display. For example, the time 12:45 might be represented in binary as 1100 0100 0010 0101.

## Common Mistakes Beginners Make
1. **Confusing binary and decimal**: 
   Wrong idea: Binary and decimal are the same thing.
   Correct idea: Binary and decimal are different number systems, with binary using only 0s and 1s, and decimal using 0-9.
2. **Not understanding base conversions**: 
   Wrong idea: Base conversions are only used in computer programming.
   Correct idea: Base conversions are used in many areas, including computer programming, engineering, and mathematics.
3. **Not checking for overflow**: 
   Wrong idea: Overflow is not a problem in computer programming.
   Correct idea: Overflow can cause errors and crashes, and should always be checked for when performing calculations.

## Programming Challenge
Describe how a computer would represent the decimal number 25 in binary, and explain the steps involved in converting the binary number back to decimal. Be sure to include the role of base conversions in this process.

## Solution
```text
1. First, we need to understand the basics of binary and decimal number systems.
2. Next, we need to convert the decimal number 25 to binary, using the division method.
3. We divide 25 by 2 and get a quotient of 12 and a remainder of 1.
4. We continue dividing the quotient by 2 until we get a quotient of 0.
5. The remainders, read from bottom to top, give us the binary representation of 25, which is 11001.
6. To convert the binary number back to decimal, we multiply each digit by the corresponding power of 2 and add the results together.
7. The result is the decimal number 25, which we started with.
```

## What Comes Next
The next topic is **Variables and Data Types**, which follows logically from this one because it builds on the foundation of binary and number systems to introduce the concept of storing and manipulating data in a computer program. Understanding binary and number systems is essential for working with variables and data types, and this topic will explore how to use these concepts to write more complex and useful programs.