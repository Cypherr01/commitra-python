## What Is This?
Authentication with passwords and hashing is a critical security mechanism that ensures only authorized users can access a system or application. Imagine a safe deposit box at a bank: just like how you need a unique combination to open your box, a user needs a unique password to access their account, and hashing is like a special lock that scrambles the combination so it can't be read by unauthorized people.

## How It Works Internally
### Introduction to Password Storage
Storing passwords securely is crucial to prevent unauthorized access. 
### Why You Never Store Plaintext Passwords
You never store plaintext passwords because if an attacker gains access to the storage, they can read all the passwords. 
### Hashing vs Encryption
Hashing is a one-way process, meaning it's easy to generate a hash from a password, but it's virtually impossible to recreate the original password from the hash. Encryption, on the other hand, is a two-way process, where data can be encrypted and then decrypted back to its original form.

```text
# Pseudocode for hashing vs encryption
function hash(password):
  # one-way process, can't get password back from hash
  return hashed_password

function encrypt(data):
  # two-way process, can get data back from encrypted_data
  return encrypted_data

function decrypt(encrypted_data):
  # two-way process, can get data back from encrypted_data
  return data
```

### Slow Hash Function Designed for Passwords — Bcrypt
Bcrypt is a slow hash function designed specifically for passwords. It's slow by design, which makes it more secure against brute-force attacks. 
### Salt Prevents Rainbow Tables
A salt is a random value added to the password before hashing, which prevents rainbow table attacks. Rainbow tables are precomputed tables of hashes for common passwords.

```text
# Pseudocode for bcrypt with salt
function bcrypt_hash(password):
  # generate a random salt
  salt = generate_salt()
  # combine password and salt
  password_with_salt = password + salt
  # hash the combined password and salt
  hashed_password = hash(password_with_salt)
  return hashed_password
```

### Passlib Library
The passlib library provides a simple way to hash and verify passwords using various algorithms, including bcrypt. 
### CryptContext, Hash(), Verify()
The CryptContext class in passlib manages the hashing and verification process, and the hash() and verify() functions are used to hash a password and verify a password against a hashed password, respectively.

```text
# Pseudocode for passlib
function hash_password(password):
  # create a CryptContext object
  crypt_context = CryptContext()
  # hash the password
  hashed_password = crypt_context.hash(password)
  return hashed_password

function verify_password(password, hashed_password):
  # create a CryptContext object
  crypt_context = CryptContext()
  # verify the password against the hashed password
  return crypt_context.verify(password, hashed_password)
```

### Why MD5/SHA256 Are Wrong for Passwords
MD5 and SHA256 are fast hash functions that are not suitable for passwords because they can be computed quickly, making them vulnerable to brute-force attacks. 
### Work Factor / Cost — Bcrypt Rounds
The work factor, or cost, of a hash function determines how computationally expensive it is to compute the hash. Bcrypt uses a variable number of rounds to adjust the work factor, making it more secure against brute-force attacks.

```text
# Pseudocode for bcrypt work factor
function bcrypt_hash(password, rounds):
  # adjust the work factor based on the number of rounds
  work_factor = adjust_work_factor(rounds)
  # hash the password with the adjusted work factor
  hashed_password = hash(password, work_factor)
  return hashed_password
```

## Syntax and Structure
```python
# Import the bcrypt library
import bcrypt

# Define a function to hash a password
def hash_password(password):
  # Generate a salt
  salt = bcrypt.gensalt()
  # Hash the password
  hashed_password = bcrypt.hashpw(password.encode('utf-8'), salt)
  return hashed_password

# Define a function to verify a password
def verify_password(password, hashed_password):
  # Verify the password against the hashed password
  return bcrypt.checkpw(password.encode('utf-8'), hashed_password)

# Example usage:
password = "mysecretpassword"
hashed_password = hash_password(password)
print(verify_password(password, hashed_password))  # Should print: True
```

