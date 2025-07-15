# Challenge: Give file type pem and require extract prive key d 
# Solution: Write code extract prive key from file pem:
from Crypto.Publickey import RSA 
f = open("privacy_enhanced_mail_1f696c053d76a78c2c531bb013a92d4a (1).pem", "r")
key = RSA.import_key(f.read())
print(key)
