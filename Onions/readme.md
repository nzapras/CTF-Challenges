﻿

# Challenge 7 - Onions

## Description

The objective of this challenge is to decrypt the provided cyphertext: `R1UyRE1PQldIRTNUR01SUUdZNERNTUpYR01aREFOU0VHWVlUTVJKWEhFWkRBTlNER1lZVE9PSldHVTNURU5aVEdKQ1RFUkpTSVVaREFOQ0RHWTRUTVFSV0dVWkRBTlJSR1pDVEVNQldJWTNFS05SWkdaRERNUkpTSVU9PT09PT0=`

# Solution
**1. Review the Ciphertext**

Reviewing the ciphertext will make users realize that the cipher applied base64.
 
**2. Decoding the Cyphertext**

The user can then use a base64 decoder tool found with a quick google search to see the plaintext.  The user will then realize that the plaintext is still encrypted and that the
true plaintext is has been evolped in multiple encryption layers. Decoding from base64 produces the following result: 

**3. Entering the Flag**

The user can then simply enter the flag in the following format: flag{Just like the salad :)}

# Recreating this challenge 

To recreate this challenge one can follow these steps:

1. Create your plaintext and apply the caeser shift.
2. Create the challenge on the CTF platform with the ciphertext provided in the challenge.

This completes the recreation of this CTF Challenge. 

