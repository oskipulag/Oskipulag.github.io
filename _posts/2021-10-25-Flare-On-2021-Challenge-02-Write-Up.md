## Challenge 02 - Known

In this challenge we are presented with the following message:

> We need your help with a ransomware infection that tied up some of our critical files. Good luck.

We received a binary called 'UnlockYourFiles.exe' and 6 encrypted files created by the so called ransomware.

It is clear our job is to understand the encryption algorithm, and possibly decrypt the files.

Checking the first 8 bytes of the encrypted files, we see the following:

```
$ for filename in *; do echo "${filename}":;  hexdump -n8 "${filename}" | cut -c 9-; done

capa.png.encrypted:
c7c7 1d25 0d63 56f3                    

cicero.txt.encrypted:
5c1d 30a8 bee5 9aeb                    

commandovm.gif.encrypted:
4a09 3323 46c1 601d                    

critical_data.txt.encrypted:
f066 18bd 0431 3a62                    

flarevm.jpg.encrypted:
83b1 2871 dd32 ee32                    

latin_alphabet.txt.encrypted:
ce0f bc60 2fe6 ea46

```

We get:
