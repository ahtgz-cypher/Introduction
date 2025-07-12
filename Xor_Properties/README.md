# Challenge: Đề bài cho một danh sách các key bị xor với nhau và yêu cầu tìm ra flag
KEY1 = a6c8b6733c9b22de7bc0253266a3867df55acde8635e19c73313

KEY2 ^ KEY1 = 37dcb292030faa90d07eec17e3b1c6d8daf94c35d4c9191a5e1e

KEY2 ^ KEY3 = c1545756687e7573db23aa1c3452a098b71a7fbf0fddddde5fc1

FLAG ^ KEY1 ^ KEY3 ^ KEY2 = 04ee9855208a2cd59091d04767ae47963170d1660df7f56f5faf

# Solution: Xor có tính chất 2 cái giống nhau xor với nhau sẽ bằng 0, áp dụng điều đó nên ta áp dụng và tìm ra được flag:
from pwn import xor
KEY1 = bytes.fromhex("a6c8b6733c9b22de7bc0253266a3867df55acde8635e19c73313")

KEY21 = bytes.fromhex("37dcb292030faa90d07eec17e3b1c6d8daf94c35d4c9191a5e1e")

KEY23 = bytes.fromhex("c1545756687e7573db23aa1c3452a098b71a7fbf0fddddde5fc1")

FLAG123 = bytes.fromhex("04ee9855208a2cd59091d04767ae47963170d1660df7f56f5faf")

KEY_2 = xor(KEY21, KEY1)

KEY_3 = xor(KEY_2, KEY23)

FLAG = xor(FLAG123, KEY1, KEY_2, KEY_3)

print(FLAG.decode())

crypto{x0r_i5_ass0c1at1v3}
