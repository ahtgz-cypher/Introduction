# Source: 
#!/usr/bin/env python3

import sys

#import this

if sys.version_info.major == 2:
    print("You are running Python 2, which is no longer supported. Please update to Python 3.")

ords = [81, 64, 75, 66, 70, 93, 73, 72, 1, 92, 109, 2, 84, 109, 66, 75, 70, 90, 2, 92, 79]

print("Here is your flag:")
print("".join(chr(o ^ 0x32) for o in ords))

# Solution:
Đề bài cho 1 dãy số đã bị xor với 0x32 (tức là 50) 
Thử thách chỉ yêu cầu mình chạy file và lấy Flag
ords = [81, 64, 75, 66, 70, 93, 73, 72, 1, 92, 109, 2, 84, 109, 66, 75, 70, 90, 2, 92, 79]

print("Here is your flag:")
print("".join(chr(o ^ 0x32) for o in ords))
Và Flag nhận được là crypto{z3n_0f_pyth0n}
