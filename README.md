# RSA-algorithm
DALL·E 2023-03-04 22.56.38 - 3d render of The RSA algorithm (Rivest-Shamir-Adleman)  in basquiat style.png

![Screenshot](DALL·E 2023-03-04 22.56.38 - 3d render of The RSA algorithm (Rivest-Shamir-Adleman)  in basquiat style.png)


My implementation of the security protocol commonly referred to as RSA
Here you are going to see an implementation of the security protocol comonly referred to as RSA. I start by converting text into ascii characters. From there I take these characters and expand them into their binary expansion. I create two tool sets.
The first tool set will run an algorithm called Fast Modular Exponentiation. This will be used to first encrypt the message, and then subsequently to decrypt the message. It will be sped up using the binary expansion of the ascii characters to help decrypt other people's codes.
Then, also in the first toolset, I run another algorithm called Exapnded Euclidean Algorithm. This will be used to determine the value of "d". "d" is the inverse of e modulo (p-1)(q-1). We keep these values d and n as our private key.
The functions in the second toolset will generate the public and private key pairs which will then be used to create a ciphertext using the public key and then decode the same using the private key. So here in my second toolset, find_public_key, I have a function that will produce two values, e and n. This function will run a loop to find e such that e is relatively prime to (p - 1) (q - 1) and not equal to p or q.
Then, in my second toolset, find_private_key, I have a function to find the decryption exponent d such that d is the modular inverse of e. This uses the Extended Eucliean Algorithm and returns d: the decryption component.
Then, in my third part, I use the Encode function Convert_Text from Second tool set and get a list of numbers. I encode each of those numbers using n and e and return the encoded cipher_text. Using the public key, the Encode function will encode a message and generate the corresponding cipher_text.
Here, in my third part, I use the Decode function. the cipher_text will be a list of integers. First, I decrypt each of those integers using n and d. I use the function that converts the integers to a string defined in second toolset to recover the original message as a string. Using the private key, the Decode function will decode a ciper_text and recover the original message.
