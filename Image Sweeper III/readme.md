﻿

# Challenge 3 - Image Sweeper III

## Description

This challenge is one in a series of challenges which starts at the image level. In the first challenge (Image Sweeper I), the user is provided an image which can then be used to reverse lookup the owner’s github account via the image file metadata.  From this point the user is expected to thoroughly inspect and review information that can be found on github as well as any other associated accounts or information that can be uncovered to determine the SSID of the WAP network the target was connected to.   

# Solution
**1. Review Metadata**

Reviewing the Metadata will reveal that the photographer's online alias is C0SM1CINFLUX.
 
**2. Conduct a Search**

After conducting a thorough search, the user should be able to find the target's github and subsequently the target's twitter page and blog.

**3. Locating the Email**

The user can then find the target's email visible in their Project-Recruiter repo readme.md file.

# Recreating this challenge 
Recreating this challenge is simple however requires a few steps.

To recreate this challenge one can follow these steps:

1. Select an image to start with.
2. Modify the copyright metadata string to be the name/alias of the target.
3. Create a supporting github account, twitter account, and blog web page.
4. Create a repo on the github account with an readme.md file that contains the target's email. 

This completes the recreation of this CTF Challenge. 

