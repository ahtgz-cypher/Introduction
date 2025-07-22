# Challenge: 
## They are wanting to tell us that password or key can be guess if it don't random, it can be brute-force by some password list and we should set it randomly unpredictable, and this challenge is a password predictable and it just be hash and we know key of encrypt AES that the list has been given.
# Solution:
## Now, we need decode string encrypt_flag has been given. After do it, we need read file and take words in file and hash them by MD5 and use it as a key to decode with ciphertext and take flag. 
impport Crypto.Cipher import AES

import hashlib

ciphertext = bytes.fromhex("c92b7734070205bdf6c0087a751466ec13ae15e6f1bcdd3f3a535ec0f4bbae66")

with open("file") as f:

    words = [w.split() for w in f.readlines()]

for w in words:

    key = hashlib.md5(w.encode()).digest()
  
    cipher = AES.new(key, AES.MODE_ECB).decrypt(ciphertext)

    if b'crypto' in cipher: 

print(cipher)

print(key.hex())
  
  exit

Because the key is set simple that's why we can break it easy

Result: 

b'crypto{k3y5__r__n07__p455w0rdz?}'
d3e23f1eb6e79ed51133e0da48e98d4a
