# Challenge: Give a file  Extract modulus from file and convert it to decimal and submit it
# Solution Use command to convert file .pub to file pem
sshkeygen -f bruce_rsa_6e7ecd53b443a97013397b1a1ea30e14.pub -e -m pem > brute_rsa.pem
Complain command:
sshkeygen: Format openssh
-f bruce_rsa_6e7ecd53b443a97013397b1a1ea30e14.pub: File public key format openssh
-e: acronym export meaning convert openssh to pem
-m pem: type pem
> brute_RSA.pem: write it on file pem

and we will receive file type 
-----BEGIN RSA PUBLIC KEY-----
MIIBigKCAYEArTy6m2vhhbwx3RVbNVb3ZOenCqqsOXHaJpbtN+OuulLKBSKpIoPB
+ZDbDXn0qWkf4lOxtGSgolkUbgG07Lhzfgs+dul4UL84CkwZExmF3Rf1nRv+v7pq
Lt2dPsCb02YLxJnhHJb4rQaz2ZM4QCtTOcqYDUeKfLHCaZU4Ekm/OApKrpfw4/0o
fn8KOrFN0t4/dqnNuwVRgoaUIhsI47reApB2rs0AP4CggSIi8s6BXCxB4YzgThBK
5760T1giACYQC5MFdq1Gw+INSFmu0CNqt5wdJ5Z4z5448Gke06R+IMtjUiGDQ3Qt
T2fK3gWhZxk14M4UNrdETgTW/mQ4B/BcvikxvoBGpKbttG0agfOjTen6wyzpGfcd
8N9rSbaqqyUwC8uDotzFtFzzutVAU9d91TagGzWBhNoMfplwVTns27GOOgv1dn5s
QSSSmP0hTbPMDlThysKkR9BiOVbBtWGQpV936pPBgyWERGqMqC9xykLdVHv2Vu05
T0WMwKCAetgtAgMBAAE=
-----END RSA PUBLIC KEY-----
and now we write code to convert it to decimal
from Crypto.Publickey import RSA
f = open("brute_RSA.pem", "r")
pubkey = RSA.import_key(f.read())
print(pubkey)
