def caesar_cipher(text, shift, operation):
    result = ""
    for char in text:
        # Check if the character is an uppercase letter
        if char.isupper():
            start = ord('A')
            result += chr((ord(char) - start + shift * operation) % 26 + start)
        # Check if the character is a lowercase letter
        elif char.islower():
            start = ord('a')
            result += chr((ord(char) - start + shift * operation) % 26 + start)
        else:
            # Non-alphabetic characters are added unchanged
            result += char
    return result

def main():
    while True:
        operation = input("Type 'e' to encrypt or 'd' to decrypt: ").lower()
        if operation not in ('e', 'd'):
            print("Invalid operation. Please enter 'e' for encryption or 'd' for decryption.")
            continue
        
        text = input("Enter the message: ")
        shift = int(input("Enter the shift value (integer): "))
        
        if operation == 'e':
            encrypted_text = caesar_cipher(text, shift, 1)
            print(f"Encrypted message: {encrypted_text}")
        elif operation == 'd':
            decrypted_text = caesar_cipher(text, shift, -1)
            print(f"Decrypted message: {decrypted_text}")
        
        another = input("Do you want to perform another operation? (yes/no): ").lower()
        if another != 'yes':
            break

if __name__ == "__main__":
    main()
