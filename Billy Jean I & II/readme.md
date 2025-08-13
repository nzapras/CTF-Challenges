﻿

# Challenge 9 - Billy Jean I

## Description

This challenge is the first challenge in two a part challenge wherein the user is provided a multi-volume file. You will need to download both of the files and put them in the same directory or else you will not be able to process the disk image. The disk image used in this challenge can be found here https://digitalcorpora.org/corpora/scenarios/m57-jean/. The disk image given is from an employee named Jean who works at M57.biz. A few weeks into the creation of the company, a confidential spreadsheet that contains the names and salaries of the company’s key employees was found posted to the comment section of one of the firm’s competitors.

With this in mind, the goal of this challenge is to determine the online identity of the adversary (email address) which leaked this information.

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

