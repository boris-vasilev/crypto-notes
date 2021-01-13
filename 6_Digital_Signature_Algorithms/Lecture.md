Lecture

A **digital signature** is a technique for establishing the origin of a particular message such that any future disputes with regard to what message was sent and who sent it could be resolved by any third party.

# Digital Signature Requirements

- Message-dependent, inc date/time
	- unreusable
	- <ins>content integrity</ins>
- Signer-dependent
	- unforgeable
	- <ins>origin authentication</ins>
- Verifiable - others can verify
- Anti-forgery - computationally infeasible to forge

(content integrity + origin authentication) guarantees **non-repudiation**

## Forgery types
- **Existential forgery** - the creation of any (M, S) pair  where S was not produced by any legitimate signer
- **Selective forgery** - given a signature S, generate a message M that matches the signature

## Why we should ONLY sign a hash value of the message?
- **Performance** - PKC operations are time consuming. If we only sign the hash value it would be much quicker since the hash of fixed-length whereas messages can have varying length.
- **Security** - forgeries are significantly harder if a hash value is signed.

# DSA (Digital Signature Algorithm)

- DSA is a PKC but unlike RSA can only be used for digital signing and not encryption
- DSA uses two pair of keys
	- a long-term Private-Public key pair
	- an ephemeral Private-Public key pair used only once, for a single message signing

## Key generation (long-term)
- Choose 3 global public key values (p, q, g) - p,q for modulus, g for generator
	- **p** is a very large prime number
	- **q** is a 160-bit prime number that is a divisor of (p-1) (i.e. (p-1) mod q = 0)
	- **g = h<sup>(p-1)/q</sup> mod p** such that
		- 1 < h < p-1
		- g > 1
- Choose long-term private key
	- Choose random private key PR<sub>a</sub> s.t. 0 < PR<sub>a</sub> < q
- Compute public key PU<sub>a</sub> = **y = g<sup>PR<sub>a</sub></sup> mod p**

## Key generation (ephemeral)
- Choose a random number k with 0 < k < q; should only be used once
- Compute signature pair
	- **r = (g<sup>k</sup>mod p)mod q**
	- **s = [k<sup>-1</sup>(H(M) + xr)]mod q**
		- ***NOTE***: Here k<sup>-1</sup> is the multiplicative inverse of k mod q **NOT** k to the power of -1
	- Signature = (r, s)
		- r - ephemeral public key
		- k - ephemeral private key
		- s - message signature
- Send M || Signature
## Signature verification
- The receiver has got PU<sub>a</sub> = {p,q,g,y} and {M' r', s'}
- To verify the signature, receiver computes
	- message hash H(M')
	- mod q inverse of s': w=(s')<sup>-1</sup>mod q
	- u1 = [H(M')w]mod q
	- u2 = (r')w mod q
	- **v = [(g<sup>u1</sup><sup>u2</sup>) mod p] mod q**
- if **v = r'** then the signature is verified
- Here M=message to be signed, H(M) =hash of message; M', r', s' = received versions of M,r,s
## RSA vs DSA
- RSA based on the difficulty of factoring large numbers
- DSA based on the difficulty of taking discrete logarithms
- DSA can only sign messages
- DSA is faster because some signature computations can be computed a priori
	- ***NOTE*** in DSA: r can be computed in advance, and also from **s = [k<sup>-1</sup>(H(M) + xr)]mod q** [k<sup>-1</sup> mod q]
- RSA singature is about 1-2k bits long, in DSA - 320 bits
- In DSA you don't recover the message digest from the signature (you verify **v = r'**), In RSA you do (decrypt signature and verify H(M') = H(M))
- DSA requires a secret number *k* for each message