Exercise

# Exercise 3.1
A Meet-in-the-middle attack could be used to break the cipher in 2<sup>56</sup> trials by observing intermediate values.
# Exercise 3.2
![78fd1281a53f1bc2bd96fb6d19e61bd1.png](../_resources/f60b0e2d6529409ba08a2348661b0904.png)
![12f439c7891a0edfd614e3da58103750.png](../_resources/271b05126e2b4c6286e8e358202cca2c.png)
i) If the ATM is hacked it could be used for fraudulent transactions. Since the ATM has access to the PIN+identity on the magnetic strip they could be stored and later used with fake *Trans Info* which will be accepted by the bank and the account will be charged.
To resolve this I would introduce a second symmetrical key cipher with key K<sub>C/Bank</sub>, known by the customer and the bank. The data on the magnetic strip is E(K<sub>C/Bank</sub>, {PIN + Indentity}) and is passed by the ATM to the bank along with E(K<sub>ATM/Bank</sub>, {TransInfo + PIN_typed}). The bank then checks if PIN == PIN_typed and sends its decision to the ATM. The ATM doesn't have access to the customer's information at any point
ii) The problem with using symmetrical key cipher is with key management. The bank needs to store the keys for all its customers. In the original solution the problem is even bigger because all the ATMs need to store the K<sub>card/ATM</sub> for all cards in the world. Even worse, the tiny chip on the card needs to store K<sub>card/ATM</sub> for all ATMs to be usable everywhere, which is absurd. And also, each time a card is issued all ATMs need to generate a cipher to be used with that card.