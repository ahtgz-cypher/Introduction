# Challenge: For the following code

from Crypto.Cipher import AES


KEY = ?

FLAG = ?


@chal.route('/block_cipher_starter/decrypt/<ciphertext>/')

def decrypt(ciphertext):

    ciphertext = bytes.fromhex(ciphertext)

    cipher = AES.new(KEY, AES.MODE_ECB)
    try:
        decrypted = cipher.decrypt(ciphertext)
    except ValueError as e:
        return {"error": str(e)}

    return {"plaintext": decrypted.hex()}


@chal.route('/block_cipher_starter/encrypt_flag/')

def encrypt_flag():

    cipher = AES.new(KEY, AES.MODE_ECB)
    encrypted = cipher.encrypt(FLAG.encode())

    return {"ciphertext": encrypted.hex()}

Based on the above code, we will know how the program works:

Flag and Key are target which we need find, give 2 functions decrypt and encrypt_flag, They are installed according to AES ECB mode and it is a web API, we can interact with it, we can get, post, put/patch and delete 
.And on the above challenge, we just use Get to receive data
# Solution: 
## Method 1: We can direct interaction and don't need write code
First, in index encrypt_flag(), we click submit and we will receive a hex string and it is ciphertext. And next, we will paste it on index decrypt(ciphertext) and we will receive a hex string too and it is plaintext 
.Finally, we take it and paste it in hex encoder/decoder below and flag will appear

crypto{bl0ck_c1ph3r5_4r3_f457_!}

## Method 2: We also can write code to decode it

import requests

BASE_URL = "https://aes.cryptohack.org/block_cipher_starter/"

r = requests.get(f"{BASE_URL}/encrypt_flag")

data = r.json()

ciphertext = data["ciphertext"]

print(ciphertext)

r = request.get(f"{BASE_URL}/decrypt/{ciphertext}")

data = r.json()

plaintext = data["plaintext"]

print(plaintext)

print("flag", bytearray.fromhex(plaintext).decode())
