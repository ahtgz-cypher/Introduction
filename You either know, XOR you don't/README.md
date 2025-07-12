# Challenge: đề bài cho 1 chuỗi hex và gợi ý là remember the flag format

0e0b213f26041e480b26217f27342e175d0e070a3c5b103e2526217f27342e175d0e077e263451150104

# Solution: decode chuỗi hex đó ra và cho nó xor với định dạng của flag là crypto{, và sau đó chúng ta phải trích một phần có nghĩa của lần xor vừa rồi và đem xor tiếp với chuỗi hex đã được decode
from pwn import xor
data = bytes.fromhex('0e0b213f26041e480b26217f27342e175d0e070a3c5b103e2526217f27342e175d0e077e263451150104')

print(xor(data, 'crypto{'.encode()))

print(xor(data, 'myXORkey'.encode()))

b'crypto{1f_y0u_Kn0w_En0uGH_y0u_Kn0w_1t_4ll}'
