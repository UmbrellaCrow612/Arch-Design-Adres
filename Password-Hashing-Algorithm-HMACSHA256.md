# ADR: Password Hashing Algorithm - HMACSHA256

## Context and Problem Statement

Our application requires a secure method for storing user passwords to protect against potential data breaches and unauthorized access. We need to select a cryptographic hashing algorithm that provides strong security, prevents password recovery, and protects against various attack vectors.

## Decision Drivers

* Strong cryptographic security
* Resistance to rainbow table and rainbow table attacks
* Performance and computational efficiency
* Compatibility with .NET ecosystem
* Industry-standard security practices

## Considered Options

* HMACSHA256
* Argon2
* bcrypt
* PBKDF2
* Scrypt

## Decision Outcome

Chosen option: "HMACSHA256", because it provides a robust, cryptographically secure hashing method with good performance characteristics and .NET framework support.

### Consequences

* Good, because it offers strong cryptographic security
* Good, because it's efficiently implemented in .NET
* Good, because it's resistant to rainbow table attacks
* Bad, because it requires additional salt implementation
* Bad, because it's not specifically designed as a key derivation function

### Confirmation

We will confirm this decision by:
1. Implementing secure salting mechanism
2. Conducting security code review
3. Performing penetration testing

## Pros and Cons of the Options

### HMACSHA256

* Good, because of strong cryptographic properties
* Good, because of native .NET support
* Good, because of computational efficiency
* Bad, because requires manual salt implementation
* Bad, because not a dedicated password hashing function

### Argon2

* Good, because it's modern and designed for password hashing
* Good, because of strong resistance to GPU and ASIC attacks
* Bad, because of higher computational complexity

### bcrypt

* Good, because specifically designed for password hashing
* Good, because of built-in salt and work factor
* Bad, because of potential performance limitations

### PBKDF2

* Good, because it's NIST recommended
* Good, because of configurable iteration count
* Bad, because vulnerable to GPU-based attacks

### Scrypt

* Good, because of memory-hard design
* Good, because resistant to hardware-based attacks
* Bad, because of higher computational requirements

## More Information

Implementation details:
1. Use cryptographically secure random salt
2. Implement multiple iterations
3. Store both hash and salt in database
4. Use constant-time comparison to prevent timing attacks

Periodic review will assess emerging cryptographic standards and potential algorithm updates.
