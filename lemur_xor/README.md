# Challenge: Cho 2 file ảnh lemur và flag và đưa ra gợi ý là xor between RGB bytes of two images - not an xor of all the data bytes of the files 
# Solution: Viết hàm xor từng bytes RGB của cả 2 ảnh
from PIL import Image
  lemur = Image.open('lemur_ed66878c338e662d3473f0d98eedbd0d.png')
  flag = Image.open('flag_7ae18c704272532658c10b5faad06d74.png')

  pixels_lemur = lemur.load()
  pixels_flag = flag.load()

  for i in range(lemur.size[0]):
    for j in range(flag.size[1]:
      l = pixel_lemur[i, j]
      f = pixel_flag[i, j]

      r = l[0] ^ f[0]
      g = l[1] ^ f[1]
      b = l[2] ^ f[2]

      pixel_flag[i, j] = (r, g, b)
  flag.save("result.png")

  flag sẽ được lưu trong result.png
  
