# Challenge: Give a code like this:
state = [

    [206, 243, 61, 34],
    [171, 11, 93, 31],
    [16, 200, 91, 108],
    [150, 3, 194, 51],
]

round_key = [

    [173, 129, 68, 82],
    [223, 100, 38, 109],
    [32, 189, 53, 8],
    [253, 48, 187, 78],
]


def add_round_key(s, k):
    ???

print(add_round_key(state, round_key))

## Require: Write code add_round_key to decode:
And we have 2 methods:
Method 1:
def add_round_key(s, k):

    for i in range(4):
      for j in range(4):
        state[i][j] ^= round_key[i][j]
    return state



Method2:
def add_round_key(s, k):

    return [[s[i][j] ^ k[i][j] for j in range(4)] for i in range(4)]



