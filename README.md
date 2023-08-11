# RSA Security Protocol Implementation: Encryption, Decryption, Key Generation, and Message Recovery

![RSA-algorithm](https://github.com/mitch-henderson/RSA-algorithm/blob/main/2023_08_mitch___h_rsa_encryption.png)


# RSA Security Protocol Implementation

Welcome to my detailed RSA (Rivest–Shamir–Adleman) security protocol implementation. The RSA protocol is one of the fundamental pillars of modern cryptography, and you can read more about it [here](https://www.encryptionconsulting.com/education-center/what-is-rsa).

## Overview
The core of this project revolves around text-to-binary conversion, Fast Modular Exponentiation for encryption and decryption, and the Extended Euclidean Algorithm for key generation.

### Text-to-Binary Conversion
I initiate the process by [transforming text into ASCII characters](https://onlinestringtools.com/convert-string-to-ascii) and subsequently expand these characters into their binary representation.

## Toolsets

### 1. Primary Algorithm Toolset:
* **[Fast Modular Exponentiation](https://www.khanacademy.org/computing/computer-science/cryptography/modarithmetic/a/fast-modular-exponentiation):** Empowers both the encryption and decryption processes. By leveraging the binary expansion of ASCII characters, this method is optimized for speed, especially when decrypting third-party codes.
* **[Extended Euclidean Algorithm](https://www.youtube.com/watch?v=hB34-GSDT3k):** Essential for deducing the value of "d" — the multiplicative inverse of "e" modulo (p-1)(q-1). Read more on determining "d" [here](https://math.stackexchange.com/questions/818293/how-do-i-find-the-inverse-of-e-bmod-p-1q-1). The private key comprises the values d and n.

### 2. Key Management Toolset:
* **find_public_key:** Generates the public key components, e and n. This function ensures 'e' is co-prime with (p-1)(q-1) and isn't equal to either p or q.
* **find_private_key:** Determines the decryption exponent 'd' using the Extended Euclidean Algorithm. This function guarantees that 'd' is the modular inverse of 'e'.

### 3. Message Encoding & Decoding Suite:
* **Encode:** Utilizes the `Convert_Text` function from the second toolset to transform text into a number sequence. Subsequently, each number is encrypted using the public key to produce the cipher_text.
* **Decode:** Decrypts the cipher_text—a series of integers—using the private key. The decoded integers are then converted back to their original text form using functions from the second toolset.

## Usage

Use the **Encode** function with the public key to transform plaintext messages into encrypted cipher_texts. For decryption, the **Decode** function will retrieve the original message from a provided cipher_text using the private key.

Thank you for exploring my RSA implementation! Feedback and contributions are always appreciated.


My implementation of the security protocol commonly referred to as [RSA(Rivest–Shamir–Adleman)](https://www.encryptionconsulting.com/education-center/what-is-rsa). I start by [converting text into ascii characters](https://onlinestringtools.com/convert-string-to-ascii). From there I take these characters and expand them into their binary expansion. I create two tool sets.
The first tool set will run an algorithm called [Fast Modular Exponentiation](https://www.khanacademy.org/computing/computer-science/cryptography/modarithmetic/a/fast-modular-exponentiation)
. This will be used to first encrypt the message, and then subsequently to decrypt the message. It will be sped up using the binary expansion of the ascii characters to help decrypt other people's codes.
Then, also in the first toolset, I run another algorithm called [Expanded Euclidean Algorithm](https://www.youtube.com/watch?v=hB34-GSDT3k). This will be used to determine the value of "d". ["d" is the inverse of e modulo (p-1)(q-1)](https://math.stackexchange.com/questions/818293/how-do-i-find-the-inverse-of-e-bmod-p-1q-1). We keep these values d and n as our private key.
The functions in the second toolset will generate the public and private key pairs which will then be used to create a ciphertext using the public key and then decode the same using the private key. So here in my second toolset, find_public_key, I have a function that will produce two values, e and n. This function will run a loop to find e such that e is relatively prime to (p - 1) (q - 1) and not equal to p or q.
Then, in my second toolset, find_private_key, I have a function to find the decryption exponent d such that d is the modular inverse of e. This uses the Extended Eucliean Algorithm and returns d: the decryption component.
Then, in my third part, I use the Encode function Convert_Text from Second tool set and get a list of numbers. I encode each of those numbers using n and e and return the encoded cipher_text. Using the public key, the Encode function will encode a message and generate the corresponding cipher_text.
Here, in my third part, I use the Decode function. the cipher_text will be a list of integers. First, I decrypt each of those integers using n and d. I use the function that converts the integers to a string defined in second toolset to recover the original message as a string. Using the private key, the Decode function will decode a ciper_text and recover the original message.
