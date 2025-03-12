# ProdigyInfoTech_-Caesar-Cipher-Encryption-and-Decryption-
## Introduction
Encryption is a crucial process in cybersecurity, ensuring data confidentiality by converting readable information into an unreadable format. The Caesar Cipher is a simple substitution cipher where each letter in the plaintext is shifted a fixed number of places in the alphabet. Although not secure for modern applications, it serves as a fundamental introduction to encryption techniques. This report details the process of implementing file encryption and decryption using the Caesar Cipher in Kali Linux with Python.


## Objective
To encrypt and decrypt a text file using the Caesar Cipher algorithm in Kali Linux.

## Step 1: Environment Setup
1. Opened Terminal in Kali Linux using `Ctrl + Alt + T`.
2. Checked Python Installation using:
   ```sh
   python3 --version
   ```
3. If Python was missing, installed it with:
   ```sh
   sudo apt update
   sudo apt install python3
   
## Step 2: Created the Python Script
1. Created the script file using:
   ```sh
   nano caesar_cipher.py
   ```
2. Added the following Python code to handle encryption and decryption:
   ```python
   def encrypt(plaintext, shift):
       result = ""
       for char in plaintext:
           if char.isalpha():
               shift_amount = shift % 26
               start = 65 if char.isupper() else 97
               encrypted_char = chr((ord(char) - start + shift_amount) % 26 + start)
               result += encrypted_char
           else:
               result += char
       return result

   def decrypt(ciphertext, shift):
       result = ""
       for char in ciphertext:
           if char.isalpha():
               shift_amount = shift % 26
               start = 65 if char.isupper() else 97
               decrypted_char = chr((ord(char) - start - shift_amount) % 26 + start)
               result += decrypted_char
           else:
               result += char
       return result

   def encrypt_file(input_file, output_file, shift):
       with open(input_file, 'r') as file:
           content = file.read()
       encrypted_content = encrypt(content, shift)
       with open(output_file, 'w') as file:
           file.write(encrypted_content)

   def decrypt_file(input_file, output_file, shift):
       with open(input_file, 'r') as file:
           content = file.read()
       decrypted_content = decrypt(content, shift)
       with open(output_file, 'w') as file:
           file.write(decrypted_content)

   def main():
       print("Caesar Cipher - File Encryption/Decryption")
       input_file = input("Enter the input file name: ")
       shift_value = int(input("Enter the shift value: "))
       
       choice = input("Do you want to (e)ncrypt or (d)ecrypt the file? ").lower()
       
       if choice == 'e':
           output_file = input("Enter the name for the encrypted output file: ")
           encrypt_file(input_file, output_file, shift_value)
           print(f"File encrypted successfully! Saved as {output_file}")
       elif choice == 'd':
           output_file = input("Enter the name for the decrypted output file: ")
           decrypt_file(input_file, output_file, shift_value)
           print(f"File decrypted successfully! Saved as {output_file}")
       else:
           print("Invalid choice!")

   if __name__ == "__main__":
       main()
   ```
3. Saved the script (`Ctrl + O`, Enter) and exited (`Ctrl + X`).
![image](https://github.com/user-attachments/assets/1cff4f70-fad8-4e0e-96c5-ba2f91858c2d)
![image](https://github.com/user-attachments/assets/24b09bc4-190d-4e0e-bf3a-20b756403c8d)

## Step 3: Created a Text File
Created a sample text file for encryption.
![image](https://github.com/user-attachments/assets/5427f952-f80c-4884-a5e3-bd7c81ba38be)

## Step 4: Encrypted the File
1. Ran the script:
   ```sh
   python3 caesar_cipher.py
   ```
2. Entered the following inputs:
   - Input file name: `Yungbizzy.txt`
   - Shift value: `3`
   - Encrypt or Decrypt: `e`
   - Output file name: `Yungbizzy_encrypted.txt`
3. Output Message:
   ```
   File encrypted successfully! Saved as Yungbizzy_encrypted.txt
   ```
4. Verified the encrypted content:
   ```sh
   cat Yungbizzy_encrypted.txt
![image](https://github.com/user-attachments/assets/4f54eb0e-0d66-4ad5-9075-5a9c6f0aa9b8)

## Step 5: Decrypted the File
1. Ran the script again:
   ```sh
   python3 caesar_cipher.py
   ```
2. Entered the following inputs:
   - Input file name: `Yungbizzy_encrypted.txt`
   - Shift value: `3`
   - Encrypt or Decrypt: `d`
   - Output file name: `decrypted.txt`
3. Output Message:
   ```
   File decrypted successfully! Saved as decrypted.txt
   ```
4. Verified the decrypted content:
   
   cat decrypted.txt
   ![image](https://github.com/user-attachments/assets/f5a8addc-fc7f-4b25-9e96-a790856494ab)

## Recommendations
1. **Use Stronger Encryption**: The Caesar Cipher is not secure for modern applications. Consider using AES (Advanced Encryption Standard) or RSA (Rivest-Shamir-Adleman) for better security.
2. **Avoid Overwriting Files**: Always save the encrypted file with a different name to prevent accidental data loss.
3. **Increase Shift Complexity**: Instead of a single shift value, consider using the Vigenère Cipher, which is more secure.
4. **Secure Key Management**: If using advanced encryption, store encryption keys separately and securely.
5. **Automate the Process**: Convert this script into a command-line tool or a simple GUI for ease of use.

## Conclusion
This report documents the successful implementation of a Caesar Cipher encryption and decryption process using Python in Kali Linux. The task included:
- Writing and running a Python script for encryption and decryption.
- Encrypting and decrypting a file using a shift value.
- Verifying the correctness of encryption and decryption.