## Practical Example
To demonstrate the concept of password hashing and verification, let's create a simple example using the bcrypt library. We'll define two functions: one to hash a password and another to verify a password against a hashed password.

## How This Connects to the Project
Before learning about password hashing and verification, the Secure API Gateway project would have been vulnerable to password attacks. 
After learning about password hashing and verification, the project can now securely store and verify user passwords. 
The exact file and function name where this concept lives in the project is `auth.py` and `hash_password()` and `verify_password()`. 
A real company that uses this exact pattern is GitHub, which uses bcrypt to securely store and verify user passwords.

## Common Mistakes Beginners Make
**Wrong idea: Storing plaintext passwords is okay because I'm the only one with access to the database.** 
Correct idea: Storing plaintext passwords is never okay, because even if you're the only one with access to the database now, that may not always be the case in the future. 
**Looks right but is silently wrong: Using a fast hash function like MD5 or SHA256 to hash passwords.** 
This is wrong because fast hash functions can be computed quickly, making them vulnerable to brute-force attacks. 
**Seems optional but critical at scale: Using a salt when hashing passwords.** 
This is critical because without a salt, an attacker can use a rainbow table to crack the password. 
**Missed config or flag: Not adjusting the work factor of the hash function.** 
This is critical because if the work factor is too low, the hash function can be computed too quickly, making it vulnerable to brute-force attacks. 
**Interview question this topic generates: How do you securely store and verify user passwords in a web application?** 
Surface answer: You use a slow hash function like bcrypt to hash the passwords, and store the hashed passwords in a database. 
Production answer: You use a slow hash function like bcrypt to hash the passwords, store the hashed passwords in a database, and use a salt to prevent rainbow table attacks.

## Verification Task 1
Debug This: "Your system shows an error message when a user tries to log in with a correct password. You have the hashed password stored in the database. Diagnose and fix."
## Solution 1
The issue is likely due to the fact that the password is not being hashed correctly before being compared to the stored hashed password. To fix this, you need to hash the input password using the same hash function and salt used to store the password, and then compare the resulting hash to the stored hash.

## Verification Task 2
Design Decision: "You're building a new web application and need to decide how to store and verify user passwords. Use either bcrypt or MD5. Defend your choice."
## Solution 2
I would choose bcrypt because it is a slow hash function that is specifically designed for passwords, making it more secure against brute-force attacks. MD5, on the other hand, is a fast hash function that is not suitable for passwords.

## Verification Task 3
Code Review: 
```python
import bcrypt

def hash_password(password):
  salt = bcrypt.gensalt()
  hashed_password = bcrypt.hashpw(password.encode('utf-8'), salt)
  return hashed_password

def verify_password(password, hashed_password):
  return bcrypt.checkpw(password.encode('utf-8'), hashed_password)

# Example usage:
password = "mysecretpassword"
hashed_password = hash_password(password)
print(verify_password(password, hashed_password))  # Should print: True
```
Find and fix the bug: The code is missing error handling for the case where the input password is None or empty.
## Solution 3
To fix this, you need to add error handling to check if the input password is None or empty before attempting to hash or verify it.

## What Comes Next
The next topic in the roadmap is RBAC — Role-Based Access Control. This topic follows logically from password hashing and verification because once you have a secure way to store and verify user passwords, you need to control what actions those users can perform within your system.

## Reference Summary
Password hashing and verification is a critical security mechanism that ensures only authorized users can access a system or application. The key concepts include hashing vs encryption, slow hash functions like bcrypt, salts to prevent rainbow table attacks, and adjusting the work factor to make the hash function more computationally expensive. The most common production mistake is using a fast hash function like MD5 or SHA256, which can be computed quickly and is vulnerable to brute-force attacks. In the Secure API Gateway project, password hashing and verification is used to securely store and verify user passwords. This concept connects to the next topic, RBAC — Role-Based Access Control, because once you have a secure way to store and verify user passwords, you need to control what actions those users can perform within your system.