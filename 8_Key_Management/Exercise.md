Exercise

# Exercise 8.1
> Assuming that Alice is to send a message, M, to Bob. Mis encrypted with a shared key established using the DH protocol. Explain whether Eve could access this message M. If so, explain how, and propose a solution to address this vulnerability.

Yes, man-in-the-middle attack
1. If Alice and Bob's keys are certified by a trusted CA a MitM attack is not an issue
2. 

# Exercise 8.2
No authentication. A could be impersonated in step 1 and B in step 2

# Exercise 8.3
i. If KDC sends the session key to Bob that is one more message KDC needs to send. KDC can become a bottleneck in the NS protocol and it's better to reduce it's jobs as much as possible to prevent it. If the key transfer can be delegated to Alice, I think that's the better option.
ii.
1. To establish a secure channel between parties that trust each other. For example, IoT devices managed by a central server. The central server takes the role of the KDC. If some of the devices want to communicate they get a session key from the server. Using PKC can be time consuming.
2. When we want to monitor/log the communication between the parties. If for some reason we want to know what party is talking to what other party we can have an NS protocol to ensure that in order for them to establish a channel they first go through KDC, whose job is to generate a session key AND monitor/log.