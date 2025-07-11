# Challenge: Chuyển chuỗi số dài và lớn(Big Integer) thành kí tự Flag
11515195063862318899931685488813747395775516287289682636499965282714637259206269
# Solution: Dùng bytea_to_long hoặc long_to_bytes để chuyển và trong bài này chúng ta phải sử dụng long_to_bytes
from Crypto.Util.number import *

data = 11515195063862318899931685488813747395775516287289682636499965282714637259206269

Flag = long_to_bytes(data)

print(Flag.decode())

crypto{3nc0d1n6_4ll_7h3_w4y_d0wn}
