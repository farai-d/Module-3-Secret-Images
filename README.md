# AES Image Encryption Project 🔐🖼️

This project demonstrates how images can be encrypted and decrypted using the Advanced Encryption Standard (AES). The goal of the assignment was to implement AES encryption in software, apply it to image data, and demonstrate how encrypted images can be securely shared and decrypted by others who possess the correct cryptographic parameters.

The project includes two notebooks and an encrypted image:

1. **AES-Images.ipynb** – main implementation of AES image encryption and decryption
2. **CBC Decrypt.ipynb** – decrypting a classmate’s encrypted image
3. **[cbc_encrypted.bin File](./cbc_encrypted.bin)** - encrypted file


---

# Project Notebooks

## Main Assignment – AES Image Encryption

➡️ [AES-Images Notebook](./AES-Images.ipynb)

This notebook implements a suite of Python functions that:

- Load an image file
- Convert image pixels into raw byte data
- Encrypt the image using AES
- Decrypt encrypted data back into the original image
- Display the encrypted and decrypted results

The notebook demonstrates how encryption transforms image data into random-looking bytes.

---

## CBC Decryption Challenge

➡️ [CBC Decrypt Notebook](./CBC%20Decrypt.ipynb)

This notebook demonstrates decrypting an encrypted image received from another student.

Steps performed:

1. Load encrypted image file
2. Extract initialization vector (IV)
3. Decrypt ciphertext using AES-CBC
4. Remove padding
5. Recover the original image
6. Display the decrypted image

Encrypted file used:

```
cbc-aes-picture.img
```

Recovered image:

```
crypto-image.png
```

---

# Encryption Details

Encryption Mode:

```
AES-256-CBC
```

Secret Key (HEX):

```
1c40e8c70c96ff7d6a41763456e02841a28568f8f36cf66a0c4812b0178def8f
```

Initialization Vector (HEX):

```
c4d1204bb0e50e4ba7b855d28bb86f08
```

Original image used:

```
crypto-image.png
```

Encrypted file generated:

```
cbc-aes-picture.img
```

---

# Example Encryption Code

```python
from Crypto.Cipher import AES
from Crypto.Util.Padding import pad

cipher = AES.new(key, AES.MODE_CBC, iv)
ciphertext = cipher.encrypt(pad(image_bytes,16))
```

---

# Example Decryption Code

```python
from Crypto.Cipher import AES
from Crypto.Util.Padding import unpad

cipher = AES.new(key, AES.MODE_CBC, iv)
plaintext = unpad(cipher.decrypt(ciphertext),16)
```

---

# Tweet Challenge

As part of the assignment, an encrypted image was shared publicly so that another student could attempt to decrypt it.

Example Tweet:

AES Image Crypto Challenge 🔐

Encrypted file: cbc-aes-picture.img  
Original image: crypto-image.png  

Cipher: AES-256-CBC  
Key (HEX):  
1c40e8c70c96ff7d6a41763456e02841a28568f8f36cf66a0c4812b0178def8f  

IV (HEX):  
c4d1204bb0e50e4ba7b855d28bb86f08  

Decrypt the image and recover the original file.

---

# How to Run the Code

Install required libraries:

```
pip install pycryptodome pillow matplotlib
```

Then open the notebooks in VS Code or Jupyter.

Recommended order:

```
1. AES-Images.ipynb
2. CBC Decrypt.ipynb
```

Running the notebooks will:

- encrypt an image
- save encrypted output
- decrypt the ciphertext
- display the recovered image

---

# Technologies Used

- Python
- PyCryptodome
- Pillow
- Matplotlib
- Jupyter Notebook

---

# Reflection

## Effort and Development Process

I spent approximately **6–8 hours** completing this project. The first part involved implementing AES encryption and learning how image data must be converted to raw bytes before encryption can occur. One challenge I encountered was handling padding and block sizes correctly. AES operates on 16-byte blocks, so the data had to be padded before encryption and unpadded after decryption.

Another breakthrough occurred when I discovered that encrypted image data can no longer be stored as a normal PNG file because encryption produces random binary data. Instead, the encrypted file was saved as a binary `.img` file and then reconstructed after decryption.

Debugging the CBC decryption process also required understanding how initialization vectors are used and how they may be stored at the beginning of encrypted files.

---

## Key Insights

One of the most important insights from this project is that **encryption algorithms are only secure when used with the correct mode and implementation**. AES itself is very secure, but using it incorrectly can still expose information.

Working with images also made encryption much more tangible. Seeing how encrypted data becomes random noise demonstrated how effective cryptography is at protecting information.

This project reinforced the importance of proper cryptographic implementation, which will be valuable in future cybersecurity and networking work.

---

## Pride in the Work

Yes, I am proud of the work completed in this project. The implementation successfully encrypts and decrypts images using AES and demonstrates a real-world application of symmetric cryptography. It was satisfying to see the original image recovered perfectly after decryption, confirming that the implementation worked correctly.

---

## Overall Impression

Overall, this assignment was both challenging and rewarding. It required combining theoretical cryptography concepts with practical programming. It helped bridge the gap between studying cryptographic algorithms and actually implementing them in software.

The project also showed how encryption tools are used in real security systems.

---

## Nation-State Security

Among the AES modes studied, **AES-256 in GCM mode** is considered strong enough for nation-state level security when implemented correctly. GCM provides both confidentiality and integrity through authenticated encryption.

ECB mode is insecure because identical plaintext blocks produce identical ciphertext blocks, which can reveal patterns. CBC improves security by chaining blocks together with an initialization vector, but it does not provide authentication. GCM is widely used in modern security protocols because it provides both encryption and data integrity.

---

# Author

Farai Denhere  
Cryptography Project – AES Image Encryption
