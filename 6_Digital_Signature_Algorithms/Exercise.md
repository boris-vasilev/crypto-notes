Exercise

# Exercise 6.1
> 1. Discuss, at the generic level, what are the factors that impact on the security of a digital signature.
> 2. Assuming that the RSA algorithm is used for signature signing, identify all possible ways of forging a signature.

- Length of the keys
- Strength of the algorithm (if it is hard to forge)
- If the keys are stored safely
---
- Generate random signature s, Generate a random message M, if H(M) = Dec(PU<sub>a</sub>, s) we have a valid A signature on message M.
- Given a message M, generate random signatures s and check H(M) = Dec(PU<sub>a</sub>, s) until a matching s is found

# Exercise 6.2
> A digital signature scheme may also be implemented using a symmetric-key cipher, but with the assistance of a trusted third party, an Arbitrator.
> 1. Design a digital signature protocol using symmetric-key encryption and an arbitrator, but do not expose the content of a message to be signed to the arbiter. 
> 2. Compare the signature protocol designed in 1. with the RSA based signature scheme.

Protocol:
1. Arbiter generates a symmetric key K
2. Arbiter generates a large integer x
3. Arbiter securely sends {K, x} to the Sender and {K} to receiver
4. Sender semds signed_M = M||E(K, H(M)||x) to receiver
5. Receiver decrypts the signature using K (getting H(M)||x). Checks the hash value, and sends the received integer x to Arbiter
6. Arbiter verifies that x is indeed the number he sent to the Sender in step 3.

It is hard for the receiver to forge a signature since they don't know what X is. Only the Sender and the Arbiter know its value. If it is sufficiently large it would take many tries until he gets it right.

Comparison to RSA based signature:
- Involves more communication costs.
- Needs a trusted third party
- Arbiter could become a bottleneck