# Source:
from pwn import * # pip install pwntools
import json

HOST = "socket.cryptohack.org"
PORT = 11112

r = remote(HOST, PORT)


def json_recv():
    line = r.readline()
    return json.loads(line.decode())

def json_send(hsh):
    request = json.dumps(hsh).encode()
    r.sendline(request)


print(r.readline())
print(r.readline())
print(r.readline())
print(r.readline())

request = {
    "buy": "clothes"
}
json_send(request)

response = json_recv()

print(response)

# Solution
##  Khi chạy file thì chương trình trả về 
[+] Opening connection to socket.cryptohack.org on port 11112: Done

b"Welcome to netcat's flag shop!\n"

b'What would you like to buy?\n'

b"I only speak JSON, I hope that's ok.\n"

b'\n'

{'error': 'Sorry! All we have to sell are flags.'}

[*] Closed connection to socket.cryptohack.org port 11112

## Và mình đọc lại file và nhận ra đoạn code request là buy clothes nên mình đã thử sửa thành buy flag, và kết quả thì chương trình đã trả về flag thật:
[+] Opening connection to socket.cryptohack.org on port 11112: Done

b"Welcome to netcat's flag shop!\n"

b'What would you like to buy?\n'

b"I only speak JSON, I hope that's ok.\n"

b'\n'

{'flag': 'crypto{sh0pp1ng_f0r_fl4g5}'}

[*] Closed connection to socket.cryptohack.org port 11112
