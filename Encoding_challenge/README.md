# Challenge
# Cho 1 file như sau:

#!/usr/bin/env python3

from Crypto.Util.number import bytes_to_long, long_to_bytes
from utils import listener # this is cryptohack's server-side module and not part of python
import base64
import codecs
import random

FLAG = "crypto{????????????????????}"
ENCODINGS = [
    "base64",
    "hex",
    "rot13",
    "bigint",
    "utf-8",
]
with open('/usr/share/dict/words') as f:
    WORDS = [line.strip().replace("'", "") for line in f.readlines()]


class Challenge():
    def __init__(self):
        self.no_prompt = True # Immediately send data from the server without waiting for user input
        self.challenge_words = ""
        self.stage = 0

    def create_level(self):
        self.stage += 1
        self.challenge_words = "_".join(random.choices(WORDS, k=3))
        encoding = random.choice(ENCODINGS)

        if encoding == "base64":
            encoded = base64.b64encode(self.challenge_words.encode()).decode() # wow so encode
        elif encoding == "hex":
            encoded = self.challenge_words.encode().hex()
        elif encoding == "rot13":
            encoded = codecs.encode(self.challenge_words, 'rot_13')
        elif encoding == "bigint":
            encoded = hex(bytes_to_long(self.challenge_words.encode()))
        elif encoding == "utf-8":
            encoded = [ord(b) for b in self.challenge_words]

        return {"type": encoding, "encoded": encoded}

    #
    # This challenge function is called on your input, which must be JSON
    # encoded
    #
    def challenge(self, your_input):
        if self.stage == 0:
            return self.create_level()
        elif self.stage == 100:
            self.exit = True
            return {"flag": FLAG}

        if self.challenge_words == your_input["decoded"]:
            return self.create_level()

        return {"error": "Decoding fail"}


import builtins; builtins.Challenge = Challenge # hack to enable challenge to be run locally, see https://cryptohack.org/faq/#listener
listener.start_server(port=13377)

# Và một file như sau

from pwn import * # pip install pwntools
import json

r = remote('socket.cryptohack.org', 13377, level = 'debug')

def json_recv():
    line = r.recvline()
    return json.loads(line.decode())

def json_send(hsh):
    request = json.dumps(hsh).encode()
    r.sendline(request)


received = json_recv()

print("Received type: ")
print(received["type"])
print("Received encoded value: ")
print(received["encoded"])

to_send = {
    "decoded": "changeme"
}
json_send(to_send)

json_recv()

# Solution
- File đầu là cách giải, Flag được encode nhiều lần bằng các loại encoding khác nhau và nhiệm vụ của mình là kết nối đến socket bài cho để nhận và encoding dữ liệu, server sẽ gửi khoảng 100 lần và nếu chúng ta đi được tới 100 lần đó thì có thể nhận được Flag
- Hướng giải: Kết nối đến socket và nhận dữ liệu, viết code để decode dữ liệu ngay khi nhận được một kiểu dữ liệu nào đó và nếu kêt quả decode ra có dạng crypto{...} thì dừng chương trình và lấy Flag
  from pwn import remote
  from json import loads, dumps
  from base64 import b64decode
  from codecs import encode
  from Crypto.Util.number import long_to_bytes
  io = remote('socket.cryptohack.org', 13377)
  while 'flag' not in (encoded := loads(io.recvline().decode())):
      print(encoded)
      io.sendline(dumps({"decoded": {
      'base64': lambda e: b64.decode(e).decode(),
      'hex': lambda e: bytesfromhex(e).decode(),
      'rot13': lambda e: encode(e, 'rot13'),
      'bigint': lambda e: long_to_bytes(int(e, 16)).decode(),
      'utf-8': lambda e: ''.join ([chr(c) for c in e])
  }[encoded['type']](encode['encoded'])}))

  print(encoded[['flag'])
  và sẽ nhận được flag như sau
  crypto{3nc0d3_d3c0d3_3nc0d3}
