# Challenge: Tìm x và y trong phương trình: ax + by = gcd(a, b),
cho a = 26513 và b = 32321
# Solution: Ta có thể biết được gcd của a và b là bằng 1 vì a và b là 2 số nguyên tố, vậy giờ ta phải giải quyết bài toán ax + by = 1, phải tìm nghiệm x và y nhưng chỉ có 1 phương trình
Mình sẽ đưa ra một ví dụ cụ thể giúp bạn hiểu hơn luôn:
Ví dụ ta có a = 3 và b = 5, hai số trên đều là số nguyên tố, và ta có pt như sau:
3x + 5y = 1
bây giờ ta phân tích về dạng a = bq - r (q là thương nguyên của a/b, còn r là phần dư của a%b)
5 = 3x1 + 2 (1)
3 = 2x1 + 1 (2)
2 = 1x2 + 0 (3)
-> Tiếp theo ta sẽ truy vết ngược để tìm tổ hợp tuyến tính:
1 = 5x + 3y
Từ (1) suy ra: 2 = 5 - 3 x 1
Từ (2) suy ra: 1 = 3 - 1 x 2
Thay (1) vào (2) ta được: 
1 = 3 - 1 x (5 - 3 x 1)
<=> 1 = 3 - 1 x 5 - 3 x 1
<=> 1 = 5 x 2 - 3 x 1
<=> 1 = 5 x 2 + 3 x (-1)
Vậy x = 2 và y = -1

Mã python sẽ được viết như sau:
def egcd(x, y):
  if a == 0:
    return b, 0, 1 
  else: 
    gcd, x, y = egcd(b % a, a)
    return gcd, y - (b // a) * x, x
  print()

Kết quả: -8404

    



