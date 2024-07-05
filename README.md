# PRODIGY_CS_01
## Description
The Caesar Cipher is a classical encryption technique used in cryptography. This project showcases a Python implementation of the Caesar Cipher, allowing for both encryption and decryption of messages by shifting the letters in the text.

## How it Works:
1. **Shifting Characters:** The cipher shifts each letter in the text by a specified number of positions in the alphabet. For example, with a shift of 3, 'A' becomes 'D', 'B' becomes 'E', and so on.
2. **Wrap-Around:** The cipher uses modulo arithmetic to ensure that the shift wraps around the end of the alphabet back to the beginning.
3. **Encryption and Decryption:** The same function handles both encryption and decryption. For decryption, the shift is simply negated.

## Code
```
def caesar_cipher(text, shift, mode):
    decrypted_text = []
    
    # Adjust shift for decryption
    if mode == 'decrypt':
        shift = -shift
    
    for char in text:
        if char.isalpha():  # Check if the character is a letter
            # Determine the base (uppercase or lowercase)
            base = ord('A') if char.isupper() else ord('a')
            # Compute the shifted position within 0-25
            shifted = (ord(char) - base + shift) % 26
            
            # Convert back to a character
            decrypted_char = chr(base + shifted)
            
            decrypted_text.append(decrypted_char)
        else:
            # If the character is not a letter, append it unchanged
            decrypted_text.append(char)
    
    return ''.join(decrypted_text)

# Ask user for input
plain_text = input("Enter the message you want to encrypt or decrypt: ")
shift_amount = int(input("Enter the shift amount (positive integer): "))
mode = input("Enter 'encrypt' or 'decrypt': ").lower()

# Check if mode is valid
if mode not in ['encrypt', 'decrypt']:
    print("Invalid mode. Please enter 'encrypt' or 'decrypt'.")
else:
    # Encrypt or decrypt based on user input
    result = caesar_cipher(plain_text, shift_amount, mode)
    
    if mode == 'encrypt':
        print("Encrypted:", result)
    elif mode == 'decrypt':
        print("Decrypted:", result)
```
