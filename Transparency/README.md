# Challenge: Give a file public key and require we research flag
# Solution: We use command to extract fingerprint SHA256 
openssl pkey -outform der publin -in transparency_afff0345c6f99bf80eab5895458d8eab.pem | sha256sum
In there:
openssl pkey: OpenSSL library use to process key (public or prive key)
-outform der; Options output is DER, that is binary form 
publin: report name input is public key 
| sha256sum: convert ouput to input of command sha256sum, sha256 is tool to calculate hash sha256 of data input

After perform command above, fingerprint sha256 will appear and we use it to lookup flag in website crt.sh or censys.io
And submit Flag
