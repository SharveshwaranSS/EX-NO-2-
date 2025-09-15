## EX. NO:2 IMPLEMENTATION OF PLAYFAIR CIPHER

### NAME :  SHARVESHWARAN SS
### REG NO: 212224220096
## AIM:

To write a C program to implement the Playfair Substitution technique.

## DESCRIPTION:

The Playfair cipher starts with creating a key table. The key table is a 5×5 grid of letters that will act as the key for encrypting your plaintext. Each of the 25 letters must be unique and one letter of the alphabet is omitted from the table (as there are 25 spots and 26 letters in the alphabet).

To encrypt a message, one would break the message into digrams (groups of 2 letters) such that, for example, "HelloWorld" becomes "HE LL OW OR LD", and map them out on the key table. The two letters of the diagram are considered as the opposite corners of a rectangle in the key table. Note the relative position of the corners of this rectangle. Then apply the following 4 rules, in order, to each pair of letters in the plaintext:
1.	If both letters are the same (or only one letter is left), add an "X" after the first letter
2.	If the letters appear on the same row of your table, replace them with the letters to their immediate right respectively
3.	If the letters appear on the same column of your table, replace them with the letters immediately below respectively
4.	If the letters are not on the same row or column, replace them with the letters on the same row respectively but at the other pair of corners of the rectangle defined by the original pair.
## EXAMPLE:
![image](https://github.com/Hemamanigandan/EX-NO-2-/assets/149653568/e6858d4f-b122-42ba-acdb-db18ec2e9675)

 

## ALGORITHM:

STEP-1: Read the plain text from the user.
STEP-2: Read the keyword from the user.
STEP-3: Arrange the keyword without duplicates in a 5*5 matrix in the row order and fill the remaining cells with missed out letters in alphabetical order. Note that ‘i’ and ‘j’ takes the same cell.
STEP-4: Group the plain text in pairs and match the corresponding corner letters by forming a rectangular grid.
STEP-5: Display the obtained cipher text.




Program:
```
import numpy as np
a = np.array([[6, 24, 1],
              [13, 16, 10],
              [20, 17, 15]])

b = np.array([[8, 5, 10],
              [21, 8, 21],
              [21, 12, 8]])

msg = "SHARVESHWARANSS"

print("Enter plain text:", msg)
nums = [ord(ch) - 65 for ch in msg]
cipher_nums = []
for i in range(0, len(nums), 3):
    block = nums[i:i+3]
    if len(block) < 3:
        block += [0] * (3 - len(block))  # pad with 'A' if needed
    block = np.array(block)
    enc = np.dot(a, block) % 26
    cipher_nums.extend(enc)
cipher_text = ''.join(chr(x + 65) for x in cipher_nums)
print("Encrypted Cipher Text:", cipher_text)
plain_nums = []
for i in range(0, len(cipher_nums), 3):
    block = cipher_nums[i:i+3]
    block = np.array(block)
    dec = np.dot(b, block) % 26
    plain_nums.extend(dec)
plain_text = ''.join(chr(x + 65) for x in plain_nums)
print("Decrypted Cipher Text:", plain_text)

```



Output:
<img width="1687" height="1022" alt="image" src="https://github.com/user-attachments/assets/90e41808-b3c8-48f4-9dc9-12803fa9b09b" />



## RESULT:

 Program has been executed successfully 
