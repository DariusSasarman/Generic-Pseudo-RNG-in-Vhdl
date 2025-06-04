# Generic-Pseudo-RNG-in-Vhdl

## Basic functionality:

Beginning from a given target seed and using a modified Linear Feedback Shift Register (LFSR), the output transmits a random number based on 'n' bits. 
A main problem of the LFSR, though, is the fact that having all output bits equal to zero results in getting stuck ( 0 xor 0 xor 0 = 0).
In this Pseudo-random number generator I tackled this issue with the following steps :

    1. Detect when this state occurs.
    2. When it does:
      a. Check if a new seed has been inserted. If yes, pick the new seed.
      b. If not, increment the previous seed, and pick the result.
    3. Load chosen seed on D flip-flops.
    4. Wait for when this happends again.

This way, all seeds are extended and overlap, making numbers exhibit higher variability.

Since all D flip-flops start with a default state '0', not entering any seed different from "00...00" makes it wait for an input. This actually takes advantage of the "main" disadvantage of an LFSR. :wink:
## Architecture overview:

![Untitled Diagram drawio](https://github.com/user-attachments/assets/5d062c62-8c25-474b-aff9-525283da7687)
