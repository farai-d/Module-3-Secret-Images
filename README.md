# AES Image Encryption Project 🔐🖼️

This project demonstrates encryption and decryption of images using the Advanced Encryption Standard (AES). The assignment explores how modern symmetric cryptography works when applied to real data such as image files.

---

## Project Notebooks

### Main Assignment
AES image encryption and experimentation with AES modes.

➡️ [AES-Images Notebook](./AES-Images.ipynb)

This notebook demonstrates:

- Loading an image
- Encrypting image data using AES
- Comparing encryption modes
- Visualizing encrypted images
- Recovering the original image

---

### CBC Decryption Challenge

Decrypting a classmate’s encrypted image using AES-CBC.

➡️ [CBC Decrypt Notebook](./CBC%20Decrypt.ipynb)

This notebook demonstrates:

- Reading encrypted image data
- Extracting the initialization vector (IV)
- Decrypting the ciphertext using AES-CBC
- Recovering and displaying the original image

---

## Technologies Used

- Python
- PyCryptodome
- Pillow
- Matplotlib
- Jupyter Notebook

---

## Learning Outcomes

Through this project I learned:

- How AES encryption works in practice
- The role of initialization vectors (IVs) in CBC mode
- How encrypted data appears random
- How to correctly decrypt ciphertext to recover original data

--

# AES Image Encryption Toolkit 🔐🖼️

This project demonstrates how to encrypt and decrypt images using the Advanced Encryption Standard (AES) in CBC mode. The program reads an image file, encrypts its bytes using AES, and produces an encrypted file. The encrypted file can then be decrypted to recover the original image.

---

## Project Overview

This toolkit was created as part of a cryptography assignment to explore modern symmetric encryption and how different AES modes behave when applied to image data.

The project shows:

- How AES encrypts raw image bytes
- How to correctly decrypt encrypted image data
- How initialization vectors (IVs) are used in CBC mode
- How encrypted images appear as random binary data

---

## Encryption Details

**Cipher:** AES-256-CBC  
**Key (HEX):**

```
1c40e8c70c96ff7d6a41763456e02841a28568f8f36cf66a0c4812b0178def8f
```

**Initialization Vector (HEX):**

```
c4d1204bb0e50e4ba7b855d28bb86f08
```

**Original Image:**

```
crypto-image.png
```

**Encrypted File:**

```
cbc-aes-picture.img
```

---

## Project Structure

```
project-folder/
│
├── crypto-image.png
├── cbc-aes-picture.img
├── decrypt.py
├── encrypt.py
└── README.md
```

---

## Requirements

Install the required Python library:

```bash
pip install pycryptodome
```

---

## Encryption Process

The encryption program:

1. Reads the original image file as raw bytes
2. Applies AES encryption in CBC mode
3. Uses a randomly generated or predefined IV
4. Writes the IV + ciphertext to an encrypted file

Example code snippet:

```python
from Crypto.Cipher import AES
from Crypto.Util.Padding import pad

cipher = AES.new(key, AES.MODE_CBC, iv)
ciphertext = cipher.encrypt(pad(image_bytes, 16))
```

---

## Decryption Process

To recover the original image, run the decryption script.

```bash
python decrypt.py
```

Example decryption code:

```python
from Crypto.Cipher import AES
from Crypto.Util.Padding import unpad

cipher = AES.new(key, AES.MODE_CBC, iv)
plaintext = unpad(cipher.decrypt(ciphertext), 16)
```

The recovered image will be saved as:

```
recovered_image.png
```

---

## Crypto Challenge

An encrypted image was shared publicly so others can attempt to decrypt it.

Challenge parameters:

```
Mode: AES-256-CBC
Encrypted File: cbc-aes-picture.img
Key (HEX): 1c40e8c70c96ff7d6a41763456e02841a28568f8f36cf66a0c4812b0178def8f
IV (HEX): c4d1204bb0e50e4ba7b855d28bb86f08
```

Goal:

Decrypt the file and recover the original image `crypto-image.png`.

---

## Security Notes

AES is a secure block cipher when implemented correctly. However, security depends heavily on the encryption mode used.

- **ECB**: insecure because it leaks patterns  
- **CBC**: secure with proper IV handling  
- **CTR**: secure stream-like mode  
- **GCM**: provides authenticated encryption and is widely used in modern systems

For high-security environments, **AES-256-GCM** is considered the most appropriate mode.

---

## Author

Farai Denhere  
Cryptography Project – AES Image Encryption
