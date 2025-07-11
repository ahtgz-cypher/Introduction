# THỬ THÁCH: Chuyển chuỗi ASCII này thành kí tự để lấy Flag
[99, 114, 121, 112, 116, 111, 123, 65, 83, 67, 73, 73, 95, 112, 114, 49, 110, 116, 52, 98, 108, 51, 125]
# Solution
data = [99, 114, 121, 112, 116, 111, 123, 65, 83, 67, 73, 73, 95, 112, 114, 49, 110, 116, 52, 98, 108, 51, 125]
Flag = "".join(chr(n) for n in data)
print(Flag)
--> Dùng chr() để đưa ASCII về dạng char(kí tự) và có thể dùng hàm ord để làm ngược lại
crypto{ASCII_pr1nt4bl3}
