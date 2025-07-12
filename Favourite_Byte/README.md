# Challenge: Cho 1 chuỗi Hex và gợi ý xor với 1 single byte, yêu cầu tìm ra FLag
# Solutin: decode chuỗi hex đó về byte và rồi lấy byte đó xor trong phạm vi từ 0 đến 255 thử, nếu tìm được Flag thì in ra

data = bytes.fromhex("73626960647f6b206821204f21254f7d694f7624662065622127234f726927756d")

for k in range(255):

    decoded = bytes([k ^ h for h in data])
    
    if b'crypto' in decoded:
    
        print(decoded.decode())

crypto{0x10_15_my_f4v0ur173_by7e}
