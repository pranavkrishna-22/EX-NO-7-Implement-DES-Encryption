# EX-NO-7-Implement-DES-Encryption

## Aim:

To use the Data Encryption Standard (DES) algorithm for a practical application, such as securing sensitive data transmission in financial transactions.

## ALGORITHM:

1. DES is based on a symmetric key encryption technique that encrypts data in 64-bit blocks.
2. DES uses a Feistel network structure with 16 rounds of processing for encryption.
3. DES has a 64-bit key, but only 56 bits are used for encryption (the remaining 8 bits are for parity).
4. DES applies initial and final permutations along with 16 rounds of substitution and permutation transformations to produce ciphertext.

## Program:
```c
#include <stdio.h>
#include <string.h>
#include <openssl/des.h>

int main() {
    DES_cblock key = {0x13,0x34,0x57,0x79,0x9B,0xBC,0xDF,0xF1};
    DES_key_schedule schedule;
    DES_set_key_checked(&key, &schedule);

    unsigned char input[100], encrypted[100], decrypted[100];

    printf("Enter plaintext: ");
    fgets((char *)input, sizeof(input), stdin);
    input[strcspn((char *)input, "\n")] = 0;  // remove newline

    // Encrypt (first 8 bytes only – to keep it beginner friendly)
    DES_ecb_encrypt((DES_cblock*)input, (DES_cblock*)encrypted, &schedule, DES_ENCRYPT);

    printf("\nPlaintext: %s", input);
    printf("\nEncrypted (Hex): ");
    for (int i = 0; i < 8; i++)
        printf("%02X ", encrypted[i]);

    // Decrypt
    DES_ecb_encrypt((DES_cblock*)encrypted, (DES_cblock*)decrypted, &schedule, DES_DECRYPT);

    printf("\nDecrypted Text: %s\n", decrypted);

    return 0;
}
```
## Output:
<img width="397" height="146" alt="Screenshot 2025-11-02 185249" src="https://github.com/user-attachments/assets/4f2530e5-c9db-4f83-ab8d-d70388466f43" />

## Result:
  The program is executed successfully

