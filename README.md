# RSA Security Protocol Implementation: Encryption, Decryption, Key Generation, and Message Recovery

![RSA-algorithm](https://github.com/mitch-henderson/RSA-algorithm/blob/main/2023_08_mitch___h_Message_Encoding_between_miami_vice_characters_using__f82cec54-3dc0-41b5-acc6-5c6158d78217.png)


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
