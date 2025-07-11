# Challenge: Chuyển chuỗi sau về byte và decode byte đó ra thành Flag
72bca9b68fc16ac7beeb8f849dca1d8a783e8acf9679bf9269f7bf
# Solution: dùng bytes.fromhex() để giải mã hex trước rồi dùng base64.b64encode() để giải mã
import base64

data = '72bca9b68fc16ac7beeb8f849dca1d8a783e8acf9679bf9269f7bf'

Hex = bytes.fromhex(data)

Flag = base64.b64encode(Hex)

print(Flag.decode())

crypto/Base+64+Encoding+is+Web+Safe/
