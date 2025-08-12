﻿

# Challenge 1 - Image Sweeper I

## Description

The objective of this challenge is to determine the owner's email from an image file that was reconstructed from a public WiFi. 

# Solution
**1. Review the Image Pr**

In wireshark analyzing the conversation between IP Addresses '192.168.10.128' and '192.168.10.130' indicates a file download from '192.168.10.130' on port 8080.
 
**2. Downloading File from TCP streams**

using the filter 'tcp.port == 8080' and observing the conversations between the two hosts reveals 9 TCP Streams ranging from (19-26 and 37).

Apply the filter 'tcp.stream eq 19' and save the TCP stream as RAW with the file name '1' in a new folder. Do the same for the remaining TCP streams such that each RAW stream file has a consecutive number.

**3. Reconstructing the file**

Analyzing the first RAW file downloaded from stream 19 reveals that this is a ZIP file. This is shown in file explorer and can be confirmed with the command:

    file 1
    "1: Zip archive data, at least v2.0 to extract, compression method=deflate"


the remainder of the files are simply data:

    file 2
    2: data

To reconstruct the file back to the original format from all of the downloaded parts, perform the following command:

    'cat * > reassembled_file'

  

The file command once again confirms this is a ZIP file:

    file reassembled_file
    reassembled_file: Zip archive data, at least v2.0 to extract, compression method=deflate

**4. Attempting to extract the file** 

Attempting to unzip the file reveals that the file is encrypted and thus the password needs to be cracked. 

    └─$ unzip reassembled_file 
    Archive:  reassembled_file
    [reassembled_file] 7-ZipPortable_25.01.paf.exe password: 
       skipping: 7-ZipPortable_25.01.paf.exe  incorrect password

**5. Cracking the password**

There are many tools which can be used to crack ZIP files with a provided word list. Johntheripper can be used as well however it requires multiple steps. the tool

    └─$ fcrackzip -D -p ./rockyou.txt -u reassembled_file 
    PASSWORD FOUND!!!!: pw == puppies

**6. Unzip file and get file hash**

Now unzip the file with the provided password and retrieve the hash.

    └─$ unzip -P "puppies" reassembled_file 
    Archive:  reassembled_file
      inflating: 7-ZipPortable_25.01.paf.exe  

    └─$ sha256sum 7-ZipPortable_25.01.paf.exe 
        4b9ffc309794b8f98fef90622ba54e067574fe6a454e31e9d1106065ba3c3167  7-ZipPortable_25.01.paf.exe


**7. Search file hash on VirusTotal** 

We then search the file hash on VirusTotal to confirm if this executable. The result indicates that this executible is flagged as malicious however is a 'EICAR-Test-File' file and thus a false positive. However, analyzing in the details section for other files with the same hash results in the flag

    7-ZipPortable_25.01.paf.exe
    flag{N0t_mal1c1ous}

Thus completing this challenge.

https://www.virustotal.com/gui/file/4b9ffc309794b8f98fef90622ba54e067574fe6a454e31e9d1106065ba3c3167/details


# Recreating this challenge 
Recreating this challenge is simple however requires a few steps.

1. Select target file and embed EICAR String
2. Duplicate the file and rename one duplicate with the flag name
3. upload the file with the flag name to VirusTotal
4. Zip original file with a password  
`Zip -e encrypted_file.zip target_file`

5. Split the file into chunks using the split command. Modify the file size accordingly  
`split -b 500k encrypted_file.zip part_`

6. Begin network capture using Wireshark
7. Transfer each split file from machineA to machineB in consecutive order using netcat  
on MachineB:  
`nc -l -p 8080 > part_##`  
on machineA  
`nc MachineB_ip 8080 < part_##`

8. Stop and save packet capture. 

This completes the recreation of this CTF Challenge. 

