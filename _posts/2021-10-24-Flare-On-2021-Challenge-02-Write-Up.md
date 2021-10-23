##

In this challenge we are pressented with the following message:

> We need your help with a ransomware infection that tied up some of our critical files. Good luck.

We received a binary called 'UnlockYourFiles.exe' and 6 encrypted fles created by the so called ransomware.

It is clear our job is to understand the encryption algorithm, and possibly decrypt the files.

Checking the first 8 bytes of the encrypted files, we see the following:
> for filename in *; do echo "${filename}":;  hexdump -n8 "${filename}" | cut -c 9-; done

We get: 
