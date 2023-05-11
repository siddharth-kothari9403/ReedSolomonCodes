# ReedSolomonCodes
Implementation of Reed Solomon Codes using Jupyter Notebook

1. The following is a code for the implementation of the integer form of the Reed Solomon Codes. The message (which is less than a given bound M) is encoded into (a1, a2, ..., ak) using Chinese Remainder Theorem, and given a limit l on the max no. of ai's that can get corrputed, we can reconstruct a even after the corruption.
2. For this implementation we choose a max length for the message (hence M = 2^length), and take a message a as input, and a corruption factor mu which denotes the fraction of values that can get corrupted (hence the limit on the max corruption is floor(mu.k)), where k is the number of primes chosen.
3. According to Reed Solomon Code, if we pick the k primes (n1, n2, ..., nk) used in CRT such that product of the primes > (2MP^2) where P = product of the maximum l primes out of n1, n2, ..., nk, then we can reconstruct the message if atmost l of the ai's get corrupted, using Euclid's Extended GCD algorithm.
4. For details on implementation and proof of correctness of the algorithm, kindly refer to A Computational Introduction to Number Theory by Victor Shoup. 
5. For our implementation we have, apart from the reconstruction algorithm, implemented the following:
    a. Binary EGCD algorithm - used to find the inverse mod n for a given number
    b. CRT algorithm - used to reconstruct a given number given its CRT representation.
    c. Euclid's EGCD algorithm - used in the reconstruction algorithm.    
6. There are 2 versions of the global setup - one is the correct one, which will always be able to reconstruct the value correctly, as it calculates the number of primes required based on the corruption factor, and keeps on choosing primes until the product becomes > 2MP^2. The other one has a probability to fail.
7. Once we have the globals ready, we use the CRT algorithm to break down the message a into a1, a2, ..., ak, and then transmit it. Transmitting involves choosing random indices which get corrupted, and giving the corrupted version (b1, b2, ..., bk) to the receiver.
8. We then follow the reconstruction algorithm as described in Victor Shoup's book.

