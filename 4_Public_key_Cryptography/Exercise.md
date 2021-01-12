Exercise

# Exercise 4.1
> Name three application scenarios or cases where using RSA is preferable than using AES and name one application scenario where the use of AES is necessary

i)
1. Digital signatures
2. For establishing of a symmetric key cipher
3. Parties do not trust each other

ii) When low latency is required.

# Exercise 4.2

>You are a recipient of p = 5, q = 7. You make the modulus n = 35 public. You also choose an exponent e = 5 and make that public too.Messages are sent to you, one letter at a time. Letters are coded into numbers as: A -> 0, B -> 1, and so on.Now, the following message has arrived for you:17 19 7 9 0 12 24Decrypt this message.

p = 5 q = 7 n = 35 e = 5
φ(n) = (5-1)(7-1) = 24

d = e<sup>-1</sup>mod φ(n) = 5<sup>-1</sup>mod 24 = 5

M = C^5mod 35
17 --> 12 --> M
19 --> 24 --> Y
7 --> 7 --> H
9 --> 4 --> E
0 --> 0 --> A
12 --> 17 --> R
24 --> 19 --> T
