# Challenge: Cho 2 số nguyên lớn, yêu càu tìm ước chung lớn nhất của 2 số nguyên đó
# Solution: Viết hàm tính ước chung lớn nhất đơn giản:
def gcd(a, b):

    while b != 0:
    
        a, b = b, a % b
        
    return(a, b)
    
result = gcd(66528, 52920)

print(result)

và chương trình sẽ in ra kết quả là 1512

