# Challenge: Write code turn matrix 4x4 into bytes to take flag
def bytes2matrix(text):

    """ Converts a 16-byte array into a 4x4 matrix.  """
    return [list(text[i:i+4]) for i in range(0, len(text), 4)]

def matrix2bytes(matrix):

    """ Converts a 4x4 matrix into a 16-byte array.  """
    ????

matrix = [

    [99, 114, 121, 112],
    [116, 111, 123, 105],
    [110, 109, 97, 116],
    [114, 105, 120, 125],
]

print(matrix2bytes(matrix))

# Solution: 

def matrix2bytes(matrix):

  return bytes([matrix[row][col] for row in range(4) for col in range(4)])
  
print(matrix2bytes.decode())

And receive flag crypto{inmatrix}
