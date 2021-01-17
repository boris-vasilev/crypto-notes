Exercise

# Exercise 10.1
i)
- Compression comes before encryption for performance reasons, to reduce the sign of the message, and for security reasons - to mask any redundancy that could be part of the message (e.g. in written text)
ii)
- No. We might want to verify the sender before decrypting the message. In order to protect against DoS attacks. If someone sends a very large message with the intention to overload the server we want to reduce the load as much as possible so verifying the sender before decrypting(a slow operation) so we can discard the message without needing to decrypt.
iii) E<sub>PU<sub>B</sub></sub>[K<sub>S</sub>]||E<sub>K<sub>S</sub></sub>[Z(M||E<sub>PR<sub>A</sub></sub>[H(M)])]

# Exercise 10.2
- X.509 uses a centralised trust model. Single point of failure. And a bottleneck.
- It is hard for new users to enter a web-of-trust if they don't know anyone there. Their keys won't be trusted by anyone.
- In a web-of-trust the key revocation is left to the user which is less secure. The user might not send it to everyone. In X.509 the user has to notify just the CA and from then on it is the CA's job to broadcast the CRL. Since the CA knows all of it's trustees, it is much less likely that they'll miss someone.
- If a CA is compromised key revocation is a much more complicated process. Not only does the CA's key need to be changed, but also all of its trustees keys as well. Note that key revocation is not something that happens rarely. Keys should be expire to keep them secure, so every once in a while an expensive process of key revocation has to happen. 